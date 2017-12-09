---
title: "Nasıl yapılır: bir veri hizmeti başvurusu (WCF Veri Hizmetleri) Ekle"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 702eda2d4641dc2efdac40f9d730228063e306a8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a><span data-ttu-id="b9fc2-102">Nasıl yapılır: bir veri hizmeti başvurusu (WCF Veri Hizmetleri) Ekle</span><span class="sxs-lookup"><span data-stu-id="b9fc2-102">How to: Add a Data Service Reference (WCF Data Services)</span></span>
<span data-ttu-id="b9fc2-103">Kullanabileceğiniz **hizmet Başvurusu Ekle** iletişim için bir başvuru eklemek için Visual Studio'da [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b9fc2-103">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span></span> <span data-ttu-id="b9fc2-104">Bu, Visual Studio geliştirme istemci uygulamasında veri hizmeti daha kolay erişmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b9fc2-104">This enables you to more easily access a data service in a client application that you develop in Visual Studio.</span></span> <span data-ttu-id="b9fc2-105">Bu yordamı tamamladıktan sonra veri sınıfları veri hizmetinden alınan meta veri göre oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b9fc2-105">When you complete this procedure, data classes are generated based on metadata that is obtained from the data service.</span></span> <span data-ttu-id="b9fc2-106">Daha fazla bilgi için bkz: [veri hizmeti istemci kitaplığı oluşturma](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="b9fc2-106">For more information, see [Generating the Data Service Client Library](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).</span></span>  
  
### <a name="to-add-a-data-service-reference"></a><span data-ttu-id="b9fc2-107">Veri hizmeti başvurusu eklemek için</span><span class="sxs-lookup"><span data-stu-id="b9fc2-107">To add a data service reference</span></span>  
  
1.  <span data-ttu-id="b9fc2-108">(İsteğe bağlı) Veri Hizmeti çözümün bir parçası değil ve çalışır durumda değil, veri hizmeti başlatın ve veri hizmeti URI'sini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b9fc2-108">(Optional) If the data service is not part of the solution and is not already running, start the data service and note the URI of the data service.</span></span>  
  
2.  <span data-ttu-id="b9fc2-109">İstemci projesine sağ tıklayın ve ardından **hizmet Başvurusu Ekle**.</span><span class="sxs-lookup"><span data-stu-id="b9fc2-109">Right-click the client project and then select **Add Service Reference**.</span></span>  
  
3.  <span data-ttu-id="b9fc2-110">Veri Hizmeti geçerli çözümün bir parçası ise, tıklatın **bulma**.</span><span class="sxs-lookup"><span data-stu-id="b9fc2-110">If the data service is part of the current solution, click **Discover**.</span></span>  
  
     <span data-ttu-id="b9fc2-111">veya</span><span class="sxs-lookup"><span data-stu-id="b9fc2-111">-or-</span></span>  
  
     <span data-ttu-id="b9fc2-112">İçinde **adresi** metin kutusuna, veri hizmeti temel URL'sini yazın gibi `http://localhost:1234/Northwind.svc`ve ardından **Git**.</span><span class="sxs-lookup"><span data-stu-id="b9fc2-112">In the **Address** text box, type the base URL of the data service, such as `http://localhost:1234/Northwind.svc`, and then click **Go**.</span></span>  
  
4.  <span data-ttu-id="b9fc2-113">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="b9fc2-113">Click **OK**.</span></span>  
  
     <span data-ttu-id="b9fc2-114">Bu, erişim ve nesneler olarak veri hizmeti kaynakları ile etkileşim kurmak için kullanılan veri sınıfları içeren yeni bir kod dosyası ekler.</span><span class="sxs-lookup"><span data-stu-id="b9fc2-114">This adds a new code file that contains the data classes that are used to access and interact with data service resources as objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9fc2-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b9fc2-115">See Also</span></span>  
 [<span data-ttu-id="b9fc2-116">Hızlı Başlangıç</span><span class="sxs-lookup"><span data-stu-id="b9fc2-116">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)