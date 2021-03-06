---
title: WPF ve XAML içinde WF tümleştirmesi
ms.date: 03/30/2017
ms.assetid: a4f53b48-fc90-4315-bca0-ba009562f488
ms.openlocfilehash: 2fb145a8511383c37be536a78522a256514c08c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518196"
---
# <a name="wpf-and-wf-integration-in-xaml"></a>WPF ve XAML içinde WF tümleştirmesi
Bu örnek, tek bir XAML belge içinde Windows Presentation Foundation (WPF) ve Windows Workflow Foundation (WF) özelliklerini kullanan bir uygulama oluşturmak gösterilmiştir. Bunu başarmak için Windows Workflow Foundation (WF) ve XAML genişletilebilirlik örnek kullanır.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 İçine ShowWindow.xaml dosyası çıkarır bir <xref:System.Activities.Statements.Sequence> sırasının etkinlikler tarafından yönetilen iki dize değişkenleri etkinlikle: `ShowWindow` ve `WriteLine`. <xref:System.Activities.Statements.WriteLine> Etkinlik için atar ifade konsol penceresine çıkarır <xref:System.Activities.Statements.WriteLine.Text%2A> özelliği. `ShowWindow` Etkinlik görüntüler bir [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] pencere yürütme mantığının parçası olarak. <xref:System.Activities.ActivityContext.DataContext%2A> Sırada bildirilen değişkenlerin pencerenin içerir. Pencerenin denetimleri bildirilen `ShowWindow` etkinliği değişkenlere işlemek için veri bağlama kullanın. Son olarak, pencerenin düğme denetimi içerir. `Click` Düğmesinin olayı tarafından işlenir bir <xref:System.Activities.ActivityDelegate> adlı `MarkupExtension` içeren bir `CloseWindow` etkinlik. `MarkUpExtension` tarafından tanımlanan herhangi bir nesne bağlamı olarak sağlar kapsanan etkinliği çağırır bir `x:Name`, yanı sıra <xref:System.Activities.ActivityContext.DataContext%2A> içeren penceresi. Bu nedenle, `CloseWindow.InArgument<Window>` pencerenin adına başvuran bir ifade kullanarak bağlanabilir.  
  
 `ShowWindow` Etkinlik türer <xref:System.Activities.AsyncCodeActivity%601> görüntülenecek sınıf bir [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] penceresi ve Pencere kapatıldığında tamamlar. `Window` Özelliği türüdür `Func<Window>` her etkinlik yürütülmesi için isteğe bağlı oluşturulması için penceresini sağlar. `Window` Özelliğini kullanan bir <xref:System.Xaml.XamlDeferringLoader> bu ertelenmiş Değerlendirme modelini etkinleştirecek şekilde. `FuncFactoryDeferringLoader` Sağlayan bir `XamlReader` seri hale getirme sırasında yakalanan ve etkinliği yürütülürken okuyun.  
  
 İyi yazılmış bir etkinlik hiçbir zaman Zamanlayıcı iş parçacığı engeller. Ancak, `ShowWindow` etkinlik görüntüleme penceresi kapatılana kadar tamamlayamıyor. `ShowWindow` Etkinlik türetme tarafından bu davranış başarır <xref:System.Activities.AsyncCodeActivity>, arama <xref:System.Activities.WorkflowInvoker.BeginInvoke%2A> yönteminde <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> yöntemi ve pencere kalıcı olarak gösteriliyor. Temsilci WPF çağrılır <xref:System.ServiceModel.InstanceContext.SynchronizationContext%2A>. `ShowWindow` Etkinlik atar <xref:System.Activities.ActivityContext.DataContext%2A> özelliğine `Window.DataContext` kapsam içinde değişkenlere herhangi bir veri sağlamak için özellik bağlı erişimi kontrol eder.  
  
 Bu örnekte ilgi son nokta bir <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension> adlı `DelegateActivityExtension`. `ProvideValue` Yöntemi bu biçimlendirme uzantısı, katıştırılmış bir etkinlik çağıran bir temsilci döndürür. Bu etkinlik içeren bir ortamda çalışır [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] veri bağlamı ve tüm `x:Name` kapsam değerleri. İçinde `GenericInvoke` yöntemi, bu ortam etkinliğine sağlanır bir <xref:System.Activities.Hosting.SymbolResolver> uzantısı. Bu uzantı eklenen bir <xref:System.Activities.WorkflowInvoker> , sonra biçimlendirme uzantının temsilci çağrılır her katıştırılmış etkinlik çağırmak için kullanılır.  
  
> [!NOTE]
>  Varsayılan Tasarımcı ShowWindow etkinlik desteklemiyor; Bu nedenle, ShowWindow.Xaml dosya Tasarımcısı'nda düzgün görüntülenmez.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], WPFWFIntegration.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Çözümü çalıştırmak için F5 tuşuna basın.  
  
4.  İlk ve son adınızı iletişim kutusuna yazın.  
  
5.  İletişim kutusunu kapatın ve konsol adınızı görüntülemektedir.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\WPFWFIntegration`