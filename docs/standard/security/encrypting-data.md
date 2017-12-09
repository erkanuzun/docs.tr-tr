---
title: "Veri Şifreleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encryption [.NET Framework], symmetric
- symmetric encryption
- cryptography [.NET Framework], asymmetric
- asymmetric encryption
ms.assetid: 7ecce51f-db5f-4bd4-9321-cceb6fcb2a77
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 42409a333623bd4d691084a0bdd2e57f2c3db4f4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="encrypting-data"></a><span data-ttu-id="d98fb-102">Veri Şifreleme</span><span class="sxs-lookup"><span data-stu-id="d98fb-102">Encrypting Data</span></span>
<span data-ttu-id="d98fb-103">Simetrik şifreleme ve asimetrik şifreleme farklı işlemler kullanılarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d98fb-103">Symmetric encryption and asymmetric encryption are performed using different processes.</span></span> <span data-ttu-id="d98fb-104">Simetrik şifreleme akışların gerçekleştirilir ve bu nedenle büyük miktarlarda verinin şifrelemek kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="d98fb-104">Symmetric encryption is performed on streams and is therefore useful to encrypt large amounts of data.</span></span> <span data-ttu-id="d98fb-105">Asimetrik şifreleme küçük bir bayt sayısı üzerinde gerçekleştirilir ve bu nedenle yalnızca küçük miktardaki veriler için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="d98fb-105">Asymmetric encryption is performed on a small number of bytes and is therefore useful only for small amounts of data.</span></span>  
  
## <a name="symmetric-encryption"></a><span data-ttu-id="d98fb-106">Simetrik şifreleme</span><span class="sxs-lookup"><span data-stu-id="d98fb-106">Symmetric Encryption</span></span>  
 <span data-ttu-id="d98fb-107">Yönetilen simetrik şifreleme sınıflarını adlı bir özel akış sınıf ile kullanılan bir <xref:System.Security.Cryptography.CryptoStream> akışa okunan veriler şifreler.</span><span class="sxs-lookup"><span data-stu-id="d98fb-107">The managed symmetric cryptography classes are used with a special stream class called a <xref:System.Security.Cryptography.CryptoStream> that encrypts data read into the stream.</span></span> <span data-ttu-id="d98fb-108">**CryptoStream** sınıfı, yönetilen akış sınıfıyla başlatılır, bir sınıf uygular <xref:System.Security.Cryptography.ICryptoTransform> arabirimi (bir şifreleme algoritması uygulayan bir sınıftan oluşturulan) ve bir <xref:System.Security.Cryptography.CryptoStreamMode> numaralandırma, izin verilen erişim türünü açıklar **CryptoStream**.</span><span class="sxs-lookup"><span data-stu-id="d98fb-108">The **CryptoStream** class is initialized with a managed stream class, a class implements the <xref:System.Security.Cryptography.ICryptoTransform> interface (created from a class that implements a cryptographic algorithm), and a <xref:System.Security.Cryptography.CryptoStreamMode> enumeration that describes the type of access permitted to the **CryptoStream**.</span></span> <span data-ttu-id="d98fb-109">**CryptoStream** türetilen herhangi bir sınıf kullanarak sınıfı başlatılabilir <xref:System.IO.Stream> dahil olmak üzere, sınıf <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, ve <xref:System.Net.Sockets.NetworkStream>.</span><span class="sxs-lookup"><span data-stu-id="d98fb-109">The **CryptoStream** class can be initialized using any class that derives from the <xref:System.IO.Stream> class, including <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, and <xref:System.Net.Sockets.NetworkStream>.</span></span> <span data-ttu-id="d98fb-110">Bu sınıfların kullanarak, simetrik şifreleme akışı nesneleri çeşitli gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d98fb-110">Using these classes, you can perform symmetric encryption on a variety of stream objects.</span></span>  
  
 <span data-ttu-id="d98fb-111">Aşağıdaki örnek yeni bir örneğini oluşturmak nasıl gösterilmektedir <xref:System.Security.Cryptography.RijndaelManaged> Rijndael şifreleme algoritması uygulayan sınıf ve şifreleme gerçekleştirileceği kullanan bir **CryptoStream** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d98fb-111">The following example illustrates how to create a new instance of the <xref:System.Security.Cryptography.RijndaelManaged> class, which implements the Rijndael encryption algorithm, and use it to perform encryption on a **CryptoStream** class.</span></span> <span data-ttu-id="d98fb-112">Bu örnekte, **CryptoStream** adlı bir akış nesnesiyle başlatılmamış `MyStream` yönetilen akış herhangi bir türde olabilir.</span><span class="sxs-lookup"><span data-stu-id="d98fb-112">In this example, the **CryptoStream** is initialized with a stream object called `MyStream` that can be any type of managed stream.</span></span> <span data-ttu-id="d98fb-113">**CreateEncryptor** yönteminden **RijndaelManaged** sınıf anahtarı ve şifreleme için kullanılan IV geçirilir.</span><span class="sxs-lookup"><span data-stu-id="d98fb-113">The **CreateEncryptor** method from the **RijndaelManaged** class is passed the key and IV that are used for encryption.</span></span> <span data-ttu-id="d98fb-114">Bu durumda, varsayılan anahtar ve IV üretilen `RMCrypto` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d98fb-114">In this case, the default key and IV generated from `RMCrypto` are used.</span></span> <span data-ttu-id="d98fb-115">Son olarak, **CryptoStreamMode.Write** , akış yazma erişimi belirtme geçirilir.</span><span class="sxs-lookup"><span data-stu-id="d98fb-115">Finally, the **CryptoStreamMode.Write** is passed, specifying write access to the stream.</span></span>  
  
