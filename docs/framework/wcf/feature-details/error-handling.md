---
title: "Hata işleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c948841a-7db9-40ae-9b78-587d216cbcaf
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 215fb30772e4f1b25e20303b3f83d6fe0c00ebae
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="error-handling"></a><span data-ttu-id="f034a-102">Hata işleme</span><span class="sxs-lookup"><span data-stu-id="f034a-102">Error handling</span></span>
## <a name="error-handling-in-windows-communication-foundation"></a><span data-ttu-id="f034a-103">Windows Communication Foundation işleme hatası</span><span class="sxs-lookup"><span data-stu-id="f034a-103">Error Handling in Windows Communication Foundation</span></span>  
 <span data-ttu-id="f034a-104">Bir hizmeti beklenmeyen bir özel durum ya da hata karşılaştığında, bir özel durum işleme çözüm tasarımı için birden çok yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="f034a-104">When a service encounters an unexpected exception or error, there are multiple ways to design an exception-handling solution.</span></span> <span data-ttu-id="f034a-105">Varken hiçbir tek "doğru" veya "en iyi uygulama" hata işleme çözüm, birden çok geçerli yol bir göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="f034a-105">While there is no single "correct" or "best practice" error-handling solution, there are multiple valid paths for one to consider.</span></span> <span data-ttu-id="f034a-106">Bir WCF uygulama, türünü ve özel durumları, işlenmiş sıklığını karmaşıklığına bağlı olarak, aşağıdaki listeden birden çok yaklaşımlar işlenmemiş yapısını birleştiren bir karma çözümü uygulamak normalde önerilir özel durumlar ve herhangi bir izleme, günlük veya ilke gereksinimleri ilişkilendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="f034a-106">It is normally recommended that one implement a hybrid solution that combines multiple approaches from the list below, depending on the complexity of the WCF implementation, the type and frequency of the exceptions, the handled vs. unhandled nature of the exceptions, and any associated tracing, logging, or policy requirements.</span></span>  
  
 <span data-ttu-id="f034a-107">Bu çözümler, bu bölümün geri kalanında daha derine açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f034a-107">These solutions are explained more deeply in the rest of this section.</span></span>  
  
