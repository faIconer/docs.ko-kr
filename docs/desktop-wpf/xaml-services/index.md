---
title: XAML 서비스
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], System.Xaml concepts
- XAML Services in WPF [XAML Services]
- System.Xaml [XAML Services], conceptual documentation
ms.assetid: 0e11f386-808c-4eae-9ba6-029ad7ba2211
ms.openlocfilehash: bfb3efb479668bcd70a3ce87b80253a73c18bb51
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/27/2020
ms.locfileid: "85840290"
---
# <a name="xaml-services"></a><span data-ttu-id="96cbf-102">XAML 서비스</span><span class="sxs-lookup"><span data-stu-id="96cbf-102">XAML Services</span></span>

<span data-ttu-id="96cbf-103">이 항목에서는 .NET XAML 서비스라는 기술 세트의 기능을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-103">This topic describes the capabilities of a technology set known as .NET XAML Services.</span></span> <span data-ttu-id="96cbf-104">설명하는 대다수 서비스 및 API는 `System.Xaml` 어셈블리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-104">The majority of the services and APIs described are located in the assembly `System.Xaml`.</span></span> <span data-ttu-id="96cbf-105">서비스로는 판독기와 작성기, 스키마 클래스 및 스키마 지원, 팩터리, 클래스 특성 설정, XAML 언어 내장 지원 및 기타 XAML 언어 기능 등이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-105">Services include readers and writers, schema classes and schema support, factories, attributing of classes, XAML language intrinsic support, and other XAML language features.</span></span>

## <a name="about-this-documentation"></a><span data-ttu-id="96cbf-106">설명서 정보</span><span class="sxs-lookup"><span data-stu-id="96cbf-106">About This Documentation</span></span>

<span data-ttu-id="96cbf-107">.NET XAML 서비스의 개념 설명서는 이전에 XAML 언어를 사용한 적이 있고 이 언어가 WPF(Windows Presentation Foundation) 또는 Windows Workflow Foundation과 같은 특정 프레임워크나 <xref:Microsoft.Build.Framework.XamlTypes>의 빌드 사용자 지정 기능과 같은 특정 기술 기능 영역에 적용되는 방법을 알고 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-107">Conceptual documentation for .NET XAML Services assumes that you have previous experience with the XAML language and how it might apply to a specific framework, for example Windows Presentation Foundation (WPF) or Windows Workflow Foundation, or a specific technology feature area, for example the build customization features in <xref:Microsoft.Build.Framework.XamlTypes>.</span></span> <span data-ttu-id="96cbf-108">이 설명서에서는 XAML의 기본 사항을 태그 언어, XAML 구문 용어 또는 기타 소개 자료로 기술하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-108">This documentation does not attempt to explain the basics of XAML as a markup language, XAML syntax terminology, or other introductory material.</span></span> <span data-ttu-id="96cbf-109">대신, 이 설명서는 System.Xaml 어셈블리 라이브러리에서 사용하도록 설정된 .NET XAML 서비스의 사용에 특별히 초점을 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-109">Instead, this documentation focuses on specifically using .NET XAML Services that are enabled in the System.Xaml assembly library.</span></span> <span data-ttu-id="96cbf-110">이 API의 대부분은 XAML 언어 통합 및 확장성 시나리오에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-110">Most of these APIs are for scenarios of XAML language integration and extensibility.</span></span> <span data-ttu-id="96cbf-111">다음과 같은 시나리오가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-111">This might include any of the following scenarios:</span></span>

- <span data-ttu-id="96cbf-112">기본 XAML 판독기 또는 XAML 작성기의 기능 확장(XAML 노드 스트림 직접 처리, 고유한 XAML 판독기 또는 XAML 작성기 파생)</span><span class="sxs-lookup"><span data-stu-id="96cbf-112">Extending the capabilities of the base XAML readers or XAML writers (processing the XAML node stream directly; deriving your own XAML reader or XAML writer).</span></span>

- <span data-ttu-id="96cbf-113">특정 프레임워크 종속성이 없는 XAML 사용 가능 사용자 지정 형식 정의 및 .NET XAML 서비스에 XAML 형식 시스템 특성을 전달하도록 형식의 특성 정의</span><span class="sxs-lookup"><span data-stu-id="96cbf-113">Defining XAML-usable custom types that do not have specific framework dependencies, and attributing the types to convey their XAML type system characteristics to .NET XAML Services.</span></span>

