---
title: Atomized XName ve XNamespace nesneleri (LINQ-XML) (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21ee7585-7df9-40b4-8c76-a12bb5f29bb3
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3d3c0b1278411c41d002c546f4b1a3be9975a801
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-visual-basic"></a><span data-ttu-id="c3b68-102">Atomized XName ve XNamespace nesneleri (LINQ-XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3b68-102">Atomized XName and XNamespace Objects (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="c3b68-103"><xref:System.Xml.Linq.XName>ve <xref:System.Xml.Linq.XNamespace> nesneler *atomized*; diğer bir deyişle, bunlar bunlar aynı tam adı içeriyorsa, aynı nesneye başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="c3b68-103"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> objects are *atomized*; that is, if they contain the same qualified name, they refer to the same object.</span></span> <span data-ttu-id="c3b68-104">Bu sorguları için performans avantajı verir: eşitlik için iki atomized adları karşılaştırdığınızda, temel alınan Ara dile yalnızca iki başvurunun aynı nesneye işaret olup olmadığını belirlemek vardır.</span><span class="sxs-lookup"><span data-stu-id="c3b68-104">This yields performance benefits for queries: When you compare two atomized names for equality, the underlying intermediate language only has to determine whether the two references point to the same object.</span></span> <span data-ttu-id="c3b68-105">Arka plandaki kod zaman alıcı olabilir karşılaştırmaları dize gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c3b68-105">The underlying code does not have to do string comparisons, which would be time consuming.</span></span>  
  
## <a name="atomization-semantics"></a><span data-ttu-id="c3b68-106">Atomization semantiği</span><span class="sxs-lookup"><span data-stu-id="c3b68-106">Atomization Semantics</span></span>  
 <span data-ttu-id="c3b68-107">Atomization anlamına gelir, iki <xref:System.Xml.Linq.XName> nesneler aynı yerel ada sahip ve aynı ad alanında oldukları, aynı örneğini paylaşırlar.</span><span class="sxs-lookup"><span data-stu-id="c3b68-107">Atomization means that if two <xref:System.Xml.Linq.XName> objects have the same local name, and they are in the same namespace, they share the same instance.</span></span> <span data-ttu-id="c3b68-108">Aynı şekilde, iki <xref:System.Xml.Linq.XNamespace> nesneler sahip aynı ad alanı URI, aynı örneğini paylaşırlar.</span><span class="sxs-lookup"><span data-stu-id="c3b68-108">In the same way, if two <xref:System.Xml.Linq.XNamespace> objects have the same namespace URI, they share the same instance.</span></span>  
  
 <span data-ttu-id="c3b68-109">Bir sınıf atomized nesneleri etkinleştirmek sınıf oluşturucusu özel ve ortak değil olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c3b68-109">For a class to enable atomized objects, the constructor for the class must be private, not public.</span></span> <span data-ttu-id="c3b68-110">Oluşturucu ortak olsaydı, atomized olmayan bir nesne oluşturabilirsiniz olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="c3b68-110">This is because if the constructor were public, you could create a non-atomized object.</span></span> <span data-ttu-id="c3b68-111"><xref:System.Xml.Linq.XName> Ve <xref:System.Xml.Linq.XNamespace> sınıfları uygulayan bir dizeye dönüştürmek için bir örtük dönüşüm işleci bir <xref:System.Xml.Linq.XName> veya <xref:System.Xml.Linq.XNamespace>.</span><span class="sxs-lookup"><span data-stu-id="c3b68-111">The <xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> classes implement an implicit conversion operator to convert a string into an <xref:System.Xml.Linq.XName> or <xref:System.Xml.Linq.XNamespace>.</span></span> <span data-ttu-id="c3b68-112">Bu nesneler örneği nereden budur.</span><span class="sxs-lookup"><span data-stu-id="c3b68-112">This is how you get an instance of these objects.</span></span> <span data-ttu-id="c3b68-113">Oluşturucusu erişilemediğinden bir kurucu kullanarak bir örneği elde edilemiyor.</span><span class="sxs-lookup"><span data-stu-id="c3b68-113">You cannot get an instance by using a constructor, because the constructor is inaccessible.</span></span>  
  
 <span data-ttu-id="c3b68-114"><xref:System.Xml.Linq.XName>ve <xref:System.Xml.Linq.XNamespace> da iki karşılaştırılan başvuruları aynı örneğini olan nesneleri olup olmadığını belirlemek için eşitlik ve eşitsizlik, işleçler.</span><span class="sxs-lookup"><span data-stu-id="c3b68-114"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> also implement the equality and inequality operators, to determine whether the two objects being compared are references to the same instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3b68-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="c3b68-115">Example</span></span>  
 <span data-ttu-id="c3b68-116">Aşağıdaki kod bazı oluşturur <xref:System.Xml.Linq.XElement> nesneleri ve aynı örnek paylaşım aynı adları gösterir.</span><span class="sxs-lookup"><span data-stu-id="c3b68-116">The following code creates some <xref:System.Xml.Linq.XElement> objects and demonstrates that identical names share the same instance.</span></span>  
  
```vb  
Dim r1 As New XElement("Root", "data1")  
Dim r2 As XElement = XElement.Parse("<Root>data2</Root>")  
  
If DirectCast(r1.Name, Object) = DirectCast(r2.Name, Object) Then  
    Console.WriteLine("r1 and r2 have names that refer to the same instance.")  
Else  
    Console.WriteLine("Different")  
End If  
  
Dim n As XName = "Root"  
  
If DirectCast(n, Object) = DirectCast(r1.Name, Object) Then  
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.")  
Else  
    Console.WriteLine("Different")  
End If  
```  
  
 <span data-ttu-id="c3b68-117">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="c3b68-117">This example produces the following output:</span></span>  
  
```  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 <span data-ttu-id="c3b68-118">Ele eksen yöntemlerden birini kullandığınızda, daha önce belirtildiği gibi faydası atomized nesnelerin ise bir <xref:System.Xml.Linq.XName> bir parametre olarak eksen yöntemi yalnızca iki başvuru istenen öğelerini seçmek için aynı örnek adlarını belirlemek vardır.</span><span class="sxs-lookup"><span data-stu-id="c3b68-118">As mentioned earlier, the benefit of atomized objects is that when you use one of the axis methods that take an <xref:System.Xml.Linq.XName> as a parameter, the axis method only has to determine that two names reference the same instance to select the desired elements.</span></span>  
  
 <span data-ttu-id="c3b68-119">Aşağıdaki örnek geçirmeden bir <xref:System.Xml.Linq.XName> için <xref:System.Xml.Linq.XContainer.Descendants%2A> sonra daha iyi performans nedeniyle atomization düzeni sahip yöntem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="c3b68-119">The following example passes an <xref:System.Xml.Linq.XName> to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method call, which then has better performance because of the atomization pattern.</span></span>  
  
```vb  
Dim root As New XElement("Root", New XElement("C1", 1), New XElement("Z1", New XElement("C1", 2), New XElement("C1", 1)))  
  
Dim query = From e In root.Descendants("C1") Where CInt(e) = 1e  
  
For Each z As var In query  
    Console.WriteLine(z)  
Next  
```  
  
 <span data-ttu-id="c3b68-120">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="c3b68-120">This example produces the following output:</span></span>  
  
```xml  
<C1>1</C1>  
<C1>1</C1>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3b68-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c3b68-121">See Also</span></span>  
 [<span data-ttu-id="c3b68-122">Performans (LINQ-XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3b68-122">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)