---
title: 'Nasıl yapılır: Odak Olaylarını Kullanarak Öğenin Rengini Değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- focus events [WPF], changing element color for
- colors of elements [WPF], changing
- elements [WPF], changing color of
ms.assetid: 7e246802-3625-47a7-ae9d-c8a2a40fd040
ms.openlocfilehash: d8d8a3e8b24021cf8a5f916ce3f291a3b66d9411
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543120"
---
# <a name="how-to-change-the-color-of-an-element-using-focus-events"></a>Nasıl yapılır: Odak Olaylarını Kullanarak Öğenin Rengini Değiştirme
Bu örnek kazanır ve kullanarak odağı kaybettiğinde öğenin rengini değiştirmek nasıl gösterir <xref:System.Windows.UIElement.GotFocus> ve <xref:System.Windows.UIElement.LostFocus> olaylar.  
  
 Bu örnek oluşan bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyası ve bir arka plan kod dosyası.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] iki oluşur kullanıcı arabirimi oluşturan <xref:System.Windows.Controls.Button> nesneleri ve olay işleyicileri iliştirir <xref:System.Windows.UIElement.GotFocus> ve <xref:System.Windows.UIElement.LostFocus> olayları <xref:System.Windows.Controls.Button> nesneleri.  
  
 [!code-xaml[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml#gotlostfocussamplexaml)]  
  
 Aşağıdaki arka plan kodu oluşturur <xref:System.Windows.UIElement.GotFocus> ve <xref:System.Windows.UIElement.LostFocus> olay işleyicileri.  Zaman <xref:System.Windows.Controls.Button> kazancı klavye odağı <xref:System.Windows.Controls.Control.Background%2A> , <xref:System.Windows.Controls.Button> kırmızı değiştirilir.  Zaman <xref:System.Windows.Controls.Button> klavye odağı kaybettiğinde <xref:System.Windows.Controls.Control.Background%2A> , <xref:System.Windows.Controls.Button> beyaza geri değişir.  
  
 [!code-csharp[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml.cs#gotlostfocussampleeventhandlers)]
 [!code-vb[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/VisualBasic/Window1.xaml.vb#gotlostfocussampleeventhandlers)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Girişe Genel Bakış](../../../../docs/framework/wpf/advanced/input-overview.md)
