---
ms.openlocfilehash: 424e8ff704b888aa3d2c1254ac712da4034f59b8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616119"
---
### <a name="obsoleteattribute-exports-as-both-obsoleteattribute-and-deprecatedattribute-in-winmd-scenarios"></a>ObsoleteAttribute가 WinMD 시나리오에서 ObsoleteAttribute와 DeprecatedAttribute를 내보냄

#### <a name="details"></a>설명

Windows 메타데이터 라이브러리(.winmd 파일)를 만들 때 <xref:System.ObsoleteAttribute?displayProperty=fullName> 특성은 <xref:System.ObsoleteAttribute?displayProperty=fullName> 및 [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute)로서 내보내집니다.

#### <a name="suggestion"></a>제안 해결 방법

<xref:System.ObsoleteAttribute?displayProperty=fullName> 특성이 사용된 기존 소스 코드를 다시 컴파일하면 C++/CX 또는 JavaScript의 해당 코드가 사용될 때 경고가 발생할 수 있습니다. <xref:System.ObsoleteAttribute?displayProperty=fullName> 및 [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute) 모두를 관리되는 어셈블리의 코드에 적용하는 것은 좋지 않습니다. 빌드 경고가 발생할 수 있습니다.

| 이름    | 값       |
|:--------|:------------|
| Scope   | Microsoft Edge        |
| 버전 | 4.5.1       |
| 형식    | 대상 변경 |
