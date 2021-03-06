---
title: "共通のスキーマ コレクション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50127ced-2ac8-4d7a-9cd1-5c98c655ff03
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 19a95cf5d8d9b5fc5f805574b6de15c90fb38efd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="common-schema-collections"></a>共通のスキーマ コレクション
共通のスキーマ コレクションとは、それぞれの .NET Framework マネージ プロバイダーにより実装されるスキーマ コレクションのことです。 呼び出すことによってサポートされるスキーマ コレクションの一覧を特定の .NET Framework マネージ プロバイダーを照会することができます、 **GetSchema**メソッド引数のない、またはスキーマ コレクション名に"metadatacollections を指定して"います。 これにより、サポートされるスキーマ コレクションの一覧、それぞれがサポートする制限数、および使用する識別子部分の数と共に、<xref:System.Data.DataTable> が返されます。 これらのコレクションは、必要なすべての列を表現します。 プロバイダーでは、任意で列を追加できます。 たとえば、`SqlClient` と `OracleClient` は、ParameterName を制限のコレクションに追加します。  
  
 プロバイダーでは必要な列の値を特定できない場合、null を返します。  
  
 使用しての詳細については、 **GetSchema**メソッドを参照してください[GetSchema およびスキーマ コレクション](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md)です。  
  
## <a name="metadatacollections"></a>MetaDataCollections  
 このスキーマ コレクションは、データベースに接続するために現在使用されている、.NET Framework マネージ プロバイダーによりサポートされるすべてのスキーマ コレクションに関する情報を公開します。  
  
|ColumnName|DataType|説明|  
|----------------|--------------|-----------------|  
|CollectionName|string|渡すコレクションの名前、 **GetSchema**のコレクションを返すメソッド。|  
|NumberOfRestrictions|int|コレクションに対して指定できる制限の数。|  
|NumberOfIdentifierParts|int|複合識別子部分とデータベース オブジェクト名部分の数。 たとえば、SQL Server の場合は、テーブルに 3 つ、列に 4 つになります。 Oracle の場合は、テーブルに 2 つ、列に 3 つになります。|  
  
## <a name="datasourceinformation"></a>DataSourceInformation  
 このスキーマ コレクションは、.NET Framework マネージ プロバイダーが現在接続しているデータ ソースに関する情報を公開します。  
  
