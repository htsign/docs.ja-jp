---
title: "推奨される国際対応アプリケーション開発手順"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- global applications, best practices
- world-ready applications, best practices
- globalization [.NET Framework], best practices
- international applications [.NET Framework], best practices
ms.assetid: f08169c7-aad8-4ec3-9a21-9ebd3b89986c
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8a50080fa4b84abe84fbb1a44f18e1fb680a07c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="best-practices-for-developing-world-ready-applications"></a>推奨される国際対応アプリケーション開発手順
このセクションでは、推奨される国際対応アプリケーション開発手順について説明します。  
  
## <a name="globalization-best-practices"></a>推奨されるグローバリゼーション手順  
  
1.  アプリケーションを内部的に Unicode アプリケーションにします。  
  
2.  データの操作と書式指定には、<xref:System.Globalization> 名前空間のカルチャ認識クラスを使用します。  
  
    -   並べ替えには <xref:System.Globalization.SortKey> クラスと <xref:System.Globalization.CompareInfo> クラスを使用します。  
  
    -   文字列比較には、<xref:System.Globalization.CompareInfo> クラスを使用します。  
  
    -   日付と時刻の書式指定には、<xref:System.Globalization.DateTimeFormatInfo> クラスを使用します。  
  
    -   数値書式指定には、<xref:System.Globalization.NumberFormatInfo> クラスを使用します。  
  
    -   グレゴリオ暦とグレゴリオ暦以外の暦には、<xref:System.Globalization.Calendar> クラスまたは特定のカレンダー実装を使用します。  
  
3.  状況に応じて、<xref:System.Globalization.CultureInfo?displayProperty=nameWithType> クラスのカルチャ プロパティ設定を使用します。 日付と時刻や数値の書式指定などの書式指定処理には、<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> プロパティを使用します。 リソースを取得するには、<xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> プロパティを使用します。 `CurrentCulture` プロパティと `CurrentUICulture` プロパティはスレッドごとに設定できることに注意してください。  
  
4.  <xref:System.Text> 名前空間のエンコーディング クラスを使用して、アプリケーションでの各種エンコーディングのデータの読み取り操作と書き込み操作を有効にします。 常に ASCII データが使用されるとは限らないことに注意してください。 どのようなテキスト入力でも、各種の言語の文字が使用される可能性があります。 たとえば、アプリケーションは、サーバー名、ディレクトリ名、ファイル名、ユーザー名、および URL に含まれる各種言語の文字を受け入れる必要があります。  
  
5.  <xref:System.Text.UTF8Encoding> クラスを使用する場合は、セキュリティ上の理由から、このクラスに用意されているエラー検出機能を使用してください。 エラー検出機能を有効にするには、`throwOnInvalidBytes` パラメーターを受け取るコンストラクターを使用してクラスのインスタンスを作成し、このパラメーターの値を `true` に設定します。  
  
6.  文字列は、できるだけ全体を 1 つのまとまりとして扱い、個々の文字の連続として処理しないようにします。 これは特に部分文字列の並べ替えと検索で重要です。 これにより、組み合わせ文字の解析に関連する問題の発生を防ぐことができます。  
  
7.  <xref:System.Drawing> 名前空間のクラスを使用してテキストを表示します。  
  
8.  オペレーティング システム間での一貫性を維持するため、ユーザー設定によって <xref:System.Globalization.CultureInfo> がオーバーライドされないようにしてください。 `CultureInfo` パラメーターを受け取る `useUserOverride` コンストラクターを使用し、このパラメーターを `false` に設定してください。  
  
9. 国際対応オペレーティング システムで、国際対応データを使用してアプリケーションの機能をテストします。  
  
10. 文字列比較操作または大文字と小文字の変更操作の結果に基づいてセキュリティ上の決定を行う場合は、アプリケーションで実行する操作がカルチャに依存しないようにします。 こうすることで、`CultureInfo.CurrentCulture` の値が結果に影響を及ぼすことがなくなります。 「文字列比較を使用して、現在のカルチャ」を参照してください[文字列を使用するためのベスト プラクティス](../../../docs/standard/base-types/best-practices-strings.md)をどのように、カルチャに依存した文字列を示す例については、比較が矛盾する結果を生成できます。  
  
## <a name="localization-best-practices"></a>推奨されるローカリゼーション手順  
  
1.  ローカライズ可能なすべてのリソースをリソース専用 DLL へ移動します。 ローカライズ可能リソースには、文字列、エラー メッセージ、ダイアログ ボックス、メニュー、埋め込みオブジェクト リソースなどのユーザー インターフェイス要素があります。  
  
