---
title: "Web サービスを使用した LINQ to SQL N 層"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9cb10eb8-957f-4beb-a271-5f682016fed2
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a8577c10dd4d3e2118a4b4dca8b22766a54fc854
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="linq-to-sql-n-tier-with-web-services"></a>Web サービスを使用した LINQ to SQL N 層
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Web サービスなどの疎結合のデータ アクセス層 (DAL) の中間層で使用するために特別に設計されています。 プレゼンテーション層が ASP.NET Web ページである場合、中間層の <xref:System.Web.UI.WebControls.LinqDataSource> とユーザー インターフェイスとのデータ転送を管理するために [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Web サーバー コントロールを使用します。 プレゼンテーション層が ASP.NET ページでない場合には、中間層とプレゼンテーション層の両方で、データのシリアル化と逆シリアル化を管理するための追加の操作を行う必要があります。  
  
## <a name="setting-up-linq-to-sql-on-the-middle-tier"></a>中間層での LINQ to SQL のセットアップ  
 Web サービスまたは n 層アプリケーションでは、中間層にデータ コンテキストおよびエンティティのクラスが含まれます。 これらのクラスは手動で作成できます。または、他の箇所で説明されているように、SQLMetal.exe または[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]を使用して作成することもできます。 オプションとして、デザイン時にエンティティ クラスをシリアル化可能にすることができます。 詳細については、次を参照してください。[する方法: エンティティをシリアル化](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md)です。 別のオプションとして、シリアル化対象のデータをカプセル化するクラスから成る別のセットを作成して、[!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] クエリ内でデータを返すときにシリアル化可能な型に射影することもできます。  
  
 その後、データの取得、挿入、更新のためにクライアントが呼び出すメソッドを持つインターフェイスを定義します。 これらのインターフェイス メソッドは [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] クエリをラップします。 任意のシリアル化技法を使って、リモート メソッド呼び出しとデータのシリアル化を扱うことができます。 唯一の要件として、たとえば標準の Northwind オブジェクト モデルにおける Customers と Orders のように、循環型または双方向のリレーションシップがオブジェクト モデルに存在する場合は、それをサポートするシリアライザーを使用する必要があります。 Windows Communication Foundation (WCF) の <xref:System.Runtime.Serialization.DataContractSerializer> は双方向リレーションシップをサポートしますが、WCF 以外の Web サービスで使用される XmlSerializer はこれをサポートしません。 XmlSerializer の使用を選択する場合には、オブジェクト モデルに循環型リレーションシップが存在しないことを確認する必要があります。  
  
 Windows Communication Foundation の詳細については、次を参照してください。 [Windows Communication Foundation サービスと Visual Studio での WCF Data Services](/visualstudio/data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio)です。  
  
 ビジネス ルールまたは他のドメイン固有のロジックを実装するために、<xref:System.Data.Linq.DataContext> 上の部分クラスとメソッド、およびエンティティ クラスを使用して [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ランタイム イベント内にフックします。 詳細については、次を参照してください。 [N 層ビジネス ロジックを実装する](../../../../../../docs/framework/data/adonet/sql/linq/implementing-business-logic-linq-to-sql.md)です。  
  
## <a name="defining-the-serializable-types"></a>シリアル化可能な型の定義  
 クライアントまたはプレゼンテーション層には、中間層から受け取るクラスについての型定義が必要です。 これらの型は、それ自体、エンティティ クラスにすることも可能です。または、リモート処理用にエンティティ クラスのいくつかのフィールドだけをラップする特殊クラスにすることも可能です。 いずれにしても、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]プレゼンテーション層がこれらの型定義を取得する方法については完全に関係がないです。 たとえば、プレゼンテーション層は、WCF を使用して型を自動生成する場合があります。または、型が定義されている DLL のコピーを持っている場合や、単に独自の型を定義する場合もあります。  
  
## <a name="retrieving-and-inserting-data"></a>データの取得と挿入  
 中間層は、プレゼンテーション層がデータにアクセスする方法を指定するインターフェイスを定義します。 たとえば `GetProductByID(int productID)`、`GetCustomers()` などです。 中間層では、通常、メソッド本体が <xref:System.Data.Linq.DataContext> の新しいインスタンスを作成し、1 つ以上のテーブルに対するクエリを実行します。 その後、中間層は <xref:System.Collections.Generic.IEnumerable%601> として結果を返します。`T` は、エンティティ クラス、またはシリアル化で使用される他の型です。 プレゼンテーション層は、中間層との間でクエリ変数を直接やり取りすることはありません。 2 つの層は、値、オブジェクト、および具象データのコレクションをやり取りします。 コレクションを受け取った後、プレゼンテーション層は必要に応じて [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] to Objects を使ってクエリを実行できます。  
  
 データの挿入時に、プレゼンテーション層は新しいオブジェクトを構築して中間層にそれを送ることができます。または、プレゼンテーション層から渡される値に基づいて中間層にオブジェクトを構築させることもできます。 一般的に、n 層アプリケーションでのデータの取得と挿入は、2 層アプリケーションでの処理と似ています。 詳細については、次を参照してください。[データベースの照会](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)と[作成し、データ変更の送信](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)です。  
  
## <a name="tracking-changes-for-updates-and-deletes"></a>更新と削除における変更内容の追跡  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、タイムスタンプ (RowVersion ともいう) および元の値に基づくオプティミスティック同時実行制御をサポートします。 データベース テーブルにタイムスタンプが存在すると、更新と削除のために、中間層とプレゼンテーション層で実行する必要のある追加の処理はあまりありません。 しかし、元の値を使ってオプティミスティック同時実行制御チェックを行う必要がある場合には、プレゼンテーション層はこれらの値を追跡して、更新時にそれを送り返す必要があります。 これは、プレゼンテーション層上のエンティティに対する変更内容が中間層で追跡されないためです。 実際、エンティティの最初の取得とその後の更新は、通常、<xref:System.Data.Linq.DataContext> のまったく別の 2 つのインスタンスによって実行されます。  
  
 プレゼンテーション層での変更箇所が多いほど、これらの変更を追跡して中間層にパッケージとして戻す操作が複雑になります。 変更内容をやり取りするメカニズムの実装は、完全にアプリケーションに依存しています。 唯一の要件は、オプティミスティック同時実行制御チェックに必要な元の値が [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] に渡されなければならないということです。  
  
 詳細については、次を参照してください。[データで取得および CUD 操作 N 層アプリケーション (LINQ to SQL)](../../../../../../docs/framework/data/adonet/sql/linq/data-retrieval-and-cud-operations-in-n-tier-applications.md)です。  
  
## <a name="see-also"></a>関連項目  
 [N 層でおよびリモート アプリケーション LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)  
 [NIB: LinqDataSource Web サーバー コントロールの概要](http://msdn.microsoft.com/en-us/104cfc3f-7385-47d3-8a51-830dfa791136)