|ColumnName|DataType|説明|  
|----------------|--------------|-----------------|  
|CompositeIdentifierSeparatorPattern|string|複合識別子内の複合セパレーターと一致する正規表現。 たとえば、"\\"。 (SQL サーバー用) または"@&#124;です。\\." (Oracle の場合) のように指定します。<br /><br /> 複合識別子はたとえば、データベース オブジェクト名の使用目的は、通常: pubs.dbo.authors またはpubs@dbo.authorsです。<br /><br /> SQL Server の正規表現を使用して"\\。"です。 Oracleclient の場合、次のように使用します。"@&#124;です。\\.".<br /><br /> ODBC の場合、Catalog_name_seperator を使用します。<br /><br /> OLE DB の場合、DBLITERAL_CATALOG_SEPARATOR または DBLITERAL_SCHEMA_SEPARATOR を使用します。|  
|DataSourceProductName|string|"Oracle" や "SQLServer" など、プロバイダーによってアクセスされる製品の名前。|  
|DataSourceProductVersion|string|プロバイダーによりアクセスされる製品のバージョンを、Microsoft の形式ではなく、データ ソースのネイティブ形式で表します。<br /><br /> 場合によっては、DataSourceProductVersion と DataSourceProductVersionNormalized は同じ値になります。 OLE DB と ODBC の場合、これらの値は、元になるネイティブ API 内の同じ関数呼び出しに割り当てられているので、常に同じ値になります。|  
|DataSourceProductVersionNormalized|string|`String.Compare()` を使用して比較できるような、データ ソースの正規化されたバージョン。 この形式は、バージョン 10 がバージョン 1 とバージョン 2 の間に並べ替えられることがないように、プロバイダーのすべてのバージョンで一貫しています。<br /><br /> たとえば、Oracle プロバイダーは、これにより、「08.01.07.04.01」を返すには、Oracle 8i データ ソースの正規化されたバージョンは、"nn.nn.nn.nn.nn"の形式を使用します。 SQL Server では、一般的な Microsoft"nn.nn.nnnn"形式を使用します。<br /><br /> 場合によっては、DataSourceProductVersion と DataSourceProductVersionNormalized は同じ値になります。 OLE DB と ODBC の場合、これらの値は、元になるネイティブ API 内の同じ関数呼び出しに割り当てられているので、常に同じ値になります。|  
|GroupByBehavior|<xref:System.Data.Common.GroupByBehavior>|GROUP BY 句の列と SELECT リストの集計以外の列間のリレーションシップを指定します。|  
|IdentifierPattern|string|識別子と一致し、その識別子の一致した値がある正規表現。 たとえば "[A-Za-z0-9_#$]" になります。|  
|IdentifierCase|<xref:System.Data.Common.IdentifierCase>|引用符で囲まれていない識別子が、大文字と小文字を区別して扱われるかどうかを示します。|  
|OrderByColumnsInSelect|bool|ORDER BY 句の列が SELECT リストになければならないかどうかを示します。 値が true である場合、SELECT リストになければならないことを示します。値が false である場合、SELECT リストにある必要がないことを示します。|  
|ParameterMarkerFormat|string|パラメーターを書式設定する方法を表す書式文字列。<br /><br /> 名前付きパラメーターがデータ ソースでサポートされている場合、この文字列内の最初のプレースホルダーは、パラメーター名が書式設定される場所である必要があります。<br /><br /> たとえば、データ ソースが名前に ":" というプレフィックスが付いたパラメーターを要求している場合、これは ":{0}" になります。 これを "p1" のパラメーター名で書式設定すると、結果の文字列は ":p1" になります。<br /><br /> データ ソース、必要なパラメーターを付けるかどうかは、' @'、名前が含まれている、このすると、'{0}'、およびパラメーターを書式設定の結果がという名前が"@p1「単になります」@p1"です。<br /><br /> データ ソースの名前付きパラメーターを期待せずの使用を想定している、'?' 文字、単に、書式指定文字列を指定することができます '?'、パラメーター名を無視します。 OLE DB の場合、"?" を返します。|  
|ParameterMarkerPattern|string|パラメーター マーカーと一致する正規表現。 パラメーター名の一致する値になります (一致する値がある場合)。<br /><br /> たとえば、パラメーター名に "@" という前置文字が含まれている、名前付きパラメーターがサポートされている場合、"(@[A-Za-z0-9_$#]*)" となります。<br /><br /> ただしで名前付きパラメーターがサポートされている場合、':' 前置文字は、パラメーター名の一部ではないとになります。": ([z0 _ $#]\*)"です。<br /><br /> もちろん、データ ソースが名前付きパラメーターをサポートしない場合は、単に "?" になります。|  
|ParameterNameMaxLength|int|パラメーター名の文字の最大長。 Visual Studio では、パラメーター名がサポートされている場合、最大長の最小値が 30 文字であることを想定しています。<br /><br /> データ ソースが名前付きパラメーターをサポートしない場合、このプロパティは 0 を返します。|  
|ParameterNamePattern|string|有効なパラメーター名と一致する正規表現。 異なるデータ ソースでは、パラメーター名として使用できる文字に関して、規則が異なります。<br /><br /> Visual Studio では、パラメーター名がサポートされている場合、文字 "\p{Lu}\p{Ll}\p{Lt}\p{Lm}\p{Lo}\p{Nl}\p{Nd}" が、パラメーター名として有効な、サポートされる最小限の文字のセットです。|  
|QuotedIdentifierPattern|string|引用符で囲まれた識別子と一致し、引用符を除いた識別子自体の一致する値のある正規表現。 たとえば、データ ソースが引用符で囲まれた識別子を識別する二重引用符を使用する場合になります:"(([^\\"] &#124;\\"\\")*)".|  
|QuotedIdentifierCase|<xref:System.Data.Common.IdentifierCase>|引用符で囲まれた識別子が、大文字と小文字を区別して扱われるかどうかを示します。|  
|StatementSeparatorPattern|string|ステートメント区切り文字と一致する正規表現。|  
|StringLiteralPattern|string|文字列リテラルと一致し、リテラル自体の一致する値のある正規表現。 たとえば、文字列を識別する、データ ソースが単一引用符を使用する場合になります:"('([^'] &#124; ')*')"'|  
|SupportedJoinOperators|<xref:System.Data.Common.SupportedJoinOperators>|データ ソースでサポートされる SQL の JOIN ステートメントの種類を指定します。|  
  
