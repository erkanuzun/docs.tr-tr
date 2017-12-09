---
title: "Nasıl yapılır: çağrı kurallı işlevleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b3d84873-7403-4957-8e20-b4ae39f50214
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 26bd528a7c2ad77cb801eb294c34e43c60d2bf76
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-canonical-functions"></a><span data-ttu-id="b645b-102">Nasıl yapılır: çağrı kurallı işlevleri</span><span class="sxs-lookup"><span data-stu-id="b645b-102">How to: Call Canonical Functions</span></span>
<span data-ttu-id="b645b-103"><xref:System.Data.Objects.EntityFunctions> Sınıfı LINQ to Entities sorgularında kullanmak için kurallı işlevleri yöntemlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="b645b-103">The <xref:System.Data.Objects.EntityFunctions> class contains methods that expose canonical functions to use in LINQ to Entities queries.</span></span> <span data-ttu-id="b645b-104">Kurallı işlevleri hakkında daha fazla bilgi için bkz: [kurallı işlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span><span class="sxs-lookup"><span data-stu-id="b645b-104">For information about canonical functions, see [Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b645b-105"><xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> Ve <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> yöntemleri <xref:System.Data.Objects.EntityFunctions> sınıfı kurallı işlevi eşdeğerleri sahip değil.</span><span class="sxs-lookup"><span data-stu-id="b645b-105">The <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> and <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> methods in the <xref:System.Data.Objects.EntityFunctions> class do not have canonical function equivalents.</span></span>  
  
 <span data-ttu-id="b645b-106">Doğrudan bir değerler kümesi üzerinde bir hesaplama gerçekleştirmek ve tek bir değer (olarak da bilinen toplama kurallı işlevleri) döndürmesi kurallı işlevler çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="b645b-106">Canonical functions that perform a calculation on a set of values and return a single value (also known as aggregate canonical functions) can be directly invoked.</span></span> <span data-ttu-id="b645b-107">Kurallı diğer işlevleri yalnızca bir LINQ to Entities sorgusunun bir parçası olarak çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="b645b-107">Other canonical functions can only be called as part of a LINQ to Entities query.</span></span> <span data-ttu-id="b645b-108">Bir toplama işlevi doğrudan çağırmak için geçmesi gereken bir <xref:System.Data.Objects.ObjectQuery%601> işlevi.</span><span class="sxs-lookup"><span data-stu-id="b645b-108">To call an aggregate function directly, you must pass an <xref:System.Data.Objects.ObjectQuery%601> to the function.</span></span> <span data-ttu-id="b645b-109">Daha fazla bilgi için aşağıdaki ikinci örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="b645b-109">For more information, see the second example below.</span></span>  
  
 <span data-ttu-id="b645b-110">Ortak dil çalışma zamanı (CLR) yöntemleri LINQ to Entities sorgularında kullanarak bazı kurallı işlevleri çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="b645b-110">You can call some canonical functions by using common language runtime (CLR) methods in LINQ to Entities queries.</span></span> <span data-ttu-id="b645b-111">Kurallı işlevlere Eşle CLR yöntemlerin listesi için bkz: [kurallı işlev eşleme CLR yönteme](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="b645b-111">For a list of CLR methods that map to canonical functions, see [CLR Method to Canonical Function Mapping](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b645b-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="b645b-112">Example</span></span>  
 <span data-ttu-id="b645b-113">Aşağıdaki örnek kullanır [AdventureWorks satış modeli](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span><span class="sxs-lookup"><span data-stu-id="b645b-113">The following example uses the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span></span> <span data-ttu-id="b645b-114">Örnek bir LINQ to kullanan varlıklar sorgu yürütür <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> tüm ürünleri için döndürülecek yöntemi arasındaki farkı `SellEndDate` ve `SellStartDate` 365 günden:</span><span class="sxs-lookup"><span data-stu-id="b645b-114">The example executes a LINQ to Entities query that uses the <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> method to return all products for which the difference between `SellEndDate` and `SellStartDate` is less than 365 days:</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="b645b-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="b645b-115">Example</span></span>  
 <span data-ttu-id="b645b-116">Aşağıdaki örnek kullanır [AdventureWorks satış modeli](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span><span class="sxs-lookup"><span data-stu-id="b645b-116">The following example uses the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span></span> <span data-ttu-id="b645b-117">Örnek toplama çağırır <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> standart sapmasını doğrudan döndürülecek yöntemi `SalesOrderHeader` toplamları.</span><span class="sxs-lookup"><span data-stu-id="b645b-117">The example calls the aggregate <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> method directly to return the standard deviation of `SalesOrderHeader` subtotals.</span></span> <span data-ttu-id="b645b-118">Unutmayın bir <xref:System.Data.Objects.ObjectQuery%601> bir LINQ to Entities sorgusunun parçası olmadan çağrılmasına izin veren işlevi geçirilir.</span><span class="sxs-lookup"><span data-stu-id="b645b-118">Note that an <xref:System.Data.Objects.ObjectQuery%601> is passed to the function, which allows it to be called without being part of a LINQ to Entities query.</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="b645b-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b645b-119">See Also</span></span>  
 [<span data-ttu-id="b645b-120">LINQ to Entities sorgularında işlevleri çağırma</span><span class="sxs-lookup"><span data-stu-id="b645b-120">Calling Functions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [<span data-ttu-id="b645b-121">LINQ to Entities sorguları</span><span class="sxs-lookup"><span data-stu-id="b645b-121">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)