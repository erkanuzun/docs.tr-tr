---
title: "Özel WSDL Yayımı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b3e8103-2c95-4db3-a05b-46aa8e9d4d29
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 07c4b4c24d6a5e075f342b186a8123a3e0f19119
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="custom-wsdl-publication"></a><span data-ttu-id="c1995-102">Özel WSDL Yayımı</span><span class="sxs-lookup"><span data-stu-id="c1995-102">Custom WSDL Publication</span></span>
<span data-ttu-id="c1995-103">Bu örnek gösterilmektedir nasıl yapılır:</span><span class="sxs-lookup"><span data-stu-id="c1995-103">This sample demonstrates how to:</span></span>  
  
-   <span data-ttu-id="c1995-104">Uygulama bir <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> özel üzerinde <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> öznitelik özelliklerini WSDL ek açıklama olarak dışa aktarmak için öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c1995-104">Implement a <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> on a custom <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> attribute to export attribute properties as WSDL annotations.</span></span>  
  
-   <span data-ttu-id="c1995-105">Uygulama <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> özel WSDL ek açıklamaları içeri aktarmak için.</span><span class="sxs-lookup"><span data-stu-id="c1995-105">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> to import the custom WSDL annotations.</span></span>  
  
-   <span data-ttu-id="c1995-106">Uygulama <xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType> ve <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType> üzerinde özel ve bir özel işlem davranışlarını sırasıyla alınan sözleşme ve işlem için CodeDom açıklamaları olarak içeri aktarılan ek açıklamaları yazmak için sözleşme.</span><span class="sxs-lookup"><span data-stu-id="c1995-106">Implement <xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType> and <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType> on a custom contract behavior and a custom operation behavior, respectively, to write imported annotations as comments in the CodeDom for the imported contract and operation.</span></span>  
  
-   <span data-ttu-id="c1995-107">Kullanım <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> WSDL indirmek için bir <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> özel WSDL içeri Aktarıcı kullanarak WSDL içe aktarmak için ve <xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType> oluşturmak için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] / / / olarak istemci kodu WSDL ek açıklamalar ile ve ''' C# ve Visual Basic açıklamaları.</span><span class="sxs-lookup"><span data-stu-id="c1995-107">Use the <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> to download the WSDL, a <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> to import the WSDL using the custom WSDL importer, and the <xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType> to generate [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client code with the WSDL annotations as /// and ''' comments in C# and Visual Basic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1995-108">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="c1995-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="c1995-109">Hizmet</span><span class="sxs-lookup"><span data-stu-id="c1995-109">Service</span></span>  
 <span data-ttu-id="c1995-110">Bu örnek hizmetinde iki özel özniteliklerle işaretlenmiş.</span><span class="sxs-lookup"><span data-stu-id="c1995-110">The service in this sample is marked with two custom attributes.</span></span> <span data-ttu-id="c1995-111">İlk `WsdlDocumentationAttribute`, oluşturucuda bir dizesini kabul eder ve bir sözleşme arabirimi veya kullanım tanımlayan bir dize işlemiyle sağlamak için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="c1995-111">The first, the `WsdlDocumentationAttribute`, accepts a string in the constructor and can be applied to provide a contract interface or operation with a string that describes its usage.</span></span> <span data-ttu-id="c1995-112">İkinci `WsdlParamOrReturnDocumentationAttribute`, değerler döndürürse veya bu değerleri işlemde açıklamak için parametreleri uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="c1995-112">The second, `WsdlParamOrReturnDocumentationAttribute`, can be applied to return values or parameters to describe those values in the operation.</span></span> <span data-ttu-id="c1995-113">Aşağıdaki örnek, bir hizmet sözleşmesini gösterir `ICalculator`, açıklanan bu öznitelikleri kullanma.</span><span class="sxs-lookup"><span data-stu-id="c1995-113">The following example shows a service contract, `ICalculator`, described using these attributes.</span></span>  
  
