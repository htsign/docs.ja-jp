---
title: "UI オートメーション クライアントにおけるキャッシュ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation caching in clients
- caching, UI Automation clients
ms.assetid: 94c15031-4975-43cc-bcd5-c9439ed21c9c
caps.latest.revision: "24"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 3cdbf82997d76def39f05ebf06b448e8e75001ac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="caching-in-ui-automation-clients"></a>UI オートメーション クライアントにおけるキャッシュ
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。  
  
 このトピックでは、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] のプロパティとコントロール パターンのキャッシュについて説明します。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]では、キャッシュとはデータをプリフェッチすることを意味します。 そのデータには、さらにプロセス間通信を行わずにアクセスできます。 キャッシュは通常、UI オートメーション クライアント アプリケーションによって使用され、プロパティとコントロール パターンを一括で取得します。 それから、必要に応じて情報がキャッシュから取得されます。 アプリケーションはキャッシュを定期的に更新します。通常は、 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] で何かが変更されたことを示すイベントへの応答として更新を行います。  
  
 キャッシュの効果は、サーバー側 UI オートメーション プロバイダーを持つ [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)] コントロールとカスタム コントロールで最も顕著に表れます。 [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] コントロールの既定のプロバイダーなど、クライアント側プロバイダーにアクセスするときは、メリットは小さくなります。  
  
 キャッシュはアプリケーションが <xref:System.Windows.Automation.CacheRequest> をアクティブにしたときに発生し、 <xref:System.Windows.Automation.AutomationElement>や <xref:System.Windows.Automation.AutomationElement.FindFirst%2A>など、 <xref:System.Windows.Automation.AutomationElement.FindAll%2A>を返すメソッドやプロパティを使用します。 メソッド、<xref:System.Windows.Automation.TreeWalker>クラスは、例外以外の場合にのみ実行は、キャッシュ、<xref:System.Windows.Automation.CacheRequest>をパラメーターとして指定された (たとえば、<xref:System.Windows.Automation.TreeWalker.GetFirstChild%28System.Windows.Automation.AutomationElement%2CSystem.Windows.Automation.CacheRequest%29?displayProperty=nameWithType>です。  
  
 また、キャッシュは、 <xref:System.Windows.Automation.CacheRequest> がアクティブなときにイベントにサブスクライブする場合にも発生します。 イベントのソースとしてイベント ハンドラーに渡された <xref:System.Windows.Automation.AutomationElement> には、元の <xref:System.Windows.Automation.CacheRequest>によって指定されているキャッシュされたプロパティとパターンが含まれています。 イベントにサブスクライブした後で <xref:System.Windows.Automation.CacheRequest> に加えられた変更が、影響を与えることはありません。  
  
 要素の [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] プロパティとコントロール パターンはキャッシュすることができます。  
  
<a name="Options_for_Caching"></a>   
## <a name="options-for-caching"></a>キャッシュのオプション  
 <xref:System.Windows.Automation.CacheRequest> はキャッシュ用の次のオプションを指定します。  
  
<a name="Properties_to_Cache"></a>   
### <a name="properties-to-cache"></a>キャッシュするプロパティ  
 要求をアクティブ化する前に、各プロパティの <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationProperty%29> を呼び出して、キャッシュするプロパティを指定できます。  
  
<a name="Control_Patterns_to_Cache"></a>   
### <a name="control-patterns-to-cache"></a>キャッシュするコントロール パターン  
 要求をアクティブ化する前に、各パターンの <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationPattern%29> を呼び出して、キャッシュするコントロール パターンを指定できます。 パターンがキャッシュされると、そのプロパティは自動的にキャッシュされません。使用して、キャッシュ プロパティを指定する必要があります<xref:System.Windows.Automation.CacheRequest.Add%2A?displayProperty=nameWithType>です。  
  
<a name="Scope_of_the_Caching"></a>   
### <a name="scope-and-filtering-of-caching"></a>キャッシュのスコープとフィルター処理  
 プロパティや設定をキャッシュ パターンを持つ要素を指定することができます、<xref:System.Windows.Automation.CacheRequest.TreeScope%2A?displayProperty=nameWithType>要求をアクティブ化する前にプロパティです。 スコープは、要求がアクティブな間に取得される要素を基準としています。 たとえば、 <xref:System.Windows.Automation.TreeScope.Children>のみを設定し、 <xref:System.Windows.Automation.AutomationElement>を取得する場合に、要素の子のプロパティとパターンはキャッシュされますが、要素自体のプロパティとパターンはキャッシュされません。 取得される要素自体についてキャッシュが行われるようにするには、 <xref:System.Windows.Automation.TreeScope.Element> プロパティに <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> を含める必要があります。 スコープを <xref:System.Windows.Automation.TreeScope.Parent> または <xref:System.Windows.Automation.TreeScope.Ancestors>に設定することはできません。 ただし、子要素がキャッシュされると親要素をキャッシュできます。このトピックの「キャッシュされた子と親の取得」を参照してください。  
  
 キャッシュの範囲がによっても影響を受ける、<xref:System.Windows.Automation.CacheRequest.TreeFilter%2A?displayProperty=nameWithType>プロパティです。 既定では、キャッシュは [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーのコントロール ビューに表示される要素にのみ実行されます。 ただし、キャッシュをすべての要素に適用したり、コンテンツ ビューに表示される要素にのみ適用したりするように、このプロパティを変更することができます。  
  
<a name="Strength_of_the_Element_References"></a>   
### <a name="strength-of-the-element-references"></a>要素の参照の強度  
 <xref:System.Windows.Automation.AutomationElement>を取得するときは、既定では、キャッシュされていないものも含め、その要素のすべてのプロパティとパターンにアクセスできます。 ただし、作業効率を向上するために、 <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> の <xref:System.Windows.Automation.CacheRequest> プロパティを <xref:System.Windows.Automation.AutomationElementMode.None>に設定して、要素への参照がキャッシュされたデータのみを参照するよう指定できます。 この場合、取得された要素のキャッシュされていないプロパティとパターンには、いずれもアクセスできません。 つまり、 <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> を通してプロパティにアクセスしたり、 `Current` の <xref:System.Windows.Automation.AutomationElement> プロパティやコントロール パターンにアクセスすることはできません。また、 <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> や <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>を使用してパターンを取得することもできません。 キャッシュされたパターンで、ように配列のプロパティを取得するメソッドを呼び出すことができます<xref:System.Windows.Automation.SelectionPattern.SelectionPatternInformation.GetSelection%2A?displayProperty=nameWithType>、not などのコントロールで、アクションを実行するが、<xref:System.Windows.Automation.InvokePattern.Invoke%2A?displayProperty=nameWithType>です。  
  
 オブジェクトへの完全参照を必要としない可能性があるアプリケーションの例として、スクリーン リーダーがあります。これは、ウィンドウ内の要素の <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> プロパティと <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> プロパティをプリフェッチしても、 <xref:System.Windows.Automation.AutomationElement> オブジェクト自体は必要としません。  
  
<a name="Activating_the_CacheRequest"></a>   
## <a name="activating-the-cacherequest"></a>CacheRequest のアクティブ化  
 <xref:System.Windows.Automation.AutomationElement> が現在のスレッドに対してアクティブである間に <xref:System.Windows.Automation.CacheRequest> オブジェクトが取得された場合にのみ、キャッシュが実行されます。 <xref:System.Windows.Automation.CacheRequest>をアクティブ化するには、2 つの方法があります。  
  
 通常の方法では、 <xref:System.Windows.Automation.CacheRequest.Activate%2A>を呼び出します。 このメソッドは、 <xref:System.IDisposable>を実装するオブジェクトを返します。 要求は、 <xref:System.IDisposable> オブジェクトが存在する限りアクティブなままです。 オブジェクトの有効期間を制御する最も簡単な方法は、 `using` ([!INCLUDE[TLA#tla_cshrp](../../../includes/tlasharptla-cshrp-md.md)]) または `Using` ([!INCLUDE[TLA2#tla_visualb](../../../includes/tla2sharptla-visualb-md.md)]) のブロック内に呼び出しを埋め込むことです。 これにより、例外が発生した場合でも、スタックから要求がポップされます。  
  
 キャッシュ要求を入れ子にする場合に有用な別の方法は、 <xref:System.Windows.Automation.CacheRequest.Push%2A>を呼び出すことです。 この方法では、スタック上に要求が配置され、アクティブ化されます。 <xref:System.Windows.Automation.CacheRequest.Pop%2A>によってスタックから削除されるまで、要求はアクティブなままです。 別の要求がスタックにプッシュされた場合、要求は一時的に非アクティブになります。スタックの最上位の要求のみがアクティブになります。  
  
<a name="Retrieving_Cached_Properties"></a>   
## <a name="retrieving-cached-properties"></a>キャッシュされたプロパティの取得  
 要素のキャッシュされたプロパティを取得するには、次のメソッドとプロパティを使用します。  
  
-   <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.Cached%2A>  
  
 要求されたプロパティがキャッシュ内にない場合、例外が発生します。  
  
 <xref:System.Windows.Automation.AutomationElement.Cached%2A>と同様、 <xref:System.Windows.Automation.AutomationElement.Current%2A>は構造体のメンバーとして、個々のプロパティを公開します。 ただし、この構造体を取得する必要はありません。個々のプロパティに直接アクセスすることができます。 たとえば、 <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> プロパティは `element.Cached.Name`から取得できます。ここで、 `element` は <xref:System.Windows.Automation.AutomationElement>です。  
  
<a name="Retrieving_Cached_Control_Patterns"></a>   
## <a name="retrieving-cached-control-patterns"></a>キャッシュされたコントロール パターンの取得  
 要素のキャッシュされたコントロール パターンを取得するには、次のメソッドを使用します。  
  
-   <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A>  
  
 パターンがキャッシュ内にない場合、 <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> で例外が発生し、 <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> が `false`を返します。  
  
 パターン オブジェクトの `Cached` プロパティを使用して、コントロール パターンのキャッシュされたプロパティを取得できます。 `Current` プロパティを通じて現在の値を取得することもできますが、 <xref:System.Windows.Automation.AutomationElementMode.None> が取得されたときに <xref:System.Windows.Automation.AutomationElement> が指定されていない場合に限ります。 (<xref:System.Windows.Automation.AutomationElementMode.Full> は既定値であり、これにより現在の値へのアクセスが許可されます。)  
  
<a name="Retrieving_Cached_Children_and_Parents"></a>   
## <a name="retrieving-cached-children-and-parents"></a>キャッシュされた子と親の取得  
 <xref:System.Windows.Automation.AutomationElement> を取得し、要求の <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> プロパティを通じてその要素の子のキャッシュを要求すると、その後は、取得した要素の <xref:System.Windows.Automation.AutomationElement.CachedChildren%2A> プロパティから子要素を取得することが可能になります。  
  
 <xref:System.Windows.Automation.TreeScope.Element> がキャッシュ要求のスコープに含まれていた場合には、要求のルート要素は、その後、任意の子要素の <xref:System.Windows.Automation.AutomationElement.CachedParent%2A> プロパティから利用できます。  
  
> [!NOTE]
>  要求のルート要素の親または先祖をキャッシュすることはできません。  
  
<a name="Updating_the_Cache"></a>   
## <a name="updating-the-cache"></a>キャッシュの更新  
 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]で何も変更されない限り、キャッシュは有効です。 キャッシュの更新は、通常はイベントへの応答として、アプリケーションが行います。  
  
 <xref:System.Windows.Automation.CacheRequest> がアクティブな間にイベントにサブスクライブすると、イベント ハンドラーのデリゲートが呼び出されるたびに、イベントのソースとしてキャッシュが更新された <xref:System.Windows.Automation.AutomationElement> を取得します。 また、 <xref:System.Windows.Automation.AutomationElement.GetUpdatedCache%2A>を呼び出して、要素のキャッシュされた情報を更新することもできます。 元の <xref:System.Windows.Automation.CacheRequest> を渡して、以前にキャッシュされたすべての情報を更新できます。  
  
 キャッシュを更新しても、既存の <xref:System.Windows.Automation.AutomationElement> の参照のプロパティはいずれも変更されません。  
  
## <a name="see-also"></a>関連項目  
 [クライアントの UI オートメーション イベント](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md)  
 [UI オートメーションにおけるキャッシュを使用します。](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)  
 [FetchTimer サンプル](http://msdn.microsoft.com/en-us/5b7d3294-de22-4f24-b2d6-d4785a304b90)
