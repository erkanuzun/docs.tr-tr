---
title: "x:Members Yönergesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 155b393d-3b49-4c5a-8c9e-b3d9893af4e4
caps.latest.revision: "5"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 230c6359c59b9f00738de9ce7ceeccd69899135f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="xmembers-directive"></a><span data-ttu-id="9553c-102">x:Members Yönergesi</span><span class="sxs-lookup"><span data-stu-id="9553c-102">x:Members Directive</span></span>
<span data-ttu-id="9553c-103">X: Class için üst öğenin uygulamak biçimlendirme içinde tanımlanan üyelerin kümesini içerir.</span><span class="sxs-lookup"><span data-stu-id="9553c-103">Holds a set of members that are defined in markup, which apply to the x:Class of the parent element.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="9553c-104">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="9553c-104">XAML Attribute Usage</span></span>  
  
```  
<object x:Class="className">  
  <x:Members>  
    oneOrMoreMembers  
  </x:Members  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="9553c-105">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="9553c-105">XAML Values</span></span>  
  
|||  
|-|-|  
|`className`|<span data-ttu-id="9553c-106">XAML üretim için yedekleme sınıfı ya da parçalı sınıf adıdır.</span><span class="sxs-lookup"><span data-stu-id="9553c-106">Name of the backing class or partial class for the XAML production.</span></span> <span data-ttu-id="9553c-107">Açıklamalar bakın.</span><span class="sxs-lookup"><span data-stu-id="9553c-107">See Remarks.</span></span>|  
|`oneOrMoreMembers`|<span data-ttu-id="9553c-108">Üye tanımları temsil eden bir veya daha fazla nesne öğeleri.</span><span class="sxs-lookup"><span data-stu-id="9553c-108">One or more object elements that represent member definitions.</span></span> <span data-ttu-id="9553c-109">Genellikle, bunlar `x:Property` nesne öğeleri.</span><span class="sxs-lookup"><span data-stu-id="9553c-109">Typically, these are `x:Property` object elements.</span></span> <span data-ttu-id="9553c-110">Açıklamalar bakın.</span><span class="sxs-lookup"><span data-stu-id="9553c-110">See Remarks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9553c-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9553c-111">Remarks</span></span>  
 <span data-ttu-id="9553c-112">.NET Framework XAML hizmetlerinde uygulamasında yedekleme sınıfı veya yoktur için temel üye uygulaması `x:Members`.</span><span class="sxs-lookup"><span data-stu-id="9553c-112">In the .NET Framework XAML Services implementation, there is no backing class or underlying member implementation for `x:Members`.</span></span> <span data-ttu-id="9553c-113">`x:Members`herhangi bir üye olarak bulunabilir özel XAML üyesi olduğu.</span><span class="sxs-lookup"><span data-stu-id="9553c-113">`x:Members` is a special XAML member that can exist as a member on any type.</span></span> <span data-ttu-id="9553c-114">XAML düğüm akış `x:Members` adlı bir üye temsil edilir `Members`, XAML dili XAML ad.</span><span class="sxs-lookup"><span data-stu-id="9553c-114">In a XAML node stream, `x:Members` is represented as a member named `Members`, from the XAML language XAML namespace.</span></span> <span data-ttu-id="9553c-115">Üye `Members` salt okunur bir genel listesini içeren `Member` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="9553c-115">The member `Members` contains a read-only generic list of `Member` objects.</span></span> <span data-ttu-id="9553c-116">Tipik biçimlendirmede tek tek üyeleri olarak belirtilen `x:Property` özelliği öğeleri.</span><span class="sxs-lookup"><span data-stu-id="9553c-116">In typical markup the individual members are specified as `x:Property` property elements.</span></span> <span data-ttu-id="9553c-117">`x:Property`özellikle türlerinin özellikleri için daha kesin bir türü ve için atanamaz `x:Member`.</span><span class="sxs-lookup"><span data-stu-id="9553c-117">`x:Property` is a more precise type specifically for properties of types and is assignable to `x:Member`.</span></span> <span data-ttu-id="9553c-118">Daha fazla bilgi için bkz: [x: Property yönergesi](../../../docs/framework/xaml-services/x-property-directive.md).</span><span class="sxs-lookup"><span data-stu-id="9553c-118">For more information, see [x:Property Directive](../../../docs/framework/xaml-services/x-property-directive.md).</span></span>  
  
 <span data-ttu-id="9553c-119">Pratik kullanımını desteklemek için `x:Members` üye tanımları biçimlendirmede belirtmek için bir yol üyeleri değiştirilebilir bir sınıf ile ilişkili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9553c-119">To support a practical usage of `x:Members` as a means to specify member definitions in markup, the members must be associated with a class that can be modified.</span></span> <span data-ttu-id="9553c-120">Hedeflenen modeli olan `x:Members` belirten bir türü bir üyesi olarak mevcut bir `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="9553c-120">The intended model is that `x:Members` exists as a member of a type that specifies an `x:Class`.</span></span> <span data-ttu-id="9553c-121">Ancak, türleri ve üyeleri ilişkilendirme veya dinamik üyenin tanımları oluşturan mekanizması .NET Framework XAML hizmetlerinde düzeyinde desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="9553c-121">However, the mechanism for associating types and members or for producing dynamic member definitions is not supported at the .NET Framework XAML Services level.</span></span> <span data-ttu-id="9553c-122">Bu üye tanımları XAML destek uygulama modelleri sahip tek tek çerçeveler bırakılır.</span><span class="sxs-lookup"><span data-stu-id="9553c-122">This is left to individual frameworks that have application models that support member definitions from XAML.</span></span> <span data-ttu-id="9553c-123">Genellikle, isteğe bağlı olarak işaretleme-XAML ve ya da derleme MSBUILD yapı eylemleri arka plan kodu ile tümleştirmek veya üretim XAML gelen saf derlemeler bu özelliği desteklemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9553c-123">Typically, MSBUILD build actions that markup-compile the XAML and either integrate it with code-behind or produce pure from-XAML assemblies are needed to support that feature.</span></span>  
  
