---
title: "方法 : デザイン時に ElementHost コントロールをコピーして貼り付ける"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9324a7b2634eb7a42b2dbd00814e9647e6741369
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-copy-and-paste-an-elementhost-control-at-design-time"></a>方法 : デザイン時に ElementHost コントロールをコピーして貼り付ける
この手順では、Windows フォーム上の Windows Presentation Foundation (WPF) コントロールをコピーする方法を示します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-copy-and-paste-an-elementhost-control-at-design-time"></a>コピーして、デザイン時に ElementHost コントロールを貼り付ける  
  
1.  新しい WPF 追加<xref:System.Windows.Controls.UserControl>を Windows フォーム プロジェクト。 コントロール型の既定の名前である `UserControl1.xaml` を使用します。 詳細については、次を参照してください。[チュートリアル: 新しい WPF コンテンツの作成デザイン時に Windows フォームで](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)です。  
  
2.  **プロパティ**ウィンドウで、設定の値、<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>プロパティの`UserControl1`に`200`です。  
  
3.  <xref:System.Windows.Controls.Control.Background%2A> プロパティの値を `Blue` に設定します。  
  
4.  プロジェクトをビルドします。  
  
5.  Windows フォーム デザイナーで `Form1` を開きます。  
  
6.  **ツールボックス**のインスタンスをドラッグ`UserControl1`フォーム上にします。  
  
     `UserControl1` のインスタンスは、`elementHost1` という名前の新しい <xref:System.Windows.Forms.Integration.ElementHost> コントロールでホストされます。  
  
7.  `elementHost1` を選択して、CTRL + C キーを押してクリップボードにコピーします。  
  
8.  フォーム上にコピーしたコントロールを貼り付けるには、CTRL + V キーを押します。  
  
     新しい<xref:System.Windows.Forms.Integration.ElementHost>という名前のコントロール`elementHost2`フォーム上に作成します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [チュートリアル: ElementHost コントロールの別の Windows フォームへのコピーと貼り付け](../../../../docs/framework/winforms/advanced/copy--paste-an-elementhost-control-into-forms.md)  
 [移行と相互運用性](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [WPF コントロールの使用](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [WPF デザイナー](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)
