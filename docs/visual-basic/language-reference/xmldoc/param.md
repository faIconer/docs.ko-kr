---
title: <param>
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: d325d5f9fbfd132630cf280653be214a267a7a80
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400062"
---
# <a name="param-visual-basic"></a>\<param>(Visual Basic)
매개 변수 이름 및 설명을 정의 합니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a>매개 변수  
 `name`  
 메서드 매개 변수의 이름입니다. 이름을 큰따옴표(“ ”)로 묶습니다.  
  
 `description`  
 매개 변수에 대한 설명입니다.  
  
## <a name="remarks"></a>설명  
 태그는 메서드에 `<param>` 대 한 매개 변수 중 하나를 설명 하기 위해 메서드 선언의 주석에서 사용 되어야 합니다.  
  
 태그에 대 한 텍스트는 `<param>` 다음 위치에 표시 됩니다.  
  
- IntelliSense의 매개 변수 정보입니다. 자세한 내용은 [Using IntelliSense](/visualstudio/ide/using-intellisense)을 참조하세요.  
  
- 개체 브라우저. 자세한 내용은 [코드 구조 보기](/visualstudio/ide/viewing-the-structure-of-code)를 참조 하세요.  
  
 [-Doc](../../reference/command-line-compiler/doc.md) 로 컴파일하여 문서 주석을 파일로 처리 합니다.  
  
## <a name="example"></a>예제  
 이 예제에서는 태그를 사용 하 여 `<param>` 매개 변수를 설명 합니다 `id` .  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>참고 항목

- [XML 주석 태그](index.md)
