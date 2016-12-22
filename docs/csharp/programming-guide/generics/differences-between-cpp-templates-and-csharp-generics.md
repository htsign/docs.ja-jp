---
title: "C++ テンプレートと C# ジェネリックの違い (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "ジェネリック [C#], 比較 (C++ のテンプレートとの)"
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# C++ テンプレートと C# ジェネリックの違い (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

C\# ジェネリックも C\+\+ テンプレートもいずれもパラメーター化された型のサポートを提供する言語機能です。  ただし、これら 2 つにはさまざまな違いがあります。  たとえば、構文レベルでは、C\# ジェネリックは、パラメーター化された型により単純にアプローチでき、C\+\+ テンプレートのような複雑さがありません。  さらに、C\# では、C\+\+ テンプレートで提供されるすべての機能が提供されるわけではありません。  また、実装レベルでは、C\# ジェネリック型の置換は実行時に行われ、その結果、インスタンス化されたオブジェクトのジェネリック型情報が保存されるという点が主に異なります。  詳細については、「[ランタイムのジェネリック](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)」を参照してください。  
  
 C\# ジェネリックと C\+\+ テンプレートの主な違いを以下に示します。  
  
-   C\# ジェネリックは、C\+\+ テンプレートほど柔軟ではありません。  たとえば、C\# ジェネリック クラスでは、ユーザー定義演算子は呼び出すことができますが、算術演算子を呼び出すことはできません。  
  
-   C\# では、`template C<int i> {}` などの非型テンプレート パラメーターを使用できません。  
  
-   C\# は、明示的な特殊化 \(特定の型のテンプレートのカスタム実装\) をサポートしません。  
  
-   C\# は、部分的な特殊化 \(型引数のサブセットのカスタム実装\) をサポートしません。  
  
-   C\# では、型パラメーターをジェネリック型の基本クラスとして使用できません。  
  
-   C\# では、型パラメーターに既定の型を割り当てることができません。  
  
-   C\# では、構築された型はジェネリックとして使用できますが、ジェネリック型パラメーター自体はジェネリックにできません。  C\+\+ では、テンプレート パラメーターを使用できます。  
  
-   C\+\+ では、テンプレート内のすべての型パラメーターに対して有効でない可能性のあるコードを使用できます。このようなコードは、型パラメーターとして使用されている特定の型に対してチェックされます。  C\# では、制約を満たすすべての型で正常に動作するようにクラスのコードを記述する必要があります。  たとえば、C\+\+ では、型パラメーターのオブジェクトで算術演算子 `+` および `-` を使用し、これらの演算子をサポートしない型を使ってテンプレートをインスタンス化するとエラーを生成する関数を記述できます。  C\# では、このような関数は許可されません。許可される言語構成要素は、制約から推定できるものだけに限られます。  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [テンプレート](/visual-cpp/cpp/templates-cpp)