```  
// Define a service contract.      
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
// Document it.  
[WsdlDocumentation("The ICalculator contract performs basic calculation services.")]  
public interface ICalculator  
{  
    [OperationContract]  
    [WsdlDocumentation("The Add operation adds two numbers and returns the result.")]  
    [return:WsdlParamOrReturnDocumentation("The result of adding the two arguments together.")]  
    double Add(  
      [WsdlParamOrReturnDocumentation("The first value to add.")]double n1,   
      [WsdlParamOrReturnDocumentation("The second value to add.")]double n2  
    );  
  
    [OperationContract]  
    [WsdlDocumentation("The Subtract operation subtracts the second argument from the first.")]  
    [return:WsdlParamOrReturnDocumentation("The result of the second argument subtracted from the first.")]  
    double Subtract(  
      [WsdlParamOrReturnDocumentation("The value from which the second is subtracted.")]double n1,   
      [WsdlParamOrReturnDocumentation("The value that is subtracted from the first.")]double n2  
    );  
  
    [OperationContract]  
    [WsdlDocumentation("The Multiply operation multiplies two values.")]  
    [return:WsdlParamOrReturnDocumentation("The result of multiplying the first and second arguments.")]  
    double Multiply(  
      [WsdlParamOrReturnDocumentation("The first value to multiply.")]double n1,   
      [WsdlParamOrReturnDocumentation("The second value to multiply.")]double n2  
    );  
  
    [OperationContract]  
    [WsdlDocumentation("The Divide operation returns the value of the first argument divided by the second argument.")]  
    [return:WsdlParamOrReturnDocumentation("The result of dividing the first argument by the second.")]  
    double Divide(  
      [WsdlParamOrReturnDocumentation("The numerator.")]double n1,   
      [WsdlParamOrReturnDocumentation("The denominator.")]double n2  
    );  
}  
```  
  
 <span data-ttu-id="c1995-114">`WsdlDocumentationAttribute` Uygulayan <xref:System.ServiceModel.Description.IContractBehavior> ve <xref:System.ServiceModel.Description.IOperationBehavior>, karşılık gelen öznitelik örnekleri eklenen <xref:System.ServiceModel.Description.ContractDescription> veya <xref:System.ServiceModel.Description.OperationDescription> hizmet açıldığında.</span><span class="sxs-lookup"><span data-stu-id="c1995-114">The `WsdlDocumentationAttribute` implements <xref:System.ServiceModel.Description.IContractBehavior> and <xref:System.ServiceModel.Description.IOperationBehavior>, so the attribute instances are added to the corresponding <xref:System.ServiceModel.Description.ContractDescription> or <xref:System.ServiceModel.Description.OperationDescription> when the service is opened.</span></span> <span data-ttu-id="c1995-115">İmplements özniteliği de <xref:System.ServiceModel.Description.IWsdlExportExtension>.</span><span class="sxs-lookup"><span data-stu-id="c1995-115">The attribute also implements <xref:System.ServiceModel.Description.IWsdlExportExtension>.</span></span> <span data-ttu-id="c1995-116">Zaman <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> olarak adlandırılır, <xref:System.ServiceModel.Description.WsdlExporter> meta verilerini dışa aktarmak için kullanılır ve <xref:System.ServiceModel.Description.WsdlContractConversionContext> nesneler geçirilir dışarı aktarılan meta veri değişikliği etkinleştirme parametre olarak hizmet açıklaması içerir.</span><span class="sxs-lookup"><span data-stu-id="c1995-116">When <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> is called, the <xref:System.ServiceModel.Description.WsdlExporter> that is used to export the metadata and the <xref:System.ServiceModel.Description.WsdlContractConversionContext> that contains the service description objects are passed in as parameters enabling the modification of the exported metadata.</span></span>  
  
 <span data-ttu-id="c1995-117">Dışarı aktarma bağlam nesnesi olup bağlı bağlı olarak, bu örnekteki bir <xref:System.ServiceModel.Description.ContractDescription> veya bir <xref:System.ServiceModel.Description.OperationDescription>, bir açıklama metin özelliğini kullanarak özniteliğinden ayıklanmış ve WSDL ek açıklama öğesi için aşağıdaki kodda gösterildiği gibi eklenir.</span><span class="sxs-lookup"><span data-stu-id="c1995-117">In this sample, depending upon whether the export context object has a <xref:System.ServiceModel.Description.ContractDescription> or an <xref:System.ServiceModel.Description.OperationDescription>, a comment is extracted from the attribute using the text property and is added to the WSDL annotation element as shown in the following code.</span></span>  
  
