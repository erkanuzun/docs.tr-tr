---
title: "Temsilcileri Kullanma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: delegates [C#], how to use
ms.assetid: 99a2fc27-a32e-4a34-921c-e65497520eec
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cef62448388299f310fa26ecb632485b6538c032
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="using-delegates-c-programming-guide"></a><span data-ttu-id="a9273-102">Temsilcileri Kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a9273-102">Using Delegates (C# Programming Guide)</span></span>
<span data-ttu-id="a9273-103">A [temsilci](../../../csharp/language-reference/keywords/delegate.md) güvenli bir yöntem, benzer bir işlev işaretçisi C ve C++ için yalıtır türüdür.</span><span class="sxs-lookup"><span data-stu-id="a9273-103">A [delegate](../../../csharp/language-reference/keywords/delegate.md) is a type that safely encapsulates a method, similar to a function pointer in C and C++.</span></span> <span data-ttu-id="a9273-104">Aksine C işlev işaretçileri, nesne yönelimli Temsilciler, güvenli ve güvenli yazın.</span><span class="sxs-lookup"><span data-stu-id="a9273-104">Unlike C function pointers, delegates are object-oriented, type safe, and secure.</span></span> <span data-ttu-id="a9273-105">Bir temsilci türü temsilci adına göre tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a9273-105">The type of a delegate is defined by the name of the delegate.</span></span> <span data-ttu-id="a9273-106">Aşağıdaki örnek, adlandırılmış bir temsilci bildirir `Del` geçen bir yöntem kapsülleyen bir [dize](../../../csharp/language-reference/keywords/string.md) bağımsız değişken ve döndürür [void](../../../csharp/language-reference/keywords/void.md):</span><span class="sxs-lookup"><span data-stu-id="a9273-106">The following example declares a delegate named `Del` that can encapsulate a method that takes a [string](../../../csharp/language-reference/keywords/string.md) as an argument and returns [void](../../../csharp/language-reference/keywords/void.md):</span></span>  
  
 [!code-csharp[csProgGuideDelegates#21](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_1.cs)]  
  
 <span data-ttu-id="a9273-107">Temsilci nesnesini normalde tarafından yöntemin adını temsilci kaydırılır sağlanması veya ile oluşturulan bir [anonim yöntemi](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="a9273-107">A delegate object is normally constructed by providing the name of the method the delegate will wrap, or with an [anonymous Method](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span></span> <span data-ttu-id="a9273-108">Bir temsilci oluşturulduktan sonra temsilciye yapılan bir yöntem çağrısı için bu yöntem temsilci tarafından geçirilir.</span><span class="sxs-lookup"><span data-stu-id="a9273-108">Once a delegate is instantiated, a method call made to the delegate will be passed by the delegate to that method.</span></span> <span data-ttu-id="a9273-109">Temsilciye çağıran tarafından geçirilen parametreler yönteme geçirilen ve dönüş değeri varsa, yönteminden çağırana temsilci tarafından döndürülür.</span><span class="sxs-lookup"><span data-stu-id="a9273-109">The parameters passed to the delegate by the caller are passed to the method, and the return value, if any, from the method is returned to the caller by the delegate.</span></span> <span data-ttu-id="a9273-110">Bu temsilci çağırma olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="a9273-110">This is known as invoking the delegate.</span></span> <span data-ttu-id="a9273-111">Sarmalanan yöntemi değilmiş gibi başlatılan bir temsilci çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="a9273-111">An instantiated delegate can be invoked as if it were the wrapped method itself.</span></span> <span data-ttu-id="a9273-112">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="a9273-112">For example:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#22](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_2.cs)]  
  
 [!code-csharp[csProgGuideDelegates#23](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_3.cs)]  
  
 <span data-ttu-id="a9273-113">Temsilci türleri türetilir <xref:System.Delegate> .NET Framework sınıf.</span><span class="sxs-lookup"><span data-stu-id="a9273-113">Delegate types are derived from the <xref:System.Delegate> class in the .NET Framework.</span></span> <span data-ttu-id="a9273-114">Temsilci türleri [korumalı](../../../csharp/language-reference/keywords/sealed.md)— bunlar türetilemez — ve özel sınıflarından mümkün değildir <xref:System.Delegate>.</span><span class="sxs-lookup"><span data-stu-id="a9273-114">Delegate types are [sealed](../../../csharp/language-reference/keywords/sealed.md)—they cannot be derived from— and it is not possible to derive custom classes from <xref:System.Delegate>.</span></span> <span data-ttu-id="a9273-115">Örneklenen temsilci bir nesne olduğundan, parametre olarak geçirilen veya yükleyebilir bir özelliğine atanır.</span><span class="sxs-lookup"><span data-stu-id="a9273-115">Because the instantiated delegate is an object, it can be passed as a parameter, or assigned to a property.</span></span> <span data-ttu-id="a9273-116">Bu temsilci bir parametre olarak kabul edin ve daha sonraki bir zamanda temsilci çağırmak bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="a9273-116">This allows a method to accept a delegate as a parameter, and call the delegate at some later time.</span></span> <span data-ttu-id="a9273-117">Bu zaman uyumsuz bir geri çağırma bilinir ve uzun bir işlem tamamlandığında, çağıran bildiren yaygın bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="a9273-117">This is known as an asynchronous callback, and is a common method of notifying a caller when a long process has completed.</span></span> <span data-ttu-id="a9273-118">Bu biçimde bir temsilci kullanıldığında, temsilci kullanarak kod kullanılan yöntemin kullanımı bilgisi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a9273-118">When a delegate is used in this fashion, the code using the delegate does not need any knowledge of the implementation of the method being used.</span></span> <span data-ttu-id="a9273-119">Arabirimleri sağlamak kapsülleme benzer bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="a9273-119">The functionality is similar to the encapsulation interfaces provide.</span></span>  
  
 <span data-ttu-id="a9273-120">Geri aramalar başka bir yaygın kullanımı bir özel karşılaştırma yöntemi tanımlama ve bu temsilciyi bir sıralama yöntemi geçirme.</span><span class="sxs-lookup"><span data-stu-id="a9273-120">Another common use of callbacks is defining a custom comparison method and passing that delegate to a sort method.</span></span> <span data-ttu-id="a9273-121">Arayanın kod Sıralama algoritması parçası olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a9273-121">It allows the caller's code to become part of the sort algorithm.</span></span> <span data-ttu-id="a9273-122">Aşağıdaki örnek yöntemi kullanan `Del` türünü bir parametre olarak:</span><span class="sxs-lookup"><span data-stu-id="a9273-122">The following example method uses the `Del` type as a parameter:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#24](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_4.cs)]  
  
 <span data-ttu-id="a9273-123">Ardından, bu yönteme yukarıda oluşturduğunuz temsilci geçirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a9273-123">You can then pass the delegate created above to that method:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#25](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_5.cs)]  
  
 <span data-ttu-id="a9273-124">ve konsola çıktı aşağıdaki alırsınız:</span><span class="sxs-lookup"><span data-stu-id="a9273-124">and receive the following output to the console:</span></span>  
  
 `The number is: 3`  
  
 <span data-ttu-id="a9273-125">Bir Özet, temsilci kullanarak `MethodWithCallback` konsol doğrudan çağırmanız gerekmez — bir konsol aklınızda tasarlanmalıdır yok.</span><span class="sxs-lookup"><span data-stu-id="a9273-125">Using the delegate as an abstraction, `MethodWithCallback` does not need to call the console directly—it does not have to be designed with a console in mind.</span></span> <span data-ttu-id="a9273-126">Ne `MethodWithCallback` değil yalnızca bir dize hazırlamak ve dize başka bir yönteme geçirin.</span><span class="sxs-lookup"><span data-stu-id="a9273-126">What `MethodWithCallback` does is simply prepare a string and pass the string to another method.</span></span> <span data-ttu-id="a9273-127">Temsil edilen bir yöntem parametreleri herhangi bir sayıda kullanabildiğiniz özellikle güçlüdür.</span><span class="sxs-lookup"><span data-stu-id="a9273-127">This is especially powerful since a delegated method can use any number of parameters.</span></span>  
  
 <span data-ttu-id="a9273-128">Örnek yöntemi sarmalamak için bir temsilci oluşturulduğunda temsilci hem örneği hem de yöntemi başvurur.</span><span class="sxs-lookup"><span data-stu-id="a9273-128">When a delegate is constructed to wrap an instance method, the delegate references both the instance and the method.</span></span> <span data-ttu-id="a9273-129">Bir temsilci sarmaladığı, yöntemi yanı sıra örnek türü olanağıyla sahiptir, bu nedenle var olduğu sürece bir yöntem temsilci imza eşleşen nesnede bir temsilci nesne türüne başvuruda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="a9273-129">A delegate has no knowledge of the instance type aside from the method it wraps, so a delegate can refer to any type of object as long as there is a method on that object that matches the delegate signature.</span></span> <span data-ttu-id="a9273-130">Bir statik yöntem sarmalamak için bir temsilci oluşturulduğunda, yalnızca yöntemi başvurur.</span><span class="sxs-lookup"><span data-stu-id="a9273-130">When a delegate is constructed to wrap a static method, it only references the method.</span></span> <span data-ttu-id="a9273-131">Aşağıdaki bildirimleri dikkate alın:</span><span class="sxs-lookup"><span data-stu-id="a9273-131">Consider the following declarations:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#26](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_6.cs)]  
  
 <span data-ttu-id="a9273-132">Statik birlikte `DelegateMethod` daha önce gösterilen şimdi tarafından Sarmalanan üç yöntem sahip olduğumuz bir `Del` örneği.</span><span class="sxs-lookup"><span data-stu-id="a9273-132">Along with the static `DelegateMethod` shown previously, we now have three methods that can be wrapped by a `Del` instance.</span></span>  
  
 <span data-ttu-id="a9273-133">Bir temsilci çağrıldığında birden fazla yöntemini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9273-133">A delegate can call more than one method when invoked.</span></span> <span data-ttu-id="a9273-134">Bu, çok noktaya yayın adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="a9273-134">This is referred to as multicasting.</span></span> <span data-ttu-id="a9273-135">Ek bir yöntem temsilcinin yöntemleri listesine eklemek için — çağırma listesi — yalnızca eklenmesi veya toplama atama işleçleri kullanarak iki temsilcileri ekleme gerektirir ('+' veya '+=').</span><span class="sxs-lookup"><span data-stu-id="a9273-135">To add an extra method to the delegate's list of methods—the invocation list—simply requires adding two delegates using the addition or addition assignment operators ('+' or '+=').</span></span> <span data-ttu-id="a9273-136">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="a9273-136">For example:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#27](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_7.cs)]  
  
 <span data-ttu-id="a9273-137">Bu noktada `allMethodsDelegate` çağırma listesinde üç yöntem içerir —`Method1`, `Method2`, ve `DelegateMethod`.</span><span class="sxs-lookup"><span data-stu-id="a9273-137">At this point `allMethodsDelegate` contains three methods in its invocation list—`Method1`, `Method2`, and `DelegateMethod`.</span></span> <span data-ttu-id="a9273-138">Özgün üç temsilcileri `d1`, `d2`, ve `d3`, değişmeden kalır.</span><span class="sxs-lookup"><span data-stu-id="a9273-138">The original three delegates, `d1`, `d2`, and `d3`, remain unchanged.</span></span> <span data-ttu-id="a9273-139">Zaman `allMethodsDelegate` olan çağrılır, tüm üç yöntem sırada çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a9273-139">When `allMethodsDelegate` is invoked, all three methods are called in order.</span></span> <span data-ttu-id="a9273-140">Temsilci başvuru parametreleri kullanıyorsa, başvuru sırayla her üç yöntem sırayla geçirilir ve sonraki yönteme değişiklikleri bir yöntem tarafından görülebilir.</span><span class="sxs-lookup"><span data-stu-id="a9273-140">If the delegate uses reference parameters, the reference is passed sequentially to each of the three methods in turn, and any changes by one method are visible to the next method.</span></span> <span data-ttu-id="a9273-141">Ne zaman yöntemlerinden herhangi birini yöntemi içinde yakalandı bir özel durumları oluşturur temsilci ve hiçbir sonraki yöntemi çağırma listesinde çağıran özel durum geçirilecek çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a9273-141">When any of the methods throws an exception that is not caught within the method, that exception is passed to the caller of the delegate and no subsequent methods in the invocation list are called.</span></span> <span data-ttu-id="a9273-142">Temsilci dönüş değeri varsa ve/veya out parametreleri, çağrılan son yönteminin parametrelerini ve dönüş değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="a9273-142">If the delegate has a return value and/or out parameters, it returns the return value and parameters of the last method invoked.</span></span> <span data-ttu-id="a9273-143">Bir yöntemi çağırma listesinden kaldırmak için azaltma kullanın veya azaltma atama işleci ('-' veya ' '-='').</span><span class="sxs-lookup"><span data-stu-id="a9273-143">To remove a method from the invocation list, use the decrement or decrement assignment operator ('-' or '-=').</span></span> <span data-ttu-id="a9273-144">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="a9273-144">For example:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#28](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_8.cs)]  
  
 <span data-ttu-id="a9273-145">Temsilci türleri türetilmiş çünkü `System.Delegate`, bu sınıf tarafından tanımlanan özellikler ve yöntemler temsilci üzerinde çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="a9273-145">Because delegate types are derived from `System.Delegate`, the methods and properties defined by that class can be called on the delegate.</span></span> <span data-ttu-id="a9273-146">Örneğin, bir temsilcinin çağırma listesinde yöntemleri sayısını bulmak için yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a9273-146">For example, to find the number of methods in a delegate's invocation list, you may write:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#29](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_9.cs)]  
  
 <span data-ttu-id="a9273-147">Temsilcileri kendi çağırma listesinde birden fazla yöntemiyle türetilen <xref:System.MulticastDelegate>, öğesinin bir alt kümesi olan `System.Delegate`.</span><span class="sxs-lookup"><span data-stu-id="a9273-147">Delegates with more than one method in their invocation list derive from <xref:System.MulticastDelegate>, which is a subclass of `System.Delegate`.</span></span> <span data-ttu-id="a9273-148">Yukarıdaki kod her iki durumda da çalışır ve her iki sınıflarını destekleyen çünkü `GetInvocationList`.</span><span class="sxs-lookup"><span data-stu-id="a9273-148">The above code works in either case because both classes support `GetInvocationList`.</span></span>  
  
 <span data-ttu-id="a9273-149">Çok noktaya yayın temsilcileri olay işlemede yaygın olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a9273-149">Multicast delegates are used extensively in event handling.</span></span> <span data-ttu-id="a9273-150">Olay kaynağı nesneleri olay almak için kayıtlı alıcı nesnelere olay bildirimleri gönderin.</span><span class="sxs-lookup"><span data-stu-id="a9273-150">Event source objects send event notifications to recipient objects that have registered to receive that event.</span></span> <span data-ttu-id="a9273-151">İçin bir olay kaydetmek için alıcı olayını işlemek için tasarlanmış bir yöntem oluşturur sonra bu yöntem için bir temsilci oluşturur ve olay kaynağı temsilci geçirir.</span><span class="sxs-lookup"><span data-stu-id="a9273-151">To register for an event, the recipient creates a method designed to handle the event, then creates a delegate for that method and passes the delegate to the event source.</span></span> <span data-ttu-id="a9273-152">Olay gerçekleştiğinde kaynak temsilcisini çağırır.</span><span class="sxs-lookup"><span data-stu-id="a9273-152">The source calls the delegate when the event occurs.</span></span> <span data-ttu-id="a9273-153">Temsilci daha sonra olay işleme alıcı olay verileri teslim yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="a9273-153">The delegate then calls the event handling method on the recipient, delivering the event data.</span></span> <span data-ttu-id="a9273-154">Temsilci türü için belirli bir olayın olay kaynağına göre tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a9273-154">The delegate type for a given event is defined by the event source.</span></span> <span data-ttu-id="a9273-155">Daha fazla bilgi için bkz: [olayları](../../../csharp/programming-guide/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="a9273-155">For more, see [Events](../../../csharp/programming-guide/events/index.md).</span></span>  
  
 <span data-ttu-id="a9273-156">Derleme zamanında atanan iki farklı türlerde temsilciler karşılaştırma bir derleme hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="a9273-156">Comparing delegates of two different types assigned at compile-time will result in a compilation error.</span></span> <span data-ttu-id="a9273-157">Temsilci örnekleri statik olarak türdeyse `System.Delegate`sonra karşılaştırma izin verilir, ancak en false döndürür çalışır zaman.</span><span class="sxs-lookup"><span data-stu-id="a9273-157">If the delegate instances are statically of the type `System.Delegate`, then the comparison is allowed, but will return false at run time.</span></span> <span data-ttu-id="a9273-158">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="a9273-158">For example:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#30](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_10.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="a9273-159">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a9273-159">See Also</span></span>  
 [<span data-ttu-id="a9273-160">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a9273-160">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a9273-161">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="a9273-161">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="a9273-162">Temsilcilerde varyans kullanma</span><span class="sxs-lookup"><span data-stu-id="a9273-162">Using Variance in Delegates</span></span>](http://msdn.microsoft.com/library/e6acad03-93e0-4efb-a158-8696d5eb4ecf)  
 [<span data-ttu-id="a9273-163">Temsilcilerde varyans</span><span class="sxs-lookup"><span data-stu-id="a9273-163">Variance in Delegates</span></span>](http://msdn.microsoft.com/library/e3b98197-6c5b-4e55-9c6e-9739b60645ca)  
 [<span data-ttu-id="a9273-164">İşlev ve eylem genel temsilcileri için varyans kullanma</span><span class="sxs-lookup"><span data-stu-id="a9273-164">Using Variance for Func and Action Generic Delegates</span></span>](http://msdn.microsoft.com/library/e69c4f39-09aa-4c6d-a752-08cc767d8290)  
 [<span data-ttu-id="a9273-165">Olayları</span><span class="sxs-lookup"><span data-stu-id="a9273-165">Events</span></span>](../../../csharp/programming-guide/events/index.md)