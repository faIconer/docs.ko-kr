---
title: ISymUnmanagedScope2 인터페이스
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2
helpviewer_keywords:
- ISymUnmanagedScope2 interface [.NET Framework debugging]
ms.assetid: 2ed6a387-ba45-483e-9a1e-b0c69f67998b
topic_type:
- apiref
ms.openlocfilehash: 886ba693183a6b99eb03635e95a9661d105de40e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610862"
---
# <a name="isymunmanagedscope2-interface"></a>ISymUnmanagedScope2 인터페이스
메서드 내의 어휘 범위를 나타냅니다. 이 인터페이스는 범위 내에 정의 된 상수에 대 한 정보를 가져오는 메서드로 [ISymUnmanagedScope](isymunmanagedscope-interface.md) 인터페이스를 확장 합니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[GetConstantCount 메서드](isymunmanagedscope2-getconstantcount-method.md)|이 범위 내에 정의 된 상수의 수를 가져옵니다.|  
|[GetConstants 메서드](isymunmanagedscope2-getconstants-method.md)|이 범위 내에 정의 된 지역 상수를 가져옵니다.|  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** CorSym, CorSym  
  
## <a name="see-also"></a>참고 항목

- [진단 기호 저장소 인터페이스](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedScope 인터페이스](isymunmanagedscope-interface.md)
