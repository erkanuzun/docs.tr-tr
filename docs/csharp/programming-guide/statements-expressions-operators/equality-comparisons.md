---
title: "Eşitlik Karşılaştırmaları (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: object equality [C#]
ms.assetid: 10b865ea-4e7b-4127-9242-c9b8f57d9f04
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 199257b1fe371dea3e4ee1eedcf11f3bdce02366
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2017
---
# <a name="equality-comparisons-c-programming-guide"></a><span data-ttu-id="7132f-102">Eşitlik Karşılaştırmaları (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="7132f-102">Equality Comparisons (C# Programming Guide)</span></span>
<span data-ttu-id="7132f-103">Bazen, eşitlik için iki değerleri karşılaştırmak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7132f-103">It is sometimes necessary to compare two values for equality.</span></span> <span data-ttu-id="7132f-104">Bazı durumlarda için test ettiğiniz *değer eşitlik*, olarak da bilinen *eşdeğer*, iki değişken tarafından bulunan değerlerin eşit olup olmadığını anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7132f-104">In some cases, you are testing for *value equality*, also known as *equivalence*, which means that the values that are contained by the two variables are equal.</span></span> <span data-ttu-id="7132f-105">Diğer durumlarda, iki değişken aynı nesnesini bellekte başvurmak olup olmadığını belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7132f-105">In other cases, you have to determine whether two variables refer to the same underlying object in memory.</span></span> <span data-ttu-id="7132f-106">Bu tür bir eşitlik adlı *başvuru eşitliği*, veya *kimlik*.</span><span class="sxs-lookup"><span data-stu-id="7132f-106">This type of equality is called *reference equality*, or *identity*.</span></span> <span data-ttu-id="7132f-107">Bu konu, bu iki tür eşitlik açıklar ve daha fazla bilgi için diğer konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="7132f-107">This topic describes these two kinds of equality and provides links to other topics for more information.</span></span>  
  
## <a name="reference-equality"></a><span data-ttu-id="7132f-108">Başvuru eşitliği</span><span class="sxs-lookup"><span data-stu-id="7132f-108">Reference Equality</span></span>  
 <span data-ttu-id="7132f-109">Referans eşitlik iki nesne başvuruları aynı temel nesneye başvuran anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7132f-109">Reference equality means that two object references refer to the same underlying object.</span></span> <span data-ttu-id="7132f-110">Aşağıdaki örnekte gösterildiği gibi bu basit atama oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="7132f-110">This can occur through simple assignment, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideStatements#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/equality-comparisons_1.cs)]  
  
 <span data-ttu-id="7132f-111">Bu kodda, iki nesne oluşturulur, ancak atama deyimi sonra her iki başvuruları aynı nesneye başvurun.</span><span class="sxs-lookup"><span data-stu-id="7132f-111">In this code, two objects are created, but after the assignment statement, both references refer to the same object.</span></span> <span data-ttu-id="7132f-112">Bu nedenle başvuru eşitliği gerekir.</span><span class="sxs-lookup"><span data-stu-id="7132f-112">Therefore they have reference equality.</span></span> <span data-ttu-id="7132f-113">Kullanım <xref:System.Object.ReferenceEquals%2A> iki başvuruları aynı nesneye başvuran olup olmadığını belirlemek amacıyla yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7132f-113">Use the <xref:System.Object.ReferenceEquals%2A> method to determine whether two references refer to the same object.</span></span>  
  
 <span data-ttu-id="7132f-114">Referans eşitlik kavramı yalnızca başvuru türleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7132f-114">The concept of reference equality applies only to reference types.</span></span> <span data-ttu-id="7132f-115">Bir değişkene bir değer türü örneği atandığında, değerin bir kopyası oluşturulur çünkü değer türü nesneler başvuru eşitliği sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="7132f-115">Value type objects cannot have reference equality because when an instance of a value type is assigned to a variable, a copy of the value is made.</span></span> <span data-ttu-id="7132f-116">Bu nedenle, bellek aynı konumda başvurmak iki sarmalanmamış yapılar hiçbir zaman olabilir.</span><span class="sxs-lookup"><span data-stu-id="7132f-116">Therefore you can never have two unboxed structs that refer to the same location in memory.</span></span> <span data-ttu-id="7132f-117">Ayrıca, kullanırsanız <xref:System.Object.ReferenceEquals%2A> iki değer türleri karşılaştırmak için sonucu her zaman olacaktır `false`nesneleri bulunan değerlerin tüm aynı olsa bile.</span><span class="sxs-lookup"><span data-stu-id="7132f-117">Furthermore, if you use <xref:System.Object.ReferenceEquals%2A> to compare two value types, the result will always be `false`, even if the values that are contained in the objects are all identical.</span></span> <span data-ttu-id="7132f-118">Her bir değişken ayrı bir nesne örneğine Kutulu olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="7132f-118">This is because each variable is boxed into a separate object instance.</span></span> <span data-ttu-id="7132f-119">Daha fazla bilgi için bkz: [nasıl yapılır: (kimlik) başvuru eşitliği testi](../../../csharp/programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md).</span><span class="sxs-lookup"><span data-stu-id="7132f-119">For more information, see [How to: Test for Reference Equality (Identity)](../../../csharp/programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md).</span></span>  
  
