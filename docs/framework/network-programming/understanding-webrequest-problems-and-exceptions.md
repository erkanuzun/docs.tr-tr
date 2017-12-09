---
title: "Anlama WebRequest sorunlarını ve özel durumlar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74a361a5-e912-42d3-8f2e-8e9a96880a2b
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d29321297a880ca961805687e51c7bb63f70ffbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="understanding-webrequest-problems-and-exceptions"></a><span data-ttu-id="4700c-102">Anlama WebRequest sorunlarını ve özel durumlar</span><span class="sxs-lookup"><span data-stu-id="4700c-102">Understanding WebRequest Problems and Exceptions</span></span>
<span data-ttu-id="4700c-103"><xref:System.Net.WebRequest>ve türetilmiş sınıflarının (<xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, ve <xref:System.Net.FileWebRequest>) olağan dışı bir koşul göstermek için özel durumlar oluşturma.</span><span class="sxs-lookup"><span data-stu-id="4700c-103"><xref:System.Net.WebRequest> and its derived classes (<xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, and <xref:System.Net.FileWebRequest>) throw exceptions to signal an abnormal condition.</span></span> <span data-ttu-id="4700c-104">Bazen bu sorunlar çözümleme açık değil.</span><span class="sxs-lookup"><span data-stu-id="4700c-104">Sometimes the resolution of these problems is not obvious.</span></span>  
  
## <a name="solutions"></a><span data-ttu-id="4700c-105">Çözümleri</span><span class="sxs-lookup"><span data-stu-id="4700c-105">Solutions</span></span>  
 <span data-ttu-id="4700c-106">İncelemek <xref:System.Net.WebException.Status%2A> özelliği <xref:System.Net.WebException> sorunu belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="4700c-106">Examine the <xref:System.Net.WebException.Status%2A> property of the <xref:System.Net.WebException> to determine the problem.</span></span> <span data-ttu-id="4700c-107">Aşağıdaki tabloda, birkaç durum değerleri ve bazı olası çözümler gösterir.</span><span class="sxs-lookup"><span data-stu-id="4700c-107">The following table shows several status values and some possible resolutions.</span></span>  
  
