---
title: "リフレクション プロバイダー (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF Data Services, プロバイダー"
ms.assetid: ef5ba300-6d7c-455e-a7bd-d0cc6d211ad4
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# リフレクション プロバイダー (WCF Data Services)
Entity Framework を介してデータ モデルからデータを公開することに加えて、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、エンティティ ベースのモデルで厳密に定義されていないデータを公開することもできます。  リフレクション プロバイダーは、<xref:System.Linq.IQueryable%601> インターフェイスを実装する型を返すクラスのデータを公開します。  [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] は、リフレクションを使用して、これらのクラスのデータ モデルを推論し、リソースに対するアドレス ベースのクエリを、公開されている <xref:System.Linq.IQueryable%601> 型に対する統合言語クエリ \(LINQ\) ベースのクエリに変換します。  
  
> [!NOTE]
>  <xref:System.Linq.Queryable.AsQueryable%2A> メソッドを使用して、<xref:System.Collections.Generic.IEnumerable%601> インターフェイスを実装する任意のクラスから <xref:System.Linq.IQueryable%601> インターフェイスを返すことができます。  これによって、ほとんどのジェネリック コレクション型をデータ サービスのデータ ソースとして使用することが可能になります。  
  
 リフレクション プロバイダーは、型の階層をサポートします。  詳細については、「[方法: リフレクション プロバイダーを使用してデータ サービスを作成する](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)」を参照してください。  
  
## データ モデルの推論  
 データ サービスを作成すると、プロバイダーはリフレクションを使用してデータ モデルを推論します。  リフレクション プロバイダーがデータ モデルを推論する方法を次の一覧に示します。  
  
-   エンティティ コンテナー – <xref:System.Linq.IQueryable%601> インターフェイスを返すプロパティとしてデータを公開するクラス。  リフレクション ベースのデータ モデルを作成すると、エンティティ コンテナーはサービスのルートを表します。  1 つの名前空間でサポートされるエンティティ コンテナー クラスは 1 つだけです。  
  
-   エンティティ セット \- <xref:System.Linq.IQueryable%601> インスタンスを返すプロパティはエンティティ セットとして処理されます。  エンティティ セットは、クエリでリソースとして直接アドレス指定されます。  エンティティ コンテナーの 1 つのプロパティが返すことができるのは、1 つの型の <xref:System.Linq.IQueryable%601> インスタンスだけです。  
  
-   エンティティ型 – エンティティ セットが返す <xref:System.Linq.IQueryable%601> の `T` 型。  継承階層の一部であるクラスは、リフレクション プロバイダーによって同等のエンティティ型階層に変換されます。  
  
-   エンティティ キー – エンティティ型である各データ クラスには 1 つのキー プロパティが必要です。  このプロパティは、<xref:System.Data.Services.Common.DataServiceKeyAttribute> 属性 \(`[DataServiceKeyAttribute]`\) で属性化されています。  
  
    > [!NOTE]
    >  <xref:System.Data.Services.Common.DataServiceKeyAttribute> 属性は、エンティティ型のインスタンスを一意に識別するために使用できるプロパティのみに適用してください。  ナビゲーション プロパティに適用すると、この属性は無視されます。  
  
-   エンティティ型プロパティ – リフレクション プロバイダーは、エンティティ キー以外で、次に示すエンティティ型のクラスのアクセス可能な非インデクサー プロパティを処理します。  
  
    -   プロパティがプリミティブ型を返す場合、プロパティはエンティティ型のプロパティと見なされます。  
  
    -   プロパティがエンティティ型でもある型を返す場合、プロパティは、多対一または一対一のリレーションシップの "一" の側を表すナビゲーション プロパティと見なされます。  
  
    -   プロパティがエンティティ型の <xref:System.Collections.Generic.IEnumerable%601> を返す場合、プロパティは、一対多または多対多のリレーションシップの "多" の側を表すナビゲーション プロパティと見なされます。  
  
    -   プロパティの戻り値の型が値型である場合、プロパティは複合型を表します。  
  
> [!NOTE]
>  エンティティ リレーショナル モデルに基づくデータ モデルとは異なり、リフレクション プロバイダーに基づくモデルではリレーショナル データは理解されません。  Entity Framework を使用して、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 経由でリレーショナル データを公開する必要があります。  
  
## データ型のマッピング  
 データ モデルが .NET Framework クラスから推論されると、次に示すようにデータ モデルのプリミティブ型が .NET Framework データ型にマップされます。  
  
|.NET Framework データ型|データ モデル型|  
|-------------------------|--------------|  
|<xref:System.Byte> `[]`|`Edm.Binary`|  
|<xref:System.Boolean>|`Edm.Boolean`|  
|<xref:System.Byte>|`Edm.Byte`|  
|<xref:System.DateTime>|`Edm.DateTime`|  
|<xref:System.Decimal>|`Edm.Decimal`|  
|<xref:System.Double>|`Edm.Double`|  
|<xref:System.Guid>|`Edm.Guid`|  
|<xref:System.Int16>|`Edm.Int16`|  
|<xref:System.Int32>|`Edm.Int32`|  
|<xref:System.Int64>|`Edm.Int64`|  
|<xref:System.SByte>|`Edm.SByte`|  
|<xref:System.Single>|`Edm.Single`|  
|<xref:System.String>|`Edm.String`|  
  
