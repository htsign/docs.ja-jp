---
title: "ADO.NET でのパフォーマンス カウンター"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 0b121b71-78f8-4ae2-9aa1-0b2e15778e57
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 18403ac8237b1e129ec07e0271ff75194d944855
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="performance-counters-in-adonet"></a>ADO.NET でのパフォーマンス カウンター
ADO.NET 2.0 では、<xref:System.Data.SqlClient> と <xref:System.Data.OracleClient> の両方をサポートする新しいパフォーマンス カウンターが導入されました。 以前のバージョンの ADO.NET で利用されていた <xref:System.Data.SqlClient> のパフォーマンス カウンターは廃止され、このトピックで説明する新しいパフォーマンス カウンターに置き換えられました。 ADO.NET のパフォーマンス カウンターを使用することで、アプリケーションやそれによって使用される接続リソースのステータスを監視できます。 パフォーマンス カウンターは、Windows パフォーマンス モニターを使って監視できるほか、<xref:System.Diagnostics.PerformanceCounter> 名前空間の <xref:System.Diagnostics> クラスを使用することでプログラムから監視することもできます。  
  
## <a name="available-performance-counters"></a>利用可能なパフォーマンス カウンター  
 次の表に示したように、<xref:System.Data.SqlClient> および <xref:System.Data.OracleClient> には現在、14 種類のパフォーマンス カウンターが存在します。 個々のカウンターの名前は、Microsoft .NET Framework の地域別バージョン全体でローカライズされているわけではないことに注意してください。  
  
