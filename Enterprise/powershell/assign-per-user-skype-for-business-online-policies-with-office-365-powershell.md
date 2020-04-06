---
title: Office 365 PowerShell を使用してユーザーごとに Skype for Business Online のポリシーを割り当てる
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: 概要:Office 365 PowerShell を使用して、ユーザーごとに Skype for Business Online のポリシーを適用した通信の設定を割り当てます。
ms.openlocfilehash: 615deca2790e206e6cf117283321307aa01eac74
ms.sourcegitcommit: f2aefbc2dbbe969fea9db3a4c558651496532413
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/05/2020
ms.locfileid: "43146812"
---
# <a name="assign-per-user-skype-for-business-online-policies-with-office-365-powershell"></a><span data-ttu-id="1631c-103">Office 365 PowerShell を使用してユーザーごとに Skype for Business Online のポリシーを割り当てる</span><span class="sxs-lookup"><span data-stu-id="1631c-103">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>

<span data-ttu-id="1631c-104">Office 365 PowerShell を使用することで、効率的にユーザーごとに Skype for Business Online のポリシーを適用した通信の設定を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="1631c-104">Using Office 365 PowerShell is an efficient way to assign per-user communication settings with Skype for Business Online policies.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="1631c-105">はじめに</span><span class="sxs-lookup"><span data-stu-id="1631c-105">Before you begin</span></span>

<span data-ttu-id="1631c-106">次の手順にしたがってコマンドを実行するためのセットアップを行います (すでに終わっている場合はこれらの手順は省略可能です)。</span><span class="sxs-lookup"><span data-stu-id="1631c-106">Use these instructions to get set up to run the commands (skip the steps you have already completed):</span></span>
  
