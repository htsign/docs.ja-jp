---
title: "トレースの構成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: tracing [WCF]
ms.assetid: 82922010-e8b3-40eb-98c4-10fc05c6d65d
caps.latest.revision: "53"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1b3b200e26d4d615dd67c13770073b76dac78005
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="configuring-tracing"></a>トレースの構成
ここでは、トレースを有効にする方法、トレースを出力し、トレース レベルを設定するようにトレース ソースを構成する方法、エンドツーエンドのトレース相関をサポートするようにアクティビティ トレースと伝達を設定する方法、およびトレースにアクセスするようにトレース リスナーを設定する方法について説明します。  
  
 実稼働またはデバッグ環境でのトレース設定の推奨事項を参照してください[トレースとメッセージ ログの推奨設定](../../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md)です。  
  
> [!IMPORTANT]
>  Windows 8 でアプリケーションによるトレース ログの生成を行うには、アプリケーションを権限の高い状態で実行 (管理者として実行) する必要があります。  
  
## <a name="enabling-tracing"></a>トレースの有効化  
 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] では次の診断トレース データが出力されます。  
  
-   操作呼び出し、コード例外、警告、その他の重要な処理イベントなど、アプリケーションのすべてのコンポーネントにおける処理マイルストーンのトレース。  
  
-   トレース機能が正しく動作しないときの Windows エラー イベント。 参照してください[イベントのログ記録](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)です。  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] トレースは、<xref:System.Diagnostics> に基づいています。 トレースを使用するには、構成ファイルまたはコードでトレース ソースを定義する必要があります。 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] は、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] アセンブリごとにトレース ソースを定義します。 `System.ServiceModel` トレース ソースは最も一般的な [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] トレース ソースで、トランスポートへの出入りからユーザー コードへの出入りまで、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 通信スタック全体の処理マイルストーンを記録します。 `System.ServiceModel.MessageLogging` トレース ソースは、システムを通過するすべてのメッセージを記録します。  
  
 既定では、トレースは無効です。 トレースを有効にするには、トレース リスナーを作成し、構成で選択したトレース ソースのトレース レベルを "Off" 以外に設定する必要があります。それ以外の場合、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] はトレースを生成しません。 リスナーを指定しないと、トレースは自動的に無効になります。 リスナーを定義してもトレース レベルを指定しないと、トレース レベルは既定で "Off" に設定され、トレースが出力されなくなります。  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 機能拡張ポイント (カスタム操作の呼び出し元など) を使用する場合、独自のトレースを出力する必要があります。 これは、機能拡張ポイントを実装すると、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] が既定のパスに標準のトレースを出力できなくなるためです。 トレースを出力することで手動トレースのサポートを実装しない場合、予測したトレースが得られない場合があります。  
  
 トレースは、アプリケーションの構成ファイル (Web ホスト型アプリケーションの場合は Web.config、自己ホスト型アプリケーションの場合は Appname.exe.config) を編集することで構成できます。 以下は、このような編集の例です。 これらの設定の詳細については、「を構成するトレース リスナーをトレースを使用する」セクションを参照してください。  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <sources>  
            <source name="System.ServiceModel"   
                    switchValue="Information, ActivityTracing"  
                    propagateActivity="true">  
            <listeners>  
               <add name="traceListener"   
                   type="System.Diagnostics.XmlWriterTraceListener"   
                   initializeData= "c:\log\Traces.svclog" />  
            </listeners>  
         </source>  
      </sources>  
   </system.diagnostics>  
</configuration>  
```  
  
> [!NOTE]
>  構成ファイルを編集する、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]でサービス プロジェクト[!INCLUDE[vs_current_short](../../../../../includes/vs-current-short-md.md)]、アプリケーションの構成ファイルを右クリックして、Web でホストされるアプリケーション、appname.exe.config 自己ホスト型アプリケーションの場合は Web.config **ソリューション エクスプ ローラー**です。 選択し、 **WCF 構成の編集**コンテキスト メニュー項目。 これにより、起動、[構成エディター ツール (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)の構成設定を変更できます[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]グラフィカル ユーザー インターフェイスを使用したサービスです。  
  
## <a name="configuring-trace-sources-to-emit-traces"></a>トレースを出力するためのトレース ソースの構成  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] は、アセンブリごとにトレース ソースを定義します。 アセンブリ内で生成されたトレースは、該当するソースで定義されているリスナーによってアクセスされます。 次のトレース ソースが定義されます。  
  
-   System.ServiceModel: 構成の読み取り、トランスポートでのメッセージの処理、セキュリティ処理、ユーザー コードでのメッセージのディスパッチなど、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 処理のすべての段階を記録します。  
  
-   System.ServiceModel.MessageLogging: システムを通過するすべてのメッセージを記録します。  
  
-   System.IdentityModel  
  
-   System.ServiceModel.Activation  
  
-   System.IO.Log: Common Log File System (CLFS) への .NET Framework インターフェイスを記録します。  
  
-   System.Runtime.Serialization: オブジェクトの読み取りまたは書き込みを記録します。  
  
-   CardSpace  
  
 各トレース ソースは、次の構成例に示すように同じ (共有) リスナーを使用するように構成できます。  
  
```xml  
<configuration>  
    <system.diagnostics>  
        <sources>  
            <source name="System.ServiceModel"   
                    switchValue="Information, ActivityTracing"  
                    propagateActivity="true">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="CardSpace">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.IO.Log">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.Runtime.Serialization">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.IdentityModel">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
        </sources>  
  
        <sharedListeners>  
            <add name="xml"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="c:\log\Traces.svclog" />  
        </sharedListeners>  
    </system.diagnostics>  
