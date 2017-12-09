---
title: "İç içe Geçmiş Türler (C# Programlama Kılavuzu)"
ms.date: 07/10/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ab13c68b638062ab89c90dbfc51b51b8d72d3bde
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="nested-types-c-programming-guide"></a><span data-ttu-id="2a4a3-102">İç içe Geçmiş Türler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="2a4a3-102">Nested Types (C# Programming Guide)</span></span>
<span data-ttu-id="2a4a3-103">İçinde tanımlanan bir türü bir [sınıfı](../../../csharp/language-reference/keywords/class.md) veya [yapısı](../../../csharp/language-reference/keywords/struct.md) iç içe geçmiş tür adı verilir.</span><span class="sxs-lookup"><span data-stu-id="2a4a3-103">A type defined within a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md) is called a nested type.</span></span> <span data-ttu-id="2a4a3-104">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="2a4a3-104">For example:</span></span>  
  
[!code-csharp[csProgGuideObjects#68](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_1.cs)]  
  
<span data-ttu-id="2a4a3-105">Dış türü bir sınıf veya yapı olup olmadığına bakılmaksızın, iç içe geçmiş türler için varsayılan değer [özel](../../../csharp/language-reference/keywords/private.md); yalnızca içeren kendi türünden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="2a4a3-105">Regardless of whether the outer type is a class or a struct, nested types default to [private](../../../csharp/language-reference/keywords/private.md); they are accessible only from their containing type.</span></span> <span data-ttu-id="2a4a3-106">Önceki örnekte, `Nested` sınıfı için dış türleri erişilemiyor.</span><span class="sxs-lookup"><span data-stu-id="2a4a3-106">In the previous example, the `Nested` class is inaccessible to external types.</span></span> 

<span data-ttu-id="2a4a3-107">Ayrıca belirtebilirsiniz bir [erişim değiştiricisi](../../language-reference/keywords/access-modifiers.md) iç içe geçmiş tür erişilebilirliğini şu şekilde tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="2a4a3-107">You can also specify an [access modifier](../../language-reference/keywords/access-modifiers.md) to define the accessibility of a nested type, as follows:</span></span>

- <span data-ttu-id="2a4a3-108">İç içe geçmiş tür bir **sınıfı** olabilir [ortak](../../../csharp/language-reference/keywords/public.md), [korumalı](../../../csharp/language-reference/keywords/protected.md), [iç](../../../csharp/language-reference/keywords/internal.md), [iç korumalı](../../../csharp/language-reference/keywords/protected-internal.md), [özel](../../../csharp/language-reference/keywords/private.md) veya [korumalı özel](../../../csharp/language-reference/keywords/private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="2a4a3-108">Nested types of a **class** can be [public](../../../csharp/language-reference/keywords/public.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), [protected internal](../../../csharp/language-reference/keywords/protected-internal.md), [private](../../../csharp/language-reference/keywords/private.md) or [private protected](../../../csharp/language-reference/keywords/private-protected.md).</span></span> 

   <span data-ttu-id="2a4a3-109">Ancak, tanımlama bir `protected`, `protected internal` veya `private protected` sınıf içinde iç içe geçmiş bir [sınıf korumalı](../../language-reference/keywords/sealed.md) derleyici uyarısı oluşturur [CS0628](../../misc/cs0628.md), "yeni korumalı üye korumalı sınıfta bildirildi."</span><span class="sxs-lookup"><span data-stu-id="2a4a3-109">However, defining a `protected`, `protected internal` or `private protected` nested class inside a [sealed class](../../language-reference/keywords/sealed.md) generates compiler warning [CS0628](../../misc/cs0628.md), "new protected member declared in sealed class."</span></span>
  
- <span data-ttu-id="2a4a3-110">İç içe geçmiş tür bir **yapısı** olabilir [ortak](../../../csharp/language-reference/keywords/public.md), [iç](../../../csharp/language-reference/keywords/internal.md), veya [özel](../../../csharp/language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="2a4a3-110">Nested types of a **struct** can be [public](../../../csharp/language-reference/keywords/public.md), [internal](../../../csharp/language-reference/keywords/internal.md), or [private](../../../csharp/language-reference/keywords/private.md).</span></span>
  
<span data-ttu-id="2a4a3-111">Aşağıdaki örnek yapar `Nested` sınıfı ortak:</span><span class="sxs-lookup"><span data-stu-id="2a4a3-111">The following example makes the `Nested` class public:</span></span>
  
[!code-csharp[csProgGuideObjects#69](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_2.cs)]  
  
 <span data-ttu-id="2a4a3-112">İç içe ya da iç, türü içeren veya dış, türü erişebilir.</span><span class="sxs-lookup"><span data-stu-id="2a4a3-112">The nested, or inner, type can access the containing, or outer, type.</span></span> <span data-ttu-id="2a4a3-113">Kapsayan tür erişmek için bağımsız değişken olarak iç içe geçmiş tür oluşturucuya geçirin.</span><span class="sxs-lookup"><span data-stu-id="2a4a3-113">To access the containing type, pass it as an argument to the constructor of the nested type.</span></span> <span data-ttu-id="2a4a3-114">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="2a4a3-114">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#70](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_3.cs)]  
  
 <span data-ttu-id="2a4a3-115">İç içe geçmiş tür içeren türünü erişilebilir üyelerin tümünü erişebilir.</span><span class="sxs-lookup"><span data-stu-id="2a4a3-115">A nested type has access to all of the members that are accessible to its containing type.</span></span> <span data-ttu-id="2a4a3-116">Devralınan tüm korumalı üyeleri de dahil olmak üzere içeren türün özel ve korumalı üyeleri erişebilir.</span><span class="sxs-lookup"><span data-stu-id="2a4a3-116">It can access private and protected members of the containing type, including any inherited protected members.</span></span>  
  
 <span data-ttu-id="2a4a3-117">Sınıfın tam adını önceki bildiriminde `Nested` olan `Container.Nested`.</span><span class="sxs-lookup"><span data-stu-id="2a4a3-117">In the previous declaration, the full name of class `Nested` is `Container.Nested`.</span></span> <span data-ttu-id="2a4a3-118">Bu, aşağıdaki gibi iç içe geçmiş sınıf yeni bir örneğini oluşturmak için kullanılan addır:</span><span class="sxs-lookup"><span data-stu-id="2a4a3-118">This is the name used to create a new instance of the nested class, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#71](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_4.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="2a4a3-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2a4a3-119">See Also</span></span>  
 [<span data-ttu-id="2a4a3-120">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2a4a3-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2a4a3-121">Sınıflar ve yapılar</span><span class="sxs-lookup"><span data-stu-id="2a4a3-121">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="2a4a3-122">Erişim değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="2a4a3-122">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="2a4a3-123">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="2a4a3-123">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)