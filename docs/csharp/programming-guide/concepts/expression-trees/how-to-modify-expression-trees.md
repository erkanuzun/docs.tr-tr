---
title: "Nasıl yapılır: ifade ağaçlarını (C#) değiştirme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 9b0cd8c2-457e-4833-9e36-31e79545f442
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4db0abec0df2bc4a17dca0ed1ee88b8a38b8ca8a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-modify-expression-trees-c"></a><span data-ttu-id="0218b-102">Nasıl yapılır: ifade ağaçlarını (C#) değiştirme</span><span class="sxs-lookup"><span data-stu-id="0218b-102">How to: Modify Expression Trees (C#)</span></span>
<span data-ttu-id="0218b-103">Bu konu bir ifade ağacına değiştirme gösterir.</span><span class="sxs-lookup"><span data-stu-id="0218b-103">This topic shows you how to modify an expression tree.</span></span> <span data-ttu-id="0218b-104">İfade ağaçları değişmez, bunlar doğrudan değiştirilemiyor anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="0218b-104">Expression trees are immutable, which means that they cannot be modified directly.</span></span> <span data-ttu-id="0218b-105">Bir ifade ağacına değiştirmek için varolan bir ifade ağacına bir kopyasını oluşturun ve bir kopya oluşturduğunuzda gerekli değişiklikleri yapın.</span><span class="sxs-lookup"><span data-stu-id="0218b-105">To change an expression tree, you must create a copy of an existing expression tree and when you create the copy, make the required changes.</span></span> <span data-ttu-id="0218b-106">Kullanabileceğiniz <xref:System.Linq.Expressions.ExpressionVisitor> sınıfı var olan bir ifade ağacına gezme ve onu ziyaret her bir düğüm kopyalamak için.</span><span class="sxs-lookup"><span data-stu-id="0218b-106">You can use the <xref:System.Linq.Expressions.ExpressionVisitor> class to traverse an existing expression tree and to copy each node that it visits.</span></span>  
  
### <a name="to-modify-an-expression-tree"></a><span data-ttu-id="0218b-107">Bir ifade ağacına değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="0218b-107">To modify an expression tree</span></span>  
  
1.  <span data-ttu-id="0218b-108">Yeni bir **konsol uygulaması** projesi.</span><span class="sxs-lookup"><span data-stu-id="0218b-108">Create a new **Console Application** project.</span></span>  
  
2.  <span data-ttu-id="0218b-109">Ekleme bir `using` dosya için yönerge `System.Linq.Expressions` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="0218b-109">Add a `using` directive to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
3.  <span data-ttu-id="0218b-110">Ekleme `AndAlsoModifier` projenize sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0218b-110">Add the `AndAlsoModifier` class to your project.</span></span>  
  
    ```csharp  
    public class AndAlsoModifier : ExpressionVisitor  
    {  
        public Expression Modify(Expression expression)  
        {  
            return Visit(expression);  
        }  
  
        protected override Expression VisitBinary(BinaryExpression b)  
        {  
            if (b.NodeType == ExpressionType.AndAlso)  
            {  
                Expression left = this.Visit(b.Left);  
                Expression right = this.Visit(b.Right);  
  
                // Make this binary expression an OrElse operation instead of an AndAlso operation.  
                return Expression.MakeBinary(ExpressionType.OrElse, left, right, b.IsLiftedToNull, b.Method);  
            }  
  
            return base.VisitBinary(b);  
        }  
    }  
    ```  
  
     <span data-ttu-id="0218b-111">Bu sınıf devralır <xref:System.Linq.Expressions.ExpressionVisitor> sınıfı ve koşullu temsil eden ifadeleri değiştirmek için özelleştirilmiş `AND` işlemleri.</span><span class="sxs-lookup"><span data-stu-id="0218b-111">This class inherits the <xref:System.Linq.Expressions.ExpressionVisitor> class and is specialized to modify expressions that represent conditional `AND` operations.</span></span> <span data-ttu-id="0218b-112">Bu işlemler erişim ilkesinden değiştirir `AND` koşullu için `OR`.</span><span class="sxs-lookup"><span data-stu-id="0218b-112">It changes these operations from a conditional `AND` to a conditional `OR`.</span></span> <span data-ttu-id="0218b-113">Bu sınıfı geçersiz kılma işlemleri yapmak için <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> temel türü yöntemi için koşullu `AND` ifadeleri ikili ifadeler olarak temsil.</span><span class="sxs-lookup"><span data-stu-id="0218b-113">To do this, the class overrides the <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> method of the base type, because conditional `AND` expressions are represented as binary expressions.</span></span> <span data-ttu-id="0218b-114">İçinde `VisitBinary` kendisine geçirilen ifade koşullu temsil ediyorsa yöntemi `AND` , işlem kodu oluşturan koşullu içeren yeni bir ifade `OR` işleci koşul yerine `AND` işleç.</span><span class="sxs-lookup"><span data-stu-id="0218b-114">In the `VisitBinary` method, if the expression that is passed to it represents a conditional `AND` operation, the code constructs a new expression that contains the conditional `OR` operator instead of the conditional `AND` operator.</span></span> <span data-ttu-id="0218b-115">Varsa geçirilir ifade `VisitBinary` koşullu göstermiyor `AND` işlemi, yöntemi için temel sınıf uygulamasını erteler.</span><span class="sxs-lookup"><span data-stu-id="0218b-115">If the expression that is passed to `VisitBinary` does not represent a conditional `AND` operation, the method defers to the base class implementation.</span></span> <span data-ttu-id="0218b-116">İletilen ifade ağaçları gibi yapı düğümlerini ancak düğümleri olan ifade ağaçları yerine kendi alt ağaçları olan taban sınıf yöntemlerini yinelemeli olarak ziyaretçi tarafından üretilen.</span><span class="sxs-lookup"><span data-stu-id="0218b-116">The base class methods construct nodes that are like the expression trees that are passed in, but the nodes have their sub trees replaced with the expression trees that are produced recursively by the visitor.</span></span>  
  
