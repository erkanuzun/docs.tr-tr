---
title: RelativeSource MarkupExtension
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 41978e7b91c50b33649bd88e23d22fce7a272c5b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="relativesource-markupextension"></a><span data-ttu-id="9fc28-102">RelativeSource MarkupExtension</span><span class="sxs-lookup"><span data-stu-id="9fc28-102">RelativeSource MarkupExtension</span></span>
<span data-ttu-id="9fc28-103">Özelliklerini belirtir bir <xref:System.Windows.Data.RelativeSource> içinde kullanılacak bağlama kaynağı, bir [bağlama biçimlendirme uzantısı](../../../../docs/framework/wpf/advanced/binding-markup-extension.md), veya ayarlarken <xref:System.Windows.Data.Binding.RelativeSource%2A> özelliği bir <xref:System.Windows.Data.Binding> XAML'de kurulan öğesi.</span><span class="sxs-lookup"><span data-stu-id="9fc28-103">Specifies properties of a <xref:System.Windows.Data.RelativeSource> binding source, to be used within a [Binding Markup Extension](../../../../docs/framework/wpf/advanced/binding-markup-extension.md), or when setting the <xref:System.Windows.Data.Binding.RelativeSource%2A> property of a <xref:System.Windows.Data.Binding> element established in XAML.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="9fc28-104">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="9fc28-104">XAML Attribute Usage</span></span>  
  
```xml  
<Binding RelativeSource="{RelativeSource modeEnumValue}" .../>  
```  
  
## <a name="xaml-attribute-usage-nested-within-binding-extension"></a><span data-ttu-id="9fc28-105">XAML Öznitelik Kullanımı (Bağlama uzantıları içinde iç içe geçmiş)</span><span class="sxs-lookup"><span data-stu-id="9fc28-105">XAML Attribute Usage (nested within Binding extension)</span></span>  
  
```xml  
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="9fc28-106">XAML Nesne Öğesi Kullanımı</span><span class="sxs-lookup"><span data-stu-id="9fc28-106">XAML Object Element Usage</span></span>  
  
```xml  
<Binding>  
  <Binding.RelativeSource>  
    <RelativeSource Mode="modeEnumValue"/>  
  </Binding.RelativeSource>  
</Binding>  
- or   
<Binding>  
  <Binding.RelativeSource>  
    <RelativeSource  
      Mode="FindAncestor"  
      AncestorType="{x:Type typeName}"  
      AncestorLevel="intLevel"  
    />  
  </Binding.RelativeSource>  
