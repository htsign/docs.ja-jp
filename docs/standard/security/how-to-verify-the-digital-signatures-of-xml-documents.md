---
title: "方法 : XML ドキュメントのデジタル署名を検証する"
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
helpviewer_keywords:
- System.Security.Cryptography.SignedXml class
- signatures, cryptographic
- System.Security.Cryptography.RSACryptoServiceProvider class
- verifying signatures
- checking signatures
- XML digital signatures
- digital signatures, verifying
ms.assetid: a4d5ceb1-b9f5-47e8-9e4a-a2b39110002f
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a2c8cf23e1f00d6deac52f3c4bee8932b7c487a4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-verify-the-digital-signatures-of-xml-documents"></a>方法 : XML ドキュメントのデジタル署名を検証する
<xref:System.Security.Cryptography.Xml> 名前空間にあるクラスを使用すると、デジタル署名で署名された XML データを検証できます。  XML デジタル署名 (XMLDSIG) を使用すると、データが署名後に変更されなかったことを確認できます。  XMLDSIG 標準の詳細については、Wide Web Consortium (W3C) 仕様 (http://www.w3.org/TR/xmldsig-core/) を参照してください。  
  
 この手順のコード例では、<`Signature`> 要素に格納されている XML デジタル署名の検証方法を示します。  この例では、キー コンテナーから RSA 公開キーを取得してから、キーを使用して署名を確認します。  
  
 この手法を使用して検証できるデジタル署名の作成方法についてを参照してください[する方法: デジタル署名で XML ドキュメントに](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md)です。  
  
### <a name="to-verify-the-digital-signature-of-an-xml-document"></a>XML ドキュメントのデジタル署名を検証するには  
  
1.  ドキュメントを検証するには、署名に使用した非対称キーと同じ非対称キーを使用する必要があります。  <xref:System.Security.Cryptography.CspParameters> オブジェクトを作成し、署名に使用したキー コンテナーの名前を指定します。  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#2)]  
  
2.  <xref:System.Security.Cryptography.RSACryptoServiceProvider> クラスを使用して公開キーを取得します。  <xref:System.Security.Cryptography.CspParameters> オブジェクトを <xref:System.Security.Cryptography.RSACryptoServiceProvider> クラスのコンストラクターに渡すと、キー コンテナーからキーが名前順で自動的に読み込まれます。  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#3)]  
  
3.  ディスクから XML ファイルを読み込んで <xref:System.Xml.XmlDocument> オブジェクトを作成します。  <xref:System.Xml.XmlDocument> オブジェクトには、確認対象の署名済みの XML ドキュメントが含まています。  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#4)]  
  
4.  <xref:System.Security.Cryptography.Xml.SignedXml> オブジェクトを新規作成し、それに <xref:System.Xml.XmlDocument> オブジェクトを渡します。  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#5)]  
  
5.  <`signature`> 要素を検索し、<xref:System.Xml.XmlNodeList> オブジェクトを新規作成します。  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#6)]  
  
6.  最初の <`signature`> 要素の XML を <xref:System.Security.Cryptography.Xml.SignedXml> オブジェクトに読み込みます。  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#7)]  
  
7.  <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> メソッドと RSA の公開キーを使用して署名を確認します。  このメソッドは、成功または失敗を示すブール値を返します。  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#8)]  
  
## <a name="example"></a>例  
 この例では、`"test.xml"` という名前のファイルがコンパイル済みのプログラムと同じディレクトリに存在することを前提としています。  `"test.xml"`で説明する手法を使用してファイルを署名する必要があります[する方法: デジタル署名で XML ドキュメントに](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md)です。  
  
 [!code-csharp[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
  
-   この例をコンパイルするには、`System.Security.dll` への参照を含める必要があります。  
  
-   名前空間 <xref:System.Xml>、<xref:System.Security.Cryptography>、および <xref:System.Security.Cryptography.Xml> を含めます。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 非対称キー ペアの秘密キーをプレーンテキストで保存または転送しないでください。  対称キーと非対称暗号化キーの詳細については、次を参照してください。[暗号化と復号化キーの生成](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)です。  
  
 秘密キーをソース コードに直接埋め込まないでください。  使用してアセンブリから、埋め込まれたキーを簡単に読み取ることができます、 [Ildasm.exe (IL 逆アセンブラー)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)またはメモ帳などのテキスト エディターで、アセンブリを開くことができます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Security.Cryptography.Xml>  
 [方法: デジタル署名で XML ドキュメントに署名する](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md)
