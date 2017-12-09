---
title: "Nasıl yapılır: Veritabanı değişiklikleri gönderme"
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
ms.assetid: c7cba174-9d40-491d-b32c-f2d73b7e9eab
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 039eaac26833651fbd82dc1a69a31f394c1464c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-submit-changes-to-the-database"></a><span data-ttu-id="f66d7-102">Nasıl yapılır: Veritabanı değişiklikleri gönderme</span><span class="sxs-lookup"><span data-stu-id="f66d7-102">How to: Submit Changes to the Database</span></span>
<span data-ttu-id="f66d7-103">Nesnelerinizi kaç değişiklikler bağımsız olarak, değişiklikler yalnızca bellek içi çoğaltmalar için yapılır.</span><span class="sxs-lookup"><span data-stu-id="f66d7-103">Regardless of how many changes you make to your objects, changes are made only to in-memory replicas.</span></span> <span data-ttu-id="f66d7-104">Veritabanındaki gerçek veriler için herhangi bir değişiklik yaptınız.</span><span class="sxs-lookup"><span data-stu-id="f66d7-104">You have made no changes to the actual data in the database.</span></span> <span data-ttu-id="f66d7-105">Açıkça çağrısı tamamlanana kadar değişiklikleriniz sunucusuna iletilmez <xref:System.Data.Linq.DataContext.SubmitChanges%2A> üzerinde <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="f66d7-105">Your changes are not transmitted to the server until you explicitly call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="f66d7-106">Bu arama yaparken <xref:System.Data.Linq.DataContext> değişikliklerinizi eşdeğer SQL komutlarını içine çevirmek çalışır.</span><span class="sxs-lookup"><span data-stu-id="f66d7-106">When you make this call, the <xref:System.Data.Linq.DataContext> tries to translate your changes into equivalent SQL commands.</span></span> <span data-ttu-id="f66d7-107">Bu eylemler geçersiz kılmak için kendi özel mantık kullanabilirsiniz, ancak gönderme sırası bir hizmet tarafından düzenlenmiş <xref:System.Data.Linq.DataContext> olarak bilinen *işlemci değiştirmek*.</span><span class="sxs-lookup"><span data-stu-id="f66d7-107">You can use your own custom logic to override these actions, but the order of submission is orchestrated by a service of the <xref:System.Data.Linq.DataContext> known as the *change processor*.</span></span> <span data-ttu-id="f66d7-108">Olayların sırası aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="f66d7-108">The sequence of events is as follows:</span></span>  
  
1.  <span data-ttu-id="f66d7-109">Çağırdığınızda <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yeni örnekleri kendisine eklenmiş olan olup olmadığını belirlemek için bilinen nesne kümesini inceler.</span><span class="sxs-lookup"><span data-stu-id="f66d7-109">When you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] examines the set of known objects to determine whether new instances have been attached to them.</span></span> <span data-ttu-id="f66d7-110">Varsa, bu yeni örnekler izlenen nesneler kümesine eklenir.</span><span class="sxs-lookup"><span data-stu-id="f66d7-110">If they have, these new instances are added to the set of tracked objects.</span></span>  
  
2.  <span data-ttu-id="f66d7-111">Bekleyen değişiklikleri bulunan tüm nesneleri aralarındaki bağımlılıkları temel nesneleri dizisini içine sıralanır.</span><span class="sxs-lookup"><span data-stu-id="f66d7-111">All objects that have pending changes are ordered into a sequence of objects based on the dependencies between them.</span></span> <span data-ttu-id="f66d7-112">Değişiklikleri bağımlı nesneler üzerinde nesneleri bağımlılıklarını sonra sıralanamadı.</span><span class="sxs-lookup"><span data-stu-id="f66d7-112">Objects whose changes depend on other objects are sequenced after their dependencies.</span></span>  
  
3.  <span data-ttu-id="f66d7-113">Gerçek değişiklikleri hemen iletilmeden önce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tekil komutlar dizi kapsülleyen bir işlem başlatır.</span><span class="sxs-lookup"><span data-stu-id="f66d7-113">Immediately before any actual changes are transmitted, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] starts a transaction to encapsulate the series of individual commands.</span></span>  
  
4.  <span data-ttu-id="f66d7-114">Nesnelere değişiklikler çevrilmiş tek tek SQL komutları ve sunucuya gönderilen.</span><span class="sxs-lookup"><span data-stu-id="f66d7-114">The changes to the objects are translated one by one to SQL commands and sent to the server.</span></span>  
  
 <span data-ttu-id="f66d7-115">Bu noktada, veritabanı tarafından algılanan tüm hataları gönderme işleminin vermemesine neden ve özel durum oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="f66d7-115">At this point, any errors detected by the database cause the submission process to stop, and an exception is raised.</span></span> <span data-ttu-id="f66d7-116">Veritabanında yapılan tüm değişiklikler geri hiçbir gönderimlerini sürekli olarak oluştuysa alınır.</span><span class="sxs-lookup"><span data-stu-id="f66d7-116">All changes to the database are rolled back as if no submissions ever occurred.</span></span> <span data-ttu-id="f66d7-117"><xref:System.Data.Linq.DataContext> Tüm değişiklikleri tam kaydını sürdürüyor.</span><span class="sxs-lookup"><span data-stu-id="f66d7-117">The <xref:System.Data.Linq.DataContext> still has a full recording of all changes.</span></span> <span data-ttu-id="f66d7-118">Bu nedenle çağrısı ve sorunu düzeltmek deneyebilirsiniz <xref:System.Data.Linq.DataContext.SubmitChanges%2A> yeniden, aşağıdaki kod örneğinde olduğu gibi.</span><span class="sxs-lookup"><span data-stu-id="f66d7-118">You can therefore try to correct the problem and call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> again, as in the code example that follows.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f66d7-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="f66d7-119">Example</span></span>  
 <span data-ttu-id="f66d7-120">Gönderme işlemi başarıyla tamamlandığında, <xref:System.Data.Linq.DataContext> değişiklik izleme bilgilerini yoksayarak tarafından yapılan değişiklikleri nesneleri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="f66d7-120">When the transaction around the submission is completed successfully, the <xref:System.Data.Linq.DataContext> accepts the changes to the objects by ignoring the change-tracking information.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#1)]
 [!code-vb[DLinqSubmittingChanges#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f66d7-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f66d7-121">See Also</span></span>  
 [<span data-ttu-id="f66d7-122">Nasıl yapılır: algılamak ve çakışan gönderimlerini gidermek</span><span class="sxs-lookup"><span data-stu-id="f66d7-122">How to: Detect and Resolve Conflicting Submissions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-detect-and-resolve-conflicting-submissions.md)  
 [<span data-ttu-id="f66d7-123">Nasıl yapılır: değişiklik çakışmalarını yönetin</span><span class="sxs-lookup"><span data-stu-id="f66d7-123">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [<span data-ttu-id="f66d7-124">Örnek veritabanları yükleme</span><span class="sxs-lookup"><span data-stu-id="f66d7-124">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [<span data-ttu-id="f66d7-125">Sağlama ve veri değişiklikleri gönderme</span><span class="sxs-lookup"><span data-stu-id="f66d7-125">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)