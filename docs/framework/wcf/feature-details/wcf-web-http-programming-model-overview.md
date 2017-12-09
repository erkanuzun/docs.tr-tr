---
title: "WCF Web HTTP Programlama Modeli Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 381fdc3a-6e6c-4890-87fe-91cca6f4b476
caps.latest.revision: "45"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eb32d1c9c0c0922dae27b2933259df9470cceeba
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-web-http-programming-model-overview"></a><span data-ttu-id="b3b41-102">WCF Web HTTP Programlama Modeli Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b3b41-102">WCF Web HTTP Programming Model Overview</span></span>
<span data-ttu-id="b3b41-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] WEB HTTP programlama modeli sağlar WEB HTTP Hizmetleri oluşturmak için gereken temel öğeleri [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b3b41-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] WEB HTTP programming model provides the basic elements required to build WEB HTTP services with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="b3b41-104">WEB HTTP Hizmetleri yelpazedeki Web tarayıcıları gibi olası istemcileri tarafından erişilecek tasarlanmıştır ve aşağıdaki benzersiz gereksinimlere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="b3b41-104"> WEB HTTP services are designed to be accessed by the widest range of possible clients, including Web browsers and have the following unique requirements:</span></span>  
  
-   <span data-ttu-id="b3b41-105">**URI ve URI İşleme** URI'ler WEB HTTP Hizmetleri tasarımında merkezi bir rol oynar.</span><span class="sxs-lookup"><span data-stu-id="b3b41-105">**URIs and URI Processing** URIs play a central role in the design of WEB HTTP services.</span></span> <span data-ttu-id="b3b41-106">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP programlama modeli kullanır <xref:System.UriTemplate> ve <xref:System.UriTemplateTable> sınıfları URI işleme özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b3b41-106">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP programming model uses the <xref:System.UriTemplate> and <xref:System.UriTemplateTable> classes to provide URI processing capabilities.</span></span>  
  
-   <span data-ttu-id="b3b41-107">**GET ve POST işlemleri için destek** WEB HTTP Hizmetleri GET fiili kullanım çeşitli yanı sıra veri alma için veri değişikliği ve Uzaktan çağırma fiiller çağırma.</span><span class="sxs-lookup"><span data-stu-id="b3b41-107">**Support for GET and POST operations** WEB HTTP services make use of the GET verb for data retrieval, in addition to various invoke verbs for data modification and remote invocation.</span></span> <span data-ttu-id="b3b41-108">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP programlama modeli kullanır <xref:System.ServiceModel.Web.WebGetAttribute> ve <xref:System.ServiceModel.Web.WebInvokeAttribute> hizmet işlemleri hem GET hem de diğer HTTP fiilleri gibi PUT, POST ilişkilendirmek ve silmek için.</span><span class="sxs-lookup"><span data-stu-id="b3b41-108">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP programming model uses the <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute> to associate service operations with both GET and other HTTP verbs like PUT, POST, and DELETE.</span></span>  
  
