---
title: İş Akışı Hizmeti Konak Genişletilebilirliği
ms.date: 03/30/2017
ms.assetid: c0e8f7bb-cb13-49ec-852f-b85d7c23972f
ms.openlocfilehash: 3393843e6be75e122c3993b3ccfb7c56d63cebad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33504074"
---
# <a name="workflow-service-host-extensibility"></a>İş Akışı Hizmeti Konak Genişletilebilirliği
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] sağlar <xref:System.ServiceModel.Activities.WorkflowServiceHost> iş akışı hizmetlerini barındırma için sınıf. Bu sınıf, kendi kendine yönetilen bir uygulamada bir iş akışı hizmeti veya bir Windows hizmeti barındırıyorsanız kullanılır. Bu sınıf ayrıca Internet Information Services (IIS) veya Windows İşlem Etkinleştirme Hizmeti (WAS) ile bir iş akışı hizmeti barındırma kullanılır. <xref:System.ServiceModel.Activities.WorkflowServiceHost> Sınıfı, özel uzantılar eklemenize izin uzantı noktaları boşta davranışı değiştirmek ve ana bilgisayar hizmet olmayan iş akışları (Mesajlaşma etkinlikleri kullanmayın iş akışları) sağlar.  
  
## <a name="workflow-service-host-extensions"></a>İş akışı hizmeti ana bilgisayar uzantıları  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost> İçeren bir <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> türündeki özelliği <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager> uzantısı eklemek için yöntemler sağlar <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Kullanım <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager.Add%2A> her iş akışı hizmeti örneği için bir uzantı ekleme yöntemi. Bir iş akışı hizmeti örneği oluşturulduğunda veya sürdürme deposundan yüklenen yeni uzantısı oluşturmak için belirtilen temsilci çağrılır. Kullanım <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager.Add%2A> her iş akışı hizmeti konağı için bir uzantı ekleme yöntemi bir uzantı örneği, tüm iş akışı hizmeti örnekleri için paylaşılır.  
  
## <a name="react-to-unhandled-exceptions"></a>İşlenmeyen özel durumlar için tepki  
 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> Bir iş akışı hizmeti içinde işlenmeyen bir özel durum oluşursa, gerçekleştirilecek eylemi belirtmenize olanak sağlar. <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior.Action%2A> Özelliği birini belirtir <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction> değerler:  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Abandon> – İş akışı hizmeti örneği durdurur.  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.AbandonAndSuspend> – Geri son kalıcı durum yapar ve iş akışı hizmeti örneği askıya alır. Bu yalnızca, iş akışı zaten en az bir kez kalıcı yapılmadı oluşur. Aksi durumda iş akışı örneği durduruldu.  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Cancel> – Örneği iptal eder.  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Terminate> – Örneği sonlandırır.  
  
 Bu davranış, aşağıdaki örnekte gösterildiği gibi kodda yapılandırılabilir.  
  
```csharp  
host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.Abandon });  
```  
  
 Bunu ayrıca bir yapılandırma dosyasında aşağıdaki örnekte gösterildiği gibi yapılandırılabilir.  
  
```xml
<behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <workflowUnhandledExceptionBehavior action="Abandon" />        
        </behavior>  
      </serviceBehaviors>  
```  
  
## <a name="hosting-non-service-workflows"></a>Barındırma hizmet olmayan iş akışları  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost> Hizmet olmayan iş akışları veya ya da ile başlamayan iş akışlarını barındırmak için kullanılan bir <xref:System.ServiceModel.Activities.Receive> etkinlik veya Mesajlaşma etkinlikleri kullanmayın iş akışları. İş akışı Hizmetleri ile normalde başlar bir <xref:System.ServiceModel.Activities.Receive> etkinlik. Zaman <xref:System.ServiceModel.Activities.WorkflowServiceHost> bir iş akışı hizmeti için bir ileti alır, zaten çalışmıyor (veya kalıcı değilse) yeni bir iş akışı hizmeti örneği oluşturulur. Bir iş akışı Al etkinliği ile başlamıyorsa, ileti almak için hiçbir etkinlik olduğundan ileti gönderme başlatılamıyor. Bir hizmet olmayan iş akışı barındırmak için öğesinden bir sınıf türetin <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> ve geçersiz kılma <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A>, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A>, ve <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnResolveBookmark%2A>. Geçersiz kılma <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A> tercih edilen örneği bir kimlik sağlamak istiyorsanız Geçersiz kılma <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> özel iş akışı bağlamı oluşturma oluşturmak veya var olan bir örneğini doldurmak için <xref:System.ServiceModel.Activities.WorkflowCreationContext>. Geçersiz kılma <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnResolveBookmark%2A> el ile gelen iletiden yer işareti ayıklamak için. Bu yöntemi geçersiz kılarsanız çağırmanız gerekir <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> WorkflowHostingEndpoint gönderilen ileti yanıtlamak amacıyla kendi gövdesindeki. Bunu yapmak, bir <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> sınırı sonunda aştı. İki yönlü sözleşmelerinde çağırmak için hata algılayabilir olabilir <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> yanıt almak için istemcinin hatadan dolayı. Tek yönlü sözleşmelerinde çağırma başarısız, hata anlamayabilir <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> sonra çok geç kadar <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> kısıtlama sınırı aşıldı. Daha fazla bilgi için lütfen bkz [WorkflowHostingEndpoint Sürdür yer işareti](../../../../docs/framework/windows-workflow-foundation/samples/workflowhostingendpoint-resume-bookmark.md)hizmet olmayan iş akışı yeni bir örneğini oluşturmak için yeni bir örnek oluşturur bir işlem tanımlayan bir hizmet sözleşmesini bildirin. Oluşturma işlemi bir IDictionary gerçekleştirmesi gereken\<dize, Nesne > herhangi geçmek için iş akışı parametreleri gerekli. Bu sözleşme örtük olarak tarafından uygulanan <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>-türetilmiş sınıf. İş akışı barındırma, bir örnek ekler <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>-çağırarak konağa türetilmiş sınıf <xref:System.ServiceModel.Activities.WorkflowServiceHost.AddServiceEndpoint%2A> ve arama <!--zz xref:System.ServiceModel.Activities.WorkflowServiceHost.Open%2A--> `System.ServiceModel.Activities.WorkflowServiceHost.Open`. İş akışı örneği oluşturmak için Oluştur bir <xref:System.ServiceModel.ChannelFactory%601> hizmet sözleşmesi türü ve çağrı <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A>. Ardından, hizmet sözleşmesini tanımlanan oluşturma işlemi çağırabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Mesajlaşma Etkinlikleri](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