</Binding>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="9fc28-107">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="9fc28-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`modeEnumValue`|<span data-ttu-id="9fc28-108">Aşağıdakilerden biri:</span><span class="sxs-lookup"><span data-stu-id="9fc28-108">One of the following:</span></span><br /><br /> <span data-ttu-id="9fc28-109">-Dize belirteci `Self`; karşılık gelen bir <xref:System.Windows.Data.RelativeSource> ile oluşturulmuş kendi <xref:System.Windows.Data.RelativeSource.Mode%2A> özelliğini <xref:System.Windows.Data.RelativeSourceMode.Self>.</span><span class="sxs-lookup"><span data-stu-id="9fc28-109">-   The string token `Self`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.Self>.</span></span><br /><span data-ttu-id="9fc28-110">-Dize belirteci `TemplatedParent`; karşılık gelen bir <xref:System.Windows.Data.RelativeSource> ile oluşturulmuş kendi <xref:System.Windows.Data.RelativeSource.Mode%2A> özelliğini <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.</span><span class="sxs-lookup"><span data-stu-id="9fc28-110">-   The string token `TemplatedParent`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.</span></span><br /><span data-ttu-id="9fc28-111">-Dize belirteci `PreviousData`; karşılık gelen bir <xref:System.Windows.Data.RelativeSource> ile oluşturulmuş kendi <xref:System.Windows.Data.RelativeSource.Mode%2A> özelliğini <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.</span><span class="sxs-lookup"><span data-stu-id="9fc28-111">-   The string token `PreviousData`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.</span></span><br /><span data-ttu-id="9fc28-112">-Aşağıda bilgi edinmek için `FindAncestor` modu.</span><span class="sxs-lookup"><span data-stu-id="9fc28-112">-   See below for information on `FindAncestor` mode.</span></span>|  
|`FindAncestor`|<span data-ttu-id="9fc28-113">Dize belirteci `FindAncestor`.</span><span class="sxs-lookup"><span data-stu-id="9fc28-113">The string token `FindAncestor`.</span></span> <span data-ttu-id="9fc28-114">Bu belirteci kullanarak moda girer bir `RelativeSource` bir üst türü ve isteğe bağlı olarak bir üst düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9fc28-114">Using this token enters a mode whereby a `RelativeSource` specifies an ancestor type and optionally an ancestor level.</span></span> <span data-ttu-id="9fc28-115">Bu karşılık gelen bir <xref:System.Windows.Data.RelativeSource> ile oluşturulmuş kendi <xref:System.Windows.Data.RelativeSource.Mode%2A> özelliğini <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.</span><span class="sxs-lookup"><span data-stu-id="9fc28-115">This corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.</span></span>|  
|`typeName`|<span data-ttu-id="9fc28-116">İçin gerekli `FindAncestor` modu.</span><span class="sxs-lookup"><span data-stu-id="9fc28-116">Required for `FindAncestor` mode.</span></span> <span data-ttu-id="9fc28-117">Doldurur bir türün adını <xref:System.Windows.Data.RelativeSource.AncestorType%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="9fc28-117">The name of a type, which fills the <xref:System.Windows.Data.RelativeSource.AncestorType%2A> property.</span></span>|  
|`intLevel`|<span data-ttu-id="9fc28-118">İçin isteğe bağlı `FindAncestor` modu.</span><span class="sxs-lookup"><span data-stu-id="9fc28-118">Optional for `FindAncestor` mode.</span></span> <span data-ttu-id="9fc28-119">Öncül düzeyi (Mantıksal ağaçta üst yön doğrultusunda değerlendirilen.)</span><span class="sxs-lookup"><span data-stu-id="9fc28-119">An ancestor level (evaluated towards the parent direction in the logical tree).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9fc28-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9fc28-120">Remarks</span></span>  
 <span data-ttu-id="9fc28-121">`{RelativeSource TemplatedParent}`bağlama kullanımları bir denetimin UI ve bir denetimin mantığı ayrılması daha büyük bir kavramı adresleri anahtar bir yöntem ' dir.</span><span class="sxs-lookup"><span data-stu-id="9fc28-121">`{RelativeSource TemplatedParent}` binding usages are a key technique that addresses a larger concept of the separation of a control's UI and a control's logic.</span></span> <span data-ttu-id="9fc28-122">Bu, şablon tanımı içinden şablonlu üst öğeye (şablonun uygulandığı çalışma zamanı nesnesi örneği) bağlanmaya olanak verir.</span><span class="sxs-lookup"><span data-stu-id="9fc28-122">This enables binding from within the template definition to the templated parent (the run time object instance where the template is applied).</span></span> <span data-ttu-id="9fc28-123">Bu durumda [TemplateBinding biçimlendirme uzantısı](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) aslında aşağıdaki bağlama ifadesi için bir toplu özelliktir: `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span><span class="sxs-lookup"><span data-stu-id="9fc28-123">For this case, the [TemplateBinding Markup Extension](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) is in fact a shorthand for the following binding expression: `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span></span> <span data-ttu-id="9fc28-124">`TemplateBinding`veya `{RelativeSource TemplatedParent}` kullanımları olan her ikisi de bir şablon tanımlayan XAML içinde yalnızca ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="9fc28-124">`TemplateBinding` or `{RelativeSource TemplatedParent}` usages are both only relevant within the XAML that defines a template.</span></span> <span data-ttu-id="9fc28-125">Daha fazla bilgi için bkz: [TemplateBinding biçimlendirme uzantısı](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)</span><span class="sxs-lookup"><span data-stu-id="9fc28-125">For more information, see [TemplateBinding Markup Extension](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)</span></span>  
  
 <span data-ttu-id="9fc28-126">`{RelativeSource FindAncestor}`esas olarak denetim şablonları veya tahmin edilebilir müstakil UI kompozisyonlarınıza, burada bir denetimi her zaman belirli bir üst türü görsel ağaçta olması beklenen durumlarda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9fc28-126">`{RelativeSource FindAncestor}` is mainly used in control templates or predictable self-contained UI compositions, for cases where a control is always expected to be in a visual tree of a certain ancestor type.</span></span> <span data-ttu-id="9fc28-127">Örneğin, bir öğe denetimini öğelerinin kullanabilirsiniz `FindAncestor` öğelerin özelliklerine bağlamak için kullanımları üst üst denetim.</span><span class="sxs-lookup"><span data-stu-id="9fc28-127">For example, items of an items control might use `FindAncestor` usages to bind to properties of their items control parent ancestor.</span></span> <span data-ttu-id="9fc28-128">Veya, bir şablon denetim oluşumuna parçası olan öğeleri kullanabilir `FindAncestor` bağlamaları aynı birleşim yapıyı üst öğe.</span><span class="sxs-lookup"><span data-stu-id="9fc28-128">Or, elements that are part of control composition in a template can use `FindAncestor` bindings to the parent elements in that same composition structure.</span></span>  
  
 <span data-ttu-id="9fc28-129">İçin nesne öğesi sözdiziminde `FindAncestor` ikinci nesne öğesi sözdizimi özellikle için kullanıldığından XAML sözdizimi bölümlerinde gösterilen modu `FindAncestor` modu.</span><span class="sxs-lookup"><span data-stu-id="9fc28-129">In the object element syntax for `FindAncestor` mode shown in the XAML Syntax sections, the second object element syntax is used specifically for `FindAncestor` mode.</span></span> <span data-ttu-id="9fc28-130">`FindAncestor`mod gerektiren bir <xref:System.Windows.Data.RelativeSource.AncestorType%2A> değeri.</span><span class="sxs-lookup"><span data-stu-id="9fc28-130">`FindAncestor` mode requires an <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value.</span></span> <span data-ttu-id="9fc28-131">Ayarlamalısınız <xref:System.Windows.Data.RelativeSource.AncestorType%2A> kullanarak bir öznitelik olarak bir [x: Type işaretleme uzantısı](../../../../docs/framework/xaml-services/x-type-markup-extension.md) aranacak üst tür referansı.</span><span class="sxs-lookup"><span data-stu-id="9fc28-131">You must set <xref:System.Windows.Data.RelativeSource.AncestorType%2A> as an attribute using an [x:Type Markup Extension](../../../../docs/framework/xaml-services/x-type-markup-extension.md) reference to the type of ancestor to look for.</span></span> <span data-ttu-id="9fc28-132"><xref:System.Windows.Data.RelativeSource.AncestorType%2A> Çalışma zamanında bağlama isteği işlendiğinde değeri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9fc28-132">The <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value is used when the binding request is processed at run-time.</span></span>  
  
 <span data-ttu-id="9fc28-133">İçin `FindAncestor` modu, isteğe bağlı özellik <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> durumlarda üst arama belirsizliğini ortadan kaldırmak yardımcı olabilecek büyük olasılıkla birden fazla üst öğe ağacında varolan türü olduğu.</span><span class="sxs-lookup"><span data-stu-id="9fc28-133">For `FindAncestor` mode, the optional property <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> can help disambiguate the ancestor lookup in cases where there is possibly more than one ancestor of that type existing in the element tree.</span></span>  
  
 <span data-ttu-id="9fc28-134">Nasıl kullanılacağı hakkında daha fazla bilgi için `FindAncestor` modu, bkz: <xref:System.Windows.Data.RelativeSource>.</span><span class="sxs-lookup"><span data-stu-id="9fc28-134">For more information on how to use the `FindAncestor` mode, see <xref:System.Windows.Data.RelativeSource>.</span></span>  
  
 <span data-ttu-id="9fc28-135">`{RelativeSource Self}`Senaryo için yararlıdır burada bir örneğinin bir özellik aynı örneği (örneğin, zorlama) herhangi bir genel bağımlılık özelliği ilişkisi ve başka bir özelliğin değeri zaten bağlı bu iki özellik arasında mevcut.</span><span class="sxs-lookup"><span data-stu-id="9fc28-135">`{RelativeSource Self}` is useful for scenarios where one property of an instance should depend on the value of another property of the same instance, and no general dependency property relationship (such as coercion) already exists between those two properties.</span></span> <span data-ttu-id="9fc28-136">İki özellik mevcut bir nesne üzerinde olduğunu değerlerin tam anlamıyla özdeş (ve aynı yazılan gibi), aynı zamanda uygulanabilir nadir olmasına rağmen bir `Converter` sahip bir bağlama parametresi `{RelativeSource Self}`ve kaynak arasında dönüştürmek için dönüştürücüyü kullanın ve Hedef türü.</span><span class="sxs-lookup"><span data-stu-id="9fc28-136">Although it is rare that two properties exist on an object such that the values are literally identical (and are identically typed), you can also apply a `Converter` parameter to a binding that has `{RelativeSource Self}`, and use the converter to convert between source and target types.</span></span> <span data-ttu-id="9fc28-137">Başka bir senaryo için `{RelativeSource Self}` parçası olarak bir <xref:System.Windows.MultiDataTrigger>.</span><span class="sxs-lookup"><span data-stu-id="9fc28-137">Another scenario for `{RelativeSource Self}` is as part of a <xref:System.Windows.MultiDataTrigger>.</span></span>  
  
 <span data-ttu-id="9fc28-138">Örneğin, aşağıdaki XAML tanımlayan bir <xref:System.Windows.Shapes.Rectangle> değerin ne olursa olsun için girilen öğesi böyle <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.Shapes.Rectangle> her zaman bir kare olur:`<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span><span class="sxs-lookup"><span data-stu-id="9fc28-138">For example, the following XAML defines a <xref:System.Windows.Shapes.Rectangle> element such that no matter what value is entered for <xref:System.Windows.FrameworkElement.Width%2A>, the <xref:System.Windows.Shapes.Rectangle> is always a square: `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span></span>  
  
 <span data-ttu-id="9fc28-139">`{RelativeSource PreviousData}`Veri şablonlarında ya da bağlamaları veri kaynağı olarak bir koleksiyon burada kullandığınız durumlarda yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="9fc28-139">`{RelativeSource PreviousData}` is useful either in data templates, or in cases where bindings are using a collection as the data source.</span></span> <span data-ttu-id="9fc28-140">Kullanabileceğiniz `{RelativeSource PreviousData}` koleksiyondaki bitişik veri öğeleri arasında ilişkiler vurgulayın.</span><span class="sxs-lookup"><span data-stu-id="9fc28-140">You can use `{RelativeSource PreviousData}` to highlight relationships between adjacent data items in the collection.</span></span> <span data-ttu-id="9fc28-141">İlişkili bir teknik belirtmektir bir <xref:System.Windows.Data.MultiBinding> veri kaynağı ve kullanım iki öğeyi ve bunların özelliklerini arasındaki farkı belirlemek için bu bağlama üzerinde bir dönüştürücü geçerli ve önceki öğeleri arasında.</span><span class="sxs-lookup"><span data-stu-id="9fc28-141">A related technique is to establish a <xref:System.Windows.Data.MultiBinding> between the current and previous items in the data source, and use a converter on that binding to determine the difference between the two items and their properties.</span></span>  
  
 <span data-ttu-id="9fc28-142">Aşağıdaki örnekte, ilk <xref:System.Windows.Controls.TextBlock> öğeleri şablonu geçerli numarasını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9fc28-142">In the following example, the first <xref:System.Windows.Controls.TextBlock> in the items template displays the current number.</span></span> <span data-ttu-id="9fc28-143">İkinci <xref:System.Windows.Controls.TextBlock> bağlamanın bir <xref:System.Windows.Data.MultiBinding> ismen iki olan <xref:System.Windows.Data.Binding> consistuents: geçerli kayıt ve kullanarak önceki veri kaydı kasıtlı olarak kullanan bir bağlama `{RelativeSource PreviousData}`.</span><span class="sxs-lookup"><span data-stu-id="9fc28-143">The second <xref:System.Windows.Controls.TextBlock> binding is a <xref:System.Windows.Data.MultiBinding> that nominally has two <xref:System.Windows.Data.Binding> consistuents: the current record, and a binding that deliberately uses the previous data record by using `{RelativeSource PreviousData}`.</span></span> <span data-ttu-id="9fc28-144">Ardından, bir dönüştürücü <xref:System.Windows.Data.MultiBinding> farkı hesaplar ve bağlamaya döndürür.</span><span class="sxs-lookup"><span data-stu-id="9fc28-144">Then, a converter on the <xref:System.Windows.Data.MultiBinding> calculates the difference and returns it to the binding.</span></span>  
  