```  
public void ExportContract(WsdlExporter exporter, WsdlContractConversionContext context)  
{  
    if (contractDescription != null)  
    {  
        // Inside this block it is the contract-level comment attribute.  
        // This.Text returns the string for the contract attribute.  
        // Set the doc element; if this isn't done first, there is no XmlElement in the   
        // DocumentElement property.  
        context.WsdlPortType.Documentation = string.Empty;  
        // Contract comments.  
        XmlDocument owner = context.WsdlPortType.DocumentationElement.OwnerDocument;  
        XmlElement summaryElement = owner.CreateElement("summary");  
        summaryElement.InnerText = this.Text;  
        context.WsdlPortType.DocumentationElement.AppendChild(summaryElement);  
    }  
    else  
    {  
        Operation operation = context.GetOperation(operationDescription);  
        if (operation != null)  
        {  
            // We are dealing strictly with the operation here.  
            // This.Text returns the string for the operation-level attributes.  
            // Set the doc element; if this isn't done first, there is no XmlElement in the   
            // DocumentElement property.  
            operation.Documentation = String.Empty;  
  
            // Operation C# triple comments.  
            XmlDocument owner = operation.DocumentationElement.OwnerDocument;  
            XmlElement newSummaryElement = owner.CreateElement("summary");  
            newSummaryElement.InnerText = this.Text;  
            operation.DocumentationElement.AppendChild(newSummaryElement);  
```  
  
 <span data-ttu-id="c1995-118">Bir işlem dışa aktardıysanız, örnek yansıma herhangi elde etmek için kullanır. `WsdlParamOrReturnDocumentationAttribute` parametreler ve dönüş değerleri için değerleri ve bunları bu işlem için WSDL ek açıklama öğeleri gibi ekler.</span><span class="sxs-lookup"><span data-stu-id="c1995-118">If an operation is being exported, the sample uses reflection to obtain any `WsdlParamOrReturnDocumentationAttribute` values for parameters and return values and adds them to the WSDL annotation elements for that operation as follows.</span></span>  
  
```  
// Get returns information  
ParameterInfo returnValue = operationDescription.SyncMethod.ReturnParameter;  
object[] returnAttrs = returnValue.GetCustomAttributes(typeof(WsdlParamOrReturnDocumentationAttribute), false);  
if (returnAttrs.Length != 0)  
{  
    // <returns>text.</returns>  
    XmlElement returnsElement = owner.CreateElement("returns");  
    returnsElement.InnerText = ((WsdlParamOrReturnDocumentationAttribute)returnAttrs[0]).ParamComment;  
    operation.DocumentationElement.AppendChild(returnsElement);  
}  
  
// Get parameter information.  
ParameterInfo[] args = operationDescription.SyncMethod.GetParameters();  
for (int i = 0; i < args.Length; i++)  
{  
    object[] docAttrs = args[i].GetCustomAttributes(typeof(WsdlParamOrReturnDocumentationAttribute), false);  
    if (docAttrs.Length == 1)  
    {  
        // <param name="Int1">Text.</param>  
        XmlElement newParamElement = owner.CreateElement("param");  
        XmlAttribute paramName = owner.CreateAttribute("name");  
        paramName.Value = args[i].Name;  
        newParamElement.InnerText = ((WsdlParamOrReturnDocumentationAttribute)docAttrs[0]).ParamComment;  
        newParamElement.Attributes.Append(paramName);  
        operation.DocumentationElement.AppendChild(newParamElement);  
    }  
}  
```  
  
 <span data-ttu-id="c1995-119">Örnek, ardından aşağıdaki yapılandırma dosyası kullanarak standart şekilde meta verileri yayımlar.</span><span class="sxs-lookup"><span data-stu-id="c1995-119">The sample then publishes metadata in the standard way, using the following configuration file.</span></span>  
  
