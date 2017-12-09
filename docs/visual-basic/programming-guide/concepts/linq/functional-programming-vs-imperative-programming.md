---
title: "İşlevsel Programlama vs. Kesinlik temelli programlama (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a1f3b57-00e6-447d-9906-74c7c4d5d85c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8519ca7fcda63e73e29d33a768c589829aafa0b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="functional-programming-vs-imperative-programming-visual-basic"></a><span data-ttu-id="42ff2-102">İşlevsel Programlama vs. Kesinlik temelli programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42ff2-102">Functional Programming vs. Imperative Programming (Visual Basic)</span></span>
<span data-ttu-id="42ff2-103">Bu konuda karşılaştırır ve işlevsel programlama daha geleneksel kesinlik temelli (yordam) programlama ile karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="42ff2-103">This topic compares and contrasts functional programming with more traditional imperative (procedural) programming.</span></span>  
  
## <a name="functional-programming-vs-imperative-programming"></a><span data-ttu-id="42ff2-104">İşlevsel Programlama vs. Kesinlik temelli programlama</span><span class="sxs-lookup"><span data-stu-id="42ff2-104">Functional Programming vs. Imperative Programming</span></span>  
 <span data-ttu-id="42ff2-105">*İşlevsel programlama* sorunu çözmeye saf bir işlev yaklaşım desteklemek için açıkça kip oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="42ff2-105">The *functional programming* paradigm was explicitly created to support a pure functional approach to problem solving.</span></span> <span data-ttu-id="42ff2-106">İşlevsel programlama biçimi olan *bildirim temelli programlama*.</span><span class="sxs-lookup"><span data-stu-id="42ff2-106">Functional programming is a form of *declarative programming*.</span></span> <span data-ttu-id="42ff2-107">Buna karşılık, nesne odaklı programlama (OOP) dil C#, Visual Basic, C++ ve Java gibi dahil olmak üzere çoğu temel dil öncelikle desteklemek için tasarlanmış olan *kesinlik temelli* (yordam) programlama.</span><span class="sxs-lookup"><span data-stu-id="42ff2-107">In contrast, most mainstream languages, including object-oriented programming (OOP) languages such as C#, Visual Basic, C++, and Java, were designed to primarily support *imperative* (procedural) programming.</span></span>  
  
 <span data-ttu-id="42ff2-108">Kesinlik temelli bir yaklaşım ile bir geliştirici açıklayan kod ayrıntı kesin bilgisayarı hedef gerçekleştirmek için uygulamanız gereken adımlar yazar.</span><span class="sxs-lookup"><span data-stu-id="42ff2-108">With an imperative approach, a developer writes code that describes in exacting detail the steps that the computer must take to accomplish the goal.</span></span> <span data-ttu-id="42ff2-109">Bu bazen olarak adlandırılır *algoritmik* programlama.</span><span class="sxs-lookup"><span data-stu-id="42ff2-109">This is sometimes referred to as *algorithmic* programming.</span></span> <span data-ttu-id="42ff2-110">Buna karşılık, işlevsel bir yaklaşım sorun yürütülecek işlevler kümesi olarak oluşturmayı kapsar.</span><span class="sxs-lookup"><span data-stu-id="42ff2-110">In contrast, a functional approach involves composing the problem as a set of functions to be executed.</span></span> <span data-ttu-id="42ff2-111">Her işlev giriş ve her hangi bir işlev döndürür dikkatle tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="42ff2-111">You define carefully the input to each function, and what each function returns.</span></span> <span data-ttu-id="42ff2-112">Aşağıdaki tabloda bu iki yaklaşım genel farklarını bazıları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="42ff2-112">The following table describes some of the general differences between these two approaches.</span></span>  
  