4.  <span data-ttu-id="0218b-117">Ekleme bir `using` dosya için yönerge `System.Linq.Expressions` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="0218b-117">Add a `using` directive to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
5.  <span data-ttu-id="0218b-118">Kodu ekleyin `Main` yöntemi Program.cs dosyasında bir ifade ağacına oluşturun ve bu yönteme geçirin onu değiştirir.</span><span class="sxs-lookup"><span data-stu-id="0218b-118">Add code to the `Main` method in the Program.cs file to create an expression tree and pass it to the method that will modify it.</span></span>  
  
    ```csharp  
    Expression<Func<string, bool>> expr = name => name.Length > 10 && name.StartsWith("G");  
    Console.WriteLine(expr);  
  
    AndAlsoModifier treeModifier = new AndAlsoModifier();  
    Expression modifiedExpr = treeModifier.Modify((Expression) expr);  
  
    Console.WriteLine(modifiedExpr);  
  
    /*  This code produces the following output:  
  
        name => ((name.Length > 10) && name.StartsWith("G"))  
        name => ((name.Length > 10) || name.StartsWith("G"))  
    */  
    ```  
  
     <span data-ttu-id="0218b-119">Koşullu içeren bir ifade kod oluşturur `AND` işlemi.</span><span class="sxs-lookup"><span data-stu-id="0218b-119">The code creates an expression that contains a conditional `AND` operation.</span></span> <span data-ttu-id="0218b-120">Ardından bir örneğini oluşturur `AndAlsoModifier` sınıfı ve ifade geçirir `Modify` bu sınıfın yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0218b-120">It then creates an instance of the `AndAlsoModifier` class and passes the expression to the `Modify` method of this class.</span></span> <span data-ttu-id="0218b-121">Değişikliği göstermek için özgün ve değiştirilen ifade ağaçları yüzdelik.</span><span class="sxs-lookup"><span data-stu-id="0218b-121">Both the original and the modified expression trees are outputted to show the change.</span></span>  
  
6.  <span data-ttu-id="0218b-122">Derleme ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0218b-122">Compile and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0218b-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0218b-123">See Also</span></span>  
 [<span data-ttu-id="0218b-124">Nasıl yapılır: ifade ağaçlarını (C#) yürütme</span><span class="sxs-lookup"><span data-stu-id="0218b-124">How to: Execute Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)  
 [<span data-ttu-id="0218b-125">İfade ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="0218b-125">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)