```xml  
<ListBox Name="fibolist">  
    <ListBox.ItemTemplate>  
        <DataTemplate>  
            <StackPanel Orientation="Horizontal">  
            <TextBlock Text="{Binding}"/>  
            <TextBlock>, difference = </TextBlock>  
                <TextBlock>  
                    <TextBlock.Text>  
                        <MultiBinding Converter="{StaticResource DiffConverter}">  
                            <Binding/>  
                            <Binding RelativeSource="{RelativeSource PreviousData}"/>  
                        </MultiBinding>  
                    </TextBlock.Text>  
                </TextBlock>  
            </StackPanel>  
        </DataTemplate>  
    </ListBox.ItemTemplate>  
```  
  
 <span data-ttu-id="9fc28-145">Veri bağlama kavram burada kapsanmayan olarak açıklayan bkz [veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9fc28-145">Describing data binding as a concept is not covered here, see [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="9fc28-146">İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML işlemci uygulamasında, bu biçimlendirme uzantısı işlenmesi tarafından tanımlanan <xref:System.Windows.Data.RelativeSource> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9fc28-146">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.Data.RelativeSource> class.</span></span>  
  
 <span data-ttu-id="9fc28-147">`RelativeSource`bir biçimlendirme uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="9fc28-147">`RelativeSource` is a markup extension.</span></span> <span data-ttu-id="9fc28-148">Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır.</span><span class="sxs-lookup"><span data-stu-id="9fc28-148">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="9fc28-149">XAML Kullanımdaki tüm biçimlendirme uzantıları `{` ve `}` olarak XAML işlemci tanıdığı biçimlendirme uzantısı öznitelik işlemelidir kuralı kendi öznitelik sözdiziminde karakterler.</span><span class="sxs-lookup"><span data-stu-id="9fc28-149">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="9fc28-150">Daha fazla bilgi için bkz: [biçimlendirme uzantıları ve WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="9fc28-150">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fc28-151">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9fc28-151">See Also</span></span>  
 <xref:System.Windows.Data.Binding>  
 [<span data-ttu-id="9fc28-152">Stil ve şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="9fc28-152">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="9fc28-153">XAML genel bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="9fc28-153">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="9fc28-154">Biçimlendirme uzantıları ve WPF XAML</span><span class="sxs-lookup"><span data-stu-id="9fc28-154">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="9fc28-155">Veri bağlama genel bakış</span><span class="sxs-lookup"><span data-stu-id="9fc28-155">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="9fc28-156">Bağlama bildirimleri genel bakış</span><span class="sxs-lookup"><span data-stu-id="9fc28-156">Binding Declarations Overview</span></span>](../../../../docs/framework/wpf/data/binding-declarations-overview.md)  
 [<span data-ttu-id="9fc28-157">x: Type işaretleme uzantısı</span><span class="sxs-lookup"><span data-stu-id="9fc28-157">x:Type Markup Extension</span></span>](../../../../docs/framework/xaml-services/x-type-markup-extension.md)