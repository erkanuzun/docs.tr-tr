---
title: "C# ve Visual Studio Code - C# Kılavuzu ile çalışmaya başlama"
description: "Oluşturma ve C# Visual Studio Code kullanarak ilk .NET Core uygulamanızda hata ayıklama hakkında bilgi edinin."
keywords: "C#, Get başlatıldığından, edinme, yükleme, Visual Studio Code, platformlar arası"
author: kendrahavens
ms.author: mairaw
ms.date: 09/27/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 76c23597-4cf9-467e-8a47-0c3703ce37e7
ms.openlocfilehash: 3a9de689946507e4b6d89f684461d65049b3375a
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2017
---
# <a name="get-started-with-c-and-visual-studio-code"></a><span data-ttu-id="d1546-104">C# ve Visual Studio Code ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="d1546-104">Get Started with C# and Visual Studio Code</span></span>

<span data-ttu-id="d1546-105">.NET core size Windows, Linux ve macOS çalışan uygulamaları oluşturmak için hızlı ve modüler bir platform sağlar.</span><span class="sxs-lookup"><span data-stu-id="d1546-105">.NET Core gives you a fast and modular platform for creating applications that run on Windows, Linux, and macOS.</span></span> <span data-ttu-id="d1546-106">Visual Studio Code C# uzantısı ile bir güçlü C# IntelliSense (Akıllı kod tamamlama) için tam destek deneyimi düzenleme ve hata ayıklama almak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1546-106">Use Visual Studio Code with the C# extension to get a powerful editing experience with full support for C# IntelliSense (smart code completion) and debugging.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d1546-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="d1546-107">Prerequisites</span></span>

