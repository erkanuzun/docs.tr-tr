---
title: "Nasıl yapılır: Windows Forms DataGridView Denetiminde Geçerli Hücreyi Alma ve Ayarlama"
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
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bb63c48831e19ce3cbb166e899aeee8b6a331839
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="fd03a-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Geçerli Hücreyi Alma ve Ayarlama</span><span class="sxs-lookup"><span data-stu-id="fd03a-102">How to: Get and Set the Current Cell in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="fd03a-103">Etkileşim <xref:System.Windows.Forms.DataGridView> hangi hücrenin şu anda etkin olan program aracılığıyla bulmak, genellikle gerektirir.</span><span class="sxs-lookup"><span data-stu-id="fd03a-103">Interaction with the <xref:System.Windows.Forms.DataGridView> often requires that you programmatically discover which cell is currently active.</span></span> <span data-ttu-id="fd03a-104">Geçerli hücreyi değiştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="fd03a-104">You may also need to change the current cell.</span></span> <span data-ttu-id="fd03a-105">Bu görevleri gerçekleştirebilir <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="fd03a-105">You can perform these tasks with the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fd03a-106">Bir satır veya sahip sütunu geçerli hücre ayarlanamıyor kendi <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> özelliğini `false`.</span><span class="sxs-lookup"><span data-stu-id="fd03a-106">You cannot set the current cell in a row or column that has its <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> property set to `false`.</span></span>  
  
 <span data-ttu-id="fd03a-107">Bağlı olarak <xref:System.Windows.Forms.DataGridView> geçerli hücreyi değiştirme denetiminin seçim modunu seçimi değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd03a-107">Depending on the <xref:System.Windows.Forms.DataGridView> control's selection mode, changing the current cell can change the selection.</span></span> <span data-ttu-id="fd03a-108">Daha fazla bilgi için bkz: [Windows Forms DataGridView denetimindeki seçim modları](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="fd03a-108">For more information, see [Selection Modes in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-get-the-current-cell-programmatically"></a><span data-ttu-id="fd03a-109">Geçerli hücreyi programlı olarak almak için</span><span class="sxs-lookup"><span data-stu-id="fd03a-109">To get the current cell programmatically</span></span>  
  
-   <span data-ttu-id="fd03a-110">Kullanım <xref:System.Windows.Forms.DataGridView> denetimin <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="fd03a-110">Use the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a><span data-ttu-id="fd03a-111">Geçerli hücreyi programlı olarak ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="fd03a-111">To set the current cell programmatically</span></span>  
  
-   <span data-ttu-id="fd03a-112">Ayarlama <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> özelliği <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="fd03a-112">Set the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="fd03a-113">Aşağıdaki kod örneğinde, 0, 1 sütunu satır için geçerli hücreyi ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="fd03a-113">In the following code example, the current cell is set to row 0, column 1.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fd03a-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="fd03a-114">Compiling the Code</span></span>  
 <span data-ttu-id="fd03a-115">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="fd03a-115">This example requires:</span></span>  
  
-   <span data-ttu-id="fd03a-116"><xref:System.Windows.Forms.Button>adlı denetimleri `getCurrentCellButton` ve `setCurrentCellButton`.</span><span class="sxs-lookup"><span data-stu-id="fd03a-116"><xref:System.Windows.Forms.Button> controls named `getCurrentCellButton` and `setCurrentCellButton`.</span></span> <span data-ttu-id="fd03a-117">İçinde [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], ilişkilendirmeniz gerekir <xref:System.Windows.Forms.Control.Click> kod örneği ilişkili olay işleyicisini her düğme için olayları.</span><span class="sxs-lookup"><span data-stu-id="fd03a-117">In [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], you must attach the <xref:System.Windows.Forms.Control.Click> events for each button to the associated event handler in the example code.</span></span>  
  
-   <span data-ttu-id="fd03a-118">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="fd03a-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="fd03a-119">Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="fd03a-119">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd03a-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fd03a-120">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="fd03a-121">Temel sütun, satır ve hücre özellikleri Windows Forms DataGridView denetiminde</span><span class="sxs-lookup"><span data-stu-id="fd03a-121">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [<span data-ttu-id="fd03a-122">Windows Forms DataGridView denetimindeki seçim modları</span><span class="sxs-lookup"><span data-stu-id="fd03a-122">Selection Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)