---
title: pInvokeStackImbalance MDA
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- stack depth
- platform invoke stack imbalance
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- PInvokeStackImbalance MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: 34ddc6bd-1675-4f35-86aa-de1645d5c631
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9938db3f4a3d054fde52139c166fb6a2e2a402df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33388062"
---
# <a name="pinvokestackimbalance-mda"></a>pInvokeStackImbalance MDA
`pInvokeStackImbalance` CLR bir platform çağırma sonra çağrı yığını derinlik belirtilen çağırma verilen beklenen Yığın derinliği eşleşmiyor algıladığında yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilirse <xref:System.Runtime.InteropServices.DllImportAttribute> özniteliği yanı sıra Yönetilen imza parametrelerinde bildirimi.  
  
> [!NOTE]
>  `pInvokeStackImbalance` MDA yalnızca 32-bit x86 için uygulanan platformlar.  
  
> [!NOTE]
>  .NET Framework sürüm 3.5, `pInvokeStackImbalance` MDA varsayılan olarak devre dışıdır. Visual Studio 2005 ile .NET Framework sürüm 3.5 kullandığınızda `pInvokeStackImbalance` MDA görünür **yönetilen hata ayıklama Yardımcıları** listesinde **özel durumları** iletişim kutusu (olduğu durumlarda görüntülenir tıklattığınız **özel durumları** üzerinde **hata ayıklama** menüsü). Ancak, seçerek veya temizleyerek **sayıcı** onay kutusunu `pInvokeStackImbalance` etkinleştirmez veya MDA; devre dışı yalnızca Visual Studio MDA etkinleştirildiğinde, bir özel durum oluşturur olup olmadığını denetler.  
  
## <a name="symptoms"></a>Belirtiler  
 Bir uygulama, bir erişim ihlali veya yapma veya bir platform aşağıdaki Bozulması çağırma çağrısı bellek karşılaşır.  
  
## <a name="cause"></a>Sebep  
 Platform yönetilen imzası çağırma çağrısı çağrılan yöntem yönetilmeyen imzası eşleşmeyebilir.  Bu uyuşmazlık parametreleri doğru sayıda bildirme değil veya parametreler için uygun boyutu belirtmeden yönetilen imza neden olabilir.  Çağırma kuralı büyük olasılıkla tarafından belirtilmediğinden MDA de etkinleştirebilirsiniz <xref:System.Runtime.InteropServices.DllImportAttribute> özniteliği, yönetilmeyen çağırma eşleşmiyor.  
  
## <a name="resolution"></a>Çözüm  
 Gözden geçirme yönetilen platform imza ve imza ve yerel hedef çağırma kuralının eşleşen onaylamak için çağırma çağırır.  Çağırma kuralı iki yönetilen ve yönetilmeyen tarafta açıkça belirtmeyi deneyin. Ayrıca değil olarak büyük olasılıkla olsa da, yönetilmeyen işlev yönetilmeyen derleyici hatada gibi diğer bazı nedenle yığının dengesini, mümkündür.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 Zorlar, tüm platform CLR nonoptimized yolu yapılacak çağrıları çağırma.  
  
## <a name="output"></a>Çıkış  
 Platform adı MDA mesajıyla Çağırma yığını dengesizliği neden yöntem çağrısı.  Bir örnek ileti bir platform çağırma yöntemi çağrıda `SampleMethod` değil:  
  
```  
A call to PInvoke function 'SampleMethod' has unbalanced the stack.   
This is likely because the managed PInvoke signature does not match   
the unmanaged target signature. Check that the calling convention and   
parameters of the PInvoke signature match the target unmanaged signature.  
```  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <pInvokeStackImbalance />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
