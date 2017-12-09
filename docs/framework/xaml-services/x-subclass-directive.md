---
title: "x:Subclass Yönergesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Subclass
- xSubclass
- x:Subclass
helpviewer_keywords:
- x:Subclass attribute [XAML Services]
- XAML [XAML Services], x:Subclass attribute
- Subclass attribute in XAML [XAML Services]
ms.assetid: 99f66072-8107-4362-ab99-8171dc83b469
caps.latest.revision: "20"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 5c6e91fcecb60dee2577ea62c2313f8b2c7eecbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="xsubclass-directive"></a><span data-ttu-id="a04cb-102">x:Subclass Yönergesi</span><span class="sxs-lookup"><span data-stu-id="a04cb-102">x:Subclass Directive</span></span>
<span data-ttu-id="a04cb-103">XAML biçimlendirme derleme davranışını değiştiren zaman `x:Class` de sağlanır.</span><span class="sxs-lookup"><span data-stu-id="a04cb-103">Modifies XAML markup compile behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="a04cb-104">Temel alan bir parçalı sınıf oluşturmak yerine `x:Class`, sağlanan `x:Class` Ara bir sınıf olarak oluşturulur ve ardından, sağlanan türetilmiş sınıf temel beklenen `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="a04cb-104">Instead of creating a partial class that is based on `x:Class`, the provided `x:Class` is created as an intermediate class, and then your provided derived class is expected to be based on `x:Class`.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="a04cb-105">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="a04cb-105">XAML Attribute Usage</span></span>  
  
```  
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="a04cb-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="a04cb-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`namespace`|<span data-ttu-id="a04cb-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="a04cb-107">Optional.</span></span> <span data-ttu-id="a04cb-108">İçeren bir CLR ad alanını belirtir `classname`.</span><span class="sxs-lookup"><span data-stu-id="a04cb-108">Specifies a CLR namespace that contains `classname`.</span></span> <span data-ttu-id="a04cb-109">Varsa `namespace` belirtilirse, nokta (.) ayıran `namespace` ve `classname`.</span><span class="sxs-lookup"><span data-stu-id="a04cb-109">If `namespace` is specified, a dot (.) separates `namespace` and `classname`.</span></span>|  
|`classname`|<span data-ttu-id="a04cb-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="a04cb-110">Required.</span></span> <span data-ttu-id="a04cb-111">CLR yüklenen XAML ve, arka plan kod bu XAML bağlayan kısmi sınıfın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a04cb-111">Specifies the CLR name of the partial class that connects the loaded XAML and your code-behind for that XAML.</span></span> <span data-ttu-id="a04cb-112">Açıklamalar bakın.</span><span class="sxs-lookup"><span data-stu-id="a04cb-112">See Remarks.</span></span>|  
|`subclassNamespace`|<span data-ttu-id="a04cb-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="a04cb-113">Optional.</span></span> <span data-ttu-id="a04cb-114">Farklı olabilir `namespace` ise her ad alanı diğer çözebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a04cb-114">Can be different from `namespace` if each namespace can resolve the other.</span></span> <span data-ttu-id="a04cb-115">İçeren bir CLR ad alanını belirtir `subclassName`.</span><span class="sxs-lookup"><span data-stu-id="a04cb-115">Specifies a CLR namespace that contains `subclassName`.</span></span> <span data-ttu-id="a04cb-116">Varsa `subclassName` belirtilirse, nokta (.) ayıran `subclassNamespace` ve `subclassName`.</span><span class="sxs-lookup"><span data-stu-id="a04cb-116">If `subclassName` is specified, a dot (.) separates `subclassNamespace` and `subclassName`.</span></span>|  
|`subclassName`|<span data-ttu-id="a04cb-117">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="a04cb-117">Required.</span></span> <span data-ttu-id="a04cb-118">Bir alt CLR adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a04cb-118">Specifies the CLR name of the subclass.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="a04cb-119">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="a04cb-119">Dependencies</span></span>  
 <span data-ttu-id="a04cb-120">[x: Class yönergesi](../../../docs/framework/xaml-services/x-class-directive.md) de aynı nesnede sağlanması gerekir ve bu nesne XAML üretim kök öğesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a04cb-120">[x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md) must also be provided on the same object, and that object must be the root element of the XAML production.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a04cb-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a04cb-121">Remarks</span></span>  
 <span data-ttu-id="a04cb-122">`x:Subclass`Kullanım öncelikle kısmi sınıf bildirimleri desteklemeyen diller için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a04cb-122">`x:Subclass` usage is primarily intended for languages that do not support partial class declarations.</span></span>  
  
 <span data-ttu-id="a04cb-123">Olarak kullanılan sınıf `x:Subclass` iç içe geçmiş sınıf olamaz ve `x:Subclass` kök nesnesine "Bağımlılıkları" bölümünde açıklandığı gibi başvurmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a04cb-123">The class used as the `x:Subclass` cannot be a nested class, and `x:Subclass` must refer to the root object as explained in the "Dependencies" section.</span></span>  
  
 <span data-ttu-id="a04cb-124">Aksi takdirde, kavramsal anlamını `x:Subclass` .NET Framework XAML Hizmetleri uygulaması tarafından tanımlanmamış.</span><span class="sxs-lookup"><span data-stu-id="a04cb-124">Otherwise, the conceptual meaning of `x:Subclass` is undefined by a .NET Framework XAML Services implementation.</span></span> <span data-ttu-id="a04cb-125">.NET Framework XAML hizmetlerinde davranışı tarafından hangi XAML biçimlendirme ve kodun yedekleme bağlı genel programlama modeli belirtmediğinden budur.</span><span class="sxs-lookup"><span data-stu-id="a04cb-125">This is because .NET Framework XAML Services behavior does not specify the overall programming model by which XAML markup and backing code are connected.</span></span> <span data-ttu-id="a04cb-126">Daha fazla kavramlarını uygulamaları ile ilgili `x:Class` ve `x:Subclass` programlama modelleri veya uygulama modelleri XAML işaretleme, derlenmiş biçimlendirme ve CLR tabanlı gerideki koddan nasıl bağlayacağınızı tanımlamak için kullanmak belirli çerçeveleri tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a04cb-126">Implementations of further concepts related to `x:Class` and `x:Subclass` are performed by specific frameworks that use programming models or application models to define how to connect XAML markup, compiled markup, and CLR-based code-behind.</span></span> <span data-ttu-id="a04cb-127">Her framework davranışı ya da derleme ortamında eklenmelidir belirli bileşenlerini bazılarını etkinleştirmek kendi yapı eylemleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="a04cb-127">Each framework might have its own build actions that enable some of the behavior, or specific components that must be included in the build environment.</span></span> <span data-ttu-id="a04cb-128">Bir çerçeve içinde yapı eylemleri de arka plan kod için kullanılan belirli CLR dil göre değişebilir.</span><span class="sxs-lookup"><span data-stu-id="a04cb-128">Within a framework, build actions can also vary based on the specific CLR language that is used for the code-behind.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="a04cb-129">WPF kullanım notları</span><span class="sxs-lookup"><span data-stu-id="a04cb-129">WPF Usage Notes</span></span>  
 <span data-ttu-id="a04cb-130">`x:Subclass`bir sayfa kök veya üzerinde olabilir <xref:System.Windows.Application> zaten uygulama tanımında kök `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="a04cb-130">`x:Subclass` can be on a page root or on the <xref:System.Windows.Application> root in the application definition, which already has `x:Class`.</span></span> <span data-ttu-id="a04cb-131">Bildirme `x:Subclass` sayfa veya uygulama kökü veya no burada belirtme dışındaki herhangi bir öğe üzerinde `x:Class` var, bir derleme zamanı hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="a04cb-131">Declaring `x:Subclass` on any element other than a page or application root, or specifying it where no `x:Class` exists, causes a compile-time error.</span></span>  
  
 <span data-ttu-id="a04cb-132">Türetilen oluşturma sınıflar, iş için doğru `x:Subclass` senaryodur oldukça karmaşık.</span><span class="sxs-lookup"><span data-stu-id="a04cb-132">Creating derived classes that work correctly for the `x:Subclass` scenario is fairly complex.</span></span> <span data-ttu-id="a04cb-133">Ara (dosyaları projenizin obj klasörü .xaml dosya adlarını dahil adlarıyla biçimlendirmesi derleme tarafından üretilen .g) incelemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="a04cb-133">You might need to examine the intermediate files (the .g files produced in the obj folder of your project by markup compile, with names that incorporate the .xaml file names).</span></span> <span data-ttu-id="a04cb-134">Bu Ara dosyaları derlenmiş uygulama birleştirilmiş kısmi sınıflarda programlama belirli yapılardan kökenini belirlemenize yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="a04cb-134">These intermediate files can help you determine the origin of certain programming constructs in the joined partial classes in the compiled application.</span></span>  
  
 <span data-ttu-id="a04cb-135">Olay işleyicileri türetilmiş sınıfında olmalıdır `internal override` (`Friend Overrides` içinde [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)]) Ara sınıfında derleme sırasında oluşturulan saplamalar işleyicileri için geçersiz kılmak için.</span><span class="sxs-lookup"><span data-stu-id="a04cb-135">Event handlers in the derived class must be `internal override` (`Friend Overrides` in [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)]) in order to override the stubs for the handlers as created in the intermediate class during compilation.</span></span> <span data-ttu-id="a04cb-136">Aksi takdirde, türetilmiş sınıf uygulamaları (gölge) Ara sınıf uygulamasını gizleme ve Ara sınıfı işleyici çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="a04cb-136">Otherwise, the derived class implementations hide (shadow) the intermediate class implementation and the intermediate class handlers are not invoked.</span></span>  
  
 <span data-ttu-id="a04cb-137">Tanımladığınızda her ikisi de `x:Class` ve `x:Subclass`, herhangi bir uygulama tarafından başvurulan sınıfı için sağlamak zorunda değildir `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="a04cb-137">When you define both `x:Class` and `x:Subclass`, you do not need to provide any implementation for the class that is referenced by `x:Class`.</span></span> <span data-ttu-id="a04cb-138">Aracılığıyla bir ad vermek yeterlidir `x:Class` derleyici (derleyici ı varsayılan adı bu durumda) Ara dosyalarında oluşturur sınıfı için bazı yönergeler sahip olması özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a04cb-138">You only need to give it a name via the `x:Class` attribute so that the compiler has some guidance for the class that it creates in the intermediate files (the compiler does not select a default name in this case).</span></span> <span data-ttu-id="a04cb-139">Verebilirsiniz `x:Class` uygulaması sınıf; ancak, bu her ikisi de kullanmak için tipik senaryo değil `x:Class` ve `x:Subclass`.</span><span class="sxs-lookup"><span data-stu-id="a04cb-139">You can give the `x:Class` class an implementation; however, this is not the typical scenario for using both `x:Class` and `x:Subclass`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a04cb-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a04cb-140">See Also</span></span>  
 [<span data-ttu-id="a04cb-141">x: Class yönergesi</span><span class="sxs-lookup"><span data-stu-id="a04cb-141">x:Class Directive</span></span>](../../../docs/framework/xaml-services/x-class-directive.md)  
 [<span data-ttu-id="a04cb-142">XAML ve WPF için özel sınıflar</span><span class="sxs-lookup"><span data-stu-id="a04cb-142">XAML and Custom Classes for WPF</span></span>](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)