|<span data-ttu-id="42ff2-113">Özelliği</span><span class="sxs-lookup"><span data-stu-id="42ff2-113">Characteristic</span></span>|<span data-ttu-id="42ff2-114">Kesinlik temelli bir yaklaşım</span><span class="sxs-lookup"><span data-stu-id="42ff2-114">Imperative approach</span></span>|<span data-ttu-id="42ff2-115">İşlevsel bir yaklaşım</span><span class="sxs-lookup"><span data-stu-id="42ff2-115">Functional approach</span></span>|  
|--------------------|-------------------------|-------------------------|  
|<span data-ttu-id="42ff2-116">Programcı odak</span><span class="sxs-lookup"><span data-stu-id="42ff2-116">Programmer focus</span></span>|<span data-ttu-id="42ff2-117">(Algoritmaları) görevlerin nasıl gerçekleştirileceği ve durumunda değişikliklerin nasıl izleneceği.</span><span class="sxs-lookup"><span data-stu-id="42ff2-117">How to perform tasks (algorithms) and how to track changes in state.</span></span>|<span data-ttu-id="42ff2-118">Hangi bilgilerin istenen ve hangi dönüşümleri gereklidir.</span><span class="sxs-lookup"><span data-stu-id="42ff2-118">What information is desired and what transformations are required.</span></span>|  
|<span data-ttu-id="42ff2-119">Durum değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="42ff2-119">State changes</span></span>|<span data-ttu-id="42ff2-120">Önemli.</span><span class="sxs-lookup"><span data-stu-id="42ff2-120">Important.</span></span>|<span data-ttu-id="42ff2-121">Varolmayan.</span><span class="sxs-lookup"><span data-stu-id="42ff2-121">Non-existent.</span></span>|  
|<span data-ttu-id="42ff2-122">Yürütme sırasını</span><span class="sxs-lookup"><span data-stu-id="42ff2-122">Order of execution</span></span>|<span data-ttu-id="42ff2-123">Önemli.</span><span class="sxs-lookup"><span data-stu-id="42ff2-123">Important.</span></span>|<span data-ttu-id="42ff2-124">Düşük önem.</span><span class="sxs-lookup"><span data-stu-id="42ff2-124">Low importance.</span></span>|  
|<span data-ttu-id="42ff2-125">Birincil akış denetimi</span><span class="sxs-lookup"><span data-stu-id="42ff2-125">Primary flow control</span></span>|<span data-ttu-id="42ff2-126">Döngüler, koşulları ve işlev (yöntem) çağrıları.</span><span class="sxs-lookup"><span data-stu-id="42ff2-126">Loops, conditionals, and function (method) calls.</span></span>|<span data-ttu-id="42ff2-127">Özyineleme dahil olmak üzere işlevi çağırır.</span><span class="sxs-lookup"><span data-stu-id="42ff2-127">Function calls, including recursion.</span></span>|  
|<span data-ttu-id="42ff2-128">Birincil işleme birimi</span><span class="sxs-lookup"><span data-stu-id="42ff2-128">Primary manipulation unit</span></span>|<span data-ttu-id="42ff2-129">Yapıları veya sınıfların örnekleri.</span><span class="sxs-lookup"><span data-stu-id="42ff2-129">Instances of structures or classes.</span></span>|<span data-ttu-id="42ff2-130">İlk sınıf nesneleri ve veri koleksiyonları görür.</span><span class="sxs-lookup"><span data-stu-id="42ff2-130">Functions as first-class objects and data collections.</span></span>|  
  
 <span data-ttu-id="42ff2-131">Çoğu dil belirli bir programlama standardı desteklemek için tasarlanmış olsa da, birçok genel diller birden fazla örneklerinde desteklemek için yeterince esnektir.</span><span class="sxs-lookup"><span data-stu-id="42ff2-131">Although most languages were designed to support a specific programming paradigm, many general languages are flexible enough to support multiple paradigms.</span></span> <span data-ttu-id="42ff2-132">Örneğin, işlev işaretçileri içeren çoğu dil credibly işlevsel programlama desteklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="42ff2-132">For example, most languages that contain function pointers can be used to credibly support functional programming.</span></span> <span data-ttu-id="42ff2-133">Ayrıca, Visual Basic tür çıkarımı ve lambda ifadeleri de dahil olmak üzere işlevsel programlama desteklemek için açık dil uzantıları içerir.</span><span class="sxs-lookup"><span data-stu-id="42ff2-133">Furthermore, Visual Basic includes explicit language extensions to support functional programming, including lambda expressions and type inference.</span></span> <span data-ttu-id="42ff2-134">LINQ teknolojisi bildirim temelli, işlevsel programlama biçimidir.</span><span class="sxs-lookup"><span data-stu-id="42ff2-134">LINQ technology is a form of declarative, functional programming.</span></span>  
  
