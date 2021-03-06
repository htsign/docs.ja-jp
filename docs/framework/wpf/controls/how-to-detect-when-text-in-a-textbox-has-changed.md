---
title: "方法 : TextBox のテキストがいつ変更されたかを検出する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 92fc8995ab75cc25bac3bb21b1646052822c3721
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a>方法 : TextBox のテキストがいつ変更されたかを検出する
この例を使用する方法を示しています、<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>イベント メソッドを実行するたびに内のテキスト、<xref:System.Windows.Controls.TextBox>コントロールが変更されました。  
  
 分離コード クラスで、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を格納している、<xref:System.Windows.Controls.TextBox>変更については、監視するコントロールを挿入するたびに呼び出すメソッドを<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>イベントが発生します。  このメソッドのシグネチャが一致で期待される必要があります、<xref:System.Windows.Controls.TextChangedEventHandler>を委任します。  
  
 イベント ハンドラーが呼び出されるとされるたびの内容、<xref:System.Windows.Controls.TextBox>ユーザー、またはプログラムによってコントロールを変更します。  
  
 **注:**このイベントが発生したときに、<xref:System.Windows.Controls.TextBox>コントロールが作成し、最初にテキストを格納します。  
  
## <a name="example"></a>例  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]を定義する、<xref:System.Windows.Controls.TextBox>コントロールを指定、<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>の属性をイベント ハンドラー メソッドの名前に一致する値。  
  
 [!code-xaml[TextBox_MiscCode#_TextChangedXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]  
  
## <a name="example"></a>例  
 分離コード クラスで、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を格納している、<xref:System.Windows.Controls.TextBox>変更については、監視するコントロールを挿入するたびに呼び出すメソッドを<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>イベントが発生します。  このメソッドのシグネチャが一致で期待される必要があります、<xref:System.Windows.Controls.TextChangedEventHandler>を委任します。  
  
 [!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
 [!code-vb[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]  
  
 イベント ハンドラーが呼び出されるとされるたびの内容、<xref:System.Windows.Controls.TextBox>ユーザー、またはプログラムによってコントロールを変更します。  
  
 **注:**このイベントが発生したときに、<xref:System.Windows.Controls.TextBox>コントロールが作成し、最初にテキストを格納します。  
  
 コメント  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.TextChangedEventArgs>  
 [TextBox の概要](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox の概要](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
