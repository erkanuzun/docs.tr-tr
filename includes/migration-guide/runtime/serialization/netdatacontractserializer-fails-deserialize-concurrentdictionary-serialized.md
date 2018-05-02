### <a name="netdatacontractserializer-fails-to-deserialize-a-concurrentdictionary-serialized-with-a-different-net-version"></a><span data-ttu-id="c8164-101">Farklı bir .NET sürüm ile seri hale getirilmiş bir ConcurrentDictionary seri durumdan çıkarılacak NetDataContractSerializer başarısız</span><span class="sxs-lookup"><span data-stu-id="c8164-101">NetDataContractSerializer fails to deserialize a ConcurrentDictionary serialized with a different .NET version</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c8164-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="c8164-102">Details</span></span>|<span data-ttu-id="c8164-103">Tasarıma göre <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> yalnızca hem seri hale getirme ve uçları seri durumdan aynı CLR Türleri paylaşıyorsa kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c8164-103">By design, the <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> can be used only if both the serializing and deserializing ends share the same CLR types.</span></span> <span data-ttu-id="c8164-104">Bu nedenle, bir .NET Framework sürümü ile seri hale getirilmiş bir nesneyi farklı bir sürüm tarafından seri durumdan çıkarılabiliyorsa garanti edilmez. <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=name> bilinen doğru .NET Framework 4.5 veya önceki serileştirilmiş ve .NET Framework 4.5.1 serisi seri durumdan değil ya da daha yeni bir tür.</span><span class="sxs-lookup"><span data-stu-id="c8164-104">Therefore, it is not guaranteed that an object serialized with one version of the .NET Framework can be deserialized by a different version.<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=name> is a type that is known to not to deserialize correctly if serialized with the .NET Framework 4.5 or earlier and deserialized with the .NET Framework 4.5.1 or later.</span></span>|
|<span data-ttu-id="c8164-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="c8164-105">Suggestion</span></span>|<span data-ttu-id="c8164-106">Bu sorunun olası iş geçici çözüm vardır:</span><span class="sxs-lookup"><span data-stu-id="c8164-106">There are a number of possible work-arounds for this issue:</span></span><ul><li><span data-ttu-id="c8164-107">.NET Framework 4.5.1, de kullanmak için biçimlendiricisi bilgisayar yükseltin.</span><span class="sxs-lookup"><span data-stu-id="c8164-107">Upgrade the serializing computer to use the .NET Framework 4.5.1, as well.</span></span></li><li><span data-ttu-id="c8164-108">Kullanım <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=name> yerine <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> tam aynı CLR türlerini hem seri hale getirme ve uçları seri durumdan beklemiyor gibi.</span><span class="sxs-lookup"><span data-stu-id="c8164-108">Use <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=name> instead of <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> as this does not expect the exact same CLR types at both serializing and deserializing ends.</span></span></li><li><span data-ttu-id="c8164-109">Kullanım <xref:System.Collections.Generic.Dictionary%602?displayProperty=name> yerine <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=name> , bu belirli 4.5 - gerçekleştirilmez beri&gt;4.5.1 bölün.</span><span class="sxs-lookup"><span data-stu-id="c8164-109">Use <xref:System.Collections.Generic.Dictionary%602?displayProperty=name> instead of <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=name> since it does not exhibit this particular 4.5-&gt;4.5.1 break.</span></span></li></ul>|
|<span data-ttu-id="c8164-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="c8164-110">Scope</span></span>|<span data-ttu-id="c8164-111">Küçük</span><span class="sxs-lookup"><span data-stu-id="c8164-111">Minor</span></span>|
|<span data-ttu-id="c8164-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="c8164-112">Version</span></span>|<span data-ttu-id="c8164-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="c8164-113">4.5.1</span></span>|
|<span data-ttu-id="c8164-114">Tür</span><span class="sxs-lookup"><span data-stu-id="c8164-114">Type</span></span>|<span data-ttu-id="c8164-115">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="c8164-115">Runtime</span></span>|
|<span data-ttu-id="c8164-116">Etkilenen API'leri</span><span class="sxs-lookup"><span data-stu-id="c8164-116">Affected APIs</span></span>|<ul><li><xref:System.Runtime.Serialization.NetDataContractSerializer.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li></ul>|
