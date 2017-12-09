---
title: "Windows Forms'ta Güvenliğe Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code access security [Windows Forms], Windows Forms
- permissions [Windows Forms], Windows Forms
- Windows Forms, security
- security [Windows Forms], about security
- access control [Windows Forms], Windows Forms
ms.assetid: 4810dc9f-ea23-4ce1-8ea1-657f0ff1d820
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e34e9dc864ffa3960c7c4f60f84b4996bab0bb28
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="security-in-windows-forms-overview"></a><span data-ttu-id="1926d-102">Windows Forms'ta Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1926d-102">Security in Windows Forms Overview</span></span>
<span data-ttu-id="1926d-103">' İn yayımlanmasından önce [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], çalışan tüm kod bir kullanıcı bilgisayar aynı hakları veya bilgisayarın kullanıcısı olan kaynaklara erişim izinleri olan kullanıcının.</span><span class="sxs-lookup"><span data-stu-id="1926d-103">Before the release of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], all code running on a user's computer had the same rights or permissions to access resources that a user of the computer had.</span></span> <span data-ttu-id="1926d-104">Örneğin, kullanıcının dosya sistemine erişim izni varsa, kodu dosya sistemi erişmesine izin; Kullanıcı bir veritabanına erişmek için izin verilen, o veritabanına erişmek için kod izin.</span><span class="sxs-lookup"><span data-stu-id="1926d-104">For example, if the user was allowed to access the file system, the code was allowed to access the file system; if the user was allowed to access a database, the code was allowed to access that database.</span></span> <span data-ttu-id="1926d-105">Bu hak ve izinler kullanıcı açıkça yerel bilgisayarda yüklü yürütülebilir dosyalarında kod için kabul edilebilir olmakla birlikte, bunlar Internet veya yerel Intranet gelen zararlı kod için kabul edilebilir olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="1926d-105">Although these rights or permissions may be acceptable for code in executables that the user has explicitly installed on the local computer, they may not be acceptable for potentially malicious code coming from the Internet or a local Intranet.</span></span> <span data-ttu-id="1926d-106">Bu kodu izniniz olmadan kullanıcının bilgisayar kaynaklarına erişebildiğini olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="1926d-106">This code should not be able to access the user's computer resources without permission.</span></span>  
  
 <span data-ttu-id="1926d-107">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] İzinleri veya kod kullanıcının sahip olduğu haklara sahip hakları ayırt olanak sağlayan bir kod erişim güvenliği adlı bir altyapı sunar.</span><span class="sxs-lookup"><span data-stu-id="1926d-107">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] introduces an infrastructure called Code Access Security that lets you differentiate the permissions, or rights, that code has from the rights that the user has.</span></span> <span data-ttu-id="1926d-108">Varsayılan olarak, Internet ve intranet'ten gelen kod yalnızca kısmi güven olarak bilinen de çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1926d-108">By default, code coming from the Internet and the Intranet can only run in what is known as partial trust.</span></span> <span data-ttu-id="1926d-109">Kısmi güven konuları kısıtlamaları bir dizi uygulamaya: başka şeylerin uygulama yerel sabit diske erişmesini sınırlıdır ve yönetilmeyen kod çalıştırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="1926d-109">Partial trust subjects an application to a series of restrictions: among other things, an application is restricted from accessing the local hard disk, and cannot run unmanaged code.</span></span> <span data-ttu-id="1926d-110">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Kod erişmek için bu kodu kimliğine göre izin kaynakları denetler: nereden geldiğini onu olup, bir [Strong-Named derlemeleri](../../../docs/framework/app-domains/strong-named-assemblies.md), bir sertifika vb. ile imzalanıp imzalanmadığı.</span><span class="sxs-lookup"><span data-stu-id="1926d-110">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] controls the resources that code is allowed to access based on the identity of that code: where it came from, whether it has a [Strong-Named Assemblies](../../../docs/framework/app-domains/strong-named-assemblies.md), whether it is signed with a certificate, and so on.</span></span>  
  
 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]<span data-ttu-id="1926d-111">Windows Forms uygulamaları dağıtmak için kullanın, teknoloji yardımcı olur, kısmi güven, tam güven veya kısmi güven yükseltilmiş izinler ile çalışan uygulamalar geliştirmek kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="1926d-111"> technology, which you use to deploy Windows Forms applications, helps make it easier for you to develop applications that run in partial trust, in full trust, or in partial trust with elevated permissions.</span></span> [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]<span data-ttu-id="1926d-112">Böylece, uygulama tam güven veya yükseltilmiş izinler yerel kullanıcıdan sorumlu bir şekilde isteyebilir izin yükseltme ve güvenilir uygulama dağıtımı gibi özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1926d-112"> provides features such as Permission Elevation and Trusted Application Deployment so that your application can request full trust or elevated permissions from the local user in a responsible manner.</span></span>  
  
