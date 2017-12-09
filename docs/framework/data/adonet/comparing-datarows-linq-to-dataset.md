---
title: "DataRow (LINQ-DataSet) karşılaştırma"
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
ms.assetid: 8fe0eadf-297b-487c-8d4b-7816753c2883
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9f17a73d2d6349d4fc35668d7251877034e5e29f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="comparing-datarows-linq-to-dataset"></a><span data-ttu-id="f3916-102">DataRow (LINQ-DataSet) karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="f3916-102">Comparing DataRows (LINQ to DataSet)</span></span>
[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]<span data-ttu-id="f3916-103">eşit olup olmadığını görmek için kaynağı öğeleri karşılaştırmak için çeşitli kümesi işleçleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f3916-103"> defines various set operators to compare source elements to see if they are equal.</span></span> [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]<span data-ttu-id="f3916-104">Aşağıdaki kümesi işleçleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="f3916-104"> provides the following set operators:</span></span>  
  
-   <xref:System.Linq.Enumerable.Distinct%2A>  
  
-   <xref:System.Linq.Enumerable.Union%2A>  
  
-   <xref:System.Linq.Enumerable.Intersect%2A>  
  
-   <xref:System.Linq.Enumerable.Except%2A>  
  
 <span data-ttu-id="f3916-105">Bu işleçlere çağırarak kaynağı öğeleri karşılaştırma <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> ve <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> öğelerinin her koleksiyon yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="f3916-105">These operators compare source elements by calling the <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> and <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> methods on each collection of elements.</span></span> <span data-ttu-id="f3916-106">Durumunda bir <xref:System.Data.DataRow>, bu operatörler genellikle ayarlama işlemleri için ideal davranışı üzerinde tablo veri değil bir başvuru karşılaştırma gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="f3916-106">In the case of a <xref:System.Data.DataRow>, these operators perform a reference comparison, which is generally not the ideal behavior for set operations over tabular data.</span></span> <span data-ttu-id="f3916-107">Ayarlama işlemleri için genellikle öğesi değerlerin eşit olup ve öğesi başvuruları belirlemek istiyor.</span><span class="sxs-lookup"><span data-stu-id="f3916-107">For set operations, you usually want to determine whether the element values are equal and not the element references.</span></span> <span data-ttu-id="f3916-108">Bu nedenle, <xref:System.Data.DataRowComparer> sınıfı eklenmiştir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f3916-108">Therefore, the <xref:System.Data.DataRowComparer> class has been added to [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="f3916-109">Bu sınıf, satır değerlerini karşılaştırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f3916-109">This class can be used to compare row values.</span></span>  
  
 <span data-ttu-id="f3916-110"><xref:System.Data.DataRowComparer> Sınıfı için bir değer karşılaştırma uygulama içerir <xref:System.Data.DataRow>, bu sınıf için ayarlama işlemleri gibi kullanılabilmesi için <xref:System.Linq.Enumerable.Distinct%2A>.</span><span class="sxs-lookup"><span data-stu-id="f3916-110">The <xref:System.Data.DataRowComparer> class contains a value comparison implementation for <xref:System.Data.DataRow>, so this class can be used for set operations such as <xref:System.Linq.Enumerable.Distinct%2A>.</span></span> <span data-ttu-id="f3916-111">Bu sınıf doğrudan örneği oluşturulamıyor; Bunun yerine, <xref:System.Data.DataRowComparer.Default%2A> özelliği kullanılan, bir örneğini döndürmek için <xref:System.Data.DataRowComparer%601>.</span><span class="sxs-lookup"><span data-stu-id="f3916-111">This class cannot be directly instantiated; instead, the <xref:System.Data.DataRowComparer.Default%2A> property must be used to return an instance of the <xref:System.Data.DataRowComparer%601>.</span></span> <span data-ttu-id="f3916-112"><xref:System.Data.DataRowComparer%601.Equals%2A> Yöntemi çağrıldıktan sonra ve iki <xref:System.Data.DataRow> Karşılaştırılacak nesneler geçirilir giriş parametreleri olarak.</span><span class="sxs-lookup"><span data-stu-id="f3916-112">The <xref:System.Data.DataRowComparer%601.Equals%2A> method is then called and the two <xref:System.Data.DataRow> objects to be compared are passed in as input parameters.</span></span> <span data-ttu-id="f3916-113"><xref:System.Data.DataRowComparer%601.Equals%2A> Yöntemi döndürür `true` ise sıralanmış bir sütun kümesini her ikisinde de değerleri <xref:System.Data.DataRow> nesneleri eşit; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="f3916-113">The <xref:System.Data.DataRowComparer%601.Equals%2A> method returns `true` if the ordered set of column values in both <xref:System.Data.DataRow> objects are equal; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3916-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="f3916-114">Example</span></span>  
 <span data-ttu-id="f3916-115">Bu örnekte `Intersect` her iki tabloda görünür kişiler döndürülecek.</span><span class="sxs-lookup"><span data-stu-id="f3916-115">This example uses `Intersect` to return contacts that appear in both tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
### <a name="example"></a><span data-ttu-id="f3916-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="f3916-116">Example</span></span>  
 <span data-ttu-id="f3916-117">Aşağıdaki örnekte, iki satır karşılaştırır ve karma kodlarını alır.</span><span class="sxs-lookup"><span data-stu-id="f3916-117">The following example compares two rows and gets their hash codes.</span></span>  
  
 [!code-vb[DP LINQ to DataSet Examples#CompareDifferentRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#comparedifferentrows)]  
  
## <a name="see-also"></a><span data-ttu-id="f3916-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f3916-118">See Also</span></span>  
 <xref:System.Data.DataRowComparer>  
 [<span data-ttu-id="f3916-119">Bir veri kümesine veri yükleme</span><span class="sxs-lookup"><span data-stu-id="f3916-119">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="f3916-120">LINQ-DataSet örnekleri</span><span class="sxs-lookup"><span data-stu-id="f3916-120">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)