- <span data-ttu-id="96cbf-114">XAML 판독기 또는 XAML 작성기를 XAML 태그 소스용 비주얼 디자이너 또는 대화형 편집기와 같은 애플리케이션의 구성 요소로 호스트</span><span class="sxs-lookup"><span data-stu-id="96cbf-114">Hosting XAML readers or XAML writers as a component of an application, such as a visual designer or interactive editor for XAML markup sources.</span></span>

- <span data-ttu-id="96cbf-115">XAML 값 변환기 작성(태그 확장, 사용자 지정 형식용 형식 변환기)</span><span class="sxs-lookup"><span data-stu-id="96cbf-115">Writing XAML value converters (markup extensions; type converters for custom types).</span></span>

- <span data-ttu-id="96cbf-116">사용자 지정 XAML 스키마 컨텍스트 정의(지원 형식 소스용 대체 어셈블리 로딩 기술 사용, 항상 어셈블리를 반영하는 대신 알려진 형식 조회 기술 사용, CLR(공용 언어 런타임) `AppDomain` 및 관련 보안 모델을 사용하지 않는 로드된 어셈블리 개념 사용)</span><span class="sxs-lookup"><span data-stu-id="96cbf-116">Defining a custom XAML schema context (using alternate assembly-loading techniques for backing type sources; using known-types lookup techniques instead of always reflecting assemblies; using loaded assembly concepts that do not use the common language runtime (CLR) `AppDomain` and its associated security model).</span></span>

- <span data-ttu-id="96cbf-117">기본 XAML 형식 시스템 확장</span><span class="sxs-lookup"><span data-stu-id="96cbf-117">Extending the base XAML type system.</span></span>

- <span data-ttu-id="96cbf-118">`Lookup` 또는 `Invoker` 기술을 사용하여 XAML 형식 시스템 및 형식 지원을 평가하는 방법에 적용</span><span class="sxs-lookup"><span data-stu-id="96cbf-118">Using the `Lookup` or `Invoker` techniques to influence the XAML type system and how type backings are evaluated.</span></span>

<span data-ttu-id="96cbf-119">언어로서 XAML의 소개 자료를 찾는 경우에는 [XAML 개요(WPF)](../fundamentals/xaml.md)를 사용해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-119">If you are looking for introductory material on XAML as a language, you might try [XAML Overview (WPF)](../fundamentals/xaml.md).</span></span> <span data-ttu-id="96cbf-120">이 항목에서는 WPF(Windows Presentation Foundation)와 XAML 태그 및 XAML 언어 기능을 둘 다 처음 사용하는 대상 그룹을 위해 XAML을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-120">That topic discusses XAML for an audience that is new both to Windows Presentation Foundation (WPF) and also to using XAML markup and XAML language features.</span></span> <span data-ttu-id="96cbf-121">또 다른 유용한 문서는 [XAML 언어 사양](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))의 소개 자료입니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-121">Another useful document is the introductory material in the [XAML language specification](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

## <a name="net-xaml-services-and-systemxaml-in-the-net-architecture"></a><span data-ttu-id="96cbf-122">.Net 아키텍처의 .NET XAML 서비스 및 `System.Xaml`</span><span class="sxs-lookup"><span data-stu-id="96cbf-122">.NET XAML Services and `System.Xaml` in the .NET Architecture</span></span>

<span data-ttu-id="96cbf-123">.NET XAML 서비스 및 `System.Xaml` 어셈블리는 XAML 언어 기능을 지원하는 데 필요한 많은 항목을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-123">.NET XAML Services and the `System.Xaml` assembly define much of what is needed for supporting XAML language features.</span></span> <span data-ttu-id="96cbf-124">여기에는 XAML 판독기 및 XAML 작성기의 기본 클래스가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-124">This includes base classes for XAML readers and XAML writers.</span></span> <span data-ttu-id="96cbf-125">프레임워크 관련 XAML 구현에 없었고 .NET XAML 서비스에 추가된 가장 중요한 기능은 XAML의 형식 시스템 표현입니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-125">The most important feature added to .NET XAML Services that was not present in any of the framework-specific XAML implementations is a type system representation for XAML.</span></span> <span data-ttu-id="96cbf-126">형식 시스템 표현은 프레임워크의 특정 기능에서 종속성을 사용하지 않고 XAML 기능을 중심으로 하는 개체 지향 방식으로 XAML을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-126">The type system representation presents XAML in an object-oriented way that centers on XAML capabilities without taking dependencies on specific capabilities of frameworks.</span></span>