## <a name="understanding-security-in-the-net-framework"></a><span data-ttu-id="1926d-113">.NET Framework Güvenliği anlama</span><span class="sxs-lookup"><span data-stu-id="1926d-113">Understanding Security in the .NET Framework</span></span>  
 <span data-ttu-id="1926d-114">Kod erişim güvenliği değişen derecelerde, diğer yönlerini kodun kimlik ve kod kaynaklandığı bağlı olarak güvenilir olması için kod sağlar.</span><span class="sxs-lookup"><span data-stu-id="1926d-114">Code access security allows code to be trusted to varying degrees, depending on where the code originates and on other aspects of the code's identity.</span></span> <span data-ttu-id="1926d-115">Ortak dil çalışma zamanı güvenlik ilkesini belirlemek için kullanır kanıt hakkında daha fazla bilgi için bkz: [kanıt](http://msdn.microsoft.com/en-us/64ceb7c8-a0b4-46c4-97dc-6c22da0539da).</span><span class="sxs-lookup"><span data-stu-id="1926d-115">For more information about the evidence the common language runtime uses to determine security policy, see [Evidence](http://msdn.microsoft.com/en-us/64ceb7c8-a0b4-46c4-97dc-6c22da0539da).</span></span> <span data-ttu-id="1926d-116">Bilgisayar sistemleri kötü amaçlı koddan korunmasına yardımcı olur ve kasıtlı olarak veya kazayla güvenliği tehlikeye güvenilen kod korumaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="1926d-116">It helps protect computer systems from malicious code and helps protect trusted code from intentionally or accidentally compromising security.</span></span> <span data-ttu-id="1926d-117">Yalnızca uygulamanız için gereken izinleri belirtebildiğinizden kod erişim güvenliği, ayrıca, uygulamanızın neler yapabileceğinizi üzerinde daha fazla denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="1926d-117">Code access security also gives you more control over what actions your application can perform, because you can specify only those permissions you need your application to have.</span></span> <span data-ttu-id="1926d-118">Bu kod değil tek kod-access-güvenlik yapma izni denetimi gerçekleştirir olsa bile kod erişim güvenliği ortak dil çalışma zamanı hedefleyen tüm yönetilen kod etkiler.</span><span class="sxs-lookup"><span data-stu-id="1926d-118">Code access security affects all managed code that targets the common language runtime, even if that code does not make a single code-access-security permission check.</span></span> <span data-ttu-id="1926d-119">Güvenlik konusunda daha fazla bilgi için [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], bkz: [temel güvenlik kavramları](../../../docs/standard/security/key-security-concepts.md) ve [kod erişim güvenliği Temelleri](../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="1926d-119">For more information about security in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], see [Key Security Concepts](../../../docs/standard/security/key-security-concepts.md) and [Code Access Security Basics](../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
 <span data-ttu-id="1926d-120">Kullanıcı bir Windows Forms yürütülebilir dosya doğrudan bir Web sunucusuna veya bir dosya paylaşımı dışına çalıştırırsanız, uygulamanız için verilen güven düzeyini kodu bulunduğu ve nasıl başlatılacağını bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1926d-120">If the user run a Windows Forms executable file directly off of a Web server or a file share, the degree of trust granted to your application depends on where the code resides, and how it is started.</span></span> <span data-ttu-id="1926d-121">Bir uygulama çalıştırıldığında otomatik olarak değerlendirilir ve ortak dil çalışma zamanı ' adlandırılmış izin kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="1926d-121">When an application runs, it is automatically evaluated and it receives a named permission set from the common language runtime.</span></span> <span data-ttu-id="1926d-122">Varsayılan olarak, yerel bilgisayardan kodu tam güven izni verilir ayarlayın, bir yerel ağ koddan yerel Intranet izni verilir ve Internet'ten kod Internet izni verilir.</span><span class="sxs-lookup"><span data-stu-id="1926d-122">By default, the code from the local computer is granted the Full Trust permission set, code from a local network is granted the Local Intranet permission set, and code from the Internet is granted the Internet permission set.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1926d-123">İçinde [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] sürüm 1.0 Service Pack 1 ve Service Pack 2, Internet bölgesi kod grubu alan hiçbir şey yapmayın izin kümesi.</span><span class="sxs-lookup"><span data-stu-id="1926d-123">In the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] version 1.0 Service Pack 1 and Service Pack 2, the Internet zone code group receives the Nothing permission set.</span></span> <span data-ttu-id="1926d-124">Diğer tüm sürümlerinde [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], Internet izinler kümesi Internet bölge kodu grubunu alır.</span><span class="sxs-lookup"><span data-stu-id="1926d-124">In all other releases of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], the Internet zone code group receives the Internet permissions set.</span></span>  
