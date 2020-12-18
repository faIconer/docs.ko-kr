---
title: "&gt;= 연산자(C# 참조)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '>=_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- greater than or equal to operator (>=) [C#]
- '>= operator [C#]'
ms.assetid: 0db4dcaf-56a3-4884-a7ad-35f64978a58d
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 59b134ce1e1169b0a5f4583374148d39ceb8326a
ms.contentlocale: ko-kr
ms.lasthandoff: 07/28/2017

---
# <a name="gt-operator-c-reference"></a>&gt;= 연산자(C# 참조)
모든 숫자 형식과 열거형은 첫 번째 피연산자가 두 번째 피연산자보다 크거나 같을 경우에 `true`를 반환하고, 그렇지 않으면 `false`를 반환하는 “크거나 같음" 관계 연산자(`>=`)를 정의합니다.  
  
## <a name="remarks"></a>설명  
 사용자 정의 형식은 `>=` 연산자를 오버로드할 수 있습니다. 자세한 내용은 [operator](../../../csharp/language-reference/keywords/operator.md)를 참조하세요. `>=` 연산자가 오버로드되면 [<=](../../../csharp/language-reference/operators/less-than-equal-operator.md) 또한 오버로드되어야 합니다. 정수 형식에 대한 연산은 일반적으로 열거형에서 허용됩니다.  
  
## <a name="example"></a>예제  
 [!code-cs[csRefOperators#39](../../../csharp/language-reference/operators/codesnippet/CSharp/greater-than-equal-operator_1.cs)]  
  
## <a name="see-also"></a>참고 항목  
 [C# 참조](../../../csharp/language-reference/index.md)   
 [C# 프로그래밍 가이드](../../../csharp/programming-guide/index.md)   
 [C# 연산자](../../../csharp/language-reference/operators/index.md)