<span data-ttu-id="96cbf-127">XAML 형식 시스템은 XAML 원본의 태그 형식 또는 런타임 세부 정보에 따라 제한되지 않으며 특정 지원 형식 시스템에 따라 제한되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-127">The XAML type system is not limited by the markup form or run-time specifics of the XAML origin; nor is it limited by any specific backing type system.</span></span> <span data-ttu-id="96cbf-128">XAML 형식 시스템은 형식, 멤버, XAML 스키마 컨텍스트, XML 수준 개념 및 기타 XAML 언어 개념이나 XAML 내장에 대한 개체 표현을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-128">The XAML type system includes object representations for types, members, XAML schema contexts, XML-level concepts, and other XAML language concepts or XAML intrinsics.</span></span> <span data-ttu-id="96cbf-129">XAML 형식 시스템을 사용하거나 확장하면 XAML 판독기 및 XAML 작성기와 같은 클래스에서 파생시킬 수 있으며 XAML을 사용하거나 내보내는 프레임워크, 기술 또는 애플리케이션에서 사용 가능한 특정 기능으로 XAML 표현의 기능을 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-129">Using or extending the XAML type system makes it possible to derive from classes like XAML readers and XAML writers, and extend the functionality of XAML representations into specific features enabled by a framework, a technology, or an application that consumes or emits XAML.</span></span> <span data-ttu-id="96cbf-130">XAML 스키마 컨텍스트의 개념은 XAML 개체 작성기 구현, 컨텍스트에서 어셈블리 정보를 통해 전달되는 기술의 지원 형식 시스템 및 XAML 노드 소스의 조합에서 실용적인 개체 그래프 작성 작업을 가능하게 합니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-130">The concept of a XAML schema context enables practical object graph write operations from the combination of a XAML object writer implementation, a technology's backing type system as communicated through assembly information in the context, and the XAML node source.</span></span> <span data-ttu-id="96cbf-131">XAML 스키마 개념에 관한 자세한 내용은</span><span class="sxs-lookup"><span data-stu-id="96cbf-131">For more information on the XAML schema concept.</span></span> <span data-ttu-id="96cbf-132">[기본 XAML 스키마 컨텍스트 및 WPF XAML 스키마 컨텍스트](default-schema-context.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="96cbf-132">see [Default XAML Schema Context and WPF XAML Schema Context](default-schema-context.md).</span></span>

## <a name="xaml-node-streams-xaml-readers-and-xaml-writers"></a><span data-ttu-id="96cbf-133">XAML 노드 스트림, XAML 판독기 및 XAML 작성기</span><span class="sxs-lookup"><span data-stu-id="96cbf-133">XAML Node Streams, XAML Readers, and XAML Writers</span></span>

<span data-ttu-id="96cbf-134">XAML 언어와 XAML을 언어로 사용하는 특정 기술 간 관계에서 .NET XAML 서비스의 역할을 이해하려면 XAML 노드 스트림의 개념을 이해하고 이 개념이 API와 용어를 어떻게 형성하는지 알아보는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-134">To understand the role that .NET XAML Services plays in the relationship between the XAML language and specific technologies that use XAML as a language, it is helpful to understand the concept of a XAML node stream and how that concept shapes the API and terminology.</span></span> <span data-ttu-id="96cbf-135">XAML 노드 스트림은 XAML 언어 표현과 XAML이 표현하고 정의하는 개체 그래프 간 개념적 매개체입니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-135">The XAML node stream is a conceptual intermediate between a XAML language representation and the object graph that the XAML represents or defines.</span></span>

