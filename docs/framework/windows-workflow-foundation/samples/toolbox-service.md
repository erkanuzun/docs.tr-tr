---
title: Araç kutusu hizmeti
ms.date: 03/30/2017
ms.assetid: 742212d0-445e-41ed-9739-9ee848ce7f1b
ms.openlocfilehash: 0b3ea56d28d202bd8356fea1783b6675a708631d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516197"
---
# <a name="toolbox-service"></a>Araç kutusu hizmeti
Bu örnek nasıl güncelleştirileceğini gösterir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] etkinlikler araç kutusu temel iş akışı bağlamı. Örnek özel bir aktivite seçili olduğundan dayalı araç kutusu içeriği değiştiren bir iş akışı içerir.  
  
## <a name="discussion"></a>Tartışma  
 İş akışı yazma sırasında müşteriler genellikle içeriğe duyarlı olması için araç kutusu istersiniz. Örneğin, kullanıcının belirli bir etkinliğe akışına eklendiğinde birkaç ek etkinlikler araç kutusu gösterir emin olmak isteyebilirsiniz. Etkinlikler iş akışını kaldırdıysanız, araç etki alanı gereksinimlerine bağlı olarak uygun şekilde tepki vermelidir.  
  
 Yeniden barındırılan iş akışı Tasarımcısı'nda araç kutusu denetim ve iş akışı Model değişiklikleri esas emin olabilirsiniz, araç kutusu denetiminde uygun değişiklikleri konak tetikler. Bununla birlikte, [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], araç kutusu kullanıcı tarafından denetlenmeyen ve böylece içeriğini değiştirmek için bir arabirim için gereklidir. `IActivityToolboxService` Bu arabirimidir.  
  
 API'si aşağıdaki dört yöntemi sağlar.  
  
```  
public interface IActivityToolboxService   
{   
        void AddCategory(string categoryName);   
        void RemoveCategory(string categoryName);   
        void AddItem(string qualifiedTypeName, string categoryName);   
        void RemoveItem(string qualifiedTypeName, string categoryName);   
        IList<string> EnumCategories();   
        IList<string> EnumItems(string categoryName);   
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], WorkflowSimulator.sln çözüm dosyasını açın.  
  
2.  CTRL + SHIFT + B tuşlarına basarak çözümü oluşturun.  
  
3.  Workflow.xaml dosyasını açın.  
  
4.  Ekleme bir **CustomActivity** Araç Kutusu'ndan bırakarak. Adlı bir ek araç kategorisine dikkat edin: **yeni WF kategori** ek bir etkinliği ile **atamak**.  
  
5.  Şimdi işaretini **CustomActivity** başka bir etkinlik içine sürükleyerek.  
  
6.  Öğe **atamak** kategorisinde **yeni WF kategori** altında araç kutusu artık kaldırılmıştır. Ayrıca, kategoride başka bir öğe yok olduğundan, kategori de kaldırılır.  
  
7.  Seçin **CustomActivity** yeniden ve kategori ve **atamak** etkinlik geri eklendi.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\IActivityToolboxService`
