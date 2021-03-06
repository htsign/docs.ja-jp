---
title: "Windows Communication Foundation とは"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation [WCF], technology overview
- technology overview [WCF]
- WCF [WCF], technology overview
ms.assetid: 40e1009d-ef15-450b-9848-62eabe5e5738
caps.latest.revision: "51"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3a24f1bd921de848cb75a2c9f35fa3dd279bc741
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="what-is-windows-communication-foundation"></a>Windows Communication Foundation とは
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] は、サービス指向アプリケーションを構築するためのフレームワークです。 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]を使用すると、1 つのサービス エンドポイントから別のサービス エンドポイントに非同期メッセージとしてデータを送信できます。 サービス エンドポイントには、IIS でホストされている、継続的に使用可能なサービスの一部を使用したり、アプリケーションでホストされているサービスを使用できます。 エンドポイントには、サービス エンドポイントからデータを要求するサービスのクライアントを使用できます。 メッセージは XML として送信された 1 文字または 1 語の簡単なものでも、バイナリ データのストリームのような複雑なものでも構いません。 サンプル シナリオをいくつか挙げます。  
  
-   ビジネス トランザクションを処理するセキュリティ保護サービス。  
  
-   トラフィック レポートやその他のモニタリング サービスなど、現在のデータを他のサービスに提供するサービス。  
  
-   2 人のユーザーがリアル タイムで通信したりデータを交換したりできるチャット サービス。  
  
-   データの 1 つ以上のサービスをポーリングし、論理プレゼンテーションで表示するダッシュボード アプリケーション。  
  
-   Windows Workflow Foundation を WCF サービスに使用した、実装されたワークフローの公開。  
  
-   最新のデータ フィードのサービスをポーリングする Silverlight アプリケーション。  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]が登場する前もそのようなアプリケーションの作成は可能でしたが、 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] によってエンドポイントの開発が一段と簡単になりました。 要約すると、 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] は Web サービスと Web サービス クライアントを作成するための管理しやすいアプローチを提供するように設計されています。  
  
## <a name="features-of-wcf"></a>WCF の機能  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] には次の機能セットがあります。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [WCF Feature Details](../../../docs/framework/wcf/feature-details/index.md)。  
  
-   **サービス指向**  
  
     WS 標準を使用する結果として、 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] を使用して *サービス指向* アプリケーションを作成できます。 サービス指向アーキテクチャ (SOA) は、データの送受信に Web サービスを使用します。 このサービスを使用する一般的な長所は、1 つのアプリケーションから別のアプリケーションへハードコーディングせずに、疎結合にできるということです。 疎結合リレーションシップでは、必須のコントラクトが一致していれば、任意のプラットフォームで作成した任意のクライアントを任意のサービスに接続できます。  
  
-   **相互運用性**  
  
     [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] は、Web サービスの相互運用性を図るために、最新の業界標準を実装しています。 [!INCLUDE[crabout](../../../includes/crabout-md.md)] については、「 [Interoperability and Integration](../../../docs/framework/wcf/feature-details/interoperability-and-integration.md)。  
  
-   **複数のメッセージ パターン**  
  
     メッセージは複数のパターンの 1 つを使用して交換されます。 最も一般的なパターンは要求/応答パターンです。このパターンでは 1 つのエンドポイントが 2 番目のエンドポイントからデータを要求し、 2 番目のエンドポイントが応答します。 その他にも一方向のメッセージなどのパターンがあります。一方向のメッセージでは、1 つのエンドポイントが応答を期待せずにメッセージを送信します。 より複雑なパターンとして、2 つのエンドポイントが接続を確立し、インスタント メッセージング プログラムのようにデータをやり取りする双方向交換パターンがあります。 [!INCLUDE[crabout](../../../includes/crabout-md.md)] を使用した異なるメッセージ交換パターンの実装方法の [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] については、「 [Contracts](../../../docs/framework/wcf/feature-details/contracts.md)。  
  
