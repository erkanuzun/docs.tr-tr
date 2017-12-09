---
title: "Nasıl yapılır: ilgili öğeleri (XPath-LINQ-XML) bulma (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 41b386ee-562d-4841-bd6b-e44a7eb69f26
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3b128c8aa801c445e5e8cd2b4aab4e55f22b086c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-related-elements-xpath-linq-to-xml-c"></a><span data-ttu-id="0308f-102">Nasıl yapılır: ilgili öğeleri (XPath-LINQ-XML) bulma (C#)</span><span class="sxs-lookup"><span data-stu-id="0308f-102">How to: Find Related Elements (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="0308f-103">Bu konu, bir öğe başka bir öğe değeri tarafından başvurulan bir öznitelik seçme alma gösterir.</span><span class="sxs-lookup"><span data-stu-id="0308f-103">This topic shows how to get an element selecting on an attribute that is referred to by the value of another element.</span></span>  
  
 <span data-ttu-id="0308f-104">XPath ifadesi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="0308f-104">The XPath expression is:</span></span>  
  
 `.//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]`  
  
## <a name="example"></a><span data-ttu-id="0308f-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="0308f-105">Example</span></span>  
 <span data-ttu-id="0308f-106">Bu örnek 12 bulur `Order` öğesini ve ardından bu sipariş için müşteri bulur.</span><span class="sxs-lookup"><span data-stu-id="0308f-106">This example finds the 12th `Order` element, and then finds the customer for that order.</span></span>  
  
 <span data-ttu-id="0308f-107">.Net listesinde içine dizin 'zero' bağlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0308f-107">Note that indexing into a list in .Net is 'zero' based.</span></span> <span data-ttu-id="0308f-108">Bir XPath kuralının koşulu düğümler koleksiyonuna dizin '' dayalı biridir.</span><span class="sxs-lookup"><span data-stu-id="0308f-108">Indexing into a collection of nodes in an XPath predicate is 'one' based.</span></span> <span data-ttu-id="0308f-109">Bu örnekte bu farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="0308f-109">This example reflects this difference.</span></span>  
  
 <span data-ttu-id="0308f-110">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: müşteriler ve siparişler (LINQ-XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="0308f-110">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
XDocument co = XDocument.Load("CustomersOrders.xml");  
  
// LINQ to XML query  
XElement customer1 =  
    (from el in co.Descendants("Customer")  
     where (string)el.Attribute("CustomerID") ==  
          (string)(co  
              .Element("Root")  
              .Element("Orders")  
              .Elements("Order")  
              .ToList()[11]  
              .Element("CustomerID"))  
    select el)  
    .First();  
  
// An alternate way to write the query that avoids creation  
// of a System.Collections.Generic.List:  
XElement customer2 =  
    (from el in co.Descendants("Customer")  
     where (string)el.Attribute("CustomerID") ==  
          (string)(co  
              .Element("Root")  
              .Element("Orders")  
              .Elements("Order")  
              .Skip(11).First()  
              .Element("CustomerID"))  
    select el)  
    .First();  
  
// XPath expression  
XElement customer3 = co.XPathSelectElement(  
  ".//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]");  
  
if (customer1 == customer2 && customer1 == customer3)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(customer1);  
```  
  
 <span data-ttu-id="0308f-111">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="0308f-111">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Customer CustomerID="HUNGC">  
  <CompanyName>Hungry Coyote Import Store</CompanyName>  
  <ContactName>Yoshi Latimer</ContactName>  
  <ContactTitle>Sales Representative</ContactTitle>  
  <Phone>(503) 555-6874</Phone>  
  <Fax>(503) 555-2376</Fax>  
  <FullAddress>  
    <Address>City Center Plaza 516 Main St.</Address>  
    <City>Elgin</City>  
    <Region>OR</Region>  
    <PostalCode>97827</PostalCode>  
    <Country>USA</Country>  
  </FullAddress>  
</Customer>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0308f-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0308f-112">See Also</span></span>  
 [<span data-ttu-id="0308f-113">LINQ-XML XPath kullanıcıların (C#)</span><span class="sxs-lookup"><span data-stu-id="0308f-113">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)