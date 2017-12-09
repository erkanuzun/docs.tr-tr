---
title: "Nasıl yapılır: zaman uyumsuz Windows Presentation Framework uygulama (WCF Veri Hizmetleri) oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: WCF Data Services, asynchronous operations
ms.assetid: 834614df-1427-4839-b0be-90f68e5afffd
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 52e952abc6f1b47d9caf7a5583bb591c51a70dde
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-an-asynchronous-windows-presentation-framework-application-wcf-data-services"></a><span data-ttu-id="94983-102">Nasıl yapılır: zaman uyumsuz Windows Presentation Framework uygulama (WCF Veri Hizmetleri) oluşturma</span><span class="sxs-lookup"><span data-stu-id="94983-102">How to: Create an Asynchronous Windows Presentation Framework Application (WCF Data Services)</span></span>
<span data-ttu-id="94983-103">İle [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], bir Windows Presentation Framework (WPF) uygulama kullanıcı Arabirimi öğesi için bir veri hizmetinden alınan veriler bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94983-103">With [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], you can bind data obtained from a data service to UI element of a Windows Presentation Framework (WPF) application.</span></span> <span data-ttu-id="94983-104">Daha fazla bilgi için bkz: [denetimlere veri bağlama](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md). Uygulama veri hizmet isteğine yanıt beklenirken yanıt vermeye devam sağlar zaman uyumsuz bir şekilde veri hizmeti karşı işlemleri de çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94983-104">For more information, see [Binding Data to Controls](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).You can also execute operations against the data service in an asynchronous manner, which enables the application to continue to respond while waiting for a response to a data service request.</span></span> <span data-ttu-id="94983-105">Silverlight uygulamaları, veri hizmeti zaman uyumsuz olarak erişmek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="94983-105">Applications for Silverlight are required to access the data service asynchronously.</span></span> <span data-ttu-id="94983-106">Daha fazla bilgi için bkz: [zaman uyumsuz işlemleri](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="94983-106">For more information, see [Asynchronous Operations](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="94983-107">Bu konuda, bir veri hizmeti zaman uyumsuz olarak erişmek ve sonuçları WPF uygulaması öğelerine bağlama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="94983-107">This topic shows how to access a data service asynchronously and bind the results to elements of a WPF application.</span></span> <span data-ttu-id="94983-108">Bu konuda kullanımda Northwind örnek veri hizmeti örnekleri ve otomatik olarak oluşturulur istemci veri sınıfları hizmeti.</span><span class="sxs-lookup"><span data-stu-id="94983-108">The examples in this topic use the Northwind sample data service and autogenerated client data service classes.</span></span> <span data-ttu-id="94983-109">Bu hizmet ve istemci veri sınıfları tamamladığınızda oluşturduğunuz [WCF Veri Hizmetleri quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="94983-109">This service and the client data classes are created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="94983-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="94983-110">Example</span></span>  
 <span data-ttu-id="94983-111">Aşağıdaki XAML WPF uygulaması penceresini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="94983-111">The following XAML defines the window of the WPF application.</span></span>  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingAsyncXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerordersasync.xaml#wpfdatabindingasyncxaml)]  
  
## <a name="example"></a><span data-ttu-id="94983-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="94983-112">Example</span></span>  
 <span data-ttu-id="94983-113">XAML dosyası için aşağıdaki arka plan kod sayfasını veri hizmeti kullanarak zaman uyumsuz bir sorguyu çalıştırır ve sonuçları WPF penceresi öğelerine bağlar.</span><span class="sxs-lookup"><span data-stu-id="94983-113">The following code-behind page for the XAML file executes an asynchronous query by using the data service and binds the results to elements in the WPF window.</span></span>  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerordersasync.xaml.cs#wpfdatabindingasync)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerordersasync.xaml.vb#wpfdatabindingasync)]  
  
## <a name="see-also"></a><span data-ttu-id="94983-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="94983-114">See Also</span></span>  
 [<span data-ttu-id="94983-115">WCF Veri Hizmetleri İstemci Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="94983-115">WCF Data Services Client Library</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)