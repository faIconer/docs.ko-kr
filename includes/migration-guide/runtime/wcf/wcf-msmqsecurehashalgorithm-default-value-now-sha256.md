---
ms.openlocfilehash: ccdf232d743c9e270b6ed21f698998eb95a97399
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621218"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a>WCF MsmqSecureHashAlgorithm 기본값은 이제 SHA256입니다.

#### <a name="details"></a>설명

.NET Framework 4.7.1부터 Msmq 메시지에 대한 WCF의 기본 메시지 서명 알고리즘은 SHA256입니다. .NET Framework 4.7 및 이전 버전에서 기본 메시지 서명 알고리즘은 SHA1입니다.

#### <a name="suggestion"></a>제안 해결 방법

.NET Framework 4.7.1 이상에서 이러한 변경 내용과의 호환성 문제가 발생하면 app.config 파일의 <code>&lt;runtime&gt;</code> 섹션에 다음 줄을 추가하여 변경 내용을 옵트아웃할 수 있습니다.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| 이름    | 값       |
|:--------|:------------|
| Scope   |부|
|버전|4.7.1|
|형식|런타임|