</configuration>  
```  
  
 さらに、次の例に示すように、ユーザー定義のトレース ソースを追加してユーザー コード トレースを出力することもできます。  
  
```xml  
<system.diagnostics>  
   <sources>  
       <source name="UserTraceSource" switchValue="Warning, ActivityTracing" >  
          <listeners>  
              <add name="xml"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="C:\logs\UserTraces.svclog" />  
          </listeners>  
       </source>  
   </sources>  
   <trace autoflush="true" />   
</system.diagnostics>  
```  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]ユーザー定義の作成、トレース ソースを参照してください[トレースを拡張する](../../../../../docs/framework/wcf/samples/extending-tracing.md)です。  
  
## <a name="configuring-trace-listeners-to-consume-traces"></a>トレースを使用するためのトレース リスナーの構成  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] は、実行時にトレース データを処理するリスナーにデータを送信します。 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] は <xref:System.Diagnostics> に出力の形式が異なる複数の定義済みリスナーを提供します。 カスタム リスナーの種類を追加することもできます。  
  
 `add` を使用して、使用するトレース リスナーの名前と種類を指定できます。 この例の構成では、リスナーに `traceListener` という名前を付け、使用する種類として標準の .NET Framework トレース リスナー (`System.Diagnostics.XmlWriterTraceListener`) を追加しています。 ソースごとに任意の数のトレース リスナーを追加できます。 トレース リスナーがトレースをファイルに出力する場合は、構成ファイルで出力ファイルの場所と名前を指定する必要があります。 指定するには、`initializeData` をそのリスナーのファイルの名前に設定します。 ファイル名を指定しないと、使用するリスナーの種類に基づいて任意のファイル名が生成されます。 <xref:System.Diagnostics.XmlWriterTraceListener> を使用した場合は、拡張子のないファイル名が生成されます。 カスタム リスナーを実装した場合は、この属性を使用して、ファイル名以外の初期化データを受け取ることもできます。 たとえば、この属性にデータベース識別子を指定できます。  
  
 カスタム トレース リスナーは、ネットワーク上のリモート データベースなどにトレースを送信するように構成できます。 アプリケーションを展開するユーザーは、リモート コンピューターのトレース ログに適切なアクセス制御を適用する必要があります。  
  
 また、トレース リスナーはプログラムによって構成することもできます。 [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][する方法: を作成し、トレース リスナーを初期化](http://go.microsoft.com/fwlink/?LinkId=94648)と[カスタム TraceListener を作成する](http://go.microsoft.com/fwlink/?LinkId=96239)です。  
  
> [!CAUTION]
>  `System.Diagnostics.XmlWriterTraceListener` はスレッド セーフではないため、トレース ソースは、トレースを出力するときにリソースを排他的にロックする可能性があります。 このリスナーを使用するように構成されたトレース ソースに多くのスレッドがトレースを出力すると、リソースの競合が発生し、パフォーマンスに重大な問題が生じる場合があります。 この問題を解決するには、スレッド セーフなカスタム リスナーを実装する必要があります。  
  
## <a name="trace-level"></a>トレース レベル  
 トレース レベルは、トレース ソースの `switchValue` 設定で制御します。 使用できるトレース レベルを次の表に示します。  
  
|トレース レベル|追跡イベントの性質|追跡イベントの内容|追跡イベント|対象ユーザー|  
|-----------------|----------------------------------|-----------------------------------|--------------------|-----------------|  
|オフ|N/A|N/A|トレースは出力されません。|N/A|  
|重大|「否定的」イベント: 予期しない処理またはエラー状態を示すイベント。||次の例を含む未処理の例外が記録されます。<br /><br /> -OutOfMemoryException<br />-ThreadAbortException (CLR が任意の threadabortexceptionhandler を呼び出します)<br />-StackOverflowException (キャッチできません)<br />-ConfigurationErrorsException<br />-SEHException<br />-アプリケーションの起動エラー<br />-フェイルファースト イベント<br />システム ハング<br />有害メッセージ: アプリケーションが障害が発生しているトレースのメッセージします。|管理者<br /><br /> アプリケーション開発者|  
|エラー|「否定的」イベント: 予期しない処理またはエラー状態を示すイベント。|予期しない処理が発生した。 アプリケーションが、タスクを正常に実行できなかった。 ただし、アプリケーションは依然として動作している。|すべての例外がログに記録されます。|管理者<br /><br /> アプリケーション開発者|  
|警告|「否定的」イベント: 予期しない処理またはエラー状態を示すイベント。|問題が発生したか、発生する可能性があるが、アプリケーションは正常に動作している。 ただし、正常な動作を継続できなくなる可能性がある。|-アプリケーションは、調整設定よりも多くの要求を受信しています。<br />-受信側キューでは、構成されている処理能力の上限付近です。<br />タイムアウトを超えました。<br />資格情報は拒否されます。|管理者<br /><br /> アプリケーション開発者|  
|情報|「肯定的」イベント: 正常なマイルス イベント|アプリケーションが正常に動作しているかどうかとは無関係の、アプリケーションの実行に関する重要で正常なマイルストーン。|一般に、システム ステータスの監視と診断、パフォーマンスの計測、またはプロファイリングに有用なメッセージが生成されます。 この情報は、キャパシティ プランニングやパフォーマンス管理のために利用できます。<br /><br /> チャネルが作成されます。<br />エンドポイントのリスナーが作成されます。<br />メッセージを入力またはトランスポートから離れる。<br />セキュリティ トークンを取得します。<br />構成の設定が読み取られます。|管理者<br /><br /> アプリケーション開発者<br /><br /> 製品開発者。|  
|詳細|「肯定的」イベント: 正常なマイルス イベント。|ユーザー コードとサービスの両方に対する低レベルのイベントが出力されます。|一般に、このレベルはデバッグやアプリケーションの最適化に利用できます。<br /><br /> -メッセージ ヘッダーが認識されます。|管理者<br /><br /> アプリケーション開発者<br /><br /> 製品開発者。|  
|ActivityTracing||処理アクティビティとコンポーネント間のフロー イベント。|このレベルを使用すると、管理者と開発者は同じアプリケーション ドメイン内のアプリケーションの相関関係を示すことができます。<br /><br /> -開始/停止など、アクティビティ境界のトレース。<br />-転送のトレース。|すべて|  
|すべて||アプリケーションが正常に動作している可能性があります。 すべてのイベントが出力されます。|前のすべてのイベント。|すべて|  
  
 Verbose から Critical までのレベルは相互にスタックされます。つまり、各トレース レベルには、そのレベルよりも上位のすべてのレベルが含まれます (Off レベルを除く)。 たとえば、Warning レベルでリッスンしているリスナーは、Critical、Error、Warning の各トレースを受け取ります。 All レベルには、Verbose から Critical までのイベントとアクティビティ トレース イベントが含まれます。  
  
> [!CAUTION]
>  Information、Verbose、および ActivityTracing の各レベルは、多くのトレースを生成するため、コンピューターで利用可能なすべてのリソースを使い果たした場合は、メッセージ スループットに悪影響を及ぼす可能性があります。  
  
## <a name="configuring-activity-tracing-and-propagation-for-correlation"></a>アクティビティ トレースと伝達の関連付けの構成  
 `activityTracing` 属性に指定する `switchValue` 値を使用してアクティビティ トレースを有効にし、エンドポイント内のアクティビティの境界と転送のトレースを出力できます。  
  
> [!NOTE]
>  [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] の特定の拡張機能を使用する場合に、アクティビティ トレースが有効になっていると、<xref:System.NullReferenceException> が発生することがあります。 この問題を解決するには、アプリケーションの構成ファイルを調べて、トレース ソースの `switchValue` 属性が `activityTracing` に設定されていないことを確認します。  
  
 `propagateActivity` 属性は、メッセージ交換に参加している他のエンドポイントにアクティビティを伝達する必要があるかどうかを示します。 この値を `true` に設定すると、任意の 2 つのエンドポイントで生成されたトレース ファイルを取得し、一方のエンドポイントのトレース セットがもう一方のエンドポイントのトレース セットにどのように転送されるかを監視できます。  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]アクティビティ トレースと伝達を参照してください。[伝達](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md)です。  
  
 両方`propagateActivity`と`ActivityTracing`System.ServiceModel TraceSource に適用されるブール値。 `ActivityTracing`値は、任意のトレース ソースにも適用されますを含む[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]またはユーザー定義のものです。  
  
 ユーザー定義のトレース ソースでは、`propagateActivity` 属性を使用できません。 ユーザー コード アクティビティ ID の伝達では、ServiceModel `ActivityTracing` 属性を `propagateActivity` に設定しているときは、ServiceModel `true` を設定しないでください。  
  
## <a name="see-also"></a>関連項目  
 [トレース](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [管理と診断](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [方法: を作成し、トレース リスナーを初期化します。](http://go.microsoft.com/fwlink/?LinkId=94648)  
 [カスタムの TraceListener の作成](http://go.microsoft.com/fwlink/?LinkId=96239)
