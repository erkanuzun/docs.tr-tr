### <a name="sqlconnectionopen-fails-on-windows-7-with-non-ifs-winsock-bsp-or-lsp-present"></a><span data-ttu-id="3df2b-101">SqlConnection.Open IFS Winsock BSP veya LSP mevcut Windows 7'de başarısız olur</span><span class="sxs-lookup"><span data-stu-id="3df2b-101">SqlConnection.Open fails on Windows 7 with non-IFS Winsock BSP or LSP present</span></span>

|   |   |
|---|---|
|<span data-ttu-id="3df2b-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="3df2b-102">Details</span></span>|<span data-ttu-id="3df2b-103"><xref:System.Data.SqlClient.SqlConnection.Open> ve <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)> IFS Winsock BSP veya LSP sahip bir Windows 7 makine üzerinde çalışan bilgisayarda .NET Framework 4. 5 ' başarısız. IFS BSP veya LSP yüklü olup olmadığını belirlemek için <code>netsh WinSock Show Catalog</code> komut ve inceleyin her <code>Winsock Catalog Provider Entry</code> döndürülen öğe.</span><span class="sxs-lookup"><span data-stu-id="3df2b-103"><xref:System.Data.SqlClient.SqlConnection.Open> and <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)> fail in the .NET Framework 4.5 if running on a Windows 7 machine with a non-IFS Winsock BSP or LSP are present on the computer.To determine whether a non-IFS BSP or LSP is installed, use the <code>netsh WinSock Show Catalog</code> command, and examine every <code>Winsock Catalog Provider Entry</code> item that is returned.</span></span> <span data-ttu-id="3df2b-104">Hizmet bayrakları değere sahip olursa <code>0x20000</code> bit kümesi, sağlayıcı IFS tanıtıcıları kullanır ve düzgün çalışır.</span><span class="sxs-lookup"><span data-stu-id="3df2b-104">If the Service Flags value has the <code>0x20000</code> bit set, the provider uses IFS handles and will work correctly.</span></span> <span data-ttu-id="3df2b-105">Varsa <code>0x20000</code> bit Temizle (ayarlanmamış), IFS BSP veya LSP.</span><span class="sxs-lookup"><span data-stu-id="3df2b-105">If the <code>0x20000</code> bit is clear (not set), it is a non-IFS BSP or LSP.</span></span>|
|<span data-ttu-id="3df2b-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="3df2b-106">Suggestion</span></span>|<span data-ttu-id="3df2b-107">.NET Framework yükselterek önlenebilir için .NET Framework 4.5.2, bu hatanın düzeltildiğini.</span><span class="sxs-lookup"><span data-stu-id="3df2b-107">This bug has been fixed in the .NET Framework 4.5.2, so it can be avoided by upgrading the .NET Framework.</span></span> <span data-ttu-id="3df2b-108">Alternatif olarak, tüm yüklü olmayan - IFS Winsock LSPs kaldırarak önlenebilir.</span><span class="sxs-lookup"><span data-stu-id="3df2b-108">Alternatively, it can be avoided by removing any installed non-IFS Winsock LSPs.</span></span>|
|<span data-ttu-id="3df2b-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="3df2b-109">Scope</span></span>|<span data-ttu-id="3df2b-110">Küçük</span><span class="sxs-lookup"><span data-stu-id="3df2b-110">Minor</span></span>|
|<span data-ttu-id="3df2b-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="3df2b-111">Version</span></span>|<span data-ttu-id="3df2b-112">4,5</span><span class="sxs-lookup"><span data-stu-id="3df2b-112">4.5</span></span>|
|<span data-ttu-id="3df2b-113">Tür</span><span class="sxs-lookup"><span data-stu-id="3df2b-113">Type</span></span>|<span data-ttu-id="3df2b-114">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="3df2b-114">Runtime</span></span>|
|<span data-ttu-id="3df2b-115">Etkilenen API'leri</span><span class="sxs-lookup"><span data-stu-id="3df2b-115">Affected APIs</span></span>|<ul><li><xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|
