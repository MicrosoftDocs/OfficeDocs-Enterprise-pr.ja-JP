---
title: 単一の Windows PowerShell ウィンドウですべての Office 365 サービスに接続する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/23/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: '概要: 単一の Windows PowerShell ウィンドウで Windows PowerShell をすべての Office 365 サービスに接続します。'
ms.openlocfilehash: 7e3a3ecbb0526c88392848cf39b59b40f1f4c80c
ms.sourcegitcommit: 3b474e0b9f0c12bb02f8439fb42b80c2f4798ce1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a>単一の Windows PowerShell ウィンドウですべての Office 365 サービスに接続する

 **概要:** 別々の PowerShell コンソール ウィンドウで各種 Office 365 サービスを管理するのではなく、1 つのコンソール ウィンドウからすべての Office 365 サービスに接続して管理できます。
  
PowerShell を使用して Office 365 を管理する場合は、最大 5 つの異なる Windows PowerShell セッション (Office 365 管理センター、SharePoint Online、Exchange Online、Skype for Business Online、およびセキュリティ/コンプライアンス センターに対応する) を同時に開くことができます。別々の Windows PowerShell セッションで 5 つの異なる接続方法を使用すると、デスクトップは以下のようになります。
  
![一度に実行している 5 つの Windows PowerShell コンソール](images/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
これは Office 365 の管理に最適な状況ではありません。サービス間管理のために 5 つのウィンドウ間でデータを交換できないからです。このトピックでは、Office 365、Skype for Business Online、Exchange Online、SharePoint Online、および セキュリティ センターとコンプライアンス センター を管理する Windows PowerShell のインスタンスを使用する方法について説明します。

## <a name="before-you-begin"></a>はじめに
<a name="BeforeYouBegin"> </a>

Windows PowerShell の単一のインスタンスからすべての Office 365 を管理する前に、次の前提条件を考慮してください。
  
- これらの手順に使用する Office 365職場または学校のアカウント は、Office 365 管理者役割のメンバーである必要があります。詳細については、「[Office 365 の管理者の役割](https://go.microsoft.com/fwlink/p/?LinkId=532367)」を参照してください。これは Office 365 PowerShell の要件であり、他のすべての Office 365 サービスについては必ずしも当てはまりません。
    
- 次の Windows の 64 ビット バージョンを使用できます。
    
  - Windows 10
    
  - Windows 8.1 または Windows 8
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 または Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    * Microsoft.NET Framework 4.5 をインストールする必要があります。*x*とし、いずれかの Windows Management Framework 3.0 または Windows Management Framework 4.0 です。詳細については、 [ [.NET Framework をインストールして](https://go.microsoft.com/fwlink/p/?LinkId=257868)Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757)または[4.0 の Windows Management Framework](https://go.microsoft.com/fwlink/p/?LinkId=391344)を参照してください。
    
    Skype for Business Online モジュール、および Office 365 モジュールの 1 つの要件のため、64 ビット バージョンの Windows を使用する必要があります。
    
- Azure AD に必要なモジュールをインストールする必要があり、SharePoint Online では、ビジネス オンラインの Skype。
    
   - [Azure Active Directory V2](connect-to-office-365-powershell.md#ConnectV2)
   - [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [Skype for Business Online、Windows PowerShell モジュール](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  Skype for Business Online、Exchange Online、およびセキュリティ/コンプライアンス センターに対して署名付きスクリプトを実行するよう Windows PowerShell を構成する必要があります。そのためには、管理者特権の Windows PowerShell セッション (Windows PowerShell ウィンドウで **[管理者として実行]** を選択して開きます) で、次のコマンドを実行します。
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a>パスワードを使用する場合の接続手順
<a name="ConnStepsPassword"> </a>

ここでは、1 つの PowerShell ウィンドウ内のすべてのサービスに接続する手順を実行します。
  
1. 管理者として Windows PowerShell を開きます ( **[管理者として実行]** を使用)。
    
2. 次のコマンドを実行し、Office 365職場または学校のアカウント の資格情報を入力します。
    
  ```
  $credential = Get-Credential
  ```

3. Azure Active Directory (AD) への接続にこのコマンドを実行します。
    
  ```
   Connect-AzureAD -Credential $credential
  ```

4. 次のコマンドを実行して、SharePoint Online に接続します。_\<domainhost>_ は実際のドメイン値に置き換えます。たとえば、`litwareinc.onmicrosoft.com` の場合、_\<domainhost>_ 値は `litwareinc` となります。
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. 次のコマンドを実行して、Skype for Business Online に接続します。初めて接続する場合、`WSMan NetworkDelayms` の値を増やすようにという警告が出ますが、無視してください。
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. 次のコマンドを実行して、Exchange Online に接続します。
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession
  ```

7. 次のコマンドを実行して、セキュリティ センターとコンプライアンス センター に接続します。
    
  ```
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

次に 1 つのブロック内のすべてのコマンドを示します。ドメイン ホストの名前を指定してから、それらすべてを同時に実行します。
  
```
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```
Windows PowerShell ウィンドウを閉じる準備が整った段階でこのコマンドを実行し、Skype for Business Online、Exchange Online、SharePoint Online、セキュリティ/コンプライアンス センターに対するアクティブなセッションを削除します。
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $SccSession ; Disconnect-SPOService
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a>多要素認証を使用する場合の接続手順
<a name="ConnStepsMFA"> </a>

Azure AD に接続する 1 つのブロック内のすべてのコマンドをここでは、SharePoint Online と多要素認証を使用して 1 つのウィンドウで Buiness の Skype です。グローバル管理者アカウントのユーザー プリンシパル名 (UPN) の名前と、ドメインのホスト名を指定し、それらすべてを同時に実行します。

````
$acctName="<UPN of a global administrator account>"
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
````

Exchange Online とセキュリティの&amp;コンプライアンス センターでは、多要素認証を使用して接続するのには次のトピックを参照してください。

- [多要素認証を使用して Exchange のオンライン PowerShell への接続します。](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell)
- [Office 365 のセキュリティとコンプライアンス センター PowerShell の多要素認証を使用してへの接続します。](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)
 
どちらの場合で、Exchange オンライン リモート PowerShell モジュールの別のセッションを使用して接続する必要があります。


## <a name="new-to-office-365"></a>Office 365 を初めて使用する場合

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>関連項目

- [Office 365 PowerShell への接続](connect-to-office-365-powershell.md)
- [Office 365 PowerShell を使用して SharePoint Online を管理する](manage-sharepoint-online-with-office-365-powershell.md)
- [Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [Windows PowerShell を使用して Office 365 でレポートを作成する](use-windows-powershell-to-create-reports-in-office-365.md)
