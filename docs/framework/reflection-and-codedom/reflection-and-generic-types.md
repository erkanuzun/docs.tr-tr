---
title: "Yansıma ve Genel Türler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- generics [.NET Framework], reflection emit
- reflection emit, generic types
- reflection, generic types
- type arguments
- generics [.NET Framework], reflection
- viewing type information
- type information, viewing
- types, generic
- type parameters
ms.assetid: f7180fc5-dd41-42d4-8a8e-1b34288e06de
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 99d8da622b23a98b8a48ad6fcdb82c270d24ed22
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="reflection-and-generic-types"></a><span data-ttu-id="5a856-102">Yansıma ve Genel Türler</span><span class="sxs-lookup"><span data-stu-id="5a856-102">Reflection and Generic Types</span></span>
<a name="top"></a><span data-ttu-id="5a856-103">Yansıma point of görünümünü genel bir tür bir sıradan türü arasındaki fark (genel tür tanımında ise) genel bir tür ile türü parametreleri kümesini ilişkili olduğunu olan veya tür bağımsız değişkenleri (yapılandırılmış bir tür ise).</span><span class="sxs-lookup"><span data-stu-id="5a856-103">From the point of view of reflection, the difference between a generic type and an ordinary type is that a generic type has associated with it a set of type parameters (if it is a generic type definition) or type arguments (if it is a constructed type).</span></span> <span data-ttu-id="5a856-104">Genel yöntem aynı şekilde bir sıradan yönteminden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="5a856-104">A generic method differs from an ordinary method in the same way.</span></span>  
  
 <span data-ttu-id="5a856-105">Genel türler ve yöntemleri yansıma nasıl işlediğini anlamak için iki anahtar vardır:</span><span class="sxs-lookup"><span data-stu-id="5a856-105">There are two keys to understanding how reflection handles generic types and methods:</span></span>  
  
-   <span data-ttu-id="5a856-106">Genel tür tanımları ve genel yöntem tanımlarını tür parametrelerini örneği tarafından temsil edilen <xref:System.Type> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5a856-106">The type parameters of generic type definitions and generic method definitions are represented by instances of the <xref:System.Type> class.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5a856-107">Birçok özellikleri ve yöntemleri <xref:System.Type> farklı davranışa sahip olduğunda bir <xref:System.Type> nesnesini temsil eden bir genel tür parametresi.</span><span class="sxs-lookup"><span data-stu-id="5a856-107">Many properties and methods of <xref:System.Type> have different behavior when a <xref:System.Type> object represents a generic type parameter.</span></span> <span data-ttu-id="5a856-108">Bu farklılıklar, özellik ve yöntem konularında belgelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="5a856-108">These differences are documented in the property and method topics.</span></span> <span data-ttu-id="5a856-109">Örneğin, <xref:System.Type.IsAutoClass%2A> ve <xref:System.Type.DeclaringType%2A>.</span><span class="sxs-lookup"><span data-stu-id="5a856-109">For example, see <xref:System.Type.IsAutoClass%2A> and <xref:System.Type.DeclaringType%2A>.</span></span> <span data-ttu-id="5a856-110">Ayrıca, bazı yalnızca olduğunda geçerlidir üyeleridir bir <xref:System.Type> nesnesini temsil eden bir genel tür parametresi.</span><span class="sxs-lookup"><span data-stu-id="5a856-110">In addition, some members are valid only when a <xref:System.Type> object represents a generic type parameter.</span></span> <span data-ttu-id="5a856-111">Örneğin, <xref:System.Type.GetGenericTypeDefinition%2A>.</span><span class="sxs-lookup"><span data-stu-id="5a856-111">For example, see <xref:System.Type.GetGenericTypeDefinition%2A>.</span></span>  
  