- <span data-ttu-id="96cbf-136">XAML 판독기는 특정 형식으로 XAML을 처리하고 XAML 노드 스트림을 생성하는 엔터티입니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-136">A XAML reader is an entity that processes XAML in some form, and produces a XAML node stream.</span></span> <span data-ttu-id="96cbf-137">API에서 XAML 판독기는 <xref:System.Xaml.XamlReader> 기본 클래스로 표현됩니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-137">In the API, a XAML reader is represented by the base class <xref:System.Xaml.XamlReader>.</span></span>

- <span data-ttu-id="96cbf-138">XAML 작성기는 XAML 노드 스트림을 처리하고 다른 항목을 생성하는 엔터티입니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-138">A XAML writer is an entity that processes a XAML node stream and produces something else.</span></span> <span data-ttu-id="96cbf-139">API에서 XAML 작성기는 <xref:System.Xaml.XamlWriter> 기본 클래스로 표현됩니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-139">In the API, a XAML writer is represented by the base class <xref:System.Xaml.XamlWriter>.</span></span>

  <span data-ttu-id="96cbf-140">XAML과 관련된 가장 일반적인 두 가지 시나리오는 XAML을 로드하여 개체 그래프를 인스턴스화하는 경우와 애플리케이션 또는 도구에서 개체 그래프를 저장하고 XAML 표현(일반적으로 텍스트 파일로 저장되는 태그 형식)을 생성하는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-140">The two most common scenarios involving XAML are loading XAML to instantiate an object graph, and saving an object graph from an application or tool and producing a XAML representation (typically in markup form saved as text file).</span></span> <span data-ttu-id="96cbf-141">XAML을 로드하고 개체 그래프를 만드는 것을 이 설명서에서는 로드 경로라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-141">Loading XAML and creating an object graph is often referred to in this documentation as the load path.</span></span> <span data-ttu-id="96cbf-142">기존 개체 그래프를 XAML로 저장하거나 직렬화하는 것을 이 설명서에서는 저장 경로라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-142">Saving or serializing an existing object graph to XAML is often referred to in this documentation as the save path.</span></span>

  <span data-ttu-id="96cbf-143">가장 일반적인 형식의 로드 경로는 다음과 같이 설명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-143">The most common type of load path can be described as follows:</span></span>

- <span data-ttu-id="96cbf-144">UTF 인코딩된 XML 형식이며 텍스트 파일로 저장된 XAML 표현으로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-144">Start with a XAML representation, in UTF-encoded XML format and saved as a text file.</span></span>

- <span data-ttu-id="96cbf-145">XAML을 <xref:System.Xaml.XamlXmlReader>로 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-145">Load that XAML into <xref:System.Xaml.XamlXmlReader>.</span></span> <span data-ttu-id="96cbf-146"><xref:System.Xaml.XamlXmlReader>는 <xref:System.Xaml.XamlReader> 서브클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-146"><xref:System.Xaml.XamlXmlReader> is a <xref:System.Xaml.XamlReader> subclass.</span></span>

- <span data-ttu-id="96cbf-147">결과는 XAML 노드 스트림입니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-147">The result is a XAML node stream.</span></span> <span data-ttu-id="96cbf-148"><xref:System.Xaml.XamlXmlReader> / <xref:System.Xaml.XamlReader> API를 사용하여 XAML 노드 스트림의 개별 노드에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-148">You can access individual nodes of the XAML node stream using <xref:System.Xaml.XamlXmlReader> / <xref:System.Xaml.XamlReader> API.</span></span> <span data-ttu-id="96cbf-149">여기에서 가장 일반적인 작업은 XAML 노드 스트림을 통해 진행하면서 “현재 레코드” 메타포를 사용하여 각 노드를 처리하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-149">The most typical operation here is to advance through the XAML node stream, processing each node using a "current record" metaphor.</span></span>

- <span data-ttu-id="96cbf-150">XAML 노드 스트림에서 <xref:System.Xaml.XamlObjectWriter> API로 결과 노드를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-150">Pass the resulting nodes from the XAML node stream to a <xref:System.Xaml.XamlObjectWriter> API.</span></span> <span data-ttu-id="96cbf-151"><xref:System.Xaml.XamlObjectWriter>는 <xref:System.Xaml.XamlWriter> 서브클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-151"><xref:System.Xaml.XamlObjectWriter> is a <xref:System.Xaml.XamlWriter> subclass.</span></span>