## <a name="functional-programming-using-xslt"></a><span data-ttu-id="42ff2-135">İşlev XSLT kullanarak programlama</span><span class="sxs-lookup"><span data-stu-id="42ff2-135">Functional Programming Using XSLT</span></span>  
 <span data-ttu-id="42ff2-136">Birçok XSLT geliştiricilerine saf işlevsel yaklaşımda biliyorsunuzdur.</span><span class="sxs-lookup"><span data-stu-id="42ff2-136">Many XSLT developers are familiar with the pure functional approach.</span></span> <span data-ttu-id="42ff2-137">XSLT stil sayfasını geliştirmek için en etkili her şablon bir yalıtılmış, birleştirilebilir dönüşümü işlemek için bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="42ff2-137">The most effective way to develop an XSLT style sheet is to treat each template as an isolated, composable transformation.</span></span> <span data-ttu-id="42ff2-138">Yürütme tamamen XML'deki vurgulanmış sırasıdır.</span><span class="sxs-lookup"><span data-stu-id="42ff2-138">The order of execution is completely de-emphasized.</span></span> <span data-ttu-id="42ff2-139">XSLT yan etkileri (ile yordam kod yürütmek için mekanizmalar kaçış içinde işlev impurity neden yan etkileri yaratabilir özel durum) izin vermiyor.</span><span class="sxs-lookup"><span data-stu-id="42ff2-139">XSLT does not allow side effects (with the exception that escaping mechanisms for executing procedural code can introduce side effects that result in functional impurity).</span></span> <span data-ttu-id="42ff2-140">XSLT etkili bir aracı olsa da, ancak bazıları onun özelliklerini en iyi değil.</span><span class="sxs-lookup"><span data-stu-id="42ff2-140">However, although XSLT is an effective tool, some of its characteristics are not optimal.</span></span> <span data-ttu-id="42ff2-141">Örneğin, XML programlama yapıları ifade kod görece ayrıntılı ve korumak bu nedenle zor hale getirir.</span><span class="sxs-lookup"><span data-stu-id="42ff2-141">For example, expressing programming constructs in XML makes code relatively verbose, and therefore difficult to maintain.</span></span> <span data-ttu-id="42ff2-142">Ayrıca, akış denetimi için özyineleme ağır bağımlılık okunması zor kodda neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="42ff2-142">Also, the heavy reliance on recursion for flow control can result in code that is hard to read.</span></span> <span data-ttu-id="42ff2-143">XSLT hakkında daha fazla bilgi için bkz: [XSLT dönüştürmeleri](../../../../standard/data/xml/xslt-transformations.md).</span><span class="sxs-lookup"><span data-stu-id="42ff2-143">For more information about XSLT, see [XSLT Transformations](../../../../standard/data/xml/xslt-transformations.md).</span></span>  
  
 <span data-ttu-id="42ff2-144">Ancak, XSLT XML bir şekli'ndan diğerine dönüştürme için saf işlevsel bir yaklaşım kullanarak değerini oluyor uygulamasına yol açıyordu.</span><span class="sxs-lookup"><span data-stu-id="42ff2-144">However, XSLT has proved the value of using a pure functional approach for transforming XML from one shape to another.</span></span> <span data-ttu-id="42ff2-145">Saf işlevsel LINQ-XML ile programlama XSLT birçok yönden benzer.</span><span class="sxs-lookup"><span data-stu-id="42ff2-145">Pure functional programming with LINQ to XML is similar in many ways to XSLT.</span></span> <span data-ttu-id="42ff2-146">Ancak, LINQ to XML ve Visual Basic tarafından sunulan programlama yapıları, daha okunabilir ve sürdürülebilir XSLT daha saf işlevsel dönüşümleri yazmaya izin verin.</span><span class="sxs-lookup"><span data-stu-id="42ff2-146">However, the programming constructs introduced by LINQ to XML and Visual Basic allow you to write pure functional transformations that are more readable and maintainable than XSLT.</span></span>  
  
