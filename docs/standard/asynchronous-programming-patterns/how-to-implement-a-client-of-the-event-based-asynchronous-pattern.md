---
title: 'Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Desenin İstemcisini Uygulama'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 21a858c1-3c99-4904-86ee-0d17b49804fa
ms.openlocfilehash: a6363bc5900c797ebd3422430f368bf2668d3364
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567282"
---
# <a name="how-to-implement-a-client-of-the-event-based-asynchronous-pattern"></a>Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Desenin İstemcisini Uygulama
Aşağıdaki kod örneğinde aynılarını bir bileşen kullanımı gösterilmiştir [olay tabanlı zaman uyumsuz desene genel bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md). Bu örnek için form kullanır `PrimeNumberCalculator` açıklanan bileşen [nasıl yapılır: olay tabanlı zaman uyumsuz deseni destekleyen bir bileşeni uygulama](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
 Bu örnek kullanan proje çalıştırdığınızda bir kılavuz ve iki düğme "Asal sayı hesaplayıcı" formla görürsünüz: **yeni görev Başlat** ve **iptal**. Tıklayabilirsiniz **yeni görev Başlat** birkaç kez art arda düğmesini ve her tıklatma için rastgele oluşturulmuş test sayının asal olup olmadığını belirlemek için bir hesaplama zaman uyumsuz bir işlem başlatılacak. Form düzenli aralıklarla ilerleme ve artımlı sonuçlarını görüntüler. Her bir işlemin benzersiz görev kimlik atanır. Hesaplamanın sonucu görüntülenen **sonuç** sütun; test sayı prime değilse olarak etiketlenir **bileşik,** ve ilk bölen görüntülenir.  
  
 İle tüm bekleyen işlemi iptal edilebilir **iptal** düğmesi. Birden çok seçimin yapılabilir.  
  
> [!NOTE]
>  Çoğu numaraları asal olmaz. Sonra birkaç tamamlanmış işlemler asal sayı bulunan değil, yalnızca diğer görevler başlatın ve bazı asal sayılar sonunda bulacaksınız.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#10)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ComponentModel.AsyncOperation>  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>