```xml  
<services>  
  <service   
      name="Microsoft.ServiceModel.Samples.CalculatorService"  
      behaviorConfiguration="CalculatorServiceBehavior">  
    <!-- ICalculator is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc  -->  
    <endpoint address=""  
              binding="wsHttpBinding"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    <!-- the mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->  
    <endpoint address="mex"  
              binding="mexHttpBinding"  
              contract="IMetadataExchange" />  
  </service>  
</services>  
  
<!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="svcutil-client"></a><span data-ttu-id="c1995-120">Svcutil istemci</span><span class="sxs-lookup"><span data-stu-id="c1995-120">Svcutil client</span></span>  
 <span data-ttu-id="c1995-121">Bu örnek Svcutil.exe kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="c1995-121">This sample does not use Svcutil.exe.</span></span> <span data-ttu-id="c1995-122">Sözleşme generatedClient.cs örnek sonra gösterir şekilde özel WSDL içe aktarma ve kod oluşturma, hizmet dosya çağrılabilir sağlanır.</span><span class="sxs-lookup"><span data-stu-id="c1995-122">The contract is provided in the generatedClient.cs file so that after the sample demonstrates custom WSDL import and code generation, the service can be invoked.</span></span> <span data-ttu-id="c1995-123">Bu örnek için aşağıdaki özel WSDL alma aracını kullanmak için Svcutil.exe çalıştırın ve belirtin `/svcutilConfig` başvuruyor Bu örnekte kullanılan istemci yapılandırma dosyasının yolu vermiş seçeneği `WsdlDocumentation.dll` kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="c1995-123">To use the following custom WSDL importer for this example, you can run Svcutil.exe and specify the `/svcutilConfig` option, giving the path to the client configuration file used in this sample, which references the `WsdlDocumentation.dll` library.</span></span> <span data-ttu-id="c1995-124">Yüklemek için `WsdlDocumentationImporter`, ancak Svuctil.exe bulun ve yükleyemediğini olmalıdır `WsdlDocumentation.dll` kitaplığı, ya da genel derleme önbelleğinde yolu kayıtlı ya da Svcutil.exe ile aynı dizinde olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c1995-124">To load the `WsdlDocumentationImporter`, however, Svuctil.exe must be able to locate and load the `WsdlDocumentation.dll` library, which means either that it is registered in the global assembly cache, in the path, or is in the same directory as Svcutil.exe.</span></span> <span data-ttu-id="c1995-125">Bu gibi temel bir örnek için yapmak için kolay Svcutil.exe ve istemci yapılandırma dosyası ile aynı dizinde içine kopyalamak için şeydir `WsdlDocumentation.dll` ve oradan çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c1995-125">For a basic sample such as this, the easiest thing to do is to copy Svcutil.exe and the client configuration file into the same directory as `WsdlDocumentation.dll` and run it from there.</span></span>  
  
## <a name="the-custom-wsdl-importer"></a><span data-ttu-id="c1995-126">Özel WSDL içeri Aktarıcı</span><span class="sxs-lookup"><span data-stu-id="c1995-126">The Custom WSDL Importer</span></span>  
 <span data-ttu-id="c1995-127">Özel <xref:System.ServiceModel.Description.IWsdlImportExtension> nesne `WsdlDocumentationImporter` de uygulayan <xref:System.ServiceModel.Description.IContractBehavior> ve <xref:System.ServiceModel.Description.IOperationBehavior> için içe aktarılan ServiceEndpoints öğelerinin eklenecek ve <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> ve <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> kod oluşturma değiştirmek için çağrılacak zaman sözleşme veya işlem kod oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="c1995-127">The custom <xref:System.ServiceModel.Description.IWsdlImportExtension> object `WsdlDocumentationImporter` also implements <xref:System.ServiceModel.Description.IContractBehavior> and <xref:System.ServiceModel.Description.IOperationBehavior> to be added to the imported ServiceEndpoints and <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> and <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> to be invoked to modify the code generation when the contract or operation code is being created.</span></span>  
  
 <span data-ttu-id="c1995-128">İlk olarak <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> yöntemi, örnek WSDL ek açıklama sözleşme veya işlem düzeyinde ve kendisi bir davranış içeri aktarılan ek açıklama metni kendi oluşturucusuna geçirerek uygun kapsamındaki olarak ekler olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="c1995-128">First, in the <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> method, the sample determines whether the WSDL annotation is at the contract or operation level, and adds itself as a behavior at the appropriate scope, passing the imported annotation text to its constructor.</span></span>  
  
```  
public void ImportContract(WsdlImporter importer, WsdlContractConversionContext context)  
{  
    // Contract Documentation  
    if (context.WsdlPortType.Documentation != null)  
    {  
        // System examines the contract behaviors to see whether any implement IWsdlImportExtension.  
        context.Contract.Behaviors.Add(new WsdlDocumentationImporter(context.WsdlPortType.Documentation));  
    }  
    // Operation Documentation  
    foreach (Operation operation in context.WsdlPortType.Operations)  
    {  
        if (operation.Documentation != null)  
        {  
            OperationDescription operationDescription = context.Contract.Operations.Find(operation.Name);  
            if (operationDescription != null)  
            {  
                // System examines the operation behaviors to see whether any implement IWsdlImportExtension.  
                operationDescription.Behaviors.Add(new WsdlDocumentationImporter(operation.Documentation));  
            }  
        }  
    }  
}  
```  
  
 <span data-ttu-id="c1995-129">Ardından, kodu oluşturulduğunda Sistem çağırır <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> ve <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29> uygun bağlam bilgilerini geçirme yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="c1995-129">Then, when the code is generated, the system invokes the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> and <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29> methods, passing the appropriate context information.</span></span> <span data-ttu-id="c1995-130">Örnek özel WSDL ek açıklamaları biçimlendirir ve bunları CodeDom yorum olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="c1995-130">The sample formats the custom WSDL annotations and inserts them as comments into the CodeDom.</span></span>  
  
```  
public void GenerateContract(ServiceContractGenerationContext context)  
{  
    Debug.WriteLine("In generate contract.");  
    context.ContractType.Comments.AddRange(FormatComments(text));  
}  
  