```vb  
Dim RMCrypto As New RijndaelManaged()  
Dim CryptStream As New CryptoStream(MyStream, RMCrypto.CreateEncryptor(RMCrypto.Key, RMCrypto.IV), CryptoStreamMode.Write)  
```  
  
```csharp  
RijndaelManaged RMCrypto = new RijndaelManaged();  
CryptoStream CryptStream = new CryptoStream(MyStream, RMCrypto.CreateEncryptor(), CryptoStreamMode.Write);  
```  
  
 <span data-ttu-id="d98fb-116">Bu kod, yazılan herhangi bir veri yürütüldükten sonra **CryptoStream** nesne Rijndael algoritması kullanılarak şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="d98fb-116">After this code is executed, any data written to the **CryptoStream** object is encrypted using the Rijndael algorithm.</span></span>  
  
 <span data-ttu-id="d98fb-117">Aşağıdaki örnek bir akış oluşturma, akış şifreleme, akış yazmak ve akış kapatılırken tüm işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d98fb-117">The following example shows the entire process of creating a stream, encrypting the stream, writing to the stream, and closing the stream.</span></span> <span data-ttu-id="d98fb-118">Bu örnek kullanılarak şifrelenmiş bir ağ akış oluşturur **CryptoStream** sınıfı ve **RijndaelManaged** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d98fb-118">This example creates a network stream that is encrypted using the **CryptoStream** class and the **RijndaelManaged** class.</span></span> <span data-ttu-id="d98fb-119">Bir ileti ile şifrelenmiş akışına yazılır <xref:System.IO.StreamWriter> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d98fb-119">A message is written to the encrypted stream with the <xref:System.IO.StreamWriter> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d98fb-120">Bu örnek, bir dosyaya yazmak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d98fb-120">You can also use this example to write to a file.</span></span> <span data-ttu-id="d98fb-121">Bunu yapmak için silme <xref:System.Net.Sockets.TcpClient> başvuru ve değiştirme <xref:System.Net.Sockets.NetworkStream> ile bir <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="d98fb-121">To do that, delete the <xref:System.Net.Sockets.TcpClient> reference and replace the <xref:System.Net.Sockets.NetworkStream> with a <xref:System.IO.FileStream>.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Security.Cryptography  
Imports System.Net.Sockets  
  
