---
title: "方法 : クライアントの資格情報の値を指定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 42c6390fb2bd39a0003beecbbe10cd72a38ed63d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-specify-client-credential-values"></a>方法 : クライアントの資格情報の値を指定する
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] では、サービスに対するクライアントの認証方法を指定できます。 たとえば、証明書を使用してクライアントを認証するように指定できます。  
  
### <a name="to-determine-the-client-credential-type"></a>クライアント資格情報の種類を特定するには  
  
1.  サービスのメタデータ エンドポイントからメタデータを取得します。 一般的に、メタデータは、選択したプログラミング言語 (既定は Visual C#) のクライアント コードおよび XML 構成ファイルという 2 つのファイルで構成されています。 メタデータは、クライアント コードおよびクライアント構成を返す Svcutil.exe ツールを使用して取得できます。 詳細については、次を参照してください。[メタデータを取得する](../../../docs/framework/wcf/feature-details/retrieving-metadata.md)と[ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)です。  
  
2.  XML 構成ファイルを開きます。 Svcutil.exe ツールを使用する場合、ファイルの既定の名前は、Output.config です。  
  
3.  検索、 **\<セキュリティ >**を持つ要素、**モード**属性 (**< セキュリティ モード =** `MessageOrTransport`  **>** 場所`MessageOrTransport`セキュリティ モードのいずれかに設定されています。  
  
4.  mode 値に一致する子要素を見つけます。 モードが に設定されている場合など、**メッセージ**、検索、 **\<メッセージ >**要素に含まれている、 **\<セキュリティ >**要素。  
  
5.  割り当てられた値に注意してください、 **clientCredentialType**属性。 実際の値は、使用されているモード (トランスポートまたはメッセージ) に依存します。  
  
 次の XML コードは、メッセージ セキュリティを使用し、クライアントの認証に証明書を要求するクライアントの構成を示します。  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows" proxyCredentialType="None"  
        realm="" />  
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"  
    algorithmSuite="Default" establishSecurityContext="true" />  
</security>  
```  
  
## <a name="example-tcp-transport-mode-with-certificate-as-client-credential"></a>例: クライアント資格情報としての証明書による TCP トランスポート モード  
 この例では、セキュリティ モードを "Transport (トランスポート)" モードに設定し、クライアント資格情報の値を X.509 証明書に設定します。 次の手順では、クライアントでクライアント資格情報の値をコードと構成を使用して設定する方法を示します。 これを使用している前提としています。、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)をサービスからメタデータ (コードと構成) を返します。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][する方法: クライアントを作成する](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)です。  
  
#### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a>クライアントでクライアント資格情報の値をコードによって指定するには  
  
1.  使用して、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)サービスからコードと構成を生成します。  
  
2.  生成されたコードを使用して、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアントのインスタンスを作成します。  
  
3.  クライアント クラスで、<xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> クラスの <xref:System.ServiceModel.ClientBase%601> プロパティを適切な値に設定します。 この例では、<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> クラスの <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> メソッドを使用して、このプロパティを X.509 証明書に設定します。  
  
     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]  
  
     <xref:System.Security.Cryptography.X509Certificates.X509FindType> クラスの任意の列挙体を使用できます。 ここでは、有効期限が切れて証明書が変更された場合に備えて、サブジェクト名を使用しています。 サブジェクト名を使用することにより、インフラストラクチャは証明書を再検索できます。  
  
#### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a>クライアントでクライアント資格情報の値を構成によって指定するには  
  
1.  追加、 [\<動作 >](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)要素を[\<動作 >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)要素。  
  
2.  追加、 [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)要素を[\<動作 >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)要素。 `name` 属性 (必須) を適切な値に必ず設定してください。  
  
3.  追加、 [ \<clientCertificate >](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)要素を[ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)要素。  
  
4.  次のコードに示すように、`storeLocation`、`storeName`、`x509FindType`、および `findValue` の各属性を適切な値に設定します。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]証明書を参照してください[証明書の使用](../../../docs/framework/wcf/feature-details/working-with-certificates.md)です。  
  
    ```xml  
    <behaviors>  
       <endpointBehaviors>  
          <behavior name="endpointCredentialBehavior">  
            <clientCredentials>  
              <clientCertificate findValue="Contoso.com"   
                                 storeLocation="LocalMachine"  
                                 storeName="TrustedPeople"  
                                 x509FindType="FindBySubjectName" />  
            </clientCredentials>  
          </behavior>  
       </endpointBehaviors>  
    </behaviors>  
    ```  
  
5.  クライアントを構成するときは、次のコードに示すように、`behaviorConfiguration` 要素の `<endpoint>` 属性を設定して動作を指定します。 エンドポイント要素の子である、 [\<クライアント >](../../../docs/framework/configure-apps/file-schema/wcf/client.md)要素。 また、`bindingConfiguration` 属性をクライアントのバインディングに設定することにより、バインディング構成の名前を指定します。 生成された構成ファイルを使用している場合は、バインディングの名前は自動的に生成されます。 この例では、名前は `"tcpBindingWithCredential"` です。  
  
    ```xml  
    <client>  
      <endpoint name =""  
                address="net.tcp://contoso.com:8036/aloha"  
                binding="netTcpBinding"  
                bindingConfiguration="tcpBindingWithCredential"  
                behaviorConfiguration="endpointCredentialBehavior" />  
    </client>  
    ```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.NetTcpBinding>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>  
 <xref:System.ServiceModel.ClientBase%601>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>  
 [WCF セキュリティのプログラミング](../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 [資格情報の種類を選択します。](../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [証明書の使用](../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [方法: クライアントを作成する](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [\<netTcpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)  
 [\<セキュリティ >](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)  
 [\<メッセージ >](../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)  
 [\<動作 >](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)  
 [\<ビヘイビアー >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
 [\<clientCertificate >](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)  
 [\<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)