public void GenerateOperation(OperationContractGenerationContext context)  
{  
    context.SyncMethod.Comments.AddRange(FormatComments(text));  
    Debug.WriteLine("In generate operation.");  
}  
```  
  
## <a name="the-client-application"></a><span data-ttu-id="c1995-131">İstemci uygulaması</span><span class="sxs-lookup"><span data-stu-id="c1995-131">The Client Application</span></span>  
 <span data-ttu-id="c1995-132">İstemci uygulama, uygulama yapılandırma dosyasında belirterek özel WSDL içeri Aktarıcı yükler.</span><span class="sxs-lookup"><span data-stu-id="c1995-132">The client application loads the custom WSDL importer by specifying it in the application configuration file.</span></span>  
  
```xml  
<client>  
  <endpoint address="http://localhost/servicemodelsamples/service.svc"   
  binding="wsHttpBinding"   
  contract="ICalculator" />  
  <metadata>  
    <wsdlImporters>  
      <extension type="Microsoft.ServiceModel.Samples.WsdlDocumentationImporter, WsdlDocumentation"/>  
    </wsdlImporters>  
  </metadata>  
</client>  
```  
  
 <span data-ttu-id="c1995-133">Özel içeri Aktarıcı belirtilen sonra [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] meta veri sistemini yükleyen özel içeri Aktarıcı hiçbir <xref:System.ServiceModel.Description.WsdlImporter> bu amaçla oluşturulmuş.</span><span class="sxs-lookup"><span data-stu-id="c1995-133">Once the custom importer has been specified, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] metadata system loads the custom importer into any <xref:System.ServiceModel.Description.WsdlImporter> created for that purpose.</span></span> <span data-ttu-id="c1995-134">Bu örnekte <xref:System.ServiceModel.Description.MetadataExchangeClient> meta veri indirmek için <xref:System.ServiceModel.Description.WsdlImporter> bir örnek oluşturur, özel içeri Aktarıcı kullanarak meta verileri almak için düzgün şekilde yapılandırılmış ve <xref:System.ServiceModel.Description.ServiceContractGenerator> hem Visual Basic değiştirilmiş sözleşme bilgileri derlemek için ve IntelliSense desteklemek için Visual Studio'da kullanılan veya XML belgeleri derlenmiş C# istemci kodu.</span><span class="sxs-lookup"><span data-stu-id="c1995-134">This sample uses the <xref:System.ServiceModel.Description.MetadataExchangeClient> to download the metadata, the <xref:System.ServiceModel.Description.WsdlImporter> properly configured to import the metadata using the custom importer the sample creates, and the <xref:System.ServiceModel.Description.ServiceContractGenerator> to compile the modified contract information into both Visual Basic and C# client code that can be used in Visual Studio to support Intellisense or compiled into XML documentation.</span></span>  
  
```  
/// From WSDL Documentation:  
///   
/// <summary>The ICalculator contract performs basic calculation   
/// services.</summary>   
///   
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://Microsoft.ServiceModel.Samples", ConfigurationName="ICalculator")]  
public interface ICalculator  
{  
  
