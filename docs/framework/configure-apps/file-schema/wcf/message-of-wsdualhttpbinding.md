---
title: '&lt;wsDualHttpBinding&gt; &lt;iletisi&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75101744-eed8-4d61-91f4-5fc4473a21f2
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f83edc08702bc6d4be674dbe94e3e841669fa207
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltmessagegt-of-ltwsdualhttpbindinggt"></a><span data-ttu-id="cfa1a-102">&lt;wsDualHttpBinding&gt; &lt;iletisi&gt;</span><span class="sxs-lookup"><span data-stu-id="cfa1a-102">&lt;message&gt; of &lt;wsDualHttpBinding&gt;</span></span>
<span data-ttu-id="cfa1a-103">İleti düzeyi güvenlik için tanımlar [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="cfa1a-103">Defines message-level security for the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>  
  
 <span data-ttu-id="cfa1a-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="cfa1a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cfa1a-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="cfa1a-105">\<bindings></span></span>  
<span data-ttu-id="cfa1a-106">\<wsDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="cfa1a-106">\<wsDualHttpBinding></span></span>  
<span data-ttu-id="cfa1a-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="cfa1a-107">\<binding></span></span>  
<span data-ttu-id="cfa1a-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="cfa1a-108">\<security></span></span>  
<span data-ttu-id="cfa1a-109">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="cfa1a-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfa1a-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cfa1a-110">Syntax</span></span>  
  
```xml  
<message   
      clientCredentialType="None/Windows/UserName/Certificate/CardSpace"  
     negotiateServiceCredential="Boolean"  
   algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"/>  
</message>  
```  
  
## <a name="type"></a><span data-ttu-id="cfa1a-111">Tür</span><span class="sxs-lookup"><span data-stu-id="cfa1a-111">Type</span></span>  
 <xref:System.ServiceModel.MessageSecurityOverHttp>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cfa1a-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cfa1a-112">Attributes and Elements</span></span>  
 <span data-ttu-id="cfa1a-113">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="cfa1a-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cfa1a-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cfa1a-114">Attributes</span></span>  
  
|<span data-ttu-id="cfa1a-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="cfa1a-115">Attribute</span></span>|<span data-ttu-id="cfa1a-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cfa1a-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cfa1a-117">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="cfa1a-117">algorithmSuite</span></span>|<span data-ttu-id="cfa1a-118">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-118">Optional.</span></span> <span data-ttu-id="cfa1a-119">İleti şifreleme ve anahtar-wrap algoritmaları ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-119">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="cfa1a-120">Algoritmaları ve anahtar boyutları tarafından belirlenen <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-120">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="cfa1a-121">Bu algoritmalar, güvenlik ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen eşlenir.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-121">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="cfa1a-122">Aşağıda için olası değerler konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-122">See below for possible values.</span></span> <span data-ttu-id="cfa1a-123">Varsayılan değer `Basic256` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-123">The default value is `Basic256`.</span></span>|  
|<span data-ttu-id="cfa1a-124">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="cfa1a-124">clientCredentialType</span></span>|<span data-ttu-id="cfa1a-125">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-125">Optional.</span></span> <span data-ttu-id="cfa1a-126">Güvenlik modu kullanılarak gerçekleştirme istemci kimlik doğrulaması olduğunda kullanılacak kimlik bilgileri türünü belirtir `Message`.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-126">Specifies the type of credential to be used when performing client authentication using the security mode is `Message`.</span></span> <span data-ttu-id="cfa1a-127">Aşağıda için olası değerler konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-127">See below for possible values.</span></span> <span data-ttu-id="cfa1a-128">Varsayılan, `Windows` değeridir.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-128">The default is `Windows`.</span></span><br /><br /> <span data-ttu-id="cfa1a-129">Bu öznitelik türünde <xref:System.ServiceModel.MessageCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-129">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|  
|<span data-ttu-id="cfa1a-130">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="cfa1a-130">negotiateServiceCredential</span></span>|<span data-ttu-id="cfa1a-131">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-131">Optional.</span></span> <span data-ttu-id="cfa1a-132">Hizmet kimlik bilgilerini bant dışı istemcide sağlanan veya anlaşma işlemi aracılığıyla istemcisine hizmetinden alınan belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-132">A Boolean value that specifies whether the service credential is provisioned at the client out of band or is obtained from the service to the client through a process of negotiation.</span></span> <span data-ttu-id="cfa1a-133">Bu tür bir anlaşma precursor normal ileti Exchange'e ' dir.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-133">Such a negotiation is a precursor to the usual message exchange.</span></span><br /><br /> <span data-ttu-id="cfa1a-134">Varsa `clientCredentialType` özniteliği eşittir None, kullanıcı adı veya sertifika, bu öznitelik ayarını `false` hizmet sertifikası bant dışı istemcide kullanılabilir olduğunu ve istemci hizmet sertifikasını belirtmek için ihtiyaç duyduğu gelir (kullanma [ \<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) içinde [ \<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-134">If the `clientCredentialType` attribute equals to None, Username, or Certificate, setting this attribute to `false` implies that the service certificate is available at the client out of band and that the client needs to specify the service certificate (using the [\<serviceCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) in the [\<serviceCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) service behavior.</span></span> <span data-ttu-id="cfa1a-135">Bu mod, WS-Trust ve WS-SecureConversation uygulayan SOAP yığınları ile birlikte çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-135">This mode is interoperable with SOAP stacks which implement WS-Trust and WS-SecureConversation.</span></span><br /><br /> <span data-ttu-id="cfa1a-136">Varsa `ClientCredentialType` özniteliği `Windows`, bu öznitelik ayarını `false` Kerberos kimlik doğrulaması tabanlı belirtir.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-136">If the `ClientCredentialType` attribute is set to `Windows`, setting this attribute to `false` specifies Kerberos based authentication.</span></span> <span data-ttu-id="cfa1a-137">Bu, istemci ve hizmet aynı Kerberos etki alanının parçası olması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-137">This means that the client and service must be part of the same Kerberos domain.</span></span> <span data-ttu-id="cfa1a-138">Bu mod uygulayan Kerberos belirteci profil (OASIS WSS TC tanımlandığı gibi) WS-Trust ve WS-SecureConversation yanı sıra SOAP yığınları birlikte çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-138">This mode is interoperable with SOAP stacks which implement the Kerberos token profile (as defined at OASIS WSS TC) as well as WS-Trust and WS-SecureConversation.</span></span> <span data-ttu-id="cfa1a-139">Bu öznitelik olduğunda `true`, SOAP iletileri üzerinden SPNego exchange tünelleri .NET SOAP anlaşması neden olur.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-139">When this attribute is `true`, it causes a .NET SOAP negotiation that tunnels SPNego exchange over SOAP messages.</span></span><br /><br /> <span data-ttu-id="cfa1a-140">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-140">The default is `true`.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="cfa1a-141">algorithmSuite özniteliği</span><span class="sxs-lookup"><span data-stu-id="cfa1a-141">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="cfa1a-142">Değer</span><span class="sxs-lookup"><span data-stu-id="cfa1a-142">Value</span></span>|<span data-ttu-id="cfa1a-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cfa1a-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cfa1a-144">Basic128</span><span class="sxs-lookup"><span data-stu-id="cfa1a-144">Basic128</span></span>|<span data-ttu-id="cfa1a-145">İleti özeti için Sha1 ve Rsa oaep mgf1p Aes128 şifreleme anahtarı kaydırma için kullanın.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-145">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="cfa1a-146">Basic192</span><span class="sxs-lookup"><span data-stu-id="cfa1a-146">Basic192</span></span>|<span data-ttu-id="cfa1a-147">Aes192 şifreleme, Sha1 oaep Rsa mgf1p anahtar kaydırma için ileti özeti için kullanın.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-147">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="cfa1a-148">Basic256</span><span class="sxs-lookup"><span data-stu-id="cfa1a-148">Basic256</span></span>|<span data-ttu-id="cfa1a-149">Aes256 şifreleme, Sha1 oaep Rsa mgf1p anahtar kaydırma için ileti özeti için kullanın.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-149">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="cfa1a-150">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="cfa1a-150">Basic256Rsa15</span></span>|<span data-ttu-id="cfa1a-151">İleti şifreleme, ileti özeti için Sha1 ve anahtar sarma Rsa15 için Aes256 kullanın.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-151">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="cfa1a-152">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="cfa1a-152">Basic192Rsa15</span></span>|<span data-ttu-id="cfa1a-153">İleti şifreleme, ileti özeti için Sha1 ve anahtar sarma Rsa15 için Aes192 kullanın.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-153">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="cfa1a-154">TripleDes</span><span class="sxs-lookup"><span data-stu-id="cfa1a-154">TripleDes</span></span>|<span data-ttu-id="cfa1a-155">TripleDes şifreleme kullanmak, Sha1 ileti özeti için oaep Rsa mgf1p anahtar kaydırma için.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-155">Use TripleDes encryption, , Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="cfa1a-156">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="cfa1a-156">Basic128Rsa15</span></span>|<span data-ttu-id="cfa1a-157">İleti şifreleme, ileti özeti için Sha1 ve anahtar sarma Rsa15 için Aes128 kullanın.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-157">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="cfa1a-158">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="cfa1a-158">TripleDesRsa15</span></span>|<span data-ttu-id="cfa1a-159">TripleDes şifreleme, ileti özeti için Sha1 ve Rsa15 anahtar kaydırma için kullanın.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-159">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="cfa1a-160">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="cfa1a-160">Basic128Sha256</span></span>|<span data-ttu-id="cfa1a-161">İleti şifreleme, ileti özeti için Sha256 ve oaep Rsa mgf1p anahtar kaydırma için için Aes256 kullanın.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-161">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="cfa1a-162">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="cfa1a-162">Basic192Sha256</span></span>|<span data-ttu-id="cfa1a-163">İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p için Aes192 kullanın.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-163">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="cfa1a-164">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="cfa1a-164">Basic256Sha256</span></span>|<span data-ttu-id="cfa1a-165">İleti şifreleme, ileti özeti için Sha256 ve oaep Rsa mgf1p anahtar kaydırma için için Aes256 kullanın.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-165">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="cfa1a-166">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="cfa1a-166">TripleDesSha256</span></span>|<span data-ttu-id="cfa1a-167">TripleDes ileti şifreleme, ileti özeti için Sha256 ve oaep Rsa mgf1p anahtar kaydırma için kullanın.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-167">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="cfa1a-168">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="cfa1a-168">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="cfa1a-169">İleti şifreleme, ileti özeti için Sha256 ve anahtar sarma Rsa15 için Aes128 kullanın.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-169">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="cfa1a-170">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="cfa1a-170">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="cfa1a-171">İleti şifreleme, ileti özeti için Sha256 ve anahtar sarma Rsa15 için Aes192 kullanın.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-171">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="cfa1a-172">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="cfa1a-172">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="cfa1a-173">İleti şifreleme, ileti özeti için Sha256 ve anahtar sarma Rsa15 için Aes256 kullanın.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-173">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="cfa1a-174">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="cfa1a-174">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="cfa1a-175">TripleDes ileti şifreleme, ileti özeti için Sha256 ve Rsa15 anahtar kaydırma için kullanın.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-175">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="cfa1a-176">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="cfa1a-176">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="cfa1a-177">Değer</span><span class="sxs-lookup"><span data-stu-id="cfa1a-177">Value</span></span>|<span data-ttu-id="cfa1a-178">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cfa1a-178">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cfa1a-179">Yok.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-179">None</span></span>|<span data-ttu-id="cfa1a-180">Bu hizmetin anonim istemcilerle etkileşime girmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-180">This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="cfa1a-181">Hizmet tarafında bu hizmeti istemci kimlik gerektirmez gösterir.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-181">On the service side, this indicates that the service does not require any client credential.</span></span> <span data-ttu-id="cfa1a-182">İstemcide, bu istemciyi istemci kimlik sağlamaz gösterir.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-182">On the client, this indicates that the client does not provide any client credential.</span></span>|  
|<span data-ttu-id="cfa1a-183">Windows</span><span class="sxs-lookup"><span data-stu-id="cfa1a-183">Windows</span></span>|<span data-ttu-id="cfa1a-184">SOAP alışverişleri Windows kimlik bilgisi kimliği doğrulanmış bağlamı altında olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-184">Allows the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="cfa1a-185">Varsa `negotiateServiceCredential` özniteliği `true`, bu bir SSPI anlaşması veya Kerberos (birlikte çalışabilen standart) ya da gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-185">If the `negotiateServiceCredential` attribute is set to `true`, this either performs an SSPI Negotiation or Kerberos (an interoperable standard).</span></span>|  
|<span data-ttu-id="cfa1a-186">UserName</span><span class="sxs-lookup"><span data-stu-id="cfa1a-186">UserName</span></span>|<span data-ttu-id="cfa1a-187">Hizmetinin gerektiren izin verir, istemci kimlik doğrulaması kullanıcı adı kimlik bilgilerini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-187">Allows the service to require that the client be authenticated using a UserName credential.</span></span> [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="cfa1a-188">bir parola Özet gönderirken ya da parola kullanarak ve böyle anahtarların ileti güvenliği için kullanarak anahtarları türetme desteklemez.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-188"> does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="cfa1a-189">Bu nedenle, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] taşıma kullanıcı adı kimlik bilgileri kullanılırken güvenli zorlar.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-189">As such, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] enforces that the transport is secured when using UserName credentials.</span></span> <span data-ttu-id="cfa1a-190">Bu kimlik bilgisi modu birlikte çalışabilir exchange veya temel çalışabilen olmayan bir anlaşma sonuçlanır `negotiateServiceCredential` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-190">This credential mode results in either an interoperable exchange or a non-interoperable negotiation based on the `negotiateServiceCredential` attribute.</span></span>|  
|<span data-ttu-id="cfa1a-191">Sertifika</span><span class="sxs-lookup"><span data-stu-id="cfa1a-191">Certificate</span></span>|<span data-ttu-id="cfa1a-192">Hizmetinin gerektiren izin verir, istemci kimlik doğrulaması kullanarak bir sertifika.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-192">Allows the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="cfa1a-193">İleti güvenlik modu kullanılıyorsa ve `negotiateServiceCredential` özniteliği `false`, istemci ile hizmet sertifikası hazırlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-193">If message security mode is used and the `negotiateServiceCredential` attribute is set to `false`, the client needs to be provisioned with the service certificate.</span></span>|  
|<span data-ttu-id="cfa1a-194">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="cfa1a-194">IssuedToken</span></span>|<span data-ttu-id="cfa1a-195">Genellikle bir güvenlik belirteci hizmeti tarafından verilen özel bir belirteç belirtir.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-195">Specifies a custom token, usually issued by a Security Token Service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cfa1a-196">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cfa1a-196">Child Elements</span></span>  
 <span data-ttu-id="cfa1a-197">Yok.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-197">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cfa1a-198">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cfa1a-198">Parent Elements</span></span>  
  
|<span data-ttu-id="cfa1a-199">Öğe</span><span class="sxs-lookup"><span data-stu-id="cfa1a-199">Element</span></span>|<span data-ttu-id="cfa1a-200">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cfa1a-200">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cfa1a-201">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="cfa1a-201">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsdualhttpbinding.md)|<span data-ttu-id="cfa1a-202">Güvenlik özelliklerini tanımlayan [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="cfa1a-202">Defines the security capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cfa1a-203">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cfa1a-203">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSDualHttpSecurity.Message%2A>  
 <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>  
 <xref:System.ServiceModel.MessageSecurityOverHttp>  
 [<span data-ttu-id="cfa1a-204">Hizmetler ve istemcileri güvenli hale getirme</span><span class="sxs-lookup"><span data-stu-id="cfa1a-204">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="cfa1a-205">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="cfa1a-205">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="cfa1a-206">Sistem tarafından sağlanan bağlamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="cfa1a-206">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="cfa1a-207">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="cfa1a-207">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="cfa1a-208">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="cfa1a-208">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)