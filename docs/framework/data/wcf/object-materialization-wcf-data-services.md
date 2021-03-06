---
title: "オブジェクトの具体化 (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, querying
ms.assetid: f0dbf7b0-0292-4e31-9ae4-b98288336dc1
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a8f20023e158b388ddd71e518ebcaa48c214252c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="object-materialization-wcf-data-services"></a>オブジェクトの具体化 (WCF Data Services)
使用すると、**サービス参照の追加**ダイアログを使用、 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] .NET Framework ベースのクライアント アプリケーションでのフィード、同等のデータ クラスは、生成、フィードによって公開されているデータ モデルの各エンティティの種類。 詳細については、次を参照してください。[データ サービス クライアント ライブラリを生成する](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)です。 クエリによって返されるエンティティ データは、これらの生成されたクライアント データ サービス クラスのいずれかのインスタンスに具体化されます。 マージ オプションおよび追跡されているオブジェクトの id の解決については、次を参照してください。[データ サービス コンテキストを管理する](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)です。  
  
 さらに [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、ツールによって生成されたデータ クラスを使用する代わりに、独自のクライアント データ サービス クラスを定義できます。 これにより、"plain-old CLR object" (POCO) データ クラスとして知られる独自のデータ クラスを使用できます。 これらの種類のカスタム データ クラスを使用する場合は、いずれかでデータ クラスを属性する必要があります<xref:System.Data.Services.Common.DataServiceKeyAttribute>または<xref:System.Data.Services.Common.DataServiceEntityAttribute>型名前でデータ サービスのデータ モデルの型名クライアントと一致していることを確認してください。  
  
 返されたデータを具体化するライブラリは、クエリの応答メッセージを受信した後、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]フィードは、クエリの型のサービス クラスのクライアント データのインスタンスにします。 これらのオブジェクトを具体化する一般的なプロセスは次のとおりです。  
  
1.  クライアント ライブラリは、応答メッセージ フィード内の `entry` 要素からシリアル化された型を読み取り、次のいずれかの方法で正しい型の新しいインスタンスの作成を試みます。  
  
    -   フィードで宣言された型の名前が <xref:System.Data.Services.Client.DataServiceQuery%601> の型と同じ場合は、空のコンストラクターを使用してこの型の新しいインスタンスが作成されます。  
  
    -   フィードで宣言された型の名前が <xref:System.Data.Services.Client.DataServiceQuery%601> の型から派生した型と同じ場合は、空のコンストラクターを使用して派生したこの型の新しいインスタンスが作成されます。  
  
    -   フィードで宣言された型が <xref:System.Data.Services.Client.DataServiceQuery%601> の型、または派生した型と一致しない場合は、空のコンストラクターを使用してクエリされた型の新しいインスタンスが作成されます。  
  
    -   <xref:System.Data.Services.Client.DataServiceContext.ResolveType%2A> プロパティが設定されている場合、指定されたデリゲートが呼び出され、既定の名前ベースの型のマッピングを上書きし、<xref:System.Func%602> によって返された型の新しいインスタンスが代わりに作成されます。 このデリゲートが NULL 値を返した場合、クエリされた型の新しいインスタンスが代わりに作成されます。 継承のシナリオをサポートするために、既定の名前ベースの型名のマッピングを上書きすることが必要な場合があります。  
  
2.  クライアント ライブラリは `id` の `entry` 要素から URI 値を読み取ります。これがエンティティの ID 値です。 <xref:System.Data.Services.Client.DataServiceContext.MergeOption%2A> の  <xref:System.Data.Services.Client.MergeOption.NoTracking> 値が使用されない限り、<xref:System.Data.Services.Client.DataServiceContext> のオブジェクトの追跡には、ID 値が使用されます。 さらに、クエリ応答でエンティティが複数回返されたときでも、単一のエンティティ インスタンスのみが作成されることを保証するためにも ID 値を使用します。  
  
3.  クライアント ライブラリは、フィード エントリからプロパティを読み取り、新しく作成されたオブジェクトに対応するプロパティを設定します。 <xref:System.Data.Services.Client.DataServiceContext> に同じ ID 値のオブジェクトが既に存在する場合、プロパティは、<xref:System.Data.Services.Client.MergeOption> の <xref:System.Data.Services.Client.DataServiceContext> 設定に基づき設定されます。 応答には、クライアント型で対応するプロパティがないプロパティ値が含まれる場合があります。 そのような場合、アクションは、<xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> の <xref:System.Data.Services.Client.DataServiceContext> プロパティの値によって異なります。 このプロパティが `true` に設定されている場合は、欠落しているプロパティは無視されます。 それ以外の場合は、エラーが発生します。 プロパティは次のように設定されます。  
  
    -   スカラー プロパティは、応答メッセージのエントリ内の対応する値に設定されます。  
  
    -   複合プロパティは、新しい複合型インスタンスに設定されます。このインスタンスは、応答からの複合型のプロパティとともに設定されます。  
  
    -   関連するエンティティのコレクションを返すナビゲーション プロパティは、<xref:System.Collections.Generic.ICollection%601> の新しいまたは既存のインスタンスに設定されます。ここで、`T` は関連エンティティの型です。 このコレクションは、関連オブジェクトが <xref:System.Data.Services.Client.DataServiceContext> に読み込まれていない限り空になります。 詳細については、次を参照してください。[遅延コンテンツを読み込んで](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)です。  
  
        > [!NOTE]
        >  生成されたクライアント データ クラスでデータ バインディングがサポートされる場合、ナビゲーション プロパティは代わりに <xref:System.Data.Services.Client.DataServiceCollection%601> クラスのインスタンスを返します。 詳細については、次を参照してください。[コントロールへのデータ バインディング](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)です。  
  
4.  <xref:System.Data.Services.Client.DataServiceContext.ReadingEntity> イベントが発生します。  
  
5.  クライアント ライブラリは <xref:System.Data.Services.Client.DataServiceContext> にオブジェクトをアタッチします。 <xref:System.Data.Services.Client.MergeOption> が <xref:System.Data.Services.Client.MergeOption.NoTracking> の場合は、オブジェクトはアタッチされません。  
  
## <a name="see-also"></a>関連項目  
 [データ サービスに対するクエリ](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
 [クエリの射影](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)