## <a name="advantages-of-pure-functions"></a><span data-ttu-id="42ff2-147">Saf işlevleri avantajları</span><span class="sxs-lookup"><span data-stu-id="42ff2-147">Advantages of Pure Functions</span></span>  
 <span data-ttu-id="42ff2-148">Saf işlev olarak işlev dönüştürmeleri uygulamak için birincil saf işlevleri birleştirilebilir nedeni: başka bir deyişle, kendi içinde bulunan ve durum bilgisiz.</span><span class="sxs-lookup"><span data-stu-id="42ff2-148">The primary reason to implement functional transformations as pure functions is that pure functions are composable: that is, self-contained and stateless.</span></span> <span data-ttu-id="42ff2-149">Bu özelliklere aşağıdakiler de dahil olmak üzere avantajları getirin:</span><span class="sxs-lookup"><span data-stu-id="42ff2-149">These characteristics bring a number of benefits, including the following:</span></span>  
  
-   <span data-ttu-id="42ff2-150">Artan okunabilirlik ve bakımı.</span><span class="sxs-lookup"><span data-stu-id="42ff2-150">Increased readability and maintainability.</span></span> <span data-ttu-id="42ff2-151">Belirli bir görevi gerçekleştirmek için her işlevi tasarlandığından bu değişkenlerinin verilir.</span><span class="sxs-lookup"><span data-stu-id="42ff2-151">This is because each function is designed to accomplish a specific task given its arguments.</span></span> <span data-ttu-id="42ff2-152">İşlev üzerinde herhangi bir dış durum bağlı değildir.</span><span class="sxs-lookup"><span data-stu-id="42ff2-152">The function does not rely on any external state.</span></span>  
  
-   <span data-ttu-id="42ff2-153">Daha kolay reiterative geliştirme.</span><span class="sxs-lookup"><span data-stu-id="42ff2-153">Easier reiterative development.</span></span> <span data-ttu-id="42ff2-154">Kod düzenleme için daha kolay olduğundan, tasarım değişiklikleri genellikle uygulamak daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="42ff2-154">Because the code is easier to refactor, changes to design are often easier to implement.</span></span> <span data-ttu-id="42ff2-155">Örneğin, karmaşık bir dönüşüm yazma ve bazı kodlar dönüşümünde birkaç kez yinelenen fark varsayalım.</span><span class="sxs-lookup"><span data-stu-id="42ff2-155">For example, suppose you write a complicated transformation, and then realize that some code is repeated several times in the transformation.</span></span> <span data-ttu-id="42ff2-156">Saf bir yöntem yeniden düzenlemeniz varsa, yan etkileri hakkında endişelenmeden gerçekleştirilse, saf yöntemini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42ff2-156">If you refactor through a pure method, you can call your pure method at will without worrying about side effects.</span></span>  
  
-   <span data-ttu-id="42ff2-157">Daha kolay test ve hata ayıklama.</span><span class="sxs-lookup"><span data-stu-id="42ff2-157">Easier testing and debugging.</span></span> <span data-ttu-id="42ff2-158">Saf işlevleri yalıtım modunda daha kolayca sınanabilir çünkü tipik değerleri, geçerli sınır durumları ve geçersiz kenar durumlarda saf işlev çağrıları test kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42ff2-158">Because pure functions can more easily be tested in isolation, you can write test code that calls the pure function with typical values, valid edge cases, and invalid edge cases.</span></span>  
  
