---
title: "Tanılama için Windows Yönetim İzlemesini Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 15d3768d9fa71e323ed3dfafb1068eb2c082b0d0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a><span data-ttu-id="1c0db-102">Tanılama için Windows Yönetim İzlemesini Kullanma</span><span class="sxs-lookup"><span data-stu-id="1c0db-102">Using Windows Management Instrumentation for Diagnostics</span></span>
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="1c0db-103">Çalışma zamanında bir hizmetin denetleme kullanıma sunan bir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Windows Yönetim Araçları (WMI) sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="1c0db-103"> exposes inspection data of a service at runtime through a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Windows Management Instrumentation (WMI) provider.</span></span>  
  
## <a name="enabling-wmi"></a><span data-ttu-id="1c0db-104">WMI etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="1c0db-104">Enabling WMI</span></span>  
 <span data-ttu-id="1c0db-105">WMI, Web tabanlı Kuruluş Yönetimi'nin (WBEM) standart Microsoft uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="1c0db-105">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]<span data-ttu-id="1c0db-106">bkz: WMI SDK [Windows Yönetim Araçları](https://msdn.microsoft.com/library/aa394582.aspx).</span><span class="sxs-lookup"><span data-stu-id="1c0db-106"> the WMI SDK, see [Windows Management Instrumentation](https://msdn.microsoft.com/library/aa394582.aspx).</span></span> <span data-ttu-id="1c0db-107">WBEM nasıl uygulamaları dış Yönetim Araçları için Yönetim Araçları'nı kullanıma sunmak için bir endüstri standardıdır.</span><span class="sxs-lookup"><span data-stu-id="1c0db-107">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="1c0db-108">Bir WMI sağlayıcısı WBEM uyumlu arabirimi aracılığıyla çalışma zamanında izleme kullanıma sunan bir bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="1c0db-108">A WMI provider is a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="1c0db-109">Öznitelik/değer çiftine sahip WMI nesneler kümesinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="1c0db-109">It consists of a set of WMI objects that have attribute/value pairs.</span></span> <span data-ttu-id="1c0db-110">Çiftleri basit türler sayısı olabilir.</span><span class="sxs-lookup"><span data-stu-id="1c0db-110">Pairs can be of a number of simple types.</span></span> <span data-ttu-id="1c0db-111">Yönetim Araçları, çalışma zamanında arabirimi üzerinden hizmetlere bağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="1c0db-111">Management tools can connect to the services through the interface at runtime.</span></span> [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="1c0db-112">adresler, bağlamalar, davranışları ve dinleyicileri gibi hizmetleri özniteliklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1c0db-112"> exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="1c0db-113">Uygulama yapılandırma dosyasında yerleşik WMI Sağlayıcısı'nın etkin hale getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="1c0db-113">The built-in WMI provider can be activated in the configuration file of the application.</span></span> <span data-ttu-id="1c0db-114">Bu yoluyla yapılır `wmiProviderEnabled` özniteliği [ \<Tanılama >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) içinde [ \<system.serviceModel >](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) bölümünde, aşağıdaki örnekte gösterildiği gibi yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="1c0db-114">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration.</span></span>  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 <span data-ttu-id="1c0db-115">Bu yapılandırma girdisi WMI arabirimini kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="1c0db-115">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="1c0db-116">Yönetim uygulamaları artık bu arabirimi üzerinden bağlanır ve Yönetim Araçları'nı uygulamanın erişir.</span><span class="sxs-lookup"><span data-stu-id="1c0db-116">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="accessing-wmi-data"></a><span data-ttu-id="1c0db-117">WMI verilerine erişme</span><span class="sxs-lookup"><span data-stu-id="1c0db-117">Accessing WMI Data</span></span>  
 <span data-ttu-id="1c0db-118">WMI veri birçok farklı yolla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="1c0db-118">WMI data can be accessed in many different ways.</span></span> <span data-ttu-id="1c0db-119">Microsoft, komut dosyaları için WMI API'lerini sağlar [!INCLUDE[vbprvb](../../../../../includes/vbprvb-md.md)] uygulamalar, C++ uygulamaları ve [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1c0db-119">Microsoft provides WMI APIs for scripts, [!INCLUDE[vbprvb](../../../../../includes/vbprvb-md.md)] applications, C++ applications, and the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="1c0db-120">Daha fazla bilgi için bkz: [kullanılarak WMI](http://go.microsoft.com/fwlink/?LinkId=95183).</span><span class="sxs-lookup"><span data-stu-id="1c0db-120">For more information, see [Using WMI](http://go.microsoft.com/fwlink/?LinkId=95183).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="1c0db-121">WMI verilerini programlı olarak erişmek için yöntemler sağlanan .NET Framework'te kullanıyorsanız bağlantı kurulduğunda tür yöntem özel durumlar oluşturma farkında olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1c0db-121">If you use the .NET Framework provided methods to programmatically access WMI data, you should be aware that such methods may throw exceptions when the connection is established.</span></span> <span data-ttu-id="1c0db-122">Bağlantı oluşturma işlemi sırasında kurulmaz <xref:System.Management.ManagementObject> örneği, ancak ilk istek gerçek veri değişimi içeren.</span><span class="sxs-lookup"><span data-stu-id="1c0db-122">The connection is not established during the construction of the <xref:System.Management.ManagementObject> instance, but on the first request involving actual data exchange.</span></span> <span data-ttu-id="1c0db-123">Bu nedenle, kullanmanız gereken bir `try..catch` olası özel durumlarını yakalama bloğu.</span><span class="sxs-lookup"><span data-stu-id="1c0db-123">Therefore, you should use a `try..catch` block to catch the possible exceptions.</span></span>  
  
 <span data-ttu-id="1c0db-124">İzleme ve ileti günlüğe kaydetme düzeyi, yanı sıra ileti günlüğe kaydetme seçeneklerini değiştirebilirsiniz `System.ServiceModel` WMI izleme kaynağı.</span><span class="sxs-lookup"><span data-stu-id="1c0db-124">You can change the trace and message logging level, as well as message logging options for the `System.ServiceModel` trace source in WMI.</span></span> <span data-ttu-id="1c0db-125">Bu erişerek yapılabilir [AppDomainInfo](../../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md) Boolean bu özellikleri sunar örneği: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`, ve `TraceLevel`.</span><span class="sxs-lookup"><span data-stu-id="1c0db-125">This can be done by accessing the [AppDomainInfo](../../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md) instance, which exposes these Boolean properties: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`, and `TraceLevel`.</span></span> <span data-ttu-id="1c0db-126">Bu nedenle, ileti günlüğe kaydetme için bir izleme dinleyicisi yapılandırmanıza rağmen ayarlamak bu seçenekleri için `false` yapılandırması, daha sonra bunları değiştirebileceğiniz `true` uygulama çalışırken.</span><span class="sxs-lookup"><span data-stu-id="1c0db-126">Therefore, if you configure a trace listener for message logging, but set these options to `false` in configuration, you can later change them to `true` when the application is running.</span></span> <span data-ttu-id="1c0db-127">Bu ileti günlüğe kaydetme çalışma zamanında etkili bir şekilde etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="1c0db-127">This will effectively enable message logging at runtime.</span></span> <span data-ttu-id="1c0db-128">İleti günlüğe kaydetme, yapılandırma dosyanızda etkinleştirirseniz, benzer şekilde, size, WMI'yı kullanarak çalışma zamanında devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c0db-128">Similarly, if you enable message logging in your configuration file, you can disable it at runtime using WMI.</span></span>  
  
 <span data-ttu-id="1c0db-129">Bilmeniz gereken olması durumunda hiçbir ileti günlük kaydı izleme dinleyicileri ileti günlüğe kaydetme veya Hayır için `System.ServiceModel` izleme dinleyicileri izleme için yapılandırma dosyasında belirtilen, değişiklikleri WMI tarafından kabul edilen olsa bile, değişikliklerin hiçbiri yürürlüğe, alınır.</span><span class="sxs-lookup"><span data-stu-id="1c0db-129">You should be aware that if no message logging trace listeners for message logging, or no `System.ServiceModel` trace listeners for tracing are specified in the configuration file, none of your changes are taken into effect, even though the changes are accepted by WMI.</span></span> <span data-ttu-id="1c0db-130">Düzgün ilgili dinleyicileri ayarlama hakkında daha fazla bilgi için bkz: [yapılandırma ileti günlüğe kaydetme](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) ve [yapılandırma izleme](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="1c0db-130">For more information on properly setting up the respective listeners, see [Configuring Message Logging](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) and [Configuring Tracing](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).</span></span> <span data-ttu-id="1c0db-131">Uygulama başladığında yapılandırması tarafından belirtilen diğer tüm izleme kaynakları izleme düzeyini etkilidir ve değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="1c0db-131">The trace level of all other trace sources specified by configuration is effective when the application starts, and cannot be changed.</span></span>  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="1c0db-132">kullanıma sunan bir `GetOperationCounterInstanceName` komut dosyası için yöntem.</span><span class="sxs-lookup"><span data-stu-id="1c0db-132"> exposes a `GetOperationCounterInstanceName` method for scripting.</span></span> <span data-ttu-id="1c0db-133">Bir işlem adıyla sağlarsanız, bu yöntem bir performans sayacı örneği adını döndürür.</span><span class="sxs-lookup"><span data-stu-id="1c0db-133">This method returns a performance counter instance name if you provide it with an operation name.</span></span> <span data-ttu-id="1c0db-134">Ancak, giriş doğrulamaz.</span><span class="sxs-lookup"><span data-stu-id="1c0db-134">However, it does not validate your input.</span></span> <span data-ttu-id="1c0db-135">Bu nedenle, yanlış işlem adı sağlarsanız, yanlış sayaç adı döndürülür.</span><span class="sxs-lookup"><span data-stu-id="1c0db-135">Therefore, if you provide an incorrect operation name, an incorrect counter name is returned.</span></span>  
  
 <span data-ttu-id="1c0db-136">`OutgoingChannel` Özelliği `Service` örneği başka bir hizmete bağlanmak için bir hizmet tarafından açılmış kanalları saymak değil [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] hedef hizmeti istemciye oluşturulmadı içinde `Service` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1c0db-136">The `OutgoingChannel` property of the `Service` instance does not count channels opened by a service to connect to another service, if the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] client to the destination service is not created within the `Service` method.</span></span>  
  
 <span data-ttu-id="1c0db-137">**Uyarı** WMI yalnızca destekleyen bir <xref:System.TimeSpan> 3 adede kadar ondalık ayırıcıların değeri.</span><span class="sxs-lookup"><span data-stu-id="1c0db-137">**Caution** WMI only supports a <xref:System.TimeSpan> value up to 3 decimal points.</span></span> <span data-ttu-id="1c0db-138">Örneğin, hizmetiniz için özelliklerinden biri ayarlarsa <xref:System.TimeSpan.MaxValue>, değeri 3 ondalık WMI aracılığıyla görüntülendiğinde noktadan sonra kesilir.</span><span class="sxs-lookup"><span data-stu-id="1c0db-138">For example, if your service sets one of its properties to <xref:System.TimeSpan.MaxValue>, its value is truncated after 3 decimal points when viewed through WMI.</span></span>  
  
## <a name="security"></a><span data-ttu-id="1c0db-139">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="1c0db-139">Security</span></span>  
 <span data-ttu-id="1c0db-140">Çünkü [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] WMI sağlayıcısı, bir ortamda Hizmetleri bulma sayesinde, kendisine erişim verilmesi için çok dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1c0db-140">Because the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] WMI provider allows the discovery of services in an environment, you should exercise extreme caution for granting access to it.</span></span> <span data-ttu-id="1c0db-141">Varsayılan yalnızca yönetici erişimi hafifletin, ortamınızda hassas bilgilere erişimi daha az güvenilir tarafların izin verebilir.</span><span class="sxs-lookup"><span data-stu-id="1c0db-141">If you relax the default administrator-only access, you may allow less-trusted parties access to sensitive data in your environment.</span></span> <span data-ttu-id="1c0db-142">Uzak WMI erişim izinlerini çözmek, özellikle saldırıları taşmasını ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="1c0db-142">Specifically, if you loosen permissions on remote WMI access, flooding attacks can occur.</span></span> <span data-ttu-id="1c0db-143">Bir işlem tarafından aşırı WMI istekleri yayılan, kendi performans düşebilir.</span><span class="sxs-lookup"><span data-stu-id="1c0db-143">If a process is flooded by excessive WMI requests, its performance can be degraded.</span></span>  
  
 <span data-ttu-id="1c0db-144">Ayrıca, MOF dosyası için erişim izinlerini hafifletin, daha az güvenilen taraf WMI davranışını denetlemek ve WMI şemasını yüklenen nesneler alter.</span><span class="sxs-lookup"><span data-stu-id="1c0db-144">In addition, if you relax access permissions for the MOF file, less-trusted parties can manipulate the behavior of WMI and alter the objects that are loaded in the WMI schema.</span></span> <span data-ttu-id="1c0db-145">Örneğin, alanlar kritik verileri Yöneticisi'nden gizli bilgiler veya dosyasına eklenen doldurmak veya özel durumlara neden alanları şekilde kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="1c0db-145">For example, fields can be removed such that critical data is concealed from the administrator or that fields that do not populate or cause exceptions are added to the file.</span></span>  
  
 <span data-ttu-id="1c0db-146">Varsayılan olarak, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] WMI sağlayıcısı verir "yürütme yöntemi", "Sağlayıcı yazma" ya Administrator "hesabı etkinleştir" izinlerini ve ASP.NET, yerel hizmet ve ağ hizmeti için "hesabı etkinleştir" izni.</span><span class="sxs-lookup"><span data-stu-id="1c0db-146">By default, the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] WMI provider grants "execute method", "provider write", and "enable account" permission for Administrator, and "enable account" permission for ASP.NET, Local Service and Network Service.</span></span> <span data-ttu-id="1c0db-147">Özellikle, üzerinde olmayan[!INCLUDE[wv](../../../../../includes/wv-md.md)] platformları, ASP.NET hesabını okuyun WMI ServiceModel ad alanına erişimi.</span><span class="sxs-lookup"><span data-stu-id="1c0db-147">In particular, on non-[!INCLUDE[wv](../../../../../includes/wv-md.md)] platforms, the ASP.NET account has read access to the WMI ServiceModel namespace.</span></span> <span data-ttu-id="1c0db-148">Belirli bir kullanıcı grubuna Bu ayrıcalıkları vermek istemiyorsanız (varsayılan olarak devre dışıdır) WMI sağlayıcısı devre dışı bırakmak veya erişimi belirli bir kullanıcı grubu için devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="1c0db-148">If you do not want to grant these privileges to a particular user group, you should either deactivate the WMI provider (it is disabled by default), or disable access for the specific user group.</span></span>  
  
 <span data-ttu-id="1c0db-149">WMI aracılığıyla yapılandırma etkinleştirmeye çalıştığınızda, ayrıca, WMI yetersiz kullanıcı ayrıcalıkların yetersizliği etkinleştirilmemiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="1c0db-149">In addition, when you attempt to enable WMI through configuration, WMI may not be enabled due to insufficient user privilege.</span></span> <span data-ttu-id="1c0db-150">Ancak, hiçbir olay bu hatayı kaydetmek için olay günlüğüne yazılır.</span><span class="sxs-lookup"><span data-stu-id="1c0db-150">However, no event is written to the event log to record this failure.</span></span>  
  
 <span data-ttu-id="1c0db-151">Kullanıcı ayrıcalık düzeylerini değiştirmek için aşağıdaki adımları kullanın.</span><span class="sxs-lookup"><span data-stu-id="1c0db-151">To modify user privilege levels, use the following steps.</span></span>  
  