> [!NOTE]
>  .NET Framework の NULL 許容値型は、対応する値型で NULL を指定できないものと同じデータ モデル型にマップされます。  
  
## データ モデルでの更新の有効化  
 この種類のデータ モデルを介して公開されるデータを更新するために、リフレクション プロバイダーは、<xref:System.Data.Services.IUpdatable> インターフェイスを定義します。  このインターフェイスは、公開されている型への更新を保存する方法をデータ サービスに指示します。  データ モデルによって定義されているリソースへの更新を有効にするには、エンティティ コンテナー クラスは、<xref:System.Data.Services.IUpdatable> インターフェイスを実装する必要があります。  <xref:System.Data.Services.IUpdatable> インターフェイスの実装例については、「[方法: LINQ to SQL データ ソースを使用してデータ サービスを作成する](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)」を参照してください。  
  
 リフレクション プロバイダーを使用してデータ ソースに更新を伝達するには、<xref:System.Data.Services.IUpdatable> インターフェイスに次のメンバーが実装されている必要があります。  
  
|メンバー|説明|  
|----------|--------|  
|<xref:System.Data.Services.IUpdatable.AddReferenceToCollection%2A>|ナビゲーション プロパティからアクセスされる関連オブジェクトのコレクションにオブジェクトを追加する機能を提供します。|  
|<xref:System.Data.Services.IUpdatable.ClearChanges%2A>|データに対する保留中の変更を取り消す機能を提供します。|  
|<xref:System.Data.Services.IUpdatable.CreateResource%2A>|指定したコンテナーに新しいリソースを作成する機能を提供します。|  
|<xref:System.Data.Services.IUpdatable.DeleteResource%2A>|リソースを削除する機能を提供します。|  
|<xref:System.Data.Services.IUpdatable.GetResource%2A>|特定のクエリおよび型名によって識別されるリソースを取得する機能を提供します。|  
|<xref:System.Data.Services.IUpdatable.GetValue%2A>|リソースのプロパティの値を返す機能を提供します。|  
|<xref:System.Data.Services.IUpdatable.RemoveReferenceFromCollection%2A>|ナビゲーション プロパティからアクセスされる関連オブジェクトのコレクションからオブジェクトを削除する機能を提供します。|  
|<xref:System.Data.Services.IUpdatable.ResetResource%2A>|指定したリソースを更新する機能を提供します。|  
|<xref:System.Data.Services.IUpdatable.ResolveResource%2A>|特定のオブジェクト インスタンスによって表されるリソースを返す機能を提供します。|  
|<xref:System.Data.Services.IUpdatable.SaveChanges%2A>|すべての保留中の変更を保存する機能を提供します。|  
|<xref:System.Data.Services.IUpdatable.SetReference%2A>|ナビゲーション プロパティを使用して関連するオブジェクト参照を設定する機能を提供します。|  
|<xref:System.Data.Services.IUpdatable.SetValue%2A>|リソースのプロパティの値を設定する機能を提供します。|  
  
## 同時実行の処理  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] は、エンティティの同時実行トークンを定義できるようにすることで、オプティミスティック同時実行制御モデルをサポートしています。  この同時実行トークンは、エンティティの 1 つ以上のプロパティが含まれており、要求、更新、または削除されているデータに対して行われた変更があるかどうかを判断するためにデータ サービスによって使用されます。  要求内の eTag から取得したトークンの値がエンティティの現在の値と異なる場合、データ サービスで例外が発生します。  リフレクション プロバイダーの同時実行トークンを定義するために <xref:System.Data.Services.ETagAttribute> がエンティティ型に適用されます。  同時実行トークンには、キー プロパティまたはナビゲーション プロパティを含めることはできません。  詳細については、「[データ サービスの更新](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)」を参照してください。  
  
## リフレクション プロバイダーによる SQL への LINQ の使用  
 既定では Entity Framework がネイティブでサポートされるので、これが [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] でリレーショナル データを使用する場合の推奨データ プロバイダーです。  ただし、データ サービスで LINQ to SQL クラスを使用するには、リフレクション プロバイダーを使用できます。  LINQ to SQL Object Relational Designer \(O\/R Designer\) によって生成される <xref:System.Data.Linq.DataContext> のメソッドによって返される <xref:System.Data.Linq.Table%601> 結果セットは、<xref:System.Linq.IQueryable%601> インターフェイスを実装します。  そのため、リフレクション プロバイダーは、生成された LINQ to SQL クラスを使用して、これらのメソッドにアクセスし、SQL Server からエンティティ データを返すことができます。  ところが、LINQ to SQL は <xref:System.Data.Services.IUpdatable> インターフェイスを実装しないので、既存の <xref:System.Data.Linq.DataContext> 部分クラスを拡張する部分クラスを追加して、<xref:System.Data.Services.IUpdatable> 実装を追加する必要があります。  詳細については、「[方法: LINQ to SQL データ ソースを使用してデータ サービスを作成する](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)」を参照してください。  
  
## 参照  
 [データ サービス プロバイダー](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)