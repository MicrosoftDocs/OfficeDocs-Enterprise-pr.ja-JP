---
title: 委任アクセス許可 (DAP) パートナー用リモート Windows PowerShell で Exchange Online テナントに接続する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: '概要: リモート Windows PowerShell で DelegatedOrg 値を使用して、Exchange Online に接続します。'
ms.openlocfilehash: f04632f9e7b5e8dec476a5381550020e5d8a1521
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230833"
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a>委任アクセス許可 (DAP) パートナー用リモート Windows PowerShell で Exchange Online テナントに接続する

*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*

> [!IMPORTANT]
> このトピックの手順は、委任アクセス許可 (DAP) パートナー専用です。DAP パートナーでない場合は、このトピックの手順を使用しないでください。 
  
DAP パートナーとは、シンジケート パートナーとクラウド ソリューション プロバイダー (CSP) パートナーです。 他の会社のネットワーク プロバイダーまたは通信プロバイダーであることもよくあります。 それらのパートナーは、顧客に提供するサービスにサブスクリプションをバンドルします。 お客様は、Microsoft 365 カスタマーテナンシーに対して (AOBO) アクセス許可を自動的に付与されたパートナーテナントを所有しており、すべての顧客テナンシーの管理とレポートを行うことができます。

DAP パートナーは、Exchange Online PowerShell を使用して、ユーザーの Exchange Online の設定を管理したり、Microsoft 365 レポートをコマンドラインから取得したりできます。 ローカル コンピューター上で Windows PowerShell を使用して Exchange Online に対するリモート PowerShell セッションを作成します。 これは、資格情報を入力し、必要な接続設定を指定してから、Exchange Online コマンドレットをローカルの Windows PowerShell セッションにインポートして使用できるようにする、簡単な3段階のプロセスです。

> [!NOTE]
> DAP パートナーは、「[多要素認証を使用して Exchange Online PowerShell に接続する](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell)」の手順を使用して Exchange Online PowerShell に接続することはできません。MFA と Exchange Online リモート PowerShell モジュールは、委任された認証では機能しません。
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>はじめに把握しておくべき情報

- 予想所要時間 : 5 分

