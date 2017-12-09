---
title: "Nasıl yapılır: Özel İlke Onaylamalarını Dışa Aktarma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 99030386-43b0-4f7b-866d-17ea307f5cbd
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1cfce32a7e7099a601c76874c8ca951488335fc6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-export-custom-policy-assertions"></a><span data-ttu-id="cbf1b-102">Nasıl yapılır: Özel İlke Onaylamalarını Dışa Aktarma</span><span class="sxs-lookup"><span data-stu-id="cbf1b-102">How to: Export Custom Policy Assertions</span></span>
<span data-ttu-id="cbf1b-103">İlke onaylamalarını hizmet uç noktası gereksinimlerini ve özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="cbf1b-103">Policy assertions describe the capabilities and requirements of a service endpoint.</span></span> <span data-ttu-id="cbf1b-104">Hizmet uygulamaları özel ilke onaylamalarını hizmeti meta verilerde bitiş noktası, iletişim kurmak için kullanabileceğiniz istemci uygulamasına bağlama veya sözleşme özelleştirme bilgileri.</span><span class="sxs-lookup"><span data-stu-id="cbf1b-104">Service applications can use custom policy assertions in service metadata to communicate endpoint, binding or contract customization information to the client application.</span></span> <span data-ttu-id="cbf1b-105">Kullanabileceğiniz [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] WSDL bağlamalarda uç noktası, işlem veya özelliklerini veya gereksinimleri iletişim bağlı olarak, ileti konuları iliştirilmiş ilke ifadelerde onaylar vermek için.</span><span class="sxs-lookup"><span data-stu-id="cbf1b-105">You can use [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to export assertions in policy expressions attached in WSDL bindings at the endpoint, operation, or message subjects, depending upon the capabilities or requirements you are communicating.</span></span>  
  
 <span data-ttu-id="cbf1b-106">Özel ilke onaylamalarını dışa aktarılır uygulayarak <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> üzerinde arabirim bir <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> ve hizmet uç noktası ya da bağlama öğesi uygulamanızda kaydetme bağlama doğrudan ya da bağlama öğesi ekleniyor yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="cbf1b-106">Custom policy assertions are exported by implementing the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface on a <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> and either inserting the binding element directly into the binding of the service endpoint or by registering the binding element in your application configuration file.</span></span> <span data-ttu-id="cbf1b-107">İlke verme uygulamanıza özel ilke değerinizi olarak eklemelisiniz bir <xref:System.Xml.XmlElement?displayProperty=nameWithType> uygun örneğine <xref:System.ServiceModel.Description.PolicyAssertionCollection?displayProperty=nameWithType> üzerinde <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> içine geçirilen <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cbf1b-107">Your policy export implementation should add your custom policy assertion as a <xref:System.Xml.XmlElement?displayProperty=nameWithType> instance to the appropriate <xref:System.ServiceModel.Description.PolicyAssertionCollection?displayProperty=nameWithType> on the <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> passed into the <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> method.</span></span>  
  
 <span data-ttu-id="cbf1b-108">Buna ek olarak işaretlemeniz gerekir <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> özelliği <xref:System.ServiceModel.Description.WsdlExporter> sınıfı ve iç içe geçmiş ilke ifadeleri ve ilke framework öznitelikleri doğru ad alanında belirtilen ilke sürümlerine göre dışarı aktarma.</span><span class="sxs-lookup"><span data-stu-id="cbf1b-108">In addition you must check the <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property of the <xref:System.ServiceModel.Description.WsdlExporter> class and export nested policy expressions and policy framework attributes in the correct namespace based on the policy version specified.</span></span>  
  
 <span data-ttu-id="cbf1b-109">Özel ilke onaylamalarını içe aktarmak için bkz: <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> ve [nasıl yapılır: özel ilke onaylamalarını içe](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md).</span><span class="sxs-lookup"><span data-stu-id="cbf1b-109">To import custom policy assertions, see <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> and [How to: Import Custom Policy Assertions](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md).</span></span>  
  
### <a name="to-export-custom-policy-assertions"></a><span data-ttu-id="cbf1b-110">Özel ilke onaylamalarını dışa aktarmak için</span><span class="sxs-lookup"><span data-stu-id="cbf1b-110">To export custom policy assertions</span></span>  
  
1.  <span data-ttu-id="cbf1b-111">Uygulama <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> üzerinde arabirim bir <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cbf1b-111">Implement the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface on a <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>.</span></span> <span data-ttu-id="cbf1b-112">Aşağıdaki kod örneğinde bir özel ilke onaylama bağlama düzeyinde uyarlamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cbf1b-112">The following code example shows the implementation of a custom policy assertion at the binding level.</span></span>  
  
     [!code-csharp[CustomPolicySample#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyexporter.cs#14)]
     [!code-vb[CustomPolicySample#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyexporter.vb#14)]  
  
2.  <span data-ttu-id="cbf1b-113">Bağlama öğesi ya da program aracılığıyla bağlama veya uygulama yapılandırma dosyası kullanarak uç nokta yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="cbf1b-113">Insert the binding element into the endpoint binding either programmatically or using an application configuration file.</span></span> <span data-ttu-id="cbf1b-114">Aşağıdaki yordamlara bakın.</span><span class="sxs-lookup"><span data-stu-id="cbf1b-114">See the following procedures.</span></span>  
  
### <a name="to-insert-a-binding-element-using-an-application-configuration-file"></a><span data-ttu-id="cbf1b-115">Uygulama yapılandırma dosyası kullanarak bir bağlama öğesi eklemek için</span><span class="sxs-lookup"><span data-stu-id="cbf1b-115">To insert a binding element using an application configuration file</span></span>  
  
1.  <span data-ttu-id="cbf1b-116">Uygulama <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType> özel ilke onaylama bağlama öğesi için.</span><span class="sxs-lookup"><span data-stu-id="cbf1b-116">Implement <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType> for your custom policy assertion binding element.</span></span>  
  
2.  <span data-ttu-id="cbf1b-117">Bağlama öğesi uzantısı yapılandırma dosyasını kullanarak eklemek [ \<bindingElementExtensions >](../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="cbf1b-117">Add the binding element extension to the configuration file using the [\<bindingElementExtensions>](../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md) element.</span></span>  
  
3.  <span data-ttu-id="cbf1b-118">Özel bağlama kullanma yapı <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cbf1b-118">Build a custom binding using the <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-insert-a-binding-element-programmatically"></a><span data-ttu-id="cbf1b-119">Program aracılığıyla bir bağlama öğesi eklemek için</span><span class="sxs-lookup"><span data-stu-id="cbf1b-119">To insert a binding element programmatically</span></span>  
  
1.  <span data-ttu-id="cbf1b-120">Yeni bir <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> ve ekleyebilmek için bir <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cbf1b-120">Create a new <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> and add it to a <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.</span></span>  
  
2.  <span data-ttu-id="cbf1b-121">Özel bağlama adım 1'den ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cbf1b-121">Add the custom binding from step 1.</span></span> <span data-ttu-id="cbf1b-122">Yeni bir uç noktası için ve bu yeni hizmet uç noktasına ekleyin <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> çağırarak <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cbf1b-122">to a new endpoint and add that new service endpoint to the <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> by calling the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
3.  <span data-ttu-id="cbf1b-123">Açık <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="cbf1b-123">Open the <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="cbf1b-124">Aşağıdaki kod örneğinde, özel bağlama oluşturma ve bağlama öğelerinin programlama ekleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="cbf1b-124">The following code example shows the creation of a custom binding and the programmatic insertion of binding elements.</span></span>  
  
     [!code-csharp[s_imperative#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_imperative/cs/service.cs#1)]
     [!code-vb[s_imperative#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_imperative/vb/service.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="cbf1b-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cbf1b-125">See Also</span></span>  
 <xref:System.ServiceModel.Description.IPolicyImportExtension>  
 <xref:System.ServiceModel.Description.IPolicyExportExtension>  
 [<span data-ttu-id="cbf1b-126">Nasıl yapılır: özel ilke onaylamalarını içe</span><span class="sxs-lookup"><span data-stu-id="cbf1b-126">How to: Import Custom Policy Assertions</span></span>](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md)