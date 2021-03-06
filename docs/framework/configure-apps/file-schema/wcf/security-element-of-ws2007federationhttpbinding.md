---
title: "&lt;ws2007FederationHttpBinding&gt; の &lt;security&gt; 要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 79976b015f35bdd71a5f95a018d85c0ba41ce0b2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecuritygt-element-of-ltws2007federationhttpbindinggt"></a>&lt;ws2007FederationHttpBinding&gt; の &lt;security&gt; 要素
セキュリティ設定を定義、 [ \<ws2007FederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md)要素。  
  
 \<システムです。ServiceModel >  
\<バインド >  
\<ws2007FederationHttpBinding >  
\<バインド >  
\<セキュリティ >  
  
## <a name="syntax"></a>構文  
  
```xml  
<ws2007FederationBinding>  
    <binding >  
        <security mode="None/Message/TransportWithMessageCredential">  
           <message negotiateServiceCredential="Boolean"  
                algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/ Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
                defaultProtectionLevel="none/sign/EncryptAndSign"   
                issuedTokenType="string"   
                issuedKeyType="SymmetricKey/PublicKey"  
           </message>  
        </security>  
    </binding>  
</ws2007FederationBinding>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`mode`|省略可能です。 適用するセキュリティの種類を指定します。 既定値は `Message` です。 この属性は <xref:System.ServiceModel.WSFederationHttpSecurityMode> 型です。|  
  
## <a name="mode-attribute"></a>mode 属性  
  
|値|説明|  
|-----------|-----------------|  
|なし|SOAP メッセージは、転送中はセキュリティで保護されません。|  
|メッセージ|SOAP メッセージ セキュリティを使用して、整合性、機密性、サーバー認証、およびクライアント認証を提供します。 既定では、本文は暗号化および署名されます。 サービスは、証明書を使用して構成する必要があります。 クライアント認証は、セキュリティ トークン サービスによってクライアントに発行されるトークンに基づいています。|  
|TransportWithMessageCredential|整合性、機密性、およびサーバー認証は、HTTPS によって提供されます。 サービスは、証明書を使用して構成する必要があります。 クライアント認証は、SOAP メッセージ セキュリティによって提供され、セキュリティ トークン サービスによってクライアントに発行されるトークンに基づいています。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<メッセージ >](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|メッセージ レベル セキュリティの設定を定義します。 この要素は <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement> 型です。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<バインド >](../../../../../docs/framework/misc/binding.md)|すべてのバインド機能を定義、 [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)です。|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.WSFederationHttpSecurity>  
 <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>  
 [方法: WSFederationHttpBinding を作成します。](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 [サービスとクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [資格情報の種類を選択します。](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [バインディング](../../../../../docs/framework/wcf/bindings.md)  
 [システム指定のバインディングを構成します。](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<バインド >](../../../../../docs/framework/misc/binding.md)
