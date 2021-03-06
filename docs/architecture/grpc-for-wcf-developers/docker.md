---
title: 도커 - WCF 개발자를 위한 gRPC
description: ASP.NET 코어 gRPC 응용 프로그램에 대한 도커 이미지 만들기
ms.date: 09/02/2019
ms.openlocfilehash: e67c43f9486fbfe9a5d3e84e3b74770eb621f604
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148116"
---
# <a name="create-docker-images"></a>Docker 이미지 만들기

이 섹션에서는 ASP.NET 코어 gRPC 응용 프로그램에 대한 Docker 이미지 생성을 다루며 Docker, Kubernetes 또는 기타 컨테이너 환경에서 실행할 준비가 되었습니다. ASP.NET 코어 MVC 웹 앱 및 gRPC 서비스와 함께 사용되는 샘플 응용 프로그램은 GitHub의 [도트넷 아키텍처/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) 리포지토리에서 사용할 수 있습니다.

## <a name="microsoft-base-images-for-aspnet-core-applications"></a>ASP.NET 코어 응용 프로그램에 대 한 마이크로소프트 기본 이미지

Microsoft는 .NET Core 응용 프로그램을 빌드하고 실행하기 위한 다양한 기본 이미지를 제공합니다. 코어 3.0 이미지를 ASP.NET 만들려면 두 개의 기본 이미지를 사용합니다.

- 응용 프로그램을 빌드하고 게시할 SDK 이미지입니다.
- 배포를 위한 런타임 이미지입니다.

