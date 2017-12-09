---
title: TCP UDP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- protocols, TCP/UDP
- network resources, TCP/UDP
- sending data, TCP/UDP
- TCP/UDP
- TcpClient class, about TcpClient class
- application protocols, TCP/UDP
- receiving data, TCP/UDP
- TcpListener class, about TcpListener class
- Socket class, about Socket class
- UDP
- data requests, TCP/UDP
- requesting data from Internet, TCP/UDP
- Internet, TCP/UDP
ms.assetid: df29b4b0-49e8-4923-82b9-13150dfc40f5
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 04a3bb1c7499a60175aaaa9715e780ea5ddceb31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="tcp-udp"></a><span data-ttu-id="327b9-102">TCP UDP</span><span class="sxs-lookup"><span data-stu-id="327b9-102">TCP-UDP</span></span>
<span data-ttu-id="327b9-103">Uygulamalar, İletim Denetimi Protokolü (TCP) ve kullanıcı veri birimi Protokolü (UDP) Hizmetleri ile kullanabileceğiniz <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, ve <xref:System.Net.Sockets.UdpClient> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="327b9-103">Applications can use Transmission Control Protocol (TCP) and User Datagram Protocol (UDP) services with the <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, and <xref:System.Net.Sockets.UdpClient> classes.</span></span> <span data-ttu-id="327b9-104">Bu protocol sınıflar üstünde oluşturulan <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> sınıf ve veri aktarma ayrıntılarını dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="327b9-104">These protocol classes are built on top of the <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> class and take care of the details of transferring data.</span></span>  
  
 <span data-ttu-id="327b9-105">Zaman uyumlu yöntemleri Protokolü sınıfları kullanan **yuva** durumu bilgilerini yönetmek veya ayarlama ayrıntılarını bilmek yükü olmadan Ağ Hizmetleri basit ve kolay erişim sağlamak için sınıfı protokole özgü yuva.</span><span class="sxs-lookup"><span data-stu-id="327b9-105">The protocol classes use the synchronous methods of the **Socket** class to provide simple and straightforward access to network services without the overhead of maintaining state information or knowing the details of setting up protocol-specific sockets.</span></span> <span data-ttu-id="327b9-106">Zaman uyumsuz kullanılacak **yuva** yöntemleri tarafından sağlanan zaman uyumsuz yöntemleri kullanabilir <xref:System.Net.Sockets.NetworkStream> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="327b9-106">To use asynchronous **Socket** methods, you can use the asynchronous methods supplied by the <xref:System.Net.Sockets.NetworkStream> class.</span></span> <span data-ttu-id="327b9-107">Erişim özelliklerine **yuva** Protokolü sınıfları tarafından gösterilmeyen sınıfı kullanmalısınız **yuva** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="327b9-107">To access features of the **Socket** class not exposed by the protocol classes, you must use the **Socket** class.</span></span>  
  
 <span data-ttu-id="327b9-108">**TcpClient** ve **TcpListener** kullanarak ağ temsil **NetworkStream** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="327b9-108">**TcpClient** and **TcpListener** represent the network using the **NetworkStream** class.</span></span> <span data-ttu-id="327b9-109">Kullandığınız <xref:System.Net.Sockets.TcpClient.GetStream%2A> ağ akışı dönüp akışın çağırmak için yöntemi <xref:System.Net.Sockets.NetworkStream.Read%2A> ve <xref:System.Net.Sockets.NetworkStream.Write%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="327b9-109">You use the <xref:System.Net.Sockets.TcpClient.GetStream%2A> method to return the network stream, and then call the stream's <xref:System.Net.Sockets.NetworkStream.Read%2A> and <xref:System.Net.Sockets.NetworkStream.Write%2A> methods.</span></span> <span data-ttu-id="327b9-110">**NetworkStream** kapatma yuva etkilemesini protocol sınıflar temel yuva, kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="327b9-110">The **NetworkStream** does not own the protocol classes' underlying socket, so closing it does not affect the socket.</span></span>  
  
 <span data-ttu-id="327b9-111">**UdpClient** sınıfı UDP veri birimi tutacak bir bayt dizisi kullanır.</span><span class="sxs-lookup"><span data-stu-id="327b9-111">The **UdpClient** class uses an array of bytes to hold the UDP datagram.</span></span> <span data-ttu-id="327b9-112">Kullandığınız <xref:System.Net.Sockets.UdpClient.Send%2A> ağa veri göndermek için yöntem ve <xref:System.Net.Sockets.UdpClient.Receive%2A> gelen bir veri biriminde almaya yöntemi.</span><span class="sxs-lookup"><span data-stu-id="327b9-112">You use the <xref:System.Net.Sockets.UdpClient.Send%2A> method to send the data to the network and the <xref:System.Net.Sockets.UdpClient.Receive%2A> method to receive an incoming datagram.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="327b9-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="327b9-113">See Also</span></span>  
 [<span data-ttu-id="327b9-114">TCP Hizmetleri kullanma</span><span class="sxs-lookup"><span data-stu-id="327b9-114">Using TCP Services</span></span>](../../../docs/framework/network-programming/using-tcp-services.md)  
 [<span data-ttu-id="327b9-115">UDP Hizmetleri kullanma</span><span class="sxs-lookup"><span data-stu-id="327b9-115">Using UDP Services</span></span>](../../../docs/framework/network-programming/using-udp-services.md)  
 [<span data-ttu-id="327b9-116">Ağda akışlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="327b9-116">Using Streams on the Network</span></span>](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [<span data-ttu-id="327b9-117">Zaman uyumsuz Server yuva kullanma</span><span class="sxs-lookup"><span data-stu-id="327b9-117">Using an Asynchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)  
 [<span data-ttu-id="327b9-118">Zaman uyumsuz istemci yuvası kullanma</span><span class="sxs-lookup"><span data-stu-id="327b9-118">Using an Asynchronous Client Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)  
 [<span data-ttu-id="327b9-119">Uygulama protokolleri kullanma</span><span class="sxs-lookup"><span data-stu-id="327b9-119">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)