Module Module1  
Sub Main()  
   Try  
      'Create a TCP connection to a listening TCP process.  
      'Use "localhost" to specify the current computer or  
      'replace "localhost" with the IP address of the   
      'listening process.   
      Dim TCP As New TcpClient("localhost", 11000)  
  
      'Create a network stream from the TCP connection.   
      Dim NetStream As NetworkStream = TCP.GetStream()  
  
      'Create a new instance of the RijndaelManaged class  
      'and encrypt the stream.  
      Dim RMCrypto As New RijndaelManaged()  
  
            Dim Key As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
            Dim IV As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
  
      'Create a CryptoStream, pass it the NetworkStream, and encrypt   
      'it with the Rijndael class.  
      Dim CryptStream As New CryptoStream(NetStream, RMCrypto.CreateEncryptor(Key, IV), CryptoStreamMode.Write)  
  
      'Create a StreamWriter for easy writing to the   
      'network stream.  
      Dim SWriter As New StreamWriter(CryptStream)  
  
      'Write to the stream.  
      SWriter.WriteLine("Hello World!")  
  
      'Inform the user that the message was written  
      'to the stream.  
      Console.WriteLine("The message was sent.")  
  
      'Close all the connections.  
      SWriter.Close()  
      CryptStream.Close()  
      NetStream.Close()  
      TCP.Close()  
   Catch  
      'Inform the user that an exception was raised.  
      Console.WriteLine("The connection failed.")  
   End Try  
End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Security.Cryptography;  
using System.Net.Sockets;  
  
