---
title: OpenFileDialog 구성 요소 개요
ms.date: 03/30/2017
f1_keywords:
- OpenFileDialog
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], about OpenFileDialog
- Open File dialog box [Windows Forms], displaying in Windows Forms
ms.assetid: cd717300-46b6-4f82-8207-b218fa7fa407
ms.openlocfilehash: c519b373150a49ee41dbb0c503f7d5a4862477d5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728441"
---
# <a name="openfiledialog-component-overview-windows-forms"></a>OpenFileDialog 구성 요소 개요(Windows Forms)

Windows Forms <xref:System.Windows.Forms.OpenFileDialog> 구성 요소는 미리 구성된 대화 상자입니다. Windows 운영 체제에서 제공 하는 동일한 **파일 열기** 대화 상자입니다. <xref:System.Windows.Forms.CommonDialog> 클래스에서 상속됩니다.

## <a name="use-this-component"></a>이 구성 요소 사용

사용자 고유의 대화 상자를 구성 하는 대신 Windows 기반 응용 프로그램 내에서이 구성 요소를 파일 선택을 위한 간단한 솔루션으로 사용 합니다. 표준 Windows 대화 상자를 사용하여 기본 기능이 사용자에게 익숙한 애플리케이션을 만듭니다. 그러나 <xref:System.Windows.Forms.OpenFileDialog> 구성 요소를 사용 하는 경우 고유한 파일 열기 논리를 작성 해야 합니다.

런타임에 대화 상자를 표시 하려면 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 메서드를 사용 합니다. 사용자가 <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A> 속성을 사용 하 여 파일을 여러 개 선택할 수 있도록 설정할 수 있습니다. 또한 <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> 속성을 사용 하 여 대화 상자에 읽기 전용 확인란이 나타나는지 확인할 수 있습니다. <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> 속성은 읽기 전용 확인란이 선택 되었는지 여부를 나타냅니다. 마지막으로 <xref:System.Windows.Forms.FileDialog.Filter%2A> 속성은 대화 상자에서 "파일 형식" 상자에 표시 되는 항목을 결정 하는 현재 파일 이름 필터 문자열을 설정 합니다.

폼에 추가 되 면 <xref:System.Windows.Forms.OpenFileDialog> 구성 요소가 Visual Studio의 Windows Forms 디자이너 아래쪽에 있는 트레이에 표시 됩니다.

## <a name="see-also"></a>참고 항목

- <xref:System.Windows.Forms.OpenFileDialog>
- [OpenFileDialog 구성 요소](openfiledialog-component-windows-forms.md)
