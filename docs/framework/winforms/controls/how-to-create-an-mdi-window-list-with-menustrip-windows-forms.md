---
title: "方法 : MenuStrip を使用して MDI ウィンドウの一覧を作成する (Windows フォーム)"
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
- MDI [Windows Forms], creating window lists
- MenuStrip control [Windows Forms], creating window lists
ms.assetid: 04fb414b-811f-4a83-aab6-b4a24646dec5
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ea2b3f41e6e40b589589db99bb2a5a0ba474c8cb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-an-mdi-window-list-with-menustrip-windows-forms"></a>方法 : MenuStrip を使用して MDI ウィンドウの一覧を作成する (Windows フォーム)
マルチ ドキュメント インターフェイス (MDI) を使用して、同じ時およびコピーに複数のドキュメントを開くし、他の 1 つのドキュメントのコンテンツを貼り付けることができますアプリケーションを作成します。  
  
 この手順では、親のウィンドウ メニュー上のすべてのアクティブな子フォームの一覧を作成する方法を示します。  
  
### <a name="to-create-an-mdi-window-list-on-a-menustrip"></a>MenuStrip を MDI ウィンドウ リストを作成するには  
  
1.  フォームを作成し、その <xref:System.Windows.Forms.Form.IsMdiContainer%2A> プロパティを `true` に設定します。  
  
2.  フォームに <xref:System.Windows.Forms.MenuStrip> を追加します。  
  
3.  2 つのトップレベルのメニュー項目を追加、<xref:System.Windows.Forms.MenuStrip>設定とその<xref:System.Windows.Forms.Control.Text%2A>プロパティ`&File`と`&Window`です。  
  
4.  サブメニュー項目を `&File` メニュー項目に追加し、その <xref:System.Windows.Forms.ToolStripItem.Text%2A> プロパティを「`&Open`」に設定します。  
  
5.  設定、<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>のプロパティ、<xref:System.Windows.Forms.MenuStrip>を`&Window`<xref:System.Windows.Forms.ToolStripMenuItem>です。  
  
6.  プロジェクトにフォームを追加し、目的のコントロールを追加し、別など<xref:System.Windows.Forms.MenuStrip>です。  
  
7.  <xref:System.Windows.Forms.ToolStripMenuItem> の `&New` の <xref:System.Windows.Forms.Control.Click> イベントにイベント ハンドラーを作成します。  
  
8.  イベント ハンドラー内で作成しの新しいインスタンスを表示するには、次のようなコードを挿入`Form2`の MDI 子フォームとして`Form1`です。  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As _  
    System.Object, ByVal e As System.EventArgs) Handles _  
    openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
    ```  
  
    ```csharp  
    private void newToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
    ```  
  
9. 配置では、次のようなコード、 `&New` <xref:System.Windows.Forms.ToolStripMenuItem>イベント ハンドラーを登録します。  
  
    ```vb  
    Private Sub newToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles newToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.newToolStripMenuItem.Click += new System.EventHandler(this.newToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   `Form1` と `Form2` という名前の 2 つの <xref:System.Windows.Forms.Form> コントロール。  
  
-   `Form1` 上の `menuStrip1` という名前の <xref:System.Windows.Forms.MenuStrip> コントロールと、`Form2` 上の `menuStrip2` という名前の <xref:System.Windows.Forms.MenuStrip> コントロール。  
  
-   <xref:System?displayProperty=nameWithType> アセンブリおよび <xref:System.Windows.Forms?displayProperty=nameWithType> アセンブリへの参照。  
  
## <a name="see-also"></a>関連項目  
 [方法: MDI 親フォームを作成する](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [方法: MDI 子フォームを作成する](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [MenuStrip コントロール](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