- 次の Windows のバージョンを使用できます。
    
  - Windows 10

  - Windows 8.1

  - Windows Server 2016

  - Windows Server 2012 または Windows Server 2012 R2

  - Windows 7 Service Pack 1 (SP1)<sup>*</sup>

  - Windows Server 2008 R2 SP1<sup>*</sup>

    <sup>*</sup> 以前のバージョンの Windows の場合は、Microsoft.NET Framework 4.5 以降をインストールしてから、更新バージョンの Windows Management Framework (3.0、4.0、5.1 のいずれか 1 つ) をインストールする必要があります。詳細については、「[.NET Framework のインストール](https://go.microsoft.com/fwlink/p/?LinkId=257868)」、「[Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757)」、「[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)」、「[Windows Management Framework 5.1](https://aka.ms/wmf5download)」を参照してください。

- スクリプトを実行するように Windows PowerShell を構成する必要があります。既定では、そのように構成されていないため、接続を試行すると、次に示すエラーが発生します。

  `Files cannot be loaded because running scripts is disabled on this system. Provide a valid certificate with which to sign the files.`

  インターネットからダウンロードしたすべての PowerShell スクリプトが信頼された発行元によって署名されていることを要求するには、管理者特権の Windows PowerShell ウィンドウ (**[管理者として実行]** を選択したときに開く Windows PowerShell ウィンドウ) で次のコマンドを実行します。

    ```
    Set-ExecutionPolicy RemoteSigned
    ```

  この設定は、コンピューターで一度だけ構成すれば、接続ごとに行う必要はありません。

- このトピックの手順に適用されるキーボード ショートカットについては、「[Exchange 管理センターのキーボード ショートカット](https://go.microsoft.com/fwlink/p/?LinkId=534017)」を参照してください。

## <a name="connect-to-exchange-online-for-customer-organizations"></a>顧客の組織の Exchange Online に接続する

1. ローカル コンピューターで、Windows PowerShell を開き、次のコマンドを実行します。
    
    ```
    $UserCredential = Get-Credential
    ```

    **[Windows PowerShell 資格情報の要求]** ダイアログ ボックスで、DAP 管理者のユーザー名とパスワードを入力してから **[OK]** をクリックします。
    
2. _\<customer tenant domain name\>_ を接続先のテナントドメインの名前に置き換えて、次のコマンドを実行します。
    
    ```
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name> -Credential $UserCredential -Authentication Basic -AllowRedirection
    ```

    このコマンドの重要な手順は、レポート情報にアクセスする顧客を指定することです。 この操作は、 _Connectionuri_パラメーターで行います。この場合、最初のドメイン名の FQDN をの値として指定し `?DelegatedOrg=` ます。 この値は、接続先の正しい Exchange Online PowerShell エンドポイントを示します。 リモート PowerShell は、レポートが実行されるたびに、特定の顧客のコンテキストで、Microsoft 365 reporting に接続する必要があります。 Exchange Online の PowerShell に接続すると、これ以降のすべてのコマンドが顧客のコンテキストで実行されます。これにより、お客様に対して利用可能なすべてのレポートにアクセスできるようになります。
    
3. 次のコマンドを実行します。
    
    ```
    Import-PSSession $Session
    ```

> [!NOTE]
> 1 つのアカウントで同時に実行できるセッションは 3 つに制限されています。完了した時点でリモート PowerShell セッションを切断してください。セッションを切断せずに Windows PowerShell ウィンドウを閉じると、使用可能なリモート PowerShell セッションがすべて消費される可能性があるため、セッションの有効期限が切れるまで待つ必要があります。リモート PowerShell セッションを切断するには、次のコマンドを実行します。

```
Remove-PSSession $Session
```
  
## <a name="how-do-you-know-this-worked"></a>正常な動作を確認する方法

手順 3 の後に、Exchange Online コマンドレットがローカル Windows PowerShell セッションにインポートされます。その様子が進行状況バーに表示されます。何もエラーが表示されなければ、正常に接続されています。簡単に確かめるには、Exchange Online コマンドレット (**Get-Mailbox** など) を実行して結果を確認します。
  
エラーが表示された場合は、次の要件を確認します。
  
- よく起きる問題がパスワードの入力ミスです。もう一度 3 つのステップを実行します。特に、ステップ 1 ではユーザー名とパスワードを慎重に入力します。
    
- Exchange Online への接続に使うアカウントは、リモート PowerShell に対して有効になっている必要があります。詳しくは、「[Exchange Online でリモート PowerShell アクセスを管理する](https://go.microsoft.com/fwlink/p/?LinkId=534018)」をご覧ください。
    
- ローカル コンピューターと Exchange Online の間に TCP ポート 80 トラフィックを開く必要があります。組織で厳格なインターネット アクセス ポリシーが使用されている場合は、開いている可能性がありますが、確認する必要があります。
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a>Invoke-Command で直接コマンドレットを呼び出す

PowerShell リモート セッション (手順 3) のインポートは、_すべての_ Exchange Online コマンドレットを取り入れるため、時間がかかる処理になります。これは、(たとえば、さまざまなテナントに対してレポートを実行したり一括変更したりするような) バッチ処理の際に問題になります。**Import-PSSession** を使用する代わりに、**Invoke-Command** で直接使用するコマンドレットを呼び出すことができます。たとえば、**Get-Milbox** コマンドレットを呼び出すには、手順 3 の `Import-PSSession $Session` コマンドの次の構文を置き換えます。
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a>その他のレポート コマンドレット

このトピックで使用したコマンドレットは Windows PowerShell コマンドレットです。これらのコマンドレットの詳細については、以下のトピックを参照してください。
  
- [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [New-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [Import-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [Remove-PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [Set-ExecutionPolicy](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

