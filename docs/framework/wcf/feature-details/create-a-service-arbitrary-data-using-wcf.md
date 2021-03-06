---
title: 'Como: criar um serviço que aceita dados arbitrários usando o modelo de programação WCF REST'
ms.date: 03/30/2017
ms.assetid: e566c15a-b600-4e4a-be3a-4af43e767dae
ms.openlocfilehash: a1c30491f6c5b0a91f93a6f26417f9dc2b996a48
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614789"
---
# <a name="how-to-create-a-service-that-accepts-arbitrary-data-using-the-wcf-rest-programming-model"></a>Como: criar um serviço que aceita dados arbitrários usando o modelo de programação WCF REST
Às vezes, os desenvolvedores devem ter controle total sobre como os dados são retornados de uma operação de serviço. Esse é o caso quando uma operação de serviço deve retornar dados em um formato não tem suporte byWCF. Este tópico discute usando o modelo de programação WCF REST para criar um serviço que recebe dados arbitrários.  
  
### <a name="to-implement-the-service-contract"></a>Para implementar o contrato de serviço  
  
1. Defina o contrato de serviço. A operação que recebe os dados arbitrários deve ter um parâmetro de tipo <xref:System.IO.Stream>. Além disso, esse parâmetro deve ser o único parâmetro passado no corpo da solicitação. A operação descrita neste exemplo também usa um parâmetro de nome de arquivo. Este parâmetro é passado na URL da solicitação. Você pode especificar que um parâmetro é passado na URL, especificando um <xref:System.UriTemplate> no <xref:System.ServiceModel.Web.WebInvokeAttribute>. Nesse caso, que o URI usado para chamar esse método termina em "UploadFile/alguns-nome do arquivo". A parte "{filename}" do modelo de URI especifica que o parâmetro de nome de arquivo para a operação é passado no URI usado para chamar a operação.  
  
    ```csharp  
     [ServiceContract]  
    public interface IReceiveData  
    {  
        [WebInvoke(UriTemplate = "UploadFile/{fileName}")]  
        void UploadFile(string fileName, Stream fileContents);  
    }  
    ```  
  
2. Implemente o contrato de serviço. O contrato tem apenas um método, `UploadFile` que recebe um arquivo de dados arbitrários em um fluxo. A operação lê o fluxo de contagem do número de bytes lidos e, em seguida, exibe o nome do arquivo e o número de bytes lidos.  
  
    ```csharp  
    public class RawDataService : IReceiveData  
    {  
        public void UploadFile(string fileName, Stream fileContents)  
        {  
            byte[] buffer = new byte[10000];  
            int bytesRead, totalBytesRead = 0;  
            do  
            {  
                bytesRead = fileContents.Read(buffer, 0, buffer.Length);  
                totalBytesRead += bytesRead;  
            } while (bytesRead > 0);  
            Console.WriteLine("Service: Received file {0} with {1} bytes", fileName, totalBytesRead);  
        }  
    }  
    ```  
  
### <a name="to-host-the-service"></a>Para hospedar o serviço  
  
1. Crie um aplicativo de console para hospedar o serviço.  
  
    ```csharp  
    class Program  
    {  
       static void Main(string[] args)  
       {  
       }  
    }  
    ```  
  
