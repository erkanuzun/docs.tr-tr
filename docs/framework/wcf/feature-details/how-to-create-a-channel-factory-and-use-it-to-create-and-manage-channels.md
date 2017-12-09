---
title: "Nasıl yapılır: Kanal Fabrikası Oluşturma ve Bunu Kanal Oluşturmak ve Yönetmek için Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 018dcc30-9f61-419e-af8e-412a85e8d282
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2fb471a0d91c350bf5df320b8f2ea3b32e74d9ab
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels"></a><span data-ttu-id="f7126-102">Nasıl yapılır: Kanal Fabrikası Oluşturma ve Bunu Kanal Oluşturmak ve Yönetmek için Kullanma</span><span class="sxs-lookup"><span data-stu-id="f7126-102">How to: Create a Channel Factory and Use it to Create and Manage Channels</span></span>
<span data-ttu-id="f7126-103"><xref:System.ServiceModel.DuplexChannelFactory%601> Sınıfı oluşturmak ve istemcilerin ve hizmet uç noktalarına gelen ileti gönderme ve alma için kullandıkları farklı türlerde çift yönlü kanalları yönetmek için araçlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="f7126-103">The <xref:System.ServiceModel.DuplexChannelFactory%601> class provides the means to create and manage duplex channels of different types that clients use to send and receive messages to and from service endpoints.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7126-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f7126-104">Example</span></span>  
 <span data-ttu-id="f7126-105">Aşağıdaki kod, bir kanal fabrikası oluşturma ve oluşturup kanalları yönetmek için kullanma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f7126-105">The following code shows how to create a channel factory and use it to create and manage channels.</span></span>  
  
 [!code-csharp[S_CustomAuthentication#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_customauthentication/cs/instance.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f7126-106">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f7126-106">See Also</span></span>  
 <xref:System.ServiceModel.DuplexChannelFactory%601>