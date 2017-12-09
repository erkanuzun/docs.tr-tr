---
title: "Nasıl yapılır: Web Kullanıcılarına Yerelleştirilmiş Tarih ve Saat Bilgilerini Görüntüleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- formatting [.NET Framework], dates
- parsing strings [.NET Framework], date and time strings
- localization [.NET Framework], date and time displays
- formatting [.NET Framework], localized data
- displaying date and time data
- localized date displays [.NET Framework]
ms.assetid: 377fe93c-32be-421a-a30a-be639a46ede8
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 21493e0e0c9e42cf5efc42d86c8f126fbae9b392
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-localized-date-and-time-information-to-web-users"></a><span data-ttu-id="5db32-102">Nasıl yapılır: Web Kullanıcılarına Yerelleştirilmiş Tarih ve Saat Bilgilerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="5db32-102">How to: Display Localized Date and Time Information to Web Users</span></span>
<span data-ttu-id="5db32-103">Bir Web sayfası dünyanın her yerden görüntülenebilir olduğundan, ayrıştırma ve tarih ve saat değerlerini biçimlendirmek işlemleri (genellikle Web sunucusunun yerel kültür biçimi) bir varsayılan biçimi üzerinde güvenmemelisiniz kullanıcıyla kullanılırken.</span><span class="sxs-lookup"><span data-stu-id="5db32-103">Because a Web page can be displayed anywhere in the world, operations that parse and format date and time values should not rely on a default format (which most often is the format of the Web server's local culture) when interacting with the user.</span></span> <span data-ttu-id="5db32-104">Bunun yerine, işleyen tarih ve saat dizeleri giriş kullanıcı tarafından Web forms kullanıcının tercih edilen kültürü kullanarak dizeleri ayrıştırma.</span><span class="sxs-lookup"><span data-stu-id="5db32-104">Instead, Web forms that handle date and time strings input by the user should parse the strings using the user's preferred culture.</span></span> <span data-ttu-id="5db32-105">Benzer şekilde, tarih ve saat verilerini kullanıcıya kullanıcının kültürü için uyumlu bir biçimde görüntülenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5db32-105">Similarly, date and time data should be displayed to the user in a format that conforms to the user's culture.</span></span> <span data-ttu-id="5db32-106">Bu konuda, bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5db32-106">This topic shows how to do this.</span></span>  
  
### <a name="to-parse-date-and-time-strings-input-by-the-user"></a><span data-ttu-id="5db32-107">Tarih ve saat ayrıştırmak için kullanıcı tarafından Giriş dizeleri</span><span class="sxs-lookup"><span data-stu-id="5db32-107">To parse date and time strings input by the user</span></span>  
  
1.  <span data-ttu-id="5db32-108">Dize dizisi tarafından döndürülen olup olmadığını belirlemek <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> özelliği doldurulur.</span><span class="sxs-lookup"><span data-stu-id="5db32-108">Determine whether the string array returned by the <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> property is populated.</span></span> <span data-ttu-id="5db32-109">Değilse, 6. adıma geçin.</span><span class="sxs-lookup"><span data-stu-id="5db32-109">If it is not, continue to step 6.</span></span>  
  
2.  <span data-ttu-id="5db32-110">Dize dizisi olarak döndürülürse <xref:System.Web.HttpRequest.UserLanguages%2A> özelliği doldurulur, ilk alt öğesi alın.</span><span class="sxs-lookup"><span data-stu-id="5db32-110">If the string array returned by the <xref:System.Web.HttpRequest.UserLanguages%2A> property is populated, retrieve its first element.</span></span> <span data-ttu-id="5db32-111">İlk öğesi, kullanıcının varsayılan veya tercih edilen dil ve bölge gösterir.</span><span class="sxs-lookup"><span data-stu-id="5db32-111">The first element indicates the user's default or preferred language and region.</span></span>  
  
3.  <span data-ttu-id="5db32-112">Örneği bir <xref:System.Globalization.CultureInfo> kullanıcıyı temsil eden nesne tercih edilen kültür çağırarak <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="5db32-112">Instantiate a <xref:System.Globalization.CultureInfo> object that represents the user's preferred culture by calling the <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> constructor.</span></span>  
  
4.  <span data-ttu-id="5db32-113">Ya da çağrısı `TryParse` veya `Parse` yöntemi <xref:System.DateTime> veya <xref:System.DateTimeOffset> türüne dönüştürmeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="5db32-113">Call either the `TryParse` or the `Parse` method of the <xref:System.DateTime> or <xref:System.DateTimeOffset> type to try the conversion.</span></span> <span data-ttu-id="5db32-114">Bir aşırı yüklemesini kullanın `TryParse` veya `Parse` yöntemi ile bir `provider` parametresi ve aşağıdakilerden birini geçirin:</span><span class="sxs-lookup"><span data-stu-id="5db32-114">Use an overload of the `TryParse` or the `Parse` method with a `provider` parameter, and pass it either of the following:</span></span>  
  
    -   <span data-ttu-id="5db32-115"><xref:System.Globalization.CultureInfo> 3. adımda oluşturulan nesne.</span><span class="sxs-lookup"><span data-stu-id="5db32-115">The <xref:System.Globalization.CultureInfo> object created in step 3.</span></span>  
  
    -   <span data-ttu-id="5db32-116"><xref:System.Globalization.DateTimeFormatInfo> Tarafından döndürülen nesne <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> özelliği <xref:System.Globalization.CultureInfo> 3. adımda oluşturulan nesne.</span><span class="sxs-lookup"><span data-stu-id="5db32-116">The <xref:System.Globalization.DateTimeFormatInfo> object that is returned by the <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> property of the <xref:System.Globalization.CultureInfo> object created in step 3.</span></span>  
  
5.  <span data-ttu-id="5db32-117">Dönüştürme başarısız olursa, tarafından döndürülen 2 ile 4 dize dizisi kalan her öğe için adımları yineleyin <xref:System.Web.HttpRequest.UserLanguages%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="5db32-117">If the conversion fails, repeat steps 2 through 4 for each remaining element in the string array returned by the <xref:System.Web.HttpRequest.UserLanguages%2A> property.</span></span>  
  
6.  <span data-ttu-id="5db32-118">Dönüştürme yine başarısız olursa veya dize dizisi olarak döndürülürse <xref:System.Web.HttpRequest.UserLanguages%2A> özelliği boşsa, dize sabit kültür tarafından döndürülen kullanarak XML'in <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="5db32-118">If the conversion still fails or if the string array returned by the <xref:System.Web.HttpRequest.UserLanguages%2A> property is empty, parse the string by using the invariant culture, which is returned by the <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> property.</span></span>  
  
### <a name="to-parse-the-local-date-and-time-of-the-users-request"></a><span data-ttu-id="5db32-119">Yerel tarih ve saat kullanıcının isteği ayrıştırılamıyor</span><span class="sxs-lookup"><span data-stu-id="5db32-119">To parse the local date and time of the user's request</span></span>  
  
1.  <span data-ttu-id="5db32-120">Ekleme bir <xref:System.Web.UI.WebControls.HiddenField> Web formu denetimi.</span><span class="sxs-lookup"><span data-stu-id="5db32-120">Add a <xref:System.Web.UI.WebControls.HiddenField> control to a Web form.</span></span>  
  
2.  <span data-ttu-id="5db32-121">İşleme bir JavaScript işlevi oluşturma `onClick` olayı bir `Submit` gelen Eşgüdümlü Evrensel Saat (UTC) için geçerli tarih ve saat ile yerel saat diliminin uzaklığı yazarak düğmesi <xref:System.Web.UI.WebControls.HiddenField.Value%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="5db32-121">Create a JavaScript function that handles the `onClick` event of a `Submit` button by writing the current date and time and the local time zone's offset from Coordinated Universal Time (UTC) to the <xref:System.Web.UI.WebControls.HiddenField.Value%2A> property.</span></span> <span data-ttu-id="5db32-122">Dize, iki bileşeni birbirinden ayırmak için sınırlayıcı (örneğin, noktalı virgül) kullanın.</span><span class="sxs-lookup"><span data-stu-id="5db32-122">Use a delimiter (such as a semicolon) to separate the two components of the string.</span></span>  
  
3.  <span data-ttu-id="5db32-123">Web formun kullanmak <xref:System.Web.UI.Control.PreRender> HTML'e işlevi eklemesine olay çıkış akışı komut dosyasına metin geçirerek <xref:System.Web.UI.ClientScriptManager.RegisterClientScriptBlock%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5db32-123">Use the Web form's <xref:System.Web.UI.Control.PreRender> event to inject the function into the HTML output stream by passing the text of the script to the <xref:System.Web.UI.ClientScriptManager.RegisterClientScriptBlock%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=nameWithType> method.</span></span>  
  
4.  <span data-ttu-id="5db32-124">Olay işleyicisine bağlanmak `Submit` düğmenin `onClick` için JavaScript işlevinin adı sağlayarak olay `OnClientClick` özniteliği `Submit` düğmesi.</span><span class="sxs-lookup"><span data-stu-id="5db32-124">Connect the event handler to the `Submit` button's `onClick` event by providing the name of the JavaScript function to the `OnClientClick` attribute of the `Submit` button.</span></span>  
  
5.  <span data-ttu-id="5db32-125">İçin bir işleyici oluşturmak `Submit` düğmenin <xref:System.Web.UI.WebControls.Button.Click> olay.</span><span class="sxs-lookup"><span data-stu-id="5db32-125">Create a handler for the `Submit` button's <xref:System.Web.UI.WebControls.Button.Click> event.</span></span>  
  
6.  <span data-ttu-id="5db32-126">Olay işleyicisinin dize dizisi tarafından döndürülen olup olmadığını belirlemek <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> özelliği doldurulur.</span><span class="sxs-lookup"><span data-stu-id="5db32-126">In the event handler, determine whether the string array returned by the <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> property is populated.</span></span> <span data-ttu-id="5db32-127">Değilse, 14. adıma geçin.</span><span class="sxs-lookup"><span data-stu-id="5db32-127">If it is not, continue to step 14.</span></span>  
  
7.  <span data-ttu-id="5db32-128">Dize dizisi olarak döndürülürse <xref:System.Web.HttpRequest.UserLanguages%2A> özelliği doldurulur, ilk alt öğesi alın.</span><span class="sxs-lookup"><span data-stu-id="5db32-128">If the string array returned by the <xref:System.Web.HttpRequest.UserLanguages%2A> property is populated, retrieve its first element.</span></span> <span data-ttu-id="5db32-129">İlk öğesi, kullanıcının varsayılan veya tercih edilen dil ve bölge gösterir.</span><span class="sxs-lookup"><span data-stu-id="5db32-129">The first element indicates the user's default or preferred language and region.</span></span>  
  
8.  <span data-ttu-id="5db32-130">Örneği bir <xref:System.Globalization.CultureInfo> kullanıcıyı temsil eden nesne tercih edilen kültür çağırarak <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="5db32-130">Instantiate a <xref:System.Globalization.CultureInfo> object that represents the user's preferred culture by calling the <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> constructor.</span></span>  
  
9. <span data-ttu-id="5db32-131">Atanmış bir dizeyi geçirmek <xref:System.Web.UI.WebControls.HiddenField.Value%2A> özelliğine <xref:System.String.Split%2A> kullanıcının yerel tarih ve saat dize gösterimini ve kullanıcının yerel saat dilimi uzaklığı dize gösterimini ayrı dizi öğeleri depolamak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="5db32-131">Pass the string assigned to the <xref:System.Web.UI.WebControls.HiddenField.Value%2A> property to the <xref:System.String.Split%2A> method to store the string representation of the user's local date and time and the string representation of the user's local time zone offset in separate array elements.</span></span>  
  
10. <span data-ttu-id="5db32-132">Ya da çağrısı <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> veya <xref:System.DateTime.TryParse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%2CSystem.DateTime%40%29?displayProperty=nameWithType> kullanıcının isteğine saat ve tarih biçimine dönüştürecek şekilde bir <xref:System.DateTime> değeri.</span><span class="sxs-lookup"><span data-stu-id="5db32-132">Call either the <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> or <xref:System.DateTime.TryParse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%2CSystem.DateTime%40%29?displayProperty=nameWithType> method to convert the date and time of the user's request to a <xref:System.DateTime> value.</span></span> <span data-ttu-id="5db32-133">Bir yöntemle kullanın bir `provider` parametresi ve aşağıdakilerden birini geçirin:</span><span class="sxs-lookup"><span data-stu-id="5db32-133">Use an overload of the method with a `provider` parameter, and pass it either of the following:</span></span>  
  
    -   <span data-ttu-id="5db32-134"><xref:System.Globalization.CultureInfo> 8. adımda oluşturduğunuz nesne.</span><span class="sxs-lookup"><span data-stu-id="5db32-134">The <xref:System.Globalization.CultureInfo> object created in step 8.</span></span>  
  
    -   <span data-ttu-id="5db32-135"><xref:System.Globalization.DateTimeFormatInfo> Tarafından döndürülen nesne <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> özelliği <xref:System.Globalization.CultureInfo> 8. adımda oluşturduğunuz nesne.</span><span class="sxs-lookup"><span data-stu-id="5db32-135">The <xref:System.Globalization.DateTimeFormatInfo> object that is returned by the <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> property of the <xref:System.Globalization.CultureInfo> object created in step 8.</span></span>  
  
11. <span data-ttu-id="5db32-136">10 adımda ayrıştırma işlemi başarısız olursa, 13. adıma gidin.</span><span class="sxs-lookup"><span data-stu-id="5db32-136">If the parse operation in step 10 fails, go to step 13.</span></span> <span data-ttu-id="5db32-137">Aksi halde çağrı <xref:System.UInt32.Parse%28System.String%29?displayProperty=nameWithType> kullanıcının saat dilimi konumu dize gösterimini bir tamsayıya dönüştürmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="5db32-137">Otherwise, call the <xref:System.UInt32.Parse%28System.String%29?displayProperty=nameWithType> method to convert the string representation of the user's time zone offset to an integer.</span></span>  
  
12. <span data-ttu-id="5db32-138">Örneği bir <xref:System.DateTimeOffset> kullanıcının yerel saat çağırarak temsil eden <xref:System.DateTimeOffset.%23ctor%28System.DateTime%2CSystem.TimeSpan%29?displayProperty=nameWithType> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="5db32-138">Instantiate a <xref:System.DateTimeOffset> that represents the user's local time by calling the <xref:System.DateTimeOffset.%23ctor%28System.DateTime%2CSystem.TimeSpan%29?displayProperty=nameWithType> constructor.</span></span>  
  
13. <span data-ttu-id="5db32-139">10 adımda dönüştürme başarısız olursa, tarafından döndürülen 7 arasındaki adımları ile 12 dize dizisi kalan her öğe için yineleyin <xref:System.Web.HttpRequest.UserLanguages%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="5db32-139">If the conversion in step 10 fails, repeat steps 7 through 12 for each remaining element in the string array returned by the <xref:System.Web.HttpRequest.UserLanguages%2A> property.</span></span>  
  
14. <span data-ttu-id="5db32-140">Dönüştürme yine başarısız olursa veya dize dizisi olarak döndürülürse <xref:System.Web.HttpRequest.UserLanguages%2A> özelliği boşsa, dize sabit kültür tarafından döndürülen kullanarak XML'in <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="5db32-140">If the conversion still fails or if the string array returned by the <xref:System.Web.HttpRequest.UserLanguages%2A> property is empty, parse the string by using the invariant culture, which is returned by the <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="5db32-141">Ardından 7 ile 12 arasında adımları yineleyin.</span><span class="sxs-lookup"><span data-stu-id="5db32-141">Then repeat steps 7 through 12.</span></span>  
  
 <span data-ttu-id="5db32-142">Sonuç bir <xref:System.DateTimeOffset> Web sayfanızın kullanıcı yerel saatini temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="5db32-142">The result is a <xref:System.DateTimeOffset> object that represents the local time of the user of your Web page.</span></span> <span data-ttu-id="5db32-143">Ardından çağırarak eşdeğer UTC belirleyebilirsiniz <xref:System.DateTimeOffset.ToUniversalTime%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5db32-143">You can then determine the equivalent UTC by calling the <xref:System.DateTimeOffset.ToUniversalTime%2A> method.</span></span> <span data-ttu-id="5db32-144">Ayrıca eşdeğer tarih ve saat Web sunucunuzda çağırarak belirleyebilirsiniz <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> yöntemi ve değerini geçirme <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> süresi dönüştürmek için saat dilimi olarak.</span><span class="sxs-lookup"><span data-stu-id="5db32-144">You can also determine the equivalent date and time on your Web server by calling the <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method and passing a value of <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> as the time zone to convert the time to.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5db32-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="5db32-145">Example</span></span>  
 <span data-ttu-id="5db32-146">Aşağıdaki örnek, HTML kaynağını ve bir tarih ve saat değeri giriş için kullanıcıdan bir ASP.NET Web formu kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="5db32-146">The following example contains both the HTML source and the code for an ASP.NET Web form that asks the user to input a date and time value.</span></span> <span data-ttu-id="5db32-147">İstemci tarafı komut dosyası, gizli bir alan için UTC yerel tarih ve saat kullanıcının isteğinin ve kullanıcının saat dilimi uzaklığını hakkında bilgi de yazar.</span><span class="sxs-lookup"><span data-stu-id="5db32-147">A client-side script also writes information on the local date and time of the user's request and the offset of the user's time zone from UTC to a hidden field.</span></span> <span data-ttu-id="5db32-148">Bu bilgiler daha sonra kullanıcının giriş görüntüleyen bir Web sayfası döndürür sunucunun tarafından ayrıştırılır.</span><span class="sxs-lookup"><span data-stu-id="5db32-148">This information is then parsed by the server, which returns a Web page that displays the user's input.</span></span> <span data-ttu-id="5db32-149">Ayrıca kullanıcının isteği kullanıcının yerel saat, saat, sunucu ve UTC kullanılarak saat ve tarihi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5db32-149">It also displays the date and time of the user's request using the user's local time, the time on the server, and UTC.</span></span>  
  
 [!code-aspx-csharp[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/cs/GetDateInfo.aspx#1)]
 [!code-aspx-vb[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/vb/GetDateInfo.aspx#1)]
  
 <span data-ttu-id="5db32-150">İstemci tarafı komut dosyası JavaScript çağrılarını `toLocaleString` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5db32-150">The client-side script calls the JavaScript `toLocaleString` method.</span></span> <span data-ttu-id="5db32-151">Bu sunucu üzerinde başarıyla ayrıştırılması olasılığı daha yüksektir kullanıcının yerel ayarı biçimlendirme kuralları izleyen bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5db32-151">This produces a string that follows the formatting conventions of the user's locale, which is more likely to be successfully parsed on the server.</span></span>  
  
 <span data-ttu-id="5db32-152"><xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> Özelliği bulunan kültür adlarından doldurulur `Accept-Language` bir HTTP isteğine dahil üstbilgileri.</span><span class="sxs-lookup"><span data-stu-id="5db32-152">The <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> property is populated from the culture names that are contained in `Accept-Language` headers included in an HTTP request.</span></span> <span data-ttu-id="5db32-153">Ancak, tüm tarayıcılar dahil `Accept-Language` üstbilgileri kendi isteklerini ve kullanıcılar da bastırmak üstbilgileri tamamen.</span><span class="sxs-lookup"><span data-stu-id="5db32-153">However, not all browsers include `Accept-Language` headers in their requests, and users can also suppress the headers completely.</span></span> <span data-ttu-id="5db32-154">Bu, kullanıcı girişi ayrıştırırken bir geri dönüş kültür sağlamak önemli kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="5db32-154">This makes it important to have a fallback culture when parsing user input.</span></span> <span data-ttu-id="5db32-155">Genellikle geri dönüş tarafından döndürülen sabit kültür kültürdür <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5db32-155">Typically the fallback culture is the invariant culture returned by <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5db32-156">Kullanıcılar ayrıca Internet Explorer kültür adlarıyla kültür adları geçerli olmayabilir olasılığı oluşturan bir metin kutusunda giriş sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5db32-156">Users can also provide Internet Explorer with culture names that they input in a text box, which creates the possibility that the culture names may not be valid.</span></span> <span data-ttu-id="5db32-157">Bu örneği oluşturulurken özel durum işleme kullanmak önemli kılar bir <xref:System.Globalization.CultureInfo> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="5db32-157">This makes it important to use exception handling when instantiating a <xref:System.Globalization.CultureInfo> object.</span></span>  
  
 <span data-ttu-id="5db32-158">Internet Explorer tarafından gönderilen HTTP isteğinden alınırken <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> dizi kullanıcı tercih sırasına göre doldurulur.</span><span class="sxs-lookup"><span data-stu-id="5db32-158">When retrieved from an HTTP request submitted by Internet Explorer, the <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> array is populated in order of user preference.</span></span> <span data-ttu-id="5db32-159">Dizinin ilk öğesi, kullanıcının birincil kültür/bölge adını içerir.</span><span class="sxs-lookup"><span data-stu-id="5db32-159">The first element in the array contains the name of the user's primary culture/region.</span></span> <span data-ttu-id="5db32-160">Dizi ek öğeler içeriyorsa, Internet Explorer bunları rasgele kültür adı noktalı virgülle ayrılmış bir kalite belirticisi atar.</span><span class="sxs-lookup"><span data-stu-id="5db32-160">If the array contains any additional items, Internet Explorer arbitrarily assigns them a quality specifier, which is delimited from the culture name by a semicolon.</span></span> <span data-ttu-id="5db32-161">Örneğin, fr-FR kültür için bir giriş form alabilir `fr-FR;q=0.7`.</span><span class="sxs-lookup"><span data-stu-id="5db32-161">For example, an entry for the fr-FR culture might take the form `fr-FR;q=0.7`.</span></span>  
  
 <span data-ttu-id="5db32-162">Örnek aramalar <xref:System.Globalization.CultureInfo.%23ctor%2A> Oluşturucu kendi `useUserOverride` parametre kümesine `false` yeni <xref:System.Globalization.CultureInfo> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="5db32-162">The example calls the <xref:System.Globalization.CultureInfo.%23ctor%2A> constructor with its `useUserOverride` parameter set to `false` to create a new <xref:System.Globalization.CultureInfo> object.</span></span> <span data-ttu-id="5db32-163">Kültür adı sunucusundaki varsayılan kültür adı ise bu, sağlar yeni <xref:System.Globalization.CultureInfo> sınıfı oluşturucusu tarafından oluşturulan nesne bir kültürün varsayılan ayarları içerir ve sunucunun kullanarak geçersiz kılınmış herhangi bir ayarı yansıtmaz  **Bölge ve Dil Seçenekleri** uygulama.</span><span class="sxs-lookup"><span data-stu-id="5db32-163">This ensures that, if the culture name is the default culture name on the server, the new <xref:System.Globalization.CultureInfo> object created by the class constructor contains a culture's default settings and does not reflect any settings overridden by using the server's **Regional and Language Options** application.</span></span> <span data-ttu-id="5db32-164">Sunucudaki tüm geçersiz kılınmış ayarları değerleri, kullanıcının sistemde yok veya kullanıcının giriş yansıtılması düşüktür.</span><span class="sxs-lookup"><span data-stu-id="5db32-164">The values from any overridden settings on the server are unlikely to exist on the user's system or to be reflected in the user's input.</span></span>  
  
 <span data-ttu-id="5db32-165">Bu örnek bir tarih ve saat (kullanıcı tarafından diğer gizli alan depolanan bir giriş) iki dize sunumu ayrıştırması nedeniyle olası tanımlar <xref:System.Globalization.CultureInfo> önceden gerekebilecek nesneleri.</span><span class="sxs-lookup"><span data-stu-id="5db32-165">Because this example parses two string representations of a date and time (one input by the user, the other stored to the hidden field), it defines the possible <xref:System.Globalization.CultureInfo> objects that may be required in advance.</span></span> <span data-ttu-id="5db32-166">Bir dizi oluşturur <xref:System.Globalization.CultureInfo> tarafından döndürülen öğe sayısından daha büyük bir nesneleri <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="5db32-166">It creates an array of <xref:System.Globalization.CultureInfo> objects that is one greater than the number of elements returned by the <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="5db32-167">Ardından başlatır bir <xref:System.Globalization.CultureInfo> nesne her bir dil/bölge dize için ve ayrıca başlatır bir <xref:System.Globalization.CultureInfo> temsil eden nesnesi <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5db32-167">It then instantiates a <xref:System.Globalization.CultureInfo> object for each language/region string, and also instantiates a <xref:System.Globalization.CultureInfo> object that represents <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="5db32-168">Kodunuzu ya da çağırabilirsiniz <xref:System.DateTime.Parse%2A> veya <xref:System.DateTime.TryParse%2A> kullanıcının dize gösterimini bir tarih ve zaman yöntemi bir <xref:System.DateTime> değeri.</span><span class="sxs-lookup"><span data-stu-id="5db32-168">Your code can call either the <xref:System.DateTime.Parse%2A> or the <xref:System.DateTime.TryParse%2A> method to convert the user's string representation of a date and time to a <xref:System.DateTime> value.</span></span> <span data-ttu-id="5db32-169">Parse yöntemi yinelenen çağrıları için tek bir ayrıştırma işlemi gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="5db32-169">Repeated calls to a parse method may be required for a single parsing operation.</span></span> <span data-ttu-id="5db32-170">Sonuç olarak, <xref:System.DateTime.TryParse%2A> yöntemi olduğundan daha iyi döndürdüğü `false` ayrıştırma işlemi başarısız olursa.</span><span class="sxs-lookup"><span data-stu-id="5db32-170">As a result, the <xref:System.DateTime.TryParse%2A> method is better because it returns `false` if a parse operation fails.</span></span> <span data-ttu-id="5db32-171">Buna karşılık, tarafından oluşturulan yinelenen özel durumları işleme <xref:System.DateTime.Parse%2A> yöntemi, bir Web uygulaması çok pahalı bir teklifinde olabilir.</span><span class="sxs-lookup"><span data-stu-id="5db32-171">In contrast, handling the repeated exceptions that may be thrown by the <xref:System.DateTime.Parse%2A> method can be a very expensive proposition in a Web application.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5db32-172">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="5db32-172">Compiling the Code</span></span>  
 <span data-ttu-id="5db32-173">Kodu derlemek için oluşturma bir [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] bir arka plan kodu olmadan Web sayfası.</span><span class="sxs-lookup"><span data-stu-id="5db32-173">To compile the code, create an [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web page without a code-behind.</span></span> <span data-ttu-id="5db32-174">Böylece tüm var olan kodu yerini örneği Web sayfasına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="5db32-174">Then copy the example into the Web page so that it replaces all the existing code.</span></span> <span data-ttu-id="5db32-175">[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web sayfası aşağıdaki denetimleri içermelidir:</span><span class="sxs-lookup"><span data-stu-id="5db32-175">The [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web page should contain the following controls:</span></span>  
  
-   <span data-ttu-id="5db32-176">A <xref:System.Web.UI.WebControls.Label> kodunda başvurulmuyor denetim.</span><span class="sxs-lookup"><span data-stu-id="5db32-176">A <xref:System.Web.UI.WebControls.Label> control, which is not referenced in code.</span></span> <span data-ttu-id="5db32-177">Ayarlama, <xref:System.Web.UI.WebControls.TextBox.Text%2A> özelliğine "bir sayı girin:".</span><span class="sxs-lookup"><span data-stu-id="5db32-177">Set its <xref:System.Web.UI.WebControls.TextBox.Text%2A> property to "Enter a Number:".</span></span>  
  
-   <span data-ttu-id="5db32-178">A <xref:System.Web.UI.WebControls.TextBox> adlı Denetim `DateString`.</span><span class="sxs-lookup"><span data-stu-id="5db32-178">A <xref:System.Web.UI.WebControls.TextBox> control named `DateString`.</span></span>  
  
-   <span data-ttu-id="5db32-179">A <xref:System.Web.UI.WebControls.Button> adlı Denetim `OKButton`.</span><span class="sxs-lookup"><span data-stu-id="5db32-179">A <xref:System.Web.UI.WebControls.Button> control named `OKButton`.</span></span> <span data-ttu-id="5db32-180">Ayarlama, <xref:System.Web.UI.WebControls.Button.Text%2A> "Tamam" özelliğine.</span><span class="sxs-lookup"><span data-stu-id="5db32-180">Set its <xref:System.Web.UI.WebControls.Button.Text%2A> property to "OK".</span></span>  
  
-   <span data-ttu-id="5db32-181">A <xref:System.Web.UI.WebControls.HiddenField> adlı Denetim `DateInfo`.</span><span class="sxs-lookup"><span data-stu-id="5db32-181">A <xref:System.Web.UI.WebControls.HiddenField> control named `DateInfo`.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="5db32-182">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="5db32-182">.NET Framework Security</span></span>  
 <span data-ttu-id="5db32-183">Bir kullanıcının HTML akışa betik injecting önlemek için kullanıcı girişi hiçbir zaman doğrudan sunucu yanıtta yansıtılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5db32-183">To prevent a user from injecting script into the HTML stream, user input should never be directly echoed back in the server response.</span></span> <span data-ttu-id="5db32-184">Bunun yerine, bunu kullanarak kodlanması gereken <xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5db32-184">Instead, it should be encoded by using the <xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5db32-185">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5db32-185">See Also</span></span>  
 [<span data-ttu-id="5db32-186">Biçimlendirme işlemlerini gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="5db32-186">Performing Formatting Operations</span></span>](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [<span data-ttu-id="5db32-187">Standart tarih ve saat biçim dizeleri</span><span class="sxs-lookup"><span data-stu-id="5db32-187">Standard Date and Time Format Strings</span></span>](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)  
 [<span data-ttu-id="5db32-188">Özel tarih ve saat biçim dizeleri</span><span class="sxs-lookup"><span data-stu-id="5db32-188">Custom Date and Time Format Strings</span></span>](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)  
 [<span data-ttu-id="5db32-189">Tarih ve saat dizelerini ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="5db32-189">Parsing Date and Time Strings</span></span>](../../../docs/standard/base-types/parsing-datetime.md)