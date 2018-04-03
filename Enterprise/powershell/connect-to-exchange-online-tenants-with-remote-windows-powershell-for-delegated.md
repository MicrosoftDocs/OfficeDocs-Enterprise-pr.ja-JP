---
title: 委任アクセス許可 (DAP) パートナー用リモート Windows PowerShell で Exchange Online テナントに接続する
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: 概要:リモート Windows PowerShell で DelegatedOrg パラメーターを使用して、Exchange Online に接続します。
ms.openlocfilehash: d8cbb6640419ba2f1de868ae88b0a273c3f71ae7
ms.sourcegitcommit: f3f81d2c2e8290948d93f3f787a679c804840256
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2018
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="239ae-103">委任アクセス許可 (DAP) パートナー用リモート Windows PowerShell で Exchange Online テナントに接続する</span><span class="sxs-lookup"><span data-stu-id="239ae-103">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="239ae-104">**概要:** リモート Windows PowerShell で _DelegatedOrg_ パラメーターを使用して、Exchange Online に接続します。</span><span class="sxs-lookup"><span data-stu-id="239ae-104">**Summary:** Use remote Windows PowerShell to connect to Exchange Online by using the _DelegatedOrg_ parameter.</span></span>
  
<span data-ttu-id="239ae-p101">リモート Windows PowerShell を使用すると、Exchange Online の設定をコマンド ラインから管理できます。ローカル コンピューターで Windows PowerShell を使用して Exchange Online へのリモート セッションを作成します。これは、Exchange Online 資格情報を入力して、必要な接続設定を指定してから、Exchange Online コマンドレットをローカル Windows PowerShell セッションにインポートしてそれらを使用できるようにするという単純な 3 段階プロセスです。</span><span class="sxs-lookup"><span data-stu-id="239ae-p101">Remote Windows PowerShell lets you manage your Exchange Online settings from the command line. You use Windows PowerShell on your local computer to create a remote session to Exchange Online. It's a three-step process where you enter your Exchange Online credentials, provide the required connection settings, and then import the Exchange Online cmdlets into your local Windows PowerShell session so that you can use them.</span></span>
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="239ae-108">始める前に把握しておくべき情報</span><span class="sxs-lookup"><span data-stu-id="239ae-108">What do you need to know before you begin?</span></span>

- <span data-ttu-id="239ae-109">予想所要時間 : 5 分</span><span class="sxs-lookup"><span data-stu-id="239ae-109">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="239ae-110">次の Windows のバージョンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="239ae-110">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="239ae-111">Windows 10</span><span class="sxs-lookup"><span data-stu-id="239ae-111">Windows 10</span></span>
    
  - <span data-ttu-id="239ae-112">Windows 8.1 または Windows 8</span><span class="sxs-lookup"><span data-stu-id="239ae-112">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="239ae-113">Windows Server 2012 R2 または Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="239ae-113">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="239ae-114">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="239ae-114">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="239ae-115">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="239ae-115">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="239ae-p102">\* .NET Framework 4.5.1 や .NET Framework 4.5 をインストールしてから、Windows Management Framework 3.0 と Windows Management Framework 4.0 のどちらかをインストールする必要があります。詳しくは、次のリソースをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="239ae-p102">\*You need to install the .NET Framework 4.5.1 or the .NET Framework 4.5 and then either the Windows Management Framework 4.0 or the Windows Management Framework 3.0 . For more information, see the following resources:</span></span>
    
    - [<span data-ttu-id="239ae-118">.NET Framework のインストール</span><span class="sxs-lookup"><span data-stu-id="239ae-118">Installing the .NET Framework</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=257868)
    
    - <span data-ttu-id="239ae-119">[Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) または [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)</span><span class="sxs-lookup"><span data-stu-id="239ae-119">[Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)</span></span>
    
