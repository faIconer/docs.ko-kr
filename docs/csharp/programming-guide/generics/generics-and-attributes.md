---
title: 제네릭 및 특성 - C# 프로그래밍 가이드
description: 제네릭 형식에 특성을 적용하는 방법을 알아봅니다. 코드 예제를 살펴보고 사용 가능한 추가 리소스를 확인합니다.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 17556af2e1bc2963de953cea242d7000509acbcd
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299879"
---
# <a name="generics-and-attributes-c-programming-guide"></a>제네릭 및 특성(C# 프로그래밍 가이드)
제네릭 형식에 특성을 적용하는 방법은 제네릭이 아닌 형식의 경우와 동일합니다. 특성 적용에 대한 자세한 내용은 [특성](../concepts/attributes/index.md)을 참조하세요.  
  
 사용자 지정 특성은 형식 인수가 제공되지 않는 개방형 제네릭 형식 및 모든 형식 매개 변수에 인수를 제공하는 폐쇄형으로 생성된 제네릭 형식만 참조할 수 있습니다.  
  
 다음 예에서는 이러한 사용자 지정 특성을 사용합니다.  
  
 [!code-csharp[csProgGuideGenerics#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#48)]  
  
 특성은 개방형 제네릭 형식을 참조할 수 있습니다.  
  
 [!code-csharp[csProgGuideGenerics#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#49)]  
  
 적절한 수의 쉼표를 사용하여 여러 형식 매개 변수를 지정합니다. 이 예제에서 `GenericClass2`는 두 개의 형식 매개 변수를 가집니다.  
  
 [!code-csharp[csProgGuideGenerics#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#50)]  
  
 특성은 폐쇄형으로 생성된 제네릭 형식을 참조할 수 있습니다.  
  
 [!code-csharp[csProgGuideGenerics#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#51)]  
  
 제네릭 형식 매개 변수를 참조하는 특성은 컴파일 시간 오류를 발생시킵니다.  
  
 [!code-csharp[csProgGuideGenerics#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#52)]  
  
 제네릭 형식은 <xref:System.Attribute>에서 상속할 수 없습니다.  
  
 [!code-csharp[csProgGuideGenerics#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#53)]  
  
 런타임에 제네릭 형식 또는 형식 매개 변수에 대한 정보를 얻으려면 <xref:System.Reflection>의 메서드를 사용합니다. 자세한 내용은 [제네릭 및 리플렉션](./generics-and-reflection.md)을 참조하세요.  
  
## <a name="see-also"></a>참고 항목

- [C# 프로그래밍 가이드](../index.md)
- [제네릭](./index.md)
- [특성](../../../standard/attributes/index.md)
