---
title: "Nasıl Yapılır: İstemci Uygulama Hizmetleri ile Kullanıcı Oturum Açma Adını Uygulama"
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
helpviewer_keywords:
- validating users [client application services]
- validation [.NET Framework], client application services
- client application services, authenticate users
ms.assetid: 5431a671-eb02-4e18-a651-24764fccec9a
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 909fbaa4e7dc1d384b5085d71cec346bde44cf14
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-user-login-with-client-application-services"></a><span data-ttu-id="c65a4-102">Nasıl Yapılır: İstemci Uygulama Hizmetleri ile Kullanıcı Oturum Açma Adını Uygulama</span><span class="sxs-lookup"><span data-stu-id="c65a4-102">How to: Implement User Login with Client Application Services</span></span>
<span data-ttu-id="c65a4-103">İstemci uygulama hizmetleri varolan aracılığıyla kullanıcıları doğrulamak için kullanabileceğiniz [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] profil hizmeti.</span><span class="sxs-lookup"><span data-stu-id="c65a4-103">You can use client application services to validate users through an existing [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] profile service.</span></span> <span data-ttu-id="c65a4-104">Nasıl ayarlandığı hakkında bilgi için [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] profil hizmet için bkz: [Microsoft Ajax ile form kimlik doğrulaması kullanarak](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e).</span><span class="sxs-lookup"><span data-stu-id="c65a4-104">For information about how to set up the [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] profile service, see [Using Forms Authentication with Microsoft Ajax](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e).</span></span>  
  
 <span data-ttu-id="c65a4-105">Aşağıdaki yordamlar, uygulamanızın istemci kimlik doğrulama hizmeti sağlayıcıları birini kullanmak için yapılandırıldığında, kimlik doğrulama hizmeti aracılığıyla kullanıcıları doğrulamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="c65a4-105">The following procedures describe how to validate users through the authentication service when your application is configured to use one of the client authentication service providers.</span></span> <span data-ttu-id="c65a4-106">Daha fazla bilgi için bkz: [nasıl yapılır: istemci uygulama hizmetleri yapılandırma](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).</span><span class="sxs-lookup"><span data-stu-id="c65a4-106">For more information, see [How to: Configure Client Application Services](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).</span></span>  
  
 <span data-ttu-id="c65a4-107">Genellikle aracılığıyla tüm doğrulama işlemini gerçekleştirecek `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c65a4-107">You will typically perform all validation through the `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c65a4-108">Bu yöntem kimlik doğrulama hizmeti yapılandırılmış kimlik doğrulama sağlayıcısı aracılığıyla etkileşim yönetir.</span><span class="sxs-lookup"><span data-stu-id="c65a4-108">This method manages the interaction with the authentication service through the configured authentication provider.</span></span> <span data-ttu-id="c65a4-109">Daha fazla bilgi için bkz: [istemci uygulama hizmetlerine genel bakış](../../../docs/framework/common-client-technologies/client-application-services-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c65a4-109">For more information, see [Client Application Services Overview](../../../docs/framework/common-client-technologies/client-application-services-overview.md).</span></span>  
  
 <span data-ttu-id="c65a4-110">Forms kimlik doğrulaması yordamları çalışan bir erişim gerektiren [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] kimlik doğrulama hizmeti.</span><span class="sxs-lookup"><span data-stu-id="c65a4-110">The forms authentication procedures require access to a running [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] authentication service.</span></span> <span data-ttu-id="c65a4-111">İstemci uygulamasının uçtan uca test konusunda yönergeler özellikleri Hizmetleri için bkz: [izlenecek yol: istemci uygulama hizmetleri kullanarak](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md).</span><span class="sxs-lookup"><span data-stu-id="c65a4-111">For guidance on end-to-end testing of client application services features, see [Walkthrough: Using Client Application Services](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md).</span></span>  
  
### <a name="to-authenticate-a-user-with-forms-authentication-using-a-membership-credentials-provider"></a><span data-ttu-id="c65a4-112">Bir kullanıcının bir üyelik kullanarak form kimlik doğrulaması ile kimlik doğrulaması için kimlik bilgileri sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="c65a4-112">To authenticate a user with forms authentication using a membership credentials provider</span></span>  
  