- <span data-ttu-id="96cbf-152"><xref:System.Xaml.XamlObjectWriter>는 소스 XAML 노드 스트림을 통해 진행함에 따라 한 번에 한 개체씩 개체 그래프를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-152">The <xref:System.Xaml.XamlObjectWriter> writes an object graph, one object at a time, in accordance to progress through the source XAML node stream.</span></span> <span data-ttu-id="96cbf-153">개체 쓰기는 지원 형식 시스템 및 프레임워크의 어셈블리와 형식에 액세스할 수 있는 구현 및 XAML 스키마 컨텍스트의 지원을 통해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-153">Object writing is done with the assistance of a XAML schema context and an implementation that can access the assemblies and types of a backing type system and framework.</span></span>

- <span data-ttu-id="96cbf-154">XAML 노드 스트림의 끝에서 <xref:System.Xaml.XamlObjectWriter.Result%2A>를 호출하여 개체 그래프의 루트 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-154">Call <xref:System.Xaml.XamlObjectWriter.Result%2A> at the end of the XAML node stream to obtain the root object of the object graph.</span></span>

  <span data-ttu-id="96cbf-155">가장 일반적인 형식의 저장 경로는 다음과 같이 설명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-155">The most common type of save path can be described as follows:</span></span>

- <span data-ttu-id="96cbf-156">전체 애플리케이션 런타임, 런타임의 UI 콘텐츠와 상태 또는 런타임에 전체 애플리케이션 개체 표현의 더 작은 세그먼트에 관한 개체 그래프로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-156">Start with the object graph of an entire application run time, the UI content and state of a run time, or a smaller segment of an overall application's object representation at run time.</span></span>

- <span data-ttu-id="96cbf-157">애플리케이션 루트 또는 문서 루트와 같은 논리적 시작 개체에서 <xref:System.Xaml.XamlObjectReader>로 개체를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-157">From a logical start object, such as an application root or document root, load the objects into <xref:System.Xaml.XamlObjectReader>.</span></span> <span data-ttu-id="96cbf-158"><xref:System.Xaml.XamlObjectReader>는 <xref:System.Xaml.XamlReader> 서브클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-158"><xref:System.Xaml.XamlObjectReader> is a <xref:System.Xaml.XamlReader> subclass.</span></span>

- <span data-ttu-id="96cbf-159">결과는 XAML 노드 스트림입니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-159">The result is a XAML node stream.</span></span> <span data-ttu-id="96cbf-160"><xref:System.Xaml.XamlObjectReader> 및 <xref:System.Xaml.XamlReader> API를 사용하여 XAML 노드 스트림의 개별 노드에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-160">You can access individual nodes of the XAML node stream using <xref:System.Xaml.XamlObjectReader> and <xref:System.Xaml.XamlReader> API.</span></span> <span data-ttu-id="96cbf-161">여기에서 가장 일반적인 작업은 XAML 노드 스트림을 통해 진행하면서 “현재 레코드” 메타포를 사용하여 각 노드를 처리하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-161">The most typical operation here is to advance through the XAML node stream, processing each node using a "current record" metaphor.</span></span>

- <span data-ttu-id="96cbf-162">XAML 노드 스트림에서 <xref:System.Xaml.XamlXmlWriter> API로 결과 노드를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-162">Pass the resulting nodes from the XAML node stream to a <xref:System.Xaml.XamlXmlWriter> API.</span></span> <span data-ttu-id="96cbf-163"><xref:System.Xaml.XamlXmlWriter>는 <xref:System.Xaml.XamlWriter> 서브클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-163"><xref:System.Xaml.XamlXmlWriter> is a <xref:System.Xaml.XamlWriter> subclass.</span></span>

- <span data-ttu-id="96cbf-164"><xref:System.Xaml.XamlXmlWriter>는 XML UTF 인코딩으로 XAML을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-164">The <xref:System.Xaml.XamlXmlWriter> writes XAML in an XML UTF encoding.</span></span> <span data-ttu-id="96cbf-165">이를 텍스트 파일, 스트림 또는 다른 형식으로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-165">You can save this as a text file, as a stream, or in other forms.</span></span>

