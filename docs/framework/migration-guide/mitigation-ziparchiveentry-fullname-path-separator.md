---
title: "Azaltma: ZipArchiveEntry.FullName yol ayırıcısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 36af59772418f5622d411f9df843f5dcd296be13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a><span data-ttu-id="9fee0-102">Azaltma: ZipArchiveEntry.FullName yol ayırıcısı</span><span class="sxs-lookup"><span data-stu-id="9fee0-102">Mitigation: ZipArchiveEntry.FullName Path Separator</span></span>
<span data-ttu-id="9fee0-103">Hedefleyen uygulamalar ile başlayan [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], kullanılan yol ayırıcısı <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> özelliği, ters eğik çizgi değişti ("\\") bir eğik çizgi ("/") için .NET Framework'ün önceki sürümlerinde kullanılan.</span><span class="sxs-lookup"><span data-stu-id="9fee0-103">Starting with apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], the path separator used in the <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> property has changed from the backslash ("\\") used in previous versions of the .NET Framework to a forward slash ("/").</span></span>   <span data-ttu-id="9fee0-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType>nesneler aşırı birini çağırarak oluşturulur <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9fee0-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> objects are created by calling one of the overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="9fee0-105">Etki</span><span class="sxs-lookup"><span data-stu-id="9fee0-105">Impact</span></span>  
 <span data-ttu-id="9fee0-106">Değişiklik 4.4.17.1 bölümüne ile uygunluk .NET uygulamasına getirir [. ZIP dosyası biçim belirtimi](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) ve sağlar. Windows olmayan sistemlerde açılması için ZIP arşivler.</span><span class="sxs-lookup"><span data-stu-id="9fee0-106">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span>  
  
 <span data-ttu-id="9fee0-107">Dizin yapısı korumak için .NET Framework Windows olmayan işletim sistemlerinde Macintosh gibi önceki bir sürümünü başarısız hedefleyen bir uygulama tarafından oluşturulan bir zip dosyası açılıyor.</span><span class="sxs-lookup"><span data-stu-id="9fee0-107">Decompressing a zip file created  by an app that targets a previous version of the .NET Framework on non-Windows operating systems such as the Macintosh fails to preserve the directory structure.</span></span> <span data-ttu-id="9fee0-108">Örneğin, dosya, dosya adı, dizin yolu bir eğik çizgi ile birlikte art arda ekler kümesi oluşturur Macintosh ("\\") karakterleri ve dosya adı.</span><span class="sxs-lookup"><span data-stu-id="9fee0-108">For example, on the Macintosh, it creates a set of files whose filename concatenates the directory path, along with any backslash ("\\") characters, and the filename.</span></span> <span data-ttu-id="9fee0-109">Sonuç olarak, açılan sıkıştırılmış dosyaların dizin yapısını korunmaz.</span><span class="sxs-lookup"><span data-stu-id="9fee0-109">As a result, the directory structure of decompressed files is not preserved.</span></span>  
  
 <span data-ttu-id="9fee0-110">Bu değişiklik etkisi. .NET Framework API'leri tarafından Windows işletim sistemi sıkıştırması ZIP dosyaları <xref:System.IO> bu API'leri bir eğik çizgi ("/") veya ters eğik çizgi sorunsuz bir şekilde işleyebilir beri ad alanı en az olmalıdır ("\\") yol ayırıcı karakter olarak.</span><span class="sxs-lookup"><span data-stu-id="9fee0-110">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in the .NET Framework <xref:System.IO> namespace should be minimal, since these APIs can seamlessly handle either a slash ("/") or a backslash ("\\") as the path separator character.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="9fee0-111">Azaltma</span><span class="sxs-lookup"><span data-stu-id="9fee0-111">Mitigation</span></span>  
 <span data-ttu-id="9fee0-112">Bu davranış istenmeyen ise, dışında bir yapılandırma ayarı ekleyerek seçebilirsiniz [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) uygulama yapılandırma dosyasının.</span><span class="sxs-lookup"><span data-stu-id="9fee0-112">If this behavior is undesirable, you can opt out of by adding a configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="9fee0-113">Aşağıdaki her ikisi de gösterir `<runtime>` bölümü ve vazgeçme anahtar.</span><span class="sxs-lookup"><span data-stu-id="9fee0-113">The following shows both the `<runtime>` section and the opt-out switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 <span data-ttu-id="9fee0-114">Buna ek olarak, .NET Framework'ün önceki sürümlerini hedefleyen ancak üzerinde çalışan uygulamalar [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] ve sonraki sürümler kabul etme Bu davranışı için bir yapılandırma ayarı ekleyerek [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) bölümü Uygulama yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="9fee0-114">In addition, apps that target previous versions of the .NET Framework but are running on the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and later versions can opt in to this behavior by adding a configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="9fee0-115">Aşağıdaki her ikisi de gösterir `<runtime>` bölümü ve katılımı anahtar.</span><span class="sxs-lookup"><span data-stu-id="9fee0-115">The following shows both the `<runtime>` section and the opt-in switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9fee0-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9fee0-116">See Also</span></span>  
 [<span data-ttu-id="9fee0-117">Yeniden hedefleme değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="9fee0-117">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)  
 [<span data-ttu-id="9fee0-118">4.6.1 uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="9fee0-118">Application Compatibility in 4.6.1</span></span>](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)