-   **サービス メタデータ**  
  
     [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] では、WSDL、XML スキーマ、WS-Policy などの業界標準で指定された形式を使用するサービス メタデータの公開をサポートしています。 このメタデータを使用して、 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスにアクセスするためのクライアントを自動生成および構成できます。 メタデータは HTTP や HTTPS 上で、または Web サービス メタデータ交換標準を使用して公開できます。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Metadata](../../../docs/framework/wcf/feature-details/metadata.md)。  
  
-   **データ コントラクト**  
  
     [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] は [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]を使用して作成されているため、適用するコントラクトを提供するコードフレンドリなメソッドが含まれています。 汎用的な型のコントラクトの 1 つにデータ コントラクトがあります。 本質的に、Visual C# または Visual Basic を使用してサービスをコード化した場合、データを処理する最も簡単な方法は、データ エンティティを表すクラスにデータ エンティティに属するプロパティを作成する方法です。 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] には、このような簡単な方法でデータを使用する包括的なシステムがあります。 データを表すクラスを作成すると、設計したデータ型にクライアントが準拠できるメタデータがサービスによって自動生成されます。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Using Data Contracts](../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
  
-   **セキュリティ**  
  
     メッセージを暗号化してプライバシーを保護し、メッセージを受信する前にユーザーが自身を認証することを必須化することができます。 SSL や WS-SecureConversation などよく知られた標準を使用してセキュリティを実装できます。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [セキュリティ](../../../docs/framework/wcf/feature-details/security.md)。  
  
-   **複数のトランスポートとエンコーディング**  
  
     メッセージは複数の組み込みトランスポート プロトコルおよびエンコーディングのいずれかを使用して送信できます。 最も一般的なプロトコルとエンコーディングは、World Wide Web で HTTP (ハイパーテキスト転送プロトコル) を使用して、テキスト エンコードされた SOAP メッセージを送信するものです。 また、 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] では、TCP、名前付きパイプ、MSMQ でメッセージを送信することもできます。 これらのメッセージはテキストとしてエンコードするか、最適化されたバイナリ形式を使用することができます。  バイナリ データは MTOM 標準を使用することで効率的に送信できます。 提供されているトランスポートまたはエンコーディングのいずれもニーズを満たさない場合は、独自のカスタム トランスポートまたはエンコーディングを作成できます。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]トランスポートとエンコーディングでサポートされている[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]を参照してください[トランスポート](../../../docs/framework/wcf/feature-details/transports.md)です。  
  
-   **キューに置かれた信頼性のあるメッセージ**  
  
     [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] では、WS-Reliable Messaging 経由で MSMQ を使用して実装された、信頼性の高いセッションで信頼性の高いメッセージ交換をサポートしています。 [!INCLUDE[crabout](../../../includes/crabout-md.md)] でサポートされている、キューに置かれた信頼性の高いメッセージングの [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] については、「 [Queues and Reliable Sessions](../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)。  
  
-   **非揮発性メッセージ**  
  
     非揮発性メッセージは、通信の中断によって失われることがないメッセージです。 非揮発性メッセージ パターンのメッセージは常にデータベースに保存されます。 中断が発生した場合、接続復旧時にデータベースでメッセージの交換を再開できます。 [!INCLUDE[wf](../../../includes/wf-md.md)]を使用して非揮発性メッセージを作成することもできます。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Workflow Services](../../../docs/framework/wcf/feature-details/workflow-services.md)。  
  
-   **トランザクション**  
  
     WCF では、WS-AtomicTtransactions、 <xref:System.Transactions> 名前空間の API、および Microsoft 分散トランザクション コーディネーターの 3 つのトランザクション モデルの 1 つを使用したトランザクションもサポートしています。 [!INCLUDE[crabout](../../../includes/crabout-md.md)] でサポートされているトランザクションの [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] については、「 [トランザクション](../../../docs/framework/wcf/feature-details/transactions-in-wcf.md)。  
  
