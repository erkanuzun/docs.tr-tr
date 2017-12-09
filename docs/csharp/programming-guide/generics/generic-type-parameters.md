---
title: "Genel Tür Parametreleri (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b32db7eb6e7788167e110a91726e9dbfe19f31ba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="generic-type-parameters-c-programming-guide"></a><span data-ttu-id="98e5f-102">Genel Tür Parametreleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="98e5f-102">Generic Type Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="98e5f-103">Genel tür veya yöntem tanımı, bir tür parametreleri bir yer tutucudur belirli türünün bir istemci olduğunda bunlar genel türünde bir değişken örneğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="98e5f-103">In a generic type or method definition, a type parameters is a placeholder for a specific type that a client specifies when they instantiate a variable of the generic type.</span></span> <span data-ttu-id="98e5f-104">Genel sınıf, gibi `GenericList<T>` listelenen [genel türlere giriş](../../../csharp/programming-guide/generics/introduction-to-generics.md), olarak kullanılamaz-çünkü bunu gerçekten bir tür değil; bir türü şeması gibi daha fazla.</span><span class="sxs-lookup"><span data-stu-id="98e5f-104">A generic class, such as `GenericList<T>` listed in [Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md), cannot be used as-is because it is not really a type; it is more like a blueprint for a type.</span></span> <span data-ttu-id="98e5f-105">Kullanılacak `GenericList<T>`, istemci kodu bildirme ve yapılandırılmış bir tür, tür bağımsız değişkeni köşeli ayraç içinde belirterek örneği.</span><span class="sxs-lookup"><span data-stu-id="98e5f-105">To use `GenericList<T>`, client code must declare and instantiate a constructed type by specifying a type argument inside the angle brackets.</span></span> <span data-ttu-id="98e5f-106">Tür bağımsız değişkeni belirli Bu sınıf için derleyici tarafından tanınan herhangi bir türü olabilir.</span><span class="sxs-lookup"><span data-stu-id="98e5f-106">The type argument for this particular class can be any type recognized by the compiler.</span></span> <span data-ttu-id="98e5f-107">Herhangi bir sayıda oluşturulan türü örnekleri, her biri farklı tür bağımsız değişkeni aşağıdaki gibi kullanarak oluşturulabilir:</span><span class="sxs-lookup"><span data-stu-id="98e5f-107">Any number of constructed type instances can be created, each one using a different type argument, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#7](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_1.cs)]  
  
 <span data-ttu-id="98e5f-108">Her bu örneklerinin `GenericList<T>`, her geçtiği `T` sınıfında çalışma zamanında tür bağımsız değişkeni ile değiştirilecektir.</span><span class="sxs-lookup"><span data-stu-id="98e5f-108">In each of these instances of `GenericList<T>`, every occurrence of `T` in the class will be substituted at run time with the type argument.</span></span> <span data-ttu-id="98e5f-109">Bu değiştirme yoluyla tek sınıf tanımını kullanarak üç ayrı tür kullanımı uyumlu ve verimli nesneleri oluşturduk.</span><span class="sxs-lookup"><span data-stu-id="98e5f-109">By means of this substitution, we have created three separate type-safe and efficient objects using a single class definition.</span></span> <span data-ttu-id="98e5f-110">Bu değiştirme CLR tarafından nasıl gerçekleştirildiğini daha fazla bilgi için bkz: [çalışma zamanı'nda genel türler](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span><span class="sxs-lookup"><span data-stu-id="98e5f-110">For more information on how this substitution is performed by the CLR, see [Generics in the Run Time](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span></span>  
  
## <a name="type-parameter-naming-guidelines"></a><span data-ttu-id="98e5f-111">Adlandırma yönergeleri tür parametresi</span><span class="sxs-lookup"><span data-stu-id="98e5f-111">Type Parameter Naming Guidelines</span></span>  
  
-   <span data-ttu-id="98e5f-112">**Yapmak** tamamen kendi kendine açıklama ve açıklayıcı bir ad, değer Ekle değil tek harf adı sürece genel tür parametreleri açıklayıcı adlar ile adı.</span><span class="sxs-lookup"><span data-stu-id="98e5f-112">**Do** name generic type parameters with descriptive names, unless a single letter name is completely self explanatory and a descriptive name would not add value.</span></span>  
  
     [!code-csharp[csProgGuideGenerics#8](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_2.cs)]  
  
-   <span data-ttu-id="98e5f-113">**Göz önünde bulundurun** T tek tek harf tür parametresi türleriyle türü parametre adı olarak kullanma.</span><span class="sxs-lookup"><span data-stu-id="98e5f-113">**Consider** using T as the type parameter name for types with one single letter type parameter.</span></span>  
  
     [!code-csharp[csProgGuideGenerics#9](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_3.cs)]  
  
-   <span data-ttu-id="98e5f-114">**Yapmak** tanımlayıcı türü parametre adları "T" ile önek.</span><span class="sxs-lookup"><span data-stu-id="98e5f-114">**Do** prefix descriptive type parameter names with "T".</span></span>  
  
     [!code-csharp[csProgGuideGenerics#10](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_4.cs)]  
  
-   <span data-ttu-id="98e5f-115">**Göz önünde bulundurun** kısıtlamaları belirten yerleştirilen bir tür parametresi parametre adına üzerinde.</span><span class="sxs-lookup"><span data-stu-id="98e5f-115">**Consider** indicating constraints placed on a type parameter in the name of parameter.</span></span> <span data-ttu-id="98e5f-116">Örneğin, bir parametre kısıtlı için `ISession` çağrılabilir `TSession`.</span><span class="sxs-lookup"><span data-stu-id="98e5f-116">For example, a parameter constrained to `ISession` may be called `TSession`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98e5f-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="98e5f-117">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="98e5f-118">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="98e5f-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="98e5f-119">Genel türler</span><span class="sxs-lookup"><span data-stu-id="98e5f-119">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)  
 [<span data-ttu-id="98e5f-120">C++ şablonları ve C# genel türleri arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="98e5f-120">Differences Between C++ Templates and C# Generics</span></span>](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)