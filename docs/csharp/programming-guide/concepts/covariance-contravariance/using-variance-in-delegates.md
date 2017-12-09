---
title: Temsilcilerde varyans (C#) kullanma
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cb8512945fa7aefa9afce4f4f1f8e0200dc3e2b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="using-variance-in-delegates-c"></a><span data-ttu-id="25a45-102">Temsilcilerde varyans (C#) kullanma</span><span class="sxs-lookup"><span data-stu-id="25a45-102">Using Variance in Delegates (C#)</span></span>
<span data-ttu-id="25a45-103">Bir temsilci için bir yöntem atadığınızda *Kovaryans* ve *değişken karşıtı* yöntemi imza bir temsilci türüyle eşleştirmek için esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="25a45-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="25a45-104">Kovaryans temsilci içinde tanımlanan daha fazla türetilmiş dönüş türüne sahip bir yöntem izin verir.</span><span class="sxs-lookup"><span data-stu-id="25a45-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="25a45-105">Değişken karşıtı temsilci türü olandan daha az türetilmiş parametre türleri içeren bir yöntem izin verir.</span><span class="sxs-lookup"><span data-stu-id="25a45-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>  
  
## <a name="example-1-covariance"></a><span data-ttu-id="25a45-106">Örnek 1: kovaryansı</span><span class="sxs-lookup"><span data-stu-id="25a45-106">Example 1: Covariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="25a45-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25a45-107">Description</span></span>  
 <span data-ttu-id="25a45-108">Bu örnek, temsilci imza dönüş türden türetilmiş dönüş türlerine sahip yöntemleriyle temsilciler'ın nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="25a45-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="25a45-109">Tarafından döndürülen veri türünü `DogsHandler` türü `Dogs`, den türetilen `Mammals` temsilci tanımlanan türü.</span><span class="sxs-lookup"><span data-stu-id="25a45-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>  
  
### <a name="code"></a><span data-ttu-id="25a45-110">Kod</span><span class="sxs-lookup"><span data-stu-id="25a45-110">Code</span></span>  
  
```csharp  
class Mammals{}  
class Dogs : Mammals{}  
  
class Program  
{  
    // Define the delegate.  
    public delegate Mammals HandlerMethod();  
  
    public static Mammals MammalsHandler()  
    {  
        return null;  
    }  
  
    public static Dogs DogsHandler()  
    {  
        return null;  
    }  
  
    static void Test()  
    {  
        HandlerMethod handlerMammals = MammalsHandler;  
  
        // Covariance enables this assignment.  
        HandlerMethod handlerDogs = DogsHandler;  
    }  
}  
```  
  
## <a name="example-2-contravariance"></a><span data-ttu-id="25a45-111">Örnek 2: değişken karşıtı</span><span class="sxs-lookup"><span data-stu-id="25a45-111">Example 2: Contravariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="25a45-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25a45-112">Description</span></span>  
 <span data-ttu-id="25a45-113">Bu örnek temsilciler türünün temel türleri temsilci imza parametre türü parametrelerine sahip yöntemleriyle nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="25a45-113">This example demonstrates how delegates can be used with methods that have parameters of a type that are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="25a45-114">Değişken karşıtı ile bir olay işleyicisi yerine ayrı işleyicileri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25a45-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="25a45-115">Örneğin, kabul eden olay işleyicisi oluşturabilirsiniz bir `EventArgs` giriş parametresi ve onunla kullanmak bir `Button.MouseClick` gönderir olay bir `MouseEventArgs` türünü bir parametre olarak ve ile bir `TextBox.KeyDown` gönderir olay bir `KeyEventArgs` parametresi.</span><span class="sxs-lookup"><span data-stu-id="25a45-115">For example, you can create an event handler that accepts an `EventArgs` input parameter and use it with a `Button.MouseClick` event that sends a `MouseEventArgs` type as a parameter, and also with a `TextBox.KeyDown` event that sends a `KeyEventArgs` parameter.</span></span>  
  
### <a name="code"></a><span data-ttu-id="25a45-116">Kod</span><span class="sxs-lookup"><span data-stu-id="25a45-116">Code</span></span>  
  
```csharp  
// Event handler that accepts a parameter of the EventArgs type.  
private void MultiHandler(object sender, System.EventArgs e)  
{  
    label1.Text = System.DateTime.Now.ToString();  
}  
  
public Form1()  
{  
    InitializeComponent();  
  
    // You can use a method that has an EventArgs parameter,  
    // although the event expects the KeyEventArgs parameter.  
    this.button1.KeyDown += this.MultiHandler;  
  
    // You can use the same method   
    // for an event that expects the MouseEventArgs parameter.  
    this.button1.MouseClick += this.MultiHandler;  
  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="25a45-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="25a45-117">See Also</span></span>  
 [<span data-ttu-id="25a45-118">Temsilcilerde varyans (C#)</span><span class="sxs-lookup"><span data-stu-id="25a45-118">Variance in Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)  
 [<span data-ttu-id="25a45-119">İşlev ve eylem genel temsilciler (C#) için varyans kullanma</span><span class="sxs-lookup"><span data-stu-id="25a45-119">Using Variance for Func and Action Generic Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)