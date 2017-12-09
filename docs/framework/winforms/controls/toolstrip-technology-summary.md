---
title: "ToolStrip Teknoloiji Özeti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStrip control [Windows Forms], technology summary
- status bars [Windows Forms], technology summary
- toolbars [Windows Forms], technology summary
- menus [Windows Forms], technology summary
ms.assetid: e8d61973-7af9-429f-9df5-05a899c15a7b
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 75b340bfb2d9106827d39a3253f65f3c2419bd94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="toolstrip-technology-summary"></a><span data-ttu-id="8ea5f-102">ToolStrip Teknoloiji Özeti</span><span class="sxs-lookup"><span data-stu-id="8ea5f-102">ToolStrip Technology Summary</span></span>
<span data-ttu-id="8ea5f-103">Bu konu hakkında bilgileri özetler `ToolStrip` denetimi ve kullanımını destekleyen sınıflar.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-103">This topic summarizes information about the `ToolStrip` control and the classes that support its use.</span></span>  
  
 <span data-ttu-id="8ea5f-104">`ToolStrip` Denetim ve onun ilişkili sınıfları sağlar eksiksiz bir çözüm araç çubukları, durum çubukları ve menüleri oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-104">The `ToolStrip` control and its associated classes provide a complete solution for creating toolbars, status bars, and menus.</span></span>  
  
## <a name="namespaces"></a><span data-ttu-id="8ea5f-105">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="8ea5f-105">Namespaces</span></span>  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
## <a name="background"></a><span data-ttu-id="8ea5f-106">Arka Plan</span><span class="sxs-lookup"><span data-stu-id="8ea5f-106">Background</span></span>  
 <span data-ttu-id="8ea5f-107">İle `ToolStrip` denetim ve onun ilişkili sınıfları, tutarlı ve profesyonel bir görünüm ve davranış olan Gelişmiş araç işlevselliği oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-107">With the `ToolStrip` control and its associated classes, you can create advanced toolbar functionality that has consistent and professional appearance and behavior.</span></span> <span data-ttu-id="8ea5f-108">`ToolStrip` Denetim ve sınıfları önceki denetimleri aşağıdaki geliştirmeleri sunar:</span><span class="sxs-lookup"><span data-stu-id="8ea5f-108">The `ToolStrip` control and classes offer the following improvements over previous controls:</span></span>  
  
-   <span data-ttu-id="8ea5f-109">Daha tutarlı bir olay modeli.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-109">A more consistent event model.</span></span>  
  
-   <span data-ttu-id="8ea5f-110">Görev listeleri ve madde koleksiyon düzenleyiciler içeren daha tutarlı bir tasarım zamanı davranışı.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-110">A more consistent design-time behavior that contains task lists and item collection editors.</span></span>  
  
-   <span data-ttu-id="8ea5f-111">Özel işleme ile `ToolStripManager` ve `ToolStripRenderer`.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-111">Custom rendering with `ToolStripManager` and `ToolStripRenderer`.</span></span>  
  
-   <span data-ttu-id="8ea5f-112">Yerleşik radye ile (yerleştirildiğinde aracı alanda yatay veya dikey alanı paylaşımı) `ToolStripContainer` ve `ToolStripPanel`.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-112">Built-in rafting (sharing of horizontal or vertical space within the tool area when docked) with the `ToolStripContainer` and `ToolStripPanel`.</span></span>  
  
-   <span data-ttu-id="8ea5f-113">Tasarım zamanı ve çalışma zamanı ile öğelerinin yeniden sıralanmasını <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-113">Design-time and run-time reordering of items with the <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> property.</span></span>  
  
-   <span data-ttu-id="8ea5f-114">Taşma menüsüyle öğelerin yeniden konumlandırma <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-114">Relocation of items to an overflow menu with the <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> property.</span></span>  
  
-   <span data-ttu-id="8ea5f-115">Tamamen yapılandırılabilir denetim konumla `ToolStripContainer`, `ToolStripPanel`, ve `ToolStripContentPanel`.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-115">Completely configurable control location with the `ToolStripContainer`, `ToolStripPanel`, and `ToolStripContentPanel`.</span></span>  
  