## <a name="datatypes"></a>DataTypes  
 このスキーマ コレクションは、.NET Framework マネージ プロバイダーが現在接続されているデータベースでサポートされているデータ型に関する情報を公開します。  
  
|ColumnName|DataType|説明|  
|----------------|--------------|-----------------|  
|TypeName|string|プロバイダー固有のデータ型の名前。|  
|ProviderDbType|int|パラメーターの型を指定するときに使用する必要のある、プロバイダー固有の型の値。 たとえば、SqlDbType.Money または OracleType.Blob になります。|  
|ColumnSize|long|数値以外の列またはパラメーターの長さは、最大長か、プロバイダーによりこの型に定義された長さのいずれかを参照します。<br /><br /> 文字データの場合、これは、最大長か、データ ソースにより定義されている単位で定義された長さです。 Oracle には、長さを指定してから、一部の文字データ型の実際の格納サイズを指定するという概念があります。 これは、Oracle の単位で長さのみを定義します。<br /><br /> 日時のデータ型の場合、これは (秒の小数部構成要素の最大有効桁数を前提として) 文字列表現の長さです。<br /><br /> データ型が数値である場合、これは、データ型の最大有効桁数の上限です。|  
|CreateFormat|string|CREATE TABLE などのデータ定義ステートメントに、この列を追加する方法を示す書式文字列。 CreateParameter 配列の各要素は、書式文字列内で "パラメーター マーカー" で表される必要があります。<br /><br /> たとえば、SQL データ型の DECIMAL には Precision と Scale が必要です。 この場合、書式文字列は "DECIMAL({0},{1})" になります。|  
|CreateParameters|string|このデータ型の列を作成する場合に指定する必要のある作成パラメーター。 各作成パラメーターは、指定される順序で、コンマで区切られた一覧として文字列内に示されます。<br /><br /> たとえば、SQL データ型の DECIMAL には Precision と Scale が必要です。 この場合、作成パラメーターには、"precision, scale" という文字列が含まれる必要があります。<br /><br /> precision を 10、scale を 2 として DECIMAL 列を作成するためのテキスト コマンド内では、CreateFormat 列の値は DECIMAL({0},{1}) になり、完全な型指定は DECIMAL(10,2) になります。|  
|DataType|string|データ型の .NET Framework 型の名前。|  
|IsAutoincrementable|bool|true の場合、このデータ型の値で自動インクリメントが行われます。<br /><br /> false の場合、このデータ型の値で自動インクリメントは行われません。<br /><br /> このデータ型の 1 つの列で自動インクリメントが行われるかどうかを示しているだけであり、この型のすべての列で自動インクリメントが行われるわけではないことに注意してください。|  
|IsBestMatch|bool|true の場合、データ ストア内のすべてのデータ型と、DataType 列の値により指定されている .NET Framework データ型との間で、最も一致するデータ型になります。<br /><br /> false の場合、データ型は、最も一致するデータ型ではありません。<br /><br /> DataType 列の値が同じ行のセットでは、1 行だけで BestMatch 列が true に設定されます。|  
|IsCaseSensitive|bool|true の場合、データ型は文字型であり、大文字と小文字が区別されます。<br /><br /> false の場合、データ型は文字型ではなく、大文字と小文字は区別されません。|  
|IsFixedLength|bool|true の場合、データ定義言語 (DDL) により作成されたこのデータ型の列は、固定長になります。<br /><br /> false の場合、DDL により作成されたこのデータ型の列は、可変長になります。<br /><br /> DBNull.Value の場合、プロバイダーがこのフィールドを固定長の列または可変長の列のどちらで割り当てるかは不明です。|  
|IsFixedPrecisionScale|bool|true の場合、データ型には、固定有効桁数と小数点以下桁数があります。<br /><br /> false の場合、データ型には、固定有効桁数と小数点以下桁数がありません。|  
|IsLong|bool|true の場合、データ型には、非常に長いデータが含まれます。非常に長いデータの定義は、プロバイダーによって異なります。<br /><br /> false の場合、データ型には、非常に長いデータは含まれません。|  
|IsNullable|bool|true の場合、データ型は null に設定できます。<br /><br /> false の場合、データ型は null に設定できません。<br /><br /> DBNull.Value の場合、データ型を null に設定できるかどうかは不明です。|  
|IsSearchable|bool|true の場合、データ型は、LIKE 述語を除く任意の演算子と共に WHERE 句で使用できます。<br /><br /> false の場合、データ型は、LIKE 述語を除く任意の演算子と共に WHERE 句で使用できません。|  
|IsSearchableWithLike|bool|true の場合、データ型は、LIKE 述語と共に使用できます。<br /><br /> false の場合、データ型は、LIKE 述語と共に使用できません。|  
|IsUnsigned|bool|true の場合、データ型は符号なしになります。<br /><br /> false の場合、データ型は符号付きになります。<br /><br /> DBNull.Value の場合、データ型に適用されません。|  
|MaximumScale|short|型インジケーターが数値型である場合、小数点の右側にとることができる最大桁数になります。 それ以外の場合は DBNull.Value になります。|  
|MinimumScale|short|型インジケーターが数値型である場合、小数点の右側にとることができる最小桁数になります。 それ以外の場合は DBNull.Value になります。|  
|IsConcurrencyType|bool|true の場合、データ型は、行が変更されるたびにデータベースにより更新され、列の値がすべての前の値とは異なります。<br /><br /> false の場合、行が変更されるたびにデータ型がデータベースにより更新されることはありません。<br /><br /> DBNull.Value の場合、データベースでは、この型のデータ型をサポートしません。|  
|IsLiteralSupported|bool|true の場合、データ型は、リテラルとして表現できます。<br /><br /> false の場合、データ型は、リテラルとして表現できません。|  
|LiteralPrefix|string|指定されたリテラルに適用されるプレフィックス。|  
|LiteralSuffix|string|指定されたリテラルに適用されるサフィックス。|  
|NativeDataType|String|NativeDataType は、データ型の OLE DB 型を公開するための OLE DB 固有の列です。|  
  
## <a name="restrictions"></a>制約  
 このスキーマ コレクションは、データベースへの接続に現在使用されている、.NET Framework マネージ プロバイダーでサポートされる制限に関する情報を公開します。  
  
|ColumnName|DataType|説明|  
|----------------|--------------|-----------------|  
|CollectionName|string|これらの制限を適用するコレクションの名前。|  
|RestrictionName|string|コレクション内の制限の名前。|  
|RestrictionDefault|string|無視されます。|  
|RestrictionNumber|int|この特定の制限が収まっているコレクションの制限内の実際の位置。|  
  
## <a name="reservedwords"></a>ReservedWords  
 このスキーマ コレクションは、.NET Framework マネージ プロバイダーが現在接続されているデータベースにより予約されている予約語に関する情報を公開します。  
  
|ColumnName|DataType|説明|  
|----------------|--------------|-----------------|  
|ところ予約語|string|プロバイダー固有の仕様には、word が予約されています。|  
  
## <a name="see-also"></a>関連項目  
 [データベース スキーマ情報の取得](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [GetSchema およびスキーマ コレクション](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
