---
title: "Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- access levels [Visual Basic], properties
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- mixed access levels
- Visual Basic code, properties
- properties [Visual Basic], access levels
- Property statement [Visual Basic], declaring mixed access levels
ms.assetid: fdbb2d97-279a-4956-b26c-cbdfbc34915a
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 90fe20303f6f2ed692e54e44ee8cc65897531543
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a><span data-ttu-id="1b687-102">Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b687-102">How to: Declare a Property with Mixed Access Levels (Visual Basic)</span></span>
<span data-ttu-id="1b687-103">İsterseniz `Get` ve `Set` yordamlarını bir özelliğe farklı erişim düzeyleri olması, daha fazla izin düzeyi kullanabilir `Property` deyimi ve ya da daha kısıtlayıcı düzeyi `Get` veya `Set` deyimi.</span><span class="sxs-lookup"><span data-stu-id="1b687-103">If you want the `Get` and `Set` procedures on a property to have different access levels, you can use the more permissive level in the `Property` statement and the more restrictive level in either the `Get` or `Set` statement.</span></span> <span data-ttu-id="1b687-104">Belirli özelliğin değerini almak kod parçalarını ve belirli bir değeri değiştirmek kod bölümlerini istediğinizde bir özelliği karışık erişim düzeyleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="1b687-104">You use mixed access levels on a property when you want certain parts of the code to be able to get the property's value, and certain other parts of the code to be able to change the value.</span></span>  
  
 <span data-ttu-id="1b687-105">Erişim düzeyleri hakkında daha fazla bilgi için bkz: [erişim düzeyini Visual Basic'te](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="1b687-105">For more information on access levels, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a><span data-ttu-id="1b687-106">Bir özelliği karışık erişim düzeyleriyle bildirme</span><span class="sxs-lookup"><span data-stu-id="1b687-106">To declare a property with mixed access levels</span></span>  
  
1.  <span data-ttu-id="1b687-107">Normal bir şekilde özelliği bildirme ve daha az kısıtlayıcı erişim düzeyini belirtin (gibi `Public`) içinde `Property` deyimi.</span><span class="sxs-lookup"><span data-stu-id="1b687-107">Declare the property in the normal way, and specify the less restrictive access level (such as `Public`) in the `Property` statement.</span></span>  
  
2.  <span data-ttu-id="1b687-108">Ya da bildirme `Get` veya `Set` daha kısıtlayıcı erişim düzeyini belirterek yordamı (gibi `Friend`).</span><span class="sxs-lookup"><span data-stu-id="1b687-108">Declare either the `Get` or the `Set` procedure specifying the more restrictive access level (such as `Friend`).</span></span>  
  
3.  <span data-ttu-id="1b687-109">Erişim düzeyi, bir özellik yordamı üzerinde belirtmeyin.</span><span class="sxs-lookup"><span data-stu-id="1b687-109">Do not specify an access level on the other property procedure.</span></span> <span data-ttu-id="1b687-110">Bildirilen erişim düzeyi varsayar `Property` deyimi.</span><span class="sxs-lookup"><span data-stu-id="1b687-110">It assumes the access level declared in the `Property` statement.</span></span> <span data-ttu-id="1b687-111">Özellik yordamları yalnızca birinde erişimi kısıtlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b687-111">You can restrict access on only one of the property procedures.</span></span>  
  
     [!code-vb[VbVbcnProcedures#10](./codesnippet/VisualBasic/how-to-declare-a-property-with-mixed-access-levels_1.vb)]  
  
     <span data-ttu-id="1b687-112">Önceki örnekte `Get` yordamı sahip aynı `Protected` özelliği kendisini olarak erişim sırada `Set` yordamı sahip `Private` erişim.</span><span class="sxs-lookup"><span data-stu-id="1b687-112">In the preceding example, the `Get` procedure has the same `Protected` access as the property itself, while the `Set` procedure has `Private` access.</span></span> <span data-ttu-id="1b687-113">Öğesinden türetilmiş bir sınıf `employee` okuyabilirsiniz `salary` değeri, ancak yalnızca `employee` sınıfı ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b687-113">A class derived from `employee` can read the `salary` value, but only the `employee` class can set it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b687-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1b687-114">See Also</span></span>  
 [<span data-ttu-id="1b687-115">Yordamları</span><span class="sxs-lookup"><span data-stu-id="1b687-115">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="1b687-116">Özellik yordamları</span><span class="sxs-lookup"><span data-stu-id="1b687-116">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="1b687-117">Parametreler ve bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="1b687-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="1b687-118">Property deyimi</span><span class="sxs-lookup"><span data-stu-id="1b687-118">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="1b687-119">Visual Basic'de özellikler ve değişkenler arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="1b687-119">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="1b687-120">Nasıl yapılır: özellik oluşturma</span><span class="sxs-lookup"><span data-stu-id="1b687-120">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="1b687-121">Nasıl yapılır: bir özellik yordamı çağırma</span><span class="sxs-lookup"><span data-stu-id="1b687-121">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)  
 [<span data-ttu-id="1b687-122">Nasıl yapılır: bildirme ve Visual Basic'te varsayılan özelliğini çağırın</span><span class="sxs-lookup"><span data-stu-id="1b687-122">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="1b687-123">Nasıl yapılır: bir özelliğe değer ekleme</span><span class="sxs-lookup"><span data-stu-id="1b687-123">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)  
 [<span data-ttu-id="1b687-124">Nasıl yapılır: bir özellikten değer alma</span><span class="sxs-lookup"><span data-stu-id="1b687-124">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)