-   <span data-ttu-id="8ea5f-116">Barındırma `ToolStrip`, geleneksel ya da özel denetimler kullanarak `ToolStripControlHost`.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-116">Hosting of `ToolStrip`, traditional, or custom controls using `ToolStripControlHost`.</span></span>  
  
-   <span data-ttu-id="8ea5f-117">Birleştirme `ToolStrip` denetimlerini kullanma `ToolStripPanel`.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-117">Merging of `ToolStrip` controls using `ToolStripPanel`.</span></span>  
  
 <span data-ttu-id="8ea5f-118">`ToolStrip`Genişletilebilir temel sınıfı olan `MenuStrip`, `ContextMenuStrip`, ve `StatusStrip`.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-118">`ToolStrip` is the extensible base class for `MenuStrip`, `ContextMenuStrip`, and `StatusStrip`.</span></span> <span data-ttu-id="8ea5f-119">Bu denetimler <xref:System.Windows.Forms.ToolStripItem> ortak davranışı ve olay işleme devralır kapsayıcıları genişlettiğini her uygulama için uygun davranışı ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-119">These controls are <xref:System.Windows.Forms.ToolStripItem> containers that inherit common behavior and event handling, extended so that each implementation deals with the behavior that is appropriate for it.</span></span> <span data-ttu-id="8ea5f-120">Öğesinden türetilen denetimler <xref:System.Windows.Forms.ToolStripItem> aşağıdaki tabloda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-120">Controls that derive from <xref:System.Windows.Forms.ToolStripItem> are listed in the following table.</span></span> <span data-ttu-id="8ea5f-121">Temel `ToolStrip` sınıfı boyama, kullanıcı girişi ve bu denetimleri için sürükle ve bırak olayları işler.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-121">The base `ToolStrip` class handles painting, user input, and drag-and-drop events for these controls.</span></span>  
  
 <span data-ttu-id="8ea5f-122">`ToolStrip`, `MenuStrip`, `ContextMenuStrip`, Ve `StatusStrip` denetimleri, önceki araç, menü, kısayol menüsünde ve durum çubuğu denetimleri, bu denetimleri geriye dönük uyumluluk için korunur rağmen değiştirin.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-122">The `ToolStrip`, `MenuStrip`, `ContextMenuStrip`, and `StatusStrip` controls replace the previous toolbar, menu, shortcut menu, and status bar controls, although those controls are retained for backward compatibility.</span></span>  
  
## <a name="toolstrip-classes-at-a-glance"></a><span data-ttu-id="8ea5f-123">Bir bakışta ToolStrip sınıfları</span><span class="sxs-lookup"><span data-stu-id="8ea5f-123">ToolStrip Classes at a Glance</span></span>  
 <span data-ttu-id="8ea5f-124">Aşağıdaki tabloda teknoloji alanına göre gruplandırılmış ToolStrip sınıflarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-124">The following table shows the ToolStrip classes grouped by technology area.</span></span>  
  
