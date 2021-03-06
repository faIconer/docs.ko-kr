---
title: 중첩된 Graphics 컨테이너 사용
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], nested containers
- graphics [Windows Forms], clipping
- graphics [Windows Forms], transformations in nested objects
ms.assetid: a0d9f178-43a4-4323-bb5a-d3e3f77ae6c1
ms.openlocfilehash: 460ebb37ee62691a1e282f756840121fd378ebd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182473"
---
# <a name="using-nested-graphics-containers"></a>중첩된 Graphics 컨테이너 사용
GDI+는 개체에서 상태의 일부를 일시적으로 바꾸거나 보강하는 <xref:System.Drawing.Graphics> 데 사용할 수 있는 컨테이너를 제공합니다. 개체의 메서드를 <xref:System.Drawing.Graphics.BeginContainer%2A> 호출 하 <xref:System.Drawing.Graphics> 여 컨테이너를 만듭니다. 반복적으로 호출하여 <xref:System.Drawing.Graphics.BeginContainer%2A> 중첩된 컨테이너를 형성할 수 있습니다. 에 대한 <xref:System.Drawing.Graphics.BeginContainer%2A> 각 호출은 <xref:System.Drawing.Graphics.EndContainer%2A>에 대한 호출과 페어링되어야 합니다.  
  
## <a name="transformations-in-nested-containers"></a>중첩 된 컨테이너의 변환  
 다음 예제는 <xref:System.Drawing.Graphics> 해당 <xref:System.Drawing.Graphics> 개체 내에 개체와 컨테이너를 만듭니다. 객체의 <xref:System.Drawing.Graphics> 세계 변환은 x 방향의 변환 100 단위와 y 방향으로 80 단위입니다. 컨테이너의 세계 변환은 30도 회전입니다. 코드는 호출을 `DrawRectangle(pen, -60, -30, 120, 60)` 두 번 만듭니다. 첫 번째 <xref:System.Drawing.Graphics.DrawRectangle%2A> 호출은 컨테이너 내부에 있습니다. 즉, 호출이 호출 <xref:System.Drawing.Graphics.BeginContainer%2A> <xref:System.Drawing.Graphics.EndContainer%2A>과 사이의 통화 사이에 있습니다. 두 번째 <xref:System.Drawing.Graphics.DrawRectangle%2A> 호출은 에 <xref:System.Drawing.Graphics.EndContainer%2A>대한 호출 후입니다.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.MiscLegacyTopics#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#61)]  
  
 앞의 코드에서 컨테이너 내부에서 가져온 사각형은 먼저 컨테이너의 월드 변환(회전)에 의해 변환된 다음 <xref:System.Drawing.Graphics> 객체의 월드 변환(번역)에 의해 변환됩니다. 컨테이너 외부에서 가져온 사각형은 <xref:System.Drawing.Graphics> 객체의 월드 변환(변환)에 의해서만 변환됩니다. 다음 그림에서는 두 사각형을 보여 주십을 보여 주십습니다.
  
 ![중첩된 컨테이너를 보여 주는 그림입니다.](./media/using-nested-graphics-containers/nested-containers-illustration.png)  
  