public class main  
{  
   public static void Main(string[] args)  
   {  
      try  
      {  
         //Create a TCP connection to a listening TCP process.  
         //Use "localhost" to specify the current computer or  
         //replace "localhost" with the IP address of the   
         //listening process.    
         TcpClient TCP = new TcpClient("localhost",11000);  
  
         //Create a network stream from the TCP connection.   
         NetworkStream NetStream = TCP.GetStream();  
  
         //Create a new instance of the RijndaelManaged class  
         // and encrypt the stream.  
         RijndaelManaged RMCrypto = new RijndaelManaged();  
  
         byte[] Key = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
         byte[] IV = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
  
         //Create a CryptoStream, pass it the NetworkStream, and encrypt   
         //it with the Rijndael class.  
         CryptoStream CryptStream = new CryptoStream(NetStream,   
         RMCrypto.CreateEncryptor(Key, IV),     
         CryptoStreamMode.Write);  
  
         //Create a StreamWriter for easy writing to the   
         //network stream.  
         StreamWriter SWriter = new StreamWriter(CryptStream);  
  
         //Write to the stream.  
         SWriter.WriteLine("Hello World!");  
  
         //Inform the user that the message was written  
         //to the stream.  
         Console.WriteLine("The message was sent.");  
  
         //Close all the connections.  
         SWriter.Close();  
         CryptStream.Close();  
         NetStream.Close();  
         TCP.Close();  
      }  
      catch  
      {  
         //Inform the user that an exception was raised.  
         Console.WriteLine("The connection failed.");  
      }  
   }  
}  
```  
  
 <span data-ttu-id="d98fb-122">Önceki örneğin başarıyla yürütmek için koyulmalıdır IP adresini dinlemesini bir işlem ve bağlantı noktası numarası belirtilen <xref:System.Net.Sockets.TcpClient> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d98fb-122">For the previous example to execute successfully, there must be a process listening on the IP address and port number specified in the <xref:System.Net.Sockets.TcpClient> class.</span></span> <span data-ttu-id="d98fb-123">Dinleme işlemi varsa, kodu dinleme işlemi bağlanmak, Rijndael Simetrik algoritma kullanarak akış şifrelemek ve "Hello World!" yazma</span><span class="sxs-lookup"><span data-stu-id="d98fb-123">If a listening process exists, the code will connect to the listening process, encrypt the stream using the Rijndael symmetric algorithm, and write "Hello World!"</span></span> <span data-ttu-id="d98fb-124">Akış.</span><span class="sxs-lookup"><span data-stu-id="d98fb-124">to the stream.</span></span> <span data-ttu-id="d98fb-125">Kod başarılı olursa, aşağıdaki metni konsola görüntüler:</span><span class="sxs-lookup"><span data-stu-id="d98fb-125">If the code is successful, it displays the following text to the console:</span></span>  
  
```  
The message was sent.  
```  
  
 <span data-ttu-id="d98fb-126">Ancak, hiçbir dinleme işlem bulunamadı veya özel durum oluşturuldu, kod, aşağıdaki metni konsola'e görüntüler:</span><span class="sxs-lookup"><span data-stu-id="d98fb-126">However, if no listening process is found or an exception is raised, the code displays the following text to the console:</span></span>  
  
```  
The connection failed.  
```  
  
## <a name="asymmetric-encryption"></a><span data-ttu-id="d98fb-127">Asimetrik şifreleme</span><span class="sxs-lookup"><span data-stu-id="d98fb-127">Asymmetric Encryption</span></span>  
 <span data-ttu-id="d98fb-128">Asimetrik algoritmalar genellikle küçük miktarda bir simetrik anahtar ve IV şifreleme gibi verileri şifrelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d98fb-128">Asymmetric algorithms are usually used to encrypt small amounts of data such as the encryption of a symmetric key and IV.</span></span> <span data-ttu-id="d98fb-129">Genellikle, bir tek tek gerçekleştirme asimetrik şifreleme başka bir taraf tarafından oluşturulan ortak anahtarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="d98fb-129">Typically, an individual performing asymmetric encryption uses the public key generated by another party.</span></span> <span data-ttu-id="d98fb-130"><xref:System.Security.Cryptography.RSACryptoServiceProvider> Sınıfı bu amaç için .NET Framework tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="d98fb-130">The <xref:System.Security.Cryptography.RSACryptoServiceProvider> class is provided by the .NET Framework for this purpose.</span></span>  
  
 <span data-ttu-id="d98fb-131">Aşağıdaki örnek, bir simetrik anahtar ve IV şifrelemek için ortak anahtar bilgileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="d98fb-131">The following example uses public key information to encrypt a symmetric key and IV.</span></span> <span data-ttu-id="d98fb-132">İki bayt dizileri bir üçüncü taraf ortak anahtarını temsil eden başlatılır.</span><span class="sxs-lookup"><span data-stu-id="d98fb-132">Two byte arrays are initialized that represent the public key of a third party.</span></span> <span data-ttu-id="d98fb-133">Bir <xref:System.Security.Cryptography.RSAParameters> nesnesi, bu değerleri başlatılır.</span><span class="sxs-lookup"><span data-stu-id="d98fb-133">An <xref:System.Security.Cryptography.RSAParameters> object is initialized to these values.</span></span> <span data-ttu-id="d98fb-134">Ardından, **RSAParameters** nesne (birlikte ortak anahtarı temsil eder) içine aktarılır bir **RSACryptoServiceProvider** kullanarak <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d98fb-134">Next, the **RSAParameters** object (along with the public key it represents) is imported into an **RSACryptoServiceProvider** using the <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d98fb-135">Son olarak, özel anahtarı IV tarafından oluşturulan ve bir <xref:System.Security.Cryptography.RijndaelManaged> sınıfı şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="d98fb-135">Finally, the private key and IV created by a <xref:System.Security.Cryptography.RijndaelManaged> class are encrypted.</span></span> <span data-ttu-id="d98fb-136">Bu örnek, sistemleri 128 bit şifreleme yüklü olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d98fb-136">This example requires systems to have 128-bit encryption installed.</span></span>  
  
```vb  
Imports System  
Imports System.Security.Cryptography  
  
