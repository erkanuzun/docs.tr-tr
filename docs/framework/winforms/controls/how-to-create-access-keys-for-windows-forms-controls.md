---
title: "Nasıl yapılır: Windows Forms Denetimleri için Erişim Tuşları Oluşturma"
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
- cpp
helpviewer_keywords:
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- mnemonics
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4faa0991-28ec-4eca-91db-51dc2cd6a7ac
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: af4cbcc5dacc4f9a0b5312b67838479bf6817228
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-access-keys-for-windows-forms-controls"></a><span data-ttu-id="af05c-102">Nasıl yapılır: Windows Forms Denetimleri için Erişim Tuşları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="af05c-102">How to: Create Access Keys for Windows Forms Controls</span></span>
<span data-ttu-id="af05c-103">Bir *erişim tuşu* altı çizili bir karakter menü, menü öğesi ya da bir düğmesi gibi denetimin etiket metnini,'dir.</span><span class="sxs-lookup"><span data-stu-id="af05c-103">An *access key* is an underlined character in the text of a menu, menu item, or the label of a control such as a button.</span></span> <span data-ttu-id="af05c-104">Bir erişim anahtarı ile kullanıcı "bir düğme önceden tanımlanmış erişim anahtarı ile birlikte ALT tuşuna basarak tıklatabilirsiniz".</span><span class="sxs-lookup"><span data-stu-id="af05c-104">With an access key, the user can "click" a button by pressing the ALT key in combination with the predefined access key.</span></span> <span data-ttu-id="af05c-105">Örneğin, bir düğme bir form yazdırma için bir yordam çalıştırıyorsa ve bu nedenle, `Text` harf "P" "düğmesi metni çalışma zamanında çizilmesini P" harfi neden olmadan önce ve işareti ekleme özelliği "Yazdır," ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="af05c-105">For example, if a button runs a procedure to print a form, and therefore its `Text` property is set to "Print," adding an ampersand before the letter "P" causes the letter "P" to be underlined in the button text at run time.</span></span> <span data-ttu-id="af05c-106">Kullanıcı ilişkili düğme ALT + S tuşlarına basarak komutu çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af05c-106">The user can run the command associated with the button by pressing ALT+P.</span></span> <span data-ttu-id="af05c-107">Odağı alamayan bir denetim için erişim tuşu sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="af05c-107">You cannot have an access key for a control that cannot receive focus.</span></span>  
  
### <a name="to-create-an-access-key-for-a-control"></a><span data-ttu-id="af05c-108">Bir denetim için erişim anahtarı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="af05c-108">To create an access key for a control</span></span>  
  
1.  <span data-ttu-id="af05c-109">Ayarlama `Text` özelliği kısayol olur harf önce ve işareti içeren bir dize için (&).</span><span class="sxs-lookup"><span data-stu-id="af05c-109">Set the `Text` property to a string that includes an ampersand (&) before the letter that will be the shortcut.</span></span>  
  
    ```vb  
    ' Set the letter "P" as an access key.  
    Button1.Text = "&Print"  
    ```  
  
    ```csharp  
    // Set the letter "P" as an access key.  
    button1.Text = "&Print";  
    ```  
  
    ```cpp  
    // Set the letter "P" as an access key.  
    button1->Text = "&Print";  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="af05c-110">Erişim anahtarı oluşturmadan ve işareti bir başlık eklemek için iki ve işaretlerini dahil (& &).</span><span class="sxs-lookup"><span data-stu-id="af05c-110">To include an ampersand in a caption without creating an access key, include two ampersands (&&).</span></span> <span data-ttu-id="af05c-111">Tek bir ve işareti yazısının görüntülenir ve hiçbir karakter çizilir.</span><span class="sxs-lookup"><span data-stu-id="af05c-111">A single ampersand is displayed in the caption and no characters are underlined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af05c-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="af05c-112">See Also</span></span>  
 <xref:System.Windows.Forms.Button>  
 [<span data-ttu-id="af05c-113">Nasıl yapılır: Windows Forms düğme tıklamalarına yanıt verme</span><span class="sxs-lookup"><span data-stu-id="af05c-113">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="af05c-114">Nasıl yapılır: tarafından görüntülenen metni ayarlama bir Windows Forms denetimi</span><span class="sxs-lookup"><span data-stu-id="af05c-114">How to: Set the Text Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [<span data-ttu-id="af05c-115">Ayrı Windows Forms denetimlerini etiketleme ve kısayollarını sunma</span><span class="sxs-lookup"><span data-stu-id="af05c-115">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)