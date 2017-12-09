---
title: "Birlikte çalışma etkinliğini bir .NET Framework 4 iş akışında kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9bb747f0-eb33-4f70-84cd-317382372dcd
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: aa8bb873ed42d5ba717359f420855b605cbe423d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="using-the-interop-activity-in-a-net-framework-4-workflow"></a><span data-ttu-id="c633e-102">Birlikte çalışma etkinliğini bir .NET Framework 4 iş akışında kullanma</span><span class="sxs-lookup"><span data-stu-id="c633e-102">Using the Interop Activity in a .NET Framework 4 Workflow</span></span>
<span data-ttu-id="c633e-103">Kullanılarak oluşturulan etkinlikleri [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] veya [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] kullanılabilir bir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] kullanarak iş akışı <xref:System.Activities.Statements.Interop> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="c633e-103">Activities created using [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] or [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] can be used in a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow by using the <xref:System.Activities.Statements.Interop> activity.</span></span> <span data-ttu-id="c633e-104">Bu konuda kullanarak genel bir bakış sağlar <xref:System.Activities.Statements.Interop> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="c633e-104">This topic provides an overview of using the <xref:System.Activities.Statements.Interop> activity.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c633e-105"><xref:System.Activities.Statements.Interop> Etkinliği iş akışı Proje olmadıkça iş akışı Tasarımcısı Araç Kutusu'nda görünmez kendi **hedef Framework** ayarını **.Net Framework 4** veya sonraki bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="c633e-105">The <xref:System.Activities.Statements.Interop> activity does not appear in the workflow designer toolbox unless the workflow's project has its **Target Framework** setting set to **.Net Framework 4** or later.</span></span>  
  
## <a name="using-the-interop-activity-in-net-framework-45-workflows"></a><span data-ttu-id="c633e-106">.NET Framework 4.5 akışlarında birlikte çalışma etkinliğini kullanma</span><span class="sxs-lookup"><span data-stu-id="c633e-106">Using the Interop Activity in .NET Framework 4.5 Workflows</span></span>  
 <span data-ttu-id="c633e-107">Bu konuda, bir [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] etkinlik kitaplığı oluşturulduğu içeren bir `DiscountCalculator` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="c633e-107">In this topic, a [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] activity library is created that contains a `DiscountCalculator` activity.</span></span> <span data-ttu-id="c633e-108">`DiscountCalculator` Satın alma miktarına bağlı bir indirim hesaplar ve oluşan bir <xref:System.Workflow.Activities.SequenceActivity> içeren bir <xref:System.Workflow.Activities.PolicyActivity>.</span><span class="sxs-lookup"><span data-stu-id="c633e-108">The `DiscountCalculator` calculates a discount based on a purchase amount and consists of a <xref:System.Workflow.Activities.SequenceActivity> that contains a <xref:System.Workflow.Activities.PolicyActivity>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c633e-109">[!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] Bu konuda oluşturulan etkinliği kullanan bir <xref:System.Workflow.Activities.PolicyActivity> etkinliğin mantığını uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="c633e-109">The [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] activity created in this topic uses a <xref:System.Workflow.Activities.PolicyActivity> to implement the logic of the activity.</span></span> <span data-ttu-id="c633e-110">Özel bir kullanmak için gerekli olmayan [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] etkinlik veya <xref:System.Activities.Statements.Interop> kullanmak için etkinlik kuralları içinde bir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] iş akışı.</span><span class="sxs-lookup"><span data-stu-id="c633e-110">It is not required to use a custom [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] activity or the <xref:System.Activities.Statements.Interop> activity in order to use rules in a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow.</span></span> <span data-ttu-id="c633e-111">Kuralları kullanma örneği için bir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] kullanmadan iş akışı <xref:System.Activities.Statements.Interop> etkinliği bkz [.NET Framework 4.5 ilke etkinlik](../../../docs/framework/windows-workflow-foundation/samples/policy-activity-in-net-framework-4-5.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="c633e-111">For an example of using rules in a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow without using the <xref:System.Activities.Statements.Interop> activity, see the [Policy Activity in .NET Framework 4.5](../../../docs/framework/windows-workflow-foundation/samples/policy-activity-in-net-framework-4-5.md) sample.</span></span>  
  
#### <a name="to-create-the-net-framework-35-activity-library-project"></a><span data-ttu-id="c633e-112">.NET Framework 3.5 etkinlik kitaplığı projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c633e-112">To create the .NET Framework 3.5 activity library project</span></span>  
  
1.  <span data-ttu-id="c633e-113">Açık [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] seçip **yeni** ve ardından **proje...**</span><span class="sxs-lookup"><span data-stu-id="c633e-113">Open [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] and select **New** and then **Project…**</span></span> <span data-ttu-id="c633e-114">gelen **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="c633e-114">from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="c633e-115">Genişletme **diğer proje türleri** düğümünde **yüklü şablonlar** bölmesinde ve select **Visual Studio çözümleri**.</span><span class="sxs-lookup"><span data-stu-id="c633e-115">Expand the **Other Project Types** node in the **Installed Templates** pane and select **Visual Studio Solutions**.</span></span>  
  
3.  <span data-ttu-id="c633e-116">Seçin **boş çözüm** gelen **Visual Studio çözümleri** listesi.</span><span class="sxs-lookup"><span data-stu-id="c633e-116">Select **Blank Solution** from the **Visual Studio Solutions** list.</span></span> <span data-ttu-id="c633e-117">Tür `PolicyInteropDemo` içinde **adı** kutusuna ve tıklatın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="c633e-117">Type `PolicyInteropDemo` in the **Name** box and click **OK**.</span></span>  
  
4.  <span data-ttu-id="c633e-118">Sağ **PolicyInteropDemo** içinde **Çözüm Gezgini** seçip **Ekle** ve ardından **yeni proje...** .</span><span class="sxs-lookup"><span data-stu-id="c633e-118">Right-click **PolicyInteropDemo** in **Solution Explorer** and select **Add** and then **New Project…**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="c633e-119">Varsa **Çözüm Gezgini** pencere görünür, select değil **Çözüm Gezgini** gelen **Görünüm** menüsü.</span><span class="sxs-lookup"><span data-stu-id="c633e-119">If the **Solution Explorer** window is not visible, select **Solution Explorer** from the **View** menu.</span></span>  
  
