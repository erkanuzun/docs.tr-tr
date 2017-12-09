---
title: "Sorgu ifade sözdizimi örnekleri: Öğesi işleçleri (LINQ-DataSet)"
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
ms.assetid: ca392dda-16e3-45c7-8d87-12d8d4ee0578
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6994aa8a06242823db31dda22678b15ce2215796
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="query-expression-syntax-examples-element-operators-linq-to-dataset"></a><span data-ttu-id="031ea-102">Sorgu ifade sözdizimi örnekleri: Öğesi işleçleri (LINQ-DataSet)</span><span class="sxs-lookup"><span data-stu-id="031ea-102">Query Expression Syntax Examples: Element Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="031ea-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.First%2A> ve <xref:System.Linq.Enumerable.ElementAt%2A> almak için yöntemleri <xref:System.Data.DataRow> öğelerinden bir <xref:System.Data.DataSet> sorgu ifade sözdizimi kullanarak.</span><span class="sxs-lookup"><span data-stu-id="031ea-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="031ea-104">`FillDataSet` Bu örneklerde kullanılan yöntemi belirtilen [yüklenirken veri içine bir veri kümesi](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="031ea-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="031ea-105">Bu konudaki örnekler kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarını AdventureWorks örnek veritabanını kullanın.</span><span class="sxs-lookup"><span data-stu-id="031ea-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="031ea-106">Aşağıdaki örneklerde bu konudaki `using` / `Imports` deyimleri:</span><span class="sxs-lookup"><span data-stu-id="031ea-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="031ea-107">Daha fazla bilgi için bkz: [nasıl yapılır: bir LINQ to Visual Studio'da DataSet projesi oluşturma](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="031ea-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="elementat"></a><span data-ttu-id="031ea-108">ElementAt</span><span class="sxs-lookup"><span data-stu-id="031ea-108">ElementAt</span></span>  
  
### <a name="example"></a><span data-ttu-id="031ea-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="031ea-109">Example</span></span>  
 <span data-ttu-id="031ea-110">Bu örnekte <xref:System.Linq.Enumerable.ElementAt%2A> beşinci adres almak için yöntemini burada `PostalCode` "M4B 1V7" ==.</span><span class="sxs-lookup"><span data-stu-id="031ea-110">This example uses the <xref:System.Linq.Enumerable.ElementAt%2A> method to retrieve the fifth address where `PostalCode` == "M4B 1V7".</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#elementat)]
 [!code-vb[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#elementat)]  
  
## <a name="first"></a><span data-ttu-id="031ea-111">ilk</span><span class="sxs-lookup"><span data-stu-id="031ea-111">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="031ea-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="031ea-112">Example</span></span>  
 <span data-ttu-id="031ea-113">Bu örnekte <xref:System.Linq.Enumerable.First%2A> ilk kişinin ilk adını döndürmek için yöntemdir 'Brooke'.</span><span class="sxs-lookup"><span data-stu-id="031ea-113">This example uses the <xref:System.Linq.Enumerable.First%2A> method to return the first contact whose first name is 'Brooke'.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#firstsimple)]
 [!code-vb[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#firstsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="031ea-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="031ea-114">See Also</span></span>  
 [<span data-ttu-id="031ea-115">Bir veri kümesine veri yükleme</span><span class="sxs-lookup"><span data-stu-id="031ea-115">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="031ea-116">LINQ-DataSet örnekleri</span><span class="sxs-lookup"><span data-stu-id="031ea-116">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="031ea-117">Standart sorgu işleçlerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="031ea-117">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)