|<span data-ttu-id="8ea5f-125">Teknoloji alanı</span><span class="sxs-lookup"><span data-stu-id="8ea5f-125">Technology area</span></span>|<span data-ttu-id="8ea5f-126">örneği</span><span class="sxs-lookup"><span data-stu-id="8ea5f-126">Class</span></span>|  
|---------------------|-----------|  
|<span data-ttu-id="8ea5f-127">Araç, durum ve menü kapsayıcıları</span><span class="sxs-lookup"><span data-stu-id="8ea5f-127">Toolbar, Status, and Menu containers</span></span>|<xref:System.Windows.Forms.ToolStrip><br /><br /> <xref:System.Windows.Forms.MenuStrip><br /><br /> <xref:System.Windows.Forms.ContextMenuStrip><br /><br /> <xref:System.Windows.Forms.StatusStrip><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownMenu>|  
|<span data-ttu-id="8ea5f-128">ToolStrip öğeleri</span><span class="sxs-lookup"><span data-stu-id="8ea5f-128">ToolStrip items</span></span>|<xref:System.Windows.Forms.ToolStripLabel><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownItem><br /><br /> <xref:System.Windows.Forms.ToolStripMenuItem><br /><br /> <xref:System.Windows.Forms.ToolStripButton><br /><br /> <xref:System.Windows.Forms.ToolStripStatusLabel><br /><br /> <xref:System.Windows.Forms.ToolStripSeparator><br /><br /> <xref:System.Windows.Forms.ToolStripControlHost><br /><br /> <xref:System.Windows.Forms.ToolStripComboBox><br /><br /> <xref:System.Windows.Forms.ToolStripTextBox><br /><br /> <xref:System.Windows.Forms.ToolStripProgressBar><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownButton><br /><br /> <xref:System.Windows.Forms.ToolStripSplitButton>|  
|<span data-ttu-id="8ea5f-129">Konum</span><span class="sxs-lookup"><span data-stu-id="8ea5f-129">Location</span></span>|<xref:System.Windows.Forms.ToolStripContainer><br /><br /> <xref:System.Windows.Forms.ToolStripContentPanel><br /><br /> <xref:System.Windows.Forms.ToolStripPanel>|  
|<span data-ttu-id="8ea5f-130">Sunu ve işleme</span><span class="sxs-lookup"><span data-stu-id="8ea5f-130">Presentation and rendering</span></span>|<xref:System.Windows.Forms.ToolStripManager><br /><br /> <xref:System.Windows.Forms.ToolStripRenderer><br /><br /> <xref:System.Windows.Forms.ToolStripProfessionalRenderer><br /><br /> <xref:System.Windows.Forms.ToolStripRenderMode><br /><br /> <xref:System.Windows.Forms.ToolStripManagerRenderMode>|  
  
## <a name="toolstrip-design-time-features"></a><span data-ttu-id="8ea5f-131">ToolStrip tasarım-zamanı özellikleri</span><span class="sxs-lookup"><span data-stu-id="8ea5f-131">ToolStrip Design-Time Features</span></span>  
 <span data-ttu-id="8ea5f-132"><xref:System.Windows.Forms.ToolStrip> Denetimlerin ailesi, düzenleme ve hızla çalışan bir uygulama oluşturabilmesi için kullanıcı arabiriminin foundation tanımlama yerinde için zengin bir araç ve şablonları sağlar.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-132">The <xref:System.Windows.Forms.ToolStrip> family of controls provides a rich set of tools and templates for in-place editing and defining the foundation of the user interface so that you can quickly create a working application.</span></span>  
  
### <a name="task-dialog-boxes"></a><span data-ttu-id="8ea5f-133">Görev iletişim kutuları</span><span class="sxs-lookup"><span data-stu-id="8ea5f-133">Task Dialog Boxes</span></span>  
 <span data-ttu-id="8ea5f-134">Visual Studio'da bir denetim Tasarımcısı'nda akıllı etiket tıklatarak kolay erişim için bir görev listesi çok sık kullanılan komutlar için görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-134">In Visual Studio, clicking the smart tag on a control in the designer displays a task list for convenient access to many frequently used commands.</span></span>  
  
