---
title: "XPathNavigator を使用した XML データの選択"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c268c49e-32b9-4171-b782-dcb7b065fa73
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9f63f23b1a07fbe77e77598cd05dcd25ee8ec158
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="select-xml-data-using-xpathnavigator"></a>XPathNavigator を使用した XML データの選択
<xref:System.Xml.XPath.XPathNavigator> クラスは、<xref:System.Xml.XPath.XPathDocument> オブジェクトまたは <xref:System.Xml.XmlDocument> オブジェクト内で XPath 式を使用してノード セットを選択するための一連のメソッドを提供します。 選択した後、選択されたノード セットに対して反復して処理を行うことができます。  
  
## <a name="xpathnavigator-selection-methods"></a>XPathNavigator の選択メソッド  
 <xref:System.Xml.XPath.XPathNavigator> クラスは、<xref:System.Xml.XPath.XPathDocument> オブジェクトまたは <xref:System.Xml.XmlDocument> オブジェクト内で XPath 式を使用してノード セットを選択するための一連のメソッドを提供します。 <xref:System.Xml.XPath.XPathNavigator> クラスは、祖先、子、および子孫のノードを、XPath 式を使用するよりも高速に選択できる最適化された一連のメソッドも提供します。 選択されたノード セットは、<xref:System.Xml.XPath.XPathNodeIterator> オブジェクトまたは、選択されたノードが単一の場合は <xref:System.Xml.XPath.XPathNavigator> オブジェクトとして返されます。  
  
### <a name="selecting-nodes-using-xpath-expressions"></a>XPath 式によるノードの選択  
 XPath 式を使用して 1 つのノード セットを選択するには、次のいずれかの選択メソッドを使用します。  
  
-   <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 呼び出されると、これらのメソッドは <xref:System.Xml.XPath.XPathNodeIterator> オブジェクト、または選択が単一ノードの場合は <xref:System.Xml.XPath.XPathNavigator> オブジェクトを使用して、自由に移動できる 1 つのノード セットを返します。  
  
 <xref:System.Xml.XPath.XPathNodeIterator> オブジェクトを使用して移動しても、その作成に使用された <xref:System.Xml.XPath.XPathNavigator> オブジェクトの位置に影響ありません。 <xref:System.Xml.XPath.XPathNavigator> メソッドから返された <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> オブジェクトは、返された単一ノード上に位置し、この場合もその作成に使用された <xref:System.Xml.XPath.XPathNavigator> オブジェクトの位置には影響しません。  
  
 次の例は、<xref:System.Xml.XPath.XPathNavigator> オブジェクトからの <xref:System.Xml.XPath.XPathDocument> オブジェクトの作成、<xref:System.Xml.XPath.XPathNavigator.Select%2A> メソッドを使用した <xref:System.Xml.XPath.XPathDocument> オブジェクト内のノードの選択、および <xref:System.Xml.XPath.XPathNodeIterator> オブジェクトを使用した選択ノード上の繰り返し処理について示しています。  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
Dim nodes As XPathNodeIterator = navigator.Select("/bookstore/book")  
  
While nodes.MoveNext()  
    Console.WriteLine(nodes.Current.Name)  
End While  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
XPathNodeIterator nodes = navigator.Select("/bookstore/book");  
  
while(nodes.MoveNext())  
{  
    Console.WriteLine(nodes.Current.Name);  
}  
```  
  
 この例は、`books.xml` ファイルを入力として使用します。  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="optimized-selection-methods"></a>最適化された選択メソッド  
 <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A> クラスの <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>、<xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A>、および <xref:System.Xml.XPath.XPathNavigator> メソッドは、子、子孫、および祖先のノードにアクセスする一般的な XPath 式に相当します。 これらのメソッドのパフォーマンスは最適化されており、対応する XPath 式よりも高速です。 <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>、<xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>、および <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> メソッドは、<xref:System.Xml.XPath.XPathNodeType> 値または選択するノードのローカル名と名前空間 URI を基にして祖先、子、および子孫のノードを選択します。 選択された祖先、子、および子孫のノードは <xref:System.Xml.XPath.XPathNodeIterator> オブジェクトとして返されます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [XPath データ モデルを使用した XML データの処理](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [XPathNavigator による XPath 式を評価します。](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [XPathNavigator によるノードの一致](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [XPath クエリで認識されるノード型](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [XPath クエリおよび名前空間](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [コンパイルされた XPath 式](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