1.  <span data-ttu-id="1c0db-152">Başlat'ı tıklatın ve ardından çalıştırın ve yazın **compmgmt.msc**.</span><span class="sxs-lookup"><span data-stu-id="1c0db-152">Click Start and then Run and type **compmgmt.msc**.</span></span>  
  
2.  <span data-ttu-id="1c0db-153">Sağ **Hizmetleri ve uygulama/WMI denetimleri** seçmek için **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="1c0db-153">Right-click **Services and Application/WMI Controls** to select **Properties**.</span></span>  
  
3.  <span data-ttu-id="1c0db-154">Seçin **güvenlik** sekmesine gidin **kök/ServiceModel** ad alanı.</span><span class="sxs-lookup"><span data-stu-id="1c0db-154">Select the **Security** Tab, and navigate to the **Root/ServiceModel** namespace.</span></span> <span data-ttu-id="1c0db-155">Tıklatın **güvenlik** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="1c0db-155">Click the **Security** button.</span></span>  
  
4.  <span data-ttu-id="1c0db-156">Belirli bir grup veya erişimi denetlemek ve kullanmak istediğiniz kullanıcıyı seçin **izin** veya **reddetme** izinlerini yapılandırmak için onay kutusunu.</span><span class="sxs-lookup"><span data-stu-id="1c0db-156">Select the specific group or user that you want to control access and use the **Allow** or **Deny** checkbox to configure permissions.</span></span>  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a><span data-ttu-id="1c0db-157">WCF WMI kayıt ek kullanıcılara izin verme</span><span class="sxs-lookup"><span data-stu-id="1c0db-157">Granting WCF WMI Registration Permissions to Additional Users</span></span>  
 <span data-ttu-id="1c0db-158">WCF WMI yönetimi verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1c0db-158">WCF exposes management data to WMI.</span></span> <span data-ttu-id="1c0db-159">Bunu bir "sağlayıcıyla" olarak da adlandırılan bir işlemdeki WMI sağlayıcısı barındırarak yapar.</span><span class="sxs-lookup"><span data-stu-id="1c0db-159">It does so by hosting an in-process WMI provider, sometimes called a "decoupled provider".</span></span> <span data-ttu-id="1c0db-160">Yönetim verileri açığa çıkarılması bu sağlayıcısını kaydeder hesap uygun izinlere sahip gerekir.</span><span class="sxs-lookup"><span data-stu-id="1c0db-160">For the management data to be exposed, the account that registers this provider must have the appropriate permissions.</span></span> <span data-ttu-id="1c0db-161">Windows, ayrıcalıklı hesaplar, yalnızca küçük bir kümesini ayrılmış sağlayıcıları varsayılan olarak kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c0db-161">In Windows, only a small set of privileged accounts can register decoupled providers by default.</span></span> <span data-ttu-id="1c0db-162">Kullanıcıların yaygın olarak WMI veri varsayılan kümesinde olmayan bir hesap altında çalışan bir WCF hizmetinden kullanıma sunmak istediğiniz sorun olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="1c0db-162">This is a problem because users commonly want to expose WMI data from a WCF service running under an account that is not in the default set.</span></span>  
  
 <span data-ttu-id="1c0db-163">Bu erişimi sağlamak için yönetici aşağıdaki sırayla ek hesap için aşağıdaki izinleri vermeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="1c0db-163">To provide this access, an administrator must grant the following permissions to the additional account in the following order:</span></span>  
  
