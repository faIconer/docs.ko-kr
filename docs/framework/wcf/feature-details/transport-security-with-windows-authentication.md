---
title: Windows 인증을 사용하는 전송 보안
description: Windows 보안으로 보호 되는 WCF 클라이언트/서비스를 보여 주는이 시나리오를 검토 합니다. 이 예제에서 인트라넷 서비스는 인적 자원 정보를 표시 합니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
ms.openlocfilehash: b6134d4cbdff0c1adea704a7f3aaff7e40fd75ec
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244766"
---
# <a name="transport-security-with-windows-authentication"></a>Windows 인증을 사용하는 전송 보안
다음 시나리오에서는 Windows 보안에 의해 보호 되는 WCF (Windows Communication Foundation) 클라이언트 및 서비스를 보여 줍니다. 프로그래밍에 대 한 자세한 내용은 [방법: Windows 자격 증명을 사용 하 여 서비스 보호](../how-to-secure-a-service-with-windows-credentials.md)를 참조 하세요.  
  
 인트라넷 웹 서비스는 인사 정보를 표시합니다. 클라이언트는 Windows Form 애플리케이션입니다. 애플리케이션은 도메인을 보호하는 Kerberos 컨트롤러와 함께 도메인에 배포됩니다.  
  
 ![Windows 인증을 사용하는 전송 보안](./media/transport-security-with-windows-authentication/secured-windows-authentication.gif)  
  
|특성|Description|  
|--------------------|-----------------|  
|보안 모드|전송|  
|상호 운용성|WCF만|  
|인증(서버)<br /><br /> 인증(클라이언트)|예, Windows 통합 인증을 사용합니다.<br /><br /> 예, Windows 통합 인증을 사용합니다.|  
|무결성|Yes|  
|기밀성|Yes|  
|전송|NET.TCP|  
|바인딩|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a>서비스  
 다음 코드와 구성은 독립적으로 실행되어야 합니다. 다음 중 하나를 수행합니다.  
  
- 구성 없이 코드를 사용하여 독립 실행형 서비스를 만듭니다.  
  
- 제공된 구성을 사용하여 서비스를 만들지만 엔드포인트를 정의하지 않습니다.  
  
### <a name="code"></a>코드  
 다음 코드에서는 Windows 보안을 사용하는 서비스 엔드포인트를 만드는 방법을 보여 줍니다.  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a>Configuration  
 다음 구성은 서비스 엔드포인트를 설정하는 데 코드 대신 사용할 수 있습니다.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"
                  binding="netTcpBinding"  
          bindingConfiguration="WindowsClientOverTcp"
                  name="WindowsClientOverTcp"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="WindowsClientOverTcp">  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>Client  
 다음 코드와 구성은 독립적으로 실행되어야 합니다. 다음 중 하나를 수행합니다.  
  
- 이 코드와 클라이언트 코드를 사용하여 독립 실행형 클라이언트를 만듭니다.  
  
- 엔드포인트 주소를 정의하지 않는 클라이언트를 만듭니다. 대신 구성 이름을 인수로 사용하는 클라이언트 생성자를 사용합니다. 예를 들어:  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>코드  
 다음 코드에서는 클라이언트를 만듭니다. 바인딩은 TCP 전송과 함께 클라이언트 자격 증명 형식이 Windows로 설정된 전송 모드 보안을 사용하도록 구성됩니다.  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a>Configuration  
 다음 구성은 클라이언트를 만드는 데 코드 대신 사용할 수 있습니다.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://localhost:8008/Calculator"
                binding="netTcpBinding"
                bindingConfiguration="NetTcpBinding_ICalculator"
                contract="ICalculator"  
                name="NetTcpBinding_ICalculator">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>참고 항목

- [보안 개요](security-overview.md)
- [방법: Windows 자격 증명을 사용하여 서비스 보호](../how-to-secure-a-service-with-windows-credentials.md)
- [Windows Server AppFabric 보안 모델](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