5.  <span data-ttu-id="c633e-120">İçinde **yüklü şablonlar** listesinde **Visual C#** ve ardından **iş akışı**.</span><span class="sxs-lookup"><span data-stu-id="c633e-120">In the **Installed Templates** list, select **Visual C#** and then **Workflow**.</span></span> <span data-ttu-id="c633e-121">Seçin **.NET Framework 3.5** .NET Framework sürüm aşağı açılan listesi ve ardından **iş akışı etkinlik kütüphanesini** gelen **şablonları** listesi.</span><span class="sxs-lookup"><span data-stu-id="c633e-121">Select **.NET Framework 3.5** from the .NET Framework version drop-down list, and then select **Workflow Activity Library** from the **Templates** list.</span></span>  
  
6.  <span data-ttu-id="c633e-122">Tür `PolicyActivityLibrary` içinde **adı** kutusuna ve tıklatın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="c633e-122">Type `PolicyActivityLibrary` in the **Name** box and click **OK**.</span></span>  
  
7.  <span data-ttu-id="c633e-123">Sağ **Activity1.cs** içinde **Çözüm Gezgini** seçip **silmek**.</span><span class="sxs-lookup"><span data-stu-id="c633e-123">Right-click **Activity1.cs** in **Solution Explorer** and select **Delete**.</span></span> <span data-ttu-id="c633e-124">Tıklatın **Tamam** onaylamak için.</span><span class="sxs-lookup"><span data-stu-id="c633e-124">Click **OK** to confirm.</span></span>  
  
#### <a name="to-create-the-discountcalculator-activity"></a><span data-ttu-id="c633e-125">DiscountCalculator etkinlik oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c633e-125">To create the DiscountCalculator activity</span></span>  
  
1.  <span data-ttu-id="c633e-126">Sağ **PolicyActivityLibrary** içinde **Çözüm Gezgini** seçip **Ekle** ve ardından **etkinlik...** .</span><span class="sxs-lookup"><span data-stu-id="c633e-126">Right-click **PolicyActivityLibrary** in **Solution Explorer** and select **Add** and then **Activity…**.</span></span>  
  
2.  <span data-ttu-id="c633e-127">Seçin **etkinlikle (kod ayrımı)** gelen **Visual C# öğeleri** listesi.</span><span class="sxs-lookup"><span data-stu-id="c633e-127">Select **Activity (with code separation)** from the **Visual C# Items** list.</span></span> <span data-ttu-id="c633e-128">Tür `DiscountCalculator` içinde **adı** kutusuna ve tıklatın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="c633e-128">Type `DiscountCalculator` in the **Name** box and click **OK**.</span></span>  
  
3.  <span data-ttu-id="c633e-129">Sağ **DiscountCalculator.xoml** içinde **Çözüm Gezgini** seçip **görünümü kodu**.</span><span class="sxs-lookup"><span data-stu-id="c633e-129">Right-click **DiscountCalculator.xoml** in **Solution Explorer** and select **View Code**.</span></span>  
  
4.  <span data-ttu-id="c633e-130">Aşağıdaki üç özellikleri ekleyin `DiscountCalculator` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c633e-130">Add the following three properties to the `DiscountCalculator` class.</span></span>  
  
    ```csharp  
    public partial class DiscountCalculator : SequenceActivity  
    {  
        public double Subtotal { get; set; }  
        public double DiscountPercent { get; set; }  
        public double Total { get; set; }  
    }  
    ```  
  
5.  <span data-ttu-id="c633e-131">Sağ **DiscountCalculator.xoml** içinde **Çözüm Gezgini** seçip **Görünüm Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="c633e-131">Right-click **DiscountCalculator.xoml** in **Solution Explorer** and select **View Designer**.</span></span>  
  
6.  <span data-ttu-id="c633e-132">Sürükleme bir **İlkesi** etkinliğinden **Windows iş akışı v3.0** bölümünü **araç** sürükleyip bırakın **DiscountCalculator** etkinliği .</span><span class="sxs-lookup"><span data-stu-id="c633e-132">Drag a **Policy** activity from the **Windows Workflow v3.0** section of the **Toolbox** and drop it in the **DiscountCalculator** activity.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="c633e-133">Varsa **araç** pencere görünür, select değil **araç** gelen **Görünüm** menüsü.</span><span class="sxs-lookup"><span data-stu-id="c633e-133">If the **Toolbox** window is not visible, select **Toolbox** from the **View** menu.</span></span>  
  
#### <a name="to-configure-the-rules"></a><span data-ttu-id="c633e-134">Kurallarını yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="c633e-134">To configure the rules</span></span>  
  
1.  <span data-ttu-id="c633e-135">Yeni eklenen tıklatın **İlkesi** henüz seçili değilse seçmek için etkinlik.</span><span class="sxs-lookup"><span data-stu-id="c633e-135">Click the newly added **Policy** activity to select it, if it is not already selected.</span></span>  
  
2.  <span data-ttu-id="c633e-136">Tıklatın **RuleSetReference** özelliğinde **özellikleri** penceresi seçin ve özellik sağındaki üç nokta düğmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="c633e-136">Click the **RuleSetReference** property in the **Properties** window to select it, and click the ellipsis button to the right of the property.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="c633e-137">Varsa **özellikleri** pencere görünür değil, seçin **Özellikler penceresini** gelen **Görünüm** menüsü.</span><span class="sxs-lookup"><span data-stu-id="c633e-137">If the **Properties** window is not visible, choose **Properties Window** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="c633e-138">Seçin **yeni tıklatın...** .</span><span class="sxs-lookup"><span data-stu-id="c633e-138">Select **Click New…**.</span></span>  
  
4.  <span data-ttu-id="c633e-139">Tıklatın **Kuralı Ekle**.</span><span class="sxs-lookup"><span data-stu-id="c633e-139">Click **Add Rule**.</span></span>  
  
