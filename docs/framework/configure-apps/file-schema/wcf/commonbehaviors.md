---
title: <commonBehaviors>
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: 73bf759fd3dfa87398aa74de93160a4ffce08eba
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2020
ms.locfileid: "61704364"
---
# \<commonBehaviors>
`commonBehaviors` 섹션은 machine.config 파일에만 정의할 수 있습니다. 이 섹션은 두 자식 컬렉션 `endpointBehaviors` 및 `serviceBehaviors`를 정의합니다.  각 컬렉션은 컴퓨터의 모든 WCF 끝점과 서비스에서 사용 하는 동작 요소를 각각 정의 합니다. `endpointBehaviors`에 정의된 동작은 클라이언트에만 적용되고 `serviceBehaviors`에 정의된 동작은 서비스에만 적용됩니다. 두 `commonBehaviors` 및 `behaviors` 섹션 모두에서 동작이 정의되는 경우 `behaviors` 섹션의 동작이 우선합니다.