2. Crie uma variável para manter o endereço básico para o serviço dentro de `Main` método.  
  
    ```csharp  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3. Criar um <xref:System.ServiceModel.ServiceHost> instância para o serviço que especifica a classe de serviço e o endereço básico.  
  
    ```csharp  
    ServiceHost host = new ServiceHost(typeof(RawDataService), new Uri(baseAddress));  
    ```  
  
4. Adicionar um ponto de extremidade que especifica o contrato <xref:System.ServiceModel.WebHttpBinding>, e <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IReceiveData), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5. Abra o host do serviço. O serviço agora está pronto para receber solicitações.  
  
    ```csharp  
    host.Open();  
    Console.WriteLine("Host opened");  
    ```  
  
### <a name="to-call-the-service-programmatically"></a>Para chamar o serviço de forma programática  
  
1. Criar um <xref:System.Net.HttpWebRequest> com o URI usado para chamar o serviço. Nesse código, o endereço base é combinado com `"/UploadFile/Text"`. O `"UploadFile"` parte do URI especifica a operação para chamar. O `"Test.txt"` parte do URI especifica o parâmetro de nome de arquivo para passar para o `UploadFile` operação. Ambos esses itens do mapa para o <xref:System.UriTemplate> aplicados ao contrato de operação.  
  
    ```csharp  
    HttpWebRequest req = (HttpWebRequest)HttpWebRequest.Create(baseAddress + "/UploadFile/Test.txt");  
    ```  
  
2. Defina a <xref:System.Net.HttpWebRequest.Method%2A> propriedade do <xref:System.Net.HttpWebRequest> para `POST` e o <xref:System.Net.HttpWebRequest.ContentType%2A> propriedade para `"text/plain"`. Isso instrui o serviço que o código está enviando dados e são de que os dados em texto sem formatação.  
  
    ```csharp  
    req.Method = "POST";  
    req.ContentType = "text/plain";  
    ```  
  
3. Chamar <xref:System.Net.HttpWebRequest.GetRequestStream%2A> para obter o fluxo da solicitação, crie os dados para enviar, gravar dados no fluxo de solicitação e feche o fluxo.  
  
    ```csharp  
    Stream reqStream = req.GetRequestStream();  
    byte[] fileToSend = new byte[12345];  
    for (int i = 0; i < fileToSend.Length; i++)  
       {  
           fileToSend[i] = (byte)('a' + (i % 26));  
       }  
    reqStream.Write(fileToSend, 0, fileToSend.Length);  
    reqStream.Close();  
    ```  
  
4. Obter a resposta do serviço chamando <xref:System.Net.HttpWebRequest.GetResponse%2A> e exibir os dados de resposta para o console.  
  
    ```csharp  
    HttpWebResponse resp = (HttpWebResponse)req.GetResponse();  
    Console.WriteLine("Client: Receive Response HTTP/{0} {1} {2}", resp.ProtocolVersion, (int)resp.StatusCode, resp.StatusDescription);  
    ```  
  
5. Feche o host de serviço.  
  
    ```csharp  
    host.Close();  
    ```  
  
## <a name="example"></a>Exemplo  
 A seguir está uma listagem completa do código para este exemplo.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.ServiceModel;  
using System.ServiceModel.Web;  
using System.ServiceModel.Description;  
using System.IO;  
using System.Net;  
  
namespace ReceiveRawData  
{  
    [ServiceContract]  
    public interface IReceiveData  
    {  
        [WebInvoke(UriTemplate = "UploadFile/{fileName}")]  
        void UploadFile(string fileName, Stream fileContents);  
    }  
    public class RawDataService : IReceiveData  
    {  
        public void UploadFile(string fileName, Stream fileContents)  
        {  
            byte[] buffer = new byte[10000];  
            int bytesRead, totalBytesRead = 0;  
            do  
            {  
                bytesRead = fileContents.Read(buffer, 0, buffer.Length);  
                totalBytesRead += bytesRead;  
            } while (bytesRead > 0);  
            Console.WriteLine("Service: Received file {0} with {1} bytes", fileName, totalBytesRead);  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
            ServiceHost host = new ServiceHost(typeof(RawDataService), new Uri(baseAddress));  
            host.AddServiceEndpoint(typeof(IReceiveData), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
            host.Open();  
            Console.WriteLine("Host opened");  
  
            HttpWebRequest req = (HttpWebRequest)HttpWebRequest.Create(baseAddress + "/UploadFile/Test.txt");  
            req.Method = "POST";  
            req.ContentType = "text/plain";  
            Stream reqStream = req.GetRequestStream();  
            byte[] fileToSend = new byte[12345];  
            for (int i = 0; i < fileToSend.Length; i++)  
            {  
                fileToSend[i] = (byte)('a' + (i % 26));  
            }  
            reqStream.Write(fileToSend, 0, fileToSend.Length);  
            reqStream.Close();  
            HttpWebResponse resp = (HttpWebResponse)req.GetResponse();  
            Console.WriteLine("Client: Receive Response HTTP/{0} {1} {2}", resp.ProtocolVersion, (int)resp.StatusCode, resp.StatusDescription);  
            host.Close();  
  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
- Ao compilar o ServiceModel e referência de código de ServiceModel  
  
## <a name="see-also"></a>Consulte também

- [UriTemplate e UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)
- [Modelo de programação HTTP Web do WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [Visão geral do modelo de programação HTTP Web do WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
