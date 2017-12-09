---
title: "Visual Basic ile .NET Framework'te Bağlantı Noktası İşlemleri"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8db016461ea204eaf349a2c588670a237c9e583b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a><span data-ttu-id="1f86a-102">Visual Basic ile .NET Framework'te Bağlantı Noktası İşlemleri</span><span class="sxs-lookup"><span data-stu-id="1f86a-102">Port Operations in the .NET Framework with Visual Basic</span></span>
<span data-ttu-id="1f86a-103">Bilgisayarınızın seri bağlantı noktaları üzerinden erişebilirsiniz [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sınıfları <xref:System.IO.Ports?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="1f86a-103">You can access your computer's serial ports through the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="1f86a-104">En önemli sınıfı <xref:System.IO.Ports.SerialPort>, zaman uyumlu ve olay denetimli g/ç, PIN ve sonu durumları erişimi ve seri sürücü özelliklerine erişimi için bir çerçeve sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f86a-104">The most important class, <xref:System.IO.Ports.SerialPort>, provides a framework for synchronous and event-driven I/O, access to pin and break states, and access to serial driver properties.</span></span> <span data-ttu-id="1f86a-105">İçinde kaydırılan bir <xref:System.IO.Stream> nesnesi üzerinden erişilebilir <xref:System.IO.Ports.SerialPort.BaseStream%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="1f86a-105">It can be wrapped in a <xref:System.IO.Stream> object, accessible through the <xref:System.IO.Ports.SerialPort.BaseStream%2A> property.</span></span> <span data-ttu-id="1f86a-106">Kaydırma <xref:System.IO.Ports.SerialPort> içinde bir <xref:System.IO.Stream> nesne akışları kullanan sınıfları tarafından erişilecek seri bağlantı noktası sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f86a-106">Wrapping <xref:System.IO.Ports.SerialPort> in a <xref:System.IO.Stream> object allows the serial port to be accessed by classes that use streams.</span></span> <span data-ttu-id="1f86a-107">Ad alanı, seri bağlantı noktaları denetim basitleştirmek numaralandırmalar içerir.</span><span class="sxs-lookup"><span data-stu-id="1f86a-107">The namespace includes enumerations that simplify the control of serial ports.</span></span>  
  
 <span data-ttu-id="1f86a-108">En basit yolu oluşturmak için bir <xref:System.IO.Ports.SerialPort> nesnesidir aracılığıyla <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1f86a-108">The simplest way to create a <xref:System.IO.Ports.SerialPort> object is through the <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1f86a-109">Kullanamazsınız [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] doğrudan bağlantı noktaları, paralel bağlantı noktaları, USB bağlantı noktaları vb. gibi diğer türleri erişmek için sınıflar.</span><span class="sxs-lookup"><span data-stu-id="1f86a-109">You cannot use [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes to directly access other types of ports, such as parallel ports, USB ports, and so on.</span></span>  
  
## <a name="enumerations"></a><span data-ttu-id="1f86a-110">Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="1f86a-110">Enumerations</span></span>  
 <span data-ttu-id="1f86a-111">Bu tabloda listelenmekte ve seri bağlantı noktasına erişmek için kullanılan ana numaralandırmalar açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="1f86a-111">This table lists and describes the main enumerations used for accessing a serial port:</span></span>  
  
|<span data-ttu-id="1f86a-112">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="1f86a-112">Enumeration</span></span>|<span data-ttu-id="1f86a-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f86a-113">Description</span></span>|  
|---|---|   
|<xref:System.IO.Ports.Handshake>|<span data-ttu-id="1f86a-114">Bir seri bağlantı noktası iletişimi için oluşturmada kullanılan Denetim Protokolü belirten bir <xref:System.IO.Ports.SerialPort> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="1f86a-114">Specifies the control protocol used in establishing a serial port communication for a <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.Parity>|<span data-ttu-id="1f86a-115">İçin eşlik biti belirten bir <xref:System.IO.Ports.SerialPort> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="1f86a-115">Specifies the parity bit for a <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.SerialData>|<span data-ttu-id="1f86a-116">Seri bağlantı noktasında alınan karakter türünü belirtir <xref:System.IO.Ports.SerialPort> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="1f86a-116">Specifies the type of character that was received on the serial port of the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.SerialError>|<span data-ttu-id="1f86a-117">Üzerinde oluşan hataları belirtir <xref:System.IO.Ports.SerialPort> nesnesi</span><span class="sxs-lookup"><span data-stu-id="1f86a-117">Specifies errors that occur on the <xref:System.IO.Ports.SerialPort> object</span></span>|  
|<xref:System.IO.Ports.SerialPinChange>|<span data-ttu-id="1f86a-118">Oluştu değişiklik türünü belirtir <xref:System.IO.Ports.SerialPort> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="1f86a-118">Specifies the type of change that occurred on the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.StopBits>|<span data-ttu-id="1f86a-119">Dur bitleri kullanılan sayısını belirtir <xref:System.IO.Ports.SerialPort> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="1f86a-119">Specifies the number of stop bits used on the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1f86a-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1f86a-120">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 [<span data-ttu-id="1f86a-121">Bilgisayar bağlantı noktalarına erişme</span><span class="sxs-lookup"><span data-stu-id="1f86a-121">Accessing the Computer's Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)