---
title: "-optimize (C# コンパイラ オプション)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /optimize
helpviewer_keywords:
- /optimize compiler option [C#]
- -o compiler option [C#]
- optimize compiler option [C#]
- /o compiler option [C#]
- -optimize compiler option [C#]
- compiler optimization [C#]
- o compiler option [C#]
ms.assetid: 6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d74a338336d5878cb8d6f212076bb9f1eb7ef768
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="optimize-c-compiler-options"></a>/optimize (C# コンパイラ オプション)
**/optimize** オプションは、コンパイラで実行する最適化を有効または無効にします。最適化を実行すると、出力ファイルのサイズが小さくなり、速度と効率が向上します。  
  
## <a name="syntax"></a>構文  
  
```console  
/optimize[+ | -]  
```  
  
## <a name="remarks"></a>コメント  
 **/optimize** は実行時にコードを最適化するように共通言語ランタイムに指示します。  
  
 既定では、最適化が無効になります。 **/optimize+** を指定して最適化を有効にします。  
  
 モジュールをアセンブリで使用するように作成する場合は、アセンブリと同じ **/optimize** 設定を使用します。  
  
 **/o** は **/optimize** の省略形です。  
  
 **/optimize** オプションと [/debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) オプションを結合することができます。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **[プロパティ]** ページを開きます。  
  
2.  **[ビルド]** プロパティ ページをクリックします。  
  
3.  **コードの最適化**プロパティを変更します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>」をご覧ください。  
  
## <a name="example"></a>例  
 `t2.cs` をコンパイルしてコンパイラの最適化を有効にします。  
  
```console  
csc t2.cs /optimize  
```  
  
## <a name="see-also"></a>関連項目  
 [C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)  
 [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)
