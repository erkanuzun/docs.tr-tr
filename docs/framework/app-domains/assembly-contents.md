---
title: "Derleme İçerikleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- assemblies [.NET Framework], single-file
- single-file assemblies
- multifile assemblies
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b51380126de164a4e0934068c7e0de55f5f3d92e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="assembly-contents"></a><span data-ttu-id="f491b-102">Derleme İçerikleri</span><span class="sxs-lookup"><span data-stu-id="f491b-102">Assembly Contents</span></span>
<span data-ttu-id="f491b-103">Genel olarak, statik bir derleme dört öğeden oluşabilir:</span><span class="sxs-lookup"><span data-stu-id="f491b-103">In general, a static assembly can consist of four elements:</span></span>  
  
-   <span data-ttu-id="f491b-104">[Derleme bildirimi](../../../docs/framework/app-domains/assembly-manifest.md), derleme meta verilerini içeriyor.</span><span class="sxs-lookup"><span data-stu-id="f491b-104">The [assembly manifest](../../../docs/framework/app-domains/assembly-manifest.md), which contains assembly metadata.</span></span>  
  
-   <span data-ttu-id="f491b-105">Tür metaverileri.</span><span class="sxs-lookup"><span data-stu-id="f491b-105">Type metadata.</span></span>  
  
-   <span data-ttu-id="f491b-106">Türleri uygulayan Microsoft ara dili (MSIL) kodu.</span><span class="sxs-lookup"><span data-stu-id="f491b-106">Microsoft intermediate language (MSIL) code that implements the types.</span></span>  
  
-   <span data-ttu-id="f491b-107">Bir kaynak kümesi.</span><span class="sxs-lookup"><span data-stu-id="f491b-107">A set of resources.</span></span>  
  
 <span data-ttu-id="f491b-108">Yalnızca derleme bildirimi gereklidir, ancak derlemeye herhangi bir anlamlı işlevsellik sağlamak için türler veya kaynaklar gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f491b-108">Only the assembly manifest is required, but either types or resources are needed to give the assembly any meaningful functionality.</span></span>  
  
 <span data-ttu-id="f491b-109">Bu öğeleri bir derleme içinde gruplandırmanın çeşitli yolları vardır.</span><span class="sxs-lookup"><span data-stu-id="f491b-109">There are several ways to group these elements in an assembly.</span></span> <span data-ttu-id="f491b-110">Tüm öğeleri, aşağıda gösterildiği şekilde tek bir fiziksel dosya halinde gruplandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f491b-110">You can group all elements in a single physical file, which is shown in the following illustration.</span></span>  
  
 <span data-ttu-id="f491b-111">![MyAssembly.dll](../../../docs/framework/app-domains/media/assemblyover1.gif "assemblyover1")</span><span class="sxs-lookup"><span data-stu-id="f491b-111">![MyAssembly.dll](../../../docs/framework/app-domains/media/assemblyover1.gif "assemblyover1")</span></span>  
<span data-ttu-id="f491b-112">Tek dosyalı derleme</span><span class="sxs-lookup"><span data-stu-id="f491b-112">Single-file assembly</span></span>  
  
 <span data-ttu-id="f491b-113">Alternatif olarak, bir derlemenin öğeleri birkaç dosya içinde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="f491b-113">Alternatively, the elements of an assembly can be contained in several files.</span></span> <span data-ttu-id="f491b-114">Bu dosyalar derlenmiş kod modülleri (.netmodule), kaynaklar (örneğin .bmp veya .jpg dosyaları) veya uygulama tarafından gereken diğer dosyalar olabilir.</span><span class="sxs-lookup"><span data-stu-id="f491b-114">These files can be modules of compiled code (.netmodule), resources (such as .bmp or .jpg files), or other files required by the application.</span></span> <span data-ttu-id="f491b-115">Farklı dillerde yazılan modülleri birleştirmek ve az kullanılan türleri yalnızca gerektiğinde indirilen bir modülün içine yerleştirerek bir uygulamanın indirilmesini optimize etmek istediğinizde bir çoklu dosya derlemesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f491b-115">Create a multifile assembly when you want to combine modules written in different languages and to optimize downloading an application by putting seldom used types in a module that is downloaded only when needed.</span></span>  
  
 <span data-ttu-id="f491b-116">Aşağıdaki görselde, kuramsal bir uygulamanın geliştiricisi bazı işlevsellik kodlarını farklı modüllere ayırmayı ve büyük bir kaynak dosyasını (bu durumda bir .bmp görüntüsü) orijinal dosyasında tutmayı seçmiştir.</span><span class="sxs-lookup"><span data-stu-id="f491b-116">In the following illustration, the developer of a hypothetical application has chosen to separate some utility code into a different module and to keep a large resource file (in this case a .bmp image) in its original file.</span></span> <span data-ttu-id="f491b-117">.NET Framework, yalnızca kendine atıfta bulunulduğunda bir dosya indirdiğinden, seyrek atıfta bulunulan bir kodu uygulamadan farklı bir dosyada tutmak kod indirmeyi optimize eder.</span><span class="sxs-lookup"><span data-stu-id="f491b-117">The .NET Framework downloads a file only when it is referenced; keeping infrequently referenced code in a separate file from the application optimizes code download.</span></span>  
  
 <span data-ttu-id="f491b-118">![MyAssembly.dll](../../../docs/framework/app-domains/media/assemblyover2.gif "assemblyover2")</span><span class="sxs-lookup"><span data-stu-id="f491b-118">![MyAssembly.dll](../../../docs/framework/app-domains/media/assemblyover2.gif "assemblyover2")</span></span>  
