---
ms.openlocfilehash: a1db9916c69c5974191eb6108fb54a0d9ff060d2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622137"
---
### <a name="sqlconnectionopen-fails-on-windows-7-with-non-ifs-winsock-bsp-or-lsp-present"></a>비 IFS Winsock BSP 또는 LSP가 있는 Windows 7에서 SqlConnection.Open이 실패합니다.

#### <a name="details"></a>설명

비 IFS Winsock BSP 또는 LSP가 있는 Windows 7 컴퓨터에서 실행 중인 .NET Framework 4.5에서 <xref:System.Data.SqlClient.SqlConnection.Open> 및 <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)>가 실패합니다. 비 IFS BSP 또는 LSP가 설치되어 있는지 여부를 확인하려면 <code>netsh WinSock Show Catalog</code> 명령을 사용하고 반환되는 모든 <code>Winsock Catalog Provider Entry</code> 항목을 검사합니다. 서비스 플래그 값이 <code>0x20000</code> 비트 집합을 가진 경우, 공급자는 IFS 핸들을 사용하고 올바르게 작동합니다. <code>0x20000</code> 비트가 지우기인 경우(집합 아님) 비 IFS BSP 또는 LSP입니다.

#### <a name="suggestion"></a>제안 해결 방법

이 버그는 .NET Framework 4.5.2에서 수정되었으므로 .NET Framework를 업그레이드하여 방지할 수 있습니다. 또는 설치된 모든 비 IFS Winsock LSP를 제거하여 방지할 수 있습니다.

| 이름    | 값       |
|:--------|:------------|
| Scope   |부|
|버전|4.5|
|형식|런타임

#### <a name="affected-apis"></a>영향을 받는 API

-<xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|
