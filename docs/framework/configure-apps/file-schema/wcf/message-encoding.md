---
title: "İleti Kodlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f30ee941-aca9-4c67-82a5-421568496f07
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8b0147049a988a8fa2d0721da39f1d9c37278803
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="message-encoding"></a><span data-ttu-id="88f0a-102">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="88f0a-102">Message Encoding</span></span>
<span data-ttu-id="88f0a-103">Kodlama Unicode karakter kümesini bir bayt dizisi dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="88f0a-103">Encoding is the process of transforming a set of Unicode characters into a sequence of bytes.</span></span> <span data-ttu-id="88f0a-104">Kod çözme ters bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="88f0a-104">Decoding is the reverse process.</span></span> <span data-ttu-id="88f0a-105">Windows Communication Foundation (WCF) SOAP iletiler için kodlamayı üç türleri içerir: metin ve ikili ileti iletim en iyi duruma getirme mekanizmasını (MTOM).</span><span class="sxs-lookup"><span data-stu-id="88f0a-105">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="88f0a-106">`binaryMessageEncoding` Yapılandırma bölümü ikili tabanlı XML iletileri için kullanılan karakter kodlama ve ileti sürüm belirtir.</span><span class="sxs-lookup"><span data-stu-id="88f0a-106">The `binaryMessageEncoding` configuration section specifies the character encoding and message versioning used for binary-based XML messages.</span></span> <span data-ttu-id="88f0a-107">İkili ileti Kodlayıcı ikili hat üzerinde Windows Communication Foundation (WCF) iletilerinde kodlar.</span><span class="sxs-lookup"><span data-stu-id="88f0a-107">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="88f0a-108">Bu kodlama ileti çok hızlı aktarımını sonuçları, birlikte çalışabilirlik tabanlı WS - üzerinde * standartları kaybolur.</span><span class="sxs-lookup"><span data-stu-id="88f0a-108">While this encoding results in very fast transmission of messages, interoperability based on the WS-* standards is lost.</span></span>  
  
 <span data-ttu-id="88f0a-109">`mtomMessageEncoding` Yapılandırma bölümünde bir ileti iletim en iyi duruma getirme mekanizmasını (MTOM) kodlama kullanılarak bir ileti için kullanılan karakter kodlama ve ileti sürüm belirtir.</span><span class="sxs-lookup"><span data-stu-id="88f0a-109">The `mtomMessageEncoding` configuration section specifies the character encoding and message versioning used for a message using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="88f0a-110">(MTOM), Windows Communication Foundation (WCF) iletilerindeki ikili veri iletmek için verimli bir teknolojidir.</span><span class="sxs-lookup"><span data-stu-id="88f0a-110">(MTOM) is an efficient technology for transmitting binary data in Windows Communication Foundation (WCF) messages.</span></span> <span data-ttu-id="88f0a-111">MTOM Kodlayıcısı verimliliği ve birlikte çalışabilirlik arasında bir denge dener.</span><span class="sxs-lookup"><span data-stu-id="88f0a-111">The MTOM encoder attempts to strike a balance between efficiency and interoperability.</span></span> <span data-ttu-id="88f0a-112">MTOM kodlama çoğu XML metin biçiminde aktarır ancak bunları olarak ileterek büyük ikili veri blokları en iyi duruma getirir-metne dönüştürme olmadan, ise.</span><span class="sxs-lookup"><span data-stu-id="88f0a-112">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to text.</span></span>  
  
 <span data-ttu-id="88f0a-113">`textMessageEncoding` Yapılandırma bölümü kablo metin tabanlı iletileri oluşturmak için kullanılan bir metin Kodlayıcı belirtir.</span><span class="sxs-lookup"><span data-stu-id="88f0a-113">The `textMessageEncoding` configuration section specifies a text encoder used to create text-based messages on the wire.</span></span> <span data-ttu-id="88f0a-114">Bu Kodlayıcı tarafından üretilen iletileri WS - için uygun * birlikte çalışabilirliği tabanlı.</span><span class="sxs-lookup"><span data-stu-id="88f0a-114">Messages produced by this encoder are suitable for WS-* based interop.</span></span> <span data-ttu-id="88f0a-115">Genellikle Web hizmeti veya Web hizmeti istemcisi metinsel XML anlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88f0a-115">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="88f0a-116">Ancak, büyük metin olarak ikili veri blokları iletmek için XML iletileri kodlama az verimli yöntemdir</span><span class="sxs-lookup"><span data-stu-id="88f0a-116">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88f0a-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="88f0a-117">See Also</span></span>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 [<span data-ttu-id="88f0a-118">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="88f0a-118">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="88f0a-119">Bağlamaları genişletme</span><span class="sxs-lookup"><span data-stu-id="88f0a-119">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="88f0a-120">Özel bağlamalar</span><span class="sxs-lookup"><span data-stu-id="88f0a-120">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="88f0a-121">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="88f0a-121">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="88f0a-122">İleti Kodlayıcı seçme</span><span class="sxs-lookup"><span data-stu-id="88f0a-122">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)