1.  <span data-ttu-id="c65a4-113">Uygulama <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="c65a4-113">Implement the <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> interface.</span></span> <span data-ttu-id="c65a4-114">Aşağıdaki örnekte gösterildiği kod bir <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A?displayProperty=nameWithType> uygulama oturum açma iletişim kutusu sınıfı için türetilen <xref:System.Windows.Forms.Form?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c65a4-114">The following code example shows a <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A?displayProperty=nameWithType> implementation for a login dialog box class derived from  <xref:System.Windows.Forms.Form?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c65a4-115">Bu iletişim kutusunda metin kutuları kullanıcı adı ve parolasını ve bir "Beni anımsa" onay kutusu vardır.</span><span class="sxs-lookup"><span data-stu-id="c65a4-115">This dialog box has text boxes for user name and password and a "remember me" check box.</span></span> <span data-ttu-id="c65a4-116">İstemci kimlik doğrulama sağlayıcısı çağırdığında <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> yöntemi, formun görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c65a4-116">When the client authentication provider calls the <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> method, the form is displayed.</span></span> <span data-ttu-id="c65a4-117">Kullanıcı oturum açma iletişim kutusunda bilgileri doldurur ve Tamam tıkladığında belirtilen değerlerle yeni bir döndürülür <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="c65a4-117">When the user fills in the information in the login dialog box and clicks OK, the specified values are returned in a new <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials> object.</span></span>  
  
     [!code-csharp[ClientApplicationServices#210](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Login.cs#210)]
     [!code-vb[ClientApplicationServices#210](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Login.vb#210)]  
  
2.  <span data-ttu-id="c65a4-118">Çağrı `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> yöntemi ve boş dize parametre değerleri olarak geçirin.</span><span class="sxs-lookup"><span data-stu-id="c65a4-118">Call the `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> method and pass in empty strings as the parameter values.</span></span> <span data-ttu-id="c65a4-119">Boş dizeler belirttiğinizde, bu yöntem dahili olarak çağırır <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> yöntemi, uygulamanız için yapılandırılan kimlik bilgileri sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="c65a4-119">When you specify empty strings, this method internally calls the <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> method for the credentials provider configured for your application.</span></span> <span data-ttu-id="c65a4-120">Aşağıdaki kod örneği, tüm Windows Forms uygulamaya erişimi kısıtlamak için bu yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="c65a4-120">The following code example calls this method to restrict access to an entire Windows Forms application.</span></span> <span data-ttu-id="c65a4-121">Bu kod ekleyebilirsiniz bir <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="c65a4-121">You can add this code to a <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> handler.</span></span>  
  
     [!code-csharp[ClientApplicationServices#317](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#317)]
     [!code-vb[ClientApplicationServices#317](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#317)]  
  
### <a name="to-authenticate-a-user-with-forms-authentication-without-using-a-membership-credentials-provider"></a><span data-ttu-id="c65a4-122">Üyelik kimlik bilgileri sağlayıcısı kullanmadan form kimlik doğrulaması ile bir kullanıcının kimliğini doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="c65a4-122">To authenticate a user with forms authentication without using a membership credentials provider</span></span>  
  
-   <span data-ttu-id="c65a4-123">Çağrı `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> yöntemi ve kullanıcı adı ve parola değerlerini geçişinde kullanıcıdan alınır.</span><span class="sxs-lookup"><span data-stu-id="c65a4-123">Call the `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> method and pass in user name and password values retrieved from the user.</span></span>  
  
     [!code-csharp[ClientApplicationServices#318](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#318)]
     [!code-vb[ClientApplicationServices#318](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#318)]  
  
### <a name="to-authenticate-a-user-with-windows-authentication"></a><span data-ttu-id="c65a4-124">Windows kimlik doğrulamasıyla kullanıcının kimliğini doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="c65a4-124">To authenticate a user with Windows authentication</span></span>  
  
-   <span data-ttu-id="c65a4-125">Çağrı `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> yöntemi ve geçişi dizeleri parametre boş.</span><span class="sxs-lookup"><span data-stu-id="c65a4-125">Call the `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> method and pass empty strings for the parameters.</span></span> <span data-ttu-id="c65a4-126">Bu yöntem çağrısı her zaman döndürülecek `true` Windows kimliğini içeren kullanıcının tanımlama bilgisi önbelleği için bir tanımlama bilgisi ekler.</span><span class="sxs-lookup"><span data-stu-id="c65a4-126">This method call will always return `true` and will add a cookie to the user's cookie cache that contains the Windows identity.</span></span>  
  
     [!code-csharp[ClientApplicationServices#319](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#319)]
     [!code-vb[ClientApplicationServices#319](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#319)]  
  
## <a name="robust-programming"></a><span data-ttu-id="c65a4-127">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="c65a4-127">Robust Programming</span></span>  
 <span data-ttu-id="c65a4-128">Bu konudaki örnek kod, bir Windows istemci uygulamasında kimlik doğrulamasının en basit kullanımları gösterir.</span><span class="sxs-lookup"><span data-stu-id="c65a4-128">The example code in this topic demonstrates the simplest usages of authentication in a Windows client application.</span></span> <span data-ttu-id="c65a4-129">Çağırdığınızda `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> yöntemi ile istemci uygulama hizmetleri ve forms kimlik doğrulaması, kodunuzu atabilirsiniz ancak, bir <xref:System.Net.WebException>.</span><span class="sxs-lookup"><span data-stu-id="c65a4-129">When you call the `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> method with client application services and forms authentication, however, your code can throw a <xref:System.Net.WebException>.</span></span> <span data-ttu-id="c65a4-130">Bu kimlik doğrulama hizmeti kullanılamaz olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c65a4-130">This indicates that the authentication service is unavailable.</span></span> <span data-ttu-id="c65a4-131">Bu özel durumun nasıl ele alınacağını örneği için bkz: [izlenecek yol: istemci uygulama hizmetleri kullanarak](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md).</span><span class="sxs-lookup"><span data-stu-id="c65a4-131">For an example of how to handle this exception, see [Walkthrough: Using Client Application Services](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c65a4-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c65a4-132">See Also</span></span>  
 [<span data-ttu-id="c65a4-133">İstemci uygulama hizmetleri</span><span class="sxs-lookup"><span data-stu-id="c65a4-133">Client Application Services</span></span>](../../../docs/framework/common-client-technologies/client-application-services.md)  
 [<span data-ttu-id="c65a4-134">İstemci uygulama hizmetlerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="c65a4-134">Client Application Services Overview</span></span>](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 [<span data-ttu-id="c65a4-135">Nasıl yapılır: istemci uygulama hizmetlerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c65a4-135">How to: Configure Client Application Services</span></span>](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 [<span data-ttu-id="c65a4-136">İzlenecek yol: İstemci uygulama hizmetleri kullanma</span><span class="sxs-lookup"><span data-stu-id="c65a4-136">Walkthrough: Using Client Application Services</span></span>](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 [<span data-ttu-id="c65a4-137">Microsoft Ajax ile form kimlik doğrulaması kullanma</span><span class="sxs-lookup"><span data-stu-id="c65a4-137">Using Forms Authentication with Microsoft Ajax</span></span>](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)