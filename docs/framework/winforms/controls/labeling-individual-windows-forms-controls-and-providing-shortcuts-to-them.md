---
title: "Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], access keys
- shortcuts [Windows Forms], controls
- keyboard shortcuts [Windows Forms], controls
- Windows Forms controls, labels
ms.assetid: 6eaf868c-819f-4131-8f59-048e20c286f7
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 32aa83e69d1159b2afa376a7155c40e2a36d7684
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them"></a><span data-ttu-id="b30f2-102">Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma</span><span class="sxs-lookup"><span data-stu-id="b30f2-102">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>
<span data-ttu-id="b30f2-103">Windows Forms'a eklenen denetimler özelliklere sahip ve kullanıcı daha fazla özelleştirmek için kullanılan yöntemleri karşılaşırsınız.</span><span class="sxs-lookup"><span data-stu-id="b30f2-103">Controls added to Windows Forms have properties and methods that are used to further specialize the user experience.</span></span> <span data-ttu-id="b30f2-104">Kullanıcı gereksinimlerine uyacak şekilde, kullanıcı arabirimi özelleştirme, iyi tasarlanmış Windows uygulamaları için son derece önemlidir.</span><span class="sxs-lookup"><span data-stu-id="b30f2-104">Customizing your user interface to suit the needs of the user is extremely important for well-designed Windows applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b30f2-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b30f2-105">In This Section</span></span>  
 [<span data-ttu-id="b30f2-106">Nasıl yapılır: tarafından görüntülenen metni ayarlama bir Windows Forms denetimi</span><span class="sxs-lookup"><span data-stu-id="b30f2-106">How to: Set the Text Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 <span data-ttu-id="b30f2-107">Bir metin etiketi denetime atama açıklar.</span><span class="sxs-lookup"><span data-stu-id="b30f2-107">Describes how to assign a text label to a control.</span></span>  
  
 [<span data-ttu-id="b30f2-108">Nasıl yapılır: tarafından görüntülenen resmi ayarlama bir Windows Forms denetimi</span><span class="sxs-lookup"><span data-stu-id="b30f2-108">How to: Set the Image Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md)  
 <span data-ttu-id="b30f2-109">Görüntüleri göstermek için bir denetiminin nasıl yapılandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="b30f2-109">Explains how to configure a control to display images.</span></span>  
  
 [<span data-ttu-id="b30f2-110">Nasıl yapılır: Windows Forms denetimleri için erişim tuşları oluşturma</span><span class="sxs-lookup"><span data-stu-id="b30f2-110">How to: Create Access Keys for Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)  
 <span data-ttu-id="b30f2-111">Önceden tanımlanmış klavye kısayolları oluşturma hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b30f2-111">Gives information about creating predefined keyboard shortcuts.</span></span>  
  
 [<span data-ttu-id="b30f2-112">Bir Windows formundaki denetimler için erişilebilirlik bilgileri sağlama</span><span class="sxs-lookup"><span data-stu-id="b30f2-112">Providing Accessibility Information for Controls on a Windows Form</span></span>](../../../../docs/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form.md)  
 <span data-ttu-id="b30f2-113">Erişilebilirlik yardımları ile çalışmak denetimleri etkinleştirme hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b30f2-113">Gives information about enabling your controls to work with accessibility aids.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b30f2-114">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="b30f2-114">Related Sections</span></span>  
 [<span data-ttu-id="b30f2-115">Windows Forms denetimleri</span><span class="sxs-lookup"><span data-stu-id="b30f2-115">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 <span data-ttu-id="b30f2-116">Diğer temel işlemleri için bağlantılar denetimleriyle yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b30f2-116">Links to other basic things you can do with controls.</span></span>  
  
 <span data-ttu-id="b30f2-117">Ayrıca bkz. [nasıl yapılır: oluşturmak erişim anahtarları için Windows Forms denetimleri kullanarak Tasarımcı](http://msdn.microsoft.com/library/ms233673\(v=vs.110\)), [nasıl yapılır: Tasarımcı kullanarak bir Windows Forms denetimi görüntülenen metin ayarlamak](http://msdn.microsoft.com/library/ms233665\(v=vs.110\)), [nasıl: resmi ayarlama Tarafından görüntülenen Tasarımcı kullanarak bir Windows Formları denetimi](http://msdn.microsoft.com/library/ms233656\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="b30f2-117">Also see [How to: Create Access Keys for Windows Forms Controls Using the Designer](http://msdn.microsoft.com/library/ms233673\(v=vs.110\)), [How to: Set the Text Displayed by a Windows Forms Control Using the Designer](http://msdn.microsoft.com/library/ms233665\(v=vs.110\)), [How to: Set the Image Displayed by a Windows Forms Control Using the Designer](http://msdn.microsoft.com/library/ms233656\(v=vs.110\)).</span></span>