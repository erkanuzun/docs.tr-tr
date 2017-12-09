---
title: "Nasıl yapılır: Durum makinesi iş akışı oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5b094fd88321ffcf8d3bb5cdefe870bd12524b4b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-state-machine-workflow"></a><span data-ttu-id="ca80d-102">Nasıl yapılır: Durum makinesi iş akışı oluşturma</span><span class="sxs-lookup"><span data-stu-id="ca80d-102">How to: Create a State Machine Workflow</span></span>
<span data-ttu-id="ca80d-103">İş akışları yerleşik etkinliklerden yanı sıra özel etkinliklerden oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="ca80d-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="ca80d-104">Bu konudaki adımları hem yerleşik etkinlikler gibi kullanan bir iş akışı oluşturma aracılığıyla <xref:System.Activities.Statements.StateMachine> etkinliği ve önceki özel etkinlikler [nasıl yapılır: bir etkinlik oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) konu.</span><span class="sxs-lookup"><span data-stu-id="ca80d-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.StateMachine> activity, and the custom activities from the previous [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="ca80d-105">Sayı tahmin eden oyun iş akışını modeller.</span><span class="sxs-lookup"><span data-stu-id="ca80d-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ca80d-106">Başlarken Öğreticisi her bir konuda önceki konularda bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ca80d-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="ca80d-107">Bu konuda tamamlamak için önce tamamlamanız gereken [nasıl yapılır: bir etkinlik oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="ca80d-107">To complete this topic, you must first complete [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ca80d-108">Öğreticinin tamamlanmış bir sürümünü indirmek için bkz: [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](http://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="ca80d-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="ca80d-109">İş akışını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="ca80d-109">To create the workflow</span></span>  
  
1.  <span data-ttu-id="ca80d-110">Sağ **NumberGuessWorkflowActivities** içinde **Çözüm Gezgini** seçip **Ekle**, **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="ca80d-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2.  <span data-ttu-id="ca80d-111">İçinde **yüklü**, **ortak öğeler** düğümü, select **iş akışı**.</span><span class="sxs-lookup"><span data-stu-id="ca80d-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="ca80d-112">Seçin **etkinlik** gelen **iş akışı** listesi.</span><span class="sxs-lookup"><span data-stu-id="ca80d-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3.  <span data-ttu-id="ca80d-113">Tür `StateMachineNumberGuessWorkflow` içine **adı** kutusuna ve tıklatın **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="ca80d-113">Type `StateMachineNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4.  <span data-ttu-id="ca80d-114">Sürükleme bir **Durum makinesi** etkinliğinden **Durum makinesi** bölümünü **araç** ve üzerine bırakın **etkinliğini Drop burada** üzerindeki etiket İş akışı tasarım yüzeyi.</span><span class="sxs-lookup"><span data-stu-id="ca80d-114">Drag a **StateMachine** activity from the **State Machine** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="ca80d-115">İş akışı değişkenleri ve bağımsız değişkenler oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="ca80d-115">To create the workflow variables and arguments</span></span>  
  
1.  <span data-ttu-id="ca80d-116">Çift **StateMachineNumberGuessWorkflow.xaml** içinde **Çözüm Gezgini** zaten görüntülenmiyorsa, iş akışı Tasarımcısı'nda görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="ca80d-116">Double-click **StateMachineNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2.  <span data-ttu-id="ca80d-117">Tıklatın **bağımsız değişkenleri** görüntülemek için iş akışı Tasarımcısı sol tarafındaki **bağımsız değişkenleri** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="ca80d-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3.  <span data-ttu-id="ca80d-118">Tıklatın **bağımsız değişkeni oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="ca80d-118">Click **Create Argument**.</span></span>  
  
4.  <span data-ttu-id="ca80d-119">Tür `MaxNumber` içine **adı** kutusunda **içinde** gelen **yönü** aşağı açılan listesinden, **Int32** gelen**Bağımsız değişken türü** aşağı açılan liste ve bağımsız değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ca80d-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5.  <span data-ttu-id="ca80d-120">Tıklatın **bağımsız değişkeni oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="ca80d-120">Click **Create Argument**.</span></span>  
  
6.  <span data-ttu-id="ca80d-121">Tür `Turns` içine **adı** altında yeni eklenen kutusuna `MaxNumber` bağımsız değişkeni, select **çıkışı** gelen **yönü** aşağı açılan listesinden,  **Int32** gelen **bağımsız değişken türü** aşağı açılan liste ve ENTER tuşuna BASIN.</span><span class="sxs-lookup"><span data-stu-id="ca80d-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7.  <span data-ttu-id="ca80d-122">Tıklatın **bağımsız değişkenleri** kapatmak için etkinlik Tasarımcısı sol tarafındaki **bağımsız değişkenleri** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="ca80d-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8.  <span data-ttu-id="ca80d-123">Tıklatın **değişkenleri** görüntülemek için iş akışı Tasarımcısı sol tarafındaki **değişkenleri** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="ca80d-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="ca80d-124">Tıklatın **değişken oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="ca80d-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="ca80d-125">Yoksa **oluşturma değişken** kutusu görüntülenir, tıklatın <xref:System.Activities.Statements.StateMachine> seçmek için iş akışı Tasarımcısı yüzey üzerinde etkinlik.</span><span class="sxs-lookup"><span data-stu-id="ca80d-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.StateMachine> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="ca80d-126">Tür `Guess` içine **adı** kutusunda **Int32** gelen **değişken türü** aşağı açılan liste ve değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ca80d-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="ca80d-127">Tıklatın **değişken oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="ca80d-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="ca80d-128">Tür `Target` içine **adı** kutusunda **Int32** gelen **değişken türü** aşağı açılan liste ve değişkeni kaydetmek için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ca80d-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="ca80d-129">Tıklatın **değişkenleri** kapatmak için etkinlik Tasarımcısı sol tarafındaki **değişkenleri** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="ca80d-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="ca80d-130">İş akışı etkinlikleri eklemek için</span><span class="sxs-lookup"><span data-stu-id="ca80d-130">To add the workflow activities</span></span>  
  
1.  <span data-ttu-id="ca80d-131">Tıklatın **State1** seçin.</span><span class="sxs-lookup"><span data-stu-id="ca80d-131">Click **State1** to select it.</span></span> <span data-ttu-id="ca80d-132">İçinde **Özellikler penceresini**, değiştirme **DisplayName** için `Initialize Target`.</span><span class="sxs-lookup"><span data-stu-id="ca80d-132">In the **Properties Window**, change the **DisplayName** to `Initialize Target`.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="ca80d-133">Varsa **Özellikler penceresini** görüntülenen, select değil **Özellikler penceresini** gelen **Görünüm** menüsü.</span><span class="sxs-lookup"><span data-stu-id="ca80d-133">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
2.  <span data-ttu-id="ca80d-134">Yeni adlandırılan çift **başlatma hedef** genişletmek için iş akışı Tasarımcısı'nda durum.</span><span class="sxs-lookup"><span data-stu-id="ca80d-134">Double-click the newly renamed **Initialize Target** state in the workflow designer to expand it.</span></span>  
  
3.  <span data-ttu-id="ca80d-135">Sürükle bir **atamak** etkinliğinden **Temelleri** bölümünü **araç** ve üzerine bırakın **girişi** bölüm durumu.</span><span class="sxs-lookup"><span data-stu-id="ca80d-135">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span> <span data-ttu-id="ca80d-136">Tür `Target` içine **için** kutusu ve aşağıdaki ifadesine **bir C# ifadesi girin** veya **bir VB ifadesi girin** kutusu.</span><span class="sxs-lookup"><span data-stu-id="ca80d-136">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="ca80d-137">Varsa **araç** penceresi görüntülenmez, seçin **araç** gelen **Görünüm** menüsü.</span><span class="sxs-lookup"><span data-stu-id="ca80d-137">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
4.  <span data-ttu-id="ca80d-138">Dönmek için genel durum makine görünümünde iş akışı Tasarımcısı'nı tıklatarak **Durum makinesi** haritasındaki iş akışı Tasarımcısı'nı üstünde görüntüle.</span><span class="sxs-lookup"><span data-stu-id="ca80d-138">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
5.  <span data-ttu-id="ca80d-139">Sürükle bir **durumu** etkinliğinden **Durum makinesi** bölümünü **araç** iş akışı tasarımcıya ve üzerine gelin, üzerinden **başlatma hedef** durumu.</span><span class="sxs-lookup"><span data-stu-id="ca80d-139">Drag a **State** activity from the **State Machine** section of the **Toolbox** onto the workflow designer and hover it over the **Initialize Target** state.</span></span> <span data-ttu-id="ca80d-140">Dört üçgenler geçici görüntüleneceğini unutmayın **başlatma hedef** üzerinde yeni bir durum olduğunda durumu.</span><span class="sxs-lookup"><span data-stu-id="ca80d-140">Note that four triangles will appear around the **Initialize Target** state when the new state is over it.</span></span> <span data-ttu-id="ca80d-141">Hemen aşağıdadır üçgen yeni durumunu bırakma **başlatma hedef** durumu.</span><span class="sxs-lookup"><span data-stu-id="ca80d-141">Drop the new state on the triangle that is immediately below the **Initialize Target** state.</span></span> <span data-ttu-id="ca80d-142">Bu iş akışı üzerine yeni durum yerleştirir ve bir geçiş oluşturur **başlatma hedef** yeni durumuna durum.</span><span class="sxs-lookup"><span data-stu-id="ca80d-142">This places the new state onto the workflow and creates a transition from the **Initialize Target** state to the new state.</span></span>  
  
6.  <span data-ttu-id="ca80d-143">Tıklatın **State1** seçmek için değiştirme **DisplayName** için `Enter Guess`ve genişletmek için iş akışı Tasarımcısı'nda durumu çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="ca80d-143">Click **State1** to select it, change the **DisplayName** to `Enter Guess`, and then double-click the state in the workflow designer to expand it.</span></span>  
  
7.  <span data-ttu-id="ca80d-144">Sürükleme bir **WriteLine** etkinliğinden **Temelleri** bölümünü **araç** ve üzerine bırakın **giriş** bölüm durumu.</span><span class="sxs-lookup"><span data-stu-id="ca80d-144">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span>  
  
8.  <span data-ttu-id="ca80d-145">İçine aşağıdaki ifadeyi yazın **metin** özellik kutusuna **WriteLine**.</span><span class="sxs-lookup"><span data-stu-id="ca80d-145">Type the following expression into the **Text** property box of the **WriteLine**.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. <span data-ttu-id="ca80d-146">Sürükle bir **atamak** etkinliğinden **Temelleri** bölümünü **araç** ve üzerine bırakma **çıkış** bölüm durumu.</span><span class="sxs-lookup"><span data-stu-id="ca80d-146">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop onto the **Exit** section of the state.</span></span>  
  
10. <span data-ttu-id="ca80d-147">Tür `Turns` içine **için** kutusu ve `Turns + 1` içine **bir C# ifadesi girin** veya **bir VB ifadesi girin** kutusu.</span><span class="sxs-lookup"><span data-stu-id="ca80d-147">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
11. <span data-ttu-id="ca80d-148">Dönmek için genel durum makine görünümünde iş akışı Tasarımcısı'nı tıklatarak **Durum makinesi** haritasındaki iş akışı Tasarımcısı'nı üstünde görüntüle.</span><span class="sxs-lookup"><span data-stu-id="ca80d-148">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
12. <span data-ttu-id="ca80d-149">Sürükleme bir **son durum** etkinliğinden **Durum makinesi** bölümünü **araç**, üzerine gelin, üzerinden **girin tahmin** durum ve bırakın sağ tarafında görünür üçgen üzerine **girin tahmin** arasında bir geçiş oluşturulan durum **girin tahmin** ve **son durum**.</span><span class="sxs-lookup"><span data-stu-id="ca80d-149">Drag a **FinalState** activity from the **State Machine** section of the **Toolbox**, hover it over the **Enter Guess** state, and drop it onto the triangle that appears to the right of the **Enter Guess** state so that a transition is created between **Enter Guess** and **FinalState**.</span></span>  
  
13. <span data-ttu-id="ca80d-150">Geçiş varsayılan adı **T2**.</span><span class="sxs-lookup"><span data-stu-id="ca80d-150">The default name of the transition is **T2**.</span></span> <span data-ttu-id="ca80d-151">Geçişi seçin ve ayarlamak için iş akışı Tasarımcısı'nda tıklatın, **DisplayName** için **tahmin doğru**.</span><span class="sxs-lookup"><span data-stu-id="ca80d-151">Click the transition in the workflow designer to select it, and set its **DisplayName** to **Guess Correct**.</span></span> <span data-ttu-id="ca80d-152">Ardından tıklatın ve seçin **son durum**ve iki durumlu birini kaplayan olmadan görüntülenecek tam geçiş adı yer olmasını sağlamak sağa sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="ca80d-152">Then click and select the **FinalState**, and drag it to the right so that there is room for the full transition name to be displayed without overlaying either of the two states.</span></span> <span data-ttu-id="ca80d-153">Bu, öğreticide kalan adımları tamamlamak daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="ca80d-153">This will make it easier to complete the remaining steps in the tutorial.</span></span>  
  
14. <span data-ttu-id="ca80d-154">Yeni adlandırılan çift **tahmin doğru** geçiş genişletmek için iş akışı Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="ca80d-154">Double-click the newly renamed **Guess Correct** transition in the workflow designer to expand it.</span></span>  
  
15. <span data-ttu-id="ca80d-155">Sürükleme bir **readInt** etkinliğinden **NumberGuessWorkflowActivities** bölümünü **araç** sürükleyip bırakın **tetikleyici** bölümü geçişin.</span><span class="sxs-lookup"><span data-stu-id="ca80d-155">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Trigger** section of the transition.</span></span>  
  
16. <span data-ttu-id="ca80d-156">İçinde **Özellikler penceresini** için **readInt** etkinliği, türü `"EnterGuess"` tırnak işaretleri içine dahil **YerİşaretiAdı** özellik değeri kutusu ve türü `Guess`içine **sonuç** özellik değeri kutusu</span><span class="sxs-lookup"><span data-stu-id="ca80d-156">In the **Properties Window** for the **ReadInt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box, and type `Guess` into the **Result** property value box</span></span>  
  
17. <span data-ttu-id="ca80d-157">İçine aşağıdaki ifadeyi yazın **tahmin doğru** geçiş'ın **koşulu** özellik değeri kutusu.</span><span class="sxs-lookup"><span data-stu-id="ca80d-157">Type the following expression into the **Guess Correct** transition’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. <span data-ttu-id="ca80d-158">Dönmek için genel durum makine görünümünde iş akışı Tasarımcısı'nı tıklatarak **Durum makinesi** haritasındaki iş akışı Tasarımcısı'nı üstünde görüntüle.</span><span class="sxs-lookup"><span data-stu-id="ca80d-158">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ca80d-159">Tetik olayı alındığında bir geçiş oluşur ve <xref:System.Activities.Statements.Transition.Condition%2A>, varsa, değerlendiren `True`.</span><span class="sxs-lookup"><span data-stu-id="ca80d-159">A transition occurs when the trigger event is received and the <xref:System.Activities.Statements.Transition.Condition%2A>, if present, evaluates to `True`.</span></span> <span data-ttu-id="ca80d-160">Bu geçiş için kullanıcının `Guess` rastgele oluşturulmuş eşleşen `Target`, Denetim geçer sonra **son durum** ve iş akışı tamamlandığında.</span><span class="sxs-lookup"><span data-stu-id="ca80d-160">For this transition, if the user’s `Guess` matches the randomly generated `Target`, then control passes to the **FinalState** and the workflow completes.</span></span>  
  
19. <span data-ttu-id="ca80d-161">Tahmin doğru olup olmamasına bağlı olarak, iş akışı ya da geçiş **son durum** veya yeniden **girin tahmin** durum başka bir deneyin.</span><span class="sxs-lookup"><span data-stu-id="ca80d-161">Depending on whether the guess is correct, the workflow should transition either to the **FinalState** or back to the **Enter Guess** state for another try.</span></span> <span data-ttu-id="ca80d-162">Her iki geçişler aracılığıyla alınacak kullanıcının tahmin bekleniyor, aynı tetikleyici paylaşmak **readInt** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="ca80d-162">Both transitions share the same trigger of waiting for the user’s guess to be received via the **ReadInt** activity.</span></span> <span data-ttu-id="ca80d-163">Bu, paylaşılan bir geçiş adı verilir.</span><span class="sxs-lookup"><span data-stu-id="ca80d-163">This is called a shared transition.</span></span> <span data-ttu-id="ca80d-164">Paylaşılan bir geçiş oluşturmak için başlangıcını gösterir daireyi tıklatın **tahmin doğru** geçer ve belirtilen istenen duruma sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="ca80d-164">To create a shared transition, click the circle that indicates the start of the **Guess Correct** transition and drag it to the desired state.</span></span> <span data-ttu-id="ca80d-165">Bu durumda geçiş kendi başına bir geçiş, bu nedenle başlangıç noktası olarak sürükleyin **tahmin doğru** geçiş ve alt geri bırakma **girin tahmin** durumu.</span><span class="sxs-lookup"><span data-stu-id="ca80d-165">In this case the transition is a self-transition, so drag the start point of the **Guess Correct** transition and drop it back onto the bottom of the **Enter Guess** state.</span></span> <span data-ttu-id="ca80d-166">Geçiş oluşturduktan sonra iş akışı Tasarımcısı'nda seçin ve ayarlayın, **DisplayName** özelliğine **tahmin yanlış**.</span><span class="sxs-lookup"><span data-stu-id="ca80d-166">After creating the transition, select it in the workflow designer and set its **DisplayName** property to **Guess Incorrect**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ca80d-167">Paylaşılan geçişleri de oluşturulabilir gelen geçiş Tasarımcısı'nda tıklayarak **paylaşılan tetikleyici geçiş Ekle** geçiş Tasarımcısı'nı ve ardından istenen hedef durumundan seçerek altındaki  **Bağlanmak için kullanılabilir durumları** açılır.</span><span class="sxs-lookup"><span data-stu-id="ca80d-167">Shared transitions can also be created from within the transition designer by clicking **Add shared trigger transition** at the bottom of the transition designer, and then selecting the desired target state from the **Available states to connect** drop-down.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ca80d-168">Unutmayın <xref:System.Activities.Statements.Transition.Condition%2A> bir geçişin değerlendiren `false` (veya bir paylaşılan tetikleyici geçiş koşulların tümü için değerlendirin `false`), geçiş gerçekleşmez ve durumundan tüm geçişler için tüm Tetikleyicileri olacaktır yeniden.</span><span class="sxs-lookup"><span data-stu-id="ca80d-168">Note that if the <xref:System.Activities.Statements.Transition.Condition%2A> of a transition evaluates to `false` (or all of the conditions of a shared trigger transition evaluate to `false`), the transition will not occur and all triggers for all the transitions from the state will be rescheduled.</span></span> <span data-ttu-id="ca80d-169">Bu öğreticide, bu durum koşulları yapılandırılmış yol nedeniyle meydana olamaz (tahmin doğru veya yanlış olmasına için belirli eylemler uyguluyoruz).</span><span class="sxs-lookup"><span data-stu-id="ca80d-169">In this tutorial, this situation cannot happen because of the way the conditions are configured (we have specific actions for whether the guess is correct or incorrect).</span></span>  
  
20. <span data-ttu-id="ca80d-170">Çift **tahmin yanlış** geçiş genişletmek için iş akışı Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="ca80d-170">Double-click the **Guess Incorrect** transition in the workflow designer to expand it.</span></span> <span data-ttu-id="ca80d-171">Unutmayın **tetikleyici** aynı zaten ayarlanmış **readInt** tarafından kullanılan etkinlik **tahmin doğru** geçiş.</span><span class="sxs-lookup"><span data-stu-id="ca80d-171">Note that the **Trigger** is already set to the same **ReadInt** activity that was used by the **Guess Correct** transition.</span></span>  
  
21. <span data-ttu-id="ca80d-172">İçine aşağıdaki ifadeyi yazın **koşulu** özellik değeri kutusu.</span><span class="sxs-lookup"><span data-stu-id="ca80d-172">Type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. <span data-ttu-id="ca80d-173">Sürükle bir **varsa** etkinliğinden **akış denetimi** bölümünü **araç** sürükleyip bırakın **eylem** geçişi bölümü.</span><span class="sxs-lookup"><span data-stu-id="ca80d-173">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Action** section of the transition.</span></span>  
  
23. <span data-ttu-id="ca80d-174">İçine aşağıdaki ifadeyi yazın **varsa** etkinliğin **koşulu** özellik değeri kutusu.</span><span class="sxs-lookup"><span data-stu-id="ca80d-174">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
24. <span data-ttu-id="ca80d-175">İki **WriteLine** etkinliklerden **Temelleri** bölümünü **araç** ve böylece içinde biridir bırakın **sonra** bölümü **varsa** etkinliği ve bir **Else** bölümü.</span><span class="sxs-lookup"><span data-stu-id="ca80d-175">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the **If** activity, and one is in the **Else** section.</span></span>  
  
25. <span data-ttu-id="ca80d-176">Tıklatın **WriteLine** etkinliğinde **sonra** seçmek için bölümünde ve içine aşağıdaki ifadeyi yazın **metin** özellik değeri kutusu.</span><span class="sxs-lookup"><span data-stu-id="ca80d-176">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```
    "Your guess is too low."  
    ```  
  
26. <span data-ttu-id="ca80d-177">Tıklatın **WriteLine** etkinliğinde **Else** seçmek için bölümünde ve içine aşağıdaki ifadeyi yazın **metin** özellik değeri kutusu.</span><span class="sxs-lookup"><span data-stu-id="ca80d-177">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```
    "Your guess is too high."  
    ```  
  
27. <span data-ttu-id="ca80d-178">Dönmek için genel durum makine görünümünde iş akışı Tasarımcısı'nı tıklatarak **Durum makinesi** haritasındaki iş akışı Tasarımcısı'nı üstünde görüntüle.</span><span class="sxs-lookup"><span data-stu-id="ca80d-178">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
     <span data-ttu-id="ca80d-179">Aşağıdaki örnek, tamamlanan iş akışı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ca80d-179">The following example illustrates the completed workflow.</span></span>  
  
     <span data-ttu-id="ca80d-180">![Durum makinesi iş akışı tamamlandı](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")</span><span class="sxs-lookup"><span data-stu-id="ca80d-180">![Completed State Machine Workflow](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")</span></span>  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="ca80d-181">İş akışı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="ca80d-181">To build the workflow</span></span>  
  
1.  <span data-ttu-id="ca80d-182">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ca80d-182">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="ca80d-183">İş akışını çalıştırmak yönergeler Lütfen görmek için sonraki konuyu [nasıl yapılır: bir iş akışını çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="ca80d-183">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span> <span data-ttu-id="ca80d-184">Zaten tamamladıysanız [nasıl yapılır: bir iş akışını çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) adım farklı bir iş akışı stil ile ve çalıştırmak bu adım Durum makinesi iş akışını kullanarak istediğiniz, için İleri atlayabilirsiniz [oluşturmak veuygulamayıçalıştırmakiçin](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication) bölümünü [nasıl yapılır: bir iş akışını çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="ca80d-184">If you have already completed the [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the state machine workflow from this step, skip ahead to the [To build and run the application](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca80d-185">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ca80d-185">See Also</span></span>  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [<span data-ttu-id="ca80d-186">Windows Workflow Foundation programlama</span><span class="sxs-lookup"><span data-stu-id="ca80d-186">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [<span data-ttu-id="ca80d-187">İş akışları tasarlama</span><span class="sxs-lookup"><span data-stu-id="ca80d-187">Designing Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [<span data-ttu-id="ca80d-188">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="ca80d-188">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [<span data-ttu-id="ca80d-189">Nasıl yapılır: bir etkinlik oluşturmak</span><span class="sxs-lookup"><span data-stu-id="ca80d-189">How to: Create an Activity</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [<span data-ttu-id="ca80d-190">Nasıl yapılır: bir iş akışını çalıştırma</span><span class="sxs-lookup"><span data-stu-id="ca80d-190">How to: Run a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)