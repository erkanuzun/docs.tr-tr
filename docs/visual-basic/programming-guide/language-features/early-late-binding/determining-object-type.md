---
title: "Nesne Türünü Belirleme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables [Visual Basic], testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9a63b5cf5941deb4dcc7518880b4dc7d0545803c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="determining-object-type-visual-basic"></a><span data-ttu-id="5eda6-102">Nesne Türünü Belirleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5eda6-102">Determining Object Type (Visual Basic)</span></span>
<span data-ttu-id="5eda6-103">Genel nesne değişkenleri (diğer bir deyişle, değişkenleri olarak bildirdiğiniz `Object`) herhangi bir sınıftan nesneleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="5eda6-103">Generic object variables (that is, variables you declare as `Object`) can hold objects from any class.</span></span> <span data-ttu-id="5eda6-104">Tür değişkenler kullanırken `Object`, nesne sınıfına göre farklı eylemleri gerekebilir; örneğin, bazı nesneler belirli özelliği veya yöntemi desteklemiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="5eda6-104">When using variables of type `Object`, you may need to take different actions based on the class of the object; for example, some objects might not support a particular property or method.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="5eda6-105">bir nesne değişkeninin hangi nesne türünü depolanan belirleme iki sağlar: `TypeName` işlevi ve `TypeOf...Is` işleci.</span><span class="sxs-lookup"><span data-stu-id="5eda6-105"> provides two means of determining which type of object is stored in an object variable: the `TypeName` function and the `TypeOf...Is` operator.</span></span>  
  