>   
>  <span data-ttu-id="1926d-125">Her bu izin kümeleri varsayılan izinler listelenir [varsayılan güvenlik ilkesi](http://msdn.microsoft.com/en-us/2c086873-0894-4f4d-8f7e-47427c1a3b55) konu.</span><span class="sxs-lookup"><span data-stu-id="1926d-125">The default permissions granted in each of these permission sets are listed in the [Default Security Policy](http://msdn.microsoft.com/en-us/2c086873-0894-4f4d-8f7e-47427c1a3b55) topic.</span></span> <span data-ttu-id="1926d-126">Uygulama alan izinlerine bağlı olarak düzgün çalışıyor ya da bir güvenlik özel durumu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1926d-126">Depending on the permissions that the application receives, it either runs correctly or generates a security exception.</span></span>  
>   
>  <span data-ttu-id="1926d-127">Çok sayıda Windows Forms uygulamaları kullanarak dağıtılacak [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1926d-127">Many Windows Forms applications will be deployed using [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)].</span></span> <span data-ttu-id="1926d-128">Oluşturmak için kullanılan araçlar bir [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] dağıtımınız ne yukarıda açıklanan daha farklı güvenlik Varsayılanları.</span><span class="sxs-lookup"><span data-stu-id="1926d-128">The tools used for generating a [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] deployment have different security defaults than what was discussed earlier.</span></span> <span data-ttu-id="1926d-129">Daha fazla bilgi için aşağıdaki tartışma bakın.</span><span class="sxs-lookup"><span data-stu-id="1926d-129">For more information, see the following discussion.</span></span>  
  
 <span data-ttu-id="1926d-130">Güvenlik İlkesi değiştirilebildiğinden uygulamanızı gerçek izinler varsayılan değerlerinden farklı olabilir; Bu, uygulamanızın tek bir bilgisayarda, ancak başka izninizin olduğundan emin anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1926d-130">The actual permissions granted to your application can be different from the default values, because the security policy can be modified; this means that your application can have permission on one computer, but not on another.</span></span>  
  
## <a name="developing-a-more-secure-windows-forms-application"></a><span data-ttu-id="1926d-131">Daha güvenli bir Windows Forms uygulaması geliştirme</span><span class="sxs-lookup"><span data-stu-id="1926d-131">Developing a More Secure Windows Forms Application</span></span>  
 <span data-ttu-id="1926d-132">Güvenlik, uygulama geliştirme tüm adımda önemlidir.</span><span class="sxs-lookup"><span data-stu-id="1926d-132">Security is important in all steps of application development.</span></span> <span data-ttu-id="1926d-133">Gözden geçirme ve aşağıdaki başlangıç [güvenli kodlama yönergeleri](../../../docs/standard/security/secure-coding-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="1926d-133">Start by reviewing and following the [Secure Coding Guidelines](../../../docs/standard/security/secure-coding-guidelines.md).</span></span>  
  
 <span data-ttu-id="1926d-134">Ardından, uygulamanızın tam güvende olup çalıştırmanız gerekir ya da kısmi güvende olup çalışmalı karar verin.</span><span class="sxs-lookup"><span data-stu-id="1926d-134">Next, decide whether your application must run in full trust, or whether it should run in partial trust.</span></span> <span data-ttu-id="1926d-135">Tam güvende uygulamanızı çalıştıran yerel bilgisayardaki kaynaklara erişimi kolay hale getirir, ancak, değil tasarlayıp uygulamanızı kesinlikle güvenli kodlama yönergelerine göre uygulamanızı ve yüksek güvenlik riskleri, kullanıcılara gösterir konu.</span><span class="sxs-lookup"><span data-stu-id="1926d-135">Running your application in full trust makes it easier to access resources on the local computer, but exposes your application and its users to high security risks if you do not design and develop your application strictly according to the Secure Coding Guidelines topic.</span></span> <span data-ttu-id="1926d-136">Kısmi güvende uygulamanızı çalıştıran daha güvenli bir uygulama geliştirmek kolaylaştırır ve çok riskini azaltır, ancak daha fazla belirli özellikleri uygulamak nasıl planlama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1926d-136">Running your application in partial trust makes it easier to develop a more secure application and reduces much risk, but requires more planning in how to implement certain features.</span></span>  
  
 <span data-ttu-id="1926d-137">Kısmi güven (diğer bir deyişle, ya da Internet veya yerel Intranet izin kümeleri) seçerseniz, uygulamanız bu ortamda davranmasına istediğiniz nasıl karar verin.</span><span class="sxs-lookup"><span data-stu-id="1926d-137">If you choose partial trust (that is, either the Internet or Local Intranet permission sets), decide how you want your application to behave in this environment.</span></span> <span data-ttu-id="1926d-138">Windows Forms zaman yarı güvenilir bir ortamda özellikleri uygulamak için alternatif, daha güvenli yolu sağlar.</span><span class="sxs-lookup"><span data-stu-id="1926d-138">Windows Forms provides alternative, more secure ways to implement features when in a semi-trusted environment.</span></span> <span data-ttu-id="1926d-139">Uygulamanızın veri erişim gibi bazı bölümleri tasarlanmış ve kısmi güven ve tam güven ortamları için farklı bir şekilde yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="1926d-139">Certain parts of your application, such as data access, can be designed and written differently for both partial trust and full trust environments.</span></span> <span data-ttu-id="1926d-140">Uygulama ayarları gibi bazı Windows Forms özellikleri, kısmi güvende çalışmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1926d-140">Some Windows Forms features, such as application settings, are designed to work in partial trust.</span></span> <span data-ttu-id="1926d-141">Daha fazla bilgi için bkz: [uygulama ayarlarına genel bakış](../../../docs/framework/winforms/advanced/application-settings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1926d-141">For more information, see [Application Settings Overview](../../../docs/framework/winforms/advanced/application-settings-overview.md).</span></span>  
  
 <span data-ttu-id="1926d-142">Uygulamanızın kısmi güven verir, ancak tam güvende çalıştırmak istiyor musunuz daha fazla izin gerekirse, yalnızca gereksinim duyduğunuz ek izinler sunduğundan sırasında kısmi güvende çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1926d-142">If your application needs more permissions than partial trust allows, but you do not want to run in full trust, you can run in partial trust while asserting only those additional permissions you need.</span></span> <span data-ttu-id="1926d-143">Kısmi güvende çalıştırmak istediğiniz, ancak bir dizine kullanıcının dosya sistemindeki Uygulama salt okunur erişim vermeniz gerekir, örneğin, isteyebilir <xref:System.Security.Permissions.FileIOPermission> yalnızca bu dizin için.</span><span class="sxs-lookup"><span data-stu-id="1926d-143">For example, if you want to run in partial trust, but must grant your application read-only access to a directory on the user's file system, you can request <xref:System.Security.Permissions.FileIOPermission> only for that directory.</span></span> <span data-ttu-id="1926d-144">Bu yaklaşım, doğru şekilde kullanıldığında, uygulama artırılmış işlevsellik sağlar ve kullanıcılarınız için güvenlik riskleri en aza.</span><span class="sxs-lookup"><span data-stu-id="1926d-144">Used correctly, this approach can give your application increased functionality and minimize security risks to your users.</span></span>  
  
 <span data-ttu-id="1926d-145">Kısmi güvende çalışacak bir uygulama geliştirirken, uygulamanızın çalıştırmalısınız hangi izinlerin izlemek ve hangi izinlerin, uygulamanızın isteğe bağlı olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1926d-145">When you develop an application that will run in partial trust, keep track of what permissions your application must run and what permissions your application could optionally use.</span></span> <span data-ttu-id="1926d-146">Tüm izinleri bilindiğinde ise uygulama düzeyinde izin bildirim temelli bir isteği olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="1926d-146">When all the permissions are known, you should make a declarative request for permission at the application level.</span></span> <span data-ttu-id="1926d-147">İzinleri bildirir isteyen [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] uygulamanızın hangi izinleri hakkında gerektiğini ve hangi izinlerin özellikle değil istediğiniz zaman çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1926d-147">Requesting permissions informs the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] run time about which permissions your application needs and which permissions it specifically does not want.</span></span> <span data-ttu-id="1926d-148">İstekte bulunan izinleri hakkında daha fazla bilgi için bkz: [izinleri isteyen](http://msdn.microsoft.com/en-us/0447c49d-8cba-45e4-862c-ff0b59bebdc2).</span><span class="sxs-lookup"><span data-stu-id="1926d-148">For more information about requesting permissions, see [Requesting Permissions](http://msdn.microsoft.com/en-us/0447c49d-8cba-45e4-862c-ff0b59bebdc2).</span></span>  
  
 <span data-ttu-id="1926d-149">İsteğe bağlı izinleri istediğinde, uygulamanızı yazma izni, izinleri gerektiren bir eylem gerçekleştirirse, oluşturulacak güvenlik özel durumları işleme gerekir.</span><span class="sxs-lookup"><span data-stu-id="1926d-149">When you request optional permissions, you must handle security exceptions that will be generated if your application performs an action that requires permissions not granted to it.</span></span> <span data-ttu-id="1926d-150">İşleme uygun <xref:System.Security.SecurityException> uygulamanız çalışmaya devam edebilir güvence altına alır.</span><span class="sxs-lookup"><span data-stu-id="1926d-150">Appropriate handling of the <xref:System.Security.SecurityException> will ensure that your application can continue to operate.</span></span> <span data-ttu-id="1926d-151">Uygulamanızı özel durum, kullanıcı için bir özellik devre hale olup olmadığını belirlemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1926d-151">Your application can use the exception to determine whether a feature should become disabled for the user.</span></span> <span data-ttu-id="1926d-152">Örneğin, bir uygulama devre dışı bırakabilirsiniz **kaydetmek** gerekli dosya izni olmayan verilirse menü seçeneği.</span><span class="sxs-lookup"><span data-stu-id="1926d-152">For example, an application can disable the **Save** menu option if the required file permission is not granted.</span></span>  
  
 <span data-ttu-id="1926d-153">Bazı durumlarda, uygulanan tüm uygun izinleri varsa bilmek zordur.</span><span class="sxs-lookup"><span data-stu-id="1926d-153">Sometimes, it is difficult to know if you have asserted all the appropriate permissions.</span></span> <span data-ttu-id="1926d-154">Yüzey üzerinde zararsız görünen bir yöntem çağrısı, örneğin, belirli bir noktada dosya sistemi yürütmesi sırasında erişebilir.</span><span class="sxs-lookup"><span data-stu-id="1926d-154">A method call which looks innocuous on the surface, for example, may access the file system at some point during its execution.</span></span> <span data-ttu-id="1926d-155">Uygulamanız gerekli izinlere sahip değil dağıtırsanız, masaüstünüzde hata ayıklama, ancak dağıtıldığında başarısız olduğunda iyi test.</span><span class="sxs-lookup"><span data-stu-id="1926d-155">If you do not deploy your application with all the required permissions, it may test fine when you debug it on your desktop, but fail when deployed.</span></span> <span data-ttu-id="1926d-156">Her iki [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] SDK ve [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] uygulama gerekli olan izinleri hesaplamak için Araçlar içerir: MT.exe komut satırı aracı ve izinleri Hesapla özelliğini [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="1926d-156">Both the [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] SDK and [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] contain tools for calculating the permissions an application needs: the MT.exe command line tool and the Calculate Permissions feature of [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], respectively.</span></span>  
  
 <span data-ttu-id="1926d-157">Aşağıdaki konularda ek Windows Forms güvenlik özellikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1926d-157">The following topics describe additional Windows Forms security features.</span></span>  
  
|<span data-ttu-id="1926d-158">Konu</span><span class="sxs-lookup"><span data-stu-id="1926d-158">Topic</span></span>|<span data-ttu-id="1926d-159">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1926d-159">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1926d-160">-   [Daha güvenli dosya ve Windows Forms veri erişimi](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="1926d-160">-   [More Secure File and Data Access in Windows Forms](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)</span></span>|<span data-ttu-id="1926d-161">Dosyaları ve verileri bir kısmi güven ortamında erişmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="1926d-161">Describes how to access files and data in a partial trust environment.</span></span>|  
|<span data-ttu-id="1926d-162">-   [Windows Forms'ta daha güvenli yazdırma](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="1926d-162">-   [More Secure Printing in Windows Forms](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)</span></span>|<span data-ttu-id="1926d-163">Kısmi güven ortamında yazdırma özelliklerine erişmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="1926d-163">Describes how to access printing features in a partial trust environment.</span></span>|  
|<span data-ttu-id="1926d-164">-   [Windows Forms'ta ek güvenlik konuları](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="1926d-164">-   [Additional Security Considerations in Windows Forms](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)</span></span>|<span data-ttu-id="1926d-165">Pano kullanma ve bir kısmi güven ortamında yönetilmeyen kod aramalarına gerçekleştirme penceresi işleme açıklar.</span><span class="sxs-lookup"><span data-stu-id="1926d-165">Describes performing window manipulation, using the Clipboard, and making calls to unmanaged code in a partial trust environment.</span></span>|  
  
-  
  
### <a name="deploying-an-application-with-the-appropriate-permissions"></a><span data-ttu-id="1926d-166">Uygun izinlere sahip bir uygulama dağıtma</span><span class="sxs-lookup"><span data-stu-id="1926d-166">Deploying an Application with the Appropriate Permissions</span></span>  
 <span data-ttu-id="1926d-167">Bir istemci bilgisayar için bir Windows Forms uygulaması dağıtmanın en yaygın ile yöntemdir [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)], tüm bileşenlerini açıklayan bir dağıtım teknolojisi, uygulamanızın çalıştırılması gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="1926d-167">The most common means of deploying a Windows Forms application to a client computer is with [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)], a deployment technology that describes all of the components your application needs to run.</span></span> [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]<span data-ttu-id="1926d-168">derleme ve uygulamayı oluşturan dosyaları açıklamak için bildirimler kullandığı XML dosyalarını çağrılır ve ayrıca, uygulamanızın izinleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1926d-168"> uses XML files called manifests to describe the assemblies and files that make up your application, and also the permissions your application requires.</span></span>  
  
 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]<span data-ttu-id="1926d-169">bir istemci bilgisayarda yükseltilmiş izinleri isteyen iki teknolojiyi sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1926d-169"> has two technologies for requesting elevated permissions on a client computer.</span></span> <span data-ttu-id="1926d-170">Her iki teknolojinin Authenticode sertifikaların kullanımını kullanır.</span><span class="sxs-lookup"><span data-stu-id="1926d-170">Both technologies rely on the use of Authenticode certificates.</span></span> <span data-ttu-id="1926d-171">Sertifikaları, uygulamanın güvenilir bir kaynaktan geliyor kullanıcılarınız için bazı güvence yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="1926d-171">The certificates help provide some assurance to your users that the application has come from a trusted source.</span></span>  
  
 <span data-ttu-id="1926d-172">Aşağıdaki tabloda bu teknolojiler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1926d-172">The following table describes these technologies.</span></span>  
  
|<span data-ttu-id="1926d-173">Yükseltilmiş izni teknolojisi</span><span class="sxs-lookup"><span data-stu-id="1926d-173">Elevated permission technology</span></span>|<span data-ttu-id="1926d-174">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1926d-174">Description</span></span>|  
|------------------------------------|-----------------|  
|<span data-ttu-id="1926d-175">İzin yükseltme</span><span class="sxs-lookup"><span data-stu-id="1926d-175">Permission Elevation</span></span>|<span data-ttu-id="1926d-176">Güvenlik iletişim kutusu ilk kez uygulamanızı çalıştığında kullanıcıya sorar.</span><span class="sxs-lookup"><span data-stu-id="1926d-176">Prompts the user with a security dialog box the first time your application runs.</span></span> <span data-ttu-id="1926d-177">**İzin yükseltme** iletişim kutusu bildirir kullanıcı kimin uygulama yayımlanan hakkında böylece kullanıcı ek güven vermek olup olmadığına dair bilinçli bir karar yapabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="1926d-177">The **Permission Elevation** dialog box informs the user about who published the application, so that the user can make an informed decision about whether to grant it additional trust</span></span>|  
|<span data-ttu-id="1926d-178">Güvenilir uygulama dağıtımı</span><span class="sxs-lookup"><span data-stu-id="1926d-178">Trusted Application Deployment</span></span>|<span data-ttu-id="1926d-179">Bir istemci bilgisayarda bir yayımcının Authenticode sertifikası tek seferlik bir yüklemesini gerçekleştirme bir Sistem Yöneticisi içerir.</span><span class="sxs-lookup"><span data-stu-id="1926d-179">Involves a system administrator performing a one-time installation of a publisher's Authenticode certificate on a client computer.</span></span> <span data-ttu-id="1926d-180">Bu noktadan itibaren sertifikayla imzalanan uygulamaların kabul olarak güvenilir ve tam güven yerel bilgisayarda ek sormadan çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1926d-180">From that point on, any applications signed with the certificate are regarded as trusted, and can run at full trust on the local computer without additional prompting.</span></span>|  
  
 <span data-ttu-id="1926d-181">Seçtiğiniz hangi teknoloji dağıtım ortamınıza bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1926d-181">Which technology you choose will depend on your deployment environment.</span></span> <span data-ttu-id="1926d-182">Daha fazla bilgi için bkz: [ClickOnce dağıtım stratejisini seçme](/visualstudio/deployment/choosing-a-clickonce-deployment-strategy).</span><span class="sxs-lookup"><span data-stu-id="1926d-182">For more information, see [Choosing a ClickOnce Deployment Strategy](/visualstudio/deployment/choosing-a-clickonce-deployment-strategy).</span></span>  
  
 <span data-ttu-id="1926d-183">Varsayılan olarak, [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] kullanılarak dağıtılan uygulamalar [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] veya [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] SDK Araçları (Mage.exe ve MageUI.exe), tam güven sahip bir istemci bilgisayarda çalışması için yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="1926d-183">By default, [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] applications deployed using either [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or the [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] SDK tools (Mage.exe and MageUI.exe) are configured to run on a client computer that has Full Trust.</span></span> <span data-ttu-id="1926d-184">Kısmi güven kullanarak veya yalnızca bazı ek izinler kullanarak uygulamanızı dağıtıyorsanız, bu varsayılanı değiştirmek gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="1926d-184">If you are deploying your application by using partial trust or by using only some additional permissions, you will have to change this default.</span></span> <span data-ttu-id="1926d-185">Bunu biriyle yapabilirsiniz [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] veya [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] SDK aracı dağıtımınızı yapılandırdığınızda MageUI.exe.</span><span class="sxs-lookup"><span data-stu-id="1926d-185">You can do this with either [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or the [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] SDK tool MageUI.exe when you configure your deployment.</span></span> <span data-ttu-id="1926d-186">İzlenecek yol MageUI.exe kullanma hakkında daha fazla bilgi için bkz: komut satırından ClickOnce uygulamasını dağıtma.</span><span class="sxs-lookup"><span data-stu-id="1926d-186">For more information about how to use MageUI.exe, see Walkthrough: Deploying a ClickOnce Application from the Command Line.</span></span>  <span data-ttu-id="1926d-187">Ayrıca bkz. [nasıl yapılır: ClickOnce uygulaması için özel izinleri ayarlama](http://msdn.microsoft.com/library/hafybdaa\(v=vs.110\)) veya [nasıl yapılır: ClickOnce uygulaması için özel izinleri ayarlama](http://msdn.microsoft.com/library/hafybdaa\(v=vs.120\)).</span><span class="sxs-lookup"><span data-stu-id="1926d-187">Also see [How to: Set Custom Permissions for a ClickOnce Application](http://msdn.microsoft.com/library/hafybdaa\(v=vs.110\)) or [How to: Set Custom Permissions for a ClickOnce Application](http://msdn.microsoft.com/library/hafybdaa\(v=vs.120\)).</span></span>  
  
 <span data-ttu-id="1926d-188">Güvenlik yönlerini hakkında daha fazla bilgi için [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] ve izin yükseltme, bkz: [ClickOnce uygulamalarının güvenliğini sağlama](/visualstudio/deployment/securing-clickonce-applications).</span><span class="sxs-lookup"><span data-stu-id="1926d-188">For more information about the security aspects of [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] and Permission Elevation, see [Securing ClickOnce Applications](/visualstudio/deployment/securing-clickonce-applications).</span></span> <span data-ttu-id="1926d-189">Güvenilir uygulama dağıtımı hakkında daha fazla bilgi için bkz: [güvenilir uygulama dağıtımına genel bakış](/visualstudio/deployment/trusted-application-deployment-overview).</span><span class="sxs-lookup"><span data-stu-id="1926d-189">For more information about Trusted Application Deployment, see [Trusted Application Deployment Overview](/visualstudio/deployment/trusted-application-deployment-overview).</span></span>  
  
### <a name="testing-the-application"></a><span data-ttu-id="1926d-190">Uygulamayı Test Etme</span><span class="sxs-lookup"><span data-stu-id="1926d-190">Testing the Application</span></span>  
 <span data-ttu-id="1926d-191">Kullanarak Windows Forms uygulaması dağıttıysanız [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], kısmi güven veya kısıtlı izin geliştirme ortamından kümesinin hata ayıklamayı etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1926d-191">If you have deployed your Windows Forms application by using [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], you can enable debugging in partial trust or a restricted permission set from the development environment.</span></span>  <span data-ttu-id="1926d-192">Ayrıca bkz. [nasıl yapılır: sınırlı izinler ile ClickOnce uygulamasında hata ayıklama](http://msdn.microsoft.com/library/593zkfdf\(v=vs.110\)) veya [nasıl yapılır: sınırlı izinler ile ClickOnce uygulamasında hata ayıklama](http://msdn.microsoft.com/library/593zkfdf\(v=vs.120\)).</span><span class="sxs-lookup"><span data-stu-id="1926d-192">Also see [How to: Debug a ClickOnce Application with Restricted Permissions](http://msdn.microsoft.com/library/593zkfdf\(v=vs.110\)) or [How to: Debug a ClickOnce Application with Restricted Permissions](http://msdn.microsoft.com/library/593zkfdf\(v=vs.120\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1926d-193">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1926d-193">See Also</span></span>  
 [<span data-ttu-id="1926d-194">Windows Forms güvenliği</span><span class="sxs-lookup"><span data-stu-id="1926d-194">Windows Forms Security</span></span>](../../../docs/framework/winforms/windows-forms-security.md)  
 [<span data-ttu-id="1926d-195">Kod erişim güvenliği temelleri</span><span class="sxs-lookup"><span data-stu-id="1926d-195">Code Access Security Basics</span></span>](../../../docs/framework/misc/code-access-security-basics.md)  
 [<span data-ttu-id="1926d-196">ClickOnce güvenliği ve dağıtımı</span><span class="sxs-lookup"><span data-stu-id="1926d-196">ClickOnce Security and Deployment</span></span>](/visualstudio/deployment/clickonce-security-and-deployment)  
 [<span data-ttu-id="1926d-197">Güvenilir Uygulama dağıtımına genel bakış</span><span class="sxs-lookup"><span data-stu-id="1926d-197">Trusted Application Deployment Overview</span></span>](/visualstudio/deployment/trusted-application-deployment-overview)  
 [<span data-ttu-id="1926d-198">Mage.exe (bildirim üretme ve düzenleme aracı)</span><span class="sxs-lookup"><span data-stu-id="1926d-198">Mage.exe (Manifest Generation and Editing Tool)</span></span>](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md)  
 [<span data-ttu-id="1926d-199">MageUI.exe (bildirim üretme ve düzenleme aracı, grafik istemci)</span><span class="sxs-lookup"><span data-stu-id="1926d-199">MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)</span></span>](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)