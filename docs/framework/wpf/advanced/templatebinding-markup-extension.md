---
title: "TemplateBinding のマークアップ拡張機能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TemplateBinding
- TemplateBindingExtension
helpviewer_keywords:
- XAML [WPF], TemplateBinding markup extension
- TemplateBinding markup extensions [WPF]
ms.assetid: 1d25bbfc-dbc2-499d-9f12-419d23d4ac6a
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5ab8645de78a79f4bd47fa436699af002db99b9b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="templatebinding-markup-extension"></a>TemplateBinding のマークアップ拡張機能
コントロール テンプレート内のプロパティの値を、template 宣言されたコントロールの別のプロパティの値にリンクします。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xml  
<object property="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-attribute-usage-for-setter-property-in-template-or-style"></a>XAML 属性の使用方法 (テンプレートまたはスタイルの Setter プロパティの場合)  
  
```xml  
<Setter Property="propertyName" Value="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`propertyName`|Setter 構文で設定されるプロパティの <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>。|  
|`sourceProperty`|template 宣言された型に存在する、<xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType> によって指定された別の依存関係プロパティ。<br /><br /> または<br /><br /> template 宣言された対象の型とは異なる型で定義されている "ドットダウン" プロパティ名。 これは、実際には <xref:System.Windows.PropertyPath> です。 参照してください[PropertyPath XAML 構文](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md)です。|  
  
## <a name="remarks"></a>コメント  
 A`TemplateBinding`の最適化された形式は、[バインド](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)テンプレートのシナリオでに似ています、`Binding`で構築された`{Binding RelativeSource={RelativeSource TemplatedParent}}`です。 関連するプロパティが既定で双方向のバインディングの場合でも、`TemplateBinding` は常に一方向のバインディングです。 関連する両方のプロパティは、依存関係プロパティである必要があります。  
  
 [RelativeSource](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md)はと共に、またはの代わりに使用する他のマークアップ拡張機能は、`TemplateBinding`テンプレート内の相対プロパティ バインディングを実行するためにします。  
  
 コントロール テンプレートを説明する概念としてはここでは含まれていません。詳細については、次を参照してください。[コントロールのスタイルとテンプレート](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)です。  
  
 属性構文は、このマークアップ拡張機能で使用される最も一般的な構文です。 `TemplateBinding` 識別子文字列の後に設定される文字列トークンは、基になる <xref:System.Windows.TemplateBindingExtension.Property%2A> 拡張クラスの <xref:System.Windows.TemplateBindingExtension> 値として割り当てられます。  
  
 オブジェクト要素構文を使用することもできますが、現実的な用途がないためここでは触れません。 `TemplateBinding` は、評価された式を使用して setter 内で値を埋め込むために使用され、`TemplateBinding` を使用する場合、TemplateBinding が `<Setter.Property>` プロパティ要素構文を埋め込むためのオブジェクト要素構文は、必要以上に詳細です。  
  
 `TemplateBinding` は、<xref:System.Windows.TemplateBindingExtension.Property%2A> プロパティをプロパティおよび値のペアとして指定する詳細出力属性使用でも使用できます。  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" .../>  
```  
  
 詳細出力の使用は、複数の設定可能プロパティを持つ拡張機能や、一部のプロパティがオプションである場合に役立ちます。 `TemplateBinding` には、必須の設定可能プロパティが 1 つしか存在しないため、このような詳細出力の使用は一般的ではありません。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML プロセッサの実装でこのマークアップ拡張機能の処理が定義されている、<xref:System.Windows.TemplateBindingExtension>クラスです。  
  
 `TemplateBinding` はマークアップ拡張機能です。 一般にマークアップ拡張機能を実装するのは、属性値をリテラル値やハンドラー名以外にエスケープする要件が存在し、その要件の適用範囲がグローバルで、特定の型やプロパティに型コンバーターを適用するだけにとどまらない場合です。 XAML の使用中のすべてのマークアップ拡張機能、`{`と`}`マークアップ拡張機能が、属性を処理する必要がありますを XAML プロセッサが認識する規則は、それぞれの属性構文内の文字です。 詳細については、次を参照してください。[マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Style>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [XAML の概要 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [RelativeSource のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md)  
 [バインドのマークアップ拡張機能](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)
