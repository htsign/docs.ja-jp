---
title: CAST (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07b6d750-dfd4-48a9-b86c-3badcbba6f70
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 353398f834aff5cefb3aed91899ce042df9df60a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="cast-entity-sql"></a>CAST (Entity SQL)
あるデータ型の式を別のデータ型に変換します。  
  
## <a name="syntax"></a>構文  
  
```  
CAST ( expression AS data_type )  
```  
  
## <a name="arguments"></a>引数  
 `expression`  
 `data_type`に変換できる任意の有効な式。  
  
 `data_type`  
 対象システムで提供されるデータ型。 プリミティブ (スカラー) 型でなければなりません。 使用される `data_type` は、クエリのスペースによって異なります。 クエリが <xref:System.Data.EntityClient.EntityCommand>で実行される場合、データ型は概念モデルで定義された型です。 詳細については、「 [CSDL Specification](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)」を参照してください。 クエリが <xref:System.Data.Objects.ObjectQuery%601>で実行される場合、データ型は共通言語ランタイム (CLR) 型です。  
  
## <a name="return-value"></a>戻り値  
 `data_type`と同じ値が返されます。  
  
## <a name="remarks"></a>コメント  
 キャスト式のセマンティックスは [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] CONVERT 式と似ています。 キャスト式は、ある型の値を別の型の値に変換する場合に使用します。  
  
```  
CAST( e as T )  
```  
  
 e が S 型で、S を T に変換できる場合、上記の式は有効なキャスト式です。 T はプリミティブ (スカラー) 型でなければなりません。  
  
 `Edm.Decimal`にキャストする場合は、オプションで精度と小数点以下桁数のファセットの値を指定できます。 明示的に指定しない場合、精度と小数点以下桁数の既定値はそれぞれ 18 と 0 です。 具体的には、 `Decimal`で次のオーバーロードがサポートされています。  
  
-   `CAST( d as Edm.Decimal );`  
  
-   `CAST( d as Edm.Decimal(precision) );`  
  
-   `CAST( d as Edm.Decimal(precision, scale) );`  
  
 キャスト式の使用は明示的な変換と見なされます。 明示的な変換では、データが切り捨てられたり、精度が失われたりする場合があります。  
  
> [!NOTE]
>  CAST はプリミティブ型と列挙メンバー型のみでサポートされています。  
  
## <a name="example"></a>例  
 次の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリは CAST 演算子を使用して、あるデータ型の式を別のデータ型にキャストします。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1.  」の手順に従って[する方法: PrimitiveType 結果が返されますそのクエリを実行する](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)です。  
  
2.  次のクエリを引数として `ExecutePrimitiveTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#CAST](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#cast)]  
  
## <a name="see-also"></a>関連項目  
 [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
