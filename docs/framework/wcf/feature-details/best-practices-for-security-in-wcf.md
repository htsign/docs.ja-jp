---
title: "WCF のセキュリティのベスト プラクティス"
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
helpviewer_keywords: best practices [WCF], security
ms.assetid: 3639de41-1fa7-4875-a1d7-f393e4c8bd69
caps.latest.revision: "19"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 441b3a72d5b0a9e63d6093bc130335801503489e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="best-practices-for-security-in-wcf"></a>WCF のセキュリティのベスト プラクティス
以下のセクションでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] を使用してセキュリティで保護されたアプリケーションを作成する場合に考慮する必要のあるベスト プラクティスを示します。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]セキュリティを参照してください[セキュリティの考慮事項](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)、[データのセキュリティに関する考慮事項](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)、および[メタデータとセキュリティに関する考慮事項](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)です。  
  
## <a name="identify-services-performing-windows-authentication-with-spns"></a>Windows 認証での SPN を使用したサービスの識別  
 サービスはユーザー プリンシパル名 (UPN) またはサービス プリンシパル名 (SPN) によって識別できます。 ネットワーク サービスのようにコンピューター アカウントを使用して実行するサービスには、サービスが実行されるコンピューターに対応する SPN ID があります。 ユーザー アカウントを使用して実行するサービスには、そのユーザーに対応する UPN ID があります。ただし、`setspn` ツールを使用するとユーザー アカウントに SPN 割り当てることができます。 サービスが SPN によって識別されるように構成し、サービスに接続するクライアントが SPN を使用してサービスに接続するように構成すると、攻撃の種類によっては攻撃が困難になります。 このガイダンスは Kerberos または SSPI ネゴシエーションを使用するバインディングに適用されます。  その場合でも、SSPI が使用できなくて NTLM が使用される場合に備えて、クライアントは SPN を指定する必要があります。  
  
## <a name="verify-service-identities-in-wsdl"></a>WSDL でのサービス ID の検証  
 WS-SecurityPolicy ではサービスが自己の ID に関する情報をメタデータの中で公開できるようになっています。 この ID 情報は `svcutil` で取得した場合や <xref:System.ServiceModel.Description.WsdlImporter> などその他の方法で取得した場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービス エンドポイント アドレスの ID プロパティに変換されます。 サービス ID が正しく有効であることを検証しないクライアントは、実質上サービス認証をバイパスすることになります。 悪意を持ったサービスは、資格情報の転送やその他の "man in the middle" 攻撃を実行するために、その WSDL での ID 宣言を変更することによって、このようなクライアントを利用できます。  
  
## <a name="use-x509-certificates-instead-of-ntlm"></a>NTLM の代わりに X509 証明書を使用する  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、ピアツーピア認証用に X509 証明書 (ピア チャネルで使用) と SSPI ネゴシエーションが Kerberos から NTLM にダウングレードされたときに使用される Windows 認証の 2 つのメカニズムが提供されています。  1024 ビット以上のキー サイズを使用する証明書ベースの認証が NTLM より好ましい理由はいくつかあります。  
  
-   相互認証が可能  
  
-   暗号化アルゴリズムの強化  
  
