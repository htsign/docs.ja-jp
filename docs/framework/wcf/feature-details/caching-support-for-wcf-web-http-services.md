---
title: "WCF WEB HTTP サービスのキャッシュ サポート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f8078e0-00d9-415c-b8ba-c1b6d5c31799
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a4dd96f444d6405022a0a812a55a92cec1052fbb
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="caching-support-for-wcf-web-http-services"></a>WCF WEB HTTP サービスのキャッシュ サポート
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]WCF Web HTTP サービスで既に ASP.NET での使用可能な宣言によるキャッシュ機構を使用できます。 これにより、WCF Web HTTP サービス操作からの応答をキャッシュできます。 キャッシュ用に構成されているサービスに対してユーザーが HTTP GET を送信すると、ASP.NET は、キャッシュされた応答を送り返し、サービス メソッドは呼び出されません。 キャッシュの有効期限が切れると、ユーザーが次回に HTTP GET を送信したときに、サービス メソッドが呼び出され、応答が再度キャッシュされます。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]ASP.NET キャッシュを参照してください[ASP.NET のキャッシュの概要](http://go.microsoft.com/fwlink/?LinkId=152534)  
  
## <a name="basic-web-http-service-caching"></a>基本的な Web HTTP サービスのキャッシュ  
 WEB HTTP サービスのキャッシュを有効にするには、まず、<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> の <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> を <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> または <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required> に設定してサービスに適用し、ASP.NET との互換性を有効にする必要があります。  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] では、キャッシュ プロファイル名を指定できる <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> という新しい属性が導入されています。 この属性は、サービス操作に適用されます。 次の例では、<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> をサービスに適用して ASP.NET との互換性を有効にし、`GetCustomer` 操作をキャッシュできるように構成しています。 <!--zz<xref:System.ServiceModel.Activation.AspNetCacheProfileAttribute>--> `System.ServiceModel.Activation.AspNetCacheProfileAttribute`属性を使用するキャッシュの設定が含まれるキャッシュ プロファイルを指定します。  
  
```csharp
[ServiceContract] AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]
public class Service
{
    [WebGet(UriTemplate = "{id}")]
    [AspNetCacheProfile("CacheFor60Seconds")]
    public Customer GetCustomer(string id)
    {
        // ...
    }
}
```  
  
 また、ASP.NET 互換性モードを Web.config ファイルで有効にすることも必要です。次にその例を示します。  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
>  ASP.NET 互換性モードが有効にされていない場合は、<xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> が使用されて、例外がスローされます。  
  
 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> によって指定されたキャッシュ プロファイル名によって、Web.config 構成ファイルに追加されるキャッシュ プロファイルが特定されます。 キャッシュ プロファイルが定義されている、<`outputCacheSetting`> 要素の次の構成例に示すようにします。  
  