1.  <span data-ttu-id="1c0db-164">WCF WMI Namespace için erişim izni.</span><span class="sxs-lookup"><span data-stu-id="1c0db-164">Permission to access to the WCF WMI Namespace.</span></span>  
  
2.  <span data-ttu-id="1c0db-165">WCF ayrılmış WMI sağlayıcısı kaydetme izni.</span><span class="sxs-lookup"><span data-stu-id="1c0db-165">Permission to register the WCF Decoupled WMI Provider.</span></span>  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a><span data-ttu-id="1c0db-166">WMI ad alanı erişim izni vermek için</span><span class="sxs-lookup"><span data-stu-id="1c0db-166">To grant WMI namespace access permission</span></span>  
  
1.  <span data-ttu-id="1c0db-167">Aşağıdaki PowerShell betiğini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1c0db-167">Run the following PowerShell script.</span></span>  
  
    ```powershell  
    write-host ""  
    write-host "Granting Access to root/servicemodel WMI namespace to built in users group"  
    write-host ""  
  
    # Create the binary representation of the permissions to grant in SDDL  
    $newPermissions = "O:BAG:BAD:P(A;CI;CCDCLCSWRPWPRCWD;;;BA)(A;CI;CC;;;NS)(A;CI;CC;;;LS)(A;CI;CC;;;BU)"  
    $converter = new-object system.management.ManagementClass Win32_SecurityDescriptorHelper  
    $binarySD = $converter.SDDLToBinarySD($newPermissions)  
    $convertedPermissions = ,$binarySD.BinarySD  
  
    # Get the object used to set the permissions  
    $security = gwmi -namespace root/servicemodel -class __SystemSecurity  
  
    # Get and output the current settings  
    $binarySD = @($null)  
    $result = $security.PsBase.InvokeMethod("GetSD",$binarySD)  
  
    $outsddl = $converter.BinarySDToSDDL($binarySD[0])  
    write-host "Previous ACL: "$outsddl.SDDL  
  
    # Change the Access Control List (ACL) using SDDL  
    $result = $security.PsBase.InvokeMethod("SetSD",$convertedPermissions)   
  
    # Get and output the current settings  
    $binarySD = @($null)  
    $result = $security.PsBase.InvokeMethod("GetSD",$binarySD)  
  
    $outsddl = $converter.BinarySDToSDDL($binarySD[0])  
    write-host "New ACL:      "$outsddl.SDDL  
    write-host ""  
    ```  
  
     <span data-ttu-id="1c0db-168">Bu PowerShell komut dosyasını, "kök/servicemodel" WMI ad alanına yerleşik Kullanıcılar grubu erişimi vermek için Güvenlik Tanımlayıcısı Tanım Dili (SDDL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="1c0db-168">This PowerShell script uses Security Descriptor Definition Language (SDDL) to grant the Built-In Users group access to the "root/servicemodel" WMI namespace.</span></span> <span data-ttu-id="1c0db-169">Aşağıdaki EDL'ler belirtir:</span><span class="sxs-lookup"><span data-stu-id="1c0db-169">It specifies the following ACLs:</span></span>  
  
    -   <span data-ttu-id="1c0db-170">Yerleşik yönetici (BA) - erişim zaten var.</span><span class="sxs-lookup"><span data-stu-id="1c0db-170">Built-In Administrator (BA) - Already Had Access.</span></span>  
  
    -   <span data-ttu-id="1c0db-171">Ağ Hizmeti (NS) - zaten Erişebiliyordunuz.</span><span class="sxs-lookup"><span data-stu-id="1c0db-171">Network Service (NS) - Already Had Access.</span></span>  
  
    -   <span data-ttu-id="1c0db-172">Yerel Sistem (LS) - erişim zaten var.</span><span class="sxs-lookup"><span data-stu-id="1c0db-172">Local System (LS) - Already Had Access.</span></span>  
  
    -   <span data-ttu-id="1c0db-173">Yerleşik kullanıcılar - erişim izni vermek için Grup.</span><span class="sxs-lookup"><span data-stu-id="1c0db-173">Built-In Users - The group to grant access to.</span></span>  
  
#### <a name="to-grant-provider-registration-access"></a><span data-ttu-id="1c0db-174">Sağlayıcı vermek için kayıt erişme</span><span class="sxs-lookup"><span data-stu-id="1c0db-174">To grant provider registration access</span></span>  
  
1.  <span data-ttu-id="1c0db-175">Aşağıdaki PowerShell betiğini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1c0db-175">Run the following PowerShell script.</span></span>  
  
    ```powershell  
    write-host ""  
    write-host "Granting WCF provider registration access to built in users group"  
    write-host ""  
    # Set security on ServiceModel provider  
    $provider = get-WmiObject -namespace "root\servicemodel" __Win32Provider  
  
    write-host "Previous ACL: "$provider.SecurityDescriptor  
    $result = $provider.SecurityDescriptor = "O:BUG:BUD:(A;;0x1;;;BA)(A;;0x1;;;NS)(A;;0x1;;;LS)(A;;0x1;;;BU)"  
  
    # Commit the changes and display it to the console  
    $result = $provider.Put()  
    write-host "New ACL:      "$provider.SecurityDescriptor  
    write-host ""  
    ```  
  
### <a name="granting-access-to-arbitrary-users-or-groups"></a><span data-ttu-id="1c0db-176">Rastgele kullanıcılara veya gruplara erişim izni verme</span><span class="sxs-lookup"><span data-stu-id="1c0db-176">Granting Access to Arbitrary Users or Groups</span></span>  
 <span data-ttu-id="1c0db-177">Bu bölümdeki örnek tüm yerel kullanıcılar için WMI sağlayıcısı kayıt ayrıcalıklar verir.</span><span class="sxs-lookup"><span data-stu-id="1c0db-177">The example in this section grants WMI Provider registration privileges to all local users.</span></span> <span data-ttu-id="1c0db-178">Daha sonra bir kullanıcı veya grup içinde yerleşik değildir erişim vermek istiyorsanız, o kullanıcının veya grubun güvenlik tanımlayıcısı (SID) edinmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1c0db-178">If you want to grant access to a user or group that is not built in, then you must obtain that user or group’s Security Identifier (SID).</span></span> <span data-ttu-id="1c0db-179">İsteğe bağlı bir kullanıcı için SID almak için basit bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="1c0db-179">There is no simple way to get the SID for an arbitrary user.</span></span> <span data-ttu-id="1c0db-180">İstenen kullanıcı olarak oturum açın ve aşağıdaki Kabuk komut vermek için bir yöntem var.</span><span class="sxs-lookup"><span data-stu-id="1c0db-180">One method is to log on as the desired user and then issue the following shell command.</span></span>  
  
```  
Whoami /user  
```  
  
 <span data-ttu-id="1c0db-181">Bu geçerli kullanıcının SID sağlar, ancak bu yöntem, üzerinde herhangi bir kullanıcı SID almak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1c0db-181">This provides the SID of the current user, but this method cannot be used to get the SID on any arbitrary user.</span></span> <span data-ttu-id="1c0db-182">SID almak için başka bir yöntem kullanmaktır [getsid.exe](http://go.microsoft.com/fwlink/?LinkId=186467) öğesinden aracı [Windows 2000 Kaynak Seti Araçları yönetim görevleri için](http://go.microsoft.com/fwlink/?LinkId=178660).</span><span class="sxs-lookup"><span data-stu-id="1c0db-182">Another method to get the SID is to use the [getsid.exe](http://go.microsoft.com/fwlink/?LinkId=186467) tool from the [Windows 2000 Resource Kit Tools for administrative tasks](http://go.microsoft.com/fwlink/?LinkId=178660).</span></span> <span data-ttu-id="1c0db-183">Bu aracı (yerel veya etki alanı) iki kullanıcı SID'si karşılaştırır ve bir yan etkisi komut satırına iki SID'ler yazdırır.</span><span class="sxs-lookup"><span data-stu-id="1c0db-183">This tool compares the SID of two users (local or domain), and as a side effect prints the two SIDs to the command line.</span></span> [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)]<span data-ttu-id="1c0db-184">[İyi bilinen SID](http://go.microsoft.com/fwlink/?LinkId=186468).</span><span class="sxs-lookup"><span data-stu-id="1c0db-184"> [Well Known SIDs](http://go.microsoft.com/fwlink/?LinkId=186468).</span></span>  
  
## <a name="accessing-remote-wmi-object-instances"></a><span data-ttu-id="1c0db-185">Uzak WMI nesne örneklerini erişme</span><span class="sxs-lookup"><span data-stu-id="1c0db-185">Accessing Remote WMI Object Instances</span></span>  
 <span data-ttu-id="1c0db-186">Erişmeniz gerekiyorsa [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] WMI örnekleri uzak makinede paket gizliliği erişmek için kullandığınız araçları etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1c0db-186">If you need to access [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] WMI instances on a remote machine, you must enable packet privacy on the tools that you use for access.</span></span> <span data-ttu-id="1c0db-187">Aşağıdaki bölümde bu elde etmek WMI CIM Studio, Windows Yönetim Araçları Sınayıcısı, yanı sıra .NET SDK 2.0 kullanarak açıklar.</span><span class="sxs-lookup"><span data-stu-id="1c0db-187">The following section describes how to achieve these using the WMI CIM Studio, Windows Management Instrumentation Tester, as well as .NET SDK 2.0.</span></span>  
  
### <a name="wmi-cim-studio"></a><span data-ttu-id="1c0db-188">WMI CIM Studio</span><span class="sxs-lookup"><span data-stu-id="1c0db-188">WMI CIM Studio</span></span>  
 <span data-ttu-id="1c0db-189">Yüklediyseniz [WMI Yönetimsel Araçlar](http://go.microsoft.com/fwlink/?LinkId=95185), WMI CIM Studio erişim WMI örnekleri için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c0db-189">If you have installed [WMI Administrative Tools](http://go.microsoft.com/fwlink/?LinkId=95185), you can use the WMI CIM Studio to access WMI instances.</span></span> <span data-ttu-id="1c0db-190">Aşağıdaki klasörde araçlardır</span><span class="sxs-lookup"><span data-stu-id="1c0db-190">The tools are in the following folder</span></span>  
  
 <span data-ttu-id="1c0db-191">**%windir%\Program Files\WMI araçları\\**</span><span class="sxs-lookup"><span data-stu-id="1c0db-191">**%windir%\Program Files\WMI Tools\\**</span></span>  
  
1.  <span data-ttu-id="1c0db-192">İçinde **ad Connect:** penceresinde, türü **root\ServiceModel** tıklatıp **Tamam.**</span><span class="sxs-lookup"><span data-stu-id="1c0db-192">In the **Connect to namespace:** window, type **root\ServiceModel** and click **OK.**</span></span>  
  
2.  <span data-ttu-id="1c0db-193">İçinde **WMI CIM Studio oturum açma** penceresinde tıklatın **Seçenekleri >>** penceresini genişletmek için düğmesi.</span><span class="sxs-lookup"><span data-stu-id="1c0db-193">In the **WMI CIM Studio Login** window, click the **Options >>** button to expand the window.</span></span> <span data-ttu-id="1c0db-194">Seçin **paket gizliliği** için **kimlik doğrulama düzeyi**, tıklatıp **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="1c0db-194">Select **Packet privacy** for **Authentication level**, and click **OK**.</span></span>  
  
### <a name="windows-management-instrumentation-tester"></a><span data-ttu-id="1c0db-195">Windows Yönetim Araçları Sınayıcısı</span><span class="sxs-lookup"><span data-stu-id="1c0db-195">Windows Management Instrumentation Tester</span></span>  
 <span data-ttu-id="1c0db-196">Bu araç, Windows tarafından yüklenir.</span><span class="sxs-lookup"><span data-stu-id="1c0db-196">This tool is installed by Windows.</span></span> <span data-ttu-id="1c0db-197">Çalıştırmak için bir komut konsolundan yazarak başlatma **cmd.exe** içinde **Başlat/Çalıştır** iletişim kutusu ve tıklatın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="1c0db-197">To run it, launch a command console by typing **cmd.exe** in the **Start/Run** dialog box and click **OK**.</span></span> <span data-ttu-id="1c0db-198">Ardından, yazın **wbemtest.exe** komut penceresinde.</span><span class="sxs-lookup"><span data-stu-id="1c0db-198">Then, type **wbemtest.exe** in the command window.</span></span> <span data-ttu-id="1c0db-199">Windows Yönetim Araçları Sınayıcısı aracı sonra başlatılır.</span><span class="sxs-lookup"><span data-stu-id="1c0db-199">The Windows Management Instrumentation Tester tool is then launched.</span></span>  
  
1.  <span data-ttu-id="1c0db-200">Tıklatın **Bağlan** pencerenin sağ üst köşesinde bulunan düğmesi.</span><span class="sxs-lookup"><span data-stu-id="1c0db-200">Click the **Connect** button on the top right corner of the window.</span></span>  
  
2.  <span data-ttu-id="1c0db-201">Yeni pencerede girin **root\ServiceModel** için **Namespace** alan ve select **paket gizliliği** için **kimlik doğrulama düzeyi**.</span><span class="sxs-lookup"><span data-stu-id="1c0db-201">In the new window, enter **root\ServiceModel** for the **Namespace** field, and select **Packet privacy** for **Authentication level**.</span></span> <span data-ttu-id="1c0db-202">**Bağlan**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1c0db-202">Click **Connect**.</span></span>  
  
### <a name="using-managed-code"></a><span data-ttu-id="1c0db-203">Yönetilen kod kullanarak</span><span class="sxs-lookup"><span data-stu-id="1c0db-203">Using Managed Code</span></span>  
 <span data-ttu-id="1c0db-204">Aynı zamanda uzak WMI örnekleri program aracılığıyla tarafından sağlanan sınıflarını kullanarak erişebilirsiniz <xref:System.Management> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="1c0db-204">You can also access remote WMI instances programmatically by using classes provided by the <xref:System.Management> namespace.</span></span> <span data-ttu-id="1c0db-205">Aşağıdaki kod örneği, bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1c0db-205">The following code sample demonstrates how to do this.</span></span>  
  
```  
String wcfNamespace = String.Format(@"\\{0}\Root\ServiceModel",      
   this.serviceMachineName);  
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```