5.  <span data-ttu-id="c633e-140">İçine aşağıdaki ifadeyi yazın **koşulu** kutusu.</span><span class="sxs-lookup"><span data-stu-id="c633e-140">Type the following expression into the **Condition** box.</span></span>  
  
    ```  
    this.Subtotal >= 50 && this.Subtotal < 100  
    ```  
  
6.  <span data-ttu-id="c633e-141">İçine aşağıdaki ifadeyi yazın **sonra Eylemler** kutusu.</span><span class="sxs-lookup"><span data-stu-id="c633e-141">Type the following expression into the **Then Actions** box.</span></span>  
  
    ```  
    this.DiscountPercent = 0.075  
    ```  
  
7.  <span data-ttu-id="c633e-142">Tıklatın **Kuralı Ekle**.</span><span class="sxs-lookup"><span data-stu-id="c633e-142">Click **Add Rule**.</span></span>  
  
8.  <span data-ttu-id="c633e-143">İçine aşağıdaki ifadeyi yazın **koşulu** kutusu.</span><span class="sxs-lookup"><span data-stu-id="c633e-143">Type the following expression into the **Condition** box.</span></span>  
  
    ```  
    this.Subtotal >= 100  
    ```  
  
9. <span data-ttu-id="c633e-144">İçine aşağıdaki ifadeyi yazın **sonra Eylemler** kutusu.</span><span class="sxs-lookup"><span data-stu-id="c633e-144">Type the following expression into the **Then Actions** box.</span></span>  
  
    ```  
    this.DiscountPercent = 0.15  
    ```  
  
10. <span data-ttu-id="c633e-145">Tıklatın **Kuralı Ekle**.</span><span class="sxs-lookup"><span data-stu-id="c633e-145">Click **Add Rule**.</span></span>  
  
11. <span data-ttu-id="c633e-146">İçine aşağıdaki ifadeyi yazın **koşulu** kutusu.</span><span class="sxs-lookup"><span data-stu-id="c633e-146">Type the following expression into the **Condition** box.</span></span>  
  
    ```  
    this.DiscountPercent > 0  
    ```  
  
12. <span data-ttu-id="c633e-147">İçine aşağıdaki ifadeyi yazın **sonra Eylemler** kutusu.</span><span class="sxs-lookup"><span data-stu-id="c633e-147">Type the following expression into the **Then Actions** box.</span></span>  
  
    ```  
    this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent  
    ```  
  
13. <span data-ttu-id="c633e-148">İçine aşağıdaki ifadeyi yazın **başka eylemler** kutusu.</span><span class="sxs-lookup"><span data-stu-id="c633e-148">Type the following expression into the **Else Actions** box.</span></span>  
  
    ```  
    this.Total = this.Subtotal  
    ```  
  
14. <span data-ttu-id="c633e-149">Tıklatın **Tamam** kapatmak için **kural kümesi düzenleyici** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="c633e-149">Click **OK** to close the **Rule Set Editor** dialog box.</span></span>  
  
15. <span data-ttu-id="c633e-150">Yeni oluşturulan emin <xref:System.Workflow.Activities.Rules.RuleSet> seçildiyse **adı** liste öğesini tıklatıp **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="c633e-150">Ensure that the newly-created <xref:System.Workflow.Activities.Rules.RuleSet> is selected in the **Name** list, and click **OK**.</span></span>  
  
16. <span data-ttu-id="c633e-151">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c633e-151">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
 <span data-ttu-id="c633e-152">Eklenen Kurallar `DiscountCalculator` etkinlik bu yordamda, aşağıdaki kod örneğinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="c633e-152">The rules added to the `DiscountCalculator` activity in this procedure are shown in the following code example.</span></span>  
  
```  
Rule1: IF this.Subtotal >= 50 && this.Subtotal < 100   
       THEN this.DiscountPercent = 0.075   
  
Rule2: IF this. Subtotal >= 100   
       THEN this.DiscountPercent = 0.15   
  
Rule3: IF this.DiscountPercent > 0   
       THEN this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent   
       ELSE this.Total = this.Subtotal  
```  
  
 <span data-ttu-id="c633e-153">Zaman <xref:System.Workflow.Activities.PolicyActivity> yürütür, bu üç kuralları değerlendirin ve değiştirme `Subtotal`, `DiscountPercent`, ve `Total` özellik değerlerini `DiscountCalculator` istenen indirim hesaplamak için etkinlik.</span><span class="sxs-lookup"><span data-stu-id="c633e-153">When the <xref:System.Workflow.Activities.PolicyActivity> executes, these three rules evaluate and modify the `Subtotal`, `DiscountPercent`, and `Total` property values of the `DiscountCalculator` activity to calculate the desired discount.</span></span>  
  
## <a name="using-the-discountcalculator-activity-with-the-interop-activity"></a><span data-ttu-id="c633e-154">İle birlikte çalışma etkinliğini DiscountCalculator etkinliğini kullanma</span><span class="sxs-lookup"><span data-stu-id="c633e-154">Using the DiscountCalculator Activity with the Interop Activity</span></span>  
 <span data-ttu-id="c633e-155">Kullanılacak `DiscountCalculator` etkinliği içinde bir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] iş akışı, <xref:System.Activities.Statements.Interop> etkinliği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c633e-155">To use the `DiscountCalculator` activity inside a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow, the <xref:System.Activities.Statements.Interop> activity is used.</span></span> <span data-ttu-id="c633e-156">Bu bölümdeki iki iş akışları oluşturulur ve bir kod ve bir iş akışı Tasarımcısı'nı kullanarak kullanarak hangi Göster nasıl kullanılacağını <xref:System.Activities.Statements.Interop> etkinlikle `DiscountCalculator` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="c633e-156">In this section two workflows are created, one using code and one using the workflow designer, which show how to use the <xref:System.Activities.Statements.Interop> activity with the `DiscountCalculator` activity.</span></span> <span data-ttu-id="c633e-157">Aynı ana bilgisayar uygulamasını hem de iş akışları için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c633e-157">The same host application is used for both workflows.</span></span>  
  
