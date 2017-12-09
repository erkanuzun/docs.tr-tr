---
title: "İç içe geçmiş varlık SQL sorguları oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 175affdd8e9763f6cc7d0c48c38498af6e8ffabb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="composing-nested-entity-sql-queries"></a><span data-ttu-id="55d5d-102">İç içe geçmiş varlık SQL sorguları oluşturma</span><span class="sxs-lookup"><span data-stu-id="55d5d-102">Composing Nested Entity SQL Queries</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="55d5d-103">bir zengin işlevsel dilidir.</span><span class="sxs-lookup"><span data-stu-id="55d5d-103"> is a rich functional language.</span></span> <span data-ttu-id="55d5d-104">Yapı bloğu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="55d5d-104">The building block of [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is an expression.</span></span> <span data-ttu-id="55d5d-105">Geleneksel SQL aksine [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir tablo sonuç kümesi sınırlı değildir: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] değişmez değerleri, parametre veya iç içe geçmiş ifadeler olabilir karmaşık ifadeler oluşturmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="55d5d-105">Unlike conventional SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not limited to a tabular result set: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] supports composing complex expressions that can have literals, parameters, or nested expressions.</span></span> <span data-ttu-id="55d5d-106">İfade bir değer parametreli veya diğer bazı ifadesi oluşur.</span><span class="sxs-lookup"><span data-stu-id="55d5d-106">A value in the expression can be parameterized or composed of some other expression.</span></span>  
  
## <a name="nested-expressions"></a><span data-ttu-id="55d5d-107">İç içe geçmiş ifadeler</span><span class="sxs-lookup"><span data-stu-id="55d5d-107">Nested Expressions</span></span>  
 <span data-ttu-id="55d5d-108">İç içe geçmiş bir ifade, kabul edilen döndürür türünde bir değer herhangi bir yere yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="55d5d-108">A nested expression can be placed anywhere a value of the type it returns is accepted.</span></span> <span data-ttu-id="55d5d-109">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="55d5d-109">For example:</span></span>  
  
```  
-- Returns a hierarchical collection of three elements at top-level.   
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 <span data-ttu-id="55d5d-110">İç içe bir sorgu projeksiyon yan tümcesinde yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="55d5d-110">A nested query can be placed in a projection clause.</span></span> <span data-ttu-id="55d5d-111">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="55d5d-111">For example:</span></span>  
  
```  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)   
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)   
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 <span data-ttu-id="55d5d-112">İçinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)], iç içe geçmiş sorgular parantez içinde her zaman alınmalıdır:</span><span class="sxs-lookup"><span data-stu-id="55d5d-112">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], nested queries must always be enclosed in parentheses:</span></span>  
  
```  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 <span data-ttu-id="55d5d-113">Aşağıdaki örnek düzgün ifadelerinde iç içe gösterilmiştir [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [nasıl yapılır: birleşim, iki sorguları sipariş](http://msdn.microsoft.com/en-us/853c583a-eaba-4400-830d-be974e735313).</span><span class="sxs-lookup"><span data-stu-id="55d5d-113">The following example demonstrates how to properly nest expressions in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [How to: Order the Union of Two Queries](http://msdn.microsoft.com/en-us/853c583a-eaba-4400-830d-be974e735313).</span></span>  
  
## <a name="nested-queries-in-projection"></a><span data-ttu-id="55d5d-114">İç içe yerleştirilmiş sorguda projeksiyon</span><span class="sxs-lookup"><span data-stu-id="55d5d-114">Nested Queries in Projection</span></span>  
 <span data-ttu-id="55d5d-115">Proje yan tümcesi iç içe geçmiş sorguları Kartezyen ürün sorguları sunucuda içine çevrilmiş.</span><span class="sxs-lookup"><span data-stu-id="55d5d-115">Nested queries in the project clause might get translated into Cartesian product queries on the server.</span></span> <span data-ttu-id="55d5d-116">SQL Server dahil olmak üzere bazı arka uç sunucularında, bu sunucu performansını olumsuz yönde etkilenebilir çok büyük almak TempDB tablo neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="55d5d-116">In some backend servers, including SLQ Server, this can cause the TempDB table to get very large, which can adversely affect server performance.</span></span>  
  
 <span data-ttu-id="55d5d-117">Bu tür bir sorgunun bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="55d5d-117">The following is an example of such a query:</span></span>  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="55d5d-118">İç içe geçmiş sorgular sıralama</span><span class="sxs-lookup"><span data-stu-id="55d5d-118">Ordering Nested Queries</span></span>  
 <span data-ttu-id="55d5d-119">Entity Framework iç içe geçmiş bir ifade herhangi bir yere sorguda yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="55d5d-119">In the Entity Framework, a nested expression can be placed anywhere in the query.</span></span> <span data-ttu-id="55d5d-120">Varlık SQL sorguları yazma büyük esneklik izin verdiğinden, bir iç içe geçmiş sorguları sıralama içeren bir sorgu yazmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="55d5d-120">Because Entity SQL allows great flexibility in writing queries, it is possible to write a query that contains an ordering of nested queries.</span></span> <span data-ttu-id="55d5d-121">Ancak, iç içe bir sorgu sırası korunmaz.</span><span class="sxs-lookup"><span data-stu-id="55d5d-121">However, the order of a nested query is not preserved.</span></span>  
  
```  
-- The following query will order the results by last name.  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query, ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="see-also"></a><span data-ttu-id="55d5d-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="55d5d-122">See Also</span></span>  
 [<span data-ttu-id="55d5d-123">Varlık SQL genel bakış</span><span class="sxs-lookup"><span data-stu-id="55d5d-123">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)