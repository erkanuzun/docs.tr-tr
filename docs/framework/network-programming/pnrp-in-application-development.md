---
title: "PNRP uygulama geliştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 752b354df897fa37bc45c1bbd1969cf93aac87ed
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="pnrp-in-application-development"></a><span data-ttu-id="e338a-102">PNRP uygulama geliştirme</span><span class="sxs-lookup"><span data-stu-id="e338a-102">PNRP in Application Development</span></span>
<span data-ttu-id="e338a-103">Windows Vista'da ağ uygulamaları ad yayını ve çözümleme işlevleri bir Basitleştirilmiş PNRP uygulama programlama arabirimi (API) erişebilir.</span><span class="sxs-lookup"><span data-stu-id="e338a-103">In Windows Vista, networking applications can access name publication and resolution functions through a simplified PNRP application programming interface (API).</span></span>  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a><span data-ttu-id="e338a-104">Eş Adı Çözümleme Protokolü'nü uygulama</span><span class="sxs-lookup"><span data-stu-id="e338a-104">Implementing the Peer Name Resolution Protocol</span></span>  
 <span data-ttu-id="e338a-105">Basitleştirilmiş PNRP API ile bulut açıkça adı ve adreslerini kaydetmek için belirtilmeyen; PNRP bileşen otomatik olarak uygun bulut birleştirme ve Bulutlar içinde yayımlamak için adresleri belirler.</span><span class="sxs-lookup"><span data-stu-id="e338a-105">With the simplified PNRP API, clouds are not explicitly specified to register the name and addresses; the PNRP component automatically determines the appropriate clouds to join and the addresses to publish within the clouds.</span></span>  
  
 <span data-ttu-id="e338a-106">Yüksek oranda Basitleştirilmiş PNRP ad çözümlemesi için Windows Vista'da, PNRP adlarını artık Windows yuvaları işlevi getaddrinfo() tümleşiktir.</span><span class="sxs-lookup"><span data-stu-id="e338a-106">For highly simplified PNRP name resolution in Windows Vista, PNRP names are now integrated into the getaddrinfo() Windows Sockets function.</span></span> <span data-ttu-id="e338a-107">Bir IPv6 adresi için bir adı çözümlemek için PNRP kullanmak için uygulamaları getaddrinfo() işlevi tam etki alanı adı (FQDN) name.prnp.net çözmek için kullanabilir hangi adının çözümlendiği eş adıdır.</span><span class="sxs-lookup"><span data-stu-id="e338a-107">To use PNRP to resolve a name to an IPv6 address, applications can use the getaddrinfo() function to resolve the Fully Qualified Domain Name (FQDN) name.prnp.net, in which name is peer name being resolved.</span></span> <span data-ttu-id="e338a-108">Windows Vista'da ayrılmış olarak etki alanı PNRP ad çözümlemesi için pnrp.net etki alanıdır.</span><span class="sxs-lookup"><span data-stu-id="e338a-108">The pnrp.net domain is a reserved domain in Windows Vista for PNRP name resolution.</span></span>  
  
 <span data-ttu-id="e338a-109">İleti PeerToPeer uygulamalar arasında geçirme PeerChannel'a ve WCF gibi temel mimarileri tarafından işlenen hala [büyük veriler ve akış](http://go.microsoft.com/fwlink/?LinkID=179652).</span><span class="sxs-lookup"><span data-stu-id="e338a-109">Message passing between PeerToPeer applications is still handled by underlying architectures such as PeerChannel and WCF [Large Data and Streaming](http://go.microsoft.com/fwlink/?LinkID=179652).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e338a-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e338a-110">See Also</span></span>  
 <xref:System.Net.PeerToPeer>