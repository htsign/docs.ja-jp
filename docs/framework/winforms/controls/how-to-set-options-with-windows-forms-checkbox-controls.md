---
title: "方法 : Windows フォームの CheckBox コントロールでオプションを設定する"
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
- cpp
f1_keywords: checked
helpviewer_keywords:
- CheckBox control [Windows Forms], checked state
- check boxes [Windows Forms], using to set options
- CheckBox control [Windows Forms], using to set options
ms.assetid: 2ac70498-7e3e-4e07-8901-ccabaeb5fd3e
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8b7d3ddb090488f6503c0765f6054308c28d4ab9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-options-with-windows-forms-checkbox-controls"></a>方法 : Windows フォームの CheckBox コントロールでオプションを設定する
Windows フォーム<xref:System.Windows.Forms.CheckBox>コントロールは、True または False をユーザーに提供するために使用またははい/いいえオプションします。 コントロールを選択すると、チェック マークが表示されます。  
  
### <a name="to-set-options-with-checkbox-controls"></a>CheckBox コントロールでオプションを設定するには  
  
1.  値を調べて、<xref:System.Windows.Forms.CheckBox.Checked%2A>状態を判断し、その値を使用してオプションを設定するプロパティです。  
  
     下、ときにコード サンプルでは、<xref:System.Windows.Forms.CheckBox>コントロールの<xref:System.Windows.Forms.CheckBox.CheckedChanged>イベントが発生すると、フォームの<xref:System.Windows.Forms.Control.AllowDrop%2A>プロパティに設定されている`false`チェック ボックスをオンにした場合。 これは、ユーザーの操作を制限する場合に便利です。  
  
    ```vb  
    Private Sub CheckBox1_CheckedChanged(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles CheckBox1.CheckedChanged  
       ' Determine the CheckState of the check box.  
       If CheckBox1.CheckState = CheckState.Checked Then  
          ' If checked, do not allow items to be dragged onto the form.  
          Me.AllowDrop = False  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void checkBox1_CheckedChanged(object sender, System.EventArgs e)  
    {  
       // Determine the CheckState of the check box.  
       if (checkBox1.CheckState == CheckState.Checked)   
       {  
          // If checked, do not allow items to be dragged onto the form.  
          this.AllowDrop = false;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // Determine the CheckState of the check box.  
          if (checkBox1->CheckState == CheckState::Checked)   
          {  
             // If checked, do not allow items to be dragged onto the form.  
             this->AllowDrop = false;  
          }  
       }  
    ```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.CheckBox>  
 [CheckBox コントロールの概要](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)  
 [方法: Windows フォームの CheckBox のクリックに応答する](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-checkbox-clicks.md)  
 [CheckBox コントロール](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)