-   転送された X509 資格情報の利用が難しくなる  
  
 転送攻撃 NTLM の概要についてを参照してください[http://msdn.microsoft.com/msdnmag/issues/06/09/SecureByDesign/default.aspx](http://go.microsoft.com/fwlink/?LinkId=109571)です。  
  
## <a name="always-revert-after-impersonation"></a>偽装後は必ず元に戻す  
 クライアントの偽装を有効にする API を使用した後は、必ず元の ID に戻してください。 たとえば、<xref:System.Security.Principal.WindowsIdentity> および <xref:System.Security.Principal.WindowsImpersonationContext> を使用する場合は、次のコードに示すように、C# の `using` ステートメントまたは [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] の `Using` ステートメントを使用します。 <xref:System.Security.Principal.WindowsImpersonationContext> クラスは <xref:System.IDisposable> インターフェイスを実装しているため、コードが `using` ブロックを抜けると共通言語ランタイム (CLR: Common Language Runtime) は自動的に元の ID に戻ります。  
  
 [!code-csharp[c_SecurityBestPractices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securitybestpractices/cs/source.cs#1)]
 [!code-vb[c_SecurityBestPractices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securitybestpractices/vb/source.vb#1)]  
  
## <a name="impersonate-only-as-needed"></a>必要な場合のみ偽装を行う  
 <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> クラスの <xref:System.Security.Principal.WindowsIdentity> メソッドを使用すると、非常に限られたスコープでしか偽装を使用できなくなります。 これは、操作全体のスコープで偽装が許可される <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> の <xref:System.ServiceModel.OperationBehaviorAttribute> プロパティとは対照的です。 可能な限り、<xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> メソッドを使用して偽装のスコープをより厳密に制御します。  
  
## <a name="obtain-metadata-from-trusted-sources"></a>信頼されたソースからメタデータを取得する  
 メタデータのソースが信頼できることと、メタデータが改ざんされていないことを確認します。 HTTP プロトコルを使用して取得したメタデータはクリア テキストで送信されるため、改ざんされるおそれがあります。 サービスが <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> および <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> プロパティを使用している場合は、サービス作成者によって提供された URL を使用して HTTPS プロトコルを介してデータをダウンロードします。  
  
## <a name="publish-metadata-using-security"></a>セキュリティを使用してメタデータを公開する  
 サービスが公開したメタデータの改ざんを防ぐには、トランスポート レベルまたはメッセージ レベルのセキュリティを使用して、メタデータ交換エンドポイントをセキュリティで保護します。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][メタデータ エンドポイントを公開](../../../../docs/framework/wcf/publishing-metadata-endpoints.md)と[する方法: コードを使用して、サービスのメタデータを公開](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)です。  
  
## <a name="ensure-use-of-local-issuer"></a>ローカル発行者の使用を確認する  
 特定のバインディングに対して発行者アドレスとバインディングが指定されている場合、ローカル発行者はこのバインディングを使用するエンドポイントには使用されません。 ローカル発行者を常に使用する必要があるクライアントには、このようなバインディングが使用されることがないか、または発行者アドレスが null となるようにクライアントによってバインディングが変更されることが保証されている必要があります。  
  
## <a name="saml-token-size-quotas"></a>SAML トークン サイズのクォータ  
 セキュリティ トークン サービス (STS: Security Token Service) によって SAML (Security Assertions Markup Language) トークンが発行されたとき、またはクライアントが認証の一部としてこれをサービスに提示したときに、SAML トークンがメッセージ内にシリアル化される場合は、メッセージの最大クォータ サイズが、SAML トークンおよびメッセージの他の部分を格納できるだけの大きさである必要があります。 通常は、既定のメッセージ クォータ サイズで十分です。 ただし、数百のクレームを含んでいるために SAML トークンのサイズが大きい場合には、シリアル化されたトークンを格納できるように、クォータを増やす必要があります。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]クォータを参照してください[データのセキュリティに関する考慮事項](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)です。  
  
## <a name="set-securitybindingelementincludetimestamp-to-true-on-custom-bindings"></a>カスタム バインドで SecurityBindingElement.IncludeTimestamp を true に設定する  
 カスタム バインディングを作成するときは、<xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> を `true` に設定する必要があります。 <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> が `false` に設定されている場合に、クライアントが、X509 証明書などの非対称キーに基づくトークンを使用すると、メッセージは署名されません。  
  
## <a name="see-also"></a>関連項目  
 [セキュリティに関する考慮事項](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [データのセキュリティに関する考慮事項](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)  
 [メタデータとセキュリティに関する考慮事項](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