-   <span data-ttu-id="5a856-112">Bir örneği varsa <xref:System.Type> tür parametreleri (için genel tür tanımları) veya tür bağımsız değişkenleri (oluşturulan türler) temsil eden türleri dizisi içerir sonra genel bir tür temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5a856-112">If an instance of <xref:System.Type> represents a generic type, then it includes an array of types that represent the type parameters (for generic type definitions) or the type arguments (for constructed types).</span></span> <span data-ttu-id="5a856-113">Aynı örneği geçerlidir <xref:System.Reflection.MethodInfo> genel yöntem temsil eden sınıf.</span><span class="sxs-lookup"><span data-stu-id="5a856-113">The same is true of an instance of the <xref:System.Reflection.MethodInfo> class that represents a generic method.</span></span>  
  
 <span data-ttu-id="5a856-114">Yansıma yöntemlerini sağlar <xref:System.Type> ve <xref:System.Reflection.MethodInfo> olanak tanıyacak şekilde tür parametreleri dizisi erişmek ve örneği olup olmadığını belirlemek için <xref:System.Type> bir tür parametresi veya gerçek bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5a856-114">Reflection provides methods of <xref:System.Type> and <xref:System.Reflection.MethodInfo> that allow you to access the array of type parameters, and to determine whether an instance of <xref:System.Type> represents a type parameter or an actual type.</span></span>  
  
 <span data-ttu-id="5a856-115">Örneğin bkz: Burada bahsedilen yöntemler gösteren kodu [nasıl yapılır: inceleyin ve Instantiate genel türleri yansıma ile](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="5a856-115">For example code demonstrating the methods discussed here, see [How to: Examine and Instantiate Generic Types with Reflection](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md).</span></span>  
  
 <span data-ttu-id="5a856-116">Aşağıdaki tartışma türü parametreler ve bağımsız değişkenler arasındaki farkı gibi genel türler terminolojisi aşina ve açık veya kapalı oluşturulan türler varsayar.</span><span class="sxs-lookup"><span data-stu-id="5a856-116">The following discussion assumes familiarity with the terminology of generics, such as the difference between type parameters and arguments and open or closed constructed types.</span></span> <span data-ttu-id="5a856-117">Daha fazla bilgi için bkz: [genel türler](../../../docs/standard/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="5a856-117">For more information, see [Generics](../../../docs/standard/generics/index.md).</span></span>  
  
 <span data-ttu-id="5a856-118">Bu genel bakışta, aşağıdaki bölümlerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="5a856-118">This overview consists of the following sections:</span></span>  
  
-   [<span data-ttu-id="5a856-119">Bu genel türü veya yöntemi mi?</span><span class="sxs-lookup"><span data-stu-id="5a856-119">Is This a Generic Type or Method?</span></span>](#is_this_a_generic_type_or_method)  
  
-   [<span data-ttu-id="5a856-120">Kapalı genel türleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="5a856-120">Generating Closed Generic Types</span></span>](#generating_closed_generic_types)  
  
-   [<span data-ttu-id="5a856-121">Tür bağımsız değişkenleri ve tür parametreleri İnceleme</span><span class="sxs-lookup"><span data-stu-id="5a856-121">Examining Type Arguments and Type Parameters</span></span>](#examining_type_arguments)  
  
-   [<span data-ttu-id="5a856-122">İnvariants</span><span class="sxs-lookup"><span data-stu-id="5a856-122">Invariants</span></span>](#invariants)  
  
-   [<span data-ttu-id="5a856-123">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="5a856-123">Related Topics</span></span>](#related_topics)  
  
<a name="is_this_a_generic_type_or_method"></a>   
## <a name="is-this-a-generic-type-or-method"></a><span data-ttu-id="5a856-124">Bu genel türü veya yöntemi mi?</span><span class="sxs-lookup"><span data-stu-id="5a856-124">Is This a Generic Type or Method?</span></span>  
 <span data-ttu-id="5a856-125">Bir örneği tarafından temsil edilen bilinmeyen bir türe incelemek için yansıma kullandığınızda <xref:System.Type>, kullanın <xref:System.Type.IsGenericType%2A> bilinmeyen tür genel olup olmadığını belirlemek için özellik.</span><span class="sxs-lookup"><span data-stu-id="5a856-125">When you use reflection to examine an unknown type, represented by an instance of <xref:System.Type>, use the <xref:System.Type.IsGenericType%2A> property to determine whether the unknown type is generic.</span></span> <span data-ttu-id="5a856-126">Döndürdüğü `true` tür genel ise.</span><span class="sxs-lookup"><span data-stu-id="5a856-126">It returns `true` if the type is generic.</span></span> <span data-ttu-id="5a856-127">Benzer şekilde, bir örneği tarafından temsil edilen bir bilinmeyen yöntem incelediğinizde <xref:System.Reflection.MethodInfo> sınıfı, kullanın <xref:System.Reflection.MethodInfo.IsGenericMethod%2A> yöntemi genel olup olmadığını belirlemek için özellik.</span><span class="sxs-lookup"><span data-stu-id="5a856-127">Similarly, when you examine an unknown method, represented by an instance of the <xref:System.Reflection.MethodInfo> class, use the <xref:System.Reflection.MethodInfo.IsGenericMethod%2A> property to determine whether the method is generic.</span></span>  
  
### <a name="is-this-a-generic-type-or-method-definition"></a><span data-ttu-id="5a856-128">Bu, bir genel tür veya yöntem tanımını mi?</span><span class="sxs-lookup"><span data-stu-id="5a856-128">Is This a Generic Type or Method Definition?</span></span>  
 <span data-ttu-id="5a856-129">Kullanmak <xref:System.Type.IsGenericTypeDefinition%2A> belirlemek için özellik isteyip bir <xref:System.Type> nesnesini temsil eden bir genel tür tanımı ve kullanımı <xref:System.Reflection.MethodInfo.IsGenericMethodDefinition%2A> belirlemek amacıyla yöntemi olup olmadığını bir <xref:System.Reflection.MethodInfo> genel yöntem tanımını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5a856-129">Use the <xref:System.Type.IsGenericTypeDefinition%2A> property to determine whether a <xref:System.Type> object represents a generic type definition, and use the <xref:System.Reflection.MethodInfo.IsGenericMethodDefinition%2A> method to determine whether a <xref:System.Reflection.MethodInfo> represents a generic method definition.</span></span>  
  
 <span data-ttu-id="5a856-130">Genel tür ve yöntemi tanımları instantiable türleri oluşturulduğu şablonlarıdır.</span><span class="sxs-lookup"><span data-stu-id="5a856-130">Generic type and method definitions are the templates from which instantiable types are created.</span></span> <span data-ttu-id="5a856-131">Genel türleri .NET Framework Sınıf Kitaplığı'nda gibi <xref:System.Collections.Generic.Dictionary%602>, genel tür tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5a856-131">Generic types in the .NET Framework class library, such as <xref:System.Collections.Generic.Dictionary%602>, are generic type definitions.</span></span>  
  
### <a name="is-the-type-or-method-open-or-closed"></a><span data-ttu-id="5a856-132">Türü veya yöntemi açık veya kapalı?</span><span class="sxs-lookup"><span data-stu-id="5a856-132">Is the Type or Method Open or Closed?</span></span>  
 <span data-ttu-id="5a856-133">İnstantiable türleri tüm kapsayan türlerinin tüm tür parametreleri de dahil olmak üzere tüm türü parametreleri için değiştirilen durumunda bir genel türü veya yöntemi kapalı.</span><span class="sxs-lookup"><span data-stu-id="5a856-133">A generic type or method is closed if instantiable types have been substituted for all its type parameters, including all the type parameters of all enclosing types.</span></span> <span data-ttu-id="5a856-134">Kapalıysa, yalnızca genel bir tür örneği oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a856-134">You can only create an instance of a generic type if it is closed.</span></span> <span data-ttu-id="5a856-135"><xref:System.Type.ContainsGenericParameters%2A?displayProperty=nameWithType> Özelliği döndürür `true` türü açıksa.</span><span class="sxs-lookup"><span data-stu-id="5a856-135">The <xref:System.Type.ContainsGenericParameters%2A?displayProperty=nameWithType> property returns `true` if a type is open.</span></span> <span data-ttu-id="5a856-136">Yöntemleri için <xref:System.Reflection.MethodInfo.ContainsGenericParameters%2A?displayProperty=nameWithType> yöntemi aynı işlevi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="5a856-136">For methods, the <xref:System.Reflection.MethodInfo.ContainsGenericParameters%2A?displayProperty=nameWithType> method performs the same function.</span></span>  
  
 [<span data-ttu-id="5a856-137">Başa dön</span><span class="sxs-lookup"><span data-stu-id="5a856-137">Back to top</span></span>](#top)  
  
<a name="generating_closed_generic_types"></a>   
## <a name="generating-closed-generic-types"></a><span data-ttu-id="5a856-138">Kapalı genel türleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="5a856-138">Generating Closed Generic Types</span></span>  
 <span data-ttu-id="5a856-139">Genel tür ya da yöntem tanımını olduktan sonra kullanmak <xref:System.Type.MakeGenericType%2A> kapalı genel bir tür oluşturmak için yöntemi veya <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A> yöntemi oluşturmak için bir <xref:System.Reflection.MethodInfo> kapalı bir genel yöntem için.</span><span class="sxs-lookup"><span data-stu-id="5a856-139">Once you have a generic type or method definition, use the <xref:System.Type.MakeGenericType%2A> method to create a closed generic type or the <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A> method to create a <xref:System.Reflection.MethodInfo> for a closed generic method.</span></span>  
  
### <a name="getting-the-generic-type-or-method-definition"></a><span data-ttu-id="5a856-140">Genel tür veya yöntem tanımını alma</span><span class="sxs-lookup"><span data-stu-id="5a856-140">Getting the Generic Type or Method Definition</span></span>  
 <span data-ttu-id="5a856-141">Bir açık genel tür ya da bir genel tür veya yöntem tanımını yöntemi varsa, örnekleri oluşturulamıyor ve eksik tür parametrelerini sağlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="5a856-141">If you have an open generic type or method that is not a generic type or method definition, you cannot create instances of it and you cannot supply the type parameters that are missing.</span></span> <span data-ttu-id="5a856-142">Genel bir tür ya da yöntem tanımı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5a856-142">You must have a generic type or method definition.</span></span> <span data-ttu-id="5a856-143">Kullanım <xref:System.Type.GetGenericTypeDefinition%2A> genel tür tanımı elde etmek için yöntemi veya <xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A> genel yöntem tanımını elde etmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5a856-143">Use the <xref:System.Type.GetGenericTypeDefinition%2A> method to obtain the generic type definition or the <xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A> method to obtain the generic method definition.</span></span>  
  
 <span data-ttu-id="5a856-144">Örneğin, bir <xref:System.Type> nesnesini temsil eden `Dictionary<int, string>` (`Dictionary(Of Integer, String)` Visual Basic'te) ve türü oluşturmak istediğiniz `Dictionary<string, MyClass>`, kullanabileceğiniz <xref:System.Type.GetGenericTypeDefinition%2A> almak için yöntemi bir <xref:System.Type> temsil eden `Dictionary<TKey, TValue>` ve ardından <xref:System.Type.MakeGenericType%2A> yöntemini üretmeye bir <xref:System.Type> temsil eden `Dictionary<int, MyClass>`.</span><span class="sxs-lookup"><span data-stu-id="5a856-144">For example, if you have a <xref:System.Type> object representing `Dictionary<int, string>` (`Dictionary(Of Integer, String)` in Visual Basic) and you want to create the type `Dictionary<string, MyClass>`, you can use the <xref:System.Type.GetGenericTypeDefinition%2A> method to get a <xref:System.Type> representing `Dictionary<TKey, TValue>` and then use the <xref:System.Type.MakeGenericType%2A> method to produce a <xref:System.Type> representing `Dictionary<int, MyClass>`.</span></span>  
  
 <span data-ttu-id="5a856-145">Genel bir tür olmayan açık genel tür örneği için "Tür parametresi veya tür bağımsız değişkeni" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="5a856-145">For an example of an open generic type that is not a generic type, see "Type Parameter or Type Argument" later in this topic.</span></span>  
  
 [<span data-ttu-id="5a856-146">Başa dön</span><span class="sxs-lookup"><span data-stu-id="5a856-146">Back to top</span></span>](#top)  
  
<a name="examining_type_arguments"></a>   
## <a name="examining-type-arguments-and-type-parameters"></a><span data-ttu-id="5a856-147">Tür bağımsız değişkenleri ve tür parametreleri İnceleme</span><span class="sxs-lookup"><span data-stu-id="5a856-147">Examining Type Arguments and Type Parameters</span></span>  
 <span data-ttu-id="5a856-148">Kullanmak <xref:System.Type.GetGenericArguments%2A?displayProperty=nameWithType> bir dizi elde etmek için yöntemi <xref:System.Type> tür parametreleri veya genel bir tür, tür bağımsız değişkenleri temsil eder ve kullanan nesneleri <xref:System.Reflection.MethodInfo.GetGenericArguments%2A?displayProperty=nameWithType> genel yöntem aynı gerçekleştirmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="5a856-148">Use the <xref:System.Type.GetGenericArguments%2A?displayProperty=nameWithType> method to obtain an array of <xref:System.Type> objects that represent the type parameters or type arguments of a generic type, and use the <xref:System.Reflection.MethodInfo.GetGenericArguments%2A?displayProperty=nameWithType> method to do the same for a generic method.</span></span>  
  
 <span data-ttu-id="5a856-149">Öğrendikten sonra bir <xref:System.Type> nesnesini temsil eden bir tür parametresi, yansıma birçok ek sorusu vardır.</span><span class="sxs-lookup"><span data-stu-id="5a856-149">Once you know that a <xref:System.Type> object represents a type parameter, there are many additional questions reflection can answer.</span></span> <span data-ttu-id="5a856-150">Türü parametrenin kaynağı, konumunu ve kendi kısıtlamaları belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a856-150">You can determine the type parameter's source, its position, and its constraints.</span></span>  
  
### <a name="type-parameter-or-type-argument"></a><span data-ttu-id="5a856-151">Tür parametresi veya tür bağımsız değişkeni</span><span class="sxs-lookup"><span data-stu-id="5a856-151">Type Parameter or Type Argument</span></span>  
 <span data-ttu-id="5a856-152">Dizinin belirli bir öğesine bir tür parametresi veya tür bağımsız değişkeni olup olmadığını belirlemek için <xref:System.Type.IsGenericParameter%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="5a856-152">To determine whether a particular element of the array is a type parameter or a type argument, use the <xref:System.Type.IsGenericParameter%2A> property.</span></span> <span data-ttu-id="5a856-153"><xref:System.Type.IsGenericParameter%2A> Özelliği `true` öğesi bir tür parametresi ise.</span><span class="sxs-lookup"><span data-stu-id="5a856-153">The <xref:System.Type.IsGenericParameter%2A> property is `true` if the element is a type parameter.</span></span>  
  
 <span data-ttu-id="5a856-154">Genel tür tanımında olmadan genel bir tür açık olabilir, bu durumda, tür bağımsız değişkenleri ve tür parametreleri bir karışımını sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5a856-154">A generic type can be open without being a generic type definition, in which case it has a mixture of type arguments and type parameters.</span></span> <span data-ttu-id="5a856-155">Örneğin, aşağıdaki kodda sınıf `D` ilk tür parametresi değiştirerek tarafından oluşturulan bir türü türetilen `D` ikinci tür parametresi için `B`.</span><span class="sxs-lookup"><span data-stu-id="5a856-155">For example, in the following code, class `D` derives from a type created by substituting the first type parameter of `D` for the second type parameter of `B`.</span></span>  
  
```csharp  
class B<T, U> {}  
class D<V, W> : B<int, V> {}  
```  
  
```vb  
Class B(Of T, U)  
End Class  
Class D(Of V, W)  
    Inherits B(Of Integer, V)  
End Class  
```  
  
```cpp  
generic<typename T, typename U> ref class B {};  
generic<typename V, typename W> ref class D : B<int, V> {};  
```  
  
 <span data-ttu-id="5a856-156">Elde varsa bir <xref:System.Type> nesnesini temsil eden `D<V, W>` ve <xref:System.Type.BaseType%2A> elde edilen türünü temel almak için özellik `type B<int, V>` açık, ancak genel tür tanımı değil.</span><span class="sxs-lookup"><span data-stu-id="5a856-156">If you obtain a <xref:System.Type> object representing `D<V, W>` and use the <xref:System.Type.BaseType%2A> property to obtain its base type, the resulting `type B<int, V>` is open, but it is not a generic type definition.</span></span>  
  
### <a name="source-of-a-generic-parameter"></a><span data-ttu-id="5a856-157">Genel bir parametrenin kaynağı</span><span class="sxs-lookup"><span data-stu-id="5a856-157">Source of a Generic Parameter</span></span>  
 <span data-ttu-id="5a856-158">Genel tür parametresi, İncelemekte olduğunuz türü, kendilerini kapsayan türle veya genel yöntem gelebilir.</span><span class="sxs-lookup"><span data-stu-id="5a856-158">A generic type parameter might come from the type you are examining, from an enclosing type, or from a generic method.</span></span> <span data-ttu-id="5a856-159">Genel tür parametresi kaynak gibi belirleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5a856-159">You can determine the source of the generic type parameter as follows:</span></span>  
  
-   <span data-ttu-id="5a856-160">İlk olarak, kullanın <xref:System.Type.DeclaringMethod%2A> tür parametresi bir genel yöntemden gelen olup olmadığını belirlemek için özellik.</span><span class="sxs-lookup"><span data-stu-id="5a856-160">First, use the <xref:System.Type.DeclaringMethod%2A> property to determine whether the type parameter comes from a generic method.</span></span> <span data-ttu-id="5a856-161">Özellik değeri null bir başvuru değilse (`Nothing` Visual Basic'te), sonra kaynak genel bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="5a856-161">If the property value is not a null reference (`Nothing` in Visual Basic), then the source is a generic method.</span></span>  
  
-   <span data-ttu-id="5a856-162">Kaynak genel yöntem değil kullanırsanız <xref:System.Type.DeclaringType%2A> genel tür genel tür parametresi belirlemek için özellik ait.</span><span class="sxs-lookup"><span data-stu-id="5a856-162">If the source is not a generic method, use the <xref:System.Type.DeclaringType%2A> property to determine the generic type the generic type parameter belongs to.</span></span>  
  
 <span data-ttu-id="5a856-163">Tür parametresi genel bir yönteme aitse <xref:System.Type.DeclaringType%2A> özelliği ilgisiz genel yöntemini bildirdi türü döndürür.</span><span class="sxs-lookup"><span data-stu-id="5a856-163">If the type parameter belongs to a generic method, the <xref:System.Type.DeclaringType%2A> property returns the type that declared the generic method, which is irrelevant.</span></span>  
  
### <a name="position-of-a-generic-parameter"></a><span data-ttu-id="5a856-164">Genel bir parametreye konumu</span><span class="sxs-lookup"><span data-stu-id="5a856-164">Position of a Generic Parameter</span></span>  
 <span data-ttu-id="5a856-165">Nadir durumlarda, kendi bildiren sınıfı türü parametre listesi bir tür parametresi konumunu belirlemek gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5a856-165">In rare situations, it is necessary to determine the position of a type parameter in the type parameter list of its declaring class.</span></span> <span data-ttu-id="5a856-166">Örneğin, sahip olduğunuz varsayalım bir <xref:System.Type> nesnesini temsil eden `B<int, V>` önceki örnekten türü.</span><span class="sxs-lookup"><span data-stu-id="5a856-166">For example, suppose you have a <xref:System.Type> object representing the `B<int, V>` type from the preceding example.</span></span> <span data-ttu-id="5a856-167"><xref:System.Type.GetGenericArguments%2A> Yöntemi, tür bağımsız değişkenleri ve, incelediğinizde listesini verir `V` kullanabileceğiniz <xref:System.Type.DeclaringMethod%2A> ve <xref:System.Type.DeclaringType%2A> nerede alanından gelir bulmak için özellikler.</span><span class="sxs-lookup"><span data-stu-id="5a856-167">The <xref:System.Type.GetGenericArguments%2A> method gives you a list of type arguments, and when you examine `V` you can use the <xref:System.Type.DeclaringMethod%2A> and <xref:System.Type.DeclaringType%2A> properties to discover where it comes from.</span></span> <span data-ttu-id="5a856-168">Daha sonra kullanabilirsiniz <xref:System.Type.GenericParameterPosition%2A> türü parametre listesine içindeki onu tanımlandığı konumunu belirlemek için özellik.</span><span class="sxs-lookup"><span data-stu-id="5a856-168">You can then use the <xref:System.Type.GenericParameterPosition%2A> property to determine its position in the type parameter list where it was defined.</span></span> <span data-ttu-id="5a856-169">Bu örnekte, `V` 0 (sıfır), tanımlandığı türü parametre listesinde konumundadır.</span><span class="sxs-lookup"><span data-stu-id="5a856-169">In this example, `V` is at position 0 (zero) in the type parameter list where it was defined.</span></span>  
  
### <a name="base-type-and-interface-constraints"></a><span data-ttu-id="5a856-170">Temel türü ve arabirim kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="5a856-170">Base Type and Interface Constraints</span></span>  
 <span data-ttu-id="5a856-171">Kullanım <xref:System.Type.GetGenericParameterConstraints%2A> temel türü bir tür parametresi kısıtlaması ve arabirim kısıtlamaları elde etmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5a856-171">Use the <xref:System.Type.GetGenericParameterConstraints%2A> method to obtain the base type constraint and interface constraints of a type parameter.</span></span> <span data-ttu-id="5a856-172">Dizideki öğeler sırası önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="5a856-172">The order of the elements of the array is not significant.</span></span> <span data-ttu-id="5a856-173">Bir arabirim türü ise bir arabirim kısıtlaması bir öğeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5a856-173">An element represents an interface constraint if it is an interface type.</span></span>  
  
### <a name="generic-parameter-attributes"></a><span data-ttu-id="5a856-174">Genel parametre öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="5a856-174">Generic Parameter Attributes</span></span>  
 <span data-ttu-id="5a856-175"><xref:System.Type.GenericParameterAttributes%2A> Özelliği alır bir <xref:System.Reflection.GenericParameterAttributes> varyansı (Kovaryans veya değişken karşıtı) ve özel bir tür parametresi kısıtlamaları belirten değer.</span><span class="sxs-lookup"><span data-stu-id="5a856-175">The <xref:System.Type.GenericParameterAttributes%2A> property gets a <xref:System.Reflection.GenericParameterAttributes> value that indicates the variance (covariance or contravariance) and the special constraints of a type parameter.</span></span>  
  
#### <a name="covariance-and-contravariance"></a><span data-ttu-id="5a856-176">Kovaryans ve Kontravaryans</span><span class="sxs-lookup"><span data-stu-id="5a856-176">Covariance and Contravariance</span></span>  
 <span data-ttu-id="5a856-177">Olup bir tür parametresi birlikte değişkendir veya karşıtı belirlemek için uygulama <xref:System.Reflection.GenericParameterAttributes.VarianceMask?displayProperty=nameWithType> için maske <xref:System.Reflection.GenericParameterAttributes> tarafından döndürülen değer <xref:System.Type.GenericParameterAttributes%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="5a856-177">To determine whether a type parameter is covariant or contravariant, apply the <xref:System.Reflection.GenericParameterAttributes.VarianceMask?displayProperty=nameWithType> mask to the <xref:System.Reflection.GenericParameterAttributes> value that is returned by the <xref:System.Type.GenericParameterAttributes%2A> property.</span></span> <span data-ttu-id="5a856-178">Sonuç ise <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>, tür parametresi değişmez.</span><span class="sxs-lookup"><span data-stu-id="5a856-178">If the result is <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>, the type parameter is invariant.</span></span> <span data-ttu-id="5a856-179">Bkz: [Kovaryans ve kontravaryans](../../../docs/standard/generics/covariance-and-contravariance.md).</span><span class="sxs-lookup"><span data-stu-id="5a856-179">See [Covariance and Contravariance](../../../docs/standard/generics/covariance-and-contravariance.md).</span></span>  
  
#### <a name="special-constraints"></a><span data-ttu-id="5a856-180">Özel kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="5a856-180">Special Constraints</span></span>  
 <span data-ttu-id="5a856-181">Özel bir tür parametresi kısıtlamaları belirlemek için uygulama <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> için maske <xref:System.Reflection.GenericParameterAttributes> tarafından döndürülen değer <xref:System.Type.GenericParameterAttributes%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="5a856-181">To determine the special constraints of a type parameter, apply the <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> mask to the <xref:System.Reflection.GenericParameterAttributes> value that is returned by the <xref:System.Type.GenericParameterAttributes%2A> property.</span></span> <span data-ttu-id="5a856-182">Sonuç ise <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>, hiçbir özel sınırlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="5a856-182">If the result is <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>, there are no special constraints.</span></span> <span data-ttu-id="5a856-183">Tür parametresi, başvuru türünde bir null değer türü olabilir ve varsayılan bir oluşturucuya sahip olmasını kısıtlanabilir.</span><span class="sxs-lookup"><span data-stu-id="5a856-183">A type parameter can be constrained to be a reference type, to be a non-nullable value type, and to have a default constructor.</span></span>  
  
 [<span data-ttu-id="5a856-184">Başa dön</span><span class="sxs-lookup"><span data-stu-id="5a856-184">Back to top</span></span>](#top)  
  
<a name="invariants"></a>   
## <a name="invariants"></a><span data-ttu-id="5a856-185">İnvariants</span><span class="sxs-lookup"><span data-stu-id="5a856-185">Invariants</span></span>  
 <span data-ttu-id="5a856-186">Yansıma genel türleri için genel koşulları değişmez koşullarını tablo için bkz: <xref:System.Type.IsGenericType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5a856-186">For a table of the invariant conditions for common terms in reflection for generic types, see <xref:System.Type.IsGenericType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5a856-187">Genel yöntemler için ilgili ek koşullar için bkz: <xref:System.Reflection.MethodInfo.IsGenericMethod%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5a856-187">For additional terms relating to generic methods, see <xref:System.Reflection.MethodInfo.IsGenericMethod%2A?displayProperty=nameWithType>.</span></span>  
  
 [<span data-ttu-id="5a856-188">Başa dön</span><span class="sxs-lookup"><span data-stu-id="5a856-188">Back to top</span></span>](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a><span data-ttu-id="5a856-189">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="5a856-189">Related Topics</span></span>  
  
|<span data-ttu-id="5a856-190">Başlık</span><span class="sxs-lookup"><span data-stu-id="5a856-190">Title</span></span>|<span data-ttu-id="5a856-191">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5a856-191">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="5a856-192">Nasıl yapılır: inceleyin ve yansıma ile genel türleri örneği</span><span class="sxs-lookup"><span data-stu-id="5a856-192">How to: Examine and Instantiate Generic Types with Reflection</span></span>](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md)|<span data-ttu-id="5a856-193">Özellikleri ve yöntemleri kullanmayı gösterir <xref:System.Type> ve <xref:System.Reflection.MethodInfo> genel türler incelemek için.</span><span class="sxs-lookup"><span data-stu-id="5a856-193">Shows how to use the properties and methods of <xref:System.Type> and <xref:System.Reflection.MethodInfo> to examine generic types.</span></span>|  
|[<span data-ttu-id="5a856-194">Genel türler</span><span class="sxs-lookup"><span data-stu-id="5a856-194">Generics</span></span>](../../../docs/standard/generics/index.md)|<span data-ttu-id="5a856-195">Genel türler özellik ve .NET Framework nasıl desteklediği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="5a856-195">Describes the generics feature and how it is supported in the .NET Framework.</span></span>|  
|[<span data-ttu-id="5a856-196">Nasıl yapılır: yansıma ile genel tür tanımlama yayma</span><span class="sxs-lookup"><span data-stu-id="5a856-196">How to: Define a Generic Type with Reflection Emit</span></span>](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)|<span data-ttu-id="5a856-197">Yansıma kullanmayı gösterir dinamik derlemelerde genel türleri oluşturmak için yayma.</span><span class="sxs-lookup"><span data-stu-id="5a856-197">Shows how to use reflection emit to generate generic types in dynamic assemblies.</span></span>|  
|[<span data-ttu-id="5a856-198">Tür bilgilerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="5a856-198">Viewing Type Information</span></span>](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)|<span data-ttu-id="5a856-199">Açıklar <xref:System.Type> sınıfı ve nasıl kullanılacağını gösteren kod örnekleri sağlar <xref:System.Type> Oluşturucular, yöntemleri, alanları, özellikleri ve olayları hakkında bilgi edinmek için çeşitli yansıma sınıflarla.</span><span class="sxs-lookup"><span data-stu-id="5a856-199">Describes the <xref:System.Type> class and provides code examples that illustrate how to use <xref:System.Type> with various reflection classes to obtain information about constructors, methods, fields, properties, and events.</span></span>|