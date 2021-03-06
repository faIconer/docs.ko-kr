---
title: '방법: StatusBar 컨트롤에 패널 추가'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- panels [Windows Forms], status bars
- status bars [Windows Forms], adding panels
- StatusBar control [Windows Forms], adding panels
ms.assetid: 835e3902-288c-4c38-9d69-0696d8695009
ms.openlocfilehash: 386c8cae425c458ddf4c446a454ae4213761e651
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142201"
---
# <a name="how-to-add-panels-to-a-statusbar-control"></a>방법: StatusBar 컨트롤에 패널 추가
> [!IMPORTANT]
> 및 <xref:System.Windows.Forms.StatusStrip> <xref:System.Windows.Forms.ToolStripStatusLabel> 컨트롤을 대체하고 <xref:System.Windows.Forms.StatusBar> 및 <xref:System.Windows.Forms.StatusBarPanel> 컨트롤에 기능을 추가합니다. 그러나 <xref:System.Windows.Forms.StatusBar> 원하는 <xref:System.Windows.Forms.StatusBarPanel> 경우 이전 버전과의 호환성 및 향후 사용모두에 대해 및 컨트롤이 유지됩니다.  
  
 [StatusBar 제어](statusbar-control-windows-forms.md) 컨트롤 내의 프로그래밍 가능한 영역은 <xref:System.Windows.Forms.StatusBarPanel> 클래스의 인스턴스로 구성됩니다. 이러한 <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> 클래스에 추가를 통해 추가 됩니다.  
  
### <a name="to-add-panels-to-a-status-bar"></a>상태 표시줄에 패널을 추가하려면  
  
1. 절차에서 상태 표시줄 패널을 <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>에 추가하여 작성합니다. 속성을 통과한 인덱스를 사용하여 개별 패널에 <xref:System.Windows.Forms.StatusBar.Panels%2A> 대한 속성 설정을 지정합니다.  
  
     다음 코드 예제에서 아이콘위치에 대해 설정된 경로는 **내 문서** 폴더입니다. 이 위치는 Windows 운영 체제를 실행하는 대부분의 컴퓨터에 이 폴더가 포함된다고 가정할 수 있으므로 사용됩니다. 또한 이 위치를 선택하면 최소한의 시스템 액세스 수준을 가진 사용자가 응용 프로그램을 안전하게 실행할 수 있습니다. 다음 예제에서는 컨트롤이 <xref:System.Windows.Forms.StatusBar> 이미 추가된 양식이 필요합니다.  
  
    > [!NOTE]
    > 는 <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> 0 기반 컬렉션이므로 코드는 그에 따라 진행되어야 합니다.  
  
    ```vb  
    Public Sub CreateStatusBarPanels()  
    ' Create panels and set text property.  
       StatusBar1.Panels.Add("One")  
       StatusBar1.Panels.Add("Two")  
       StatusBar1.Panels.Add("Three")  
    ' Set properties of StatusBar panels.  
    ' Set AutoSize property of panels.  
       StatusBar1.Panels(0).AutoSize = StatusBarPanelAutoSize.Spring  
       StatusBar1.Panels(1).AutoSize = StatusBarPanelAutoSize.Contents  
       StatusBar1.Panels(2).AutoSize = StatusBarPanelAutoSize.Contents  
    ' Set BorderStyle property of panels.  
       StatusBar1.Panels(0).BorderStyle = StatusBarPanelBorderStyle.Raised  
       StatusBar1.Panels(1).BorderStyle = StatusBarPanelBorderStyle.Sunken  
       StatusBar1.Panels(2).BorderStyle = StatusBarPanelBorderStyle.Raised  
    ' Set Icon property of third panel. You should replace the bolded  
    ' icon in the sample below with an icon of your own choosing.  
       StatusBar1.Panels(2).Icon = New _
       System.Drawing.Icon(System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Icon.ico")  
       StatusBar1.ShowPanels = True  
    End Sub  
    ```  
  
    ```csharp  
    public void CreateStatusBarPanels()  
    {  
       // Create panels and set text property.  
       statusBar1.Panels.Add("One");  
       statusBar1.Panels.Add("Two");  
       statusBar1.Panels.Add("Three");  
       // Set properties of StatusBar panels.  
       // Set AutoSize property of panels.  
       statusBar1.Panels[0].AutoSize = StatusBarPanelAutoSize.Spring;  
       statusBar1.Panels[1].AutoSize = StatusBarPanelAutoSize.Contents;  
       statusBar1.Panels[2].AutoSize = StatusBarPanelAutoSize.Contents;  
       // Set BorderStyle property of panels.  
       statusBar1.Panels[0].BorderStyle =  
          StatusBarPanelBorderStyle.Raised;  
       statusBar1.Panels[1].BorderStyle = StatusBarPanelBorderStyle.Sunken;  
       statusBar1.Panels[2].BorderStyle = StatusBarPanelBorderStyle.Raised;  
       // Set Icon property of third panel. You should replace the bolded  
       // icon in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       statusBar1.Panels[2].Icon =
          new System.Drawing.Icon (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       + @"\Icon.ico");  
       statusBar1.ShowPanels = true;  
    }  
    ```  
  
    ```cpp  
    public:  
       void CreateStatusBarPanels()  
       {  
          // Create panels and set text property.  
          statusBar1->Panels->Add("One");  
          statusBar1->Panels->Add("Two");  
          statusBar1->Panels->Add("Three");  
          // Set properties of StatusBar panels.  
          // Set AutoSize property of panels.  
          statusBar1->Panels[0]->AutoSize =  
             StatusBarPanelAutoSize::Spring;  
          statusBar1->Panels[1]->AutoSize =  
             StatusBarPanelAutoSize::Contents;  
          statusBar1->Panels[2]->AutoSize =  
             StatusBarPanelAutoSize::Contents;  
          // Set BorderStyle property of panels.  
          statusBar1->Panels[0]->BorderStyle =  
             StatusBarPanelBorderStyle::Raised;  
          statusBar1->Panels[1]->BorderStyle =  
             StatusBarPanelBorderStyle::Sunken;  
          statusBar1->Panels[2]->BorderStyle =  
             StatusBarPanelBorderStyle::Raised;  
          // Set Icon property of third panel.  
          // You should replace the bolded image
          // in the sample below with an icon of your own choosing.  
          statusBar1->Panels[2]->Icon =  
             gcnew System::Drawing::Icon(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Icon.ico"));  
          statusBar1->ShowPanels = true;  
       }  
    ```  
  
## <a name="see-also"></a>참고 항목

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [컬렉션 편집기 대화 상자](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/xc4yyekt(v=vs.100))
- [방법: 상태 표시줄 패널의 크기 설정](how-to-set-the-size-of-status-bar-panels.md)
- [연습: 런타임에 상태 표시줄 정보 업데이트](walkthrough-updating-status-bar-information-at-run-time.md)
- [방법: Windows Forms StatusBar 컨트롤에서 클릭한 패널 확인](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [StatusBar 컨트롤 개요](statusbar-control-overview-windows-forms.md)