## <a name="clipping-in-nested-containers"></a>중첩 컨테이너에서 클리핑  
 다음 예제에서는 중첩된 컨테이너가 클리핑 영역을 처리하는 방법을 보여 줍니다. 코드는 해당 <xref:System.Drawing.Graphics> <xref:System.Drawing.Graphics> 개체 내에 개체와 컨테이너를 만듭니다. <xref:System.Drawing.Graphics> 개체의 클리핑 영역은 사각형이고 컨테이너의 클리핑 영역은 타원입니다. 코드는 메서드를 두 <xref:System.Drawing.Graphics.DrawLine%2A> 번 호출합니다. 첫 번째 <xref:System.Drawing.Graphics.DrawLine%2A> 호출은 컨테이너 내부에 있으며 두 <xref:System.Drawing.Graphics.DrawLine%2A> 번째 호출은 호출 <xref:System.Drawing.Graphics.EndContainer%2A>후 컨테이너 외부에 있습니다. 첫 번째 선은 두 클리핑 영역의 교차점에 의해 잘립니다. 두 번째 줄은 <xref:System.Drawing.Graphics> 오브젝트의 직사각형 클리핑 영역에 의해서만 잘립니다.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#62](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#62)]
 [!code-vb[System.Drawing.MiscLegacyTopics#62](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#62)]  
  
 다음 그림에서는 잘린 두 줄을 보여 주었습니다.
  
 ![잘린 선이 있는 중첩 된 컨테이너를 보여 주는 그림입니다.](./media/using-nested-graphics-containers/nested-container-clipped-lines.png)  
  
 앞의 두 예제에서 볼 수 있듯이 변환 및 클리핑 영역은 중첩된 컨테이너에서 누적됩니다. 컨테이너와 <xref:System.Drawing.Graphics> 개체의 월드 변환을 설정하면 컨테이너 내부에서 가져온 항목에 두 변환이 모두 적용됩니다. 컨테이너의 변환이 먼저 적용되고 개체의 변환이 <xref:System.Drawing.Graphics> 두 번째로 적용됩니다. 컨테이너와 <xref:System.Drawing.Graphics> 오브젝트의 클리핑 영역을 설정하면 컨테이너 내부에서 가져온 항목은 두 클리핑 영역의 교차점에 의해 잘립니다.  
  
## <a name="quality-settings-in-nested-containers"></a>중첩 컨테이너의 품질 설정  
 중첩된<xref:System.Drawing.Graphics.SmoothingMode%2A> <xref:System.Drawing.Graphics.TextRenderingHint%2A>컨테이너의 품질 설정(, 및 등)은 누적되지 않습니다. 오히려 컨테이너의 품질 설정이 개체의 품질 <xref:System.Drawing.Graphics> 설정을 일시적으로 대체합니다. 새 컨테이너를 만들 때 해당 컨테이너의 품질 설정은 기본값으로 설정됩니다. 예를 <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>들어, 의 <xref:System.Drawing.Graphics> 스무딩 모드가 있는 오브젝트가 있다고 가정합니다. 컨테이너를 만들 때 컨테이너 내부의 스무딩 모드는 기본 스무딩 모드입니다. 컨테이너의 스무딩 모드를 자유롭게 설정할 수 있으며 컨테이너 내부에서 가져온 모든 항목은 설정한 모드에 따라 그려집니다. 호출 <xref:System.Drawing.Graphics.EndContainer%2A> 후 그려진 항목은 호출 전에 제자리에 있던<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>스무딩 모드()에 <xref:System.Drawing.Graphics.BeginContainer%2A>따라 그려집니다.  
  
## <a name="several-layers-of-nested-containers"></a>중첩 된 컨테이너의 여러 레이어  
 개체의 하나의 컨테이너로 <xref:System.Drawing.Graphics> 제한되지 않습니다. 앞의 컨테이너에 각각 중첩된 컨테이너 시퀀스를 만들 수 있으며, 중첩된 각 컨테이너의 월드 변환, 클리핑 영역 및 품질 설정을 지정할 수 있습니다. 가장 안쪽 컨테이너 내부에서 그리기 메서드를 호출하는 경우 가장 안쪽 컨테이너에서 시작하여 가장 바깥쪽 컨테이너로 끝나는 변환이 순서대로 적용됩니다. 가장 안쪽 컨테이너 내부에서 가져온 항목은 모든 클리핑 영역의 교차점에 의해 잘립니다.  
  
 다음 예제에서 <xref:System.Drawing.Graphics> 개체를 만들고 텍스트 렌더링 <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>힌트를 으로 설정합니다. 코드는 두 개의 컨테이너를 만들고 하나는 다른 컨테이너 내에 중첩됩니다. 외부 컨테이너의 텍스트 렌더링 힌트가 <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>로 설정되고 내부 컨테이너의 텍스트 <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>렌더링 힌트가 로 설정됩니다. 코드는 내부 컨테이너에서 하나, 외부 컨테이너에서 문자열, 개체 자체에서 <xref:System.Drawing.Graphics> 하나씩 세 개의 문자열을 그립니다.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#63](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#63)]
 [!code-vb[System.Drawing.MiscLegacyTopics#63](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#63)]  
  
 다음 그림에서는 세 개의 문자열을 보여 주시고 있습니다. 내부 컨테이너와 <xref:System.Drawing.Graphics> 오브젝트에서 가져온 문자열은 안티 앨리어싱으로 부드럽게 처리됩니다. <xref:System.Drawing.Graphics.TextRenderingHint%2A> 외부 컨테이너에서 가져온 문자열은 속성이 로 설정되어 있으므로 안티 앨리어싱으로 <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>부드럽게 처리되지 않습니다.  
  
 ![중첩된 컨테이너에서 가져온 문자열을 보여 주는 그림입니다.](./media/using-nested-graphics-containers/nested-containers-three-strings.png)  
  
## <a name="see-also"></a>참고 항목

- <xref:System.Drawing.Graphics>
- [Graphics 개체의 상태 관리](managing-the-state-of-a-graphics-object.md)
