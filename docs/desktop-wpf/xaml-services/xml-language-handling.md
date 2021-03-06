---
title: XAML의 xml:lang 처리
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
ms.openlocfilehash: b5a06adbb7cb874bc09899118f13b91fbec7a85e
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/27/2020
ms.locfileid: "81432709"
---
# <a name="xmllang-handling-in-xaml"></a>XAML의 xml:lang 처리

특성은 `xml:lang` XML의 요소에 대한 언어 및 문화문화 정보를 선언하는 XML 정의 특성입니다. XAML을 사용해도 특성의 의미가 동일하게 유지되지만, 일부 추가적인 고려 사항이 적용됩니다.

## <a name="xaml-attribute-usage"></a>XAML 특성 사용

```xaml
<object xml:lang="rfc3066lang" />
```

## <a name="xaml-values"></a>XAML 값

|||
|-|-|
|*rfc3066lang*|[RFC 3066](https://www.ietf.org/rfc/rfc3066.txt) 표준에서 파생되고 언어 또는 언어 영역을 식별하는 문자열입니다. 후자의 경우, 언어 및 지역이 단일 하이픈으로 구분됩니다. 값 및 형식에 대한 자세한 내용은 <xref:System.Windows.Markup.XmlLanguage> 를 참조하세요.|

## <a name="remarks"></a>설명

속성에 `xml:lang` 대한 [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] 정의는 XML에 `xml:lang` 대한 W3C(월드 와이드 웹 컨소시엄)에서 "특수 특성"으로 정의된 것으로부터 파생됩니다. 언어 및 문화권 정보는 구현에 따라 요소에서 다양한 방법으로 처리될 수 있습니다. 하지만 [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] 특성의 기본 `xml:lang` 처리는 없습니다.

`xml:lang` 특성의 기본값은 이 특성 수준의 빈 문자열입니다.

`xml:lang` 특성 효과 및 특성의 값은 일반적으로 `xml:lang` 값에 영향을 주는 시스템에서 해석될 때 자식 요소에 지속됩니다.

.NET XAML 서비스의 XAML 작성자가 `xml:lang` 해석할 <xref:System.Windows.Markup.XmlLanguage> 때 <xref:System.Globalization.CultureInfo> 값은 기본 개체 표현에서 만들거나 개체를 만들 수 있습니다. 그러나 해당 동작은 지정된 `xml:lang` 값이 해당 클래스에 대한 유효한 구성인지 여부에 따라 달라집니다.

프레임워크는 `xml:lang` 를 속성에 적용하여 프레임워크에서 정의된 속성과 <xref:System.Windows.Markup.XmlLangPropertyAttribute> 의 의미 사이에 연결을 XML 형식으로 만들 수 있습니다.

## <a name="wpf-usage-nodes"></a>WPF 사용 노드

<xref:System.Windows.FrameworkElement> 또는 <xref:System.Windows.FrameworkContentElement>의 파생 클래스인 요소의 경우, <xref:System.Windows.FrameworkElement.Language%2A> 특성의 해당되는 `xml:lang` 종속성 속성을 사용할 수 있습니다. 기본적으로, <xref:System.Windows.FrameworkElement.Language%2A> 속성은 이 속성 또는 `xml:lang` 특성 처리를 통해 달리 설정되지 않은 경우 "en-US"를 사용합니다.

## <a name="see-also"></a>참조

- [WPF의 전역화](../../framework/wpf/advanced/globalization-for-wpf.md)