1. <span data-ttu-id="1631c-107">[Skype for Business Online Connector モジュール](https://www.microsoft.com/download/details.aspx?id=39366)をダウンロードしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="1631c-107">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366).</span></span>
    
2. <span data-ttu-id="1631c-108">Windows PowerShell コマンド プロンプトを開いて次のコマンドを実行します:</span><span class="sxs-lookup"><span data-stu-id="1631c-108">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
```powershell
Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
```

<span data-ttu-id="1631c-109">ダイアログ ボックスが表示されたら、Skype for Business Online 管理者のアカウント名とパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="1631c-109">When prompted, enter your Skype for Business Online administrator account name and password.</span></span>
    
## <a name="updating-external-communication-settings-for-a-user-account"></a><span data-ttu-id="1631c-110">ユーザー アカウントの外部通信設定を更新する</span><span class="sxs-lookup"><span data-stu-id="1631c-110">Updating external communication settings for a user account</span></span>

<span data-ttu-id="1631c-p101">ユーザー アカウントの外部通信設定を変更するとします。たとえば、Alex がフェデレーション ユーザーと通信できるようにする (EnableFederationAccess を True に設定) と同時に、Windows Live ユーザーとは通信できないようにするとします (EnablePublicCloudAccess を False に設定)。この場合、次の 2 つの手順が必要になります。</span><span class="sxs-lookup"><span data-stu-id="1631c-p101">Suppose you want to change external communication settings on a user account. For example, you want to allow Alex to communicate with federated users (EnableFederationAccess is equal to True) but not with Windows Live users (EnablePublicCloudAccess equals False). To do that, you need to do two things:</span></span>
  
1. <span data-ttu-id="1631c-114">この条件を満たす外部アクセス ポリシーを探す。</span><span class="sxs-lookup"><span data-stu-id="1631c-114">Find an external access policy that meets our criteria.</span></span>
    
2. <span data-ttu-id="1631c-115">その外部アクセス ポリシーを Alex に割り当てる。</span><span class="sxs-lookup"><span data-stu-id="1631c-115">Assign that external access policy to Alex.</span></span>
    
> [!NOTE]
>  <span data-ttu-id="1631c-p102">自分だけのカスタム ポリシーを作成することはできません。これは、Skype for Business Online がカスタム ポリシーの作成を許可していないためです。代わりに、Office 365 用に特別に作成されたポリシーの 1 つを割り当てる必要があります。このように事前に作成されたポリシーは次のとおりです。4 種類のクライアント ポリシー、224 種類の会議ポリシー、5 種類のダイヤル プラン、5 種類の外部アクセス ポリシー、1 つのホスト型ボイスメール ポリシー、4 種類の音声ポリシー。</span><span class="sxs-lookup"><span data-stu-id="1631c-p102">You can't create a custom policy all our own. That's because Skype for Business Online does not allow you to create custom policies. Instead, you must assign one of the policies that were created specifically for Office 365. Those pre-created policies include: 4 different client policies, 224 different conferencing policies, 5 different dial plans, 5 different external access policies, 1 hosted voicemail policy, and 4 different voice policies.</span></span>
  
<span data-ttu-id="1631c-p103">Alex に割り当てる外部アクセス ポリシーを特定するにはどうしたらいいでしょうか。次のコマンドは、EnableFederationAccess が True に設定され、EnablePublicCloudAccess が False に設定されたすべての外部アクセス ポリシーを返します。</span><span class="sxs-lookup"><span data-stu-id="1631c-p103">So how do you determine which external access policy to assign Alex? The following command returns all the external access policies where EnableFederationAccess is set to True and EnablePublicCloudAccess is set to False:</span></span>
  
```powershell
Get-CsExternalAccessPolicy | Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

<span data-ttu-id="1631c-p104">このコマンドでは、EnableFederationAccess プロパティが True に設定され、EnablePublicCloudAccess プロパティが False に設定されているという 2 つの条件を満たしているすべてのポリシーを返します。こうして、このコマンドは指定された条件を満たす 1 つのポリシー (FederationOnly) を返します。以下に例を示します。</span><span class="sxs-lookup"><span data-stu-id="1631c-p104">What the command does is return all the policies that meet two criteria: the EnableFederationAccess property is set to True, and the EnablePublicCloudAccess policy is set to False. In turn, that command returns one policy that meets our criteria (FederationOnly). Here is an example:</span></span>
  
```powershell
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

> [!NOTE]
> <span data-ttu-id="1631c-p105">ポリシー ID は Tag:FederationOnly になっています。ただし、Tag: プレフィックスは Microsoft Lync 2013 に対して実行された早期プレリリース作業から継承されたものです。ユーザーに対するポリシーの割り当てに関して言えば、Tag: プレフィックスを削除してポリシー名の FederationOnly だけを使用すべきです。</span><span class="sxs-lookup"><span data-stu-id="1631c-p105">The policy Identity says Tag:FederationOnly. As it turns out, the Tag: prefix is a carryover from the early pre-release work done on Microsoft Lync 2013. When it comes to assigning policies to users, you should delete the Tag: prefix and use just the policy name: FederationOnly.</span></span> 
  
<span data-ttu-id="1631c-p106">これで、Alex に割り当てるポリシーが特定されたため、このポリシーを [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974) コマンドレットを使用して割り当てることができます。以下に例を示します。</span><span class="sxs-lookup"><span data-stu-id="1631c-p106">Now that you know which policy to assign to Alex, we can assign that policy by using the [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974) cmdlet. Here is an example:</span></span>
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

<span data-ttu-id="1631c-130">ポリシーの割り当ては簡単にでき、割り当てるユーザーの ID とポリシー名を指定するだけでポリシーを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="1631c-130">Assigning a policy is pretty simple: you simply specify the Identity of the user and the name of the policy to be assigned.</span></span> 
  
<span data-ttu-id="1631c-p107">ポリシーとポリシー割り当てに関して言えば、一度に処理するユーザー アカウントの数は 1 つに制限されません。たとえば、フェデレーション パートナーおよび Windows Live ユーザーとの通信が許可されているすべてのユーザーのリストが必要だとします。このようなユーザーには外部ユーザー アクセス ポリシーの FederationAndPICDefault が割り当てられていることはすでにわかっています。それがわかっているため、1 つの単純なコマンドを実行するだけで、このようなすべてのユーザーのリストを表示することができます。以下にコマンドを示します。</span><span class="sxs-lookup"><span data-stu-id="1631c-p107">And when it comes to policies and policy assignments, you're not limited to working with user accounts one a time. For example, suppose you need a list of all the users who are allowed to communicate with federated partners and with Windows Live users. We already know that those users have been assigned the external user access policy FederationAndPICDefault. Because we know that, you can display a list of all those users by running one simple command. Here is the command:</span></span>
  
```powershell
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

<span data-ttu-id="1631c-p108">つまり、ExternalAccessPolicy プロパティが FederationAndPICDefault に設定されているすべてのユーザーが表示されます (画面上に表示される情報量を制限するには、Select-Object コマンドレットを使用して各ユーザーの表示名だけを出力するようにします)。</span><span class="sxs-lookup"><span data-stu-id="1631c-p108">In other words, show us all the users where the ExternalAccessPolicy property is set to FederationAndPICDefault. (And, in order to limit the amount of information that appears onscreen, use the Select-Object cmdlet to display show us only each user's display name.)</span></span> 
  
<span data-ttu-id="1631c-138">すべてのユーザー アカウントが同じポリシーを使用するように構成する場合は次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="1631c-138">To configure all our user accounts to use that same policy, use this command:</span></span>
  
```powershell
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

<span data-ttu-id="1631c-139">このコマンドでは、Get-CsOnlineUser を使用して、Lync に対して有効になっているすべてのユーザーのコレクションを返します。その後、そのすべての情報が Grant-CsExternalAccessPolicy に送信され、FederationAndPICDefault ポリシーがコレクション内のすべてのユーザーそれぞれに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="1631c-139">This command uses Get-CsOnlineUser to return a collection of all the users who have been enabled for Lync, then sends all that information to Grant-CsExternalAccessPolicy, which assigns the FederationAndPICDefault policy to each and every user in the collection.</span></span>
  
<span data-ttu-id="1631c-p109">もう一つの例として、Alex にすでに FederationAndPICDefault ポリシーを割り当てていたものの、グローバルな外部アクセス ポリシーで管理することにしたとします。グローバル ポリシーは誰かに明示的に割り当てることはできません。他のユーザーごとのポリシーが割り当てられていない場合にのみ使用されます。つまり、Alex をグローバル ポリシーで管理する場合は、事前に彼に割り当てられたユーザーごとのポリシーを *解除する*  必要があります。コマンドの例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="1631c-p109">As an additional example, suppose you've previously assigned Alex the FederationAndPICDefault policy and now you've changed your mind and would like him to be managed by the global external access policy. You can't explicitly assign the global policy to anyone. It is only used if no other per-user policy is assigned. Therefore, if we want Alex to be managed by the global policy, you need to  *unassign*  any per-user policy previously assigned to him. Here is an example command:</span></span>
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

<span data-ttu-id="1631c-p110">このコマンドでは、Alex に割り当てられた外部アクセス ポリシーの名前を Null 値 ($Null) に設定します。Null は "何もない" という意味です。言い換えれば、どの外部アクセス ポリシーも Alex に割り当てられていないということになります。どの外部アクセス ポリシーもユーザーに割り当てられていなければ、そのユーザーはグローバル ポリシーによって管理されます。</span><span class="sxs-lookup"><span data-stu-id="1631c-p110">This command sets the name of the external access policy assigned to Alex to a null value ($Null). Null means "nothing". In other words, no external access policy is assigned to Alex. When no external access policy is assigned to a user, that user then gets managed by the global policy.</span></span>
  
<span data-ttu-id="1631c-p111">Windows PowerShell を使用してユーザー アカウントを削除するには、Azure Active Directory コマンドレットを使用して Alex の Skype for Business Online ライセンスを削除します。詳しくは、「[Office 365 PowerShell を使ったサービスへのアクセスを無効にする](assign-licenses-to-user-accounts-with-office-365-powershell.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1631c-p111">To disable a user account using Windows PowerShell, use the Azure Active Directory cmdlets to remove Alex's Skype for Business Online license. For more information, see [Disable access to services with Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md).</span></span>

## <a name="managing-large-numbers-of-users"></a><span data-ttu-id="1631c-151">多数のユーザーを管理する</span><span class="sxs-lookup"><span data-stu-id="1631c-151">Managing large numbers of users</span></span>

<span data-ttu-id="1631c-152">多数のユーザー (1000 以上) を管理するには、[コマンド](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-7)レットを使用してスクリプトブロックでコマンドをバッチ処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1631c-152">To manage large numbers of users (1000 or more), you need to batch the commands via a script block using the [Invoke-Command](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-7) cmdlet.</span></span>  <span data-ttu-id="1631c-153">前の例では、コマンドレットが実行されるたびに、呼び出しを設定し、その結果が返されるまで待機してから、再度送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1631c-153">In previous examples, each time a cmdlet is executed, it must set up the call and then wait for the result before sending it back.</span></span>  <span data-ttu-id="1631c-154">スクリプトブロックを使用すると、コマンドレットをリモートで実行し、完了したらデータを返送できます。</span><span class="sxs-lookup"><span data-stu-id="1631c-154">When using a script block, this allows the cmdlets to be executed remotely, and once completed, send the data back.</span></span> 

```powershell
Import-Module LyncOnlineConnector
$sfbSession = New-CsOnlineSession
$users = Get-CsOnlineUser -Filter { ClientPolicy -eq $null } -ResultSize 500

$batch = 50
$filter = ''
$total = $users.Count
$count = 0
    $users | ForEach-Object {
    $upn = $_.UserPrincipalName
    $filter += "(UserPrincipalName -eq '$upn')"
    $batch--
    $count++
    if (($batch -eq 0) -or ($count -eq $total)) {
        $filterSB=[ScriptBlock]::Create($filter)
        Invoke-Command -Session $s -ScriptBlock {param($f) Get-CsOnlineUser -filter $f | Grant-CsClientPolicy -PolicyName "ClientPolicyNoIMURL" -Passthru | Grant-CsExternalAccessPolicy -PolicyName "FederationAndPICDefault"} -ArgumentList $filterSB

        # Reset
        $batch = 50
        $filter = ''
    } else {
        $filter += " -or "
    }
}
```

<span data-ttu-id="1631c-155">これにより、クライアントポリシーを持たない時間に500ユーザーが検索されます。</span><span class="sxs-lookup"><span data-stu-id="1631c-155">This will find 500 users at a time who do not have a client policy.</span></span> <span data-ttu-id="1631c-156">これにより、クライアントポリシー "ClientPolicyNoIMURL" と "FederationAndPicDefault" という外部アクセスポリシーが付与されます。</span><span class="sxs-lookup"><span data-stu-id="1631c-156">It will grant them the client policy "ClientPolicyNoIMURL" and the external access policy "FederationAndPicDefault".</span></span> <span data-ttu-id="1631c-157">結果は50のグループにバッチ処理され、50の各バッチがリモートコンピューターに送信されます。</span><span class="sxs-lookup"><span data-stu-id="1631c-157">The results are batched into groups of 50 and each batch of 50 is then sent to the remote machine.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1631c-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="1631c-158">See also</span></span>

[<span data-ttu-id="1631c-159">Office 365 PowerShell を使用して Skype for Business Online を管理する</span><span class="sxs-lookup"><span data-stu-id="1631c-159">Manage Skype for Business Online with Office 365 PowerShell</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)
  
[<span data-ttu-id="1631c-160">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="1631c-160">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="1631c-161">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="1631c-161">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
