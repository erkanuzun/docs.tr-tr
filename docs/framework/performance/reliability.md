---
title: "Güvenilirlik"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server [.NET Framework]
- managed code, reliability
- reliability [.NET Framework]
- writing reliable code
- code, reliability
ms.assetid: 294aa306-0afe-4cbe-b397-86ba9f1860f8
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bd13a09e66c865630b9db3210bbd95bab14cb214
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="reliability"></a><span data-ttu-id="43846-102">Güvenilirlik</span><span class="sxs-lookup"><span data-stu-id="43846-102">Reliability</span></span>
<span data-ttu-id="43846-103">SQL Server gibi sunucu ortamlarında kod yürütme zaman uyumsuz özel durumları karşı korumak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="43846-103">It is important that code executing in server environments such as SQL Server protect against asynchronous exceptions.</span></span> <span data-ttu-id="43846-104">Güvenilirlik, burada açıklandığı gibi SQL Server'a özel değildir ancak yazma için güvenilir bir .NET Framework sürüm yürütülen herhangi bir ana bilgisayar için 2.0 ortamı kodu.</span><span class="sxs-lookup"><span data-stu-id="43846-104">Reliability, as discussed here, is not specific to SQL Server but to writing reliable code for any host executing in a .NET Framework version 2.0 environment.</span></span> <span data-ttu-id="43846-105">Ancak, SQL Server kapsamlı yapmadan ilk Hizmeti'yle sürüm 2.0, yeni güvenilirlik özelliklerini örnek olarak kullanılmak üzere olur.</span><span class="sxs-lookup"><span data-stu-id="43846-105">However, SQL Server is the first service making extensive use of the new reliability features of version 2.0, so it is used as an example.</span></span>  
  
 <span data-ttu-id="43846-106">SQL Server çalıştıran kodu diğer sunucu ortamları'den daha sıkı güvenilirlik yönergeleri uğraşmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="43846-106">Code running in SQL Server must deal with more stringent reliability guidelines than other server environments.</span></span> <span data-ttu-id="43846-107">Bu SQL Server'ın sürekli kaynak tüketimi nedeniyle kenarına işlemdir.</span><span class="sxs-lookup"><span data-stu-id="43846-107">This is due to SQL Server’s steady operation at the edge of resource consumption.</span></span>  <span data-ttu-id="43846-108"><xref:System.OutOfMemoryException>ve <xref:System.Threading.ThreadAbortException> özel durumlar SQL Server ortamında seyrek değildir.</span><span class="sxs-lookup"><span data-stu-id="43846-108"><xref:System.OutOfMemoryException> and <xref:System.Threading.ThreadAbortException> exceptions are not uncommon in the SQL Server environment.</span></span> <span data-ttu-id="43846-109">Bu genel olarak daha az üzerinde odaklanmış güvenilirlik yönergelerdir ve yönetilen kod face, düzgün biçimde başarısız olmasına daha fazla üzerinde tam olarak güvenilmeyen izin verme <xref:System.AppDomain>-sunucusu tutar tutarlılık ve kullanılabilirlik birincil yoludur geri dönüşümü düzeyi.</span><span class="sxs-lookup"><span data-stu-id="43846-109">These guidelines in general are focused less on reliability and more on allowing fully trusted managed code to fail gracefully in the face of <xref:System.AppDomain>-level recycling, which is the primary way the server maintains consistency and availability.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="43846-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="43846-110">In This Section</span></span>  
 [<span data-ttu-id="43846-111">SQL Server programlama ve konak koruması öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="43846-111">SQL Server Programming and Host Protection Attributes</span></span>](../../../docs/framework/performance/sql-server-programming-and-host-protection-attributes.md)  
 <span data-ttu-id="43846-112">Açıklar nasıl <xref:System.Security.Permissions.HostProtectionAttribute> özniteliği SQL Server tarafından yönetilen kodun yürütülmesini kısıtlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="43846-112">Describes how the <xref:System.Security.Permissions.HostProtectionAttribute> attribute is used by SQL Server to restrict the execution of managed code.</span></span>  
  
 [<span data-ttu-id="43846-113">Güvenilirlik en iyi uygulamalar</span><span class="sxs-lookup"><span data-stu-id="43846-113">Reliability Best Practices</span></span>](../../../docs/framework/performance/reliability-best-practices.md)  
 <span data-ttu-id="43846-114">Güvenilirlik gereksinimlerini karşılayan kod yazma için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="43846-114">Provides guidelines for writing code that meets reliability requirements.</span></span>  
  
 [<span data-ttu-id="43846-115">Kısıtlı yürütme bölgeleri</span><span class="sxs-lookup"><span data-stu-id="43846-115">Constrained Execution Regions</span></span>](../../../docs/framework/performance/constrained-execution-regions.md)  
 <span data-ttu-id="43846-116">Kısıtlı yürütme bölgeleri (CERs) davranışını ve işlevi açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="43846-116">Describes the function and behavior of constrained execution regions (CERs).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="43846-117">Başvuru</span><span class="sxs-lookup"><span data-stu-id="43846-117">Reference</span></span>  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
  
 <xref:System.Security.Permissions.HostProtectionResource>