#### <a name="to-create-the-host-application"></a><span data-ttu-id="c633e-158">Ana bilgisayar uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c633e-158">To create the host application</span></span>  
  
1.  <span data-ttu-id="c633e-159">Sağ **PolicyInteropDemo** içinde **Çözüm Gezgini** seçip **Ekle**ve ardından **yeni proje...** .</span><span class="sxs-lookup"><span data-stu-id="c633e-159">Right-click **PolicyInteropDemo** in **Solution Explorer** and select **Add**, and then **New Project…**.</span></span>  
  
2.  <span data-ttu-id="c633e-160">Emin **.NET Framework 4.5** .NET Framework sürüm aşağı açılan listesinde seçilen ve seçin **iş akışı konsol uygulaması** gelen **Visual C# öğeleri** listesi.</span><span class="sxs-lookup"><span data-stu-id="c633e-160">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list, and select  **Workflow Console Application** from the **Visual C# Items** list.</span></span>  
  
3.  <span data-ttu-id="c633e-161">Tür `PolicyInteropHost` içine **adı** kutusuna ve tıklatın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="c633e-161">Type `PolicyInteropHost` into the **Name** box and click **OK**.</span></span>  
  
4.  <span data-ttu-id="c633e-162">Sağ **PolicyInteropHost** içinde **Çözüm Gezgini** seçip **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="c633e-162">Right-click **PolicyInteropHost** in **Solution Explorer** and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="c633e-163">İçinde **hedef framework** aşağı açılan listesinde, seçimden değiştirme **.NET Framework 4 istemci profili** için **.NET Framework 4.5**.</span><span class="sxs-lookup"><span data-stu-id="c633e-163">In the **Target framework** drop-down list, change the selection from **.NET Framework 4 Client Profile** to **.NET Framework 4.5**.</span></span> <span data-ttu-id="c633e-164">Tıklatın **Evet** onaylamak için.</span><span class="sxs-lookup"><span data-stu-id="c633e-164">Click **Yes** to confirm.</span></span>  
  
6.  <span data-ttu-id="c633e-165">Sağ **PolicyInteropHost** içinde **Çözüm Gezgini** seçip **Başvuru Ekle...** .</span><span class="sxs-lookup"><span data-stu-id="c633e-165">Right-click **PolicyInteropHost** in **Solution Explorer** and select **Add Reference…**.</span></span>  
  
7.  <span data-ttu-id="c633e-166">Seçin **PolicyActivityLibrary** gelen **projeleri** sekmesinde **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="c633e-166">Select **PolicyActivityLibrary** from the **Projects** tab and click **OK**.</span></span>  
  
8.  <span data-ttu-id="c633e-167">Sağ **PolicyInteropHost** içinde **Çözüm Gezgini** seçip **Başvuru Ekle...** .</span><span class="sxs-lookup"><span data-stu-id="c633e-167">Right-click **PolicyInteropHost** in **Solution Explorer** and select **Add Reference…**.</span></span>  
  
9. <span data-ttu-id="c633e-168">Seçin **System.Workflow.Activities**, **System.Workflow.ComponentModel**ve ardından **System.Workflow.Runtime** gelen **.NET**sekmesinde **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="c633e-168">Select **System.Workflow.Activities**, **System.Workflow.ComponentModel**, and then **System.Workflow.Runtime** from the **.NET** tab and click **OK**.</span></span>  
  
10. <span data-ttu-id="c633e-169">Sağ **PolicyInteropHost** içinde **Çözüm Gezgini** seçip **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="c633e-169">Right-click **PolicyInteropHost** in **Solution Explorer** and select **Set as StartUp Project**.</span></span>  
  
11. <span data-ttu-id="c633e-170">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c633e-170">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
### <a name="using-the-interop-activity-in-code"></a><span data-ttu-id="c633e-171">Birlikte çalışma etkinlik kod içinde kullanma</span><span class="sxs-lookup"><span data-stu-id="c633e-171">Using the Interop Activity in Code</span></span>  
 <span data-ttu-id="c633e-172">Bu örnekte, bir iş akışı tanımını içeren kodu kullanılarak oluşturulan <xref:System.Activities.Statements.Interop> etkinlik ve `DiscountCalculator` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="c633e-172">In this example, a workflow definition is created using code that contains the <xref:System.Activities.Statements.Interop> activity and the `DiscountCalculator` activity.</span></span> <span data-ttu-id="c633e-173">Bu iş akışını kullanarak çağrılan <xref:System.Activities.WorkflowInvoker> ve kural değerlendirme sonuçlarını konsolunu kullanarak yazılır bir <xref:System.Activities.Statements.WriteLine> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="c633e-173">This workflow is invoked using <xref:System.Activities.WorkflowInvoker> and the results of the rule evaluation are written to the console using a <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
##### <a name="to-use-the-interop-activity-in-code"></a><span data-ttu-id="c633e-174">Birlikte çalışma etkinlik kodda kullanmak için</span><span class="sxs-lookup"><span data-stu-id="c633e-174">To use the Interop activity in code</span></span>  
  
1.  <span data-ttu-id="c633e-175">Sağ **Program.cs** içinde **Çözüm Gezgini** seçip **görünümü kodu**.</span><span class="sxs-lookup"><span data-stu-id="c633e-175">Right-click **Program.cs** in **Solution Explorer** and select **View Code**.</span></span>  
  
2.  <span data-ttu-id="c633e-176">Aşağıdakileri ekleyin `using` deyimini dosyanın üst.</span><span class="sxs-lookup"><span data-stu-id="c633e-176">Add the following `using` statement at the top of the file.</span></span>  
  
    ```csharp  
    using PolicyActivityLibrary;  
    ```  
  