-   **AJAX および REST サポート**  
  
     REST は、進化し続ける Web 2.0 テクノロジの一例です。 SOAP エンベロープにラップされていない "書式なし" XML データを処理するように[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] を構成できます。 また、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] を拡張して、ATOM (一般的な RSS 標準) などの特定の XML 形式や、JSON (JavaScript Object Notation) などの XML 以外の形式をサポートすることもできます。  
  
-   **機能拡張**  
  
     [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] アーキテクチャーには多数の機能拡張ポイントがあります。 追加の機能が必要になった場合、サービスの動作をカスタマイズできる多数のエントリ ポイントがあります。 [!INCLUDE[crabout](../../../includes/crabout-md.md)] については、「 [Extending WCF](../../../docs/framework/wcf/extending/extending-wcf.md)。  
  
## <a name="wcf-integration-with-other-microsoft-technologies"></a>WCF と他のマイクロソフト テクノロジと統合  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] は柔軟性の高いプラットフォームです。 この柔軟性を活かして、 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] は他のいくつかの Microsoft 製品でも使用されています。 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]の基本を理解することで、これらの製品を使用するときにもすぐにこの利点を活用できます。  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] とペアを組んでいる最初のテクノロジは、Windows Workflow Foundation (WF) です。 ワークフロー「アクティビティ」としてワークフローの手順をカプセル化することによってアプリケーションの開発を簡略化します。 [!INCLUDE[wf2](../../../includes/wf2-md.md)]の最初のバージョンでは、開発者がワークフローのホストを作成する必要がありました。 次のバージョンの [!INCLUDE[wf2](../../../includes/wf2-md.md)] は [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]と統合されました。 これにより、任意のワークフローを簡単に [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスでホストできるようになりました。これは [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]で WF/WCF のプロジェクトの種類を自動的に選択して実行できます。  
  
 Microsoft BizTalk Server R2 も [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] を通信テクノロジに使用しています。 BizTalk は、1 つの標準化形式のデータを受け取り、別の形式に変換するように設計されています。 メッセージは、厳密なマッピングか、またはワークフロー エンジンなどの BizTalk 機能の 1 つを使用してメッセージを変換できる、中央管理のメッセージ ボックスに配信する必要があります。 BizTalk では、 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 業務基幹 (LOB) アダプターを使用してメッセージをメッセージ ボックスに配信できます。  
  
 Microsoft Silverlight は開発者がストリーミング ビデオなどメディアを多用する Web サイトを作成できる、相互運用が可能で充実した Web アプリケーションを作成するためのプラットフォームです。 バージョン 2 以降、Silverlight は [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] を通信テクノロジに組み込み、Silverlight アプリケーションを [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] エンドポイントに接続するようになりました。  
  
 [!INCLUDE[dublin](../../../includes/dublin-md.md)] アプリケーション サーバーは、 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] を通信に使用するアプリケーションを配置および管理するために特別に構築されています。 [!INCLUDE[dublin2](../../../includes/dublin2-md.md)] には、 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]対応アプリケーションに合わせて特別に設計された豊富なツールおよび構成オプションが揃っています。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel>  
 [Windows Communication Foundation の基本概念](../../../docs/framework/wcf/fundamental-concepts.md)  
 [Windows Communication Foundation のアーキテクチャ](../../../docs/framework/wcf/architecture.md)  
 [ガイドラインとベスト プラクティス](../../../docs/framework/wcf/guidelines-and-best-practices.md)  
 [チュートリアル入門](../../../docs/framework/wcf/getting-started-tutorial.md)  
 [ドキュメントのガイド](../../../docs/framework/wcf/guide-to-the-documentation.md)  
 [基本的な WCF プログラミング](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Windows Communication Foundation サンプル](http://msdn.microsoft.com/en-us/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)