-   <span data-ttu-id="b3b41-109">**Birden çok veri biçimleri** Web stili Hizmetleri'ni birçok tür SOAP iletilerine ek veri işleme.</span><span class="sxs-lookup"><span data-stu-id="b3b41-109">**Multiple data formats** Web-style services process many kinds of data in addition to SOAP messages.</span></span> <span data-ttu-id="b3b41-110">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP programlama modeli kullanır <xref:System.ServiceModel.WebHttpBinding> ve <xref:System.ServiceModel.Description.WebHttpBehavior> XML belgeleri, JSON veri nesnesi ve ikili içerik görüntü, video dosyaları veya düz metin gibi akışları da dahil olmak üzere birçok farklı veri biçimleri desteklemek için.</span><span class="sxs-lookup"><span data-stu-id="b3b41-110">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP programming model uses the <xref:System.ServiceModel.WebHttpBinding> and <xref:System.ServiceModel.Description.WebHttpBehavior> to support many different data formats including XML documents, JSON data object, and streams of binary content such as images, video files, or plain text.</span></span>  
  
 <span data-ttu-id="b3b41-111">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP programlama modeli genişletir ulaşabileceği [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP Hizmetleri, AJAX ve JSON Hizmetleri ve dağıtım (ATOM/RSS) akışları içeren Web stili senaryoları için.</span><span class="sxs-lookup"><span data-stu-id="b3b41-111">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP programming model extends the reach of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to cover Web-style scenarios that include WEB HTTP services, AJAX and JSON services, and Syndication (ATOM/RSS) feeds.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="b3b41-112">AJAX ve JSON Hizmetleri bkz [AJAX tümleştirme ve JSON desteği](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md).</span><span class="sxs-lookup"><span data-stu-id="b3b41-112"> AJAX and JSON services, see [AJAX Integration and JSON Support](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="b3b41-113">Dağıtım, bkz: [WCF dağıtımı genel bakış](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b3b41-113"> Syndication, see [WCF Syndication Overview](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md).</span></span>  
  
 <span data-ttu-id="b3b41-114">Bir WEB HTTP hizmetinden döndürülen veri türleri hakkında ek bir kısıtlama yoktur.</span><span class="sxs-lookup"><span data-stu-id="b3b41-114">There are no extra restrictions on the types of data that can be returned from a WEB HTTP service.</span></span> <span data-ttu-id="b3b41-115">Bir WEB HTTP hizmeti işleminin serializable bir tür döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="b3b41-115">Any serializable type can be returned from an WEB HTTP service operation.</span></span> <span data-ttu-id="b3b41-116">Hangi veri türleri bir URL belirtilebilir bir sınırlama yoktur bir web tarayıcısı tarafından WEB HTTP hizmeti işlemleri olabileceğinden çağırır.</span><span class="sxs-lookup"><span data-stu-id="b3b41-116">Because WEB HTTP service operations can be invoke by a web browser there is a limitation on what data types can be specified in a URL.</span></span> <span data-ttu-id="b3b41-117">Varsayılan olarak desteklenen hangi türleri hakkında daha fazla bilgi için bkz: **UriTemplate sorgu dizesi parametreleri ve URL'leri** bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="b3b41-117">For more information on what types are supported by default see the **UriTemplate Query String Parameters and URLs** section below.</span></span> <span data-ttu-id="b3b41-118">Varsayılan davranış, gerçek parametre türü için bir URL içinde belirtilen parametreler dönüştürme belirten kendi T:System.ServiceModel.Dispatcher.QueryStringConverter uygulamasını sağlayarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b3b41-118">The default behavior can be changed by providing your own T:System.ServiceModel.Dispatcher.QueryStringConverter implementation which specifies how to convert the parameters specified in a URL to the actual parameter type.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="b3b41-119"><xref:System.ServiceModel.Dispatcher.QueryStringConverter></span><span class="sxs-lookup"><span data-stu-id="b3b41-119"> <xref:System.ServiceModel.Dispatcher.QueryStringConverter></span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="b3b41-120">İle yazılmış Hizmetler [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP programlama modeli SOAP iletilerine kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="b3b41-120">Services written with the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP programming model do not use SOAP messages.</span></span> <span data-ttu-id="b3b41-121">SOAP kullanılmadığı için güvenlik özellikleri tarafından sağlanan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b3b41-121">Because SOAP is not used, the security features provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cannot be used.</span></span> <span data-ttu-id="b3b41-122">Ancak taşıma tabanlı güvenlik hizmetiniz HTTPS ile barındırarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3b41-122">You can, however use transport-based security by hosting your service with HTTPS.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="b3b41-123">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenlik, bkz: [güvenliğine genel bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)</span><span class="sxs-lookup"><span data-stu-id="b3b41-123"> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security, see [Security Overview](../../../../docs/framework/wcf/feature-details/security-overview.md)</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="b3b41-124">WebDAV uzantısının IIS yüklemek, tüm PUT isteklerini işlemek için uzantı çalışır WebDAV bir HTTP 405 hata dönmek Web HTTP Hizmetleri neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="b3b41-124">Installing the WebDAV extension for IIS can cause Web HTTP services to return an HTTP 405 error as the WebDAV extension attempts to handle all PUT requests.</span></span> <span data-ttu-id="b3b41-125">Bu sorunu çözmek için WebDAV uzantısının kaldırın veya WebDAV uzantısı, web siteniz için devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3b41-125">To work around this issue you can uninstall the WebDAV extension or disable the WebDAV extension for your web site.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="b3b41-126">[IIS ve WebDav](http://learn.iis.net/page.aspx/357/webdav-for-iis-70/)</span><span class="sxs-lookup"><span data-stu-id="b3b41-126"> [IIS and WebDav](http://learn.iis.net/page.aspx/357/webdav-for-iis-70/)</span></span>  
  
## <a name="uri-processing-with-uritemplate-and-uritemplatetable"></a><span data-ttu-id="b3b41-127">UriTemplate ve UriTemplateTable işleme URI</span><span class="sxs-lookup"><span data-stu-id="b3b41-127">URI Processing with UriTemplate and UriTemplateTable</span></span>  
 <span data-ttu-id="b3b41-128">URI şablonları, yapısal olarak benzer URI'ler büyük kümesini ifade etmek için verimli bir sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b3b41-128">URI templates provide an efficient syntax for expressing large sets of structurally similar URIs.</span></span> <span data-ttu-id="b3b41-129">Örneğin, aşağıdaki şablonu, "a" ile başlamalı ve bitmelidir "c" Ara kesiminin ile değeri dikkate almaksızın üç segment URI'ler kümesini ifade eder: bir / {/c segmentlere}</span><span class="sxs-lookup"><span data-stu-id="b3b41-129">For example, the following template expresses the set of all three-segment URIs that begin with "a" and end with "c" without regard to the value of the intermediate segment: a/{segment}/c</span></span>  
  
 <span data-ttu-id="b3b41-130">Bu şablon URI'ler aşağıdaki gibi açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="b3b41-130">This template describes URIs like the following:</span></span>  
  
-   <span data-ttu-id="b3b41-131">a/x/c</span><span class="sxs-lookup"><span data-stu-id="b3b41-131">a/x/c</span></span>  
  
-   <span data-ttu-id="b3b41-132">a/y/c</span><span class="sxs-lookup"><span data-stu-id="b3b41-132">a/y/c</span></span>  
  
-   <span data-ttu-id="b3b41-133">a/z/c</span><span class="sxs-lookup"><span data-stu-id="b3b41-133">a/z/c</span></span>  
  
-   <span data-ttu-id="b3b41-134">ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="b3b41-134">and so on.</span></span>  
  
 <span data-ttu-id="b3b41-135">Bu şablonda değişmez değer yerine değişken kesimi kuşak gösterimi ("{segment}") gösterir.</span><span class="sxs-lookup"><span data-stu-id="b3b41-135">In this template, the curly brace notation ("{segment}") indicates a variable segment instead of a literal value.</span></span>  
  
 <span data-ttu-id="b3b41-136">.NET framework URI Şablonlarıyla Çalışma adlı bir API sağlar <xref:System.UriTemplate>.</span><span class="sxs-lookup"><span data-stu-id="b3b41-136">.NET Framework provides an API for working with URI templates called <xref:System.UriTemplate>.</span></span> <span data-ttu-id="b3b41-137">`UriTemplates`aşağıdakileri yapmanıza olanak sağlar:</span><span class="sxs-lookup"><span data-stu-id="b3b41-137">`UriTemplates` allow you to do the following:</span></span>  
  
-   <span data-ttu-id="b3b41-138">Aşağıdakilerden birini çağırabilirsiniz `Bind` üretmek için parametreleri kümesini yöntemleriyle bir *tamamen-kapalı URI* şablonu ile eşleşen.</span><span class="sxs-lookup"><span data-stu-id="b3b41-138">You can call one of the `Bind` methods with a set of parameters to produce a *fully-closed URI* that matches the template.</span></span> <span data-ttu-id="b3b41-139">Başka bir deyişle, tüm değişkenler URI şablonunu gerçek değerlerle değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="b3b41-139">This means all variables within the URI template are replaced with actual values.</span></span>  
  
-   <span data-ttu-id="b3b41-140">Çağırabilirsiniz `Match`(bir aday kendi destekçi URI bölümleri ve şablondaki değişkenleri göre etiketli URI'ın farklı bölümleri içeren bir sözlüğü döndürür aday ayırmak için bir şablon kullanır URI ile).</span><span class="sxs-lookup"><span data-stu-id="b3b41-140">You can call `Match`() with a candidate URI, which uses a template to break up a candidate URI into its constituent parts and returns a dictionary that contains the different parts of the URI labeled according to the variables in the template.</span></span>  
  
-   <span data-ttu-id="b3b41-141">`Bind`() ve `Match`(), böylece çağırabilirsiniz inverses olan `Match`( `Bind`(x)) ve başlattığınız ile aynı ortamı geri dönün.</span><span class="sxs-lookup"><span data-stu-id="b3b41-141">`Bind`() and `Match`() are inverses so that you can call `Match`( `Bind`( x ) ) and come back with the same environment you started with.</span></span>  
  
 <span data-ttu-id="b3b41-142">(Bir istek URİ'SİNDE tabanlı bir hizmet işlemi için gönderme olduğu gerekli özellikle sunucuda) birçok kez olan bir dizi izlemek istediğiniz <xref:System.UriTemplate> bağımsız olarak her kapsanan bir adresi bir veri yapısı nesneleri Şablonlar.</span><span class="sxs-lookup"><span data-stu-id="b3b41-142">There are many times (especially on the server, where dispatching a request to a service operation based on the URI is necessary) that you want to keep track of a set of <xref:System.UriTemplate> objects in a data structure that can independently address each of the contained templates.</span></span> <span data-ttu-id="b3b41-143"><xref:System.UriTemplateTable>URI şablonları kümesini temsil eder ve bir dizi şablonları ve bir aday URI verilen en iyi eşleşmeyi seçer.</span><span class="sxs-lookup"><span data-stu-id="b3b41-143"><xref:System.UriTemplateTable> represents a set of URI templates and selects the best match given a set of templates and a candidate URI.</span></span> <span data-ttu-id="b3b41-144">Bu belirli ağ yığınını ile bağlı değil ([!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dahil) için gerekli olan her yerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3b41-144">This is not affiliated with any particular networking stack ([!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] included) so you can use it wherever necessary.</span></span>  
  
 <span data-ttu-id="b3b41-145">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmet modeli kullanır <xref:System.UriTemplate> ve <xref:System.UriTemplateTable> URI tarafından tanımlanan bir dizi hizmet işlemleri ilişkilendirmek üzere bir <xref:System.UriTemplate>.</span><span class="sxs-lookup"><span data-stu-id="b3b41-145">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Service Model makes use of <xref:System.UriTemplate> and <xref:System.UriTemplateTable> to associate service operations with a set of URIs described by a <xref:System.UriTemplate>.</span></span> <span data-ttu-id="b3b41-146">Bir hizmet işlemi ile ilişkili bir <xref:System.UriTemplate>, kullanarak <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b3b41-146">A service operation is associated with a <xref:System.UriTemplate>, using either the <xref:System.ServiceModel.Web.WebGetAttribute> or the <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="b3b41-147"><xref:System.UriTemplate> ve <xref:System.UriTemplateTable>, bkz: [UriTemplate ve UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)</span><span class="sxs-lookup"><span data-stu-id="b3b41-147"> <xref:System.UriTemplate> and <xref:System.UriTemplateTable>, see [UriTemplate and UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)</span></span>  
  
## <a name="webget-and-webinvoke-attributes"></a><span data-ttu-id="b3b41-148">WebGet ve Webınvoke öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="b3b41-148">WebGet and WebInvoke Attributes</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="b3b41-149">WEB HTTP Hizmetleri alma fiilleri (örneğin HTTP GET) ek olarak çeşitli kullanın (örneğin HTTP POST, PUT ve Sil) fiillerini çağırma.</span><span class="sxs-lookup"><span data-stu-id="b3b41-149"> WEB HTTP services make use of retrieval verbs (for example HTTP GET) in addition to various invoke verbs (for example HTTP POST, PUT, and DELETE).</span></span> <span data-ttu-id="b3b41-150">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP programlama modeli sağlayan hizmet geliştiricileri denetim hem URI şablonunu ve kendi hizmet işlemleriyle ilişkili fiil <xref:System.ServiceModel.Web.WebGetAttribute> ve <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b3b41-150">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP programming model allows service developers to control the both the URI template and verb associated with their service operations with the <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span></span> <span data-ttu-id="b3b41-151"><xref:System.ServiceModel.Web.WebGetAttribute> Ve <xref:System.ServiceModel.Web.WebInvokeAttribute> nasıl tek tek işlemleri denetlemenizi URI'ler için bağlanan ve HTTP yöntemleri bu URI ile ilişkili izin verir.</span><span class="sxs-lookup"><span data-stu-id="b3b41-151">The <xref:System.ServiceModel.Web.WebGetAttribute> and the <xref:System.ServiceModel.Web.WebInvokeAttribute> allow you to control how individual operations get bound to URIs and the HTTP methods associated with those URIs.</span></span> <span data-ttu-id="b3b41-152">Örneğin, ekleme <xref:System.ServiceModel.Web.WebGetAttribute> ve <xref:System.ServiceModel.Web.WebInvokeAttribute> aşağıdaki kodda.</span><span class="sxs-lookup"><span data-stu-id="b3b41-152">For example, adding <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute> in the following code.</span></span>  
  
```  
[ServiceContract]  
interface ICustomer  
{  
  //"View It"  
  
  [WebGet]  
  Customer GetCustomer():  
  
  //"Do It"  
    [WebInvoke]  
  Customer UpdateCustomerName( string id,   
                               string newName );  
}  
```  
  
 <span data-ttu-id="b3b41-153">Önceki kod, aşağıdaki HTTP isteklerini yapmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b3b41-153">The preceding code allows you to make the following HTTP requests.</span></span>  
  
 `GET /GetCustomer`  
  
 `POST /UpdateCustomerName`  
  
 <span data-ttu-id="b3b41-154"><xref:System.ServiceModel.Web.WebInvokeAttribute>POST ancak varsayılanlara bunu diğer fiiller için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3b41-154"><xref:System.ServiceModel.Web.WebInvokeAttribute> defaults to POST but you can use it for other verbs too.</span></span>  
  
```  
[ServiceContract]  
interface ICustomer  
{  
  //"View It" -> HTTP GET  
    [WebGet( UriTemplate="customers/{id}" )]  
  Customer GetCustomer( string id ):  
  
  //"Do It" -> HTTP PUT  
  [WebInvoke( UriTemplate="customers/{id}", Method="PUT" )]  
  Customer UpdateCustomer( string id, Customer newCustomer );  
}  
```  
  
 <span data-ttu-id="b3b41-155">Tam bir örnek görmek için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kullanan hizmet [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP programlama modeli, bkz: [nasıl yapılır: temel bir WCF Web HTTP hizmeti oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)</span><span class="sxs-lookup"><span data-stu-id="b3b41-155">To see a complete sample of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that uses the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP programming model, see [How to: Create a Basic WCF Web HTTP Service](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)</span></span>  
  
## <a name="uritemplate-query-string-parameters-and-urls"></a><span data-ttu-id="b3b41-156">UriTemplate sorgu dizesi parametreleri ve URL'leri</span><span class="sxs-lookup"><span data-stu-id="b3b41-156">UriTemplate Query String Parameters and URLs</span></span>  
 <span data-ttu-id="b3b41-157">Web stili Hizmetleri hizmet işlemle ilişkili bir URL yazarak bir Web tarayıcısından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="b3b41-157">Web-style services can be called from a Web browser by typing a URL that is associated with a service operation.</span></span> <span data-ttu-id="b3b41-158">Bu hizmet işlemleri URL'de dize biçimindeki belirtilmelidir sorgu dizesi parametreleri sürebilir.</span><span class="sxs-lookup"><span data-stu-id="b3b41-158">These service operations may take query string parameters that must be specified in a string form within the URL.</span></span> <span data-ttu-id="b3b41-159">Aşağıdaki tabloda bir URL ve kullanılan biçimi içinde geçirilen türleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b3b41-159">The following table shows the types that can be passed within a URL and the format used.</span></span>  
  
|<span data-ttu-id="b3b41-160">Tür</span><span class="sxs-lookup"><span data-stu-id="b3b41-160">Type</span></span>|<span data-ttu-id="b3b41-161">Biçimi</span><span class="sxs-lookup"><span data-stu-id="b3b41-161">Format</span></span>|  
|----------|------------|  
|<xref:System.Byte>|<span data-ttu-id="b3b41-162">0 - 255</span><span class="sxs-lookup"><span data-stu-id="b3b41-162">0 - 255</span></span>|  
|<xref:System.SByte>|<span data-ttu-id="b3b41-163">-128 - 127</span><span class="sxs-lookup"><span data-stu-id="b3b41-163">-128 - 127</span></span>|  
|<xref:System.Int16>|<span data-ttu-id="b3b41-164">-32768 - 32767</span><span class="sxs-lookup"><span data-stu-id="b3b41-164">-32768 - 32767</span></span>|  
|<xref:System.Int32>|<span data-ttu-id="b3b41-165">-2,147,483,648 - 2,147,483,647</span><span class="sxs-lookup"><span data-stu-id="b3b41-165">-2,147,483,648 - 2,147,483,647</span></span>|  
|<xref:System.Int64>|<span data-ttu-id="b3b41-166">-9,223,372,036,854,775,808 - 9,223,372,036,854,775,807</span><span class="sxs-lookup"><span data-stu-id="b3b41-166">-9,223,372,036,854,775,808 - 9,223,372,036,854,775,807</span></span>|  
|<xref:System.UInt16>|<span data-ttu-id="b3b41-167">0 - 65535</span><span class="sxs-lookup"><span data-stu-id="b3b41-167">0 - 65535</span></span>|  
|<xref:System.UInt32>|<span data-ttu-id="b3b41-168">0 - 4,294,967,295</span><span class="sxs-lookup"><span data-stu-id="b3b41-168">0 - 4,294,967,295</span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="b3b41-169">0 - 18,446,744,073,709,551,615</span><span class="sxs-lookup"><span data-stu-id="b3b41-169">0 - 18,446,744,073,709,551,615</span></span>|  
|<xref:System.Single>|<span data-ttu-id="b3b41-170">-3.402823e38 - 3.402823e38 (üstel gösterimde gerekli değildir)</span><span class="sxs-lookup"><span data-stu-id="b3b41-170">-3.402823e38 - 3.402823e38 (exponent notation is not required)</span></span>|  
|<xref:System.Double>|<span data-ttu-id="b3b41-171">-1.79769313486232e308 - 1.79769313486232e308 (üstel gösterimde gerekli değildir)</span><span class="sxs-lookup"><span data-stu-id="b3b41-171">-1.79769313486232e308 - 1.79769313486232e308 (exponent notation is not required)</span></span>|  
|<xref:System.Char>|<span data-ttu-id="b3b41-172">Herhangi bir tek karakteri</span><span class="sxs-lookup"><span data-stu-id="b3b41-172">Any single character</span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="b3b41-173">Tüm ondalık standart gösteriminde (üs yok)</span><span class="sxs-lookup"><span data-stu-id="b3b41-173">Any decimal in standard notation (no exponent)</span></span>|  
|<xref:System.Boolean>|<span data-ttu-id="b3b41-174">TRUE veya False (duyarsız büyük-küçük harf)</span><span class="sxs-lookup"><span data-stu-id="b3b41-174">True or False (case insensitive)</span></span>|  
|<xref:System.String>|<span data-ttu-id="b3b41-175">Herhangi bir dize (dize desteklenmez ve yok kaçış yapılır null)</span><span class="sxs-lookup"><span data-stu-id="b3b41-175">Any string (null string is not supported and no escaping is done)</span></span>|  
|<xref:System.DateTime>|<span data-ttu-id="b3b41-176">AA/GG/YYYY</span><span class="sxs-lookup"><span data-stu-id="b3b41-176">MM/DD/YYYY</span></span><br /><br /> <span data-ttu-id="b3b41-177">AA/GG/YYYY SS: DD: [AM &#124; PM]</span><span class="sxs-lookup"><span data-stu-id="b3b41-177">MM/DD/YYYY HH:MM:SS [AM&#124;PM]</span></span><br /><br /> <span data-ttu-id="b3b41-178">Ayın günü yıl</span><span class="sxs-lookup"><span data-stu-id="b3b41-178">Month Day Year</span></span><br /><br /> <span data-ttu-id="b3b41-179">Ay gün yıl ss [AM &#124; PM]</span><span class="sxs-lookup"><span data-stu-id="b3b41-179">Month Day Year HH:MM:SS [AM&#124;PM]</span></span>|  
|<xref:System.TimeSpan>|<span data-ttu-id="b3b41-180">GG SS: DD:</span><span class="sxs-lookup"><span data-stu-id="b3b41-180">DD.HH:MM:SS</span></span><br /><br /> <span data-ttu-id="b3b41-181">Burada gg gün, ss = = saat, dd dakika, SS = = saniye</span><span class="sxs-lookup"><span data-stu-id="b3b41-181">Where DD = Days, HH = Hours, MM = minutes, SS = Seconds</span></span>|  
|<xref:System.Guid>|<span data-ttu-id="b3b41-182">Örneğin bir GUID:</span><span class="sxs-lookup"><span data-stu-id="b3b41-182">A GUID, for example:</span></span><br /><br /> <span data-ttu-id="b3b41-183">936DA01F-9ABD-4d9d-80C7-02AF85C822A8</span><span class="sxs-lookup"><span data-stu-id="b3b41-183">936DA01F-9ABD-4d9d-80C7-02AF85C822A8</span></span>|  
|<xref:System.DateTimeOffset>|<span data-ttu-id="b3b41-184">AA/GG/YYYY SS: DD: SS: DD</span><span class="sxs-lookup"><span data-stu-id="b3b41-184">MM/DD/YYYY HH:MM:SS MM:SS</span></span><br /><br /> <span data-ttu-id="b3b41-185">Burada gg gün, ss = = saat, dd dakika, SS = = saniye</span><span class="sxs-lookup"><span data-stu-id="b3b41-185">Where DD = Days, HH = Hours, MM = minutes, SS = Seconds</span></span>|  
|<span data-ttu-id="b3b41-186">Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="b3b41-186">Enumerations</span></span>|<span data-ttu-id="b3b41-187">Numaralandırma değeri örneğin, aşağıdaki kodda gösterildiği gibi numaralandırması tanımlayan.</span><span class="sxs-lookup"><span data-stu-id="b3b41-187">The enumeration value for example, which defines the enumeration as shown in the following code.</span></span><br /><br /> `public enum Days{ Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday };`<br /><br /> <span data-ttu-id="b3b41-188">Tek tek numaralandırma değerlerini (ya da bunlara karşılık gelen tamsayı değerler) herhangi birini sorgu dizesinde belirtilen.</span><span class="sxs-lookup"><span data-stu-id="b3b41-188">Any of the individual enumeration values (or their corresponding integer values) may be specified in the query string.</span></span>|  
|<span data-ttu-id="b3b41-189">Türleri bir `TypeConverterAttribute` , dönüştürebilir türü için ve bir dize gösterimi.</span><span class="sxs-lookup"><span data-stu-id="b3b41-189">Types that have a `TypeConverterAttribute` that can convert the type to and from a string representation.</span></span>|<span data-ttu-id="b3b41-190">Tür dönüştürücü bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b3b41-190">Depends on the Type Converter.</span></span>|  
  
## <a name="formats-and-the-wcf-web-http-programming-model"></a><span data-ttu-id="b3b41-191">Biçimleri ve WCF WEB HTTP programlama modeli</span><span class="sxs-lookup"><span data-stu-id="b3b41-191">Formats and the WCF WEB HTTP Programming Model</span></span>  
 <span data-ttu-id="b3b41-192">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP programlama modeli birçok farklı veri biçimleri ile çalışmak için yeni özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b3b41-192">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP programming model has new features to work with many different data formats.</span></span> <span data-ttu-id="b3b41-193">Bağlama katmanında <xref:System.ServiceModel.WebHttpBinding> okuma ve yazma aşağıdaki farklı veri türleri:</span><span class="sxs-lookup"><span data-stu-id="b3b41-193">At the binding layer, the <xref:System.ServiceModel.WebHttpBinding> can read and write the following different kinds of data:</span></span>  
  
-   <span data-ttu-id="b3b41-194">XML</span><span class="sxs-lookup"><span data-stu-id="b3b41-194">XML</span></span>  
  
-   <span data-ttu-id="b3b41-195">JSON</span><span class="sxs-lookup"><span data-stu-id="b3b41-195">JSON</span></span>  
  
-   <span data-ttu-id="b3b41-196">Donuk ikili akışlar</span><span class="sxs-lookup"><span data-stu-id="b3b41-196">Opaque binary streams</span></span>  
  
 <span data-ttu-id="b3b41-197">Yani [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP programlama modeli, istediğiniz türde veriyi işleyebilen ancak karşı programlama <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="b3b41-197">This means the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP programming model can handle any type of data but, you may be programming against <xref:System.IO.Stream>.</span></span>  
  
 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)]<span data-ttu-id="b3b41-198">JSON verilerini (AJAX) yanı sıra dağıtım akışlarını (ATOM ve RSS dahil) destekler.</span><span class="sxs-lookup"><span data-stu-id="b3b41-198"> provides support for JSON data (AJAX) as well as Syndication feeds (including ATOM and RSS).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="b3b41-199">Bu özellikler bkz [WCF Web HTTP biçimlendirme](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)[WCF dağıtımı genel bakış](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md) ve [AJAX tümleştirme ve JSON desteği](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md).</span><span class="sxs-lookup"><span data-stu-id="b3b41-199"> these features, see [WCF Web HTTP Formatting](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)[WCF Syndication Overview](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md) and [AJAX Integration and JSON Support](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md).</span></span>  
  
## <a name="wcf-web-http-programming-model-and-security"></a><span data-ttu-id="b3b41-200">WCF WEB HTTP programlama modeli ve güvenlik</span><span class="sxs-lookup"><span data-stu-id="b3b41-200">WCF WEB HTTP Programming Model and Security</span></span>  
 <span data-ttu-id="b3b41-201">Çünkü [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP programlama modeli desteklemez WS-* protokoller, güvenli hale getirmek için tek yolu bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP hizmeti hizmeti SSL ile HTTPS üzerinden kullanıma etmektir.</span><span class="sxs-lookup"><span data-stu-id="b3b41-201">Because the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP programming model does not support the WS-* protocols, the only way to secure a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP service is to expose the service over HTTPS using SSL.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="b3b41-202">SSL ile ayarlama [!INCLUDE[iisver](../../../../includes/iisver-md.md)], bkz: [IIS'te SSL uygulama](http://go.microsoft.com/fwlink/?LinkId=131613)</span><span class="sxs-lookup"><span data-stu-id="b3b41-202"> setting up SSL with [!INCLUDE[iisver](../../../../includes/iisver-md.md)], see [How to implement SSL in IIS](http://go.microsoft.com/fwlink/?LinkId=131613)</span></span>  
  
## <a name="troubleshooting-the-wcf-web-http-programming-model"></a><span data-ttu-id="b3b41-203">WCF WEB HTTP programlama modeli sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="b3b41-203">Troubleshooting the WCF WEB HTTP Programming Model</span></span>  
 <span data-ttu-id="b3b41-204">WCF WEB HTTP çağırma zaman Hizmetleri kullanarak bir <xref:System.ServiceModel.Channels.ChannelFactoryBase%601> bir kanal oluşturmak için <xref:System.ServiceModel.Description.WebHttpBehavior> kullanan <xref:System.ServiceModel.EndpointAddress> dosya olsa bile farklı bir ayarla <xref:System.ServiceModel.EndpointAddress> geçirilir <xref:System.ServiceModel.Channels.ChannelFactoryBase%601>.</span><span class="sxs-lookup"><span data-stu-id="b3b41-204">When calling WCF WEB HTTP services using a <xref:System.ServiceModel.Channels.ChannelFactoryBase%601> to create a channel, the <xref:System.ServiceModel.Description.WebHttpBehavior> uses the <xref:System.ServiceModel.EndpointAddress> set in the configuration file even if a different <xref:System.ServiceModel.EndpointAddress> is passed to the <xref:System.ServiceModel.Channels.ChannelFactoryBase%601>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3b41-205">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b3b41-205">See Also</span></span>  
 [<span data-ttu-id="b3b41-206">WCF dağıtımı</span><span class="sxs-lookup"><span data-stu-id="b3b41-206">WCF Syndication</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)  
 [<span data-ttu-id="b3b41-207">WCF Web HTTP programlama nesnesi modeli</span><span class="sxs-lookup"><span data-stu-id="b3b41-207">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)  
 [<span data-ttu-id="b3b41-208">WCF Web HTTP programlama modeli</span><span class="sxs-lookup"><span data-stu-id="b3b41-208">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)