---
title: "Nasıl yapılır: Çizgi Çizmek için Kalem Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
ms.assetid: 0828c331-a438-4bdd-a4d6-3ef1e59e8795
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 481200d1383fd6cc5e95379823af651c78275cb5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-pen-to-draw-lines"></a><span data-ttu-id="8ce3d-102">Nasıl yapılır: Çizgi Çizmek için Kalem Kullanma</span><span class="sxs-lookup"><span data-stu-id="8ce3d-102">How to: Use a Pen to Draw Lines</span></span>
<span data-ttu-id="8ce3d-103">Çizgi çizmek için size gereken bir <xref:System.Drawing.Graphics> nesne ve <xref:System.Drawing.Pen> nesne.</span><span class="sxs-lookup"><span data-stu-id="8ce3d-103">To draw lines, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="8ce3d-104"><xref:System.Drawing.Graphics> Nesnesi sağlar <xref:System.Drawing.Graphics.DrawLine%2A> yöntemi ve <xref:System.Drawing.Pen> nesnesi satırının renk ve genişlik gibi özellikleri saklar.</span><span class="sxs-lookup"><span data-stu-id="8ce3d-104">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawLine%2A> method, and the <xref:System.Drawing.Pen> object stores features of the line, such as color and width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ce3d-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="8ce3d-105">Example</span></span>  
 <span data-ttu-id="8ce3d-106">Aşağıdaki örnek bir satırından çizer (20, 10) için (300, 100).</span><span class="sxs-lookup"><span data-stu-id="8ce3d-106">The following example draws a line from (20, 10) to (300, 100).</span></span> <span data-ttu-id="8ce3d-107">İlk ifade kullanan <xref:System.Drawing.Pen.%23ctor%2A> siyah kalem oluşturmak için sınıfı oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="8ce3d-107">The first statement uses the <xref:System.Drawing.Pen.%23ctor%2A> class constructor to create a black pen.</span></span> <span data-ttu-id="8ce3d-108">Bir bağımsız değişken geçirilen <xref:System.Drawing.Pen.%23ctor%2A> Oluşturucusu olan bir <xref:System.Drawing.Color> ile oluşturulan nesne <xref:System.Drawing.Color.FromArgb%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8ce3d-108">The one argument passed to the <xref:System.Drawing.Pen.%23ctor%2A> constructor is a <xref:System.Drawing.Color> object created with the <xref:System.Drawing.Color.FromArgb%2A> method.</span></span> <span data-ttu-id="8ce3d-109">Oluşturmak için kullanılan değerleri <xref:System.Drawing.Color> nesne — (255, 0, 0, 0) — rengi alfa, kırmızı, yeşil ve mavi bileşenlerinin karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="8ce3d-109">The values used to create the <xref:System.Drawing.Color> object — (255, 0, 0, 0) — correspond to the alpha, red, green, and blue components of the color.</span></span> <span data-ttu-id="8ce3d-110">Bu değerleri donuk siyah kalem tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="8ce3d-110">These values define an opaque black pen.</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8ce3d-111">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="8ce3d-111">Compiling the Code</span></span>  
 <span data-ttu-id="8ce3d-112">Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="8ce3d-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ce3d-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8ce3d-113">See Also</span></span>  
 <xref:System.Drawing.Pen>  
 [<span data-ttu-id="8ce3d-114">Çizgiler ve şekiller çizmek için kalem kullanma</span><span class="sxs-lookup"><span data-stu-id="8ce3d-114">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [<span data-ttu-id="8ce3d-115">Kalemler, çizgiler ve dikdörtgenler GDI +'da</span><span class="sxs-lookup"><span data-stu-id="8ce3d-115">Pens, Lines, and Rectangles in GDI+</span></span>](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)