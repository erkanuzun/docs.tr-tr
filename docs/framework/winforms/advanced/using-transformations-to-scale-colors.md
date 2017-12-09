---
title: "Renkleri Ölçeklendirmek için Dönüştürmeleri Kullanma"
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
- transformations [Windows Forms], for scaling colors
- colors [Windows Forms], scaling
ms.assetid: df23c887-7fd6-4b15-ad94-e30b5bd4b849
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a4584b74cd7a394f7dd04d0cfba150b907ca7c82
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="using-transformations-to-scale-colors"></a><span data-ttu-id="9ba68-102">Renkleri Ölçeklendirmek için Dönüştürmeleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="9ba68-102">Using Transformations to Scale Colors</span></span>
<span data-ttu-id="9ba68-103">Ölçeklendirme dönüştürme, bir veya daha fazla bir sayıyla dört renk bileşenleri çarpar.</span><span class="sxs-lookup"><span data-stu-id="9ba68-103">A scaling transformation multiplies one or more of the four color components by a number.</span></span> <span data-ttu-id="9ba68-104">Ölçeklendirme temsil eden renk matrisi girişi aşağıdaki tabloda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9ba68-104">The color matrix entries that represent scaling are given in the following table.</span></span>  
  
|<span data-ttu-id="9ba68-105">Ölçeklendirilmesi bileşeni</span><span class="sxs-lookup"><span data-stu-id="9ba68-105">Component to be scaled</span></span>|<span data-ttu-id="9ba68-106">Matris giriş</span><span class="sxs-lookup"><span data-stu-id="9ba68-106">Matrix entry</span></span>|  
|----------------------------|------------------|  
|<span data-ttu-id="9ba68-107">kırmızı</span><span class="sxs-lookup"><span data-stu-id="9ba68-107">Red</span></span>|<span data-ttu-id="9ba68-108">[0][0]</span><span class="sxs-lookup"><span data-stu-id="9ba68-108">[0][0]</span></span>|  
|<span data-ttu-id="9ba68-109">Yeşil</span><span class="sxs-lookup"><span data-stu-id="9ba68-109">Green</span></span>|<span data-ttu-id="9ba68-110">[1][1]</span><span class="sxs-lookup"><span data-stu-id="9ba68-110">[1][1]</span></span>|  
|<span data-ttu-id="9ba68-111">Mavi</span><span class="sxs-lookup"><span data-stu-id="9ba68-111">Blue</span></span>|<span data-ttu-id="9ba68-112">[2][2]</span><span class="sxs-lookup"><span data-stu-id="9ba68-112">[2][2]</span></span>|  
|<span data-ttu-id="9ba68-113">Alfa</span><span class="sxs-lookup"><span data-stu-id="9ba68-113">Alpha</span></span>|<span data-ttu-id="9ba68-114">[3][3]</span><span class="sxs-lookup"><span data-stu-id="9ba68-114">[3][3]</span></span>|  
  