|パフォーマンス カウンター|説明|  
|-------------------------|-----------------|  
|`HardConnectsPerSecond`|データベース サーバーに対する 1 秒あたりの接続数。|  
|`HardDisconnectsPerSecond`|データベース サーバーに対する 1 秒あたりの切断数。|  
|`NumberOfActiveConnectionPoolGroups`|アクティブな一意の接続プール グループの数。 このカウンターは、AppDomain に見つかった一意の接続文字列数によって制御されます。|  
|`NumberOfActiveConnectionPools`|接続プールの合計数。|  
|`NumberOfActiveConnections`|現在使用中のアクティブな接続の数。 **注:**既定でこのパフォーマンス カウンターが有効にできません。 このパフォーマンス カウンターを有効にするを参照してください。[既定ではオフになってカウンターのアクティブ化](#ActivatingOffByDefault)です。|  
|`NumberOfFreeConnections`|接続プール内の利用可能な接続数。 **注:**既定でこのパフォーマンス カウンターが有効にできません。 このパフォーマンス カウンターを有効にするを参照してください。[既定ではオフになってカウンターのアクティブ化](#ActivatingOffByDefault)です。|  
|`NumberOfInactiveConnectionPoolGroups`|排除対象としてマークされた一意の接続プール グループの数。 このカウンターは、AppDomain に見つかった一意の接続文字列数によって制御されます。|  
|`NumberOfInactiveConnectionPools`|最近のアクティビティが存在せず、破棄待ち状態となっている、アクティブでない接続プールの数。|  
|`NumberOfNonPooledConnections`|プールされていないアクティブな接続の数。|  
|`NumberOfPooledConnections`|接続プール インフラストラクチャによって管理されているアクティブな接続の数。|  
|`NumberOfReclaimedConnections`|アプリケーションによって `Close` も `Dispose` も呼び出されなかった場合に、ガベージ コレクションによって回収された接続の数。 接続を明示的に閉じるか破棄しないと、パフォーマンスが低下します。|  
|`NumberOfStasisConnections`|現在アクションの完了を待っている (そのためにアプリケーションからは使用できない) 接続の数。|  
|`SoftConnectsPerSecond`|接続プールからプルされているアクティブな接続の数。 **注:**既定でこのパフォーマンス カウンターが有効にできません。 このパフォーマンス カウンターを有効にするを参照してください。[既定ではオフになってカウンターのアクティブ化](#ActivatingOffByDefault)です。|  
|`SoftDisconnectsPerSecond`|接続プールに戻されているアクティブな接続の数。 **注:**既定でこのパフォーマンス カウンターが有効にできません。 このパフォーマンス カウンターを有効にするを参照してください。[既定ではオフになってカウンターのアクティブ化](#ActivatingOffByDefault)です。|  
  
### <a name="connection-pool-groups-and-connection-pools"></a>接続プール グループと接続プール  
 Windows 認証 (統合セキュリティ) を使用している場合、`NumberOfActiveConnectionPoolGroups` と `NumberOfActiveConnectionPools` の両方のパフォーマンス カウンターを監視する必要があります。 なぜなら、接続プール グループは接続文字列単位でマップされるためです。 統合セキュリティを使用した場合、接続文字列にマップされた接続プールの他に、個々の Windows ID 用に別々のプールが作成されます。 たとえば、同じ AppDomain に属する Fred と Julie が、どちらも `"Data Source=MySqlServer;Integrated Security=true"` という接続文字列を使用した場合、その接続文字列に対応した接続プール グループが作成され、それに加えて、2 つのプール (Fred 用と Julie 用) が作成されます。 John と Martha が同一の SQL Server ログインで接続文字列を使用する場合`"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"`の 1 つのプールのみが作成され、 **lowPrivUser**の id。  
  
<a name="ActivatingOffByDefault"></a>   
### <a name="activating-off-by-default-counters"></a>既定ではオフになっているカウンターのアクティブ化  
 `NumberOfFreeConnections`、`NumberOfActiveConnections`、`SoftDisconnectsPerSecond`、`SoftConnectsPerSecond` の各パフォーマンス カウンターは、既定ではオフになっています。 有効にするには、アプリケーションの構成ファイルに次の情報を追加します。  
  
```xml  
<system.diagnostics>  
  <switches>  
    <add name="ConnectionPoolPerformanceCounterDetail"  
         value="4"/>  
  </switches>  
</system.diagnostics>  
```  
  
## <a name="retrieving-performance-counter-values"></a>パフォーマンス カウンターの値の取得  
 次のコンソール アプリケーションは、アプリケーションでパフォーマンス カウンターの値を取得する方法を示しています。 すべての ADO.NET パフォーマンス カウンターの情報を取得できるように、接続を開いてアクティブにする必要があります。  
  
> [!NOTE]
>  この例は、サンプルを使用して**AdventureWorks**データベースに含まれている[!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]です。 サンプル コードの接続文字列は、データベースがローカル コンピューターにインストールされていること、SqlExpress というインスタンス名で実行されていること、接続文字列に指定された情報と一致する SQL Server ログインが作成済みであることを想定しています。 既定のセキュリティ設定を使用するようにサーバーが構成されている場合、そのままでは Windows 認証しか許可されないため、SQL Server ログインを有効にする必要があります。 接続文字列は環境に合わせて変更してください。  
  
### <a name="example"></a>例  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System.Data.SqlClient  
Imports System.Diagnostics  
Imports System.Runtime.InteropServices  
  
Class Program  
  
    Private PerfCounters(9) As PerformanceCounter  
    Private connection As SqlConnection = New SqlConnection  
  
    Public Shared Sub Main()  
        Dim prog As Program = New Program  
        ' Open a connection and create the performance counters.   
        prog.connection.ConnectionString = _  
           GetIntegratedSecurityConnectionString()  
        prog.SetUpPerformanceCounters()  
        Console.WriteLine("Available Performance Counters:")  
  
        ' Create the connections and display the results.  
        prog.CreateConnections()  
        Console.WriteLine("Press Enter to finish.")  
        Console.ReadLine()  
    End Sub  
  
    Private Sub CreateConnections()  
        ' List the Performance counters.  
        WritePerformanceCounters()  
  
        ' Create 4 connections and display counter information.  
        Dim connection1 As SqlConnection = New SqlConnection( _  
           GetIntegratedSecurityConnectionString)  
        connection1.Open()  
        Console.WriteLine("Opened the 1st Connection:")  
        WritePerformanceCounters()  
  
        Dim connection2 As SqlConnection = New SqlConnection( _  
           GetSqlConnectionStringDifferent)  
        connection2.Open()  
        Console.WriteLine("Opened the 2nd Connection:")  
        WritePerformanceCounters()  
  
        Console.WriteLine("Opened the 3rd Connection:")  
        Dim connection3 As SqlConnection = New SqlConnection( _  
           GetSqlConnectionString)  
        connection3.Open()  
        WritePerformanceCounters()  
  
        Dim connection4 As SqlConnection = New SqlConnection( _  
           GetSqlConnectionString)  
        connection4.Open()  
        Console.WriteLine("Opened the 4th Connection:")  
        WritePerformanceCounters()  
  
        connection1.Close()  
        Console.WriteLine("Closed the 1st Connection:")  
        WritePerformanceCounters()  
  
        connection2.Close()  
        Console.WriteLine("Closed the 2nd Connection:")  
        WritePerformanceCounters()  
  
        connection3.Close()  
        Console.WriteLine("Closed the 3rd Connection:")  
        WritePerformanceCounters()  
  
        connection4.Close()  
        Console.WriteLine("Closed the 4th Connection:")  
        WritePerformanceCounters()  
    End Sub  
  
    Private Enum ADO_Net_Performance_Counters  
        NumberOfActiveConnectionPools  
        NumberOfReclaimedConnections  
        HardConnectsPerSecond  
        HardDisconnectsPerSecond  
        NumberOfActiveConnectionPoolGroups  
        NumberOfInactiveConnectionPoolGroups  
        NumberOfInactiveConnectionPools  
        NumberOfNonPooledConnections  
        NumberOfPooledConnections  
        NumberOfStasisConnections  
        ' The following performance counters are more expensive to track.  
        ' Enable ConnectionPoolPerformanceCounterDetail in your config file.  
        '     SoftConnectsPerSecond  
        '     SoftDisconnectsPerSecond  
        '     NumberOfActiveConnections  
        '     NumberOfFreeConnections  
    End Enum  
  
    Private Sub SetUpPerformanceCounters()  
        connection.Close()  
        Me.PerfCounters(9) = New PerformanceCounter()  
  
        Dim instanceName As String = GetInstanceName()  
        Dim apc As Type = GetType(ADO_Net_Performance_Counters)  
        Dim i As Integer = 0  
        Dim s As String = ""  
        For Each s In [Enum].GetNames(apc)  
            Me.PerfCounters(i) = New PerformanceCounter()  
            Me.PerfCounters(i).CategoryName = ".NET Data Provider for SqlServer"  
            Me.PerfCounters(i).CounterName = s  
            Me.PerfCounters(i).InstanceName = instanceName  
            i = (i + 1)  
        Next  
    End Sub  
  
    Private Declare Function GetCurrentProcessId Lib "kernel32.dll" () As Integer  
  
    Private Function GetInstanceName() As String  
        'This works for Winforms apps.   
        Dim instanceName As String = _  
           System.Reflection.Assembly.GetEntryAssembly.GetName.Name  
  
        ' Must replace special characters like (, ), #, /, \\   
        Dim instanceName2 As String = _  
           AppDomain.CurrentDomain.FriendlyName.ToString.Replace("(", "[") _  
           .Replace(")", "]").Replace("#", "_").Replace("/", "_").Replace("\\", "_")  
  
        'For ASP.NET applications your instanceName will be your CurrentDomain's   
        'FriendlyName. Replace the line above that sets the instanceName with this:   
        'instanceName = AppDomain.CurrentDomain.FriendlyName.ToString.Replace("(", "[") _  
        '    .Replace(")", "]").Replace("#", "_").Replace("/", "_").Replace("\\", "_")  
  
        Dim pid As String = GetCurrentProcessId.ToString  
        instanceName = (instanceName + ("[" & (pid & "]")))  
        Console.WriteLine("Instance Name: {0}", instanceName)  
        Console.WriteLine("---------------------------")  
        Return instanceName  
    End Function  
  
    Private Sub WritePerformanceCounters()  
        Console.WriteLine("---------------------------")  
        For Each p As PerformanceCounter In Me.PerfCounters  
            Console.WriteLine("{0} = {1}", p.CounterName, p.NextValue)  
        Next  
        Console.WriteLine("---------------------------")  
    End Sub  
  
    Private Shared Function GetIntegratedSecurityConnectionString() As String  
        ' To avoid storing the connection string in your code,   
        ' you can retrive it from a configuration file.   
        Return ("Data Source=.\SqlExpress;Integrated Security=True;" &   
          "Initial Catalog=AdventureWorks")  
    End Function  
  
    Private Shared Function GetSqlConnectionString() As String  
        ' To avoid storing the connection string in your code,   
        ' you can retrive it from a configuration file.   
        Return ("Data Source=.\SqlExpress;User Id=LowPriv;Password=Data!05;" &   
          "Initial Catalog=AdventureWorks")  
    End Function  
  
    Private Shared Function GetSqlConnectionStringDifferent() As String  
        ' To avoid storing the connection string in your code,   
        ' you can retrive it from a configuration file.   
        Return ("Initial Catalog=AdventureWorks;Data Source=.\SqlExpress;" & _  
          "User Id=LowPriv;Password=Data!05;")  
    End Function  
End Class  
```  
  
```csharp  
using System;  
using System.Data.SqlClient;  
using System.Diagnostics;  
using System.Runtime.InteropServices;  
  
class Program  
{  
    PerformanceCounter[] PerfCounters = new PerformanceCounter[10];  
    SqlConnection connection = new SqlConnection();  
  
    static void Main()  
    {  
        Program prog = new Program();  
        // Open a connection and create the performance counters.  
        prog.connection.ConnectionString =  
           GetIntegratedSecurityConnectionString();  
        prog.SetUpPerformanceCounters();  
        Console.WriteLine("Available Performance Counters:");  
  
        // Create the connections and display the results.  
        prog.CreateConnections();  
        Console.WriteLine("Press Enter to finish.");  
        Console.ReadLine();  
    }  
  
    private void CreateConnections()  
    {  
        // List the Performance counters.  
        WritePerformanceCounters();  
  
        // Create 4 connections and display counter information.  
        SqlConnection connection1 = new SqlConnection(  
              GetIntegratedSecurityConnectionString());  
        connection1.Open();  
        Console.WriteLine("Opened the 1st Connection:");  
        WritePerformanceCounters();  
  
        SqlConnection connection2 = new SqlConnection(  
              GetSqlConnectionStringDifferent());  
        connection2.Open();  
        Console.WriteLine("Opened the 2nd Connection:");  
        WritePerformanceCounters();  
  
        SqlConnection connection3 = new SqlConnection(  
              GetSqlConnectionString());  
        connection3.Open();  
        Console.WriteLine("Opened the 3rd Connection:");  
        WritePerformanceCounters();  
  
        SqlConnection connection4 = new SqlConnection(  
              GetSqlConnectionString());  
        connection4.Open();  
        Console.WriteLine("Opened the 4th Connection:");  
        WritePerformanceCounters();  
  
        connection1.Close();  
        Console.WriteLine("Closed the 1st Connection:");  
        WritePerformanceCounters();  
  
        connection2.Close();  
        Console.WriteLine("Closed the 2nd Connection:");  
        WritePerformanceCounters();  
  
        connection3.Close();  
        Console.WriteLine("Closed the 3rd Connection:");  
        WritePerformanceCounters();  
  
        connection4.Close();  
        Console.WriteLine("Closed the 4th Connection:");  
        WritePerformanceCounters();  
    }  
  
    private enum ADO_Net_Performance_Counters  
    {  
        NumberOfActiveConnectionPools,  
        NumberOfReclaimedConnections,  
        HardConnectsPerSecond,  
        HardDisconnectsPerSecond,  
        NumberOfActiveConnectionPoolGroups,  
        NumberOfInactiveConnectionPoolGroups,  
        NumberOfInactiveConnectionPools,  
        NumberOfNonPooledConnections,  
        NumberOfPooledConnections,  
        NumberOfStasisConnections  
        // The following performance counters are more expensive to track.  
        // Enable ConnectionPoolPerformanceCounterDetail in your config file.  
        //     SoftConnectsPerSecond  
        //     SoftDisconnectsPerSecond  
        //     NumberOfActiveConnections  
        //     NumberOfFreeConnections  
    }  
  
    private void SetUpPerformanceCounters()  
    {  
        connection.Close();  
        this.PerfCounters = new PerformanceCounter[10];  
        string instanceName = GetInstanceName();  
        Type apc = typeof(ADO_Net_Performance_Counters);  
        int i = 0;  
        foreach (string s in Enum.GetNames(apc))  
        {  
            this.PerfCounters[i] = new PerformanceCounter();  
            this.PerfCounters[i].CategoryName = ".NET Data Provider for SqlServer";  
            this.PerfCounters[i].CounterName = s;  
            this.PerfCounters[i].InstanceName = instanceName;  
            i++;  
        }  
    }  
  
    [DllImport("kernel32.dll", SetLastError = true)]  
    static extern int GetCurrentProcessId();  
  
    private string GetInstanceName()  
    {  
        //This works for Winforms apps.  
        string instanceName =  
            System.Reflection.Assembly.GetEntryAssembly().GetName().Name;  
  
        // Must replace special characters like (, ), #, /, \\  
        string instanceName2 =  
            AppDomain.CurrentDomain.FriendlyName.ToString().Replace('(', '[')  
            .Replace(')', ']').Replace('#', '_').Replace('/', '_').Replace('\\', '_');  
  
        // For ASP.NET applications your instanceName will be your CurrentDomain's   
        // FriendlyName. Replace the line above that sets the instanceName with this:  
        // instanceName = AppDomain.CurrentDomain.FriendlyName.ToString().Replace('(','[')  
        // .Replace(')',']').Replace('#','_').Replace('/','_').Replace('\\','_');  
  
        string pid = GetCurrentProcessId().ToString();  
        instanceName = instanceName + "[" + pid + "]";  
        Console.WriteLine("Instance Name: {0}", instanceName);  
        Console.WriteLine("---------------------------");  
        return instanceName;  
    }  
  
    private void WritePerformanceCounters()  
    {  
        Console.WriteLine("---------------------------");  
        foreach (PerformanceCounter p in this.PerfCounters)  
        {  
            Console.WriteLine("{0} = {1}", p.CounterName, p.NextValue());  
        }  
        Console.WriteLine("---------------------------");  
    }  
  
    private static string GetIntegratedSecurityConnectionString()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrive it from a configuration file.  
        return @"Data Source=.\SqlExpress;Integrated Security=True;" +  
          "Initial Catalog=AdventureWorks";  
    }  
    private static string GetSqlConnectionString()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrive it from a configuration file.  
        return @"Data Source=.\SqlExpress;User Id=LowPriv;Password=Data!05;" +  
        //  "Initial Catalog=AdventureWorks";  
    }  
  
    private static string GetSqlConnectionStringDifferent()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrive it from a configuration file.  
        return @"Initial Catalog=AdventureWorks;Data Source=.\SqlExpress;" +  
          "User Id=LowPriv;Password=Data!05;";  
    }  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [データ ソースへの接続](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [OLE DB、ODBC、および Oracle 接続プール](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)  
 [ASP.NET 用のパフォーマンス カウンター](http://msdn.microsoft.com/library/1e122fcb-05c0-4f9f-bef1-f47023fa1ac6)  
 [ランタイム プロファイリング](../../../../docs/framework/debug-trace-profile/runtime-profiling.md)  
 [パフォーマンスしきい値の監視の概要](http://msdn.microsoft.com/en-us/d40f10b9-e2b7-4ec8-a9b3-706929e5bf35)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
