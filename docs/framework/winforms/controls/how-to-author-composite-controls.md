---
title: "方法 : 複合コントロールを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UserControl class [Windows Forms], creating composite controls
- user controls [Windows Forms], creating
- user controls [Windows Forms], inheriting from
- composite controls [Windows Forms], creating
ms.assetid: 79c9cf05-5ab6-4a18-886d-88a64748b098
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 72c68568f0178956d6154f0b3a070e69b6ff0502
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-author-composite-controls"></a>方法 : 複合コントロールを作成する
複合コントロールはさまざまな方法で使用できます。 Windows デスクトップ アプリケーション プロジェクトの一部として複合コントロールを作成し、プロジェクト内のフォーム上でのみ使用することができます。 または、Windows コントロール ライブラリ プロジェクトで複合コントロールを作成し、プロジェクトをアセンブリにコンパイルして、他のプロジェクトで使用することもできます。 そのコントロールから継承することや、ビジュアル継承を使用して特殊な用途のために簡単にカスタマイズすることまでできます。  
  
> [!NOTE]
>  Web フォームで使用する複合コントロールを作成する場合は、「[カスタム ASP.NET サーバー コントロールの開発](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef)」を参照してください。  
>   
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-author-a-composite-control"></a>複合コントロールを作成するには  
  
1.  `DemoControlHost` という新しい **Windows アプリケーション** プロジェクトを開きます。  
  
2.  **[プロジェクト]** メニューの **[ユーザー コントロールの追加]**をクリックします。  
  
3.  **[新しい項目の追加]** ダイアログ ボックスで、クラス ファイル (.vb または .cs ファイル) に複合コントロールに付ける名前を指定します。  
  
4.  **[追加]** をクリックして、複合コントロールのクラス ファイルを作成します。  
  
5.  複合コントロールのサーフェスに **[ツールボックス]** からコントロールを追加します。  
  
6.  複合コントロールまたはその内在コントロールによって発生したイベントを処理するために、イベント プロシージャにコードを配置します。  
  
7.  複合コントロールのデザイナーを閉じて、メッセージが表示されたらファイルを保存します。  
  
8.  **[ビルド]** メニューの **[ソリューションのビルド]**をクリックします。  
  
     カスタム コントロールが **[ツールボックス]** に表示されるようにプロジェクトをビルドする必要があります。  
  
9. **[ツールボックス]** の **[DemoControlHost]** タブを使用して、コントロールのインスタンスを `Form1` に追加します。  
  
### <a name="to-author-a-control-class-library"></a>コントロール クラス ライブラリを作成するには  
  
1.  新しい **Windows コントロール ライブラリ** プロジェクトを開きます。  
  
     既定では、プロジェクトに複合コントロールが含まれます。  
  
2.  上記の手順の説明に従ってコントロールとコードを追加します。  
  
3.  継承クラスで変更しないコントロールを選択して、このコントロールの **Modifiers** プロパティを **Private** に設定します。  
  
4.  DLL をビルドします。  
  
### <a name="to-inherit-from-a-composite-control-in-a-control-class-library"></a>コントロール クラス ライブラリの複合コントロールから継承するには  
  
1.  **[ファイル]** メニューで、**[追加]** をポイントし、**[新しいプロジェクト]** を選択して、新しい **Windows アプリケーション** プロジェクトをソリューションに追加します。  
  
2.  **ソリューション エクスプローラー**で、新しいプロジェクトの **[参照設定]** フォルダーを右クリックし、**[参照の追加]** をクリックして **[参照の追加]** ダイアログ ボックスを開きます。  
  
3.  **[プロジェクト]** タブを選択し、コントロール ライブラリ プロジェクトをダブルクリックします。  
  
4.  **[ビルド]** メニューの **[ソリューションのビルド]**をクリックします。  
  
5.  **ソリューション エクスプローラー**で、コントロール ライブラリ プロジェクトを右クリックし、ショートカット メニューの **[新しい項目の追加]** をクリックします。  
  
6.  **[新しい項目の追加]** ダイアログ ボックスの **[継承されたユーザー コントロール]** テンプレートを選択します。  
  
7.  **[継承ピッカー]** ダイアログ ボックスで、継承元のコントロールをダブルクリックします。  
  
     新しいコントロールがプロジェクトに追加されます。  
  
8.  新しいコントロールのビジュアル デザイナーを開き、別の内在コントロールを追加します。  
  
     DLL の複合コントロールから継承された内在コントロールを表示し、**Modifiers** プロパティが **Public** であるコントロールのプロパティを変更することができます。 **Modifiers** プロパティが **Private** であるコントロールのプロパティを変更することはできません。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: Visual Basic による複合コントロールの作成](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [チュートリアル: Visual C# による複合コントロールの作成](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 [チュートリアル: Visual Basic による Windows フォーム コントロールからの継承](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 [チュートリアル: Visual C# による Windows フォーム コントロールからの継承](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 [コントロールの種類に関するアドバイス](../../../../docs/framework/winforms/controls/control-type-recommendations.md)  
 [方法: Windows フォームのコントロールを作成する](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [さまざまなカスタム コントロール](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