## <a name="transitioning-for-oop-developers"></a><span data-ttu-id="42ff2-159">OOP geliştiriciler için geçiş</span><span class="sxs-lookup"><span data-stu-id="42ff2-159">Transitioning for OOP Developers</span></span>  
 <span data-ttu-id="42ff2-160">Geleneksel nesne odaklı programlama (OOP), çoğu Geliştirici kesinliği/yordam stili programlamada bilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42ff2-160">In traditional object-oriented programming (OOP), most developers are accustomed to programming in the imperative/procedural style.</span></span> <span data-ttu-id="42ff2-161">Saf işlevsel stilde geliştirmek için geçiş yapmak için bunlar kendi düşünmeye ve bunların yaklaşımı geliştirme için bir geçiş yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="42ff2-161">To switch to developing in a pure functional style, they have to make a transition in their thinking and their approach to development.</span></span>  
  
 <span data-ttu-id="42ff2-162">Sorunları çözmek için OOP geliştiriciler sınıfı hiyerarşi tasarımı, üzerinde uygun kapsülleme odaklanmanıza ve sınıf sözleşmeleri açısından düşünün.</span><span class="sxs-lookup"><span data-stu-id="42ff2-162">To solve problems, OOP developers design class hierarchies, focus on proper encapsulation, and think in terms of class contracts.</span></span> <span data-ttu-id="42ff2-163">Nesne türlerinin durumu ve davranış en önemli ve bu sorunları çözmek için sınıflar, arabirimler, devralma ve çok biçimlilik, gibi dil özellikleri sağlanır.</span><span class="sxs-lookup"><span data-stu-id="42ff2-163">The behavior and state of object types are paramount, and language features, such as classes, interfaces, inheritance, and polymorphism, are provided to address these concerns.</span></span>  
  
 <span data-ttu-id="42ff2-164">Buna karşılık, işlevsel programlama veri koleksiyonları saf işlevsel dönüşümleri değerlendirilmesinde bir alıştırma olarak hesaplama sorunları yaklaşıyor.</span><span class="sxs-lookup"><span data-stu-id="42ff2-164">In contrast, functional programming approaches computational problems as an exercise in the evaluation of pure functional transformations of data collections.</span></span> <span data-ttu-id="42ff2-165">İşlevsel programlama durumu ve değişebilir veri engeller ve bunun yerine uygulama işlevlerin vurgular.</span><span class="sxs-lookup"><span data-stu-id="42ff2-165">Functional programming avoids state and mutable data, and instead emphasizes the application of functions.</span></span>  
  
 <span data-ttu-id="42ff2-166">Neyse ki, kesinlik temelli ve işlevsel programlama yaklaşımlar desteklediğinden, Visual Basic işlevsel programlama için tam artık gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="42ff2-166">Fortunately, Visual Basic doesn't require the full leap to functional programming, because it supports both imperative and functional programming approaches.</span></span> <span data-ttu-id="42ff2-167">Bir geliştirici, hangi yaklaşımın belirli bir senaryo için en uygun olan seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42ff2-167">A developer can choose which approach is most appropriate for a particular scenario.</span></span> <span data-ttu-id="42ff2-168">Aslında, programlar genellikle her iki yaklaşımı birleştirir.</span><span class="sxs-lookup"><span data-stu-id="42ff2-168">In fact, programs often combine both approaches.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42ff2-169">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="42ff2-169">See Also</span></span>  
 [<span data-ttu-id="42ff2-170">Giriş saf işlevsel Dönüşümleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42ff2-170">Introduction to Pure Functional Transformations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
 [<span data-ttu-id="42ff2-171">XSLT dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="42ff2-171">XSLT Transformations</span></span>](../../../../standard/data/xml/xslt-transformations.md)  
 [<span data-ttu-id="42ff2-172">Saf işlevleri (Visual Basic) yeniden düzenleme</span><span class="sxs-lookup"><span data-stu-id="42ff2-172">Refactoring Into Pure Functions (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/refactoring-into-pure-functions.md)