Module Module1  
  
    Sub Main()  
        'Initialize the byte arrays to the public key information.  
      Dim PublicKey As Byte() =  {214, 46, 220, 83, 160, 73, 40, 39, 201, 155, 19,202, 3, 11, 191, 178, 56, 74, 90, 36, 248, 103, 18, 144, 170, 163, 145, 87, 54, 61, 34, 220, 222, 207, 137, 149, 173, 14, 92, 120, 206, 222, 158, 28, 40, 24, 30, 16, 175, 108, 128, 35, 230, 118, 40, 121, 113, 125, 216, 130, 11, 24, 90, 48, 194, 240, 105, 44, 76, 34, 57, 249, 228, 125, 80, 38, 9, 136, 29, 117, 207, 139, 168, 181, 85, 137, 126, 10, 126, 242, 120, 247, 121, 8, 100, 12, 201, 171, 38, 226, 193, 180, 190, 117, 177, 87, 143, 242, 213, 11, 44, 180, 113, 93, 106, 99, 179, 68, 175, 211, 164, 116, 64, 148, 226, 254, 172, 147}  
  
        Dim Exponent As Byte() = {1, 0, 1}  
  
        'Create values to store encrypted symmetric keys.  
        Dim EncryptedSymmetricKey() As Byte  
        Dim EncryptedSymmetricIV() As Byte  
  
        'Create a new instance of the RSACryptoServiceProvider class.  
        Dim RSA As New RSACryptoServiceProvider()  
  
        'Create a new instance of the RSAParameters structure.  
        Dim RSAKeyInfo As New RSAParameters()  
  
        'Set RSAKeyInfo to the public key values.   
        RSAKeyInfo.Modulus = PublicKey  
        RSAKeyInfo.Exponent = Exponent  
  
        'Import key parameters into RSA.  
        RSA.ImportParameters(RSAKeyInfo)  
  
        'Create a new instance of the RijndaelManaged class.  
        Dim RM As New RijndaelManaged()  
  
        'Encrypt the symmetric key and IV.  
        EncryptedSymmetricKey = RSA.Encrypt(RM.Key, False)  
        EncryptedSymmetricIV = RSA.Encrypt(RM.IV, False)  
    End Sub  
  
End Module  
```  
  
```csharp  
using System;  
using System.Security.Cryptography;  
  
class Class1  
{  
   static void Main()  
   {  
      //Initialize the byte arrays to the public key information.  
      byte[] PublicKey = {214,46,220,83,160,73,40,39,201,155,19,202,3,11,191,178,56,  
            74,90,36,248,103,18,144,170,163,145,87,54,61,34,220,222,  
            207,137,149,173,14,92,120,206,222,158,28,40,24,30,16,175,  
            108,128,35,230,118,40,121,113,125,216,130,11,24,90,48,194,  
            240,105,44,76,34,57,249,228,125,80,38,9,136,29,117,207,139,  
            168,181,85,137,126,10,126,242,120,247,121,8,100,12,201,171,  
            38,226,193,180,190,117,177,87,143,242,213,11,44,180,113,93,  
            106,99,179,68,175,211,164,116,64,148,226,254,172,147};  
  
      byte[] Exponent = {1,0,1};  
  
      //Create values to store encrypted symmetric keys.  
      byte[] EncryptedSymmetricKey;  
      byte[] EncryptedSymmetricIV;  
  
      //Create a new instance of the RSACryptoServiceProvider class.  
      RSACryptoServiceProvider RSA = new RSACryptoServiceProvider();  
  
      //Create a new instance of the RSAParameters structure.  
      RSAParameters RSAKeyInfo = new RSAParameters();  
  
      //Set RSAKeyInfo to the public key values.   
      RSAKeyInfo.Modulus = PublicKey;  
      RSAKeyInfo.Exponent = Exponent;  
  
      //Import key parameters into RSA.  
      RSA.ImportParameters(RSAKeyInfo);  
  
      //Create a new instance of the RijndaelManaged class.  
      RijndaelManaged RM = new RijndaelManaged();  
  
      //Encrypt the symmetric key and IV.  
      EncryptedSymmetricKey = RSA.Encrypt(RM.Key, false);  
      EncryptedSymmetricIV = RSA.Encrypt(RM.IV, false);  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d98fb-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d98fb-137">See Also</span></span>  
 [<span data-ttu-id="d98fb-138">Şifreleme ve şifre çözme için anahtarlar oluşturma</span><span class="sxs-lookup"><span data-stu-id="d98fb-138">Generating Keys for Encryption and Decryption</span></span>](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)  
 [<span data-ttu-id="d98fb-139">Verilerin şifresini çözme</span><span class="sxs-lookup"><span data-stu-id="d98fb-139">Decrypting Data</span></span>](../../../docs/standard/security/decrypting-data.md)  
 [<span data-ttu-id="d98fb-140">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="d98fb-140">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)