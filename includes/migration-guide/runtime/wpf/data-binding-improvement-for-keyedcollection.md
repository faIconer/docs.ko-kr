---
ms.openlocfilehash: a0dc2401155a162eaa5aa6b4d9e6af1ca1c2ccc8
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802716"
---
### <a name="data-binding-improvement-for-keyedcollection"></a><span data-ttu-id="578fb-101">KeyedCollection에 대한 데이터 바인딩 개선</span><span class="sxs-lookup"><span data-stu-id="578fb-101">Data Binding improvement for KeyedCollection</span></span>

|   |   |
|---|---|
|<span data-ttu-id="578fb-102">세부 정보</span><span class="sxs-lookup"><span data-stu-id="578fb-102">Details</span></span>|<span data-ttu-id="578fb-103">원본 개체가 동일한 서명(예: KeyedCollection&lt;int,TItem&gt;)이 있는 사용자 지정 인덱서를 선언할 때 IList 인덱서가 잘못 사용된 <xref:System.Windows.Data.Binding>을 수정했습니다.</span><span class="sxs-lookup"><span data-stu-id="578fb-103">Fixed <xref:System.Windows.Data.Binding> incorrect use of IList indexer when the source object declares a custom indexer with the same signature (e.g. KeyedCollection&lt;int,TItem&gt;).</span></span>|
|<span data-ttu-id="578fb-104">제안</span><span class="sxs-lookup"><span data-stu-id="578fb-104">Suggestion</span></span>|<span data-ttu-id="578fb-105">애플리케이션이 이 변경에서 이점을 활용하려면 .NET Framework 4.7.2 이상에서 실행해야 하며, 앱 구성 파일의 <code>&lt;runtime&gt;</code> 섹션에 다음과 같은 [AppContext 스위치](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element)를 추가하여 변경 내용을 옵트인하고 <code>false</code>로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="578fb-105">In order for the application to benefit from this change, it must run on the .NET Framework 4.7.2 or later, and it must opt in to the change by adding the following [AppContext switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the <code>&lt;runtime&gt;</code> section of the app config file and setting it to <code>false</code>:</span></span><pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.Binding.IListIndexerHidesCustomIndexer=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="578fb-106">범위</span><span class="sxs-lookup"><span data-stu-id="578fb-106">Scope</span></span>|<span data-ttu-id="578fb-107">주요함</span><span class="sxs-lookup"><span data-stu-id="578fb-107">Major</span></span>|
|<span data-ttu-id="578fb-108">버전</span><span class="sxs-lookup"><span data-stu-id="578fb-108">Version</span></span>|<span data-ttu-id="578fb-109">4.8</span><span class="sxs-lookup"><span data-stu-id="578fb-109">4.8</span></span>|
|<span data-ttu-id="578fb-110">Type</span><span class="sxs-lookup"><span data-stu-id="578fb-110">Type</span></span>|<span data-ttu-id="578fb-111">런타임</span><span class="sxs-lookup"><span data-stu-id="578fb-111">Runtime</span></span>|
