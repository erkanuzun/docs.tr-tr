### <a name="signedxml-and-encryptedxml-breaking-changes"></a><span data-ttu-id="6aba3-101">SignedXml ve EncryptedXml yeni değişiklikler</span><span class="sxs-lookup"><span data-stu-id="6aba3-101">SignedXml and EncryptedXml Breaking Changes</span></span>

|   |   |
|---|---|
|<span data-ttu-id="6aba3-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="6aba3-102">Details</span></span>|<span data-ttu-id="6aba3-103">.NET Framework 4.6.2, güvenlik giderir <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=name> ve <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=name> farklı çalışma zamanı davranışları sağlama.</span><span class="sxs-lookup"><span data-stu-id="6aba3-103">In .NET Framework 4.6.2, Security fixes in <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=name> and <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=name> lead to different run-time behaviors.</span></span> <span data-ttu-id="6aba3-104">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="6aba3-104">For example,</span></span><ul><li><span data-ttu-id="6aba3-105">Bir belgede aynı birden çok öğe varsa <code>id</code> özniteliği ve imza hedeflediği bu öğelerden birine imza kök olarak belgeyi artık geçersiz olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="6aba3-105">If a document has multiple elements with the same <code>id</code> attribute and a signature targets one of those elements as the root of the signature, the document will now be considered invalid.</span></span></li><li><span data-ttu-id="6aba3-106">Kurallı olmayan XPath dönüştürme algoritmaları başvurularında kullanarak belgeleri artık geçersiz olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="6aba3-106">Documents using non-canonical XPath transform algorithms in references are now considered invalid.</span></span></li><li><span data-ttu-id="6aba3-107">Kurallı olmayan XSLT dönüşümü algoritmaları başvurularında kullanarak belgeleri şimdi dikkat edilmelidir geçersiz.</span><span class="sxs-lookup"><span data-stu-id="6aba3-107">Documents using non-canonical XSLT transform algorithms in references are now consider invalid.</span></span></li><li><span data-ttu-id="6aba3-108">Bunu yapmak dış kaynak ayrılmış imzaları program yapmayı kullanımı yükleyemez.</span><span class="sxs-lookup"><span data-stu-id="6aba3-108">Any program making use of external resource detached signatures will be unable to do so.</span></span></li></ul>|
|<span data-ttu-id="6aba3-109">Öneri</span><span class="sxs-lookup"><span data-stu-id="6aba3-109">Suggestion</span></span>|<span data-ttu-id="6aba3-110">Geliştiriciler kullanımını gözden geçirmek isteyebilirsiniz <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> ve <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform>, yanı sıra türleri türetilmiş <xref:System.Security.Cryptography.Xml.Transform> bu yana bir belge alıcı işlemek olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="6aba3-110">Developers might want to review the usage of <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> and <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform>, as well as types derived from <xref:System.Security.Cryptography.Xml.Transform> since a document receiver may not be able to process it.</span></span>|
|<span data-ttu-id="6aba3-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="6aba3-111">Scope</span></span>|<span data-ttu-id="6aba3-112">Küçük</span><span class="sxs-lookup"><span data-stu-id="6aba3-112">Minor</span></span>|
|<span data-ttu-id="6aba3-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="6aba3-113">Version</span></span>|<span data-ttu-id="6aba3-114">4.6.2</span><span class="sxs-lookup"><span data-stu-id="6aba3-114">4.6.2</span></span>|
|<span data-ttu-id="6aba3-115">Tür</span><span class="sxs-lookup"><span data-stu-id="6aba3-115">Type</span></span>|<span data-ttu-id="6aba3-116">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="6aba3-116">Runtime</span></span>|
|<span data-ttu-id="6aba3-117">Etkilenen API'leri</span><span class="sxs-lookup"><span data-stu-id="6aba3-117">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.Xml.Transform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXPathTransform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform?displayProperty=nameWithType></li></ul>|
