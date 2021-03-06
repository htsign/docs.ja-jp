---
title: "グループ結合の実行"
description: "グループ結合を実行する方法。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.openlocfilehash: 5e26473e19a5b6107d7aceea5e9829b48aa522b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="perform-grouped-joins"></a>グループ結合の実行

グループ結合は、階層データ構造を作成する場合に便利です。 これは、最初のコレクションの各要素と、2 番目のコレクションの相関関係を持つ要素のセットを組み合わせたものです。  
  
 たとえば、`Student` という名前のクラスまたはリレーショナル データベース テーブルに、`Id` と `Name` という 2 つのフィールドが含まれているとします。 `Course` という名前の 2 番目のクラスまたはリレーショナル データベース テーブルには、`StudentId` と `CourseTitle` という 2 つのフィールドが含まれているとします。 この 2 つのデータ ソースのグループ結合は、`Student.Id` と `Course.StudentId` の一致に基づいて、`Course` オブジェクトのコレクションを持つ各 `Student` をグループ化します (コレクションは空の場合もあります)。  
  
> [!NOTE]
>  最初のコレクションの各要素は、2 番目のコレクションに相関関係を持つ要素があるかどうかにかかわらず、グループ結合の結果セットに表示されます。 相関関係を持つ要素が見つからない場合、その要素の相関関係を持つ要素のシーケンスは空です。 そのため、結果セレクターは最初のコレクションのすべての要素にアクセスできます。 これは、非グループ結合の結果セレクターとは異なります。非グループ結合の結果セレクターは、2 番目のコレクションに一致するものがない最初のコレクションの要素にアクセスすることはできません。  
  
 このトピックの最初の例では、グループ結合を実行する方法を示します。 2 つ目の例では、グループ結合を使用して XML 要素を作成する方法を示します。  
  
## <a name="example"></a>例  
  
### <a name="group-join-example"></a>グループ結合の例  
 次の例では、`Pet.Owner` プロパティと一致する `Person` に基づいて、`Person` 型と `Pet` 型のオブジェクトのグループ結合を実行します。 一致ごとに要素のペアを生成する非グループ結合と異なり、グループ結合は最初のコレクションの要素ごとに 1 つのオブジェクト (この例では `Person` オブジェクト) のみを作成します。 2 番目のコレクションの対応する要素 (この例では `Pet` オブジェクト) が 1 つのコレクションにグループ化されます。 最後に、結果セレクター機能により、`Person.FirstName` と、`Pet` オブジェクトのコレクションで構成される一致ごとに匿名型が作成されます。  
  
 [!code-csharp[CsLINQProgJoining#5](../../../samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]  
  
## <a name="example"></a>例  
  
### <a name="group-join-to-create-xml-example"></a>XML を作成するグループ結合の例  
 グループ結合は、LINQ to XML を使用した XML の作成に適しています。 次の例は前の例に似ていますが、匿名型を作成するのではなく、結果セレクター機能により、結合されたオブジェクトを表す XML 要素を作成する点が異なります。  
  
 [!code-csharp[CsLINQProgJoining#6](../../../samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]  
 
## <a name="see-also"></a>関連項目  
 <xref:System.Linq.Enumerable.Join%2A>  
 <xref:System.Linq.Enumerable.GroupJoin%2A>  
 [内部結合の実行](perform-inner-joins.md)  
 [左外部結合の実行](perform-left-outer-joins.md)  
 [匿名型](../programming-guide/classes-and-structs/anonymous-types.md)  
 