|<span data-ttu-id="4700c-108">Durum</span><span class="sxs-lookup"><span data-stu-id="4700c-108">Status</span></span>|<span data-ttu-id="4700c-109">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="4700c-109">Details</span></span>|<span data-ttu-id="4700c-110">Çözüm</span><span class="sxs-lookup"><span data-stu-id="4700c-110">Solution</span></span>|  
|------------|-------------|--------------|  
|<xref:System.Net.WebExceptionStatus.SendFailure><br /><br /> <span data-ttu-id="4700c-111">veya</span><span class="sxs-lookup"><span data-stu-id="4700c-111">-or-</span></span><br /><br /> <xref:System.Net.WebExceptionStatus.ReceiveFailure>|<span data-ttu-id="4700c-112">Temel alınan yuva ile ilgili bir sorun yoktur.</span><span class="sxs-lookup"><span data-stu-id="4700c-112">There is a problem with the underlying socket.</span></span> <span data-ttu-id="4700c-113">Bağlantı sıfırlanmış.</span><span class="sxs-lookup"><span data-stu-id="4700c-113">The connection may have been reset.</span></span>|<span data-ttu-id="4700c-114">Yeniden bağlanma ve isteği yeniden gönderin.</span><span class="sxs-lookup"><span data-stu-id="4700c-114">Reconnect and resend the request.</span></span><br /><br /> <span data-ttu-id="4700c-115">En son hizmet paketinin yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="4700c-115">Make sure the latest service pack is installed.</span></span><br /><br /> <span data-ttu-id="4700c-116">Değerini artırın <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="4700c-116">Increase the value of the <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="4700c-117">Ayarlama <xref:System.Net.HttpWebRequest.KeepAlive%2A?displayProperty=nameWithType> için `false`.</span><span class="sxs-lookup"><span data-stu-id="4700c-117">Set <xref:System.Net.HttpWebRequest.KeepAlive%2A?displayProperty=nameWithType> to `false`.</span></span><br /><br /> <span data-ttu-id="4700c-118">İle en fazla bağlantı sayısını artıracak <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="4700c-118">Increase the number of maximum connections with the <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> property.</span></span><br /><br /> <span data-ttu-id="4700c-119">Proxy yapılandırmasını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="4700c-119">Check the proxy configuration.</span></span><br /><br /> <span data-ttu-id="4700c-120">SSL kullanıyorsanız, sunucu işlemi sertifika deposuna erişim izni olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="4700c-120">If using SSL, make sure the server process has permission to access the Certificate store.</span></span><br /><br /> <span data-ttu-id="4700c-121">Büyük miktarda veri göndermek istiyorsanız, ayarlayın <xref:System.Net.HttpWebRequest.AllowWriteStreamBuffering%2A> için `false`.</span><span class="sxs-lookup"><span data-stu-id="4700c-121">If sending a large amount of data, set <xref:System.Net.HttpWebRequest.AllowWriteStreamBuffering%2A> to `false`.</span></span>|  
|<xref:System.Net.WebExceptionStatus.TrustFailure>|<span data-ttu-id="4700c-122">Sunucu sertifikası doğrulanamadı.</span><span class="sxs-lookup"><span data-stu-id="4700c-122">The server certificate could not be validated.</span></span>|<span data-ttu-id="4700c-123">Internet Explorer kullanarak URI açmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="4700c-123">Try to open the URI using Internet Explorer.</span></span> <span data-ttu-id="4700c-124">IE tarafından görüntülenen tüm güvenlik uyarıları çözümleyin.</span><span class="sxs-lookup"><span data-stu-id="4700c-124">Resolve any Security Alerts displayed by IE.</span></span> <span data-ttu-id="4700c-125">Güvenlik Uyarısı çözümlenemiyor sonra uygulayan bir sertifika ilkesi sınıf oluşturabilirsiniz <xref:System.Net.ICertificatePolicy> döndüren `true`ve ona geçirin <xref:System.Net.ServicePointManager.CertificatePolicy%2A>.</span><span class="sxs-lookup"><span data-stu-id="4700c-125">If you cannot resolve the security alert, then you can create a certificate policy class that implements <xref:System.Net.ICertificatePolicy> that returns `true`, and pass it to <xref:System.Net.ServicePointManager.CertificatePolicy%2A>.</span></span><br /><br /> <span data-ttu-id="4700c-126">Başvurmak [http://support.microsoft.com/?id=823177](http://go.microsoft.com/fwlink/?LinkID=179653).</span><span class="sxs-lookup"><span data-stu-id="4700c-126">Refer to [http://support.microsoft.com/?id=823177](http://go.microsoft.com/fwlink/?LinkID=179653).</span></span><br /><br /> <span data-ttu-id="4700c-127">Sunucu sertifikası imzalı sertifika yetkilisinin sertifikayı Internet Explorer'da güvenilen sertifika yetkilisi listesine eklendiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="4700c-127">Make sure that the certificate of the Certificate Authority that signed the server certificate is added to the Trusted Certificate Authority list in Internet Explorer.</span></span><br /><br /> <span data-ttu-id="4700c-128">Ana bilgisayar adı URL'de sunucu sertifikasının ortak adına eşleştiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="4700c-128">Make sure that the host name in the URL matches the common name on the server certificate.</span></span>|  
|<xref:System.Net.WebExceptionStatus.SecureChannelFailure>|<span data-ttu-id="4700c-129">SSL işlem sırasında bir hata oluştu veya sertifika ile ilgili bir sorun yoktur.</span><span class="sxs-lookup"><span data-stu-id="4700c-129">An error occurred in the SSL transaction, or there is a certificate problem.</span></span>|<span data-ttu-id="4700c-130">.NET Framework sürüm 1.1 yalnızca SSL sürüm 3.0 destekler.</span><span class="sxs-lookup"><span data-stu-id="4700c-130">The .NET Framework version 1.1 only supports SSL version 3.0.</span></span> <span data-ttu-id="4700c-131">Sunucu yalnızca TLS sürüm 1.0 veya 2.0 sürümünde SSL kullanıyorsa, özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="4700c-131">If the server is using only TLS version 1.0 or SSL version 2.0, the exception is thrown.</span></span> <span data-ttu-id="4700c-132">Yükseltme .NET Framework sürüm 2.0 ve ayarlayın <xref:System.Net.ServicePointManager.SecurityProtocol%2A> sunucu eşleşecek şekilde.</span><span class="sxs-lookup"><span data-stu-id="4700c-132">Upgrade to .NET Framework version 2.0, and set <xref:System.Net.ServicePointManager.SecurityProtocol%2A> to match the server.</span></span><br /><br /> <span data-ttu-id="4700c-133">İstemci sertifikası, sunucunun güvenmediği bir sertifika yetkilisi (CA) tarafından imzalanmış.</span><span class="sxs-lookup"><span data-stu-id="4700c-133">The client certificate was signed by a Certificate Authority (CA) that the server does not trust.</span></span> <span data-ttu-id="4700c-134">CA'ın sertifikasını sunucuya yükleyin.</span><span class="sxs-lookup"><span data-stu-id="4700c-134">Install the CA's certificate on the server.</span></span> <span data-ttu-id="4700c-135">Bkz: [http://support.microsoft.com/?id=332077](http://go.microsoft.com/fwlink/?LinkID=179654).</span><span class="sxs-lookup"><span data-stu-id="4700c-135">See [http://support.microsoft.com/?id=332077](http://go.microsoft.com/fwlink/?LinkID=179654).</span></span><br /><br /> <span data-ttu-id="4700c-136">En son hizmet paketine sahip olduğunuzdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="4700c-136">Make sure you have the latest service pack installed.</span></span>|  
|<xref:System.Net.WebExceptionStatus.ConnectFailure>|<span data-ttu-id="4700c-137">Bağlantı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="4700c-137">The connection failed.</span></span>|<span data-ttu-id="4700c-138">Bir güvenlik duvarı veya proxy bağlantıyı engelliyor.</span><span class="sxs-lookup"><span data-stu-id="4700c-138">A firewall or proxy is blocking the connection.</span></span> <span data-ttu-id="4700c-139">Güvenlik Duvarı veya proxy bağlantıya izin verecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="4700c-139">Modify the firewall or proxy to allow the connection.</span></span><br /><br /> <span data-ttu-id="4700c-140">Açıkça belirtmek bir <xref:System.Net.WebProxy> çağırarak istemci uygulamasında <xref:System.Net.WebProxy> Oluşturucusu (WebServiceProxyClass.Proxy yeni adımdaki ([http://server:80](http://server/), doğru)).</span><span class="sxs-lookup"><span data-stu-id="4700c-140">Explicitly designate a <xref:System.Net.WebProxy> in the client application by calling the <xref:System.Net.WebProxy> constructor (WebServiceProxyClass.Proxy = new WebProxy([http://server:80](http://server/), true)).</span></span><br /><br /> <span data-ttu-id="4700c-141">FileMon veya Regmon çalışan işlem kimliğini WSPWSP.dll, HKLM\System\CurrentControlSet\Services\DnsCache veya HKLM\System\CurrentControlSet\Services\WinSock2 erişmek için gerekli izinlere sahip olduğundan emin olmak için çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4700c-141">Run Filemon or Regmon to ensure that the worker process identity has the necessary permissions to access WSPWSP.dll, HKLM\System\CurrentControlSet\Services\DnsCache or HKLM\System\CurrentControlSet\Services\WinSock2.</span></span>|  
|<xref:System.Net.WebExceptionStatus.NameResolutionFailure>|<span data-ttu-id="4700c-142">Etki alanı adı hizmeti ana bilgisayar adı çözümlenemedi.</span><span class="sxs-lookup"><span data-stu-id="4700c-142">The Domain Name Service could not resolve the host name.</span></span>|<span data-ttu-id="4700c-143">Proxy doğru şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="4700c-143">Configure the proxy correctly.</span></span> <span data-ttu-id="4700c-144">Bkz: [http://support.microsoft.com/?id=318140](http://go.microsoft.com/fwlink/?LinkID=179655).</span><span class="sxs-lookup"><span data-stu-id="4700c-144">See [http://support.microsoft.com/?id=318140](http://go.microsoft.com/fwlink/?LinkID=179655).</span></span><br /><br /> <span data-ttu-id="4700c-145">Herhangi bir virüsten koruma yazılımı yüklü veya güvenlik duvarı bağlantıyı engellemediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="4700c-145">Ensure that any installed anti-virus software or firewall is not blocking the connection.</span></span>|  
|<xref:System.Net.WebExceptionStatus.RequestCanceled>|<span data-ttu-id="4700c-146"><xref:System.Net.WebRequest.Abort%2A>çağrılan, veya bir hata oldu.</span><span class="sxs-lookup"><span data-stu-id="4700c-146"><xref:System.Net.WebRequest.Abort%2A> was called, or an error occurred.</span></span>|<span data-ttu-id="4700c-147">Bu sorunun nedeni istemci veya sunucu üzerinde ağır bir yük.</span><span class="sxs-lookup"><span data-stu-id="4700c-147">This problem might be caused by a heavy load on the client or server.</span></span> <span data-ttu-id="4700c-148">Yükü azaltın.</span><span class="sxs-lookup"><span data-stu-id="4700c-148">Reduce the load.</span></span><br /><br /> <span data-ttu-id="4700c-149">Artırmak <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> ayarı.</span><span class="sxs-lookup"><span data-stu-id="4700c-149">Increase the <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> setting.</span></span><br /><br /> <span data-ttu-id="4700c-150">Bkz: [http://support.microsoft.com/?id=821268](http://go.microsoft.com/fwlink/?LinkID=179656) Web hizmeti performans ayarlarını değiştirmek için.</span><span class="sxs-lookup"><span data-stu-id="4700c-150">See [http://support.microsoft.com/?id=821268](http://go.microsoft.com/fwlink/?LinkID=179656) to modify Web service performance settings.</span></span>|  
|<xref:System.Net.WebExceptionStatus.ConnectionClosed>|<span data-ttu-id="4700c-151">Uygulama zaten kapatılmış bir yuva yazma girişiminde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="4700c-151">The application attempted to write to a socket that has already been closed.</span></span>|<span data-ttu-id="4700c-152">İstemci veya sunucu aşırı yüklendi.</span><span class="sxs-lookup"><span data-stu-id="4700c-152">The client or server is overloaded.</span></span> <span data-ttu-id="4700c-153">Yükü azaltın.</span><span class="sxs-lookup"><span data-stu-id="4700c-153">Reduce the load.</span></span><br /><br /> <span data-ttu-id="4700c-154">Artırmak <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> ayarı.</span><span class="sxs-lookup"><span data-stu-id="4700c-154">Increase the <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> setting.</span></span><br /><br /> <span data-ttu-id="4700c-155">Bkz: [http://support.microsoft.com/?id=821268](http://go.microsoft.com/fwlink/?LinkID=179656) Web hizmeti performans ayarlarını değiştirmek için.</span><span class="sxs-lookup"><span data-stu-id="4700c-155">See [http://support.microsoft.com/?id=821268](http://go.microsoft.com/fwlink/?LinkID=179656) to modify Web service performance settings.</span></span>|  
|<xref:System.Net.WebExceptionStatus.MessageLengthLimitExceeded>|<span data-ttu-id="4700c-156">Belirlenen sınırı (<xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>) iletide uzunluğu aşıldı.</span><span class="sxs-lookup"><span data-stu-id="4700c-156">The limit set (<xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>) on the message length was exceeded.</span></span>|<span data-ttu-id="4700c-157">Değerini artırın <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="4700c-157">Increase the value of the <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A> property.</span></span>|  
|<xref:System.Net.WebExceptionStatus.ProxyNameResolutionFailure>|<span data-ttu-id="4700c-158">Etki alanı adı hizmeti proxy konak adı çözümlenemedi.</span><span class="sxs-lookup"><span data-stu-id="4700c-158">The Domain Name Service could not resolve the proxy host name.</span></span>|<span data-ttu-id="4700c-159">Proxy doğru şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="4700c-159">Configure the proxy correctly.</span></span> <span data-ttu-id="4700c-160">Bkz: [http://support.microsoft.com/?id=318140](http://go.microsoft.com/fwlink/?LinkID=179655).</span><span class="sxs-lookup"><span data-stu-id="4700c-160">See [http://support.microsoft.com/?id=318140](http://go.microsoft.com/fwlink/?LinkID=179655).</span></span><br /><br /> <span data-ttu-id="4700c-161">Zorla <xref:System.Net.HttpWebRequest> ayarlayarak proxy kullanmayı <xref:System.Net.HttpWebRequest.Proxy%2A> özelliğine `null`.</span><span class="sxs-lookup"><span data-stu-id="4700c-161">Force <xref:System.Net.HttpWebRequest> to use no proxy by setting the <xref:System.Net.HttpWebRequest.Proxy%2A> property to `null`.</span></span>|  
|<xref:System.Net.WebExceptionStatus.ServerProtocolViolation>|<span data-ttu-id="4700c-162">Sunucudan gelen yanıtı geçerli bir HTTP yanıt değil.</span><span class="sxs-lookup"><span data-stu-id="4700c-162">The response from the server is not a valid HTTP response.</span></span> <span data-ttu-id="4700c-163">Sunucu yanıtı HTTP 1.1 RFC ile uyumlu değil, .NET Framework algıladığında, bu sorun oluşur.</span><span class="sxs-lookup"><span data-stu-id="4700c-163">This problem occurs when the .NET Framework detects that the server response does not comply with HTTP 1.1 RFC.</span></span> <span data-ttu-id="4700c-164">Yanıtı yanlış üstbilgilerinde veya yanlış üstbilgi ayırıcısı içeriyor. Bu sorun ortaya çıkabilir. RFC 2616 HTTP 1.1 ve sunucudan gelen yanıt geçerli biçimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4700c-164">This problem may occur when the response contains incorrect headers or incorrect header delimiters.RFC 2616 defines HTTP 1.1 and the valid format for the response from the server.</span></span> <span data-ttu-id="4700c-165">Daha fazla bilgi için bkz: [http://www.ietf.org](http://go.microsoft.com/fwlink/?LinkID=147388).</span><span class="sxs-lookup"><span data-stu-id="4700c-165">For more information, see [http://www.ietf.org](http://go.microsoft.com/fwlink/?LinkID=147388).</span></span>|<span data-ttu-id="4700c-166">İşlemin bir ağ izlemesi yapın ve yanıt üstbilgileri inceleyin.</span><span class="sxs-lookup"><span data-stu-id="4700c-166">Get a network trace of the transaction and examine the headers in the response.</span></span><br /><br /> <span data-ttu-id="4700c-167">Uygulamanız sunucu yanıtı olmadan gerektiriyorsa (Bu bir güvenlik sorunu olabilir) ayrıştırma, kümesi `useUnsafeHeaderParsing` için `true` yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="4700c-167">If your application requires the server response without parsing (this could be a security issue), set `useUnsafeHeaderParsing` to `true` in the configuration file.</span></span> <span data-ttu-id="4700c-168">Bkz: [ \<httpWebRequest > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/httpwebrequest-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="4700c-168">See [\<httpWebRequest> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/httpwebrequest-element-network-settings.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4700c-169">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4700c-169">See Also</span></span>  
 <xref:System.Net.HttpWebRequest>  
 <xref:System.Net.HttpWebResponse>  
 <xref:System.Net.Dns>