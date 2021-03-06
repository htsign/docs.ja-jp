---
title: "アナウンスのサンプル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 954a75e4-9a97-41d6-94fc-43765d4205a9
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 045807df433d519b00969812afb0ae2feac94b75
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="announcements-sample"></a>アナウンスのサンプル
このサンプルでは、探索機能のアナウンス機能を使用する方法を示します。 アナウンス機能を使用すると、サービスに関するメタデータを含むアナウンス メッセージをサービスから送信できます。 既定では、サービスが開始されたときに Hello アナウンスが送信され、サービスがシャットダウンされたときに Bye アナウンスが送信されます。 これらのアナウンスは、マルチキャストすることも、Point-to-Point 送信することもできます。 このサンプルは、2 つのプロジェクト (サービスとクライアント) で構成されます。  
  
## <a name="service"></a>サービス  
 このプロジェクトには、自己ホスト型の電卓サービスが含まれています。 `Main` メソッドでは、サービス ホストが作成され、それにサービス エンドポイントが追加されます。 次に、<xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> が作成されます。 アナウンスを有効にする場合は、アナウンス エンドポイントを <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> に追加する必要があります。 この場合、UDP マルチキャストを使用して、標準エンドポイントをアナウンス エンドポイントとして追加します。 これにより、既知の UDP アドレスからアナウンスがブロードキャストされます。  
  
```  
Uri baseAddress = new Uri("http://localhost:8000/" + Guid.NewGuid().ToString());  
  
// Create a ServiceHost for the CalculatorService type.  
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))  
{  
     serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new WSHttpBinding(), String.Empty);  
  
     ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();  
  
     // Announce the availability of the service over UDP multicast  
    serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());  
  
    // Make the service discoverable over UDP multicast.  
    serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);                  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    serviceHost.Open();  
    // ...  
}  
```  
  
## <a name="client"></a>クライアント  
 このプロジェクトでは、クライアントが <xref:System.ServiceModel.Discovery.AnnouncementService> をホストすることに注意してください。 また、2 つのデリゲートがイベントに登録されます。 これらのイベントにより、オンラインおよびオフラインのアナウンスを受信したときのクライアントの処理が決定されます。  
  
```  
// Create an AnnouncementService instance  
AnnouncementService announcementService = new AnnouncementService();  
  
// Subscribe the announcement events  
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;  
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;  
```  
  
 `OnOnlineEvent` メソッドと `OnOfflineEvent` メソッドはそれぞれ、Hello アナウンス メッセージと Bye アナウンス メッセージを処理します。  
  
```  
static void OnOnlineEvent(object sender, AnnouncementEventArgs e)  
{  
    Console.WriteLine();              
    Console.WriteLine("Received an online announcement from {0}:", e.AnnouncementMessage.EndpointDiscoveryMetadata.Address);  
PrintEndpointDiscoveryMetadata(e.AnnouncementMessage.EndpointDiscoveryMetadata);  
}  
  
static void OnOfflineEvent(object sender, AnnouncementEventArgs e)  
{  
    Console.WriteLine();  
    Console.WriteLine("Received an offline announcement from {0}:", e.AnnouncementMessage.EndpointDiscoveryMetadata.Address);  
            PrintEndpointDiscoveryMetadata(e.AnnouncementMessage.EndpointDiscoveryMetadata);  
}  
```  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  このサンプルは、HTTP エンドポイントを使用して、このサンプルを適切な URL Acl を実行する必要があります追加を参照してください[を構成する HTTP および HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353)詳細についてはします。 管理特権で次のコマンドを実行すると、適切な ACL が追加されます。 そのままではコマンドが動作しない場合は、代わりに、ドメインとユーザー名を引数に指定して実行してみてください。 `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  ソリューションをビルドします。  
  
3.  client.exe アプリケーションを実行します。  
  
4.  service.exe アプリケーションを実行します。 クライアントは、オンライン アナウンスを受信します。  
  
5.  service.exe アプリケーションを終了します。 クライアントは、オフライン アナウンスを受信します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Announcements`  
  
## <a name="see-also"></a>関連項目