## <a name="scaling-one-color"></a><span data-ttu-id="9ba68-115">Bir renk ölçeklendirme</span><span class="sxs-lookup"><span data-stu-id="9ba68-115">Scaling One Color</span></span>  
 <span data-ttu-id="9ba68-116">Aşağıdaki örnek oluşturan bir <xref:System.Drawing.Image> ColorBars2.bmp dosyasından nesnesi.</span><span class="sxs-lookup"><span data-stu-id="9ba68-116">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars2.bmp.</span></span> <span data-ttu-id="9ba68-117">Ardından kod, her piksel mavi bileşeninin görüntüde 2 faktörüyle ölçeklendirir.</span><span class="sxs-lookup"><span data-stu-id="9ba68-117">Then the code scales the blue component of each pixel in the image by a factor of 2.</span></span> <span data-ttu-id="9ba68-118">Özgün görüntüsüne dönüştürülmüş yansımasının yanında çizilir.</span><span class="sxs-lookup"><span data-stu-id="9ba68-118">The original image is drawn alongside the transformed image.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.RecoloringImages#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#41)]  
  
 <span data-ttu-id="9ba68-119">Aşağıdaki çizimde özgün resim soldaki ve ölçeklendirilmiş görüntü sağ tarafta gösterir.</span><span class="sxs-lookup"><span data-stu-id="9ba68-119">The following illustration shows the original image on the left and the scaled image on the right.</span></span>  
  
 <span data-ttu-id="9ba68-120">![Renkleri ölçeklendirmek](../../../../docs/framework/winforms/advanced/media/colortrans3.png "colortrans3")</span><span class="sxs-lookup"><span data-stu-id="9ba68-120">![Scale Colors](../../../../docs/framework/winforms/advanced/media/colortrans3.png "colortrans3")</span></span>  
  
 <span data-ttu-id="9ba68-121">Aşağıdaki tabloda, önce ve sonra mavi ölçeklendirme dört Çubuklar için renk vektörlerinin listeler.</span><span class="sxs-lookup"><span data-stu-id="9ba68-121">The following table lists the color vectors for the four bars before and after the blue scaling.</span></span> <span data-ttu-id="9ba68-122">Dördüncü renk çubuğu mavi bileşeni için 0,6 0,8 oluştu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9ba68-122">Note that the blue component in the fourth color bar went from 0.8 to 0.6.</span></span> <span data-ttu-id="9ba68-123">Çünkü [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] sonucu yalnızca kesirli kısmını korur.</span><span class="sxs-lookup"><span data-stu-id="9ba68-123">That is because [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] retains only the fractional part of the result.</span></span> <span data-ttu-id="9ba68-124">Örneğin, (2)(0.8) 1.6, = ve kesirli 1.6 0,6 bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="9ba68-124">For example, (2)(0.8) = 1.6, and the fractional part of 1.6 is 0.6.</span></span> <span data-ttu-id="9ba68-125">Yalnızca kesir bölümünü korunuyor sonucu her zaman [0, 1] aralığında olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9ba68-125">Retaining only the fractional part ensures that the result is always in the interval [0, 1].</span></span>  
  
