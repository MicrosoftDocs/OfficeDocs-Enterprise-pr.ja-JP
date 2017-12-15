---
title: "委任アクセス許可 (DAP) パートナー用リモート Windows PowerShell で Exchange Online テナントに接続する"
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: "概要:リモート Windows PowerShell で DelegatedOrg パラメーターを使用して、Exchange Online に接続します。"
ms.openlocfilehash: 9bb6a5a316f4bc23c6586da825b8755cf755f484
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a>委任アクセス許可 (DAP) パートナー用リモート Windows PowerShell で Exchange Online テナントに接続する

 **の概要:**_DelegatedOrg_パラメーターを使用して Exchange Online に接続するには、リモートの Windows PowerShell を使用します。
  
リモート Windows PowerShell を使用すると、Exchange Online の設定をコマンド ラインから管理できます。ローカル コンピューターで Windows PowerShell を使用して Exchange Online へのリモート セッションを作成します。これは、Exchange Online 資格情報を入力して、必要な接続設定を指定してから、Exchange Online コマンドレットをローカル Windows PowerShell セッションにインポートしてそれらを使用できるようにするという単純な 3 段階プロセスです。
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>始める前に把握しておくべき情報

- 予想所要時間 : 5 分
    
- 次の Windows のバージョンを使用できます。
    
  - Windows 10
    
  - Windows 8.1 または Windows 8
    
  - Windows Server 2012 R2 または Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    * .NET Framework 4.5.1 や .NET Framework 4.5 をインストールしてから、Windows Management Framework 3.0 と Windows Management Framework 4.0 のどちらかをインストールする必要があります。詳しくは、次のリソースをご覧ください。
    
  - [.NET Framework のインストール](https://go.microsoft.com/fwlink/p/?LinkId=257868)
    
  - [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) か[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)
    
- このトピックの手順に適用されるキーボード ショートカットについては、「[Exchange 管理センターのキーボード ショートカット](https://go.microsoft.com/fwlink/p/?LinkId=534017)」をご覧ください。
    
## 

> [!IMPORTANT]
> この手順は委任アクセス許可 (DAP) パートナーのみを対象にしています。DAP パートナー以外のユーザーの場合は、この手順を使わないでください。 
  
DAP パートナーとは、シンジケート パートナーとクラウド ソリューション プロバイダー (CSP) パートナーです。他の会社のネットワーク プロバイダーまたは通信プロバイダーであることもよくあります。それらのパートナーは、顧客に提供するサービスにサブスクリプションをバンドルします。代理で管理 (AOBO) 権限を Office 365顧客テナンシーに自動的に付与して、すべての顧客のテナンシーを管理し報告できるようにするパートナー テナンシーを所有しています。
  
## <a name="connect-to-exchange-online"></a>Exchange Online に接続する

1. ローカル コンピューターで、Windows PowerShell を開き、次のコマンドを実行します。
    
  ```
  $UserCredential = Get-Credential
  ```

    **[Windows PowerShell 資格情報の要求]** ダイアログ ボックスで、DAP 管理者のユーザー名とパスワードを入力してから **[OK]** をクリックします。
    
2. 次のコマンドを実行する交換_<customer tenant domain name>_への接続に使用するテナント ドメインの名前を持つ。
    
  ```
  $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name>-Credential $UserCredential -Authentication Basic -AllowRedirection
  ```

    このコマンドの主要な手順では、レポートの情報にアクセスする顧客を指定します。これは  _ConnectionURI_ パラメーターで実行します。ここでは、 _DelegatedOrg_ パラメーターの値として、最初のドメイン名の FQDN を指定します。これにより、Exchange Online PowerShell のリモート Windows PowerShell のリモート Windows PowerShell に、接続先のエンドポイントが伝えられます。リモート Windows PowerShell は、レポートを実行するたびに、特定の顧客のコンテキストで Office 365 のレポートに接続する必要があります。この顧客を指定すると、次のコマンドはすべてこの顧客のコンテキストで実行されます。これにより、パートナーは、この顧客で使用可能なすべてのレポートにアクセスできるようになります。
    
3. 次のコマンドを実行します。
    
  ```
  Import-PSSession $Session
  ```

> [!NOTE]
> 1 つのアカウントで同時に実行できるセッションは 3 つに制限されています。完了した時点でリモート Windows PowerShell セッションを切断してください。セッションを切断せずに Windows PowerShell ウィンドウを閉じると、使用可能なリモート Windows PowerShell セッションがすべて消費される可能性があるため、セッションの有効期限が切れるまで待つ必要があります。リモート Windows PowerShell セッションを切断するには、次のコマンドを実行します。 >  `Remove-PSSession $Session`
  
## <a name="how-do-you-know-this-worked"></a>正常な動作を確認する方法

手順 3 の後に、Exchange Online コマンドレットがローカル Windows PowerShell セッションにインポートされます。その様子がプログレスバーに表示されます。何もエラーが表示されなければ、正常に接続されています。簡単に確かめるには、Exchange Online コマンドレット ( **Get-Mailbox** など) を実行して結果を確認します。
  
エラーが表示された場合は、次の要件を確認します。
  
- よく起きる問題がパスワードの入力ミスです。もう一度 3 つのステップを実行します。特に、ステップ 1 ではユーザー名とパスワードを慎重に入力します。
    
- サービス拒否 (DoS) 攻撃を防止するため、Exchange Online 組織に対して開かれる Windows PowerShell のリモート接続は 3 つに制限されています。
    
- スクリプトを実行するためには、Windows PowerShell を構成する必要があります。この設定は、コンピューターで一度だけ構成すれば、接続ごとに行う必要はありません。Windows PowerShell で署名されたスクリプトの実行を有効にするには、管理者特権の Windows PowerShell ウィンドウ ( **[管理者として実行]** を選択すると開く Windows PowerShell ウィンドウ) で次のコマンドを実行します。
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

- Exchange Online への接続に使うアカウントは、リモート Windows PowerShell に対して有効になっている必要があります。詳しくは、「[Exchange Online でリモート PowerShell アクセスを管理する](https://go.microsoft.com/fwlink/p/?LinkId=534018)」をご覧ください。
    
- ローカル コンピューターと Exchange Online の間に TCP ポート 80 トラフィックを開く必要があります。組織で厳格なインターネット アクセス ポリシーが使用されている場合は、開いている可能性がありますが、確認する必要があります。
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a>Invoke-Command で直接コマンドレットを呼び出す

Windows PowerShell リモート セッションのインポートは、すべての Exchange Online コマンドレットを取り入れるため時間がかかる処理になります。これは、たとえば、さまざまなテナントに対してレポートを実行したり一括変更したりするようなバッチ処理の際に問題になります。 **Import-PSSession** を使用する代わりに、 **Invoke-Command** で直接使用するコマンドレットを呼び出すことができます。たとえば、 **get-mailbox** コマンドレットを呼び出すには、 `Import-PSSession $Session` の次の構文を置き換えます。
  
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
    