3.  <span data-ttu-id="c633e-177">İçeriği Kaldır `Main` yöntemi ve aşağıdaki kod ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c633e-177">Remove the contents of the `Main` method and replace with the following code.</span></span>  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        CalculateDiscountUsingCodeWorkflow();  
    }  
    ```  
  
4.  <span data-ttu-id="c633e-178">İçinde yeni bir yöntem oluşturma `Program` adlı bir sınıf `CalculateDiscountUsingCodeWorkflow` aşağıdaki kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="c633e-178">Create a new method in the `Program` class called `CalculateDiscountUsingCodeWorkflow` that contains the following code.</span></span>  
  
    ```csharp  
    static void CalculateDiscountUsingCodeWorkflow()  
    {  
        Variable<double> Subtotal = new Variable<double>  
        {  
            Default = 75.99,  
            Name = "Subtotal"  
        };  
  
        Variable<double> DiscountPercent = new Variable<double>  
        {  
            Name = "DiscountPercent"  
        };  
  
        Variable<double> Total = new Variable<double>  
        {  
            Name = "Total"  
        };  
  
        Activity wf = new Sequence  
        {  
            Variables = { Subtotal, DiscountPercent, Total },  
            Activities =   
            {  
                new Interop  
                {  
                    ActivityType = typeof(DiscountCalculator),  
                    ActivityProperties =   
                    {  
                        { "Subtotal", new InArgument<double>(Subtotal) },  
                        { "DiscountPercentOut", new OutArgument<double>(DiscountPercent) },  
                        { "TotalOut", new OutArgument<double>(Total) }  
                    }  
                },  
                new WriteLine  
                {  
                    Text =  new InArgument<string>(env =>   
                        string.Format("Subtotal: {0:C}, Discount {1}%, Total {2:C}",   
                        Subtotal.Get(env), DiscountPercent.Get(env) * 100, Total.Get(env)))  
                }  
            }  
        };  
  
        WorkflowInvoker.Invoke(wf);  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="c633e-179">`Subtotal`, `DiscountPercent`, Ve `Total` özelliklerini `DiscountCalculator` etkinlik bağımsız ortaya <xref:System.Activities.Statements.Interop> etkinliği ve yerel ilişkili iş akışı değişken <xref:System.Activities.Statements.Interop> etkinliğin <xref:System.Activities.Statements.Interop.ActivityProperties%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="c633e-179">The `Subtotal`, `DiscountPercent`, and `Total` properties of the `DiscountCalculator` activity are surfaced as arguments of the <xref:System.Activities.Statements.Interop> activity, and bound to local workflow variables in the <xref:System.Activities.Statements.Interop> activity’s <xref:System.Activities.Statements.Interop.ActivityProperties%2A> collection.</span></span> <span data-ttu-id="c633e-180">`Subtotal`eklenen bir <xref:System.Activities.ArgumentDirection.In> bağımsız değişkeni çünkü `Subtotal` veri akışları içine <xref:System.Activities.Statements.Interop> etkinlik, ve `DiscountPercent` ve `Total` olarak eklenir <xref:System.Activities.ArgumentDirection.Out> bağımsız değişkenler dışı kendi veri akışları için <xref:System.Activities.Statements.Interop> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="c633e-180">`Subtotal` is added as an <xref:System.Activities.ArgumentDirection.In> argument because the `Subtotal` data flows into the <xref:System.Activities.Statements.Interop> activity, and `DiscountPercent` and `Total` are added as <xref:System.Activities.ArgumentDirection.Out> arguments because their data flows out of the <xref:System.Activities.Statements.Interop> activity.</span></span> <span data-ttu-id="c633e-181">Unutmayın iki <xref:System.Activities.ArgumentDirection.Out> bağımsız değişken adlarıyla eklenen `DiscountPercentOut` ve `TotalOut` temsil ettikleri belirtmek için <xref:System.Activities.ArgumentDirection.Out> bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="c633e-181">Note that the two <xref:System.Activities.ArgumentDirection.Out> arguments are added with the names `DiscountPercentOut` and `TotalOut` to indicate that they represent <xref:System.Activities.ArgumentDirection.Out> arguments.</span></span> <span data-ttu-id="c633e-182">`DiscountCalculator` Türü olarak belirtildiğinde <xref:System.Activities.Statements.Interop> etkinliğin <xref:System.Activities.Statements.Interop.ActivityType%2A>.</span><span class="sxs-lookup"><span data-stu-id="c633e-182">The `DiscountCalculator` type is specified as the <xref:System.Activities.Statements.Interop> activity’s <xref:System.Activities.Statements.Interop.ActivityType%2A>.</span></span>  
  
5.  <span data-ttu-id="c633e-183">Derleme ve uygulamayı çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c633e-183">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="c633e-184">Yedek için farklı değerler `Subtotal` tarafından sağlanan farklı indirim düzeyleri çıkışı test etmek için değer `DiscountCalculator` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="c633e-184">Substitute different values for the `Subtotal` value to test out the different discount levels provided by the `DiscountCalculator` activity.</span></span>  
  
    ```csharp  
    Variable<double> Subtotal = new Variable<double>  
    {  
        Default = 75.99, // Change this value.  
        Name = "Subtotal"  
    };  
    ```  
  
### <a name="using-the-interop-activity-in-the-workflow-designer"></a><span data-ttu-id="c633e-185">Birlikte çalışma etkinliğini iş akışı Tasarımcısı'nda kullanma</span><span class="sxs-lookup"><span data-stu-id="c633e-185">Using the Interop Activity in the Workflow Designer</span></span>  
 <span data-ttu-id="c633e-186">Bu örnekte, bir iş akışı, iş akışı Tasarımcısı'nı kullanarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c633e-186">In this example, a workflow is created using the workflow designer.</span></span> <span data-ttu-id="c633e-187">Bu iş akışı önceki örnekte, aynı işlevselliği dışında daha kullanmak yerine sahip bir <xref:System.Activities.Statements.WriteLine> indirim görüntülenecek etkinlik konak uygulama alır ve iş akışı tamamlandığında indirim bilgilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c633e-187">This workflow has the same functionality as the previous example, except than instead of using a <xref:System.Activities.Statements.WriteLine> activity to display the discount, the host application retrieves and displays the discount information when the workflow completes.</span></span> <span data-ttu-id="c633e-188">Ayrıca, yerine yerel iş akışı değişkenleri verileri içerecek şekilde, bağımsız değişkenler iş akışı Tasarımcısı'nda oluşturulur ve iş akışı çağrıldığında değerler, ana bilgisayardan geçirilir.</span><span class="sxs-lookup"><span data-stu-id="c633e-188">Also, instead of using local workflow variables to contain the data, arguments are created in the workflow designer and the values are passed in from the host when the workflow is invoked.</span></span>  
  
##### <a name="to-host-the-policyactivity-using-a-workflow-designer-created-workflow"></a><span data-ttu-id="c633e-189">İş Akışı Tasarımcısı tarafından oluşturulan bir iş akışını kullanarak PolicyActivity barındırmak için</span><span class="sxs-lookup"><span data-stu-id="c633e-189">To host the PolicyActivity using a Workflow Designer-created workflow</span></span>  
  
1.  <span data-ttu-id="c633e-190">Sağ **Workflow1.xaml** içinde **Çözüm Gezgini** seçip **silmek**.</span><span class="sxs-lookup"><span data-stu-id="c633e-190">Right-click **Workflow1.xaml** in **Solution Explorer** and select **Delete**.</span></span> <span data-ttu-id="c633e-191">Tıklatın **Tamam** onaylamak için.</span><span class="sxs-lookup"><span data-stu-id="c633e-191">Click **OK** to confirm.</span></span>  
  
2.  <span data-ttu-id="c633e-192">Sağ **PolicyInteropHost** içinde **Çözüm Gezgini** seçip **Ekle**, **yeni öğe...** .</span><span class="sxs-lookup"><span data-stu-id="c633e-192">Right-click **PolicyInteropHost** in **Solution Explorer** and select **Add**, **New Item…**.</span></span>  
  
3.  <span data-ttu-id="c633e-193">Genişletme **Visual C# öğeleri** düğümü ve select **iş akışı**.</span><span class="sxs-lookup"><span data-stu-id="c633e-193">Expand the **Visual C# Items** node and select **Workflow**.</span></span> <span data-ttu-id="c633e-194">Seçin **etkinlik** gelen **Visual C# öğeleri** listesi.</span><span class="sxs-lookup"><span data-stu-id="c633e-194">Select **Activity** from the **Visual C# Items** list.</span></span>  
  
4.  <span data-ttu-id="c633e-195">Tür `DiscountWorkflow` içine **adı** kutusuna ve tıklatın **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="c633e-195">Type `DiscountWorkflow` into the **Name** box and click **Add**.</span></span>  
  
5.  <span data-ttu-id="c633e-196">Tıklatın **bağımsız değişkenleri** görüntülemek için iş akışı Tasarımcısı sol alt köşesine düğmesinde **bağımsız değişkenleri** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="c633e-196">Click the **Arguments** button on the lower left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
6.  <span data-ttu-id="c633e-197">Tıklatın **bağımsız değişkeni oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="c633e-197">Click **Create Argument**.</span></span>  
  
7.  <span data-ttu-id="c633e-198">Tür `Subtotal` içine **adı** kutusunda **içinde** gelen **yönü** açılan listesinde, select **çift** gelen**Bağımsız değişken türü** aşağı açılır ve bağımsız değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c633e-198">Type `Subtotal` into the **Name** box, select **In** from the **Direction** drop-down, select **Double** from the **Argument type** drop-down, and then press ENTER to save the argument.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c633e-199">Varsa **çift** bulunmayan **bağımsız değişken türü** aşağı açılan listesinden, **türleri için Gözat...** , türü `System.Double` içinde **türü adı** ve'ı tıklatın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="c633e-199">If **Double** is not in the **Argument type** drop-down list, select **Browse for Types …**, type `System.Double` in the **Type Name** box, and click **OK**.</span></span>  
  
8.  <span data-ttu-id="c633e-200">Tıklatın **bağımsız değişkeni oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="c633e-200">Click **Create Argument**.</span></span>  
  
9. <span data-ttu-id="c633e-201">Tür `DiscountPercent` içine **adı** kutusunda **çıkışı** gelen **yönü** açılan listesinde, select **çift** gelen**Bağımsız değişken türü** aşağı açılır ve bağımsız değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c633e-201">Type `DiscountPercent` into the **Name** box, select **Out** from the **Direction** drop-down, select **Double** from the **Argument type** drop-down, and then press ENTER to save the argument.</span></span>  
  
10. <span data-ttu-id="c633e-202">Tıklatın **bağımsız değişkeni oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="c633e-202">Click **Create Argument**.</span></span>  
  
11. <span data-ttu-id="c633e-203">Tür `Total` içine **adı** kutusunda **çıkışı** gelen **yönü** açılan listesinde, select **çift** gelen**Bağımsız değişken türü** aşağı açılır ve bağımsız değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c633e-203">Type `Total` into the **Name** box, select **Out** from the **Direction** drop-down, select **Double** from the **Argument type** drop-down, and then press ENTER to save the argument.</span></span>  
  
12. <span data-ttu-id="c633e-204">Tıklatın **bağımsız değişkenleri** kapatmak için iş akışı Tasarımcısı sol alt köşesine düğmesinde **bağımsız değişkenleri** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="c633e-204">Click the **Arguments** button on the lower left side of the workflow designer to close the **Arguments** pane.</span></span>  
  
13. <span data-ttu-id="c633e-205">Sürükleme bir **dizisi** etkinliğinden **akış denetimi** bölümünü **araç** ve iş akışı Tasarımcı yüzeyine bırakın.</span><span class="sxs-lookup"><span data-stu-id="c633e-205">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the workflow designer surface.</span></span>  
  
14. <span data-ttu-id="c633e-206">Sürükleme bir **birlikte çalışabilirliği** etkinliğinden **geçiş** bölümünü **araç** sürükleyip bırakın **dizisi** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="c633e-206">Drag an **Interop** activity from the **Migration** section of the **Toolbox** and drop it in the **Sequence** activity.</span></span>  
  
15. <span data-ttu-id="c633e-207">Tıklatın **birlikte çalışabilirliği** faaliyete **göz atmak için tıklatın...**</span><span class="sxs-lookup"><span data-stu-id="c633e-207">Click the **Interop** activity on the **Click to browse…**</span></span> <span data-ttu-id="c633e-208">Etiket, yazın **DiscountCalculator** içinde **türü adı** ve'ı tıklatın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="c633e-208">label, type **DiscountCalculator** in the **Type Name** box, and click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c633e-209">Zaman <xref:System.Activities.Statements.Interop> etkinlik, iş akışına eklenir ve `DiscountCalculator` türü olarak belirtildiğinde kendi <xref:System.Activities.Statements.Interop.ActivityType%2A>, <xref:System.Activities.Statements.Interop> etkinlik üç gösterir <xref:System.Activities.ArgumentDirection.In> bağımsız değişkenleri ve üç <xref:System.Activities.ArgumentDirection.Out> üç genel temsil eden bağımsız değişkenler özelliklerini `DiscountCalculator` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="c633e-209">When the <xref:System.Activities.Statements.Interop> activity is added to the workflow and the `DiscountCalculator` type is specified as its <xref:System.Activities.Statements.Interop.ActivityType%2A>, the <xref:System.Activities.Statements.Interop> activity exposes three <xref:System.Activities.ArgumentDirection.In> arguments and three <xref:System.Activities.ArgumentDirection.Out> arguments that represent the three public properties of the `DiscountCalculator` activity.</span></span> <span data-ttu-id="c633e-210"><xref:System.Activities.ArgumentDirection.In> Bağımsız değişkenleri üç genel özellikleri ve üç aynı ada sahip <xref:System.Activities.ArgumentDirection.Out> bağımsız değişkenleri ile aynı ada sahip **çıkışı** özellik adı eklenir.</span><span class="sxs-lookup"><span data-stu-id="c633e-210">The <xref:System.Activities.ArgumentDirection.In> arguments have the same name as the three public properties, and the three <xref:System.Activities.ArgumentDirection.Out> arguments have the same names with **Out** appended to the property name.</span></span> <span data-ttu-id="c633e-211">Aşağıdaki adımlarda, önceki adımlarda oluşturduğunuz iş akışı değişkenleri bağlı <xref:System.Activities.Statements.Interop> etkinliğin bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="c633e-211">In the following steps, the workflow arguments created in the previous steps are bound to the <xref:System.Activities.Statements.Interop> activity’s arguments.</span></span>  
  
16. <span data-ttu-id="c633e-212">Tür `DiscountPercent` içine **bir VB ifadesi girin** kutusunun sağındaki **DiscountPercentOut** özelliği ve SEKME tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c633e-212">Type `DiscountPercent` into the **Enter a VB expression** box to the right of the **DiscountPercentOut** property and press TAB.</span></span>  
  
17. <span data-ttu-id="c633e-213">Tür `Subtotal` içine **bir VB ifadesi girin** kutusunun sağındaki **alt toplam** özelliği ve SEKME tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c633e-213">Type `Subtotal` into the **Enter a VB expression** box to the right of the **Subtotal** property and press TAB.</span></span>  
  
18. <span data-ttu-id="c633e-214">Tür `Total` içine **bir VB ifadesi girin** kutusunun sağındaki **TotalOut** özelliği ve SEKME tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c633e-214">Type `Total` into the **Enter a VB expression** box to the right of the **TotalOut** property and press TAB.</span></span>  
  
19. <span data-ttu-id="c633e-215">Sağ **Program.cs** içinde **Çözüm Gezgini** seçip **görünümü kodu**.</span><span class="sxs-lookup"><span data-stu-id="c633e-215">Right-click **Program.cs** in **Solution Explorer** and select **View Code**.</span></span>  
  
20. <span data-ttu-id="c633e-216">Aşağıdakileri ekleyin `using` deyimini dosyanın üst.</span><span class="sxs-lookup"><span data-stu-id="c633e-216">Add the following `using` statement at the top of the file.</span></span>  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
21. <span data-ttu-id="c633e-217">Açıklama çağrısı çıkışı `CalculateDiscountInCode` yönteminde `Main` yöntemi ve aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c633e-217">Comment out the call to the `CalculateDiscountInCode` method in the `Main` method and add the following code.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c633e-218">Önceki yordamda ve varsayılan takip ettiğiniz değil, `Main` kodu varsa, Değiştir `Main` aşağıdaki kod ile.</span><span class="sxs-lookup"><span data-stu-id="c633e-218">If you did not follow the previous procedure and the default `Main` code is present, replace the contents of `Main` with the following code.</span></span>  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        CalculateDiscountUsingDesignerWorkflow();  
        //CalculateDiscountUsingCodeWorkflow();  
    }  
    ```  
  
22. <span data-ttu-id="c633e-219">İçinde yeni bir yöntem oluşturma `Program` adlı bir sınıf `CalculateDiscountUsingDesignerWorkflow` aşağıdaki kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="c633e-219">Create a new method in the `Program` class called `CalculateDiscountUsingDesignerWorkflow` that contains the following code.</span></span>  
  
    ```csharp  
    static void CalculateDiscountUsingDesignerWorkflow()  
    {  
        double SubtotalValue = 125.99;  
        Dictionary<string, object> wfargs = new Dictionary<string, object>  
        {  
            {"Subtotal", SubtotalValue}  
        };  
  
        Activity wf = new DiscountWorkflow();  
  
        IDictionary<string, object> outputs =  
            WorkflowInvoker.Invoke(wf, wfargs);  
  
        Console.WriteLine("Subtotal: {0:C}, Discount {1}%, Total {2:C}",  
            SubtotalValue, (double)outputs["DiscountPercent"] * 100,  
            outputs["Total"]);  
    }  
    ```  
  
23. <span data-ttu-id="c633e-220">Derleme ve uygulamayı çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c633e-220">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="c633e-221">Farklı bir belirtmek için `Subtotal` tutar, değerini değiştirme `SubtotalValue` aşağıdaki kodda.</span><span class="sxs-lookup"><span data-stu-id="c633e-221">To specify a different `Subtotal` amount, change the value of `SubtotalValue` in the following code.</span></span>  
  
    ```csharp  
    double SubtotalValue = 125.99; // Change this value.  
    ```  
  
## <a name="rules-features-overview"></a><span data-ttu-id="c633e-222">Kuralları özelliklere genel bakış</span><span class="sxs-lookup"><span data-stu-id="c633e-222">Rules Features Overview</span></span>  
 <span data-ttu-id="c633e-223">[!INCLUDE[wf1](../../../includes/wf1-md.md)] Kurallar altyapısı öncelik tabanlı bir şekilde İleri zincirleme desteğiyle kuralları işlemek için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="c633e-223">The [!INCLUDE[wf1](../../../includes/wf1-md.md)] rules engine provides support for processing rules in a priority-based manner with support for forward chaining.</span></span> <span data-ttu-id="c633e-224">Kurallar, bir koleksiyondaki öğelerin veya tek bir öğe için değerlendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c633e-224">Rules can be evaluated for a single item or for items in a collection.</span></span> <span data-ttu-id="c633e-225">Kurallar ve belirli kurallar işlevselliği hakkında bilgi genel bakış için lütfen aşağıdaki tabloya bakın.</span><span class="sxs-lookup"><span data-stu-id="c633e-225">For an overview of rules and information on specific rules functionality, please refer to the following table.</span></span>  
  
|<span data-ttu-id="c633e-226">Kuralları özelliği</span><span class="sxs-lookup"><span data-stu-id="c633e-226">Rules Feature</span></span>|<span data-ttu-id="c633e-227">Belgeler</span><span class="sxs-lookup"><span data-stu-id="c633e-227">Documentation</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="c633e-228">Kurallarına genel bakış</span><span class="sxs-lookup"><span data-stu-id="c633e-228">Rules Overview</span></span>|[<span data-ttu-id="c633e-229">Windows Workflow Foundation kurallar altyapısı giriş</span><span class="sxs-lookup"><span data-stu-id="c633e-229">Introduction to the Windows Workflow Foundation Rules Engine</span></span>](http://go.microsoft.com/fwlink/?LinkID=152836)|  
|<span data-ttu-id="c633e-230">RuleSet</span><span class="sxs-lookup"><span data-stu-id="c633e-230">RuleSet</span></span>|<span data-ttu-id="c633e-231">[İş akışlarında RuleSets kullanarak](http://go.microsoft.com/fwlink/?LinkId=178516) ve<xref:System.Workflow.Activities.Rules.RuleSet></span><span class="sxs-lookup"><span data-stu-id="c633e-231">[Using RuleSets in Workflows](http://go.microsoft.com/fwlink/?LinkId=178516) and <xref:System.Workflow.Activities.Rules.RuleSet></span></span>|  
|<span data-ttu-id="c633e-232">Kuralları değerlendirmesi</span><span class="sxs-lookup"><span data-stu-id="c633e-232">Evaluation of Rules</span></span>|[<span data-ttu-id="c633e-233">RuleSets kuralları değerlendirmesine</span><span class="sxs-lookup"><span data-stu-id="c633e-233">Rules Evaluation in RuleSets</span></span>](http://go.microsoft.com/fwlink/?LinkId=178517)|  
|<span data-ttu-id="c633e-234">Zincirleme kuralları</span><span class="sxs-lookup"><span data-stu-id="c633e-234">Rules Chaining</span></span>|<span data-ttu-id="c633e-235">[İleri denetim zincirleme](http://go.microsoft.com/fwlink/?LinkId=178518) ve [İleri kuralları zincirleme](http://go.microsoft.com/fwlink/?LinkId=178519)</span><span class="sxs-lookup"><span data-stu-id="c633e-235">[Forward Chaining Control](http://go.microsoft.com/fwlink/?LinkId=178518) and [Forward Chaining of Rules](http://go.microsoft.com/fwlink/?LinkId=178519)</span></span>|  
|<span data-ttu-id="c633e-236">Kural koleksiyonlarında işleme</span><span class="sxs-lookup"><span data-stu-id="c633e-236">Processing Collections in Rules</span></span>|[<span data-ttu-id="c633e-237">Kural koleksiyonlarında işleme</span><span class="sxs-lookup"><span data-stu-id="c633e-237">Processing Collections in Rules</span></span>](http://go.microsoft.com/fwlink/?LinkId=178520)|  
|<span data-ttu-id="c633e-238">PolicyActivity kullanma</span><span class="sxs-lookup"><span data-stu-id="c633e-238">Using the PolicyActivity</span></span>|<span data-ttu-id="c633e-239">[Kullanarak PolicyActivity etkinliğini](http://go.microsoft.com/fwlink/?LinkId=178521) ve<xref:System.Workflow.Activities.PolicyActivity></span><span class="sxs-lookup"><span data-stu-id="c633e-239">[Using the PolicyActivity Activity](http://go.microsoft.com/fwlink/?LinkId=178521) and <xref:System.Workflow.Activities.PolicyActivity></span></span>|  
  
 <span data-ttu-id="c633e-240">Oluşturulan iş akışları [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] tarafından sağlanan tüm kuralları özelliklere kullanmayın [!INCLUDE[wf1](../../../includes/wf1-md.md)]bildirim temelli etkinlik koşullar ve gibi koşullu etkinlikler gibi <xref:System.Workflow.Activities.ConditionedActivityGroup> ve <xref:System.Workflow.Activities.ReplicatorActivity>.</span><span class="sxs-lookup"><span data-stu-id="c633e-240">Workflows created in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] do not use all of the rules features provided by [!INCLUDE[wf1](../../../includes/wf1-md.md)], such as declarative activity conditions and conditional activities such as the <xref:System.Workflow.Activities.ConditionedActivityGroup> and <xref:System.Workflow.Activities.ReplicatorActivity>.</span></span> <span data-ttu-id="c633e-241">Gerekirse, bu işlevselliği kullanılarak oluşturulan iş akışları için kullanılabilir [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] ve [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c633e-241">If required, this functionality is available for workflows created using [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] and [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="c633e-242">[Geçiş Kılavuzu](../../../docs/framework/windows-workflow-foundation/migration-guidance.md).</span><span class="sxs-lookup"><span data-stu-id="c633e-242"> [Migration Guidance](../../../docs/framework/windows-workflow-foundation/migration-guidance.md).</span></span>