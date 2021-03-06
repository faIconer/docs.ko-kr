---
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
ms.openlocfilehash: 52ef0b991554c800dba4320b0c64c81ddd1b0ff4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414287"
---
# <a name="-win32icon"></a>-win32icon
출력 파일에 .ico 파일을 삽입합니다. 이 .ico 파일은 **파일 탐색기**에서 출력 파일을 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a>인수  
  
|용어|정의|  
|---|---|  
|`filename`|출력 파일에 추가할 .ico 파일입니다. 공백이 있으면 파일 이름을 따옴표(" ")로 묶습니다.|  
  
## <a name="remarks"></a>설명  
 Microsoft Windows RC(리소스 컴파일러)를 사용하여 .ico 파일을 만들 수 있습니다. 리소스 컴파일러는 Visual C++ 프로그램을 컴파일할 때 호출됩니다. .iso 파일은 .rc 파일에서 만들어집니다. `-win32icon` 및 `-win32resource` 옵션은 함께 사용할 수 없습니다.  
  
 .NET Framework 리소스 파일 또는 [-resource (Visual Basic)](resource.md)를 참조하여 .NET Framework 리소스 파일을 연결하려면 [-linkresource(Visual Basic)](linkresource.md)를 참조하세요. .res 파일을 가져오려면 [-win32resource](win32resource.md)를 참조하세요.  
  
|Visual Studio IDE에서 -win32icon을 설정하려면 다음을 수행합니다.|  
|---|  
|1.  **솔루션 탐색기**에서 프로젝트를 선택합니다. **프로젝트** 메뉴에서 **속성**을 클릭합니다. <br />2.  **애플리케이션** 탭을 클릭합니다.<br />3.  **아이콘** 상자에서 값을 수정합니다.|  
  
## <a name="example"></a>예제  
 다음 코드에서는 `In.vb`를 컴파일하고 .ico 파일 `Rf.ico`를 연결합니다.  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a>참조

- [Visual Basic 명령줄 컴파일러](index.md)
- [샘플 컴파일 명령줄](sample-compilation-command-lines.md)
