---
title: "方法 : Windows フォーム BindingNavigator コントロールを使用してデータ間を移動する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingNavigator control [Windows Forms], navigating data
- data [Windows Forms], navigating
- data navigation
- examples [Windows Forms], BindingNavigator control
ms.assetid: 0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 08b9fb555966cf8459646a12da69c6db3361f0b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-navigate-data-with-the-windows-forms-bindingnavigator-control"></a>方法 : Windows フォーム BindingNavigator コントロールを使用してデータ間を移動する
Windows フォームに <xref:System.Windows.Forms.BindingNavigator> コントロールが登場したことで、開発者はエンドユーザーに、作成したフォームにおける単純なデータ移動および操作のためのユーザー インターフェイスを提供できるようになります。  
  
 <xref:System.Windows.Forms.BindingNavigator> コントロールは、データセットの最初、最後、次、前のレコードへの移動が構成済みのボタンや、レコードを追加および削除するためのボタンを持つ <xref:System.Windows.Forms.ToolStrip> コントロールです。 <xref:System.Windows.Forms.BindingNavigator> コントロールへのボタンの追加は、<xref:System.Windows.Forms.ToolStrip> コントロールなので簡単です。  「[方法 : Windows フォーム BindingNavigator コントロールに [Load]、[Save]、[Cancel] の各ボタンを追加する](http://msdn.microsoft.com/library/safa4957\(v=vs.110\))」も参照してください。  
  
 <xref:System.Windows.Forms.BindingNavigator> コントロールの各ボタンについて、同じ機能をプログラムで許可する <xref:System.Windows.Forms.BindingSource> コンポーネントの対応するメンバーが存在します。 たとえば、<xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> ボタンは <xref:System.Windows.Forms.BindingSource> コンポーネントの <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> メソッドに対応し、<xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> ボタンは <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> メソッドに対応します。 その結果、データ レコード間を移動する <xref:System.Windows.Forms.BindingNavigator> コントロールを有効にするために必要なのは、<xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> プロパティをフォームの適切な <xref:System.Windows.Forms.BindingSource> コンポーネントに設定するだけです。  
  
### <a name="to-set-up-the-bindingnavigator-control"></a>BindingNavigator コントロールを設定するには  
  
1.  `bindingSource1` という名前の <xref:System.Windows.Forms.BindingSource> コンポーネントを 1 つ、`textBox1` と `textBox2` という名前の <xref:System.Windows.Forms.TextBox> コントロールを 2 つ追加します。  
  
2.  `bindingSource1` をデータにバインドし、テキスト ボックス コントロールを `bindingSource1` にバインドします。 そのためには、以下のコードをフォームに貼り付け、フォームのコンストラクターまたは <xref:System.Windows.Forms.Form.Load> イベント処理メソッドから `LoadData` を呼び出します。  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#2)]  
  
3.  `bindingNavigator1` という名前の <xref:System.Windows.Forms.BindingNavigator> コントロールをフォームに追加します。  
  
4.  `bindingNavigator1` の <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> プロパティを `bindingSource1` に設定します。 これは、デザイナーを使用して、またはコード内で実行できます。  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#3)]  
  
## <a name="example"></a>例  
 次のコード例は、これまで説明した手順の完全な例です。  
  
 [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System、System.Data、System.Drawing、System.Windows.Forms、および System.Xml アセンブリへの参照。  
  
 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] のコマンド ラインからこの例をビルドする方法については、「[コマンド ラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)」または「[csc.exe を使用したコマンド ラインからのビルド](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。 また、コードを新しいプロジェクトに貼り付けることにより、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。  「[方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.BindingNavigator>  
 [BindingNavigator コントロール](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [ToolStrip コントロール](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
