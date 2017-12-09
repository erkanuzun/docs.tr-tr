---
title: "Nasıl yapılır: veritabanına Satır Ekle"
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
ms.assetid: 44d99680-69c7-4879-a732-f6771b334211
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a96a0ab800076db16022f5b02c84d7a53ca99147
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-insert-rows-into-the-database"></a><span data-ttu-id="bb64e-102">Nasıl yapılır: veritabanına Satır Ekle</span><span class="sxs-lookup"><span data-stu-id="bb64e-102">How to: Insert Rows Into the Database</span></span>
<span data-ttu-id="bb64e-103">Nesneleri ile ilişkili için ekleyerek bir veritabanına Satır Ekle [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> toplama ve değişiklikler veritabanına gönderiliyor.</span><span class="sxs-lookup"><span data-stu-id="bb64e-103">You insert rows into a database by adding objects to the associated [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="bb64e-104">Değişikliklerinizi uygun SQL içine çevirir `INSERT` komutları.</span><span class="sxs-lookup"><span data-stu-id="bb64e-104"> translates your changes into the appropriate SQL `INSERT` commands.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bb64e-105">Geçersiz kılabilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] varsayılan yöntemlerini `Insert`, `Update`, ve `Delete` veritabanı işlemleri.</span><span class="sxs-lookup"><span data-stu-id="bb64e-105">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="bb64e-106">Daha fazla bilgi için bkz: [özelleştirme ekleme, güncelleştirme ve silme işlemleri](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="bb64e-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="bb64e-107">Kullanan geliştiriciler [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] kullanabilirsiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] aynı amaçla saklı yordamlar geliştirilir.</span><span class="sxs-lookup"><span data-stu-id="bb64e-107">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to develop stored procedures for the same purpose.</span></span>  
  
 <span data-ttu-id="bb64e-108">Aşağıdaki adımlarda varsayılmaktadır geçerli bir <xref:System.Data.Linq.DataContext> Northwind veritabanına bağlar.</span><span class="sxs-lookup"><span data-stu-id="bb64e-108">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="bb64e-109">Daha fazla bilgi için bkz: [nasıl yapılır: bir veritabanına bağlanmak](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="bb64e-109">For more information, see [How to: Connect to a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span></span>  
  
### <a name="to-insert-a-row-into-the-database"></a><span data-ttu-id="bb64e-110">Veritabanına bir satır eklemek için</span><span class="sxs-lookup"><span data-stu-id="bb64e-110">To insert a row into the database</span></span>  
  
1.  <span data-ttu-id="bb64e-111">Gönderilecek sütun verileri içeren yeni bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bb64e-111">Create a new object that includes the column data to be submitted.</span></span>  
  
2.  <span data-ttu-id="bb64e-112">Yeni nesne için ekleme [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` veritabanındaki hedef tabloyla ilişkili koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="bb64e-112">Add the new object to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` collection associated with the target table in the database.</span></span>  
  
3.  <span data-ttu-id="bb64e-113">Veritabanı için değişiklik gönderin.</span><span class="sxs-lookup"><span data-stu-id="bb64e-113">Submit the change to the database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb64e-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="bb64e-114">Example</span></span>  
 <span data-ttu-id="bb64e-115">Aşağıdaki kod örneğinde türünde yeni bir nesne oluşturur `Order` ve uygun değerlerle doldurur.</span><span class="sxs-lookup"><span data-stu-id="bb64e-115">The following code example creates a new object of type `Order` and populates it with appropriate values.</span></span> <span data-ttu-id="bb64e-116">Ardından yeni nesneye ekler `Order` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="bb64e-116">It then adds the new object to the `Order` collection.</span></span> <span data-ttu-id="bb64e-117">Son olarak, yeni bir satır olarak değişiklik veritabanına gönderdiğinde `Orders` tablo.</span><span class="sxs-lookup"><span data-stu-id="bb64e-117">Finally, it submits the change to the database as a new row in the `Orders` table.</span></span>  
  
 [!code-csharp[System.Data.Linq.Table#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.Table#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="bb64e-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bb64e-118">See Also</span></span>  
 [<span data-ttu-id="bb64e-119">Nasıl yapılır: değişiklik çakışmalarını yönetin</span><span class="sxs-lookup"><span data-stu-id="bb64e-119">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [<span data-ttu-id="bb64e-120">DataContext yöntemleri (O/R Tasarımcısı)</span><span class="sxs-lookup"><span data-stu-id="bb64e-120">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [<span data-ttu-id="bb64e-121">Nasıl yapılır: güncelleştirme, ekleme ve silme (O/R Tasarımcısı) gerçekleştirmek için saklı yordamlar atayın</span><span class="sxs-lookup"><span data-stu-id="bb64e-121">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)  
 [<span data-ttu-id="bb64e-122">Sağlama ve veri değişiklikleri gönderme</span><span class="sxs-lookup"><span data-stu-id="bb64e-122">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)