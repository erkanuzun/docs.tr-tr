---
title: Oluşturma ve bir iş akışı örneği çalıştırma
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: 3bfcde3dd635820fa66d639134a43e5e43186c17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513692"
---
# <a name="creating-and-running-a-workflow-instance"></a>Oluşturma ve bir iş akışı örneği çalıştırma
Bu örnek, bir iş akışı örneği çalıştırmak gösterilmiştir. Zaman uyumlu ve zaman uyumsuz olarak yürütülecek nasıl gösterir.  
  
## <a name="demonstrates"></a>Gösteriler  
 <xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.  
  
## <a name="discussion"></a>Tartışma  
 İlk bölümü örneğinin kullandığı <xref:System.Activities.WorkflowInvoker.Invoke%2A>. Bir iş akışını yürütmek için en temel yolu budur. İş akışları ile yürütülen <xref:System.Activities.WorkflowInvoker.Invoke%2A> zaman uyumlu olarak yürütülür.  
  
 İkinci bölümü örneğinin kullandığı <xref:System.Activities.WorkflowApplication> sınıfı. <xref:System.Activities.WorkflowApplication> çalışan bir iş akışı ile etkileşim kurmak için ve iş akışını zaman uyumsuz olarak çalıştırmak için yeteneği dahil olmak üzere her örneği üzerinde daha fazla denetime sahip olmasını sağlar.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WorkflowInvoker ve WorkflowApplication Kullanma](../../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md)
