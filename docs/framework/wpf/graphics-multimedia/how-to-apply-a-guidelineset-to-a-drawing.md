---
title: "Nasıl yapılır: Çizime GuidelineSet Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GuidelineSet property [WPF], applying to drawings
- graphics [WPF], GuidelineSet property
ms.assetid: 45f3e0b4-8820-45a7-b865-b8ea5b17b0c8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dd8d93d128c03cb9ee482860603e5734e96c6fc2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-a-guidelineset-to-a-drawing"></a><span data-ttu-id="d087f-102">Nasıl yapılır: Çizime GuidelineSet Uygulama</span><span class="sxs-lookup"><span data-stu-id="d087f-102">How to: Apply a GuidelineSet to a Drawing</span></span>
<span data-ttu-id="d087f-103">Bu örnek nasıl uygulanacağını gösterir bir <xref:System.Windows.Media.GuidelineSet> için bir <xref:System.Windows.Media.DrawingGroup>.</span><span class="sxs-lookup"><span data-stu-id="d087f-103">This example shows how to apply a <xref:System.Windows.Media.GuidelineSet> to a <xref:System.Windows.Media.DrawingGroup>.</span></span>  
  
 <span data-ttu-id="d087f-104"><xref:System.Windows.Media.DrawingGroup> Sınıftır türü <xref:System.Windows.Media.Drawing> olan bir <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="d087f-104">The <xref:System.Windows.Media.DrawingGroup> class is the only type of <xref:System.Windows.Media.Drawing> that has a <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> property.</span></span> <span data-ttu-id="d087f-105">Uygulanacak bir <xref:System.Windows.Media.GuidelineSet> başka türde <xref:System.Windows.Media.Drawing>, ekleyebilmek için bir <xref:System.Windows.Media.DrawingGroup> ve ardından uygulama <xref:System.Windows.Media.GuidelineSet> için <xref:System.Windows.Media.DrawingGroup>.</span><span class="sxs-lookup"><span data-stu-id="d087f-105">To apply a <xref:System.Windows.Media.GuidelineSet> to another type of <xref:System.Windows.Media.Drawing>, add it to a <xref:System.Windows.Media.DrawingGroup> and then apply the <xref:System.Windows.Media.GuidelineSet> to your <xref:System.Windows.Media.DrawingGroup>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d087f-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="d087f-106">Example</span></span>  
 <span data-ttu-id="d087f-107">Aşağıdaki örnekte iki oluşturur <xref:System.Windows.Media.DrawingGroup> tek fark neredeyse aynı; nesneleri: ikinci <xref:System.Windows.Media.DrawingGroup> sahip bir <xref:System.Windows.Media.GuidelineSet> ve ilk desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d087f-107">The following example creates two <xref:System.Windows.Media.DrawingGroup> objects that are almost identical; the only difference is: the second <xref:System.Windows.Media.DrawingGroup> has a <xref:System.Windows.Media.GuidelineSet> and the first does not.</span></span>  
  
 <span data-ttu-id="d087f-108">Aşağıdaki çizimde örnek çıktısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d087f-108">The following illustration shows the output from the example.</span></span> <span data-ttu-id="d087f-109">İşleme fark nedeniyle arasında iki <xref:System.Windows.Media.DrawingGroup> nesnedir nedenle hafif, çizimlerin bölümleri genişletilir.</span><span class="sxs-lookup"><span data-stu-id="d087f-109">Because the rendering difference between the two <xref:System.Windows.Media.DrawingGroup> objects is so subtle, portions of the drawings are enlarged.</span></span>  
  
 <span data-ttu-id="d087f-110">![İle ve GuidelineSet olmadan DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")</span><span class="sxs-lookup"><span data-stu-id="d087f-110">![A DrawingGroup with and without a GuidelineSet](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupGuidelineSetExample.cs#graphicsmmdrawinggroupguidelinesetexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupGuidelineSetExample.xaml#graphicsmmdrawinggroupguidelinesetexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="d087f-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d087f-111">See Also</span></span>  
 <xref:System.Windows.Media.DrawingGroup>  
 <xref:System.Windows.Media.GuidelineSet>  
 [<span data-ttu-id="d087f-112">Çizim nesnelerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="d087f-112">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)