---
title: ConfigurationCodeGenerator
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3913aae8-165f-4014-9262-7fe426f90cb2
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eb88d7e523c671886e3ccb0fe22d545c616e2289
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="configurationcodegenerator"></a><span data-ttu-id="b2678-102">ConfigurationCodeGenerator</span><span class="sxs-lookup"><span data-stu-id="b2678-102">ConfigurationCodeGenerator</span></span>
<span data-ttu-id="b2678-103">ConfigurationCodeGenerator, özel kanal uygulamaları yapılandırma sistemi için kullanıma sunmak için kullanabileceğiniz bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="b2678-103">The ConfigurationCodeGenerator is a tool that you can use to expose your custom channel implementations to the configuration system.</span></span> <span data-ttu-id="b2678-104">Bu, kanalınızı yalnızca bunlar bir sistem tarafından sağlanan gibi bağlama yapılandırdığınız gibi bir .config dosyası kullanarak yapılandırmak, özel kanal kullanıcılarının sağlar `NetTcpBinding` veya özel bir bağlama kullanarak `TcpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="b2678-104">This allows users of your custom channel to configure your channel by using a .config file just as they would configure a system-provided binding such as `NetTcpBinding` or a custom binding using the `TcpTransportBindingElement`.</span></span>  
  
 <span data-ttu-id="b2678-105">Ne zaman özel bir kanalda yazma ve yeni bir kullanarak programlama modeli kullanıma `BindingElement` veya `Binding`, yapmak için sınıf kümesi oluşturmalısınız `BindingElement` veya `Binding` .config dosyası kullanılarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="b2678-105">When you write a custom channel and expose it to the programming model by using a new `BindingElement` or `Binding`, you must create a set of classes to make the `BindingElement` or `Binding` configurable using a .config file.</span></span> <span data-ttu-id="b2678-106">Bu sınıfları oluşturmak ve müşterinizin deneyimini geliştirmek için ConfigurationCodeGenerator aracını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2678-106">You can use the ConfigurationCodeGenerator tool to generate these classes and enhance your customer's experience.</span></span>  
  
### <a name="to-build-the-tool"></a><span data-ttu-id="b2678-107">Aracı yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="b2678-107">To build the tool</span></span>  
  
1.  <span data-ttu-id="b2678-108">Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b2678-108">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="b2678-109">Bir dosya oluşturur çözümü oluşturma: ConfigurationCodeGenerator.exe.</span><span class="sxs-lookup"><span data-stu-id="b2678-109">Building the solution generates one file: ConfigurationCodeGenerator.exe.</span></span> <span data-ttu-id="b2678-110">İçin sınıflar oluşturmak için bu aracı kullanmak nasıl oluşturulduğunu gösteren örnek komut satırı dosya SampleRun.cmd sahip [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="b2678-110">The file SampleRun.cmd has a sample command line that shows how to use this tool to generate the classes for the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
### <a name="to-run-the-tool"></a><span data-ttu-id="b2678-111">Aracı çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="b2678-111">To run the tool</span></span>  
  
1.  <span data-ttu-id="b2678-112">Her iki özel varsa komut isteminde aşağıdaki komutu yazın `BindingElement` türünü ve özel bir `Binding` türü:</span><span class="sxs-lookup"><span data-stu-id="b2678-112">At the command prompt type the following if you have both a custom `BindingElement` type and a custom `Binding` type:</span></span>  
  
    ```  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereTheseTypesAreDefined  
    ```  
  
     <span data-ttu-id="b2678-113">Veya yalnızca özel varsa, aşağıdaki komutu yazın `BindingElement` türü:</span><span class="sxs-lookup"><span data-stu-id="b2678-113">Or type the following if you have only a custom `BindingElement` type:</span></span>  
  
    ```  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /dll: TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     <span data-ttu-id="b2678-114">Veya yalnızca özel varsa, aşağıdaki komutu yazın `Binding` türü:</span><span class="sxs-lookup"><span data-stu-id="b2678-114">Or type the following if you have only a custom `Binding` type:</span></span>  
  
    ```  
    ConfigurationCodeGenerator.exe /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     <span data-ttu-id="b2678-115">Komutu için üç .cs dosyaları oluşturur `BindingElement` (belirttiyseniz / olabilir: seçeneği), standart beş .cs dosyaları `Binding` (/sb belirtilmişse: seçeneği) ve bir .xml dosyası.</span><span class="sxs-lookup"><span data-stu-id="b2678-115">The command generates three .cs files for the `BindingElement` (if you specified the /be: option), five .cs files for the standard `Binding` (if you specified the /sb: option), and a .xml file.</span></span>  
  
    1.  <span data-ttu-id="b2678-116">/Be seçeneği kullanılırsa, .cs birini uygulayan dosyaları `BindingElementExtensionSection` bağlama öğesi için.</span><span class="sxs-lookup"><span data-stu-id="b2678-116">If you used the /be option, one of the .cs files implements the `BindingElementExtensionSection` for your binding element.</span></span> <span data-ttu-id="b2678-117">Bu kodu gösterir, `BindingElement` yapılandırma sistemi için özel diğer bağlamalar bağlama öğesi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2678-117">This code exposes your `BindingElement` to the configuration system, so that other custom bindings can use your binding element.</span></span> <span data-ttu-id="b2678-118">Diğer dosyaları Varsayılanları ve sabitleri temsil eden sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="b2678-118">The other files have classes that represent defaults and constants.</span></span> <span data-ttu-id="b2678-119">Dosyalarınız `//TODO` açıklamaları, varsayılan değerleri güncelleştirmek için şu aralıklarla uyar.</span><span class="sxs-lookup"><span data-stu-id="b2678-119">The files have `//TODO` comments to remind you to update the default values.</span></span>  
  
    2.  <span data-ttu-id="b2678-120">/Sb seçeneği belirtilmişse, iki .cs dosyaları uygulayan bir `StandardBindingElement` ve `StandardBindingCollectionElement` sırasıyla, bu, yapılandırma sistemi, standart bağlama kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="b2678-120">If you specified the /sb option, two of the .cs files implement a `StandardBindingElement` and a `StandardBindingCollectionElement` respectively, which exposes your standard binding to the configuration system.</span></span> <span data-ttu-id="b2678-121">Diğer dosyaları Varsayılanları ve sabitleri temsil eden sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="b2678-121">The other files have classes that represent defaults and constants.</span></span> <span data-ttu-id="b2678-122">Dosyalarınız `//TODO` açıklamaları, varsayılan değerleri güncelleştirmek için şu aralıklarla uyar.</span><span class="sxs-lookup"><span data-stu-id="b2678-122">The files have `//TODO` comments to remind you to update the default values.</span></span>  
  
         <span data-ttu-id="b2678-123">/Sb belirtilmişse: CodeToAddTo seçeneği\<*YourStdBinding*> .cs sahip kodu, standart bağlama uygular sınıfına el ile eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b2678-123">If you specified the /sb: option the CodeToAddTo\<*YourStdBinding*>.cs has code that you must manually add into the class that implements your standard binding.</span></span>  
  
     <span data-ttu-id="b2678-124">SampleConfig.xml dosya önceki adımda 1 veya 2 tanımlı işleyicileri kaydeder yapılandırma dosyasının eklemelisiniz yapılandırma kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="b2678-124">The SampleConfig.xml file contains the configuration code that you must add to the configuration file that registers the handlers defined in the previous step 1 or 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2678-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b2678-125">See Also</span></span>