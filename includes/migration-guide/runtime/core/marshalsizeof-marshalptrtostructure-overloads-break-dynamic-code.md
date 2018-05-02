### <a name="marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a><span data-ttu-id="77465-101">Marshal.SizeOf ve Marshal.PtrToStructure aşırı dinamik kodu Böl</span><span class="sxs-lookup"><span data-stu-id="77465-101">Marshal.SizeOf and Marshal.PtrToStructure overloads break dynamic code</span></span>

|   |   |
|---|---|
|<span data-ttu-id="77465-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="77465-102">Details</span></span>|<span data-ttu-id="77465-103">Yöntemlere dinamik olarak bağlama .NET Framework 4.5.1,'den başlayarak <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)>, veya <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)>, (üzerinden, Windows PowerShell, IronPython veya C# dinamik anahtar sözcüğü, örneğin) sonuçlanabilir <code>MethodInvocationExceptions</code> bu yöntemlerin yeni aşırı altyapılarının belirsiz olabilecek eklenmediğinden.</span><span class="sxs-lookup"><span data-stu-id="77465-103">Beginning in the .NET Framework 4.5.1, dynamically binding to the methods <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)>, or <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)>, (via Windows PowerShell, IronPython, or the C# dynamic keyword, for example) can result in <code>MethodInvocationExceptions</code> because new overloads of these methods have been added that may be ambiguous to the scripting engines.</span></span>|
|<span data-ttu-id="77465-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="77465-104">Suggestion</span></span>|<span data-ttu-id="77465-105">Hangi aşırı yüklemenin kullanılması gerektiğini açıkça belirtmek için komut dosyaları güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="77465-105">Update scripts to clearly indicate which overload should be used.</span></span> <span data-ttu-id="77465-106">Genellikle yöntemleri türü parametreleri olarak açıkça atama tarafından yapılır olabilir <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="77465-106">This can typically done by explicitly casting the methods' type parameters as <xref:System.Type>.</span></span> <span data-ttu-id="77465-107">Bkz: [bu bağlantıyı](https://support.microsoft.com/kb/2909958/) daha fazla ayrıntı ve nasıl örnekleri için geçici çözüm sorun.</span><span class="sxs-lookup"><span data-stu-id="77465-107">See [this link](https://support.microsoft.com/kb/2909958/) for more detail and examples of how to workaround the issue.</span></span>|
|<span data-ttu-id="77465-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="77465-108">Scope</span></span>|<span data-ttu-id="77465-109">Küçük</span><span class="sxs-lookup"><span data-stu-id="77465-109">Minor</span></span>|
|<span data-ttu-id="77465-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="77465-110">Version</span></span>|<span data-ttu-id="77465-111">4.5.1</span><span class="sxs-lookup"><span data-stu-id="77465-111">4.5.1</span></span>|
|<span data-ttu-id="77465-112">Tür</span><span class="sxs-lookup"><span data-stu-id="77465-112">Type</span></span>|<span data-ttu-id="77465-113">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="77465-113">Runtime</span></span>|