## <a name="xmembers-for-windows-workflow-foundation"></a><span data-ttu-id="9553c-124">x: Members Windows Workflow Foundation için</span><span class="sxs-lookup"><span data-stu-id="9553c-124">x:Members for Windows Workflow Foundation</span></span>  
 <span data-ttu-id="9553c-125">Windows Workflow Foundation için `x:Members` tamamen XAML veya XAML oluşan özel bir aktivite üyeleri içerir – dinamik üyeler arka plan kodu ile bir etkinlik Tasarımcısı için tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="9553c-125">For Windows Workflow Foundation, `x:Members` contains the members of a custom activity composed entirely in XAML, or XAML –defined dynamic members for an activity designer with code-behind.</span></span> <span data-ttu-id="9553c-126">`x:Class`XAML üretim kök öğesinin de belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="9553c-126">`x:Class` must also be specified on the root element of the XAML production.</span></span> <span data-ttu-id="9553c-127">Bu, .NET Framework XAML hizmetlerinde düzeyinde zorunlu değildir, ancak XAML üretim özel etkinlikler ve Windows Workflow Foundation XAML genel destek MSBUILD yapı eylemleri tarafından yüklenen bir gereksinim haline gelir.</span><span class="sxs-lookup"><span data-stu-id="9553c-127">This is not a requirement at the .NET Framework XAML Services level, but becomes a requirement when the XAML production is loaded by the MSBUILD build actions that support custom activities and Windows Workflow Foundation XAML in general.</span></span> <span data-ttu-id="9553c-128">`x:Members`Biçimlendirme bildirir nesne öğesinin ilk alt öğe olmalıdır `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="9553c-128">`x:Members` must be the first child element in markup of the object element that declares the `x:Class`.</span></span>