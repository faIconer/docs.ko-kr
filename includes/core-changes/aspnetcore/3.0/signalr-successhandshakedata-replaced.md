---
ms.openlocfilehash: fa0f54404d1e14afa6ce48a425c984a48498a1ee
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393958"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a>SignalR: HandshakeProtocol.SuccessHandshakeData가 대체됨

[HandshakeProtocol.SuccessHandshakeData](https://github.com/aspnet/AspNetCore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) 필드가 제거되었으며 특정 `IHubProtocol`에 제공된 성공적인 핸드셰이크 응답을 생성하는 도우미 메서드로 대체되었습니다. 

#### <a name="version-introduced"></a>도입된 버전

3.0

#### <a name="old-behavior"></a>이전 동작

`HandshakeProtocol.SuccessHandshakeData`는 `public static ReadOnlyMemory<byte>` 필드입니다.

#### <a name="new-behavior"></a>새 동작

`HandshakeProtocol.SuccessHandshakeData`는 지정된 프로토콜을 기반으로 `ReadOnlyMemory<byte>`를 반환하는 `static` `GetSuccessfulHandshake(IHubProtocol protocol)` 메서드로 대체되었습니다. 

#### <a name="reason-for-change"></a>변경 이유

비상수이며 선택된 프로토콜에 따라 변경되는 추가 필드가 핸드셰이크 _응답_에 추가되었습니다.

#### <a name="recommended-action"></a>권장 작업

없음 이 형식은 사용자 코드에서 사용하도록 설계되지 않았습니다. `public`이기 때문에 SignalR 서버와 클라이언트 간에 공유할 수 있습니다. .NET으로 작성된 고객 SignalR 클라이언트에서도 사용할 수 있습니다. SignalR의 **사용자**는 이 변경 내용의 영향을 받지 않아야 합니다.

#### <a name="category"></a>범주

ASP.NET Core

#### <a name="affected-apis"></a>영향을 받는 API

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=namewithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->