### <a name="the-microsoft-enterprise-library"></a><span data-ttu-id="f034a-108">Microsoft Enterprise kitaplığı</span><span class="sxs-lookup"><span data-stu-id="f034a-108">The Microsoft Enterprise Library</span></span>  
 <span data-ttu-id="f034a-109">Microsoft Enterprise kitaplığı özel durum işleme uygulama bloğu ortak tasarım desenleri uygulamak ve kurumsal uygulama mimari katmanları tüm oluşan özel durum işleme için tutarlı bir strateji oluşturmak yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="f034a-109">The Microsoft Enterprise Library Exception Handling Application Block helps implement common design patterns and create a consistent strategy for processing exceptions that occur in all architectural layers of an enterprise application.</span></span> <span data-ttu-id="f034a-110">Uygulama bileşenleri catch deyimleri bulunan tipik kod desteklemek üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f034a-110">It is designed to support the typical code contained in catch statements in application components.</span></span> <span data-ttu-id="f034a-111">Bu kod (örneğin, özel durum bilgilerini kaydeder kodu) bir uygulama boyunca aynı catch blokları içinde yinelenen yerine, özel durum işleme uygulama bloğu geliştiricilerin bu mantığı yeniden kullanılabilir özel durum işleyicileri olarak kapsülleyen olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="f034a-111">Instead of repeating this code (such as code that logs exception information) in identical catch blocks throughout an application, the Exception Handling Application Block allows developers to encapsulate this logic as reusable exception handlers.</span></span>  
  
 <span data-ttu-id="f034a-112">Bu kitaplık out-of--box hataya sözleşme özel durum işleyicisi içerir.</span><span class="sxs-lookup"><span data-stu-id="f034a-112">This Library includes out-of-the-box a Fault Contract Exception Handler.</span></span> <span data-ttu-id="f034a-113">Bu özel durum işleyici Windows® Communication Foundation (WCF) hizmetini sınırlarında kullanılmak üzere tasarlanmış ve yeni bir arıza sözleşme özel durumu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f034a-113">This exception handler is designed for use at Windows® Communication Foundation (WCF) service boundaries, and generates a new Fault Contract from the exception.</span></span>  
  
 <span data-ttu-id="f034a-114">Yaygın olarak kullanılan en iyi uygulamaları ekleyebilir ve özel durum uygulamanızın genelinde işleme için ortak bir yaklaşım sağlamak için uygulama blokları hedefleyin.</span><span class="sxs-lookup"><span data-stu-id="f034a-114">Application blocks aim to incorporate commonly used best practices and provide a common approach for exception handling throughout your application.</span></span> <span data-ttu-id="f034a-115">Diğer taraftan, özel hata işleyicileri ve hataya sözleşmeleri birinin üzerinde kendi geliştirilen ayrıca çok kullanışlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="f034a-115">On the other hand, custom error handlers and fault contracts developed on one’s own can also be very useful.</span></span> <span data-ttu-id="f034a-116">Örneğin, özel hata işleyicileri FaultExceptions tüm özel durumlar otomatik olarak Yükselt ve günlüğe kaydetme özellikleri uygulamanıza eklemek için mükemmel bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="f034a-116">For instance, custom error handlers provide an excellent opportunity to automatically promote all exceptions to FaultExceptions and also to add logging capabilities to your application.</span></span>  
  
 <span data-ttu-id="f034a-117">Daha fazla bilgi için lütfen bkz [Microsoft Enterprise Kitaplığı](http://msdn.microsoft.com/library/ff632023.aspx).</span><span class="sxs-lookup"><span data-stu-id="f034a-117">For more information, please see [Microsoft Enterprise Library](http://msdn.microsoft.com/library/ff632023.aspx).</span></span>  
  
### <a name="dealing-with-expected-exceptions"></a><span data-ttu-id="f034a-118">Beklenen özel durumlar postalarla</span><span class="sxs-lookup"><span data-stu-id="f034a-118">Dealing with Expected Exceptions</span></span>  
 <span data-ttu-id="f034a-119">Eylem uygun seyri olan her işlem ya da ilgili genişletilebilirlik noktası beklenen özel durumları yakalamak için bunlar veriler kurtarılamaz, uygun özel hataya bir FaultException iade karar verdikten sonra\<T ></span><span class="sxs-lookup"><span data-stu-id="f034a-119">The proper course of action is to catch expected exceptions in every operation or relevant extensibility point, decide whether they can be recovered from, and return the proper custom fault in a FaultException\<T></span></span>  
  
### <a name="dealing-with-unexpected-exceptions-using-an-ierrorhandler"></a><span data-ttu-id="f034a-120">Beklenmeyen bir IErrorHandler kullanarak istisnalar ele alma</span><span class="sxs-lookup"><span data-stu-id="f034a-120">Dealing with Unexpected Exceptions using an IErrorHandler</span></span>  
 <span data-ttu-id="f034a-121">Beklenmeyen durumlarla başa çıkmak için önerilen yol eyleminin "bir IErrorHandler kanca" kullanmamaktır.</span><span class="sxs-lookup"><span data-stu-id="f034a-121">To deal with unexpected exceptions, the recommended course of action is to "hook" an IErrorHandler.</span></span> <span data-ttu-id="f034a-122">Hata işleyicileri yalnızca özel durumlarını yakalama WCF çalışma zamanı düzeyinde ("hizmet modeli" katman), kanal katmanında.</span><span class="sxs-lookup"><span data-stu-id="f034a-122">Error handlers only catch exceptions at the WCF runtime level (the "service model" layer), not at the channel layer.</span></span> <span data-ttu-id="f034a-123">Çoğu senaryoda önerilmez özel bir kanal oluşturmak için yalnızca bir IErrorHandler kanal düzeyinde kanca şekilde denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f034a-123">The only way to hook an IErrorHandler at the channel level is to create a custom channel, which is not recommended in most scenarios.</span></span>  
  
 <span data-ttu-id="f034a-124">"Beklenmeyen bir özel durum" genellikle ne kurtarılamaz bir özel durum, ne de bir işlem özel durumu olan; Bu, bunun yerine, beklenmeyen bir kullanıcı özel durumdur.</span><span class="sxs-lookup"><span data-stu-id="f034a-124">An "unexpected exception" is generally neither an irrecoverable exception nor a processing exception; it is, instead, an unexpected user exception.</span></span> <span data-ttu-id="f034a-125">Kurtarılamaz bir özel durum (bir bellek yetersiz özel durum gibi) – bir genellikle işlenen tarafından [hizmet modeli özel durum işleyicisi](http://msdn.microsoft.com/library/system.servicemodel.dispatcher.exceptionhandler.aspx) otomatik olarak – genellikle düzgün işlenemez ve bu tür özel bir durumu işlemek için yalnızca açıklaması Ek günlük hiç olabilir veya standart bir özel durum istemciye döndürülecek.</span><span class="sxs-lookup"><span data-stu-id="f034a-125">An irrecoverable exception (such as an out-of-memory exception) – one generally handled by the [Service Model Exception Handler](http://msdn.microsoft.com/library/system.servicemodel.dispatcher.exceptionhandler.aspx) automatically – cannot generally be handled gracefully, and the only reason to handle such an exception at all may be do additional logging or to return a standard exception to the client.</span></span> <span data-ttu-id="f034a-126">Genellikle çok erken ya da çok geç hata işleyici tarafından müdahale olduğundan bir işlem özel durum iletisi – işlemde oluşur Örneğin, seri hale getirme, kodlayıcı veya biçimlendirici düzeyinde – genellikle bir IErrorHandler işlenemiyor Bu özel durumları ortaya süre.</span><span class="sxs-lookup"><span data-stu-id="f034a-126">A processing exception occurs in the processing of the message – for example, at the serialization, encoder, or formatter level – generally cannot be handled at an IErrorHandler, because it is generally either too early or too late for the error handler to intervene by the time these exceptions occur.</span></span> <span data-ttu-id="f034a-127">Benzer şekilde, aktarım özel durumlar bir IErrorHandler işlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="f034a-127">Similarly, transport exceptions cannot be handled at an IErrorHandler.</span></span>  
  
 <span data-ttu-id="f034a-128">Bir özel durum bir IErrorHandler ile açıkça uygulamanızın davranışını kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f034a-128">With an IErrorHandler, you can explicitly control the behavior of your application when an exception is thrown.</span></span> <span data-ttu-id="f034a-129">Görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f034a-129">You may:</span></span>  
  
1.  <span data-ttu-id="f034a-130">Bir arıza istemciye göndermek isteyip istemediğinizi karar verin</span><span class="sxs-lookup"><span data-stu-id="f034a-130">Decide whether or not to send a fault to the client</span></span>  
  
2.  <span data-ttu-id="f034a-131">Bir özel durum hatası ile değiştir</span><span class="sxs-lookup"><span data-stu-id="f034a-131">Replace an exception with a fault</span></span>  
  
3.  <span data-ttu-id="f034a-132">Bir hata ile başka bir hataya değiştirin</span><span class="sxs-lookup"><span data-stu-id="f034a-132">Replace a fault with another fault</span></span>  
  
4.  <span data-ttu-id="f034a-133">Günlüğü veya izleme gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="f034a-133">Perform logging or tracing</span></span>  
  
5.  <span data-ttu-id="f034a-134">Diğer özel etkinlikleri gerçekleştirmek</span><span class="sxs-lookup"><span data-stu-id="f034a-134">Perform other custom activities</span></span>  
  
 <span data-ttu-id="f034a-135">Hizmetiniz için kanal dağıtıcıları ErrorHandlers özelliğine ekleyerek bir özel hata işleyici yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f034a-135">One can install a custom error handler by adding it to the ErrorHandlers property of the channel dispatchers for your service.</span></span>  <span data-ttu-id="f034a-136">Birden fazla hata işleyicisine olması mümkündür ve bu koleksiyona eklendikleri sırayla çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f034a-136">It is possible to have more than one error handler and they are called in the order they are added to this collection.</span></span>  
  
 <span data-ttu-id="f034a-137">IErrorHandler.ProvideFault istemciye gönderilen hata iletisi denetler.</span><span class="sxs-lookup"><span data-stu-id="f034a-137">IErrorHandler.ProvideFault controls the fault message that is sent to the client.</span></span> <span data-ttu-id="f034a-138">Bu yöntem, hizmetinizde bir işlem tarafından oluşturulan özel durum türü ne olursa olsun çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f034a-138">This method is called regardless of the type of the exception thrown by an operation in your service.</span></span> <span data-ttu-id="f034a-139">Hiçbir işlem burada gerçekleştirilirse, WCF varsayılan davranışını varsayar ve olmamış gibi hiçbir özel hata işleyicileri yerinde devam eder.</span><span class="sxs-lookup"><span data-stu-id="f034a-139">If no operation is performed here, WCF assumes its default behaviour and continues as if there were no custom error handlers in place.</span></span>  
  
 <span data-ttu-id="f034a-140">(Örneği değil atıldı ve kanal Faulted durumuna taşınmaz sağlanarak) istemciye gönderilmeden önce hataları için özel durumları dönüştürme için merkezi bir konum oluşturmak istediğinizde bu yaklaşımı belki de kullanabilirsiniz bir alandır.</span><span class="sxs-lookup"><span data-stu-id="f034a-140">One area that you could perhaps use this approach is when you want to create a central place for converting exceptions to faults before they are sent to the client (ensuring that the instance is not disposed and the channel is not moved to the Faulted state).</span></span>  
  
 <span data-ttu-id="f034a-141">IErrorHandler.HandleError yöntemi genellikle hata ile ilgili davranışları hata günlüğü oluşturmayı, gibi kapatılıyor uygulama, vb. Sistem bildirimleri uygulamak için kullanılır. Hizmetin birden fazla yerde IErrorHandler.HandleError çağrılabilir ve burada hata atılır, bağlı olarak HandleError yöntemi olabilir işlemi olarak iş parçacığı tarafından çağrılan değil; veya Bu konuda, hiçbir garanti hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="f034a-141">The IErrorHandler.HandleError method is usually used to implement error-related behaviors such as error logging, system notifications, shutting down the application, etc. IErrorHandler.HandleError can be called at multiple places inside the service, and depending on where the error is thrown, the HandleError method may or may not be called by the same thread as the operation; no guarantees are made in this regard.</span></span>  
  
### <a name="dealing-with-exceptions-outside-wcf"></a><span data-ttu-id="f034a-142">Özel durumlar dışında WCF postalarla</span><span class="sxs-lookup"><span data-stu-id="f034a-142">Dealing with Exceptions outside WCF</span></span>  
 <span data-ttu-id="f034a-143">Genellikle, yapılandırma özel durumları, veritabanı bağlantı dizesi özel durumları ve benzer diğer özel durumlar WCF uygulaması bağlamında oluşabilir, ancak kendileri olmayan nedeni hizmet modeli veya web hizmeti özel durumları.</span><span class="sxs-lookup"><span data-stu-id="f034a-143">Often, configuration exceptions, database connection string exceptions, and other similar exceptions may occur within the context of a WCF application, but are themselves are not exceptions caused by the service model or the web service itself.</span></span> <span data-ttu-id="f034a-144">Bu özel durumlar "Normal" özel durumlar web hizmetine dış ve yalnızca ortamında dış diğer özel durumlar işlenecek şekilde yapılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f034a-144">These exceptions are "regular" exceptions external to the web service, and should be handled just as other external exceptions in the environment are to be handled.</span></span>  
  
### <a name="tracing-exceptions"></a><span data-ttu-id="f034a-145">Özel durum izleme</span><span class="sxs-lookup"><span data-stu-id="f034a-145">Tracing exceptions</span></span>  
 <span data-ttu-id="f034a-146">İzleme, bir olası tüm özel durumları görebileceğiniz yalnızca "catch-tüm" yerdir.</span><span class="sxs-lookup"><span data-stu-id="f034a-146">Tracing is the only "catch-all" place where one can potentially see all exceptions.</span></span> <span data-ttu-id="f034a-147">İzleme ve kaydetme izleme ve günlük özel durumları hakkında daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="f034a-147">For more information on tracing and logging exceptions, see Tracing and Logging.</span></span>  
  
### <a name="uri-template-errors-when-using-webgetattribute-and-webinvokeattribute"></a><span data-ttu-id="f034a-148">WebGetAttribute hem de WebInvokeAttribute kullanırken URI şablonunu hataları</span><span class="sxs-lookup"><span data-stu-id="f034a-148">URI template errors when using WebGetAttribute and WebInvokeAttribute</span></span>  
 <span data-ttu-id="f034a-149">WebGet ve Webınvoke öznitelikleri işlemi parametreleri için istek adresi bileşenlerinin eşleştiren bir URI şablonunu belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f034a-149">The WebGet and WebInvoke attributes allow you to specify a URI template that maps components of the request address to operation parameters.</span></span> <span data-ttu-id="f034a-150">Örneğin, URI şablonunu "hava durumu / {state} / {Şehir}" istek adresi değişmez değer belirteçleri, durumu adlı bir parametre ve şehir adlı bir parametre eşler.</span><span class="sxs-lookup"><span data-stu-id="f034a-150">For example, the URI template "weather/{state}/{city}" maps the request address into literal tokens, a parameter named state, and a parameter named city.</span></span> <span data-ttu-id="f034a-151">Bu parametreler sonra adıyla bazı işleminin resmi parametrelerin bağlı.</span><span class="sxs-lookup"><span data-stu-id="f034a-151">These parameters might then be bound by name to some of the formal parameters of the operation.</span></span>  
  
 <span data-ttu-id="f034a-152">Yazılı sözleşme biçimsel parametresi dize olmayan türlerde olabilir şablon parametreleri dizeler URI içindeki biçiminde görünür.</span><span class="sxs-lookup"><span data-stu-id="f034a-152">The template parameters appear in the form of strings within the URI while the formal parameters of a typed contract might be of non-string types.</span></span> <span data-ttu-id="f034a-153">Bu nedenle, bir dönüştürme işlemi çağrılabilir önce gerçekleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f034a-153">Therefore, a conversion needs to take place before the operation can be invoked.</span></span> <span data-ttu-id="f034a-154">A [dönüştürme biçimleri tablosunun](http://msdn.microsoft.com/library/bb412172.aspx) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f034a-154">A [table of conversion formats](http://msdn.microsoft.com/library/bb412172.aspx) is available.</span></span>  
  
 <span data-ttu-id="f034a-155">Ancak, dönüştürme başarısız olursa, ardından bir şeyler yanlış geçtiğini bilmeniz işlemi olanak yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="f034a-155">However, if the conversion fails, then there's no way to let the operation know that something has gone wrong.</span></span> <span data-ttu-id="f034a-156">Tür dönüşümü, bunun yerine bir gönderme hatası biçiminde ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="f034a-156">The type conversion instead surfaces in the form of a dispatch failure.</span></span>  
  
 <span data-ttu-id="f034a-157">Tür dönüştürme gönderme hatası olabilir diğer türlerde gönderme hataları gibi aynı hata işleyicisine yükleyerek sahip denetlenir.</span><span class="sxs-lookup"><span data-stu-id="f034a-157">A type conversion dispatch failure can be inspected the same as with many other types of dispatch failures by installing an error handler.</span></span> <span data-ttu-id="f034a-158">Hizmet düzeyi özel durumları işleme IErrorHandler genişletilebilirlik noktası çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="f034a-158">The IErrorHandler extensibility point is called to handle service-level exceptions.</span></span> <span data-ttu-id="f034a-159">Buradan, geri çağırana – gönderilecek yanıt olarak hem de özel görevler gerçekleştirmek ve raporlama – seçmiş olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f034a-159">From there, the response to be sent back to the caller – as well as perform any custom tasks and reporting – may be chosen.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f034a-160">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f034a-160">See Also</span></span>  
 [<span data-ttu-id="f034a-161">Temel WCF hata işleme</span><span class="sxs-lookup"><span data-stu-id="f034a-161">Basic WCF Error Handling</span></span>](http://msdn.microsoft.com/library/gg281715.aspx)