-   <span data-ttu-id="8ea5f-135">[MenuStrip görevler iletişim kutusu](http://msdn.microsoft.com/library/ms233645\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="8ea5f-135">[MenuStrip Tasks Dialog Box](http://msdn.microsoft.com/library/ms233645\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="8ea5f-136">[ToolStrip görevler iletişim kutusu](http://msdn.microsoft.com/library/ms233648\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="8ea5f-136">[ToolStrip Tasks Dialog Box](http://msdn.microsoft.com/library/ms233648\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="8ea5f-137">[ContextMenuStrip görevler iletişim kutusu](http://msdn.microsoft.com/library/ms233646\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="8ea5f-137">[ContextMenuStrip Tasks Dialog Box](http://msdn.microsoft.com/library/ms233646\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="8ea5f-138">[StatusStrip görevler iletişim kutusu](http://msdn.microsoft.com/library/ms233642\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="8ea5f-138">[StatusStrip Tasks Dialog Box](http://msdn.microsoft.com/library/ms233642\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="8ea5f-139">[ToolStripContainer görevler iletişim kutusu](http://msdn.microsoft.com/library/ms233647\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="8ea5f-139">[ToolStripContainer Tasks Dialog Box](http://msdn.microsoft.com/library/ms233647\(v=vs.110\))</span></span>  
  
### <a name="items-collection-editors"></a><span data-ttu-id="8ea5f-140">Öğeleri koleksiyon düzenleyiciler</span><span class="sxs-lookup"><span data-stu-id="8ea5f-140">Items Collection Editors</span></span>  
 <span data-ttu-id="8ea5f-141">Visual Studio'da tıkladığınızda, **öğe düzenleme** görev listesi veya seçin ve denetim sağ **öğe düzenleme** denetimi için koleksiyon Düzenleyicisi'ni kısayol menüsünde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-141">In Visual Studio, when you click **Edit Items** on the task list or right-click the control and select **Edit Items** in the shortcut menu, the collection editor for the control is displayed.</span></span> <span data-ttu-id="8ea5f-142">Koleksiyon düzenleyiciler, eklemek, kaldırmak ve denetimi içeren öğeleri yeniden sıralamak olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-142">Collection editors let you add, remove, and reorder items that the control contains.</span></span> <span data-ttu-id="8ea5f-143">Ayrıca, görüntüleyin ve denetim ve denetimin öğeleri özelliklerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-143">You can also view and change the properties for the control and the control's items.</span></span>  
  
-   <span data-ttu-id="8ea5f-144">[MenuStrip öğeleri koleksiyonu Düzenleyicisi](http://msdn.microsoft.com/library/ms233625\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="8ea5f-144">[MenuStrip Items Collection Editor](http://msdn.microsoft.com/library/ms233625\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="8ea5f-145">[StatusStrip öğeleri koleksiyonu Düzenleyicisi](http://msdn.microsoft.com/library/ms233631\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="8ea5f-145">[StatusStrip Items Collection Editor](http://msdn.microsoft.com/library/ms233631\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="8ea5f-146">[ContextMenuStrip öğeleri koleksiyonu Düzenleyicisi](http://msdn.microsoft.com/library/ms233641\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="8ea5f-146">[ContextMenuStrip Items Collection Editor](http://msdn.microsoft.com/library/ms233641\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="8ea5f-147">[ToolStrip öğeleri koleksiyonu Düzenleyicisi](http://msdn.microsoft.com/library/ms233643\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="8ea5f-147">[ToolStrip Items Collection Editor](http://msdn.microsoft.com/library/ms233643\(v=vs.110\))</span></span>  
  
## <a name="hosting-controls"></a><span data-ttu-id="8ea5f-148">Denetimleri barındırma</span><span class="sxs-lookup"><span data-stu-id="8ea5f-148">Hosting Controls</span></span>  
 <span data-ttu-id="8ea5f-149"><xref:System.Windows.Forms.ToolStripControlHost> SAX için yerleşik sarmalayıcıları <xref:System.Windows.Forms.ToolStripComboBox>, <xref:System.Windows.Forms.ToolStripTextBox>, ve <xref:System.Windows.Forms.ToolStripProgressBar> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-149">The <xref:System.Windows.Forms.ToolStripControlHost> class provides built-in wrappers for <xref:System.Windows.Forms.ToolStripComboBox>, <xref:System.Windows.Forms.ToolStripTextBox>, and <xref:System.Windows.Forms.ToolStripProgressBar> controls.</span></span> <span data-ttu-id="8ea5f-150">Başka var veya COM denetimi de barındırabilir bir <xref:System.Windows.Forms.ToolStripControlHost>.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-150">You can also host any other existing or COM control in a <xref:System.Windows.Forms.ToolStripControlHost>.</span></span>  
  
 <span data-ttu-id="8ea5f-151">Denetimi barındırma örneği için bkz: [nasıl yapılır: ToolStripControlHost ile Windows Forms denetimini kaydırma](../../../../docs/framework/winforms/controls/how-to-wrap-a-windows-forms-control-with-toolstripcontrolhost.md).</span><span class="sxs-lookup"><span data-stu-id="8ea5f-151">For an example of control hosting, see [How to: Wrap a Windows Forms Control with ToolStripControlHost](../../../../docs/framework/winforms/controls/how-to-wrap-a-windows-forms-control-with-toolstripcontrolhost.md).</span></span>  
  
## <a name="rendering"></a><span data-ttu-id="8ea5f-152">İşleme</span><span class="sxs-lookup"><span data-stu-id="8ea5f-152">Rendering</span></span>  
 <span data-ttu-id="8ea5f-153"><xref:System.Windows.Forms.ToolStrip>sınıfları diğer Windows Forms denetimlerini önemli ölçüde farklı bir işleme uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-153"><xref:System.Windows.Forms.ToolStrip> classes implement a rendering scheme that is significantly different from other Windows Forms controls.</span></span> <span data-ttu-id="8ea5f-154">Bu düzeniyle stilleri ve Temalar kolayca uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-154">With this scheme, you can easily apply styles and themes.</span></span>  
  
 <span data-ttu-id="8ea5f-155">Stil uygulamak için bir <xref:System.Windows.Forms.ToolStrip> ve tüm <xref:System.Windows.Forms.ToolStripItem> içerdiği nesneleri sahip olmadığınız işlemek <xref:System.Windows.Forms.ToolStripItem.Paint> her öğe için bir olay.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-155">To apply a style to a <xref:System.Windows.Forms.ToolStrip> and all the <xref:System.Windows.Forms.ToolStripItem> objects it contains, you do not have to handle the <xref:System.Windows.Forms.ToolStripItem.Paint> event for each item.</span></span> <span data-ttu-id="8ea5f-156">Bunun yerine, ayarlayabileceğiniz <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> özelliğini birine <xref:System.Windows.Forms.ToolStripRenderMode> dışındaki değerleri <xref:System.Windows.Forms.ToolStripRenderMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-156">Instead, you can set the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> property to one of the <xref:System.Windows.Forms.ToolStripRenderMode> values other than <xref:System.Windows.Forms.ToolStripRenderMode.Custom>.</span></span> <span data-ttu-id="8ea5f-157">Alternatif olarak, ayarlayabileceğiniz <xref:System.Windows.Forms.ToolStrip.Renderer%2A> doğrudan öğesinden devralınan bir sınıf için <xref:System.Windows.Forms.ToolStripRenderer> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-157">Alternatively, you can set the <xref:System.Windows.Forms.ToolStrip.Renderer%2A> directly to any class that inherits from the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span> <span data-ttu-id="8ea5f-158">Bu özelliği otomatik olarak ayarlar ayarı <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-158">Setting this property automatically sets the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>.</span></span>  
  
 <span data-ttu-id="8ea5f-159">Birden çok aynı stili uygulayabilirsiniz <xref:System.Windows.Forms.ToolStrip> ayarlayarak aynı uygulamada nesneler <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> için <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode> ve ayarı <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A> veya <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> özelliğine <xref:System.Windows.Forms.ToolStripManagerRenderMode> istediğiniz veya <xref:System.Windows.Forms.ToolStripRenderer> değeri sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-159">You can apply the same style to multiple <xref:System.Windows.Forms.ToolStrip> objects in the same application by setting the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode> and setting the <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A> or <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> property to <xref:System.Windows.Forms.ToolStripManagerRenderMode> that you want or <xref:System.Windows.Forms.ToolStripRenderer> value, respectively.</span></span>  
  
 <span data-ttu-id="8ea5f-160">İşleme örnekleri için bkz: [nasıl yapılır: Windows Forms'ta ToolStrip denetimi için özel Oluşturucu oluşturup](../../../../docs/framework/winforms/controls/create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md).</span><span class="sxs-lookup"><span data-stu-id="8ea5f-160">For examples of rendering, see [How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms](../../../../docs/framework/winforms/controls/create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md).</span></span>  
  
## <a name="styles-and-themes"></a><span data-ttu-id="8ea5f-161">Stilleri ve Temalar</span><span class="sxs-lookup"><span data-stu-id="8ea5f-161">Styles and Themes</span></span>  
 <span data-ttu-id="8ea5f-162"><xref:System.Windows.Forms.ToolStrip>ve ilişkili sınıfları sağlar görsel stilleri ve geçersiz kılma gerektirmeyen özel görünüm desteklemek için kolay bir yol <xref:System.Windows.Forms.ToolStripItem.OnPaint%2A> her öğe için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-162"><xref:System.Windows.Forms.ToolStrip> and associated classes provide an easy way to support visual styles and custom appearance that do not require overriding the <xref:System.Windows.Forms.ToolStripItem.OnPaint%2A> methods for each item.</span></span> <span data-ttu-id="8ea5f-163">Kullanım <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> ve <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> ve <xref:System.Windows.Forms.ToolStrip.Renderer%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-163">Use the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> and the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> and <xref:System.Windows.Forms.ToolStrip.Renderer%2A> properties.</span></span>  
  
## <a name="rafting-and-docking"></a><span data-ttu-id="8ea5f-164">Radye ve yerleştirme</span><span class="sxs-lookup"><span data-stu-id="8ea5f-164">Rafting and Docking</span></span>  
 <span data-ttu-id="8ea5f-165">Raft, yerleştirme veya için mutlak konumlandırılması <xref:System.Windows.Forms.ToolStrip> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-165">You can raft, dock, or absolutely position <xref:System.Windows.Forms.ToolStrip> controls.</span></span> <span data-ttu-id="8ea5f-166"><xref:System.Windows.Forms.ToolStrip>öğeleri düzenlenir <xref:System.Windows.Forms.ToolStrip.LayoutEngine%2A> kapsayıcısının.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-166"><xref:System.Windows.Forms.ToolStrip> items are laid out by the <xref:System.Windows.Forms.ToolStrip.LayoutEngine%2A> of the container.</span></span>  
  
 <span data-ttu-id="8ea5f-167">*Radye* yatay veya dikey boşluk paylaşmak için araç çubukları özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-167">*Rafting* is the ability of toolbars to share horizontal or vertical space.</span></span> <span data-ttu-id="8ea5f-168">Bir Windows formunda olabilir bir <xref:System.Windows.Forms.ToolStripContainer> formun sol, sağ, üst ve alt kenarı konumlandırma ve radye panoları sırayla sahip <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, ve <xref:System.Windows.Forms.StatusStrip> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-168">A Windows form can have a <xref:System.Windows.Forms.ToolStripContainer> that in turn has panels on the form's left, right, top, and bottom sides for positioning and rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="8ea5f-169">Birden çok <xref:System.Windows.Forms.ToolStrip> denetimleri yığın dikey bunları sola veya sağa moduna geçirirseniz <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-169">Multiple <xref:System.Windows.Forms.ToolStrip> controls stack vertically if you put them in the left or right <xref:System.Windows.Forms.ToolStripContainer>.</span></span> <span data-ttu-id="8ea5f-170">Bunları üstüne veya altına yerleştirin varsa bunlar yatay yığın <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-170">They stack horizontally if you put them in the top or bottom <xref:System.Windows.Forms.ToolStripContainer>.</span></span> <span data-ttu-id="8ea5f-171">Orta kullanabilirsiniz <xref:System.Windows.Forms.ToolStripContentPanel> , <xref:System.Windows.Forms.ToolStripContainer> geleneksel denetimleri form üzerinde konumlandırmak için.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-171">You can use the central <xref:System.Windows.Forms.ToolStripContentPanel> of the <xref:System.Windows.Forms.ToolStripContainer> to position traditional controls on the form.</span></span>  
  
 <span data-ttu-id="8ea5f-172">Tüm <xref:System.Windows.Forms.ToolStripContainer> denetimleri tasarım zamanında doğrudan seçilebilir ve silinebilir.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-172">Any or all <xref:System.Windows.Forms.ToolStripContainer> controls are directly selectable at design time and can be deleted.</span></span> <span data-ttu-id="8ea5f-173">A <xref:System.Windows.Forms.ToolStripContainer> genişletilebilir ve daraltılabilir ve içerdiği denetimleriyle göre yeniden boyutlandırır.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-173">A <xref:System.Windows.Forms.ToolStripContainer> is expandable and collapsible, and resizes with the controls that it contains.</span></span>  
  
 <span data-ttu-id="8ea5f-174">*Yerleştirme* formun sol, sağ, üst veya alt kenar basit konumunda bir denetimin belirtilmesi.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-174">*Docking* is the specifying of a control's simple location on the form's left, right, top, or bottom side.</span></span>  
  
 <span data-ttu-id="8ea5f-175">Yerleştirme üzerinden radye avantajı olan <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, ve <xref:System.Windows.Forms.StatusStrip> denetimleri başka denetimlerle birlikte yatay veya dikey boşluk paylaşabilir.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-175">The advantage of rafting over docking is that <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, and <xref:System.Windows.Forms.StatusStrip> controls can share horizontal or vertical space with other controls.</span></span>  
  
 <span data-ttu-id="8ea5f-176">Çoğu <xref:System.Windows.Forms.ToolStrip> denetimleri yerleşik radye kullanmak yerine diğer denetimleri gibi forma.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-176">Most of the <xref:System.Windows.Forms.ToolStrip> controls can be docked to the form like other controls instead of using rafting.</span></span> <span data-ttu-id="8ea5f-177">Ayrıca belirtebilirsiniz bir <xref:System.Windows.Forms.ToolStrip> denetim serbestçe konumlandırılmış formda grubundan kaldırarak kendi <xref:System.Windows.Forms.ToolStripContainer> ve ayarı kendi `Dock` özelliğine `None`, veya ilgili ayarlayarak mutlak konumunu belirtebilirsiniz <xref:System.Windows.Forms.Control.Location%2A> özellik.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-177">You can also specify that a <xref:System.Windows.Forms.ToolStrip> control be freely positioned on the form by removing it from its <xref:System.Windows.Forms.ToolStripContainer> and setting its `Dock` property to `None`, or you can specify its absolute position by setting the respective <xref:System.Windows.Forms.Control.Location%2A> property.</span></span> <span data-ttu-id="8ea5f-178">Bkz: [nasıl yapılır: forma ToolStripContainer ToolStrip dışı taşıma](../../../../docs/framework/winforms/controls/how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="8ea5f-178">See [How to: Move a ToolStrip Out of a ToolStripContainer onto a Form](../../../../docs/framework/winforms/controls/how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form.md).</span></span>  
  
 <span data-ttu-id="8ea5f-179">Bir veya daha fazla <xref:System.Windows.Forms.ToolStripPanel> özellikle birden çok belge arabirimi (MDI) uygulamaları için daha fazla esneklik için denetimleri veya ihtiyacınız yoksa bir <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-179">Use one or more <xref:System.Windows.Forms.ToolStripPanel> controls for more flexibility, especially for Multiple Document Interface (MDI) applications, or if you do not need a <xref:System.Windows.Forms.ToolStripContainer>.</span></span> <span data-ttu-id="8ea5f-180">A <xref:System.Windows.Forms.ToolStripPanel> dockable alanı bulma ve radye sağlar <xref:System.Windows.Forms.ToolStrip> denetimleri ancak değil geleneksel kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-180">A <xref:System.Windows.Forms.ToolStripPanel> provides a dockable space for locating and rafting <xref:System.Windows.Forms.ToolStrip> controls but not traditional controls.</span></span> <span data-ttu-id="8ea5f-181">Varsayılan olarak, <xref:System.Windows.Forms.ToolStripPanel> Tasarımcısı'nda görünmez **araç**, ancak bunu var. sağ tıklayarak put **araç**ve ardından **öğeleri Seç**.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-181">By default, the <xref:System.Windows.Forms.ToolStripPanel> does not appear in the designer **Toolbox**, but you can put it there by right-clicking the **Toolbox**, and then click **Choose Items**.</span></span> <span data-ttu-id="8ea5f-182">Program aracılığıyla da erişebilirsiniz <xref:System.Windows.Forms.ToolStripPanel> ister başka bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-182">You can also programmatically access the <xref:System.Windows.Forms.ToolStripPanel> like any other class.</span></span>  
  
 <span data-ttu-id="8ea5f-183"><xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, Ve <xref:System.Windows.Forms.StatusStrip> öğeleri taşma olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-183">The <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, and <xref:System.Windows.Forms.StatusStrip> let items overflow.</span></span> <span data-ttu-id="8ea5f-184">Bu, Microsoft Office araç çubuklarında bu öğeler davranır şekilde benzer.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-184">This is similar to the way these items behave on Microsoft Office toolbars.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ea5f-185">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8ea5f-185">See Also</span></span>  
 [<span data-ttu-id="8ea5f-186">ToolStrip denetimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="8ea5f-186">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [<span data-ttu-id="8ea5f-187">ToolStrip denetim mimarisi</span><span class="sxs-lookup"><span data-stu-id="8ea5f-187">ToolStrip Control Architecture</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)