    /// From WSDL Documentation:  
    ///   
    /// <summary>The Add operation adds two numbers and returns the   
    /// result.</summary><returns>The result of adding the two arguments   
    /// together.</returns><param name="n1">The first value to add.</param><param   
    /// name="n2">The second value to add.</param>   
    ///   
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Add", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/AddResponse")]  
    double Add(double n1, double n2);  
  
    /// From WSDL Documentation:  
    ///   
    /// <summary>The Subtract operation subtracts the second argument from the   
    /// first.</summary><returns>The result of the second argument subtracted from the   
    /// first.</returns><param name="n1">The value from which the second is   
    /// subtracted.</param><param name="n2">The value that is subtracted from the   
    /// first.</param>   
    ///   
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Subtract", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/SubtractResponse")]  
    double Subtract(double n1, double n2);  
  
    /// From WSDL Documentation:  
    ///   
    /// <summary>The Multiply operation multiplies two values.</summary><returns>The   
    /// result of multiplying the first and second arguments.</returns><param   
    /// name="n1">The first value to multiply.</param><param name="n2">The second value   
    /// to multiply.</param>   
    ///   
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Multiply", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/MultiplyResponse")]  
    double Multiply(double n1, double n2);  
  
    /// From WSDL Documentation:  
    ///   
    /// <summary>The Divide operation returns the value of the first argument divided   
    /// by the second argument.</summary><returns>The result of dividing the first   
    /// argument by the second.</returns><param name="n1">The numerator.</param><param   
    /// name="n2">The denominator.</param>   
    ///   
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Divide", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/DivideResponse")]  
    double Divide(double n1, double n2);  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c1995-135">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="c1995-135">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c1995-136">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c1995-136">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="c1995-137">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c1995-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="c1995-138">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c1995-138">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c1995-139">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="c1995-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c1995-140">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c1995-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c1995-141">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="c1995-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c1995-142">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="c1995-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\WsdlDocumentation`  
  
## <a name="see-also"></a><span data-ttu-id="c1995-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c1995-143">See Also</span></span>