## <a name="value-equality"></a><span data-ttu-id="7132f-120">Değer eşitliği</span><span class="sxs-lookup"><span data-stu-id="7132f-120">Value Equality</span></span>  
 <span data-ttu-id="7132f-121">Değer eşitliği iki nesnenin aynı değeri veya değerler içeren anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7132f-121">Value equality means that two objects contain the same value or values.</span></span> <span data-ttu-id="7132f-122">İçin basit değer türleri gibi [int](../../../csharp/language-reference/keywords/int.md) veya [bool](../../../csharp/language-reference/keywords/bool.md), testler için değer eşitliği kolay.</span><span class="sxs-lookup"><span data-stu-id="7132f-122">For primitive value types such as [int](../../../csharp/language-reference/keywords/int.md) or [bool](../../../csharp/language-reference/keywords/bool.md), tests for value equality are straightforward.</span></span> <span data-ttu-id="7132f-123">Kullanabileceğiniz [ == ](../../../csharp/language-reference/operators/equality-comparison-operator.md) aşağıdaki örnekte gösterildiği gibi işleci.</span><span class="sxs-lookup"><span data-stu-id="7132f-123">You can use the [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) operator, as shown in the following example.</span></span>  
  
```csharp  
int a = GetOriginalValue();  
int b = GetCurrentValue();  
  
// Test for value equality.   
if( b == a)   
{  
    // The two integers are equal.  
}  
```  
  
 <span data-ttu-id="7132f-124">Ne tür tanımlar anlamak gerektirdiğinden diğer çoğu türleri için değer eşitlik için test daha karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="7132f-124">For most other types, testing for value equality is more complex because it requires that you understand how the type defines it.</span></span> <span data-ttu-id="7132f-125">Sınıflar ve birden çok özellik veya alana sahip yapılar için değer eşitliği genellikle tüm alanları veya özellikleri aynı değere sahip anlamına tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="7132f-125">For classes and structs that have multiple fields or properties, value equality is often defined to mean that all fields or properties have the same value.</span></span> <span data-ttu-id="7132f-126">Örneğin, iki `Point` nesneleri için pointB.X pointA.X eşittir ve pointA.Y pointB.Y için eşit ise eşdeğer olarak tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="7132f-126">For example, two `Point` objects might be defined to be equivalent if pointA.X is equal to pointB.X and pointA.Y is equal to pointB.Y.</span></span>  
  
 <span data-ttu-id="7132f-127">Ancak, eşdeğer bir türdeki tüm alanları dayanması gereksinimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="7132f-127">However, there is no requirement that equivalence be based on all the fields in a type.</span></span> <span data-ttu-id="7132f-128">Bir alt kümesinde dayanabilir.</span><span class="sxs-lookup"><span data-stu-id="7132f-128">It can be based on a subset.</span></span> <span data-ttu-id="7132f-129">Sahibi olmadığınız türleri karşılaştırdığınızda, özellikle nasıl eşdeğer bu türü için tanımlı anlamak emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7132f-129">When you compare types that you do not own, you should make sure to understand specifically how equivalence is defined for that type.</span></span> <span data-ttu-id="7132f-130">Kendi sınıflar ve yapılar değer eşitliği tanımlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir tür için değer eşitliği tanımlama](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md).</span><span class="sxs-lookup"><span data-stu-id="7132f-130">For more information about how to define value equality in your own classes and structs, see [How to: Define Value Equality for a Type](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md).</span></span>  
  