```xml
<!-- ...  -->
<system.web>  
   <caching>  
      <outputCacheSettings>  
         <outputCacheProfiles>  
            <add name="CacheFor60Seconds" duration="60" varyByParam="none" sqlDependency="MyTestDatabase:MyTable"/>  
         </outputCacheProfiles>  
      </outputCacheSettings>  
   </caching>  
   <!-- ... -->  
</system.web>  
```  
  
 これは、ASP.NET アプリケーションで使用できる構成要素と同じです。 ASP.NET キャッシュ プロファイル[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、<xref:System.Web.Configuration.OutputCacheProfile> を参照してください。 Web HTTP サービスの場合、キャッシュ プロファイルで最も重要な属性は `cacheDuration` と `varyByParam` です。 この 2 つの属性はどちらも必要です。 `cacheDuration` は、応答がキャッシュに保持される時間 (秒数) を設定します。 `varyByParam` では、応答のキャッシュに使用されるクエリ文字列パラメーターを指定できます。 異なるクエリ文字列パラメーターの値を使用する要求は、すべて個別にキャッシュされます。 たとえば、http://MyServer/MyHttpService/MyOperation?param=10 に最初の要求を送ると、同じ URI を使用して送られるすべての後続の要求には、キャッシュされている応答が返されます (キャッシュ期間が経過していない場合)。 クエリ文字列パラメーターの値が異なることを除いて同じである同様の要求に対する応答は、個別にキャッシュされます。 このような個別のキャッシングを行わない場合は、`varyByParam` を "none" に設定します。  
  
## <a name="sql-cache-dependency"></a>SQL キャッシュ依存関係  
 Web HTTP サービスの応答も、SQL キャッシュ依存関係と併せてキャッシュできます。 SQL データベースに格納されているデータに応じて WCF Web HTTP サービスが異なる場合は、サービスの応答をキャッシュして、キャッシュした応答を、SQL データベース テーブル内のデータの変更時に無効にすることもできます。 この動作は、すべて Web.config ファイル内で構成します。 内の接続文字列を定義する必要があります最初に、<`connectionStrings`> 要素。  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 内の SQL キャッシュ依存関係を有効にする必要があります、<`caching`> 内の要素、<`system.web`> 要素の構成例を次に示すようにします。  
  
```xml  
<system.web>
  <caching>
    <sqlCacheDependency enabled="true" pollTime="1000">
      <databases>
        <add name="MyTestDatabase" connectionStringName="connectString" />
      </databases>
    </sqlCacheDependency>
    <!-- ... -->
  </caching>
  <!-- ... -->
</system.web>
```  
  
 ここでは、SQL キャッシュ依存関係を有効にし、ポーリング タイムを 1000 ミリ秒に設定しています。 ポーリング タイムが経過するたびに、データベース テーブルで更新の有無が確認されます。 変更が検出されると、キャッシュの内容が削除され、次にサービス操作が呼び出されたときに、新しい応答がキャッシュされます。 内で、<`sqlCacheDependency`> 要素は、データベースを追加し、内の接続文字列を参照、<`databases`> 要素の次の例に示すようにします。  
  
```xml  
<system.web>
  <caching>
    <sqlCacheDependency enabled="true" pollTime="1000">
      <databases>
        <add name="MyTestDatabase" connectionStringName="connectString" />
      </databases>  
    </sqlCacheDependency>  
    <!-- ... -->  
  </caching>  
  <!-- ... -->  
</system.web>  
```  
  
 次に、出力キャッシュ内の設定を構成する必要があります、<`caching`> 要素の次の例に示すようにします。  
  
```xml
<system.web>
  <caching>  
    <!-- ...  -->
    <outputCacheSettings>
      <outputCacheProfiles>
        <add name="CacheFor60Seconds" duration="60" varyByParam="none" sqlDependency="MyTestDatabase:MyTable" />
      </outputCacheProfiles>
    </outputCacheSettings>
  </caching>
  <!-- ... -->
</system.web>
```  
  
 ここでは、キャッシュ期間が 60 秒に、`varyByParam` が none に設定されており、`sqlDependency` が、コロン区切りのデータベース名とテーブルのペアをセミコロンで区切ったリストに設定されています。 `MyTable` のデータが変更されると、キャッシュされているサービス操作への応答が削除されます。この操作が呼び出されると、新しい応答が (サービス操作の呼び出しによって) 生成され、キャッシュされて、クライアントに返されます。  
  
> [!IMPORTANT]
>  SQL データベースにアクセスする asp.net、使用する必要があります、 [ASP.NET SQL Server の登録ツール](http://go.microsoft.com/fwlink/?LinkId=152536)です。 また、適切なユーザー アカウントに、データベースおよびテーブルへのアクセスを許可する必要があります。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Web アプリケーションから SQL Server へのアクセス](http://go.microsoft.com/fwlink/?LinkId=178988)です。  
  
## <a name="conditional-http-get-based-caching"></a>条件付きの HTTP GET ベースのキャッシュ  
 Web HTTP シナリオで条件付きの HTTP GET はよく使用サービスによってキャッシュを実装するインテリジェント HTTP」の説明に従って、 [HTTP 仕様](http://go.microsoft.com/fwlink/?LinkId=165800)です。 そのためには、サービスが ETag ヘッダーの値を HTTP 応答に設定する必要があります。 また、HTTP 要求の If-None-Match ヘッダーの値を確認して、指定されている ETag が現在の ETag と一致するかどうかを調べる必要もあります。  
  
 GET および HEAD 要求の場合、<xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> は ETag 値を取得し、この値と要求内の If-None-Match ヘッダーとを比較します。 ヘッダーが存在し、一致が見つかった場合は、HTTP ステータス コード 304 (変更なし) が設定された <xref:System.ServiceModel.Web.WebFaultException> がスローされ、一致する ETag が設定されている応答に ETag ヘッダーが追加されます。  
  
 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> メソッドのオーバーロードの 1 つは、最終更新日を取得し、これを、要求の If-Modified-Since ヘッダーと比較します。 ヘッダーが存在し、リソースが変更されていない場合は、HTTP ステータス コード 304 (変更なし) が設定された <xref:System.ServiceModel.Web.WebFaultException> がスローされます。  
  
 PUT、POST、および DELETE の各要求の場合、<xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> は、リソースの現在の ETag 値を取得します。 現在の ETag 値が null の場合は、メソッドはなし-If-match ヘッダーがの値を持つことが確認"*"です。  現在の ETag 値が既定値ではない場合、メソッドは、現在の ETag 値と要求の If-None- Match ヘッダーを比較します。 どちらの場合も、求められるヘッダーが要求内に存在しない、またはヘッダーの値がチェック条件を満たしていないと、メソッドは、HTTP ステータス コード 412 (必須条件に失敗しました) が設定された <xref:System.ServiceModel.Web.WebFaultException> をスローし、応答の ETag ヘッダーを現在の ETag 値に設定します。  
  
 `CheckConditional` メソッドも <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> メソッドも、応答ヘッダーに設定される ETag 値が、確実に HTTP 仕様に沿った有効な ETag になるようにします。 これには、ETag 値を囲む二重引用符がない場合に二重引用符を付ける処理や、二重引用符内の文字を適切にエスケープする処理が含まれます。 ETag の弱い比較はサポートされていません。  
  
 これらのメソッドを使用する方法の例を次に示します。  
  
```csharp
[WebGet(UriTemplate = "{id}"), Description("Returns the specified customer from customers collection. Returns NotFound if there is no such customer. Supports conditional GET.")]
public Customer GetCustomer(string id)
{
    lock (writeLock)
    {
        // return NotFound if there is no item with the specified id.
        object itemEtag = customerEtags[id];
        if (itemEtag == null)
        {
            throw new WebFaultException(HttpStatusCode.NotFound);
        }
  
        // return NotModified if the client did a conditional GET and the customer item has not changed
        // since when the client last retrieved it
        WebOperationContext.Current.IncomingRequest.CheckConditionalRetrieve((long)itemEtag);
        Customer result = this.customers[id] as Customer;
        
        // set the customer etag before returning the result
        WebOperationContext.Current.OutgoingResponse.SetETag((long)itemEtag);
        return result;
    }
}
```  
  
## <a name="security-considerations"></a>セキュリティの考慮事項  
 承認が必要な要求の応答はキャッシュしないでください。応答がキャッシュから提供された場合は、承認が実行されません。  このような応答をキャッシュすると、重大なセキュリティの脆弱性が生じます。  通常、承認が必要な要求ではユーザー固有のデータが提供されるため、サーバー側でキャッシュしても利点はありません。  このような場合は、クライアント側でキャッシュするか、単にキャッシュをまったく行わない方が適切です。