2.  文字列やユーザー インターフェイス リソースをハードコーディングしないでください。  
  
3.  ローカライズできないリソースをリソース専用 DLL に含めないでください。 ローカライズを行う翻訳者を混乱させる原因となります。  
  
4.  文字列を実行時に連結して使う方法は避けてください。 連結される文字列は、英語の語順に依存することが多く、ほかの言語でのローカライズ作業が困難になります。  
  
5.  "Empty Folder" のように、構成要素の文法的な役割によって複数の翻訳が存在するあいまいな文字列を使用しないでください。 たとえば、"empty" は動詞または形容詞として解釈できるため、イタリア語やフランス語などの言語での翻訳結果が異なることがあります。  
  
6.  アプリケーションではテキストが含まれているイメージやアイコンを使用しないでください。 このようなイメージやアイコンのローカライズには時間と労力がかかります。  
  
7.  ユーザー インターフェイスの文字列は、表示領域に余裕がある程度の長さにしておいてください。 言語によっては、ユーザー インターフェイスが他の言語よりも 50 ～ 75% 長い領域を必要とする場合があります。  
  
8.  カルチャに基づいてリソースを取得するには、<xref:System.Resources.ResourceManager?displayProperty=nameWithType> クラスを使用します。  
  
9. 使用してローカライズできるように、Windows フォーム ダイアログ ボックスを作成する Visual Studio を使用して、 [Windows フォーム リソース エディター (Winres.exe)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md)です。 Windows フォームのダイアログ ボックスを手動でコーディングしないでください。  
  
10. 専門的なローカライズ (翻訳) 作業を計画してください。  
  
11. 作成して、リソースのローカライズの詳細については、次を参照してください。[アプリケーションのリソース](../../../docs/framework/resources/index.md)です。  
  
## <a name="globalization-best-practices-for-aspnet-applications"></a>推奨される ASP.NET アプリケーションのグローバライズ手順  
  
1.  <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> プロパティおよび <xref:System.Globalization.CultureInfo.CurrentCulture%2A> プロパティをアプリケーションで明示的に設定します。 既定値には依存しないでください。  
  
2.  ASP.NET アプリケーションはマネージ アプリケーションであり、カルチャに基づいた情報の取得、表示、および操作では、ほかのマネージ アプリケーションと同じクラスを使用できます。  
  
3.  ASP.NET では次に示す 3 種類のエンコーディングを指定できる点に注意してください。  
  
    -   requestEncoding は、クライアントのブラウザーから受信されたエンコーディングを指定します。  
  
    -   responseEncoding は、クライアント ブラウザーへ送信するエンコーディングを指定します。 ほとんどの場合、このエンコーディングは requestEncoding に指定されたエンコーディングと同一です。  
  
    -   fileEncoding は、.aspx、.asmx、.asax の各ファイルの解析の既定エンコーディングを指定します。  
  
4.  ASP.NET アプリケーション内の次の 3 か所で、requestEncoding、responseEncoding、fileEncoding、culture、uiCulture の各属性の値を指定します。  
  
    -   Web.config ファイルのグローバリゼーション セクション。 Web.config ファイルは、ASP.NET アプリケーションの外部ファイルです。 詳細については、次を参照してください。 [\<グローバリゼーション > 要素](http://msdn.microsoft.com/en-us/e2dffc8e-ebd2-439b-a2fd-e3ac5e620da7)です。  
  
    -   ページ ディレクティブ。 アプリケーションがページを処理している時点では、ファイルは既に読み取られています。 そのため、fileEncoding と requestEncoding を指定するには遅すぎます。 ページ ディレクティブでは uiCulture、Culture、および responseEncoding だけを指定できます。  
  
    -   アプリケーション コード (プログラムで指定)。 この設定は、要求ごとに変更できます。 ページ ディレクティブの場合と同様に、アプリケーション コードの処理時点では、fileEncoding と requestEncoding の指定は遅すぎます。 アプリケーション コードでは、uiCulture、Culture、および responseEncoding だけを指定できます。  
  
5.  uiCulture 値には、ブラウザー受け入れ言語を設定できます。  
  
## <a name="see-also"></a>関連項目  
 [グローバライズとローカライズ](../../../docs/standard/globalization-localization/index.md)  
 [デスクトップ アプリケーションのリソース](../../../docs/framework/resources/index.md)
