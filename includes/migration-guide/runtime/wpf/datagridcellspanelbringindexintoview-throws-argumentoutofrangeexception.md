---
ms.openlocfilehash: d78d083b16ac034c6c393dbc0f6094ee4c6c63c0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622374"
---
### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a>DataGridCellsPanel.BringIndexIntoView가 ArgumentOutOfRangeException을 throw합니다.

#### <a name="details"></a>세부 정보

<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)>는 열 가상화가 활성화되었지만 열 너비가 아직 결정되지 않았을 때 비동기적으로 작동합니다.  비동기 작업이 실행되기 전에 열이 제거되면 <xref:System.ArgumentOutOfRangeException?displayProperty=fullName>이 발생할 수 있습니다.

#### <a name="suggestion"></a>제안 해결 방법

다음 중 하나:<ol><li>NET Framework 4.7로 업그레이드합니다.</li><li>.NET Framework 4.6.2에 대한 최신 서비스 패치를 설치합니다.</li><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)>에 대한 비동기 응답이 완료될 때까지 열이 제거되지 않도록 합니다.</li></ol>

| 이름    | 값       |
|:--------|:------------|
| Scope   |Microsoft Edge|
|버전|4.6.2|
|형식|런타임

#### <a name="affected-apis"></a>영향을 받는 API

-<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType></li></ul>|