- <span data-ttu-id="96cbf-166"><xref:System.Xaml.XamlXmlWriter.Flush%2A>를 호출하여 최종 출력을 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-166">Call <xref:System.Xaml.XamlXmlWriter.Flush%2A> to obtain the final output.</span></span>

<span data-ttu-id="96cbf-167">XAML 노드 스트림 개념에 관한 자세한 내용은 [XAML 노드 스트림 구조 및 개념 이해](understanding-xaml-node-stream-structures-and-concepts.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="96cbf-167">For more information about XAML node stream concepts, see [Understanding XAML Node Stream Structures and Concepts](understanding-xaml-node-stream-structures-and-concepts.md).</span></span>

### <a name="the-xamlservices-class"></a><span data-ttu-id="96cbf-168">XamlServices 클래스</span><span class="sxs-lookup"><span data-stu-id="96cbf-168">The XamlServices Class</span></span>

<span data-ttu-id="96cbf-169">항상 XAML 노드 스트림을 처리해야 하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-169">It is not always necessary to deal with a XAML node stream.</span></span> <span data-ttu-id="96cbf-170">기본 로드 경로 또는 기본 저장 경로를 원하는 경우 <xref:System.Xaml.XamlServices> 클래스에서 API를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-170">If you want a basic load path or a basic save path, you can use APIs in the <xref:System.Xaml.XamlServices> class.</span></span>

- <span data-ttu-id="96cbf-171"><xref:System.Xaml.XamlServices.Load%2A>의 다양한 시그니처는 로드 경로를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-171">Various signatures of <xref:System.Xaml.XamlServices.Load%2A> implement a load path.</span></span> <span data-ttu-id="96cbf-172">파일 또는 스트림을 로드하거나, 판독기 API와 함께 로드하여 XAML 입력을 래핑하는 <xref:System.Xml.XmlReader>, <xref:System.IO.TextReader>또는 <xref:System.Xaml.XamlReader>를 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-172">You can either load a file or stream, or can load an <xref:System.Xml.XmlReader>, <xref:System.IO.TextReader> or <xref:System.Xaml.XamlReader> that wrap your XAML input by loading with that reader's APIs.</span></span>

- <span data-ttu-id="96cbf-173"><xref:System.Xaml.XamlServices.Save%2A>의 다양한 시그니처는 개체 그래프를 저장하고 스트림, 파일 또는 <xref:System.Xml.XmlWriter>/<xref:System.IO.TextWriter> 인스턴스로 출력을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-173">Various signatures of <xref:System.Xaml.XamlServices.Save%2A> save an object graph and produce output as a stream, file, or <xref:System.Xml.XmlWriter>/<xref:System.IO.TextWriter> instance.</span></span>

- <span data-ttu-id="96cbf-174"><xref:System.Xaml.XamlServices.Transform%2A>은 로드 경로 및 저장 경로를 단일 작업으로 연결하여 XAML을 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-174"><xref:System.Xaml.XamlServices.Transform%2A> converts XAML by linking a load path and a save path as a single operation.</span></span> <span data-ttu-id="96cbf-175"><xref:System.Xaml.XamlReader> 및 <xref:System.Xaml.XamlWriter>에 다른 스키마 컨텍스트 또는 다른 지원 형식 시스템을 사용할 수 있으며, 이는 결과 XAML이 변환되는 방식에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-175">A different schema context or different backing type system could be used for <xref:System.Xaml.XamlReader> and <xref:System.Xaml.XamlWriter>, which is what influences how the resulting XAML is transformed.</span></span>

<span data-ttu-id="96cbf-176"><xref:System.Xaml.XamlServices>를 사용하는 방법에 관한 자세한 내용은 [XAMLServices 클래스 및 기본 XAML 읽기 또는 쓰기](basic-reading-writing.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="96cbf-176">For more information about how to use <xref:System.Xaml.XamlServices>, see [XAMLServices Class and Basic XAML Reading or Writing](basic-reading-writing.md).</span></span>

## <a name="xaml-type-system"></a><span data-ttu-id="96cbf-177">XAML 형식 시스템</span><span class="sxs-lookup"><span data-stu-id="96cbf-177">XAML Type System</span></span>

<span data-ttu-id="96cbf-178">XAML 형식 시스템은 XAML 노드 스트림의 지정된 개별 노드를 사용하는 데 필요한 API를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-178">The XAML type system provides the APIs that are required to work with a given individual node of a XAML node stream.</span></span>

<span data-ttu-id="96cbf-179"><xref:System.Xaml.XamlType>은 개체의 표현이며 시작 개체 노드와 끝 개체 노드 사이에서 처리하는 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-179"><xref:System.Xaml.XamlType> is the representation for an object - what you are processing between a start object node and end object node.</span></span>

<span data-ttu-id="96cbf-180"><xref:System.Xaml.XamlMember>는 개체 멤버의 표현이며 시작 멤버 노드와 끝 멤버 노드 사이에서 처리하는 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-180"><xref:System.Xaml.XamlMember> is the representation for a member of an object - what you are processing between a start member node and end member node.</span></span>

<span data-ttu-id="96cbf-181"><xref:System.Xaml.XamlType.GetAllMembers%2A>, <xref:System.Xaml.XamlType.GetMember%2A> 및 <xref:System.Xaml.XamlMember.DeclaringType%2A>과 같은 API는 <xref:System.Xaml.XamlType>와 <xref:System.Xaml.XamlMember> 간 관계를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-181">APIs such as <xref:System.Xaml.XamlType.GetAllMembers%2A> and <xref:System.Xaml.XamlType.GetMember%2A> and <xref:System.Xaml.XamlMember.DeclaringType%2A> report the relationships between a <xref:System.Xaml.XamlType> and <xref:System.Xaml.XamlMember>.</span></span>

<span data-ttu-id="96cbf-182">.NET XAML 서비스에서 구현되는 XAML 형식 시스템의 기본 동작은 CLR(공용 언어 런타임) 및 어셈블리에서 리플렉션을 통한 CLR 형식의 정적 분석을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-182">The default behavior of the XAML type system as implemented by .NET XAML Services is based on the common language runtime (CLR), and static analysis of CLR types in assemblies by using reflection.</span></span> <span data-ttu-id="96cbf-183">따라서 특정 CLR 형식의 경우 XAML 형식 시스템의 기본 구현은 해당 형식 및 해당 멤버의 XAML 스키마를 공개하고 XAML 형식 시스템 측면에서 보고할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-183">Therefore, for a specific CLR type, the default implementation of the XAML type system can expose the XAML schema of that type and its members and report it in terms of the XAML type system.</span></span> <span data-ttu-id="96cbf-184">기본 XAML 형식 시스템에서 형식 할당 가능성의 개념은 CLR 상속에 매핑되고 인스턴스, 값 형식 등의 개념은 CLR의 지원 동작 및 기능에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-184">In the default XAML type system, the concept of assignability of types is mapped onto CLR inheritance, and the concepts of instances, value types, and so on, are also mapped to the supporting behaviors and features of the CLR.</span></span>

## <a name="reference-for-xaml-language-features"></a><span data-ttu-id="96cbf-185">XAML 언어 기능의 참조</span><span class="sxs-lookup"><span data-stu-id="96cbf-185">Reference for XAML Language Features</span></span>

<span data-ttu-id="96cbf-186">XAML을 지원하기 위해 .NET XAML 서비스는 XAML 언어 XAML 네임스페이스에 대해 정의된 대로 XAML 언어 개념의 특정 구현을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-186">To support XAML, .NET XAML Services provides specific implementation of XAML language concepts as defined for the XAML language XAML namespace.</span></span> <span data-ttu-id="96cbf-187">이 내용은 특정 참조 페이지로 문서화됩니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-187">These are documented as specific reference pages.</span></span> <span data-ttu-id="96cbf-188">언어 기능은 .NET XAML 서비스에서 정의된 XAML 판독기 또는 XAML 작성기에서 이 언어 기능이 처리될 때 동작하는 방식의 관점에서 문서화됩니다.</span><span class="sxs-lookup"><span data-stu-id="96cbf-188">The language features are documented from the perspective of how these language features behave when they are processed by a XAML reader or XAML writer that is defined by .NET XAML Services.</span></span> <span data-ttu-id="96cbf-189">자세한 내용은 [XAML 네임스페이스(x:) 언어 기능](namespace-language-features.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="96cbf-189">For more information, see [XAML Namespace (x:) Language Features](namespace-language-features.md).</span></span>