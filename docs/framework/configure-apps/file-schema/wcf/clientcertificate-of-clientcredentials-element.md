---
title: "&lt;clientCredentials&gt; Öğesi &lt;clientCertificate&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b3fa000-3434-4142-a178-11903bdd2c5d
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b42167491de72eff5f17dfd8f25ad862c118c23f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltclientcertificategt-of-ltclientcredentialsgt-element"></a><span data-ttu-id="f747a-102">&lt;clientCredentials&gt; Öğesi &lt;clientCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="f747a-102">&lt;clientCertificate&gt; of &lt;clientCredentials&gt; Element</span></span>
<span data-ttu-id="f747a-103">Bir hizmet için bir istemci kimlik doğrulaması için kullanılan bir X.509 sertifikası tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f747a-103">Defines an X.509 certificate used to authenticate a client to a service.</span></span>  
  
 <span data-ttu-id="f747a-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f747a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f747a-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="f747a-105">\<behaviors></span></span>  
<span data-ttu-id="f747a-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="f747a-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="f747a-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="f747a-107">\<behavior></span></span>  
<span data-ttu-id="f747a-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="f747a-108">\<clientCredentials></span></span>  
<span data-ttu-id="f747a-109">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="f747a-109">\<clientCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f747a-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f747a-110">Syntax</span></span>  
  