<span data-ttu-id="f491b-119">Çoklu dosya derlemesi</span><span class="sxs-lookup"><span data-stu-id="f491b-119">Multifile assembly</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f491b-120">Bir çoklu dosya derlemesini oluşturan dosyalar dosya sistemi tarafından fiziksel olarak bağlı değildir.</span><span class="sxs-lookup"><span data-stu-id="f491b-120">The files that make up a multifile assembly are not physically linked by the file system.</span></span> <span data-ttu-id="f491b-121">Bunun yerine, derleme bildirimi aracılığıyla bağlanırlar ve ortak dil çalışma zamanı, bunları birer birim olarak yönetir.</span><span class="sxs-lookup"><span data-stu-id="f491b-121">Rather, they are linked through the assembly manifest and the common language runtime manages them as a unit.</span></span>  
  
 <span data-ttu-id="f491b-122">Bu görselde, üç dosya da MyAssembly.dll içindeki derleme bildiriminde açıklandığı şekilde bir derlemede bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f491b-122">In this illustration, all three files belong to an assembly, as described in the assembly manifest contained in MyAssembly.dll.</span></span> <span data-ttu-id="f491b-123">Dosya sistemi açısından üç ayrı dosyadırlar.</span><span class="sxs-lookup"><span data-stu-id="f491b-123">To the file system, they are three separate files.</span></span> <span data-ttu-id="f491b-124">Util.netmodule dosyası hiçbir derleme bilgisi içermediğinden, bu dosyanın bir modül olarak derlendiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f491b-124">Note that the file Util.netmodule was compiled as a module because it contains no assembly information.</span></span> <span data-ttu-id="f491b-125">Derleme oluşturulduğunda derleme bildirimi MyAssembly.dll içine eklenerek Util.netmodule ve Graphic.bmp ile olan ilişkisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f491b-125">When the assembly was created, the assembly manifest was added to MyAssembly.dll, indicating its relationship with Util.netmodule and Graphic.bmp.</span></span>  
  
 <span data-ttu-id="f491b-126">Kaynak kodunuzu tasarlarken, uygulamanızın işlevselliğini bir veya daha fazla dosyaya nasıl ayıracağınız hakkında açık kararlar verirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f491b-126">As you currently design your source code, you make explicit decisions about how to partition the functionality of your application into one or more files.</span></span> <span data-ttu-id="f491b-127">.NET Framework kodu tasarlarken, işlevselliği bir veya daha fazla derlemeye nasıl ayıracağınız hakkında da benzer kararlar verirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f491b-127">When designing .NET Framework code, you will make similar decisions about how to partition the functionality into one or more assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f491b-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f491b-128">See Also</span></span>  
 [<span data-ttu-id="f491b-129">Ortak dil çalışma zamanı derlemeleri</span><span class="sxs-lookup"><span data-stu-id="f491b-129">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [<span data-ttu-id="f491b-130">Derleme bildirimi</span><span class="sxs-lookup"><span data-stu-id="f491b-130">Assembly Manifest</span></span>](../../../docs/framework/app-domains/assembly-manifest.md)  
 [<span data-ttu-id="f491b-131">Derleme güvenliği konuları</span><span class="sxs-lookup"><span data-stu-id="f491b-131">Assembly Security Considerations</span></span>](../../../docs/framework/app-domains/assembly-security-considerations.md)