1. <span data-ttu-id="d1546-108">Yükleme [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="d1546-108">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
2. <span data-ttu-id="d1546-109">Yükleme [.NET Core SDK](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="d1546-109">Install the [.NET Core SDK](https://www.microsoft.com/net/download/core).</span></span>
3. <span data-ttu-id="d1546-110">Yükleme [C# uzantısı](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) Visual Studio kod marketten.</span><span class="sxs-lookup"><span data-stu-id="d1546-110">Install the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) from the Visual Studio Code Marketplace.</span></span>

## <a name="hello-world"></a><span data-ttu-id="d1546-111">Merhaba Dünya</span><span class="sxs-lookup"><span data-stu-id="d1546-111">Hello World</span></span>

<span data-ttu-id="d1546-112">.NET Core üzerinde basit bir "Hello World" programla başlayalım:</span><span class="sxs-lookup"><span data-stu-id="d1546-112">Let's get started with a simple "Hello World" program on .NET Core:</span></span>

1. <span data-ttu-id="d1546-113">Bir proje açın:</span><span class="sxs-lookup"><span data-stu-id="d1546-113">Open a project:</span></span>

    * <span data-ttu-id="d1546-114">Visual Studio Code'da açın.</span><span class="sxs-lookup"><span data-stu-id="d1546-114">Open Visual Studio Code.</span></span>
    * <span data-ttu-id="d1546-115">Sol menüde Explorer simgesine tıklayın ve ardından **Klasör Aç**.</span><span class="sxs-lookup"><span data-stu-id="d1546-115">Click on the Explorer icon on the left menu and then click **Open Folder**.</span></span>
    * <span data-ttu-id="d1546-116">Seçin **dosya** > **klasörünü Aç** olması ve'ı tıklatın, C# projesinde istediğiniz klasörü açmak için ana menüden **Klasör Seç**.</span><span class="sxs-lookup"><span data-stu-id="d1546-116">Select **File** > **Open Folder** from the main menu to open the folder you want your C# project to be in and click **Select Folder**.</span></span> <span data-ttu-id="d1546-117">Bizim örneğimizde, bir klasör adında Projemizin için oluşturuyoruz *HelloWorld*.</span><span class="sxs-lookup"><span data-stu-id="d1546-117">For our example, we're creating a folder for our project named *HelloWorld*.</span></span>

      ![VSCodeOpenFolder](media/with-visual-studio-code/vscodeopenfolder.png)

2. <span data-ttu-id="d1546-119">Bir C# projesi başlatın:</span><span class="sxs-lookup"><span data-stu-id="d1546-119">Initialize a C# project:</span></span>
    * <span data-ttu-id="d1546-120">Visual Studio koddan seçerek tümleşik Terminali açın **Görünüm** > **tümleşik Terminal** ana menüden.</span><span class="sxs-lookup"><span data-stu-id="d1546-120">Open the Integrated Terminal from Visual Studio Code by selecting **View** > **Integrated Terminal** from the main menu.</span></span>
    * <span data-ttu-id="d1546-121">Terminal penceresinde yazın `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="d1546-121">In the terminal window, type `dotnet new console`.</span></span>
    * <span data-ttu-id="d1546-122">Bu komut oluşturur bir `Program.cs` , adlandırılmış bir C# proje dosyası ile birlikte yazılmış bir basit "Hello World" programla klasörünüzdeki dosya `HelloWorld.csproj`.</span><span class="sxs-lookup"><span data-stu-id="d1546-122">This command creates a `Program.cs` file in your folder with a simple "Hello World" program already written, along with a C# project file named `HelloWorld.csproj`.</span></span>

      ![Dotnet yeni komutu](media/with-visual-studio-code/dotnetnew.png)

3. <span data-ttu-id="d1546-124">Yapı varlıklar çözün:</span><span class="sxs-lookup"><span data-stu-id="d1546-124">Resolve the build assets:</span></span>

    * <span data-ttu-id="d1546-125">İçin **.NET Core 1.x**, türü `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="d1546-125">For **.NET Core 1.x**, type `dotnet restore`.</span></span> <span data-ttu-id="d1546-126">Çalışan `dotnet restore` projenizi oluşturmak için gereken gerekli .NET Core paketlerini erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="d1546-126">Running `dotnet restore` gives you access to the  required .NET Core packages that are needed to build your project.</span></span>

      ![Dotnet restore komutu](media/with-visual-studio-code/dotnetrestore.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. <span data-ttu-id="d1546-128">"Hello World" programı çalıştır:</span><span class="sxs-lookup"><span data-stu-id="d1546-128">Run the "Hello World" program:</span></span>

    * <span data-ttu-id="d1546-129">Türü `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="d1546-129">Type `dotnet run`.</span></span> 

      ![Dotnet komutunu çalıştırın](media/with-visual-studio-code/dotnetrun.png)

<span data-ttu-id="d1546-131">Üzerinde kısa videosu ek kurulum Yardım almak için izleyebileceğiniz [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), veya [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="d1546-131">You can also watch a short video tutorial for further setup help on [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), or [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

## <a name="debug"></a><span data-ttu-id="d1546-132">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="d1546-132">Debug</span></span>

1. <span data-ttu-id="d1546-133">Açık *Program.cs* üzerinde tıklatarak.</span><span class="sxs-lookup"><span data-stu-id="d1546-133">Open *Program.cs* by clicking on it.</span></span> <span data-ttu-id="d1546-134">Visual Studio Code C# dosyasını açın ilk kez [OmniSharp](http://www.omnisharp.net/) Düzenleyicisi'nde yükler.</span><span class="sxs-lookup"><span data-stu-id="d1546-134">The first time you open a C# file in Visual Studio Code, [OmniSharp](http://www.omnisharp.net/) loads in the editor.</span></span>

    ![Program.cs dosyasını açın](media/with-visual-studio-code/opencs.png)

2. <span data-ttu-id="d1546-136">Visual Studio Code oluşturun ve uygulamanızın hatalarını ayıklama eksik varlıklar eklemenizi ister.</span><span class="sxs-lookup"><span data-stu-id="d1546-136">Visual Studio Code should prompt you to add the missing assets to build and debug your app.</span></span> <span data-ttu-id="d1546-137">Seçin **Evet**.</span><span class="sxs-lookup"><span data-stu-id="d1546-137">Select **Yes**.</span></span> 

    ![Eksik varlıklar sor](media/with-visual-studio-code/missing-assets.png)

3. <span data-ttu-id="d1546-139">Hata ayıklama görünümünü açmak için sol tarafındaki menüde hata ayıklama simgeyi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="d1546-139">To open the Debug view, click on the Debugging icon on the left side menu.</span></span>

    ![Hata ayıklama sekmesini açın](media/with-visual-studio-code/opendebug.png)

4. <span data-ttu-id="d1546-141">Yeşil ok bölmesinin üst bulun.</span><span class="sxs-lookup"><span data-stu-id="d1546-141">Locate the green arrow at the top of the pane.</span></span> <span data-ttu-id="d1546-142">Aşağı açılan yanında sahip olduğundan emin olun `.NET Core Launch (console)` seçili.</span><span class="sxs-lookup"><span data-stu-id="d1546-142">Make sure the drop-down next to it has `.NET Core Launch (console)` selected.</span></span>

    ![.NET Core seçme](media/with-visual-studio-code/selectcore.png)

5. <span data-ttu-id="d1546-144">Kesme noktası tıklayarak projenize ekleme **Düzenleyicisi kenar boşluğu**, sol tarafındaki satırını 9 yanındaki düzenleyicide satır numaralarını alanı olduğu.</span><span class="sxs-lookup"><span data-stu-id="d1546-144">Add a breakpoint to your project by clicking on the **editor margin**, which is the space on the left of the line numbers in the editor, next to line 9.</span></span>

    ![Kesme noktası ayarlama](media/with-visual-studio-code/setbreakpoint.png)

6. <span data-ttu-id="d1546-146">Hata ayıklama başlatmak için <kbd>F5</kbd> veya yeşil ok.</span><span class="sxs-lookup"><span data-stu-id="d1546-146">To start debugging, select <kbd>F5</kbd> or the green arrow.</span></span> <span data-ttu-id="d1546-147">Önceki adımda ayarladığınız kesme noktasına ulaştığında hata ayıklayıcı programınızın çalışmayı durdurur.</span><span class="sxs-lookup"><span data-stu-id="d1546-147">The debugger stops execution of your program when it reaches the breakpoint you set in the previous step.</span></span>
    * <span data-ttu-id="d1546-148">Hata ayıklama sırasında üst sol bölmede, yerel değişkenleri görüntüleyemez veya hata ayıklama konsolunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1546-148">While debugging, you can view your local variables in the top left pane or use the debug console.</span></span>

    ![Çalıştırın ve hata ayıklama](media/with-visual-studio-code/rundebug.png)

7. <span data-ttu-id="d1546-150">Hata ayıklama devam etmek için üst yeşil ok veya durdurmak için kırmızı kare üst seçin.</span><span class="sxs-lookup"><span data-stu-id="d1546-150">Select the green arrow at the top to continue debugging, or select the red square at the top to stop.</span></span>

> [!TIP] 
> <span data-ttu-id="d1546-151">Daha fazla bilgi ve .NET Core OmniSharp Visual Studio Code ile hata ayıklama ipuçları sorun giderme için bkz: [.NET çekirdek hata ayıklayıcısı yönergeleri](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="d1546-151">For more information and troubleshooting tips on .NET Core debugging with OmniSharp in Visual Studio Code, see [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d1546-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1546-152">See also</span></span>
<span data-ttu-id="d1546-153">[Visual Studio Code ayarlama](https://code.visualstudio.com/docs/setup/setup-overview) </span><span class="sxs-lookup"><span data-stu-id="d1546-153">[Setting up Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview) </span></span>  
[<span data-ttu-id="d1546-154">Visual Studio kodda hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="d1546-154">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/editor/debugging)