---
title: "Kaynak Tüketimini Denetleme ve Performansı Geliştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a829669-5f76-4c88-80ec-92d0c62c0660
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8cd80805eee58db16f5865683cbd322a49c554a8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="controlling-resource-consumption-and-improving-performance"></a><span data-ttu-id="16334-102">Kaynak Tüketimini Denetleme ve Performansı Geliştirme</span><span class="sxs-lookup"><span data-stu-id="16334-102">Controlling Resource Consumption and Improving Performance</span></span>
<span data-ttu-id="16334-103">Bu konu, farklı bölgelerdeki çeşitli özellikleri açıklar [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] kaynak tüketimini denetleme ve performans ölçümleri etkileyen iş mimarisi.</span><span class="sxs-lookup"><span data-stu-id="16334-103">This topic describes various properties in different areas of the [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] architecture that work to control resource consumption and affect performance metrics.</span></span>  
  
## <a name="properties-that-constrain-resource-consumption-in-wcf"></a><span data-ttu-id="16334-104">WCF kaynak tüketimini sınırlamak özellikleri</span><span class="sxs-lookup"><span data-stu-id="16334-104">Properties that Constrain Resource Consumption in WCF</span></span>  
 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="16334-105">belirli türde bir işlemler güvenlik veya performans amacıyla kısıtlamalar geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="16334-105"> applies constraints on certain types of processes for either security or performance purposes.</span></span> <span data-ttu-id="16334-106">Bu kısıtlamaların iki ana biçimde, kotaları ve kısıtlamaları gelir.</span><span class="sxs-lookup"><span data-stu-id="16334-106">These constraints come in two main forms, either quotas and throttles.</span></span> <span data-ttu-id="16334-107">*Kotalar* ulaştı veya aşıldı sistemde belirli bir noktada hemen bir özel durum harekete kısıtlamalardır.</span><span class="sxs-lookup"><span data-stu-id="16334-107">*Quotas* are limits that when reached or exceeded trigger an immediate exception at some point in the system.</span></span> <span data-ttu-id="16334-108">*Kısıtlar* hemen bir özel durum oluşturulmasına neden olmaz kısıtlamalardır.</span><span class="sxs-lookup"><span data-stu-id="16334-108">*Throttles* are limits that do not immediately cause an exception to be thrown.</span></span> <span data-ttu-id="16334-109">Bunun yerine, bir kısıtlama sınırına ulaşıldığında, işleme devam eder ancak sınırlarda tarafından kısıtlama değeri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="16334-109">Instead, when a throttle limit is reached, processing continues but within the limits set by that throttle value.</span></span> <span data-ttu-id="16334-110">Sınırlı bu işlem başka bir yerde bir özel durum harekete, ancak bu uygulamanın bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="16334-110">This limited processing might trigger an exception elsewhere, but this depends upon the application.</span></span>  
  
 <span data-ttu-id="16334-111">Kotaları ve kısıtlamaları arasında ayrım yanı sıra kısıtlayan bazı özellikleri seri hale getirme düzeyinde, bazı aktarım düzeyinde ve bazı uygulama düzeyinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="16334-111">In addition to the distinction between quotas and throttles, some constraining properties are located at the serialization level, some at the transport level, and some at the application level.</span></span> <span data-ttu-id="16334-112">Örneğin, kota <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType>, tüm sistem tarafından sağlanan aktarım bağlama öğeleri tarafından uygulanan ayarlanmış 65,536 bayt varsayılan olarak hizmet reddi saldırılarına karşı bir hizmet olarak aşırı bellek neden olarak yapmasının kötü amaçlı istemcileri azaltabilir Tüketim.</span><span class="sxs-lookup"><span data-stu-id="16334-112">For example, the quota <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType>, which is implemented by all system-supplied transport binding elements, is set to 65,536 bytes by default to hinder malicious clients from engaging in denial-of-service attacks against a service by causing excessive memory consumption.</span></span> <span data-ttu-id="16334-113">(Tipik olarak, performans bu değeri azaltarak artırabilirsiniz.)</span><span class="sxs-lookup"><span data-stu-id="16334-113">(Typically, you can increase performance by lowering this value.)</span></span>  
  
 <span data-ttu-id="16334-114">Bir seri hale getirme kota örneğidir <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> tek bir seri hale getirici serileştiren veya seri durumdan çıkarır nesneler en fazla sayısını belirtir özelliği <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A> yöntem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="16334-114">An example of a serialization quota is the <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> property, which specifies the maximum number of objects that the serializer serializes or deserializes in a single <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A> method call.</span></span> <span data-ttu-id="16334-115">Uygulama düzeyi kısıtlama örneğidir <xref:System.ServiceModel.Dispatcher.ServiceThrottle.MaxConcurrentSessions%2A?displayProperty=nameWithType> varsayılan olarak 10 eşzamanlı süre sonuyla kanalı bağlantıları sayısını kısıtlar özelliği.</span><span class="sxs-lookup"><span data-stu-id="16334-115">An example of an application-level throttle is the <xref:System.ServiceModel.Dispatcher.ServiceThrottle.MaxConcurrentSessions%2A?displayProperty=nameWithType> property, which by default restricts the number of concurrent sessionful channel connections to 10.</span></span> <span data-ttu-id="16334-116">(Kotaları aksine bu kısıtlama değeri ulaştıysanız, uygulamanın devam ettirir, ancak yeni hiçbir süre sonuyla kanalı diğer süre sonuyla kanallarını sonlanana yeni istemciler bağlanamıyor anlamı kabul eder.)</span><span class="sxs-lookup"><span data-stu-id="16334-116">(Unlike the quotas, if this throttle value is reached, the application continues processing but accepts no new sessionful channels, which means that new clients cannot connect until one of the other sessionful channels is ended.)</span></span>  
  
 <span data-ttu-id="16334-117">Bu denetimler, belirli türde bir saldırılarına karşı Giden kutusu azaltma sağlamak ya da performans ölçümleri bellek alanını, başlangıç saati vb. gibi artırmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="16334-117">These controls are designed to provide an out-of-the-box mitigation against certain types of attacks or to improve performance metrics such as memory footprint, start-up time, and so on.</span></span> <span data-ttu-id="16334-118">Ancak, uygulamaya bağlı olarak, bu denetimleri hizmet uygulama performansını olumsuz yönde hiç çalışma uygulamanın veya engeller.</span><span class="sxs-lookup"><span data-stu-id="16334-118">However, depending on the application, these controls can impede service application performance or prevent the application from working at all.</span></span> <span data-ttu-id="16334-119">Örneğin, akış video için tasarlanmış bir uygulama varsayılan kolayca aşabilir <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="16334-119">For example, an application designed to stream video can easily exceed the default <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="16334-120">Bu konu tüm düzeylerdeki uygulamalara uygulanan çeşitli denetimlerin genel bir bakış sağlar [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], bir ayar, uygulamanızın olup hindering hakkında daha fazla bilgi edinmek için çeşitli yollarını açıklar ve çeşitli düzeltmek için yolları açıklanmaktadır sorunları.</span><span class="sxs-lookup"><span data-stu-id="16334-120">This topic provides an overview of the various controls applied to applications at all levels of [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], describes various ways to obtain more information about whether a setting is hindering your application, and describes ways to correct various problems.</span></span> <span data-ttu-id="16334-121">Çoğu kısıtlamaları ve bazı kotalar temel özelliği seri hale getirme veya taşıma kısıtlaması olsa bile uygulama düzeyinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="16334-121">Most throttles and some quotas are available at the application level, even when the base property is a serialization or transport constraint.</span></span> <span data-ttu-id="16334-122">Örneğin, ayarlayabileceğiniz <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> özelliğini kullanarak <xref:System.ServiceModel.ServiceBehaviorAttribute.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> hizmet sınıfı özelliği.</span><span class="sxs-lookup"><span data-stu-id="16334-122">For example, you can set the <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> property using the <xref:System.ServiceModel.ServiceBehaviorAttribute.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> property on the service class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16334-123">Belirli bir sorun varsa, ilk okumalısınız [WCF sorun giderme Hızlı Başlangıç](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md) sorununuzu (ve bir çözüm) var. listelenmiş olup olmadığını görmek için.</span><span class="sxs-lookup"><span data-stu-id="16334-123">If you have a particular problem, you should first read the [WCF Troubleshooting Quickstart](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md) to see whether your problem (and a solution) is listed there.</span></span>  
  
 <span data-ttu-id="16334-124">Seri hale getirme işlemlerini kısıtlamak özellikler listelenmiştir [veriler için güvenlik konuları](../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span><span class="sxs-lookup"><span data-stu-id="16334-124">Properties that restrict serialization processes are listed in [Security Considerations for Data](../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span></span> <span data-ttu-id="16334-125">Taşımasıyla ilgili kaynaklarının kullanımını kısıtlamak özellikler listelenmiştir [taşıma kotaları](../../../docs/framework/wcf/feature-details/transport-quotas.md).</span><span class="sxs-lookup"><span data-stu-id="16334-125">Properties that restrict the consumption of resources related to transports are listed in [Transport Quotas](../../../docs/framework/wcf/feature-details/transport-quotas.md).</span></span> <span data-ttu-id="16334-126">Uygulama katmanı kaynaklarının kullanımını kısıtlamak özellikleri üyeleri olan <xref:System.ServiceModel.Dispatcher.ServiceThrottle> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="16334-126">Properties that restrict the consumption of resources at the application layer are the members of the <xref:System.ServiceModel.Dispatcher.ServiceThrottle> class.</span></span>  
  
## <a name="detecting-application-and-performance-issues-related-to-quota-settings"></a><span data-ttu-id="16334-127">Uygulama ve kota ayarlarıyla ilgili performans sorunlarını algılama</span><span class="sxs-lookup"><span data-stu-id="16334-127">Detecting Application and Performance Issues Related to Quota Settings</span></span>  
 <span data-ttu-id="16334-128">Yukarıdaki değerleri Varsayılanları, genel güvenlik sorunları karşı temel koruma sağlarken çok çeşitli uygulama türleri arasında temel uygulama işlevselliğini etkinleştirmek için seçildi.</span><span class="sxs-lookup"><span data-stu-id="16334-128">The defaults of the preceding values have been chosen to enable basic application functionality across a wide range of application types while providing basic protection against common security issues.</span></span> <span data-ttu-id="16334-129">Ancak, aksi takdirde uygulamanın güvenli ve tasarlandığı gibi çalışır ancak farklı bir uygulama tasarımları bir veya daha fazla kısıtlama ayarlarını aşabilir.</span><span class="sxs-lookup"><span data-stu-id="16334-129">However, different application designs might exceed one or more throttle settings although the application otherwise is secure and would work as designed.</span></span> <span data-ttu-id="16334-130">Bu durumlarda, hangi Kısıtlama değerlerinin aşıldı tanımlamanız gerekir ve ne düzey ve uygulama verimliliğini artırmak için eylem uygun seyri üzerinde karar verin.</span><span class="sxs-lookup"><span data-stu-id="16334-130">In these cases, you must identify which throttle values are being exceeded and at what level, and decide on the appropriate course of action to increase application throughput.</span></span>  
  
 <span data-ttu-id="16334-131">Genellikle, uygulama yazmak ve bu hata ayıklama, ayarladığınızda <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> özelliğine `true` yapılandırma dosyası veya program aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="16334-131">Typically, when writing the application and debugging it, you set the <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> property to `true` in the configuration file or programmatically.</span></span> <span data-ttu-id="16334-132">Bu bildirir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] görüntülemek için istemci uygulaması hizmeti özel durum Yığın izlemeleri dönün.</span><span class="sxs-lookup"><span data-stu-id="16334-132">This instructs [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] to return service exception stack traces to the client application for viewing.</span></span> <span data-ttu-id="16334-133">Bu özellik, çoğu uygulama düzeyinde istisnalar hangi kota ayarları söz konusu, bu sorun olursa görüntülemek şekilde bildirir.</span><span class="sxs-lookup"><span data-stu-id="16334-133">This feature reports most application-level exceptions in such a way as to display which quota settings might be involved, if that is the problem.</span></span>  
  
 <span data-ttu-id="16334-134">Bazı özel durumlar uygulama katmanın görünürlüğünü aşağıda çalışma zamanında gerçekleşir ve bu mekanizmayı kullanarak döndürülmez ve bunlar özel tarafından ele alınması değil <xref:System.ServiceModel.Dispatcher.IErrorHandler?displayProperty=nameWithType> uygulaması.</span><span class="sxs-lookup"><span data-stu-id="16334-134">Some exceptions happen at run time below the visibility of the application layer and are not returned using this mechanism, and they might not be handled by a custom <xref:System.ServiceModel.Dispatcher.IErrorHandler?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="16334-135">Microsoft Visual Studio gibi geliştirme ortamında varsa, bu özel durumlar çoğunu otomatik olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="16334-135">If you are in a development environment like Microsoft Visual Studio, most of these exceptions are displayed automatically.</span></span> <span data-ttu-id="16334-136">Ancak, bazı özel durumlar gibi geliştirme ortamı ayarları tarafından maskelenecek [sadece kendi kodumu](http://go.microsoft.com/fwlink/?LinkId=82174) Visual Studio 2005'te ayarlar.</span><span class="sxs-lookup"><span data-stu-id="16334-136">However, some exceptions can be masked by development environment settings such as the [Just My Code](http://go.microsoft.com/fwlink/?LinkId=82174) settings in Visual Studio 2005.</span></span>  
  
 <span data-ttu-id="16334-137">Geliştirme ortamınızı yeteneklerini bağımsız olarak yeteneklerini kullanabilir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ileti izleme ve tüm özel durumları hata ayıklama ve uygulamalarınızın performansını ayarlamak için kaydetme.</span><span class="sxs-lookup"><span data-stu-id="16334-137">Regardless of the capabilities of your development environment, you can use capabilities of [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] tracing and message logging to debug all exceptions and tune the performance of your applications.</span></span> <span data-ttu-id="16334-138">Daha fazla bilgi için bkz: [kullanarak izleme uygulamanız sorun giderme için](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span><span class="sxs-lookup"><span data-stu-id="16334-138">For more information, see [Using Tracing to Troubleshoot Your Application](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span></span>  
  
## <a name="performance-issues-and-xmlserializer"></a><span data-ttu-id="16334-139">Performans sorunlarını ve XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="16334-139">Performance Issues and XmlSerializer</span></span>  
 <span data-ttu-id="16334-140">Hizmetler ve seri hale getirilebilir kullanarak veri türlerini kullanan istemci uygulamaları <xref:System.Xml.Serialization.XmlSerializer> oluşturmak ve bu veri türleri için seri hale getirme kodu, yavaş başlatma performansının düşmesine neden olabilir çalışma zamanında derleyin.</span><span class="sxs-lookup"><span data-stu-id="16334-140">Services and client applications that use data types that are serializable using the <xref:System.Xml.Serialization.XmlSerializer> generate and compile serialization code for those data types at run time, which can result in slow start-up performance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16334-141">Önceden oluşturulmuş serileştirme kod, yalnızca istemci uygulamaları ve Hizmetleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="16334-141">Pre-generated serialization code can be used only in client applications and not in services.</span></span>  
  
 <span data-ttu-id="16334-142">[ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) başlangıcından bu uygulamalar için uygulama için derlenmiş derlemelerden gerekli serileştirme kod oluşturarak performansı artırabilir.</span><span class="sxs-lookup"><span data-stu-id="16334-142">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) can improve start-up performance for these applications by generating the necessary serialization code from the compiled assemblies for the application.</span></span> <span data-ttu-id="16334-143">Daha fazla bilgi için bkz: [nasıl yapılır: Başlangıç saati, WCF istemci XmlSerializer kullanarak uygulamaları geliştirmek](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md).</span><span class="sxs-lookup"><span data-stu-id="16334-143">For more information, see [How to: Improve the Startup Time of WCF Client Applications using the XmlSerializer](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md).</span></span>  
  
## <a name="performance-issues-when-hosting-wcf-services-under-aspnet"></a><span data-ttu-id="16334-144">WCF hizmetleri ASP.NET altında barındırdığında performans sorunları</span><span class="sxs-lookup"><span data-stu-id="16334-144">Performance Issues When Hosting WCF Services Under ASP.NET</span></span>  
 <span data-ttu-id="16334-145">Bir WCF Hizmeti IIS ve ASP.NET altında barındırıldığında, IIS ve ASP.NET yapılandırma ayarlarını WCF hizmetini işleme ve bellek ayak etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="16334-145">When a WCF service is hosted under IIS and ASP.NET, the configuration settings of IIS and ASP.NET can affect the throughput and memory footprint of the WCF service.</span></span>  [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="16334-146">ASP.NET performansı bkz [ASP.NET performans geliştirme](http://go.microsoft.com/fwlink/?LinkId=186462).</span><span class="sxs-lookup"><span data-stu-id="16334-146"> ASP.NET performance, see [Improving ASP.NET Performance](http://go.microsoft.com/fwlink/?LinkId=186462).</span></span>  <span data-ttu-id="16334-147">Bir ayar olabilir istenmeyen sonuçlara olan <xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A>, bir özelliği olan <xref:System.Web.Configuration.ProcessModelSection>.</span><span class="sxs-lookup"><span data-stu-id="16334-147">One setting that might have unintended consequences is <xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A>, which is a property of the <xref:System.Web.Configuration.ProcessModelSection>.</span></span> <span data-ttu-id="16334-148">Uygulamanızın istemci sabit veya küçük bir sayısı varsa, ayarı <xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A> 2 CPU kullanımı % 100 yakın olan çok işlemcili bir makinede verimliliği artırma sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="16334-148">If your application has a fixed or small number of clients, setting <xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A> to 2 might provide a throughput boost on a multiprocessor machine that has a CPU utilization close to 100%.</span></span> <span data-ttu-id="16334-149">Bu artış performans maliyeti ile gelir: de ölçeklenebilirlik azaltabilir bellek kullanımında artışa neden olur.</span><span class="sxs-lookup"><span data-stu-id="16334-149">This increase in performance comes with a cost: it will also cause an increase in memory usage, which could reduce scalability.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16334-150">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="16334-150">See Also</span></span>  
 [<span data-ttu-id="16334-151">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="16334-151">Administration and Diagnostics</span></span>](../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="16334-152">Büyük veri ve akış</span><span class="sxs-lookup"><span data-stu-id="16334-152">Large Data and Streaming</span></span>](../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)