## <a name="typename-and-typeofis"></a><span data-ttu-id="5eda6-106">TypeName ve TypeOf... Değil</span><span class="sxs-lookup"><span data-stu-id="5eda6-106">TypeName and TypeOf…Is</span></span>  
 <span data-ttu-id="5eda6-107">`TypeName` İşlev bir dize döndürür ve aşağıdaki kod parçasında gösterildiği gibi bir nesne sınıf adını görüntülemek veya depolamak gereken en iyi seçimdir:</span><span class="sxs-lookup"><span data-stu-id="5eda6-107">The `TypeName` function returns a string and is the best choice when you need to store or display the class name of an object, as shown in the following code fragment:</span></span>  
  
 [!code-vb[VbVbalrOOP#92](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_1.vb)]  
  
 <span data-ttu-id="5eda6-108">`TypeOf...Is` İşlecidir nesnenin türü, test etmek için en iyi seçenek, bir eşdeğer dize karşılaştırma kullanmaktan çok daha hızlı olduğundan `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="5eda6-108">The `TypeOf...Is` operator is the best choice for testing an object's type, because it is much faster than an equivalent string comparison using `TypeName`.</span></span> <span data-ttu-id="5eda6-109">Aşağıdaki kod parçası kullanan `TypeOf...Is` içinde bir `If...Then...Else` deyimi:</span><span class="sxs-lookup"><span data-stu-id="5eda6-109">The following code fragment uses `TypeOf...Is` within an `If...Then...Else` statement:</span></span>  
  
 [!code-vb[VbVbalrOOP#93](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_2.vb)]  
  
 <span data-ttu-id="5eda6-110">Bir uyarı notu buraya son sözcüktür.</span><span class="sxs-lookup"><span data-stu-id="5eda6-110">A word of caution is due here.</span></span> <span data-ttu-id="5eda6-111">`TypeOf...Is` Operatörü döndürür `True` bir nesne belirli bir tür ya da belirli bir türden türetilmiş.</span><span class="sxs-lookup"><span data-stu-id="5eda6-111">The `TypeOf...Is` operator returns `True` if an object is of a specific type, or is derived from a specific type.</span></span> <span data-ttu-id="5eda6-112">Hemen bunu olan her şeyi [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] normalde dizeler ve tamsayılar gibi nesneler olarak düşünülen bazı öğeler içerir nesneleri içerir.</span><span class="sxs-lookup"><span data-stu-id="5eda6-112">Almost everything you do with [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] involves objects, which include some elements not normally thought of as objects, such as strings and integers.</span></span> <span data-ttu-id="5eda6-113">Bu nesneler türetilmiş ve yöntemleri devralır <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="5eda6-113">These objects are derived from and inherit methods from <xref:System.Object>.</span></span> <span data-ttu-id="5eda6-114">Geçirildiğinde bir `Integer` ve ile değerlendirilen `Object`, `TypeOf...Is` operatörü döndürür `True`.</span><span class="sxs-lookup"><span data-stu-id="5eda6-114">When passed an `Integer` and evaluated with `Object`, the `TypeOf...Is` operator returns `True`.</span></span> <span data-ttu-id="5eda6-115">Aşağıdaki örnek, rapor parametresi `InParam` hem de bir `Object` ve bir `Integer`:</span><span class="sxs-lookup"><span data-stu-id="5eda6-115">The following example reports that the parameter `InParam` is both an `Object` and an `Integer`:</span></span>  
  
 [!code-vb[VbVbalrOOP#94](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_3.vb)]  
  
 <span data-ttu-id="5eda6-116">Aşağıdaki örnek, her ikisi de kullanır `TypeOf...Is` ve `TypeName` kendisine geçirilen nesne türünü belirlemek için `Ctrl` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="5eda6-116">The following example uses both `TypeOf...Is` and `TypeName` to determine the type of object passed to it in the `Ctrl` argument.</span></span> <span data-ttu-id="5eda6-117">`TestObject` Yordam çağrıları `ShowType` üç farklı türde denetimleri ile.</span><span class="sxs-lookup"><span data-stu-id="5eda6-117">The `TestObject` procedure calls `ShowType` with three different kinds of controls.</span></span>  
  
#### <a name="to-run-the-example"></a><span data-ttu-id="5eda6-118">Örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="5eda6-118">To run the example</span></span>  
  
1.  <span data-ttu-id="5eda6-119">Yeni bir Windows uygulama projesi oluşturun ve ekleyin bir <xref:System.Windows.Forms.Button> denetimi, bir <xref:System.Windows.Forms.CheckBox> denetimi ve <xref:System.Windows.Forms.RadioButton> forma denetim.</span><span class="sxs-lookup"><span data-stu-id="5eda6-119">Create a new Windows Application project and add a <xref:System.Windows.Forms.Button> control, a <xref:System.Windows.Forms.CheckBox> control, and a <xref:System.Windows.Forms.RadioButton> control to the form.</span></span>  
  
2.  <span data-ttu-id="5eda6-120">Formunuzda düğmesinden çağrı `TestObject` yordamı.</span><span class="sxs-lookup"><span data-stu-id="5eda6-120">From the button on your form, call the `TestObject` procedure.</span></span>  
  
3.  <span data-ttu-id="5eda6-121">Formunuz için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5eda6-121">Add the following code to your form:</span></span>  
  
     [!code-vb[VbVbalrOOP#95](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5eda6-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5eda6-122">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Information.TypeName%2A>  
 [<span data-ttu-id="5eda6-123">Bir özelliği bir dize adı kullanarak veya yöntemi çağırma</span><span class="sxs-lookup"><span data-stu-id="5eda6-123">Calling a Property or Method Using a String Name</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)  
 [<span data-ttu-id="5eda6-124">Nesne veri türü</span><span class="sxs-lookup"><span data-stu-id="5eda6-124">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="5eda6-125">If... Then... Else deyimi</span><span class="sxs-lookup"><span data-stu-id="5eda6-125">If...Then...Else Statement</span></span>](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [<span data-ttu-id="5eda6-126">Dize veri türü</span><span class="sxs-lookup"><span data-stu-id="5eda6-126">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)  
 [<span data-ttu-id="5eda6-127">Integer veri türü</span><span class="sxs-lookup"><span data-stu-id="5eda6-127">Integer Data Type</span></span>](../../../../visual-basic/language-reference/data-types/integer-data-type.md)