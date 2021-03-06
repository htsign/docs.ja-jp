---
title: "例: データ バインディング時の例外の処理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd63ed96-9853-46dc-ade5-7bd1b0f39110
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 18f2d06d3a6974b913af663a38a6155b38422232
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="example-handling-exceptions-when-binding-data"></a>例: データ バインディング時の例外の処理
> [!NOTE]
>  このトピックでは、プレリリース ソフトウェアである .NET Native Developer Preview について述べています。 プレビュー版は、[Microsoft Connect Web サイト](http://go.microsoft.com/fwlink/?LinkId=394611)からダウンロードできます (登録が必要です)。  
  
 次の例は、[!INCLUDE[net_native](../../../includes/net-native-md.md)] ツール チェーンでコンパイルされたアプリがデータをバインドしようとしたときにスローされる [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) 例外の解決方法を示しています。 例外情報は次のとおりです。  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:   
App.ViewModels.MainPageVM  
```  
  
 関連付けられている呼び出し履歴は次のとおりです。  
  
```  
Reflection::Execution::ReflectionDomainSetupImplementation.CreateNonInvokabilityException+0x238  
Reflection::Core::ReflectionDomain.CreateNonInvokabilityException+0x2e  
Reflection::Core::Execution::ExecutionEnvironment.+0x316  
System::Reflection::Runtime::PropertyInfos::RuntimePropertyInfo.GetValue+0x1cb  
System::Reflection::PropertyInfo.GetValue+0x22  
System::Runtime::InteropServices::WindowsRuntime::CustomPropertyImpl.GetValue+0x42  
App!$66_Interop::McgNative.Func_IInspectable_IInspectable+0x158  
App!$66_Interop::McgNative::__vtable_Windows_UI_Xaml_Data__ICustomProperty.GetValue__STUB+0x46  
Windows_UI_Xaml!DirectUI::PropertyProviderPropertyAccess::GetValue+0x3f   
Windows_UI_Xaml!DirectUI::PropertyAccessPathStep::GetValue+0x31   
Windows_UI_Xaml!DirectUI::PropertyPathListener::ConnectPathStep+0x113  
```  
  
## <a name="what-was-the-app-doing"></a>アプリが行っていた動作は何か  
 スタックの最下位にある [Windows.UI.Xaml](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.aspx) 名前空間のフレームは、XAML レンダリング エンジンが実行されていたことを示します。   <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> メソッドの使用は、そのメタデータが削除された型での、プロパティ値のリフレクション ベースのルックアップを示します。  
  
 メタデータ ディレクティブを提供するための最初の手順は、型の `serialize` メタデータを追加して、そのプロパティすべてをアクセス可能にすることです。  
  
```xml  
<Type Name="App.ViewModels.MainPageVM" Serialize="Required Public" />  
```  
  
## <a name="is-this-an-isolated-case"></a>特殊なケースかどうか  
 このシナリオでは、ある `ViewModel` について、データ バインディングに不完全なメタデータが含まれる場合、他のものにも同じことが該当する可能性があります。  アプリのビュー モデルがすべて `App.ViewModels` 名前空間内にあるようにコードが作成されている場合、より一般的なランタイム ディレクティブを使用できます。  
  
```xml  
<Namespace Name="App.ViewModels " Serialize="Required Public" />  
```  
  
## <a name="could-the-code-be-rewritten-to-not-use-reflection"></a>リフレクションを使用しないようにコードを書き換えることができるか  
 データ バインディングではリフレクションが多用されるため、リフレクションを使用しないようにコードを変更することはできません。  
  
 ただし、`ViewModel` を XAML ページに指定して、ツール チェーンがコンパイル時にプロパティ バインディングを正しい型に関連付けて、ランタイム ディレクティブを使用せずにメタデータを保持できるようにする方法はあります。  たとえば、プロパティに [Windows.UI.Xaml.Data.BindableAttribute](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.data.bindableattribute.aspx) 属性を適用できます。 これにより、XAML コンパイラが必要なルックアップ情報を生成するようになり、Default.rd.xml ファイルのランタイム ディレクティブが不要になります。  
  
## <a name="see-also"></a>関連項目  
 [はじめに](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [例: 動的プログラミングのトラブルシューティング](../../../docs/framework/net-native/example-troubleshooting-dynamic-programming.md)
