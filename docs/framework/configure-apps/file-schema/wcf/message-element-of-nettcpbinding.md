---
title: "&lt;netTcpBinding&gt; &lt;ileti&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d71edd9-c085-4c2e-b6d3-980c313366f9
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f589dea8cace4a049c701cd00fd9a62d40fcf219
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltmessagegt-element-of-ltnettcpbindinggt"></a><span data-ttu-id="641b4-102">&lt;netTcpBinding&gt; &lt;ileti&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="641b4-102">&lt;message&gt; element of &lt;netTcpBinding&gt;</span></span>
<span data-ttu-id="641b4-103">İleti düzeyi güvenlik gereksinimleri ile yapılandırılmış bir uç nokta türünü tanımlar [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="641b4-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>  
  
 <span data-ttu-id="641b4-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="641b4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="641b4-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="641b4-105">\<bindings></span></span>  
<span data-ttu-id="641b4-106">\<netTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="641b4-106">\<netTcpBinding></span></span>  
<span data-ttu-id="641b4-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="641b4-107">\<binding></span></span>  
<span data-ttu-id="641b4-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="641b4-108">\<security></span></span>  
<span data-ttu-id="641b4-109">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="641b4-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="641b4-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="641b4-110">Syntax</span></span>  
  
```xml  
<message   
      algorithmSuite=System.Servicemodel.Security.SecurityAlgorithmsuite  
    clientCredentialType="None/Windows/UserName/Certificate/IssuedToken"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="641b4-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="641b4-111">Attributes and Elements</span></span>  
 <span data-ttu-id="641b4-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="641b4-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="641b4-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="641b4-113">Attributes</span></span>  
  
|<span data-ttu-id="641b4-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="641b4-114">Attribute</span></span>|<span data-ttu-id="641b4-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="641b4-115">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="641b4-116">İleti şifreleme ve anahtar-wrap algoritmaları ayarlar.</span><span class="sxs-lookup"><span data-stu-id="641b4-116">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="641b4-117">Algoritmaları ve anahtar boyutları tarafından belirlenen <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="641b4-117">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="641b4-118">Bu algoritmalar, güvenlik ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen eşlenir.</span><span class="sxs-lookup"><span data-stu-id="641b4-118">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="641b4-119">Olası değerler aşağıdaki tabloda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="641b4-119">Possible values are shown in the following table.</span></span> <span data-ttu-id="641b4-120">Varsayılan değer `Basic256` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="641b4-120">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="641b4-121">Hizmet bağlama belirtiyorsa bir `algorithmSuite` varsayılan ve sizin için eşit olmayan değer üretmek Svcutil.exe, kullanarak yapılandırma dosyasını sonra doğru oluşturulmaz ve bu özniteliği ayarlamak için yapılandırma dosyasını el ile düzenlemeniz gerekir İstenen değeri.</span><span class="sxs-lookup"><span data-stu-id="641b4-121">If the service binding specifies an `algorithmSuite` value that is not equal to the default, and you generate the configuration file using Svcutil.exe, then it is not generated correctly, and you must manually edit the configuration file to set this attribute to the desired value.</span></span>|  
|`clientCredentialType`|<span data-ttu-id="641b4-122">İleti tabanlı güvenlik kullanarak istemci kimlik doğrulaması yapılırken kullanılacak kimlik bilgileri türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="641b4-122">Specifies the type of credential to be used when performing client authentication using Message-based security.</span></span> <span data-ttu-id="641b4-123">Olası değerler aşağıdaki tabloda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="641b4-123">Possible values are shown in the following table.</span></span> <span data-ttu-id="641b4-124">Varsayılan değer `UserName` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="641b4-124">The default value is `UserName`.</span></span> <span data-ttu-id="641b4-125">Bu öznitelik türünde <xref:System.ServiceModel.MessageCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="641b4-125">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="641b4-126">algorithmSuite özniteliği</span><span class="sxs-lookup"><span data-stu-id="641b4-126">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="641b4-127">Değer</span><span class="sxs-lookup"><span data-stu-id="641b4-127">Value</span></span>|<span data-ttu-id="641b4-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="641b4-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="641b4-129">Basic128</span><span class="sxs-lookup"><span data-stu-id="641b4-129">Basic128</span></span>|<span data-ttu-id="641b4-130">İleti özeti için Sha1 ve Rsa oaep mgf1p Aes128 şifreleme anahtarı kaydırma için kullanın.</span><span class="sxs-lookup"><span data-stu-id="641b4-130">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="641b4-131">Basic192</span><span class="sxs-lookup"><span data-stu-id="641b4-131">Basic192</span></span>|<span data-ttu-id="641b4-132">Aes192 şifreleme, Sha1 oaep Rsa mgf1p anahtar kaydırma için ileti özeti için kullanın.</span><span class="sxs-lookup"><span data-stu-id="641b4-132">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="641b4-133">Basic256</span><span class="sxs-lookup"><span data-stu-id="641b4-133">Basic256</span></span>|<span data-ttu-id="641b4-134">Aes256 şifreleme, Sha1 oaep Rsa mgf1p anahtar kaydırma için ileti özeti için kullanın.</span><span class="sxs-lookup"><span data-stu-id="641b4-134">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="641b4-135">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="641b4-135">Basic256Rsa15</span></span>|<span data-ttu-id="641b4-136">İleti şifreleme, ileti özeti için Sha1 ve anahtar sarma Rsa15 için Aes256 kullanın.</span><span class="sxs-lookup"><span data-stu-id="641b4-136">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="641b4-137">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="641b4-137">Basic192Rsa15</span></span>|<span data-ttu-id="641b4-138">İleti şifreleme, ileti özeti için Sha1 ve anahtar sarma Rsa15 için Aes192 kullanın.</span><span class="sxs-lookup"><span data-stu-id="641b4-138">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="641b4-139">TripleDes</span><span class="sxs-lookup"><span data-stu-id="641b4-139">TripleDes</span></span>|<span data-ttu-id="641b4-140">TripleDes şifreleme, Sha1 oaep Rsa mgf1p anahtar kaydırma için ileti özeti için kullanın.</span><span class="sxs-lookup"><span data-stu-id="641b4-140">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="641b4-141">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="641b4-141">Basic128Rsa15</span></span>|<span data-ttu-id="641b4-142">İleti şifreleme, ileti özeti için Sha1 ve anahtar sarma Rsa15 için Aes128 kullanın.</span><span class="sxs-lookup"><span data-stu-id="641b4-142">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="641b4-143">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="641b4-143">TripleDesRsa15</span></span>|<span data-ttu-id="641b4-144">TripleDes şifreleme, ileti özeti için Sha1 ve Rsa15 anahtar kaydırma için kullanın.</span><span class="sxs-lookup"><span data-stu-id="641b4-144">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="641b4-145">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="641b4-145">Basic128Sha256</span></span>|<span data-ttu-id="641b4-146">İleti şifreleme, ileti özeti için Sha256 ve oaep Rsa mgf1p anahtar kaydırma için için Aes256 kullanın.</span><span class="sxs-lookup"><span data-stu-id="641b4-146">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="641b4-147">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="641b4-147">Basic192Sha256</span></span>|<span data-ttu-id="641b4-148">İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p için Aes192 kullanın.</span><span class="sxs-lookup"><span data-stu-id="641b4-148">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="641b4-149">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="641b4-149">Basic256Sha256</span></span>|<span data-ttu-id="641b4-150">İleti şifreleme, ileti özeti için Sha256 ve oaep Rsa mgf1p anahtar kaydırma için için Aes256 kullanın.</span><span class="sxs-lookup"><span data-stu-id="641b4-150">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="641b4-151">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="641b4-151">TripleDesSha256</span></span>|<span data-ttu-id="641b4-152">TripleDes ileti şifreleme, ileti özeti için Sha256 ve oaep Rsa mgf1p anahtar kaydırma için kullanın.</span><span class="sxs-lookup"><span data-stu-id="641b4-152">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="641b4-153">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="641b4-153">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="641b4-154">İleti şifreleme, ileti özeti için Sha256 ve anahtar sarma Rsa15 için Aes128 kullanın.</span><span class="sxs-lookup"><span data-stu-id="641b4-154">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="641b4-155">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="641b4-155">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="641b4-156">İleti şifreleme, ileti özeti için Sha256 ve anahtar sarma Rsa15 için Aes192 kullanın.</span><span class="sxs-lookup"><span data-stu-id="641b4-156">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="641b4-157">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="641b4-157">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="641b4-158">İleti şifreleme, ileti özeti için Sha256 ve anahtar sarma Rsa15 için Aes256 kullanın.</span><span class="sxs-lookup"><span data-stu-id="641b4-158">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="641b4-159">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="641b4-159">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="641b4-160">TripleDes ileti şifreleme, ileti özeti için Sha256 ve Rsa15 anahtar kaydırma için kullanın.</span><span class="sxs-lookup"><span data-stu-id="641b4-160">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="641b4-161">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="641b4-161">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="641b4-162">Değer</span><span class="sxs-lookup"><span data-stu-id="641b4-162">Value</span></span>|<span data-ttu-id="641b4-163">Açıklama</span><span class="sxs-lookup"><span data-stu-id="641b4-163">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="641b4-164">Yok.</span><span class="sxs-lookup"><span data-stu-id="641b4-164">None</span></span>|<span data-ttu-id="641b4-165">Bu hizmetin anonim istemcilerle etkileşime girmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="641b4-165">This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="641b4-166">Hizmette bu hizmeti istemci kimlik gerektirmez gösterir.</span><span class="sxs-lookup"><span data-stu-id="641b4-166">On the service, this indicates that the service does not require any client credential.</span></span> <span data-ttu-id="641b4-167">İstemcide, bu istemciyi istemci kimlik sağlamaz gösterir.</span><span class="sxs-lookup"><span data-stu-id="641b4-167">On the client, this indicates that the client does not provide any client credential.</span></span>|  
|<span data-ttu-id="641b4-168">Windows</span><span class="sxs-lookup"><span data-stu-id="641b4-168">Windows</span></span>|<span data-ttu-id="641b4-169">SOAP alışverişleri Windows kimlik bilgisi kimliği doğrulanmış bağlamı altında olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="641b4-169">Allows the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span>|  
|<span data-ttu-id="641b4-170">UserName</span><span class="sxs-lookup"><span data-stu-id="641b4-170">UserName</span></span>|<span data-ttu-id="641b4-171">Hizmetinin gerektiren izin verir, istemci kimlik doğrulaması kullanıcı adı kimlik bilgilerini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="641b4-171">Allows the service to require that the client be authenticated using a UserName credential.</span></span> [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="641b4-172">bir parola Özet gönderirken ya da parola kullanarak ve böyle anahtarların ileti güvenliği için kullanarak anahtarları türetme desteklemez.</span><span class="sxs-lookup"><span data-stu-id="641b4-172"> does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="641b4-173">Bu nedenle, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] taşıma kullanıcı adı kimlik bilgileri kullanılırken güvenli zorlar.</span><span class="sxs-lookup"><span data-stu-id="641b4-173">As such, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] enforces that the transport is secured when using UserName credentials.</span></span> <span data-ttu-id="641b4-174">Bu kimlik bilgisi modu birlikte çalışabilir exchange veya temel çalışabilen olmayan bir anlaşma sonuçlanır `negotiateServiceCredential` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="641b4-174">This credential mode results in either an interoperable exchange or a non-interoperable negotiation based on the `negotiateServiceCredential` attribute.</span></span>|  
|<span data-ttu-id="641b4-175">Sertifika</span><span class="sxs-lookup"><span data-stu-id="641b4-175">Certificate</span></span>|<span data-ttu-id="641b4-176">Hizmetinin gerektiren izin verir, istemci kimlik doğrulaması kullanarak bir sertifika.</span><span class="sxs-lookup"><span data-stu-id="641b4-176">Allows the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="641b4-177">İleti güvenlik modu kullanılıyorsa ve `negotiateServiceCredential` özniteliği `false`, istemci ile hizmet sertifikası sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="641b4-177">If message security mode is used and the `negotiateServiceCredential` attribute is set to `false`, the client must be provisioned with the service certificate.</span></span>|  
|<span data-ttu-id="641b4-178">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="641b4-178">IssuedToken</span></span>|<span data-ttu-id="641b4-179">Genellikle bir güvenlik belirteci hizmeti (STS) tarafından verilen özel bir belirteç belirtir.</span><span class="sxs-lookup"><span data-stu-id="641b4-179">Specifies a custom token, usually issued by a Security Token Service (STS).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="641b4-180">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="641b4-180">Child Elements</span></span>  
 <span data-ttu-id="641b4-181">Yok.</span><span class="sxs-lookup"><span data-stu-id="641b4-181">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="641b4-182">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="641b4-182">Parent Elements</span></span>  
  
|<span data-ttu-id="641b4-183">Öğe</span><span class="sxs-lookup"><span data-stu-id="641b4-183">Element</span></span>|<span data-ttu-id="641b4-184">Açıklama</span><span class="sxs-lookup"><span data-stu-id="641b4-184">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="641b4-185">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="641b4-185">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|<span data-ttu-id="641b4-186">Güvenlik özellikleri için tanımlar <xref:System.ServiceModel.Configuration.NetTcpBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="641b4-186">Defines the security capabilities for the <xref:System.ServiceModel.Configuration.NetTcpBindingElement>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="641b4-187">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="641b4-187">Remarks</span></span>  
 <span data-ttu-id="641b4-188">İleti bütünlüğü ve gizliliği SOAP iletisi ve karşılıklı kimlik doğrulama iletişimi eş için ileti düzeyi güvenlik kullanır.</span><span class="sxs-lookup"><span data-stu-id="641b4-188">Message uses message-level security for the integrity and confidentiality of the SOAP message, and for mutual authentication of the communication peers.</span></span> <span data-ttu-id="641b4-189">Bağlamada bu güvenlik modunu seçtiyseniz, kanal yığını ile ileti güvenliği bağlama öğeleri yapılandırılır ve SOAP iletilerine uyumlu WS güvenliği sağlanan-güvenlik * standartları.</span><span class="sxs-lookup"><span data-stu-id="641b4-189">If this security mode is selected on a binding, the channel stack is configured with message security binding elements and the SOAP messages are secured in compliance with WS-Security* standards.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="641b4-190">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="641b4-190">See Also</span></span>  
 <xref:System.ServiceModel.MessageSecurityOverTcp>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.NetTcpSecurity.Message%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [<span data-ttu-id="641b4-191">Hizmetler ve istemcileri güvenli hale getirme</span><span class="sxs-lookup"><span data-stu-id="641b4-191">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="641b4-192">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="641b4-192">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="641b4-193">Sistem tarafından sağlanan bağlamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="641b4-193">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="641b4-194">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="641b4-194">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="641b4-195">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="641b4-195">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)