---
title: 'Nasıl yapılır: BindingSource ve ResetItem Metodunu Kullanarak Değişiklik Bildirimleri Verme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- change notifications [Windows Forms], raising
- data binding [Windows Forms], change notifications
- BindingSource component [Windows Forms], raising change notifications with
- data sources [Windows Forms], detecting changes
- change notifications
ms.assetid: ab8b4096-37ff-4e30-aabc-de79a2f2e972
ms.openlocfilehash: 5894e7036126cb5271cea65e6025e9880b0cbe3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534605"
---
# <a name="how-to-raise-change-notifications-using-the-bindingsource-resetitem-method"></a>Nasıl yapılır: BindingSource ve ResetItem Metodunu Kullanarak Değişiklik Bildirimleri Verme
Öğeler değişti, eklendiğinde veya bazı veri kaynakları, denetimleri için değişiklik bildirimleri yükseltmeyin. İle <xref:System.Windows.Forms.BindingSource> bileşeni, bu tür veri kaynaklarına bağlayın ve kodunuzdan bir değişiklik bildirimi oluştur.  
  
## <a name="example"></a>Örnek  
 Kullanarak bu formu gösteren bir <xref:System.Windows.Forms.BindingSource> bir listeye bağlamak için bileşen bir <xref:System.Windows.Forms.DataGridView> denetim. Listenin değişiklik bildirimleri oluşturmaz böylece <xref:System.Windows.Forms.BindingSource.ResetItem%2A> yöntemi <xref:System.Windows.Forms.BindingSource> listedeki bir öğe değiştirildiğinde çağrılır. biçimindeki telefon numarasıdır.  
  
 [!code-cpp[System.Windows.Forms.DataConnector.ResetItem#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.ResetItem#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.ResetItem#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Data, System.Drawing ve System.Windows.Forms derlemelerine başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.  Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [BindingSource Bileşeni](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
