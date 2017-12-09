---
title: "LINQ-DataSet sorguları"
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
ms.assetid: c1a78fa8-9f0c-40bc-a372-5575a48708fe
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 31923631d5b93368f8b71ff38d1244d726341fdc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="queries-in-linq-to-dataset"></a><span data-ttu-id="e7d23-102">LINQ-DataSet sorguları</span><span class="sxs-lookup"><span data-stu-id="e7d23-102">Queries in LINQ to DataSet</span></span>
<span data-ttu-id="e7d23-103">Bir sorgu veri kaynağından verileri alan bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="e7d23-103">A query is an expression that retrieves data from a data source.</span></span> <span data-ttu-id="e7d23-104">Sorguları genellikle ilişkisel veritabanları için SQL ve XML için XQuery gibi bir özel sorgu dili ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="e7d23-104">Queries are usually expressed in a specialized query language, such as SQL for relational databases and XQuery for XML.</span></span> <span data-ttu-id="e7d23-105">Bu nedenle, geliştiricilerin her veri kaynağı veya bunlar sorgu veri biçimi türü için yeni bir sorgu dili öğrenin gerekirdi.</span><span class="sxs-lookup"><span data-stu-id="e7d23-105">Therefore, developers have had to learn a new query language for each type of data source or data format that they query.</span></span> [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]<span data-ttu-id="e7d23-106">çeşitli veri kaynakları ve biçimleri arasında verilerle çalışmak için daha basit ve tutarlı bir modeli sunar.</span><span class="sxs-lookup"><span data-stu-id="e7d23-106"> offers a simpler, consistent model for working with data across various kinds of data sources and formats.</span></span> <span data-ttu-id="e7d23-107">İçinde bir [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] sorgu, çalışma her zaman nesneleri programlama ile.</span><span class="sxs-lookup"><span data-stu-id="e7d23-107">In a [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] query, you always work with programming objects.</span></span>  
  
 <span data-ttu-id="e7d23-108">A [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] sorgu işlemi üç eylemlerini oluşur: veri kaynağı veya kaynakları edinme, sorguyu oluşturmak ve sorgu yürütün.</span><span class="sxs-lookup"><span data-stu-id="e7d23-108">A [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] query operation consists of three actions: obtain the data source or sources, create the query, and execute the query.</span></span>  
  
 <span data-ttu-id="e7d23-109">Veri kaynakları uygulayan <xref:System.Collections.Generic.IEnumerable%601> genel arabirim sorgulanan aracılığıyla [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e7d23-109">Data sources that implement the <xref:System.Collections.Generic.IEnumerable%601> generic interface can be queried through [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)].</span></span> <span data-ttu-id="e7d23-110">Çağırma <xref:System.Data.DataTableExtensions.AsEnumerable%2A> üzerinde bir <xref:System.Data.DataTable> genel uygulayan bir nesne döndürür <xref:System.Collections.Generic.IEnumerable%601> için veri kaynağı görevi gören arabirimi [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorgular.</span><span class="sxs-lookup"><span data-stu-id="e7d23-110">Calling <xref:System.Data.DataTableExtensions.AsEnumerable%2A> on a <xref:System.Data.DataTable> returns an object which implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, which serves as the data source for [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] queries.</span></span>  
  
 <span data-ttu-id="e7d23-111">Sorgu, tam olarak veri kaynağından almak istediğiniz bilgileri belirtin.</span><span class="sxs-lookup"><span data-stu-id="e7d23-111">In the query, you specify exactly the information that you want to retrieve from the data source.</span></span> <span data-ttu-id="e7d23-112">Bir sorgu de nasıl bu bilgileri sıralanmış, gruplandırılmış ve, döndürülmeden önce şeklinde belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7d23-112">A query can also specify how that information should be sorted, grouped, and shaped before it is returned.</span></span> <span data-ttu-id="e7d23-113">İçinde [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], sorgu bir değişkende depolanır.</span><span class="sxs-lookup"><span data-stu-id="e7d23-113">In [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], a query is stored in a variable.</span></span> <span data-ttu-id="e7d23-114">Sorgu değerleri dizisi döndürmek üzere tasarlanmış sorgu değişkeni numaralandırılabilir bir tür olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e7d23-114">If the query is designed to return a sequence of values, the query variable itself must be a enumerable type.</span></span> <span data-ttu-id="e7d23-115">Bu sorgu değişkeni hiçbir eylemde bulunmaz ve hiçbir veri döndürür; yalnızca, sorgu bilgileri depolar.</span><span class="sxs-lookup"><span data-stu-id="e7d23-115">This query variable takes no action and returns no data; it only stores the query information.</span></span> <span data-ttu-id="e7d23-116">Bir sorgu oluşturduktan sonra herhangi bir veri almak için bu sorguyu yürütmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e7d23-116">After you create a query you must execute that query to retrieve any data.</span></span>  
  
 <span data-ttu-id="e7d23-117">Değerleri dizisi döndüren bir sorgu, sorgu değişkeni hiçbir zaman sorgu sonuçlarını tutar ve yalnızca sorgu komutları depolar.</span><span class="sxs-lookup"><span data-stu-id="e7d23-117">In a query that returns a sequence of values, the query variable itself never holds the query results and only stores the query commands.</span></span> <span data-ttu-id="e7d23-118">Sorgunun içinde üzerinden sorgu değişkeni yinelendiğinde kadar ertelenmiş bir `foreach` veya `For Each` döngü.</span><span class="sxs-lookup"><span data-stu-id="e7d23-118">Execution of the query is deferred until the query variable is iterated over in a `foreach` or `For Each` loop.</span></span> <span data-ttu-id="e7d23-119">Bu adlı *yürütme ertelenmiş*; diğer bir deyişle, sorgu yürütme süre sorgu oluşturulan sonra oluşur.</span><span class="sxs-lookup"><span data-stu-id="e7d23-119">This is called *deferred execution*; that is, query execution occurs some time after the query is constructed.</span></span> <span data-ttu-id="e7d23-120">Bu sorgu, istediğiniz sıklıkta yürütebilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e7d23-120">This means that you can execute a query as often as you want to.</span></span> <span data-ttu-id="e7d23-121">Örneğin, diğer uygulamalar tarafından güncelleştirilmiş bir veritabanı varsa, bu yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="e7d23-121">This is useful when, for example, you have a database that is being updated by other applications.</span></span> <span data-ttu-id="e7d23-122">Uygulamanızda güncelleştirilmiş bilgileri her zaman döndürme en son bilgiler almak ve sorguyu tekrar tekrar yürütmek için bir sorgu oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7d23-122">In your application, you can create a query to retrieve the latest information and repeatedly execute the query, returning the updated information every time.</span></span>  
  
 <span data-ttu-id="e7d23-123">Değerleri bir dizi döndürmesi ertelenmiş sorguları aksine, bir tek değer döndüren sorgular hemen çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="e7d23-123">In contrast to deferred queries, which return a sequence of values, queries that return a singleton value are executed immediately.</span></span> <span data-ttu-id="e7d23-124">Singleton sorguları bazı örnekleri şunlardır <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Average%2A>, ve <xref:System.Linq.Enumerable.First%2A>.</span><span class="sxs-lookup"><span data-stu-id="e7d23-124">Some examples of singleton queries are <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Average%2A>, and <xref:System.Linq.Enumerable.First%2A>.</span></span> <span data-ttu-id="e7d23-125">Sorgu sonuçları singleton sonucu hesaplamak için gerekli olduğundan bu hemen yürütün.</span><span class="sxs-lookup"><span data-stu-id="e7d23-125">These execute immediately because the query results are required to calculate the singleton result.</span></span> <span data-ttu-id="e7d23-126">Ortalama işlevi çalışmak için giriş, örneğin, sorgu sonuçları ortalamasını bulmak için sorgu yürütülmelidir.</span><span class="sxs-lookup"><span data-stu-id="e7d23-126">For example, in order to find the average of the query results the query must be executed so that the averaging function has input data to work with.</span></span> <span data-ttu-id="e7d23-127">Aynı zamanda <xref:System.Linq.Enumerable.ToList%2A> veya <xref:System.Linq.Enumerable.ToArray%2A> bir tek değer üretmez bir sorgu hemen yürütülmesi zorlamak için bir sorgu yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="e7d23-127">You can also use the <xref:System.Linq.Enumerable.ToList%2A> or <xref:System.Linq.Enumerable.ToArray%2A> methods on a query to force immediate execution of a query that does not produce a singleton value.</span></span> <span data-ttu-id="e7d23-128">Bir sorgunun sonuçlarını önbelleğe almak istediğiniz zaman hemen yürütme zorlamak için bu teknikler yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e7d23-128">These techniques to force immediate execution can be useful when you want to cache the results of a query.</span></span> <span data-ttu-id="e7d23-129">Ertelenmiş ve hemen sorgu yürütme hakkında daha fazla bilgi için bkz: [LINQ ile çalışmaya başlama](http://msdn.microsoft.com/en-us/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9).</span><span class="sxs-lookup"><span data-stu-id="e7d23-129">For more information about deferred and immediate query execution, see [Getting Started with LINQ](http://msdn.microsoft.com/en-us/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9).</span></span>  
  
## <a name="queries"></a><span data-ttu-id="e7d23-130">Sorgular</span><span class="sxs-lookup"><span data-stu-id="e7d23-130">Queries</span></span>  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="e7d23-131">sorgu içinde iki farklı sözdizimi şeklide: Sorgu ifade sözdizimi ve yöntem temelli sorgu sözdizimi.</span><span class="sxs-lookup"><span data-stu-id="e7d23-131"> queries can be formulated in two different syntaxes: query expression syntax and method-based query syntax.</span></span>  
  
### <a name="query-expression-syntax"></a><span data-ttu-id="e7d23-132">Sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e7d23-132">Query Expression Syntax</span></span>  
 <span data-ttu-id="e7d23-133">Sorgu ifadeleri bildirim temelli sorgu söz dizimi ' dir.</span><span class="sxs-lookup"><span data-stu-id="e7d23-133">Query expressions are a declarative query syntax.</span></span> <span data-ttu-id="e7d23-134">Bu sözdiziminin sorguları SQL benzer bir biçimde C# veya Visual Basic yazmak bir geliştirici sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7d23-134">This syntax enables a developer to write queries in C# or Visual Basic in a format similar to SQL.</span></span> <span data-ttu-id="e7d23-135">Sorgu ifade sözdizimini kullanarak, daha karmaşık filtreleme, sıralama ve veri kaynaklarında çok az kod ile gruplandırma işlemleri gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="e7d23-135">By using query expression syntax, you can perform even complex filtering, ordering, and grouping operations on data sources with minimal code.</span></span> <span data-ttu-id="e7d23-136">Daha fazla bilgi için bkz: [LINQ Sorgu ifadeleri](http://msdn.microsoft.com/library/40638f19-fb46-4d26-a2d9-a383b48f5ed4) ve [temel sorgu işlemleri (Visual Basic)](~/docs/visual-basic/programming-guide/concepts/linq/basic-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="e7d23-136">For more information, see [LINQ Query Expressions](http://msdn.microsoft.com/library/40638f19-fb46-4d26-a2d9-a383b48f5ed4) and [Basic Query Operations (Visual Basic)](~/docs/visual-basic/programming-guide/concepts/linq/basic-query-operations.md).</span></span>  
  
 <span data-ttu-id="e7d23-137">C# 3. 0'sorgu ifade sözdizimi yenidir ve [!INCLUDE[vb_orcas_long](../../../../includes/vb-orcas-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e7d23-137">Query expression syntax is new in C# 3.0 and [!INCLUDE[vb_orcas_long](../../../../includes/vb-orcas-long-md.md)].</span></span> <span data-ttu-id="e7d23-138">Ancak, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ortak dil çalışma zamanı (CLR), sorgu ifade sözdizimi kendisini okuyamıyor.</span><span class="sxs-lookup"><span data-stu-id="e7d23-138">However, the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] common language runtime (CLR) cannot read the query expression syntax itself.</span></span> <span data-ttu-id="e7d23-139">Bu nedenle, derleme zamanında sorgu ifadeleri bir şeye CLR anlamak çevrilebilir: yöntem çağrıları.</span><span class="sxs-lookup"><span data-stu-id="e7d23-139">Therefore, at compile time, query expressions are translated to something that the CLR does understand: method calls.</span></span> <span data-ttu-id="e7d23-140">Bu yöntemler denir *standart sorgu işleçleri*.</span><span class="sxs-lookup"><span data-stu-id="e7d23-140">These methods are referred to as the *standard query operators*.</span></span> <span data-ttu-id="e7d23-141">Bir geliştirici olarak doğrudan sorgu sözdizimini kullanarak yerine yöntemi sözdizimini kullanarak çağırma seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="e7d23-141">As a developer, you have the option of calling them directly by using method syntax, instead of using query syntax.</span></span> <span data-ttu-id="e7d23-142">Daha fazla bilgi için bkz: [sorgu sözdizimi ve yöntem sözdizimi LINQ](~/docs/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).</span><span class="sxs-lookup"><span data-stu-id="e7d23-142">For more information, see [Query Syntax and Method Syntax in LINQ](~/docs/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).</span></span> <span data-ttu-id="e7d23-143">Standart sorgu işleçleri kullanma hakkında daha fazla bilgi için bkz: [NOT ın yapı: LINQ genel programlama kılavuzu](http://msdn.microsoft.com/en-us/609c7a6b-cbdd-429d-99f3-78d13d3bc049).</span><span class="sxs-lookup"><span data-stu-id="e7d23-143">For more information about how to use the standard query operators, see [NOT IN BUILD: LINQ General Programming Guide](http://msdn.microsoft.com/en-us/609c7a6b-cbdd-429d-99f3-78d13d3bc049).</span></span>  
  
 <span data-ttu-id="e7d23-144">Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.Select%2A> bulunan tüm satırlar döndürülecek `Product` tablo ve ürün adlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e7d23-144">The following example uses <xref:System.Linq.Enumerable.Select%2A> to return all the rows from `Product` table and display the product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="method-based-query-syntax"></a><span data-ttu-id="e7d23-145">Yöntem temelli sorgu söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e7d23-145">Method-Based Query Syntax</span></span>  
 <span data-ttu-id="e7d23-146">Formüle başka bir şekilde [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorguları kullanmaktır yöntem temelli sorgular.</span><span class="sxs-lookup"><span data-stu-id="e7d23-146">The other way to formulate [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] queries is by using method-based queries.</span></span> <span data-ttu-id="e7d23-147">Yöntem temelli sorgu sözdizimini doğrudan yöntem çağrılarını dizisidir [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] lambda ifadeleri parametre olarak geçirme işleci yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="e7d23-147">The method-based query syntax is a sequence of direct method calls to [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] operator methods, passing lambda expressions as the parameters.</span></span> <span data-ttu-id="e7d23-148">Daha fazla bilgi için bkz: [Lambda ifadeleri](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="e7d23-148">For more information, see [Lambda Expressions](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="e7d23-149">Bu örnekte <xref:System.Linq.Enumerable.Select%2A> bulunan tüm satırlar döndürülecek `Product` ve ürün adlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e7d23-149">This example uses <xref:System.Linq.Enumerable.Select%2A> to return all the rows from `Product` and display the product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
## <a name="composing-queries"></a><span data-ttu-id="e7d23-150">Sorgular oluşturma</span><span class="sxs-lookup"><span data-stu-id="e7d23-150">Composing Queries</span></span>  
 <span data-ttu-id="e7d23-151">Sorgu değerleri dizisi döndürmek üzere tasarlanmış, bu konuda daha önce belirtildiği gibi sorgu değişkeni yalnızca sorgu komutları depolar.</span><span class="sxs-lookup"><span data-stu-id="e7d23-151">As mentioned earlier in this topic, the query variable itself only stores the query commands when the query is designed to return a sequence of values.</span></span> <span data-ttu-id="e7d23-152">Sorgu hemen yürütme neden olacak bir yöntem içermiyorsa, gerçek sorgunun yürütülmesi, sorgu değişkeninde üzerinden yineleme kadar ertelenir bir `foreach` veya `For Each` döngü.</span><span class="sxs-lookup"><span data-stu-id="e7d23-152">If the query does not contain a method that will cause immediate execution, the actual execution of the query is deferred until you iterate over the query variable in a `foreach` or `For Each` loop.</span></span> <span data-ttu-id="e7d23-153">Ertelenmiş yürütme birleştirilecek birden çok sorgu veya bir sorgu genişletilmesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7d23-153">Deferred execution enables multiple queries to be combined or a query to be extended.</span></span> <span data-ttu-id="e7d23-154">Bir sorgu genişletildiğinde, yeni işlem içerecek şekilde değiştirilir ve son yürütme değişiklikleri yansıtır.</span><span class="sxs-lookup"><span data-stu-id="e7d23-154">When a query is extended, it is modified to include the new operations, and the eventual execution will reflect the changes.</span></span> <span data-ttu-id="e7d23-155">Aşağıdaki örnekte, tüm ürünleri ilk sorguyu döndürür.</span><span class="sxs-lookup"><span data-stu-id="e7d23-155">In the following example, the first query returns all the products.</span></span> <span data-ttu-id="e7d23-156">İkinci sorguyu kullanarak ilk genişletir `Where` "M" boyuttaki tüm ürünleri döndürmek için:</span><span class="sxs-lookup"><span data-stu-id="e7d23-156">The second query extends the first by using `Where` to return all the products of size "L":</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Composing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#composing)]
 [!code-vb[DP LINQ to DataSet Examples#Composing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#composing)]  
  
 <span data-ttu-id="e7d23-157">Sonra bir sorgu yürütüldükten, hiçbir ek sorgular oluşur ve izleyen tüm sorgular bellek içi kullanacağı [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] işleçler.</span><span class="sxs-lookup"><span data-stu-id="e7d23-157">After a query has been executed, no additional queries can be composed, and all subsequent queries will use the in-memory [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] operators.</span></span> <span data-ttu-id="e7d23-158">Sorgu yürütme sorgu değişkeninde üzerinden yineleme yaparken oluşacak bir `foreach` veya `For Each` deyimi veya biri için bir çağrı tarafından [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] hemen yürütme neden dönüşüm işleçleri.</span><span class="sxs-lookup"><span data-stu-id="e7d23-158">Query execution will occur when you iterate over the query variable in a `foreach` or `For Each` statement, or by a call to one of the [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] conversion operators that cause immediate execution.</span></span> <span data-ttu-id="e7d23-159">Bu işleçler şunlardır: <xref:System.Linq.Enumerable.ToList%2A>, <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToLookup%2A>, ve <xref:System.Linq.Enumerable.ToDictionary%2A>.</span><span class="sxs-lookup"><span data-stu-id="e7d23-159">These operators include the following: <xref:System.Linq.Enumerable.ToList%2A>, <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToLookup%2A>, and <xref:System.Linq.Enumerable.ToDictionary%2A>.</span></span>  
  
 <span data-ttu-id="e7d23-160">Aşağıdaki örnekte, ilk sorguyu fiyat listesi tarafından sıralanan tüm ürünleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="e7d23-160">In the following example, the first query returns all the products ordered by list price.</span></span> <span data-ttu-id="e7d23-161"><xref:System.Linq.Enumerable.ToArray%2A> Yöntemi hemen sorgu yürütme zorlamak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="e7d23-161">The <xref:System.Linq.Enumerable.ToArray%2A> method is used to force immediate query execution:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToArray2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#toarray2)]
 [!code-vb[DP LINQ to DataSet Examples#ToArray2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#toarray2)]  
  
## <a name="see-also"></a><span data-ttu-id="e7d23-162">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e7d23-162">See Also</span></span>  
 [<span data-ttu-id="e7d23-163">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e7d23-163">Programming Guide</span></span>](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
 [<span data-ttu-id="e7d23-164">Veri kümeleri sorgulama</span><span class="sxs-lookup"><span data-stu-id="e7d23-164">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [<span data-ttu-id="e7d23-165">C# üzerinde LINQ ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="e7d23-165">Getting Started with LINQ in C#</span></span>](~/docs/csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [<span data-ttu-id="e7d23-166">Visual Basic'te Lınq'e Başlarken</span><span class="sxs-lookup"><span data-stu-id="e7d23-166">Getting Started with LINQ in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)