---
title: "Meta Veri Sistemini Genişletme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: extending metadata [WCF]
ms.assetid: 8c6b3b00-61b8-4589-8fa5-546cc33719bf
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d0c729850e25e9fe4bec37dc366053de8c56f210
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="extending-the-metadata-system"></a><span data-ttu-id="dec33-102">Meta Veri Sistemini Genişletme</span><span class="sxs-lookup"><span data-stu-id="dec33-102">Extending the Metadata System</span></span>
<span data-ttu-id="dec33-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Meta veri sistemi grubudur sınıflar ve arabirimler hizmet tabanlı uygulamalar uygulamak için gereken meta verileri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="dec33-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] metadata system is a group of classes and interfaces that represent metadata required to implement service-based applications.</span></span> <span data-ttu-id="dec33-104">Değiştirin veya sınıflarını genişletmek veya uygulama ve Web Hizmetleri Açıklama Dili (WSDL) uzantıları veya özel WS-PolicyAttachments onaylar gibi özel meta verileri içeri ve dışarı aktarmak arabirimleri yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="dec33-104">Modify or extend the classes or implement and configure the interfaces to export and import custom metadata such as Web Services Description Language (WSDL) extensions or custom WS-PolicyAttachments assertions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dec33-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="dec33-105">In This Section</span></span>  
 [<span data-ttu-id="dec33-106">WCF uzantısı için özel meta verileri dışarı aktarma</span><span class="sxs-lookup"><span data-stu-id="dec33-106">Exporting Custom Metadata for a WCF Extension</span></span>](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md)  
 <span data-ttu-id="dec33-107">Uygulama ve nasıl kullanılacağını açıklar <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> özel ilke onaylamalarını WSDL belgelere katıştırma arabirimi.</span><span class="sxs-lookup"><span data-stu-id="dec33-107">Describes how to implement and use the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface to embed custom policy assertions in WSDL documents.</span></span>  
  
 [<span data-ttu-id="dec33-108">WCF uzantısı için özel meta verileri alma</span><span class="sxs-lookup"><span data-stu-id="dec33-108">Importing Custom Metadata for a WCF Extension</span></span>](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)  
 <span data-ttu-id="dec33-109">Uygulama ve nasıl kullanılacağını açıklar <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> okumak ve özel ilke onaylamalarını WSDL belgelerde yanıt vermesi için arabirim.</span><span class="sxs-lookup"><span data-stu-id="dec33-109">Describes how to implement and use the <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interface to read and respond to custom policy assertions in WSDL documents.</span></span>  
  
 [<span data-ttu-id="dec33-110">Yayımlama ve özel bağlama üzerinden meta verileri alma</span><span class="sxs-lookup"><span data-stu-id="dec33-110">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 <span data-ttu-id="dec33-111">Özel bağlama meta veri değişimi açıklar.</span><span class="sxs-lookup"><span data-stu-id="dec33-111">Describes how to exchange metadata over custom bindings.</span></span>