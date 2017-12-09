---
title: "Grafik İşleme Kayıt Defteri Ayarları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- rendering graphics [WPF], registry settings
- rendering graphics [WPF]
- rendering graphics [WPF], troubleshooting
- troubleshooting graphics rendering [WPF]
- graphics [WPF], rendering
ms.assetid: f4b41b42-327d-407c-b398-3ed5f505df8b
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c1a86d715edb68564d6ebfcc8a419e333da4ea03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="graphics-rendering-registry-settings"></a><span data-ttu-id="8d631-102">Grafik İşleme Kayıt Defteri Ayarları</span><span class="sxs-lookup"><span data-stu-id="8d631-102">Graphics Rendering Registry Settings</span></span>
<span data-ttu-id="8d631-103">Bu konu genel bir bakış sağlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] etkileyen kayıt defteri ayarlarını grafik oluşturma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="8d631-103">This topic provides an overview of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] graphics rendering registry settings that affect [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span>  
  

  
<a name="overview"></a>   
## <a name="when-to-use-graphics-rendering-registry-settings"></a><span data-ttu-id="8d631-104">Grafik işleme kayıt defteri ayarları kullanmak ne zaman</span><span class="sxs-lookup"><span data-stu-id="8d631-104">When to Use Graphics Rendering Registry Settings</span></span>  
 <span data-ttu-id="8d631-105">Bu kayıt defteri ayarları, sorun giderme, hata ayıklama ve ürün destek amaçları için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="8d631-105">These registry settings are provided for troubleshooting, debugging, and product support purposes.</span></span> <span data-ttu-id="8d631-106">Kayıt defterinde değişiklik tüm etkilediğinden [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar, uygulamanız hiçbir zaman alter bu kayıt defteri anahtarları otomatik olarak veya yükleme sırasında.</span><span class="sxs-lookup"><span data-stu-id="8d631-106">Because changes to the registry affect all [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications, your application should never alter these registry keys automatically, or during installation.</span></span>  
  
<a name="xpdmandwddm"></a>   
## <a name="what-are-xpdm-and-wddm"></a><span data-ttu-id="8d631-107">XPDM ve WDDM nedir?</span><span class="sxs-lookup"><span data-stu-id="8d631-107">What are XPDM and WDDM?</span></span>  
 <span data-ttu-id="8d631-108">Grafik kayıt defteri ayarları işleme bazıları video kartınız bir XPDM veya WDDM sürücüsünü kullanıp kullanmadığını bağlı olarak farklı varsayılan değerlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8d631-108">Some of the graphics rendering registry settings have different default values, depending on whether your video card uses an XPDM or WDDM driver.</span></span> <span data-ttu-id="8d631-109">XPDM [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] görüntü sürücüsü modeli ve WDDM olan Windows görüntü sürücüsü modeli.</span><span class="sxs-lookup"><span data-stu-id="8d631-109">XPDM is the [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] Display Driver Model and WDDM is the Windows Display Driver Model.</span></span> <span data-ttu-id="8d631-110">WDDM çalıştıran bilgisayarlarda kullanılabilir [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] ve [!INCLUDE[win7](../../../../includes/win7-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8d631-110">WDDM is available on computers running [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] and [!INCLUDE[win7](../../../../includes/win7-md.md)].</span></span> <span data-ttu-id="8d631-111">XPDM çalıştıran bilgisayarlarda kullanılabilir [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)], [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)], ve [!INCLUDE[TLA#tla_winnetsvrfam](../../../../includes/tlasharptla-winnetsvrfam-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8d631-111">XPDM is available on computers running [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)], [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)], and [!INCLUDE[TLA#tla_winnetsvrfam](../../../../includes/tlasharptla-winnetsvrfam-md.md)].</span></span> <span data-ttu-id="8d631-112">WDDM hakkında daha fazla bilgi için bkz: [Windows Vista görüntü sürücüsü modeli Tasarım Kılavuzu](http://go.microsoft.com/fwlink/?LinkId=178394).</span><span class="sxs-lookup"><span data-stu-id="8d631-112">For more information about WDDM, see [Windows Vista Display Driver Model Design Guide](http://go.microsoft.com/fwlink/?LinkId=178394).</span></span>  
  
<a name="registry_settings"></a>   
## <a name="registry-settings"></a><span data-ttu-id="8d631-113">Kayıt defteri ayarları</span><span class="sxs-lookup"><span data-stu-id="8d631-113">Registry Settings</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="8d631-114">dört kayıt defteri ayarlarını denetlemek için sağlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] işleme:</span><span class="sxs-lookup"><span data-stu-id="8d631-114"> provides four registry settings for controlling [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rendering:</span></span>  
  
|<span data-ttu-id="8d631-115">Ayar</span><span class="sxs-lookup"><span data-stu-id="8d631-115">Setting</span></span>|<span data-ttu-id="8d631-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8d631-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8d631-117">**Donanım hızlandırma seçeneği devre dışı bırak**</span><span class="sxs-lookup"><span data-stu-id="8d631-117">**Disable Hardware Acceleration Option**</span></span>|<span data-ttu-id="8d631-118">Donanım hızlandırma etkin olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8d631-118">Specifies whether hardware acceleration should be enabled.</span></span>|  
|<span data-ttu-id="8d631-119">**En büyük çoklu örneklem değeri**</span><span class="sxs-lookup"><span data-stu-id="8d631-119">**Maximum Multisample Value**</span></span>|<span data-ttu-id="8d631-120">Düzgünleştirmek için çoklu örnekleme derecesini belirtir [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] içeriği.</span><span class="sxs-lookup"><span data-stu-id="8d631-120">Specifies the degree of multisampling for antialiasing [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] content.</span></span>|  
|<span data-ttu-id="8d631-121">**Gerekli ekran kartı sürücüsü tarih ayarı**</span><span class="sxs-lookup"><span data-stu-id="8d631-121">**Required Video Driver Date Setting**</span></span>|<span data-ttu-id="8d631-122">Sistem Kasım 2004'ten önce yayımlanan sürücüler için donanım hızlandırmasını devre dışı bırakır olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8d631-122">Specifies whether the system disables hardware acceleration for drivers released before November 2004.</span></span>|  
|<span data-ttu-id="8d631-123">**Başvuru tarayıcısını seçeneği kullanma**</span><span class="sxs-lookup"><span data-stu-id="8d631-123">**Use Reference Rasterizer Option**</span></span>|<span data-ttu-id="8d631-124">Belirtir olup olmadığını [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görüntüleyiciye kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8d631-124">Specifies whether [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] should use the reference rasterizer.</span></span>|  
  
 <span data-ttu-id="8d631-125">Bu ayarların nasıl başvurulacağını bildiği bir dış yapılandırma yardımcı programı tarafından erişilebilen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kayıt defteri ayarları.</span><span class="sxs-lookup"><span data-stu-id="8d631-125">These settings can be accessed by any external configuration utility that knows how to reference the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] registry settings.</span></span> <span data-ttu-id="8d631-126">Bu ayarları da oluşturulabilir veya değerleri kullanarak doğrudan erişerek [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Kayıt Defteri Düzenleyicisi'ni.</span><span class="sxs-lookup"><span data-stu-id="8d631-126">These settings can also be created or modified by accessing the values directly by using the [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Registry Editor.</span></span>  
  
<a name="disablehardwareacceleration"></a>   
## <a name="disable-hardware-acceleration-option"></a><span data-ttu-id="8d631-127">Donanım hızlandırma seçeneği devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="8d631-127">Disable Hardware Acceleration Option</span></span>  
  
|<span data-ttu-id="8d631-128">Kayıt defteri anahtarı</span><span class="sxs-lookup"><span data-stu-id="8d631-128">Registry key</span></span>|<span data-ttu-id="8d631-129">Değer türü</span><span class="sxs-lookup"><span data-stu-id="8d631-129">Value type</span></span>|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\DisableHWAcceleration`|<span data-ttu-id="8d631-130">DWORD</span><span class="sxs-lookup"><span data-stu-id="8d631-130">DWORD</span></span>|  
  
 <span data-ttu-id="8d631-131">**Donanım hızlandırma seçeneği devre dışı** hata ayıklama ve test amaçları için donanım hızlandırmasını devre dışı bırakmak üzere sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d631-131">The **disable hardware acceleration option** enables you to turn off hardware acceleration for debugging and test purposes.</span></span> <span data-ttu-id="8d631-132">Bir uygulamada işleme yapıların gördüğünüzde, donanım hızlandırmasını devre dışı bırakmak deneyin.</span><span class="sxs-lookup"><span data-stu-id="8d631-132">When you see rendering artifacts in an application, try turning off hardware acceleration.</span></span> <span data-ttu-id="8d631-133">Yapı kaybolursa, sorunu, video sürücüsü ile olabilir.</span><span class="sxs-lookup"><span data-stu-id="8d631-133">If the artifact disappears, the problem might be with your video driver.</span></span>  
  
 <span data-ttu-id="8d631-134">**Donanım hızlandırma seçeneği devre dışı** , 0 veya 1 olan bir DWORD değeridir.</span><span class="sxs-lookup"><span data-stu-id="8d631-134">The **disable hardware acceleration option** is a DWORD value that is either 0 or 1.</span></span> <span data-ttu-id="8d631-135">1 değeri, donanım hızlandırmasını devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="8d631-135">A value of 1 disables hardware acceleration.</span></span> <span data-ttu-id="8d631-136">Sistem donanım hızlandırma gereksinimlerini karşılaması koşuluyla 0 değeri, donanım hızlandırmasını sağlar; Daha fazla bilgi için bkz: [grafik işleme katmanları](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md).</span><span class="sxs-lookup"><span data-stu-id="8d631-136">A value of 0 enables hardware acceleration, provided the system meets hardware acceleration requirements; for more information, see [Graphics Rendering Tiers](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md).</span></span>  
  
<a name="maxmultisample"></a>   
## <a name="maximum-multisample-value"></a><span data-ttu-id="8d631-137">En büyük çoklu örneklem değeri</span><span class="sxs-lookup"><span data-stu-id="8d631-137">Maximum Multisample Value</span></span>  
  
|<span data-ttu-id="8d631-138">Kayıt defteri anahtarı</span><span class="sxs-lookup"><span data-stu-id="8d631-138">Registry key</span></span>|<span data-ttu-id="8d631-139">Değer türü</span><span class="sxs-lookup"><span data-stu-id="8d631-139">Value type</span></span>|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\MaxMultisampleType`|<span data-ttu-id="8d631-140">DWORD</span><span class="sxs-lookup"><span data-stu-id="8d631-140">DWORD</span></span>|  
  
 <span data-ttu-id="8d631-141">**Maksimum çoklu örneklem değeri** düzgünleştirme en fazla ayarlamanıza olanak tanır [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] içeriği.</span><span class="sxs-lookup"><span data-stu-id="8d631-141">The **maximum multisample value** enables you to adjust the maximum amount of antialiasing of [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] content.</span></span> <span data-ttu-id="8d631-142">Bu düzey devre dışı bırakma [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] düzgünleştirme içinde [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] veya içinde etkinleştirmek [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8d631-142">Use this level to disable [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] antialiasing in [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] or enable it in [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)].</span></span>  
  
 <span data-ttu-id="8d631-143">**Maksimum çoklu örneklem değeri** 0 ile 16 arasında değişen bir DWORD değeri.</span><span class="sxs-lookup"><span data-stu-id="8d631-143">The **maximum multisample value** is a DWORD value that ranges from 0 to 16.</span></span> <span data-ttu-id="8d631-144">0 değeri, 3-b içeriğinin çoklu örneklem düzgünleştirme devre dışı bırakılmalıdır ve 16 değerinin 16 x'çoklu örneklem düzgünleştirme kullanmaya video kartı tarafından desteklenirse çalışır belirtir.</span><span class="sxs-lookup"><span data-stu-id="8d631-144">A value of 0 specifies that multisample antialiasing of 3-D content should be disabled, and a value of 16 will attempt to use up to 16x multisample antialiasing, if supported by the video card.</span></span> <span data-ttu-id="8d631-145">Bu kayıt defteri anahtarı değerini XPDM sürücülerini kullanan bilgisayarlarda ayarı uygulamaların büyük miktarda ek ekran belleği kullanmasına, düşmesine neden olur dikkat [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] oluşturma ve işleme hatalara olanağına sahiptir ve kararlılık sorunları.</span><span class="sxs-lookup"><span data-stu-id="8d631-145">Beware that setting this registry key value on computers using XPDM drivers will cause applications to use a large amount of additional video memory, decrease the performance of [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] rendering, and has the potential to introduce rendering errors and stability problems.</span></span>  
  
 <span data-ttu-id="8d631-146">Bu kayıt defteri anahtarı ayarlanmadığında [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XPDM sürücüleri için 0 ve 4 WDDM sürücüleri için varsayılan olarak yükler.</span><span class="sxs-lookup"><span data-stu-id="8d631-146">When this registry key is not set, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] defaults to 0 for XPDM drivers and 4 for WDDM drivers.</span></span>  
  
<a name="requiredvideodriverdatesetting"></a>   
## <a name="required-video-driver-date-setting"></a><span data-ttu-id="8d631-147">Gerekli ekran kartı sürücüsü tarih ayarı</span><span class="sxs-lookup"><span data-stu-id="8d631-147">Required Video Driver Date Setting</span></span>  
  
|<span data-ttu-id="8d631-148">Kayıt defteri anahtarı</span><span class="sxs-lookup"><span data-stu-id="8d631-148">Registry key</span></span>|<span data-ttu-id="8d631-149">Değer türü</span><span class="sxs-lookup"><span data-stu-id="8d631-149">Value type</span></span>|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\RequiredVideoDriverDate`|<span data-ttu-id="8d631-150">Dize</span><span class="sxs-lookup"><span data-stu-id="8d631-150">String</span></span>|  
  
 <span data-ttu-id="8d631-151">Kasım, 2004, [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] yayımlanan yönergeleri sınama sürücüsü yeni bir sürümünü; tarihi bu teklif daha iyi kararlılık sonra yazılan sürücüler.</span><span class="sxs-lookup"><span data-stu-id="8d631-151">In November, 2004, [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] released a new version of the driver testing guidelines; the drivers written after this date offer better stability.</span></span> <span data-ttu-id="8d631-152">Varsayılan olarak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] donanım hızlandırma ardışık düzeni için bu sürücüleri kullanır ve yazılım sürücüleri için işlemeye bu tarihten önce yayımlanan XPDM döner.</span><span class="sxs-lookup"><span data-stu-id="8d631-152">By default, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] will use the hardware acceleration pipeline for these drivers and will fall back to software rendering for XPDM drivers published before this date.</span></span>  
  
 <span data-ttu-id="8d631-153">**Video sürücüsü tarih ayarı gerekli** XPDM sürücüleri için alternatif bir minimum tarih belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d631-153">The **required video driver date setting** enables you to specify an alternate minimum date for XPDM drivers.</span></span> <span data-ttu-id="8d631-154">Video sürücüsü desteklemek için kararlı olduğundan eminseniz yalnızca Kasım 2004'den önceki bir tarih belirtmelisiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8d631-154">You should only specify a date earlier than November, 2004 if you are confident that your video driver is stable enough to support [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="8d631-155">Gerekli ekran kartı sürücüsü ayarı aşağıdaki biçimde bir dize alır:</span><span class="sxs-lookup"><span data-stu-id="8d631-155">The required video driver setting takes a string of the following format:</span></span>  
  
||  
|-|  
|<span data-ttu-id="8d631-156">*YYYY* `/` *MM* `/` *GG*</span><span class="sxs-lookup"><span data-stu-id="8d631-156">*YYYY* `/` *MM* `/` *DD*</span></span>|  
  
 <span data-ttu-id="8d631-157">Burada *YYYY* dört rakamlı yıl *MM* iki basamaklı ay ve *GG* iki basamaklı günüdür.</span><span class="sxs-lookup"><span data-stu-id="8d631-157">Where *YYYY* is the four-digit year, *MM* is the two-digit month, and *DD* is the two digit day.</span></span> <span data-ttu-id="8d631-158">Bu değer ayarlanmadığında [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Kasım 2004 kendi gerekli ekran kartı sürücüsü tarihini olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="8d631-158">When this value is unset, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uses November, 2004 as its required video driver date.</span></span>  
  
<a name="usereferencerasterizeroption"></a>   
## <a name="use-reference-rasterizer-option"></a><span data-ttu-id="8d631-159">Başvuru tarayıcısını seçeneği kullanma</span><span class="sxs-lookup"><span data-stu-id="8d631-159">Use Reference Rasterizer Option</span></span>  
  
|<span data-ttu-id="8d631-160">Kayıt defteri anahtarı</span><span class="sxs-lookup"><span data-stu-id="8d631-160">Registry key</span></span>|<span data-ttu-id="8d631-161">Değer türü</span><span class="sxs-lookup"><span data-stu-id="8d631-161">Value type</span></span>|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\UseReferenceRasterizer`|<span data-ttu-id="8d631-162">DWORD</span><span class="sxs-lookup"><span data-stu-id="8d631-162">DWORD</span></span>|  
  
 <span data-ttu-id="8d631-163">**Başvuru tarayıcısını seçeneği kullanma** zorlamak sağlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hata ayıklama için bir sanal donanım işleme moduna: [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] donanım moduna girer, ancak kullanır [!INCLUDE[TLA#tla_d3d](../../../../includes/tlasharptla-d3d-md.md)] yazılım tarayıcısı, başvuru gerçek donanım aygıtı yerine d3dref9.dll.</span><span class="sxs-lookup"><span data-stu-id="8d631-163">The **use reference rasterizer option** enables you to force [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] into a simulated hardware rendering mode for debugging: [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] goes into hardware mode, but uses the [!INCLUDE[TLA#tla_d3d](../../../../includes/tlasharptla-d3d-md.md)] reference software rasterizer, d3dref9.dll, instead of an actual hardware device.</span></span>  
  
 <span data-ttu-id="8d631-164">Görüntüleyiciye çok yavaştır, ancak sürücü sorunlarından kaynaklanan işleme sorunlarını önlemek için video sürücünüzü atlar.</span><span class="sxs-lookup"><span data-stu-id="8d631-164">The reference rasterizer is very slow, but bypasses your video driver to avoid any rendering issues caused by driver problems.</span></span> <span data-ttu-id="8d631-165">Bu nedenle, görüntüleyiciye işleme sorunlarını video sürücüsü tarafından neden olup olmadığını belirlemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d631-165">For this reason, you can use the reference rasterizer to determine if rendering issues are caused by the video driver.</span></span> <span data-ttu-id="8d631-166">D3dref9.dll dosya, uygulama, gibi herhangi bir konumda sistem yolunda veya yerel dizin uygulamanın erişebildiği bir konumda olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8d631-166">The d3dref9.dll file must be in a location where the application can access it, such as in any location in the system path or in the local directory of the application.</span></span>  
  
 <span data-ttu-id="8d631-167">**Başvuru tarayıcısını seçeneği kullanma** bir DWORD değeri alır.</span><span class="sxs-lookup"><span data-stu-id="8d631-167">The **use reference rasterizer option** takes a DWORD value.</span></span> <span data-ttu-id="8d631-168">0 değeri, görüntüleyiciye kullanılmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8d631-168">A value of 0 indicates that the reference rasterizer is not used.</span></span> <span data-ttu-id="8d631-169">Diğer bir sıfır olmayan bir değer zorlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görüntüleyiciye kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="8d631-169">Any other non-zero value forces [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to use the reference rasterizer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d631-170">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8d631-170">See Also</span></span>  
 [<span data-ttu-id="8d631-171">Grafik işleme katmanları</span><span class="sxs-lookup"><span data-stu-id="8d631-171">Graphics Rendering Tiers</span></span>](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)  
 [<span data-ttu-id="8d631-172">WPF Grafik işleme genel bakış</span><span class="sxs-lookup"><span data-stu-id="8d631-172">WPF Graphics Rendering Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)