| 이미지 | Description |
| ----- | ----------- |
| [mcr.microsoft.com/dotnet/core/sdk](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | 을 통해 `docker build`응용 프로그램을 빌드하는 경우 생산에 사용할 수 없습니다. |
| [mcr.microsoft.com/dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | 런타임 및 ASP.NET Core 종속성을 포함합니다. 생산을 위해. |

각 이미지에 대해 태그별로 구별되는 서로 다른 Linux 배포판을 기반으로 하는 네 가지 변형이 있습니다.

| 이미지 태그 | Linux | 메모 |
| --------- | ----- | ----- |
| 3.0 버스터, 3.0 | Debian 10 | OS 변형이 지정되지 않은 경우 기본 이미지입니다. |
| 3.0 알파인 | 알파인 3.9 | 알파인 베이스 이미지는 데비안 이나 우분투 이미지 보다 훨씬 작습니다. |
| 3.0 디스코 | Ubuntu 19.04 | |
| 3.0 바이오닉 | Ubuntu 18.04 | |

알프스 의 기본 이미지는 데비안 과 우분투 이미지의 경우 200 MB에 비해 약 100 MB입니다. 일부 소프트웨어 패키지 또는 라이브러리는 Alpine의 패키지 관리에서 사용하지 못할 수 있습니다. 사용할 이미지를 잘 모르는 경우 기본 데비안(Debian)을 선택해야 합니다.

> [!IMPORTANT]
> 빌드 및 런타임에 동일한 Linux 변형을 사용해야 합니다. 한 변형에 빌드되고 게시된 응용 프로그램은 다른 변형에서 작동하지 않을 수 있습니다.

## <a name="create-a-docker-image"></a>Docker 이미지 만들기

Docker 이미지는 *Dockerfile*에 의해 정의됩니다. 이 파일은 응용 프로그램을 빌드하고 응용 프로그램을 빌드하거나 실행하는 데 필요한 모든 종속성을 설치하는 데 필요한 모든 명령을 포함하는 텍스트 파일입니다. 다음 예제에서는 ASP.NET 코어 3.0 응용 프로그램에 대한 가장 간단한 Dockerfile을 보여 주며 다음과 같은 예제를 보여 주며 다음과 같은 예제를 보여 주며 다음과 같은 예제를 보여 주며 다음과 같은

```dockerfile
# Application build steps
FROM mcr.microsoft.com/dotnet/core/sdk:3.0 as builder

WORKDIR /src

COPY . .

RUN dotnet restore

RUN dotnet publish -c Release -o /published src/StockData/StockData.csproj

# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

# Uncomment the line below if running with HTTPS
# ENV ASPNETCORE_URLS=https://+:443

WORKDIR /app

COPY --from=builder /published .

ENTRYPOINT [ "dotnet", "StockData.dll" ]
```

Dockerfile에는 두 부분으로 구성됩니다. `sdk` 두 번째는 `aspnet` 베이스에서 런타임 이미지를 만듭니다. 이는 런타임 `sdk` 이미지의 경우 약 200MB에 비해 이미지가 약 900MB이며 대부분의 내용은 런타임에 필요하지 않습니다.

### <a name="the-build-steps"></a>빌드 단계

| 단계 | Description |
| ---- | ----------- |
| `FROM ...` | 기본 이미지를 선언하고 별칭을 `builder` 할당합니다. |
| `WORKDIR /src` | 디렉터리를 `/src` 만들고 현재 작업 디렉토리로 설정합니다. |
| `COPY . .` | 호스트의 현재 디렉터리 아래에 있는 모든 것을 이미지의 현재 디렉터리로 복사합니다. |
| `RUN dotnet restore` | 모든 외부 패키지를 복원합니다(ASP.NET 코어 3.0 프레임워크는 SDK와 함께 사전 설치되어 있음). |
| `RUN dotnet publish ...` | 릴리스 빌드를 빌드하고 게시합니다. 플래그는 `--runtime` 필요하지 않습니다. |

### <a name="the-runtime-image-steps"></a>런타임 이미지 단계

| 단계 | Description |
| ---- | ----------- |
| `FROM ...` | 새 기본 이미지를 선언합니다. |
| `WORKDIR /app` | 디렉터리를 `/app` 만들고 현재 작업 디렉토리로 설정합니다. |
| `COPY --from=builder ...` | 첫 번째 `builder` `FROM` 줄의 별칭을 사용하여 이전 이미지에서 게시된 응용 프로그램을 복사합니다. |
| `ENTRYPOINT [ ... ]` | 컨테이너가 시작될 때 실행되도록 명령을 설정합니다. 런타임 이미지의 `dotnet` 명령은 DLL 파일만 실행할 수 있습니다. |

### <a name="https-in-docker"></a>도커의 HTTPS

Docker에 대 한 `ASPNETCORE_URLS` Microsoft 기본 `http://+:80`이미지 환경 변수를 설정 합니다., 즉 Kestrel 해당 포트에 HTTPS 없이 실행 됩니다. 사용자 지정 [인증서(자체 호스팅 gRPC 응용 프로그램에](self-hosted.md)설명된 대로)와 함께 HTTPS를 사용하는 경우 이를 재정의해야 합니다. Dockerfile의 런타임 이미지 생성 부분에서 환경 변수를 설정합니다.

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a>.dockerignore 파일

소스 `.gitignore` 제어에서 특정 파일 및 디렉터리를 `.dockerignore` 제외하는 파일과 마찬가지로 파일을 사용하여 파일 및 디렉터리가 빌드 하는 동안 이미지에 복사되는 것을 제외할 수 있습니다. 이렇게 하면 복사 시간을 절약할 수 있지만 PC의 `obj` 디렉터리를 이미지로 복사하여 발생하는 일부 오류를 방지할 수도 있습니다. 최소한 `bin` `.dockerignore` 파일에 대한 `obj` 항목을 추가해야 합니다.

```console
bin/
obj/
```

## <a name="build-the-image"></a>이미지 빌드

단일 응용 프로그램과 단일 Dockerfile이 있는 솔루션의 경우 Dockerfile을 기본 디렉터리에 넣는 것이 가장 간단합니다. 즉, 파일과 동일한 디렉토리에 `.sln` 넣습니다. 이 경우 이미지를 빌드하려면 Dockerfile이 `docker build` 포함된 디렉터리에서 다음 명령을 사용합니다.

```console
docker build --tag stockdata .
```

혼동할 수 `--tag` 있는 플래그(단축할 `-t`수 있음)는 지정된 경우 실제 태그를 포함하여 이미지의 전체 이름을 지정합니다. 끝에는 `.` 빌드가 실행될 컨텍스트를 지정합니다. Dockerfile의 `COPY` 명령에 대한 현재 작업 디렉토리입니다.

단일 솔루션 내에 여러 응용 프로그램이 있는 경우 파일 옆에 각 응용 프로그램에 대한 `.csproj` Dockerfile을 자체 폴더에 유지할 수 있습니다. 솔루션과 모든 `docker build` 프로젝트가 이미지에 복사되도록 기본 디렉터리에서 명령을 계속 실행해야 합니다. (또는) `-f`플래그를 사용하여 현재 디렉터리 `--file` 아래에 Dockerfile을 지정할 수 있습니다.

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a>컴퓨터의 컨테이너에서 이미지 실행

로컬 Docker 인스턴스에서 이미지를 실행하려면 `docker run` 명령을 사용합니다.

```console
docker run -ti -p 5000:80 stockdata
```

플래그는 `-ti` 현재 터미널을 컨테이너터미널에 연결하고 대화형 모드로 실행됩니다. 로컬 `-p 5000:80` 호스트 네트워크 인터페이스에서 포트 5000에 컨테이너에 (링크) 포트(80)를 게시합니다.

## <a name="push-the-image-to-a-registry"></a>이미지를 레지스트리로 푸시

이미지가 작동하는지 확인한 후 Docker 레지스트리로 푸시하여 다른 시스템에서 사용할 수 있도록 합니다. 내부 네트워크는 Docker 레지스트리를 프로비전해야 합니다. 이는 [Docker `registry` 자체 이미지(Docker](https://docs.docker.com/registry/deploying/) 레지스트리가 Docker 컨테이너에서 실행됨)를 실행하는 것만큼 간단할 수 있지만 다양한 포괄적인 솔루션을 사용할 수 있습니다. 외부 공유 및 클라우드 사용의 경우 Azure 컨테이너 [레지스트리](https://docs.microsoft.com/azure/container-registry/) 또는 [Docker Hub와](https://docs.docker.com/docker-hub/repos/)같은 다양한 관리되는 레지스트리를 사용할 수 있습니다.

Docker Hub로 푸시하려면 사용자 또는 조직 이름으로 이미지 이름을 접두사로 지정합니다.

```console
docker tag stockdata myorg/stockdata
docker push myorg/stockdata
```

개인 레지스트리로 푸시하려면 레지스트리 호스트 이름과 조직 이름으로 이미지 이름을 접두사로 지정합니다.

```console
docker tag stockdata internal-registry:5000/myorg/stockdata
docker push internal-registry:5000/myorg/stockdata
```

이미지가 레지스트리에 있으면 개별 Docker 호스트 또는 Kubernetes와 같은 컨테이너 오케스트레이션 엔진에 이미지를 배포할 수 있습니다.

>[!div class="step-by-step"]
>[이전](self-hosted.md)
>[다음](kubernetes.md)