|<span data-ttu-id="9ba68-126">Özgün</span><span class="sxs-lookup"><span data-stu-id="9ba68-126">Original</span></span>|<span data-ttu-id="9ba68-127">Genişletilmiş</span><span class="sxs-lookup"><span data-stu-id="9ba68-127">Scaled</span></span>|  
|--------------|------------|  
|<span data-ttu-id="9ba68-128">(0.4, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="9ba68-128">(0.4, 0.4, 0.4, 1)</span></span>|<span data-ttu-id="9ba68-129">(0.4, 0.4, 0.8, 1)</span><span class="sxs-lookup"><span data-stu-id="9ba68-129">(0.4, 0.4, 0.8, 1)</span></span>|  
|<span data-ttu-id="9ba68-130">(0.4, 0.2, 0.2, 1)</span><span class="sxs-lookup"><span data-stu-id="9ba68-130">(0.4, 0.2, 0.2, 1)</span></span>|<span data-ttu-id="9ba68-131">(0.4, 0.2, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="9ba68-131">(0.4, 0.2, 0.4, 1)</span></span>|  
|<span data-ttu-id="9ba68-132">(0.2, 0.4, 0.2, 1)</span><span class="sxs-lookup"><span data-stu-id="9ba68-132">(0.2, 0.4, 0.2, 1)</span></span>|<span data-ttu-id="9ba68-133">(0.2, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="9ba68-133">(0.2, 0.4, 0.4, 1)</span></span>|  
|<span data-ttu-id="9ba68-134">(0.4, 0.4, 0.8, 1)</span><span class="sxs-lookup"><span data-stu-id="9ba68-134">(0.4, 0.4, 0.8, 1)</span></span>|<span data-ttu-id="9ba68-135">(0.4, 0.4, 0.6, 1)</span><span class="sxs-lookup"><span data-stu-id="9ba68-135">(0.4, 0.4, 0.6, 1)</span></span>|  
  
## <a name="scaling-multiple-colors"></a><span data-ttu-id="9ba68-136">Birden çok renkleri ölçekleme</span><span class="sxs-lookup"><span data-stu-id="9ba68-136">Scaling Multiple Colors</span></span>  
 <span data-ttu-id="9ba68-137">Aşağıdaki örnek oluşturan bir <xref:System.Drawing.Image> ColorBars2.bmp dosyasından nesnesi.</span><span class="sxs-lookup"><span data-stu-id="9ba68-137">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars2.bmp.</span></span> <span data-ttu-id="9ba68-138">Ardından kod her piksel kırmızı, yeşil ve mavi bileşenlerinin görüntüde ölçeklendirir.</span><span class="sxs-lookup"><span data-stu-id="9ba68-138">Then the code scales the red, green, and blue components of each pixel in the image.</span></span> <span data-ttu-id="9ba68-139">Kırmızı bileşenleri yüzde 25'i ölçeklenir, yeşil bileşenleri yüzde 35 ' ölçeklenir ve mavi bileşenleri yüzde 50 ' ölçeklenir.</span><span class="sxs-lookup"><span data-stu-id="9ba68-139">The red components are scaled down 25 percent, the green components are scaled down 35 percent, and the blue components are scaled down 50 percent.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.RecoloringImages#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#42)]  
  
 <span data-ttu-id="9ba68-140">Aşağıdaki çizimde özgün resim soldaki ve ölçeklendirilmiş görüntü sağ tarafta gösterir.</span><span class="sxs-lookup"><span data-stu-id="9ba68-140">The following illustration shows the original image on the left and the scaled image on the right.</span></span>  
  
 <span data-ttu-id="9ba68-141">![Renkleri ölçeklendirmek](../../../../docs/framework/winforms/advanced/media/colortrans4.png "colortrans4")</span><span class="sxs-lookup"><span data-stu-id="9ba68-141">![Scale Colors](../../../../docs/framework/winforms/advanced/media/colortrans4.png "colortrans4")</span></span>  
  
 <span data-ttu-id="9ba68-142">Aşağıdaki tabloda, önce ve sonra kırmızı, yeşil ve mavi ölçeklendirme dört Çubuklar için renk vektörlerinin listeler.</span><span class="sxs-lookup"><span data-stu-id="9ba68-142">The following table lists the color vectors for the four bars before and after the red, green and blue scaling.</span></span>  
  
|<span data-ttu-id="9ba68-143">Özgün</span><span class="sxs-lookup"><span data-stu-id="9ba68-143">Original</span></span>|<span data-ttu-id="9ba68-144">Genişletilmiş</span><span class="sxs-lookup"><span data-stu-id="9ba68-144">Scaled</span></span>|  
|--------------|------------|  
|<span data-ttu-id="9ba68-145">(0.6, 0.6, 0.6, 1)</span><span class="sxs-lookup"><span data-stu-id="9ba68-145">(0.6, 0.6, 0.6, 1)</span></span>|<span data-ttu-id="9ba68-146">(0.45, 0.39, 0.3, 1)</span><span class="sxs-lookup"><span data-stu-id="9ba68-146">(0.45, 0.39, 0.3, 1)</span></span>|  
|<span data-ttu-id="9ba68-147">(0, 1, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="9ba68-147">(0, 1, 1, 1)</span></span>|<span data-ttu-id="9ba68-148">(0, 0.65, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="9ba68-148">(0, 0.65, 0.5, 1)</span></span>|  
|<span data-ttu-id="9ba68-149">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="9ba68-149">(1, 1, 0, 1)</span></span>|<span data-ttu-id="9ba68-150">(0.75, 0.65, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="9ba68-150">(0.75, 0.65, 0, 1)</span></span>|  
|<span data-ttu-id="9ba68-151">(1, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="9ba68-151">(1, 0, 1, 1)</span></span>|<span data-ttu-id="9ba68-152">(0.75, 0, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="9ba68-152">(0.75, 0, 0.5, 1)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9ba68-153">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9ba68-153">See Also</span></span>  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [<span data-ttu-id="9ba68-154">Grafikler ve Windows Forms'ta çizme</span><span class="sxs-lookup"><span data-stu-id="9ba68-154">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="9ba68-155">Görüntüleri yeniden renklendirme</span><span class="sxs-lookup"><span data-stu-id="9ba68-155">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)