- <span data-ttu-id="239ae-120">このトピックの手順に適用されるキーボード ショートカットについては、「[Exchange 管理センターのキーボード ショートカット](https://go.microsoft.com/fwlink/p/?LinkId=534017)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="239ae-120">For information about keyboard shortcuts that might apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](https://go.microsoft.com/fwlink/p/?LinkId=534017).</span></span>
    
## 

> [!IMPORTANT]
> <span data-ttu-id="239ae-p103">この手順は委任アクセス許可 (DAP) パートナーのみを対象にしています。DAP パートナー以外のユーザーの場合は、この手順を使わないでください。</span><span class="sxs-lookup"><span data-stu-id="239ae-p103">This procedure is only for Delegated Access Permission (DAP) partners. If you are not a DAP partner, do not use this procedure.</span></span> 
  
<span data-ttu-id="239ae-p104">DAP パートナーとは、シンジケート パートナーとクラウド ソリューション プロバイダー (CSP) パートナーです。他の会社のネットワーク プロバイダーまたは通信プロバイダーであることもよくあります。それらのパートナーは、顧客に提供するサービスにサブスクリプションをバンドルします。代理で管理 (AOBO) 権限を Office 365顧客テナンシーに自動的に付与して、すべての顧客のテナンシーを管理し報告できるようにするパートナー テナンシーを所有しています。</span><span class="sxs-lookup"><span data-stu-id="239ae-p104">DAP partners are Syndication and Cloud Solution Providers (CSP) partners. They are frequently network or telecom providers to other companies. They bundle subscriptions into their service offerings to their customers. They own a partner tenancy that is automatically granted Administer On Behalf Of (AOBO) permissions to their Office 365customer tenancies so they can administer and report on all of their customer tenancies.</span></span>
  
## <a name="connect-to-exchange-online"></a><span data-ttu-id="239ae-127">Exchange Online に接続する</span><span class="sxs-lookup"><span data-stu-id="239ae-127">Connect to Exchange Online</span></span>

1. <span data-ttu-id="239ae-128">ローカル コンピューターで、Windows PowerShell を開き、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="239ae-128">On your local computer, open Windows PowerShell and run the following command.</span></span>
    
  ```
  $UserCredential = Get-Credential
  ```

    <span data-ttu-id="239ae-129">**[Windows PowerShell 資格情報の要求]** ダイアログ ボックスで、DAP 管理者のユーザー名とパスワードを入力してから **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="239ae-129">In the **Windows PowerShell Credential Request** dialog box, enter your DAP administrator user name and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="239ae-130">_<customer tenant domain name>_ を接続先のテナントのドメイン名に置き換えて、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="239ae-130">Run the following command, replacing  _<customer tenant domain name>_ with the name of the tenant domain that you want to connect to.</span></span>
    
  ```
  $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name>-Credential $UserCredential -Authentication Basic -AllowRedirection
  ```

    <span data-ttu-id="239ae-p105">このコマンドの主要な手順では、レポートの情報にアクセスする顧客を指定します。これは  _ConnectionURI_ パラメーターで実行します。ここでは、 _DelegatedOrg_ パラメーターの値として、最初のドメイン名の FQDN を指定します。これにより、Exchange Online PowerShell のリモート Windows PowerShell のリモート Windows PowerShell に、接続先のエンドポイントが伝えられます。リモート Windows PowerShell は、レポートを実行するたびに、特定の顧客のコンテキストで Office 365 のレポートに接続する必要があります。この顧客を指定すると、次のコマンドはすべてこの顧客のコンテキストで実行されます。これにより、パートナーは、この顧客で使用可能なすべてのレポートにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="239ae-p105">The key step in this command is specifying which customer to access for the reporting information. You do this in the  _ConnectionURI_ parameter, where you provide the FQDN of the initial domain name as the value to the _DelegatedOrg_ parameter. This tells remote Windows PowerShell for Exchange Online PowerShell remote Windows PowerShell the endpoint to connect to. remote Windows PowerShell must connect to Office 365 reporting in the context of a specific customer each time a report is run. After this customer is specified, all of the following commands are run in the context of that customer. This lets the partner to access all the available reports for this customer.</span></span>
    
3. <span data-ttu-id="239ae-137">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="239ae-137">Run the following command.</span></span>
    
  ```
  Import-PSSession $Session
  ```

> [!NOTE]
> <span data-ttu-id="239ae-p106">1 つのアカウントで同時に実行できるセッションは 3 つに制限されています。完了した時点でリモート Windows PowerShell セッションを切断してください。セッションを切断せずに Windows PowerShell ウィンドウを閉じると、使用可能なリモート Windows PowerShell セッションがすべて消費される可能性があるため、セッションの有効期限が切れるまで待つ必要があります。リモート Windows PowerShell セッションを切断するには、次のコマンドを実行します。 >  `Remove-PSSession $Session`</span><span class="sxs-lookup"><span data-stu-id="239ae-p106">There is a limit of three simultaneous sessions that can run under one account. Be sure to disconnect the remote Windows PowerShell session when you're finished. If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote Windows PowerShell sessions available to you, and you'll need to wait for the sessions to expire. To disconnect the remote Windows PowerShell session, run the following command. >  `Remove-PSSession $Session`</span></span>
  
## <a name="how-do-you-know-this-worked"></a><span data-ttu-id="239ae-142">正常な動作を確認する方法</span><span class="sxs-lookup"><span data-stu-id="239ae-142">How do you know this worked?</span></span>

<span data-ttu-id="239ae-p107">手順 3 の後に、Exchange Online コマンドレットがローカル Windows PowerShell セッションにインポートされます。その様子がプログレスバーに表示されます。何もエラーが表示されなければ、正常に接続されています。簡単に確かめるには、Exchange Online コマンドレット ( **Get-Mailbox** など) を実行して結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="239ae-p107">After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar. If you don't receive any errors, you connected successfully. A quick test is to run an Exchange Online cmdlet—for example, **Get-Mailbox** —and see the results.</span></span>
  
<span data-ttu-id="239ae-146">エラーが表示された場合は、次の要件を確認します。</span><span class="sxs-lookup"><span data-stu-id="239ae-146">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="239ae-p108">よく起きる問題がパスワードの入力ミスです。もう一度 3 つのステップを実行します。特に、ステップ 1 ではユーザー名とパスワードを慎重に入力します。</span><span class="sxs-lookup"><span data-stu-id="239ae-p108">A common problem is an incorrect password. Run the three steps again and pay close attention to the user name and password you enter in Step 1.</span></span>
    
- <span data-ttu-id="239ae-149">サービス拒否 (DoS) 攻撃を防止するため、Exchange Online 組織に対して開かれる Windows PowerShell のリモート接続は 3 つに制限されています。</span><span class="sxs-lookup"><span data-stu-id="239ae-149">To help prevent denial-of-service (DoS) attacks, you're limited to three open remote Windows PowerShell connections to your Exchange Online organization.</span></span>
    
- <span data-ttu-id="239ae-p109">スクリプトを実行するためには、Windows PowerShell を構成する必要があります。この設定は、コンピューターで一度だけ構成すれば、接続ごとに行う必要はありません。Windows PowerShell で署名されたスクリプトの実行を有効にするには、管理者特権の Windows PowerShell ウィンドウ ( **[管理者として実行]** を選択すると開く Windows PowerShell ウィンドウ) で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="239ae-p109">Windows PowerShell needs to be configured to run scripts. You need to configure this setting only once on your computer, not every time you connect. To enable Windows PowerShell to run signed scripts, run the following command in an elevated Windows PowerShell window (a Windows PowerShell window you opened by selecting **Run as administrator**).</span></span>
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

- <span data-ttu-id="239ae-p110">Exchange Online への接続に使うアカウントは、リモート Windows PowerShell に対して有効になっている必要があります。詳しくは、「[Exchange Online でリモート PowerShell アクセスを管理する](https://go.microsoft.com/fwlink/p/?LinkId=534018)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="239ae-p110">The account you use to connect to Exchange Online must be enabled for remote Windows PowerShell. For more information, see [Manage Remote PowerShell Access in Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span></span>
    
- <span data-ttu-id="239ae-p111">ローカル コンピューターと Exchange Online の間に TCP ポート 80 トラフィックを開く必要があります。組織で厳格なインターネット アクセス ポリシーが使用されている場合は、開いている可能性がありますが、確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="239ae-p111">TCP port 80 traffic needs to be open between your local computer and Exchange Online. It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.</span></span>
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a><span data-ttu-id="239ae-157">Invoke-Command で直接コマンドレットを呼び出す</span><span class="sxs-lookup"><span data-stu-id="239ae-157">Call the cmdlet directly with Invoke-Command</span></span>

<span data-ttu-id="239ae-p112">Windows PowerShell リモート セッションのインポートは、すべての Exchange Online コマンドレットを取り入れるため時間がかかる処理になります。これは、たとえば、さまざまなテナントに対してレポートを実行したり一括変更したりするようなバッチ処理の際に問題になります。 **Import-PSSession** を使用する代わりに、 **Invoke-Command** で直接使用するコマンドレットを呼び出すことができます。たとえば、 **get-mailbox** コマンドレットを呼び出すには、 `Import-PSSession $Session` の次の構文を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="239ae-p112">Importing a remote Windows PowerShell session can be a lengthy process because it brings in all Exchange Online cmdlets. This can be an issue in batch processing—for example, when you are running reports or making bulk changes for different tenants. As an alternative to using **Import-PSSession**, you can call cmdlets you want to use directly with **Invoke-Command**. For example, to call the **get-mailbox** cmdlet, substitute this syntax for `Import-PSSession $Session`.</span></span>
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a><span data-ttu-id="239ae-162">その他のレポート コマンドレット</span><span class="sxs-lookup"><span data-stu-id="239ae-162">More reporting cmdlets</span></span>

<span data-ttu-id="239ae-p113">このトピックで使用したコマンドレットは Windows PowerShell コマンドレットです。これらのコマンドレットの詳細については、以下のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="239ae-p113">The cmdlets that you used in this topic are Windows PowerShell cmdlets. For more information about these cmdlets, see the following topics:</span></span>
  
- [<span data-ttu-id="239ae-165">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="239ae-165">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [<span data-ttu-id="239ae-166">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="239ae-166">New-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [<span data-ttu-id="239ae-167">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="239ae-167">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [<span data-ttu-id="239ae-168">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="239ae-168">Remove-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [<span data-ttu-id="239ae-169">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="239ae-169">Set-ExecutionPolicy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

