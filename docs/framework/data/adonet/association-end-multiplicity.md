---
title: "İlişki uç Çokluk"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3d6071b2dfab4a1f057c9e04b84e1163fb0a53c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="association-end-multiplicity"></a><span data-ttu-id="85887-102">İlişki uç Çokluk</span><span class="sxs-lookup"><span data-stu-id="85887-102">association end multiplicity</span></span>
<span data-ttu-id="85887-103">*İlişki uç Çokluk* sayısını tanımlar [varlık türü](../../../../docs/framework/data/adonet/entity-type.md) bir sonunda olabilir örnekleri bir [ilişkilendirme](../../../../docs/framework/data/adonet/association-type.md).</span><span class="sxs-lookup"><span data-stu-id="85887-103">*Association end multiplicity* defines the number of [entity type](../../../../docs/framework/data/adonet/entity-type.md) instances that can be at one end of an [association](../../../../docs/framework/data/adonet/association-type.md).</span></span>  
  
 <span data-ttu-id="85887-104">Bir ilişkilendirme end Çokluk şu değerlerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="85887-104">An association end multiplicity can have one of the following values:</span></span>  
  
-   <span data-ttu-id="85887-105">bir (1): Bu tam olarak bir varlık türü örneği var ilişkisi sonunda gösterir.</span><span class="sxs-lookup"><span data-stu-id="85887-105">one (1): Indicates that exactly one entity type instance exists at the association end.</span></span>  
  
-   <span data-ttu-id="85887-106">sıfır veya bir (0.. 1 çokluğa): sıfır veya bir varlık türü örnekleri ilişkilendirme sonunda mevcut olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="85887-106">zero or one (0..1): Indicates that zero or one entity type instances exist at the association end.</span></span>  
  
-   <span data-ttu-id="85887-107">birçok (*): sıfır, bir veya daha fazla varlık türü örnekleri ilişkilendirme sonunda mevcut olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="85887-107">many (*): Indicates that zero, one, or more entity type instances exist at the association end.</span></span>  
  
 <span data-ttu-id="85887-108">Bir ilişkilendirme genellikle kendi ilişkilendirme son Çeşitlilikler tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="85887-108">An association is often characterized by its association end multiplicities.</span></span> <span data-ttu-id="85887-109">Örneğin, bir ilişki uçlarından biri (1) ve çok sayıda Çeşitlilikler (*) varsa, ilişki bir-çok ilişkisi adı verilir.</span><span class="sxs-lookup"><span data-stu-id="85887-109">For example, if the ends of an association have multiplicities one (1) and many (*), the association is called a one-to-many association.</span></span> <span data-ttu-id="85887-110">Aşağıdaki örnekte `PublishedBy` ilişkilendirmedir bir-çok ilişkisi (birçok books yayımcı yayımlar ve kitap bir yayımcı tarafından yayımlanan).</span><span class="sxs-lookup"><span data-stu-id="85887-110">In the example below, the `PublishedBy` association is a one-to-many association (a publisher publishes many books and a book is published by one publisher).</span></span> <span data-ttu-id="85887-111">`WrittenBy` İlişkilendirmedir bir çok-çok ilişkisi (kitap birden çok yazar olabilir ve bir yazar birden çok books yazabilirsiniz).</span><span class="sxs-lookup"><span data-stu-id="85887-111">The `WrittenBy` association is a many-to-many association (a book can have multiple authors and an author can write multiple books).</span></span>  
  
## <a name="example"></a><span data-ttu-id="85887-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="85887-112">Example</span></span>  
 <span data-ttu-id="85887-113">Aşağıdaki diyagramda iki ilişkilendirmeleri kavramsal modelle gösterir: `PublishedBy` ve `WrittenBy`.</span><span class="sxs-lookup"><span data-stu-id="85887-113">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="85887-114">İlişkilendirme sona `PublishedBy` ilişkisi olan `Book` ve `Publisher` varlık türleri.</span><span class="sxs-lookup"><span data-stu-id="85887-114">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="85887-115">Çokluğu `Publisher` sonudur bir (1) ve çokluğu `Book` sonudur birçok (*).</span><span class="sxs-lookup"><span data-stu-id="85887-115">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (*).</span></span>  
  
 <span data-ttu-id="85887-116">![Örnek modeli](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="85887-116">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="85887-117">Kavramsal şema tanım dili adlı bir etki alanına özgü dil (DSL) ADO.NET Entity Framework kullanır ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) kavramsal modeller tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="85887-117">The ADO.NET Entity Framework uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="85887-118">Aşağıdaki CSDL tanımlar `PublishedBy` Yukarıdaki diyagramda gösterildiği ilişkilendirme:</span><span class="sxs-lookup"><span data-stu-id="85887-118">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="85887-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="85887-119">See Also</span></span>  
 [<span data-ttu-id="85887-120">Varlık veri modeli temel kavramları</span><span class="sxs-lookup"><span data-stu-id="85887-120">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="85887-121">Varlık veri modeli</span><span class="sxs-lookup"><span data-stu-id="85887-121">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)