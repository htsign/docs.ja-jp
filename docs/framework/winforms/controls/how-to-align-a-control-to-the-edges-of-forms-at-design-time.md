---
title: "方法 : デザイン時にフォームの端に合わせてコントロールを配置する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], docking using designer
- Dock property [Windows Forms], aligning controls (using designer)
ms.assetid: 51f08998-5e3b-4330-be58-a4edd0eb60f4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 86134902a6645d2c9bf7bcef2cf93bf543d8c9bc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-align-a-control-to-the-edges-of-forms-at-design-time"></a>方法 : デザイン時にフォームの端に合わせてコントロールを配置する
コントロールを設定して、フォームの端に合わせて調整を行うことができます、<xref:System.Windows.Forms.Control.Dock%2A>です。 このプロパティは、フォーム内のコントロールの場所を指定します。 <xref:System.Windows.Forms.Control.Dock%2A> プロパティには次の値のいずれかを設定できます。  
  
|設定|コントロールへの影響|  
|-------------|----------------------------|  
|<xref:System.Windows.Forms.DockStyle.Bottom>|フォームの下部にドッキングします。|  
|<xref:System.Windows.Forms.DockStyle.Fill>|フォームの残りの全スペースを埋めます。|  
|<xref:System.Windows.Forms.DockStyle.Left>|フォームの左側にドッキングします。|  
|<xref:System.Windows.Forms.DockStyle.None>|指定された場所に表示されますどこにもドッキングせず、<xref:System.Windows.Forms.Control.Location%2A>です。|  
|<xref:System.Windows.Forms.DockStyle.Right>|フォームの右側にドッキングします。|  
|<xref:System.Windows.Forms.DockStyle.Top>|フォームの上部にドッキングします。|  
  
 これらの値は、コードでも設定できます。 詳細については、次を参照してください。[する方法: コントロールをフォームの端を揃える](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md)です。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-set-the-dock-property-for-your-control-at-design-time"></a>デザイン時に、コントロールの Dock プロパティを設定するには  
  
1.  Windows フォーム デザイナーでコントロールを選択します。  
  
2.  **プロパティ**ウィンドウで、ドロップダウン リスト ボックスには、[次へ] をクリック、<xref:System.Windows.Forms.Control.Dock%2A>プロパティです。  
  
     6 つを表すグラフィカル インターフェイス<xref:System.Windows.Forms.Control.Dock%2A>設定が表示されます。  
  
3.  適切な設定を選択します。  
  
4.  コントロールの設定で指定された方法でドッキングされます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>  
 [方法: フォームの端に合わせてコントロールを配置する](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md)  
 [チュートリアル: スナップ線を使用した Windows フォーム上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [方法: Windows フォームにコントロールを固定する](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)  
 [方法: TableLayoutPanel コントロールで子コントロールを固定およびドッキングする](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [方法: FlowLayoutPanel コントロールで子コントロールを固定およびドッキングする](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)  
 [チュートリアル: TableLayoutPanel を使用した Windows フォーム上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [チュートリアル: FlowLayoutPanel を使用した Windows フォーム上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [デザイン時の Windows フォーム コントロールの開発](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)