```xml  
<clientCertificate findValue="String"   
    storeLocation="LocalMachine/CurrentUser"  
    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f747a-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f747a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f747a-112">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="f747a-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f747a-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f747a-113">Attributes</span></span>  
  
|<span data-ttu-id="f747a-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f747a-114">Attribute</span></span>|<span data-ttu-id="f747a-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f747a-115">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="f747a-116">X.509 sertifika deposunda arama için değer içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="f747a-116">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="f747a-117">Özniteliğinde bulunan türü gereksinimlerini karşılaması gerekir `X509FindType` öznitelik değeri.</span><span class="sxs-lookup"><span data-stu-id="f747a-117">The type contained in the attribute must satisfy the requirements of the `X509FindType` attribute value.</span></span> <span data-ttu-id="f747a-118">Varsayılan boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="f747a-118">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="f747a-119">İstemcinin hizmete kendi kimliğini doğrulamak için kullandığı X.509 sertifikasının konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="f747a-119">Specifies the location of the X.509 certificate that the client uses to authenticate itself to the service.</span></span> <span data-ttu-id="f747a-120">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f747a-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f747a-121">-LocalMachine: Yerel Makine sertifika deposuna.</span><span class="sxs-lookup"><span data-stu-id="f747a-121">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="f747a-122">-Currentuser'a: sertifika deposuna geçerli kullanıcıya atanmış.</span><span class="sxs-lookup"><span data-stu-id="f747a-122">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="f747a-123">LocalMachine varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="f747a-123">The default is LocalMachine.</span></span> <span data-ttu-id="f747a-124">Bu öznitelik türünde <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span><span class="sxs-lookup"><span data-stu-id="f747a-124">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
|`storeName`|<span data-ttu-id="f747a-125">Aranacak X.509 Sertifika deposu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f747a-125">Specifies the name of the X.509 certificate store to search.</span></span> <span data-ttu-id="f747a-126">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f747a-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f747a-127">-Adres Defteri: Diğer kullanıcılar sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="f747a-127">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="f747a-128">-AuthRoot: sertifika deposunu üçüncü taraf sertifika yetkilileri (CA'lar) için.</span><span class="sxs-lookup"><span data-stu-id="f747a-128">-   AuthRoot: Certificate store for third-party certificate authorities (CAs).</span></span><br /><span data-ttu-id="f747a-129">-CertificateAuthority: Ara sertifika yetkilileri (CA) sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="f747a-129">-   CertificateAuthority: Certificate store for intermediate certificate authorities (CAs).</span></span><br /><span data-ttu-id="f747a-130">-İzin verilmeyen: mağaza iptal edilen sertifikaları için sertifika.</span><span class="sxs-lookup"><span data-stu-id="f747a-130">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="f747a-131">-My: Sertifika deposunda kişisel sertifikalar için.</span><span class="sxs-lookup"><span data-stu-id="f747a-131">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="f747a-132">-Kök: Güvenilen kök sertifika yetkilileri (CA'lar) sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="f747a-132">-   Root: Certificate store for trusted root certificate authorities (CAs).</span></span><br /><span data-ttu-id="f747a-133">-TrustedPeople: Doğrudan güvenilir kişiler ve kaynaklar sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="f747a-133">-   TrustedPeople: Certificate store for directly trusted people and resources.</span></span><br /><span data-ttu-id="f747a-134">-TrustedPublisher: Doğrudan Güvenilen Yayımcılar sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="f747a-134">-   TrustedPublisher: Certificate store for directly trusted publishers.</span></span><br /><br /> <span data-ttu-id="f747a-135">Varsayılan değer My.</span><span class="sxs-lookup"><span data-stu-id="f747a-135">The default is My.</span></span> <span data-ttu-id="f747a-136">Bu öznitelik türünde <xref:System.Security.Cryptography.X509Certificates.StoreName>.</span><span class="sxs-lookup"><span data-stu-id="f747a-136">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreName>.</span></span>|  
|<span data-ttu-id="f747a-137">X509FindType</span><span class="sxs-lookup"><span data-stu-id="f747a-137">X509FindType</span></span>|<span data-ttu-id="f747a-138">Yürütülecek X.509 arama türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f747a-138">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="f747a-139">İçinde yer alan türü `findValue` özniteliği bu öznitelik gereksinimlerini karşılaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f747a-139">The type contained in the `findValue` attribute must satisfy the requirements of this attribute.</span></span> <span data-ttu-id="f747a-140">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f747a-140">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f747a-141">-FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="f747a-141">-   FindByThumbPrint</span></span><br /><span data-ttu-id="f747a-142">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="f747a-142">-   FindBySubjectName</span></span><br /><span data-ttu-id="f747a-143">-FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="f747a-143">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="f747a-144">-FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="f747a-144">-   FindByIssuerName</span></span><br /><span data-ttu-id="f747a-145">-FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="f747a-145">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="f747a-146">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="f747a-146">-   FindBySerialNumber</span></span><br /><span data-ttu-id="f747a-147">-FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="f747a-147">-   FindByTimeValid</span></span><br /><span data-ttu-id="f747a-148">-FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="f747a-148">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="f747a-149">-FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="f747a-149">-   FindByTemplateName</span></span><br /><span data-ttu-id="f747a-150">-FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="f747a-150">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="f747a-151">-FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="f747a-151">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="f747a-152">-FindByExtension</span><span class="sxs-lookup"><span data-stu-id="f747a-152">-   FindByExtension</span></span><br /><span data-ttu-id="f747a-153">-FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="f747a-153">-   FindByKeyUsage</span></span><br /><span data-ttu-id="f747a-154">-FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="f747a-154">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="f747a-155">FindBySubjectDistinguishedName varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="f747a-155">The default value is FindBySubjectDistinguishedName.</span></span> <span data-ttu-id="f747a-156">Bu öznitelik türünde <xref:System.Security.Cryptography.X509Certificates.X509FindType>.</span><span class="sxs-lookup"><span data-stu-id="f747a-156">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509FindType>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f747a-157">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f747a-157">Child Elements</span></span>  
 <span data-ttu-id="f747a-158">Yok.</span><span class="sxs-lookup"><span data-stu-id="f747a-158">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f747a-159">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f747a-159">Parent Elements</span></span>  
  
|<span data-ttu-id="f747a-160">Öğe</span><span class="sxs-lookup"><span data-stu-id="f747a-160">Element</span></span>|<span data-ttu-id="f747a-161">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f747a-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f747a-162">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="f747a-162">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="f747a-163">Bir hizmet için istemci kimlik doğrulaması için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f747a-163">Specifies the credentials used to authenticate the client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f747a-164">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f747a-164">Remarks</span></span>  
 <span data-ttu-id="f747a-165">Bu yapılandırma öğesi bu öğeye sahip istemci kimlik doğrulaması için kullanılan sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="f747a-165">This configuration element specifies the certificate used to authenticate the client with this element.</span></span> [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)]<span data-ttu-id="f747a-166">[Nasıl yapılır: istemci kimlik bilgileri değerlerini belirtme](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).</span><span class="sxs-lookup"><span data-stu-id="f747a-166"> [How to: Specify Client Credential Values](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f747a-167">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f747a-167">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ClientCertificate%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>  
 [<span data-ttu-id="f747a-168">Güvenlik davranışları</span><span class="sxs-lookup"><span data-stu-id="f747a-168">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="f747a-169">Nasıl yapılır: istemci kimlik bilgileri değerlerini belirtme</span><span class="sxs-lookup"><span data-stu-id="f747a-169">How to: Specify Client Credential Values</span></span>](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)  
 [<span data-ttu-id="f747a-170">İstemcilerinin güvenliğini sağlama</span><span class="sxs-lookup"><span data-stu-id="f747a-170">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="f747a-171">Sertifikalar ile çalışma</span><span class="sxs-lookup"><span data-stu-id="f747a-171">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="f747a-172">Hizmetler ve istemcileri güvenli hale getirme</span><span class="sxs-lookup"><span data-stu-id="f747a-172">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)