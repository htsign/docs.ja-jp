---
title: "カスタム バインドを使用したセキュリティ機能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 9d252dca363c952dde44b499363e285d4bb7eb82
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="security-capabilities-with-custom-bindings"></a>カスタム バインドを使用したセキュリティ機能
一般的なセキュリティ タスクのほとんどは、システム指定のバインディングのいずれかを使用して実行できます。 ただし、より高度な制御が必要な場合は、以下のトピックで説明するように、<xref:System.ServiceModel.Channels.SecurityBindingElement> を使用してカスタム バインディングを作成できます。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]カスタム バインディングを参照してください[カスタム バインド](../../../../docs/framework/wcf/extending/custom-bindings.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [SecurityBindingElement 認証モード](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 カスタム バインドで使用できる認証モードについて説明します。  
  
 [方法: SecurityBindingElement を使用してカスタム バインディングを作成します。](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 セキュリティ要素を使用してカスタム バインドを作成するための基本手順について説明します。  
  
 [方法: 指定された認証モード用の SecurityBindingElement を作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 指定した認証モード用のセキュリティ要素を作成する方法について説明します。  
  
 [方法: WSFederationHttpBinding 上のセッションが無効にするにセキュリティで保護](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 フェデレーション サービスを作成する際に、セキュリティで保護されたセッションを無効にする方法について説明します。  
  
 [方法: メッセージ リプレイ検出を有効にします。](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 リプレイ攻撃の発生を確認する方法について説明します。  
  
 [方法: サポート資格情報の作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-supporting-credential.md)  
 必要な場合に、サービスにサポート資格情報を提供する方法について説明します。  
  
 [方法: 署名確認を設定](../../../../docs/framework/wcf/feature-details/how-to-set-up-a-signature-confirmation.md)  
 メッセージにデジタル署名する際に署名を確認する手順について説明します。  
  
 [方法: セット最大クロックのずれ](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)  
 サービスとクライアント間で許容される最大の時刻のずれを設定する方法について説明します。  
  
 [方法: デジタル署名の暗号化を無効にします。](../../../../docs/framework/wcf/feature-details/how-to-disable-encryption-of-digital-signatures.md)  
 デジタル署名の暗号化を無効にするとどのようなパフォーマンス上の利点があるかを説明します。  
  
## <a name="reference"></a>参照  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## <a name="related-sections"></a>関連項目  
 [保護レベルの理解](../../../../docs/framework/wcf/understanding-protection-level.md)  
  
 [サービスとクライアントのセキュリティ保護](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
## <a name="see-also"></a>関連項目  
 [バインディングとセキュリティ](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 [セキュリティの概要](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [システム標準のバインディング](../../../../docs/framework/wcf/system-provided-bindings.md)