### <a name="value-equality-for-floating-point-values"></a><span data-ttu-id="7132f-131">Kayan nokta değerleri için değer eşitliği</span><span class="sxs-lookup"><span data-stu-id="7132f-131">Value Equality for Floating Point Values</span></span>  
 <span data-ttu-id="7132f-132">Eşitlik karşılaştırmaları kayan noktası değerleri ([çift](../../../csharp/language-reference/keywords/double.md) ve [float](../../../csharp/language-reference/keywords/float.md)) imprecision noktası aritmetik ikili bilgisayarlarda kayan nedeniyle sorunludur.</span><span class="sxs-lookup"><span data-stu-id="7132f-132">Equality comparisons of floating point values ([double](../../../csharp/language-reference/keywords/double.md) and [float](../../../csharp/language-reference/keywords/float.md)) are problematic because of the imprecision of floating point arithmetic on binary computers.</span></span> <span data-ttu-id="7132f-133">Açıklamalar konusunda daha fazla bilgi için bkz: <xref:System.Double?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7132f-133">For more information, see the remarks in the topic <xref:System.Double?displayProperty=nameWithType>.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="7132f-134">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="7132f-134">Related Topics</span></span>  
  
|<span data-ttu-id="7132f-135">Başlık</span><span class="sxs-lookup"><span data-stu-id="7132f-135">Title</span></span>|<span data-ttu-id="7132f-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7132f-136">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="7132f-137">Nasıl yapılır: (kimlik) başvuru eşitliği testi</span><span class="sxs-lookup"><span data-stu-id="7132f-137">How to: Test for Reference Equality (Identity)</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md)|<span data-ttu-id="7132f-138">İki değişken başvuru eşitliği sahip olup olmadığınızı belirlemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="7132f-138">Describes how to determine whether two variables have reference equality.</span></span>|  
|[<span data-ttu-id="7132f-139">Nasıl yapılır: tür için değer eşitliği tanımlama</span><span class="sxs-lookup"><span data-stu-id="7132f-139">How to: Define Value Equality for a Type</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md)|<span data-ttu-id="7132f-140">Bir tür için değer eşitliği özel bir tanımını sağlamak üzere açıklar.</span><span class="sxs-lookup"><span data-stu-id="7132f-140">Describes how to provide a custom definition of value equality for a type.</span></span>|  
|[<span data-ttu-id="7132f-141">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7132f-141">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)|<span data-ttu-id="7132f-142">Önemli C# dil özellikleri ve C# .NET çerçevesi aracılığıyla kullanılabilen özellikleri hakkında ayrıntılı bilgi için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="7132f-142">Provides links to detailed information about important C# language features and features that are available to C# through the .NET Framework.</span></span>|  
|[<span data-ttu-id="7132f-143">Türler</span><span class="sxs-lookup"><span data-stu-id="7132f-143">Types</span></span>](../../../csharp/programming-guide/types/index.md)|<span data-ttu-id="7132f-144">C# tür sistemi ve ek bilgilere bağlantılar hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7132f-144">Provides information about the C# type system and links to additional information.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7132f-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7132f-145">See Also</span></span>  
 [<span data-ttu-id="7132f-146">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7132f-146">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)