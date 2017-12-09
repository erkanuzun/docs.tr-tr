---
title: FTP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: FTP
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d7b169a6de494d10fa332ebf5f2aa315ae69653a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ftp"></a><span data-ttu-id="9b755-102">FTP</span><span class="sxs-lookup"><span data-stu-id="9b755-102">FTP</span></span>
<span data-ttu-id="9b755-103">.NET Framework, FTP Protokolü ile için kapsamlı destek sağlar. <xref:System.Net.FtpWebRequest> ve <xref:System.Net.FtpWebResponse> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="9b755-103">The .NET Framework provides comprehensive support for the FTP protocol with the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes.</span></span> <span data-ttu-id="9b755-104">Bu sınıfların türetilmiş <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="9b755-104">These classes are derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="9b755-105">Çoğu durumda, <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıfları isteği yapmak için gerekli olan tüm sağlar, ancak özellik olarak sunulan FTP özgü özellikler erişmesi gerekiyorsa, bu sınıfları typecast <xref:System.Net.FtpWebRequest> veya <xref:System.Net.FtpWebResponse>.</span><span class="sxs-lookup"><span data-stu-id="9b755-105">In most cases, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide all that is necessary to make the request, but if you need access to the FTP-specific features exposed as properties, you can typecast these classes to <xref:System.Net.FtpWebRequest> or <xref:System.Net.FtpWebResponse>.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="9b755-106">Örnekler</span><span class="sxs-lookup"><span data-stu-id="9b755-106">Examples</span></span>  
 <span data-ttu-id="9b755-107">Daha fazla bilgi için aşağıdaki konulara bakın: [nasıl yapılır: dosyaları FTP ile](../../../docs/framework/network-programming/how-to-download-files-with-ftp.md), [nasıl yapılır: FTP karşıya yükleme dosyalarıyla](../../../docs/framework/network-programming/how-to-upload-files-with-ftp.md), ve [nasıl yapılır: FTP ile dizin içeriğini listele](../../../docs/framework/network-programming/how-to-list-directory-contents-with-ftp.md).</span><span class="sxs-lookup"><span data-stu-id="9b755-107">For more information, see the following topics: [How to: Download Files with FTP](../../../docs/framework/network-programming/how-to-download-files-with-ftp.md), [How to: Upload Files with FTP](../../../docs/framework/network-programming/how-to-upload-files-with-ftp.md), and [How to: List Directory Contents with FTP](../../../docs/framework/network-programming/how-to-list-directory-contents-with-ftp.md).</span></span>  
  
## <a name="ftp-and-proxies"></a><span data-ttu-id="9b755-108">FTP ve proxy'ler</span><span class="sxs-lookup"><span data-stu-id="9b755-108">FTP and proxies</span></span>  
 <span data-ttu-id="9b755-109">Bir proxy sunucu varsa (tarafından belirtilen <xref:System.Net.FtpWebRequest.Proxy%2A> özelliği) bir HTTP proxy yalnızca ise <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, ve <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> komutları desteklenir.</span><span class="sxs-lookup"><span data-stu-id="9b755-109">If a proxy (specified by the <xref:System.Net.FtpWebRequest.Proxy%2A> property) is an HTTP proxy, then only the <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, and <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> commands are supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b755-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9b755-110">See Also</span></span>  
 [<span data-ttu-id="9b755-111">Bir Proxy üzerinden Internet erişimi</span><span class="sxs-lookup"><span data-stu-id="9b755-111">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [<span data-ttu-id="9b755-112">Ağ programlama örnekleri</span><span class="sxs-lookup"><span data-stu-id="9b755-112">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)  
 [<span data-ttu-id="9b755-113">FTP istemcisi teknolojisi örnek</span><span class="sxs-lookup"><span data-stu-id="9b755-113">FTP Client Technology Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=179557)  
 [<span data-ttu-id="9b755-114">FTP Gezgini teknolojisi örneği</span><span class="sxs-lookup"><span data-stu-id="9b755-114">FTP Explorer Technology Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=179569)  
 [<span data-ttu-id="9b755-115">Uygulama protokolleri kullanma</span><span class="sxs-lookup"><span data-stu-id="9b755-115">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)