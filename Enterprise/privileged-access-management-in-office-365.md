---
title: 特権にアクセス、Office 365 の管理
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 7/13/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Strat_O365_IP
ms.custom: Ent_Solutions
ms.assetid: ''
description: このトピックを使用して、Office 365 にアクセス権限の管理機能の詳細について
ms.openlocfilehash: b2db3e16e53cca7deb2bf8fbff61b5b981f42fa6
ms.sourcegitcommit: b39b8ae3b4268d6475b54e2fdb62982b2c7d9943
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "20319208"
---
# <a name="privileged-access-management-in-office-365"></a><span data-ttu-id="7b2c5-103">特権にアクセス、Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="7b2c5-103">Privileged access management in Office 365</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7b2c5-104">このトピックでは、Office 365 の E5 と高度なコンプライアンスの Sku でのみ現在使用できるパブリック ベータ版の機能の展開と構成のガイダンスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-104">This topic covers deployment and configuration guidance for public beta features only currently available in Office 365 E5 and Advanced Compliance SKUs.</span></span>

<span data-ttu-id="7b2c5-p101">管理者アクセス権を Office 365 の管理により、きめ細かなアクセス特権の管理タスクを制御します。 機密性の高いデータへのアクセスを位置または重要な構成設定へのアクセス権を持つ既存の権限を持つ管理者アカウントを使用するための侵害から組織を保護するために役立ちます。アクセス権限の管理を有効にすると、ユーザーは、承認のワークフローは、高度なスコープ設定と期限付きでの管理者特権、特権のあるタスクを完了する、ジャスト ・ イン ・ タイムのアクセス権を要求する必要があります。これにより、ユーザーだけからだけアクセスできる機密データや重要な構成設定の露出を危険にさらさず、当面のタスクを実行します。Office 365 にアクセス権限の管理を有効にすると、ゼロ位置の特権で実行され、このような地位の管理アクセスのために起因する脆弱性に対する防御層を提供する組織が有効になります。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-p101">Privileged access management allows granular access control over privileged admin tasks in Office 365.  It can help protect your organization from breaches that may use existing privileged admin accounts with standing access to sensitive data or access to critical configuration settings. After enabling privileged access management, users will need to request just-in-time access to complete elevated and privileged tasks through an approval workflow that is highly scoped and time-bound. This gives users just-enough-access to perform the task at hand, without risking exposure of sensitive data or critical configuration settings. Enabling privileged access management in Office 365 will enable your organization to operate with zero standing privileges and provide a layer of defense against vulnerabilities arising because of such standing administrative access.</span></span> 

<span data-ttu-id="7b2c5-110">このトピックでは、有効にし、Office 365 の組織内のアクセス権限の管理について説明し、要求、承認、および機能を管理するための参考資料としてサービスを提供します。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-110">This topic will guide you through enabling and configuring privileged access management in your Office 365 organization and serve as a reference guide for requesting, approving, and managing the feature.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="7b2c5-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="7b2c5-111">Before you begin</span></span>

### <a name="limited-functionality"></a><span data-ttu-id="7b2c5-112">限られた機能</span><span class="sxs-lookup"><span data-stu-id="7b2c5-112">Limited functionality</span></span>
<span data-ttu-id="7b2c5-p102">パブリック ベータ版での管理者アクセス権管理機能は Office 365 では、 [Exchange オンライン PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps)を使用します。特権にアクセス Exchange 管理コマンドレットのレベルでのタスクの定義の管理について説明します。将来的に Office 365 を解放、特権のアクセス機能は、管理ポータルに表示され、他の Office 365 のワークロードのサービスでは、説明します。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-p102">During the public beta, privileged access management features are only available through [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) in Office 365. Privileged access management covers the task definitions at the level of Exchange management cmdlets. In future Office 365 releases, privileged access features will be available through the admin portal and will cover other Office 365 workloads services.</span></span>

### <a name="connecting-to-exchange-online-powershell"></a><span data-ttu-id="7b2c5-116">PowerShell のオンラインの Exchange への接続</span><span class="sxs-lookup"><span data-stu-id="7b2c5-116">Connecting to Exchange Online PowerShell</span></span>
<span data-ttu-id="7b2c5-117">有効にして、Exchange のオンライン PowerShell を使用して Office 365 にアクセス権限を使用してには、このトピックの構成手順が説明します。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-117">The configuration steps in this topic will walk you through enabling and using privileged access in Office 365 using Exchange Online PowerShell.</span></span> 

<span data-ttu-id="7b2c5-118">[Exchange オンライン PowerShell への接続は、多要素認証を使用して](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell?view=exchange-ps)Office 365 のアカウント情報を有効にして、組織の管理者のアクセスを構成する Exchange のオンライン PowerShell に接続するための手順に従います。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-118">Follow the steps in [Connect to Exchange Online PowerShell using Multi-Factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell?view=exchange-ps) to connect to Exchange Online PowerShell with your Office 365 credentials to enable and configure privileged access for your organization.</span></span>

> [!NOTE]
> <span data-ttu-id="7b2c5-p103">オンライン PowerShell を Exchange に接続中にアクセス権限を有効にする手順を使用する Office 365 の組織の多要素認証を有効にする必要はありません。多要素認証で接続する、要求に署名するためのアクセス権限で使用される、OAuth トークンを作成します。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-p103">You do not need to enable multi-factor authentication for your Office 365 organization to use the steps to enable privileged access while connecting to Exchange Online PowerShell. Connecting with multi-factor authentication creates an OAuth token that is used by privileged access for signing your requests.</span></span>

## <a name="enable-and-configure-privileged-access-management"></a><span data-ttu-id="7b2c5-121">有効にして、アクセス権限の管理を構成します。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-121">Enable and configure privileged access management</span></span>

### <a name="step-1---create-an-approvers-group"></a><span data-ttu-id="7b2c5-122">手順 1 - 承認者のグループを作成します。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-122">Step 1 - Create an approver's group</span></span>
<span data-ttu-id="7b2c5-p104">Office 365 管理ポータルから**のグループ**を選択します > **グループの追加**、特権を持つ既定のアクセスの承認者のメールが有効なセキュリティ グループを作成します。完了したら、作成し、承認者のグループを保存するのには、**追加**を選択します。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-p104">From Office 365 Admin Portal, select **Groups** > **Add a group**, then create a mail enabled security group for the default privileged access approvers. When complete, select **Add** to create and save the approver group.</span></span>

![Office 365 管理ポータルにアクセス権限の承認者の画面](images/privileged-access-approvers-ui.png)

> [!NOTE] 
> <span data-ttu-id="7b2c5-p105">この時点では、管理者アクセス権を持つユーザーだけできるは Office 365 の管理者のアクセスからの要求を承認します。将来的に、承認者グループの一部になっているユーザーはアクセス権の要求を承認することになります。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-p105">At this time, only users with administrative access are allowed to approve requests from Office 365 priviledged access. In future any user who is part of the Approvers’ group will be able to approve access requests.</span></span>

### <a name="step-2---enable-privileged-access-in-office-365"></a><span data-ttu-id="7b2c5-128">手順 2 - Office 365 の管理者のアクセスを有効にします。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-128">Step 2 - Enable privileged access in Office 365</span></span>
<span data-ttu-id="7b2c5-129">アクセス権限を明示的に有効にする既定の承認者グループとアクセス権限の管理アクセスの制御から除外することがシステム アカウントのセットを含む必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-129">Privileged access needs to be explicitly turned on with the default approver group and including a set of system accounts that you’d want to be excluded from the privileged access management access control.</span></span> 

<span data-ttu-id="7b2c5-130">アクセス権限を有効にして、承認者のグループを割り当てるには、Exchange オンライン PowerShell で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-130">Run the following command in Exchange Online PowerShell to enable privileged access and to assign the approver's group:</span></span>
```
Enable-ElevatedAccessControl -AdminGroup '<default approver group>' -SystemAccounts @('<systemAccountUPN1>','<systemAccountUPN2>')
```
<span data-ttu-id="7b2c5-131">例:</span><span class="sxs-lookup"><span data-stu-id="7b2c5-131">Example:</span></span>
```
Enable-ElevatedAccessControl -AdminGroup 'pamapprovers@fabrikam.onmicrosoft.com' -SystemAccounts @('sys1@fabrikamorg.onmicrosoft.com', sys2@fabrikamorg.onmicrosoft.com')
```

> [!NOTE]
> <span data-ttu-id="7b2c5-132">システム アカウントの機能は、組織内の特定の自動化を確実に使用可能になりますが、アクセス権限の依存関係を持たない作業できますを推奨するこのような除外される例外的な許可承認および監査する必要があります。普段は。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-132">System accounts feature is made available to ensure certain automations within your organizations can work without dependency on privileged access, however it is recommended that such exclusions be exceptional and those allowed should be approved and audited regularly.</span></span>

### <a name="step-3---create-an-approval-policy"></a><span data-ttu-id="7b2c5-133">手順 3 - 承認ポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-133">Step 3 - Create an approval policy</span></span>
<span data-ttu-id="7b2c5-p106">承認ポリシーを使用すると、特定の承認の要件を個々 のタスクのスコープを定義できます。承認の種類のオプションは、**自動**または**手動**です。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-p106">An approval policy allows you to define the specific approval requirements scoped at individual tasks. The approval type options are **Auto** or **Manual**.</span></span> 

<span data-ttu-id="7b2c5-136">次のコマンドを実行 Exchange オンライン PowerShell の承認ポリシーを定義します。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-136">Run the following command in Exchange Online PowerShell to define an approval policy:</span></span>
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\<exchange management cmdlet name>' -ApprovalType <Manual, Auto> -ApproverGroup '<default/custom approver group>'
```
<span data-ttu-id="7b2c5-137">例:</span><span class="sxs-lookup"><span data-stu-id="7b2c5-137">Example:</span></span>
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\New-MoveRequest' -ApprovalType Manual -ApproverGroup 'mbmanagers@fabrikamorg.onmicrosoft.com'
```

## <a name="using-privileged-access-in-your-office-365-organization"></a><span data-ttu-id="7b2c5-138">Office 365 組織内のアクセス権限を使用します。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-138">Using privileged access in your Office 365 organization</span></span>

### <a name="requesting-elevation-authorization-to-execute-tasks"></a><span data-ttu-id="7b2c5-139">タスクを実行する昇格の承認を要求します。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-139">Requesting elevation authorization to execute tasks</span></span>
<span data-ttu-id="7b2c5-p107">いったん有効に、特権を持つアクセスでは、定義されている関連する承認ポリシーを持つ任意のタスクを実行するための承認が必要です。含まれているタスクを実行するために必要とするユーザーの承認ポリシーが要求する必要があり、タスクを実行するために必要なアクセス許可を持つために、アクセスの承認を付与します。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-p107">Once enabled, privileged access requires approvals for executing any task that has an associated approval policy defined. Users needing to execute tasks included in the an approval policy must request and be granted access approval in order to have permissions necessary to execute the task.</span></span>

<span data-ttu-id="7b2c5-142">次のコマンドを実行 Exchange オンライン PowerShell を作成し、承認者のグループに承認依頼を送信します。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-142">Run the following command in Exchange Online PowerShell to create and submit an approval request to the approver's group:</span></span>
```
New-ElevatedAccessRequest -Task 'Exchange\<exchange management cmdlet name>' -Reason '<appropriate reason>' -DurationHours <duration in hours>
```
<span data-ttu-id="7b2c5-143">例:</span><span class="sxs-lookup"><span data-stu-id="7b2c5-143">Example:</span></span>
```
New-ElevatedAccessRequest -Task 'Exchange\New-MoveRequest' -Reason 'Attempting to fix the user mailbox error' -DurationHours 4
```
### <a name="view-status-of-elevation-requests"></a><span data-ttu-id="7b2c5-144">昇格の要求のステータスを表示</span><span class="sxs-lookup"><span data-stu-id="7b2c5-144">View status of elevation requests</span></span>
<span data-ttu-id="7b2c5-145">要求 ID に関連付けられているを使用して、昇格の要求の状態を確認できる承認要求が作成されると、</span><span class="sxs-lookup"><span data-stu-id="7b2c5-145">After an approval request is created, elevation request status can be reviewed using the associated with request ID.</span></span>

<span data-ttu-id="7b2c5-146">次のコマンドを実行 Exchange オンライン PowerShell は、特定の要求 ID の承認の要求の状態を表示するのには。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-146">Run the following command in Exchange Online PowerShell to view a approval request status for a specific request ID:</span></span>
```
Get-ElevatedAccessRequest -Identity <request ID> | select RequestStatus
```
<span data-ttu-id="7b2c5-147">例:</span><span class="sxs-lookup"><span data-stu-id="7b2c5-147">Example:</span></span>
```
Get-ElevatedAccessRequest -Identity 28560ed0-419d-4cc3-8f5b-603911cbd450 | select RequestStatus
```

### <a name="approving-an-elevation-authorization-request"></a><span data-ttu-id="7b2c5-148">昇格の承認要求を承認します。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-148">Approving an elevation authorization request</span></span>
<span data-ttu-id="7b2c5-149">承認要求が作成されると、関連する承認者グループのメンバーは電子メール通知が表示され、要求 ID に関連付けられている要求を承認することができます。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-149">When an approval request is created, members of the relevant approver group will receive an email notification and can approve the request associated with the request ID.</span></span> 

<span data-ttu-id="7b2c5-150">次のコマンドを実行 Exchange オンラインの昇格の承認要求を承認する PowerShell:</span><span class="sxs-lookup"><span data-stu-id="7b2c5-150">Run the following command in Exchange Online PowerShell to approve an elevation authorization request:</span></span>
```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
<span data-ttu-id="7b2c5-151">例:</span><span class="sxs-lookup"><span data-stu-id="7b2c5-151">Example:</span></span>
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```
### <a name="denying-an-elevation-authorization-request"></a><span data-ttu-id="7b2c5-152">昇格の承認要求を拒否します。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-152">Denying an elevation authorization request</span></span>
<span data-ttu-id="7b2c5-153">承認要求が作成されると、関連する承認者グループのメンバーは、要求 ID に関連付けられている要求を拒否できます。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-153">When an approval request is created, members of the relevant approver group can deny the request associated with the request ID.</span></span> 

<span data-ttu-id="7b2c5-154">次のコマンドを実行 Exchange オンラインの昇格の承認要求を拒否する PowerShell:</span><span class="sxs-lookup"><span data-stu-id="7b2c5-154">Run the following command in Exchange Online PowerShell to deny an elevation authorization request:</span></span>
```
Deny-ElevatedAccessRequest -RequestId <request id> -Comment '<denial comment>'
```
<span data-ttu-id="7b2c5-155">例:</span><span class="sxs-lookup"><span data-stu-id="7b2c5-155">Example:</span></span>
```
Deny-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<denial comment>'
```

### <a name="running-the-task"></a><span data-ttu-id="7b2c5-156">タスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-156">Running the task</span></span>
<span data-ttu-id="7b2c5-p108">承認を付与すると、要求元のユーザーは、目的のタスクを実行できるとアクセス権限は承認され、ユーザーの代わりにタスクを実行します。承認は、要求の有効期間 (既定の期間は、4 時間) 中に、依頼者が目的のタスクを複数回実行します。このようなすべての実行はログに記録したり、セキュリティとコンプライアンスの監査に使用可能です。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-p108">After approval is granted, the requesting user can execute the intended task and privileged access will authorize and execute the task on users’ behalf. The approval remains valid for the requested duration (default duration is 4 hours), during which the requester can execute the intended task multiple times. All such executions are logged and made available for security and compliance auditing.</span></span> 

### <a name="disable-privileged-access-in-office-365"></a><span data-ttu-id="7b2c5-160">Office 365 の管理者のアクセスを無効にします。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-160">Disable privileged access in Office 365</span></span>
<span data-ttu-id="7b2c5-p109">必要な場合は、Office 365 にアクセス権限の管理を無効にできます。特権を無効にするとアクセスは削除されません、関連付けられている承認ポリシーや承認者のグループです。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-p109">If needed, you can disable privileged access management in Office 365. Disabling privileged access does not delete any associated approval policies or approver groups.</span></span>

<span data-ttu-id="7b2c5-163">次のコマンドを実行 Exchange オンライン Powershell へのアクセス権限を無効にします。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-163">Run the following command in Exchange Online Powershell to disable privileged access:</span></span>

```
Disable-ElevatedAccessControl
```
## <a name="managed-access-to-microsoft-graph-in-microsoft-azure"></a><span data-ttu-id="7b2c5-164">グラフで、Microsoft Azure へのアクセスを管理</span><span class="sxs-lookup"><span data-stu-id="7b2c5-164">Managed access to Microsoft Graph in Microsoft Azure</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7b2c5-165">このセクションでは、Office 365 の E5 と高度なコンプライアンスの Sku でのみ現在使用できるパブリック ベータ版の Microsoft Graph 機能の展開と構成のガイダンスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-165">This section covers deployment and configuration guidance for a public beta Microsoft Graph feature only currently available in Office 365 E5 and Advanced Compliance SKUs.</span></span>

<span data-ttu-id="7b2c5-p110">グラフで、Microsoft Azure にアクセスを管理より細かいレベルの Office 365 のデータを細かく制御をより細かく組織を支援するサービスです。このシステムは、アプリケーション開発者はそのデータの分析を偽造できます。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-p110">Managed access to Microsoft Graph in Microsoft Azure is a service that helps organizations exert a granular level of control over their Office 365 data. This system allows application developers to forge insights with that data.</span></span> 

<span data-ttu-id="7b2c5-p111">このシステムでは、管理者による監視を使用してデータを Office 365 にスコープ指定されたアクセスを許可する、承認のワークフローを使用してデータの制御をアサートするのに Office 365 の管理者権限を持ってアクセスを使用します。データに対する要求は、アプリケーションがインストールされ、Office 365 のデータへのアクセスが必要になっています。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-p111">This system uses Office 365 privileged access to assert control over their data through its approval workflow, allowing scoped access to Office 365 data with admin oversight. Requests for data come in when applications are installed and require access to Office 365 data.</span></span>

### <a name="view-request-details"></a><span data-ttu-id="7b2c5-170">要求の詳細の表示</span><span class="sxs-lookup"><span data-stu-id="7b2c5-170">View request details</span></span>
<span data-ttu-id="7b2c5-171">Office 365 のデータのアクセス権の要求の詳細を表示します。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-171">View details of the access requests for Office 365 data.</span></span>

<span data-ttu-id="7b2c5-172">次のコマンドを実行 Exchange オンライン Powershell のデータ要求を表示するのには。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-172">Run the following command in Exchange Online Powershell to view data requests:</span></span>
```
Get-ElevatedAccessRequest | where {$_.RequestedAccess -like '*Data Access Request*'} | select RequestorUPN, Service, RequestedAccess | fl
```
<span data-ttu-id="7b2c5-173">出力の例:</span><span class="sxs-lookup"><span data-stu-id="7b2c5-173">Example output:</span></span>
```
RequestorUPN    : admin@contoso.com
Service         : Office365
RequestedAccess : Data Access Request
```

### <a name="approve-data-access-requests"></a><span data-ttu-id="7b2c5-174">データ アクセス要求を承認します。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-174">Approve data access requests</span></span>
<span data-ttu-id="7b2c5-175">すべてのデータ アクセス要求を承認するには標準のアクセス権限の承認のコマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-175">All data access requests can be approved through the standard privileged access approval cmdlets.</span></span>

<span data-ttu-id="7b2c5-176">次のコマンドを実行 Exchange オンライン特定のリクエスターのすべてのデータ要求を承認する Powershell:</span><span class="sxs-lookup"><span data-stu-id="7b2c5-176">Run the following command in Exchange Online Powershell to approve all data requests for specific requestor:</span></span>

```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
<span data-ttu-id="7b2c5-177">例:</span><span class="sxs-lookup"><span data-stu-id="7b2c5-177">Example:</span></span>
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```

## <a name="getting-help-and-providing-feedback"></a><span data-ttu-id="7b2c5-178">ヘルプを表示し、フィードバックを提供します。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-178">Getting help and providing feedback</span></span>
<span data-ttu-id="7b2c5-p112">あるパブリック ベータ版の中に、臨時のバグに遭遇は、必要フィードバックとアクセス権限の管理の改善のご提案を認識しています。フィードバックは大切にする私たちと共有することを推奨します。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-p112">We recognize that during the public beta you may come across an occasional bug or have feedback and suggestions on how we can improve privileged access management. We value your feedback and encourage you to share it with us:</span></span>
- <span data-ttu-id="7b2c5-181">[Office プレビュー Yammer グループ](https://www.yammer.com/officeenterprisenda/#/threads/inGroup?type=in_group&feedId=14435206)でのご意見広告のご提案を転記します。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-181">Post your feedback ad suggestions in the [Office Preview Yammer Group](https://www.yammer.com/officeenterprisenda/#/threads/inGroup?type=in_group&feedId=14435206).</span></span>
- <span data-ttu-id="7b2c5-182">[Office プレビュー VSO](https://office-previews.visualstudio.com/previews)の区分パス「Office 365 管理者アクセス管理」の下、バグ レポートをファイルします。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-182">File your bug reports under area path “Office 365 Privileged Access Management” on the [Office Preview VSO](https://office-previews.visualstudio.com/previews).</span></span>

## <a name="frequently-asked-questions"></a><span data-ttu-id="7b2c5-183">よく寄せられる質問</span><span class="sxs-lookup"><span data-stu-id="7b2c5-183">Frequently asked questions</span></span>

### <a name="what-skus-do-i-need-to-use-privileged-access-in-office-365"></a><span data-ttu-id="7b2c5-184">Office 365 にアクセス権限を使用する必要があるどのような Sku をしますか。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-184">What SKUs do I need to use privileged access in Office 365?</span></span>
<span data-ttu-id="7b2c5-185">管理者アクセス権を Office 365 の管理は、現在のみ E5 と高度なコンプライアンスの Sku をご利用できます。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-185">Privileged access management in Office 365 is currently only available for customers with E5 and Advanced Compliance SKUs.</span></span>

### <a name="when-will-privileged-access-be-available-for-office-365-workloads-beyond-exchange"></a><span data-ttu-id="7b2c5-186">特権を持つアクセス可能になります Exchange 以外の Office 365 の作業負荷でしょうか。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-186">When will privileged access be available for Office 365 workloads beyond Exchange?</span></span>
<span data-ttu-id="7b2c5-p113">その他の Office 365 のワークロードでは、この機能をすぐに提供する予定です。タイムラインを共有する準備ができました、Office 365 のロードマップを使用可能ながあります。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-p113">We plan to offer this feature in other Office 365 workloads soon. When we’re ready to share a timeline, it will be available through the Office 365 roadmap.</span></span>

### <a name="how-is-this-different-from-azure-active-directorys-privileged-identity-management"></a><span data-ttu-id="7b2c5-189">どのようにするには Azure Active Directory の管理者の Id 管理とは異なる</span><span class="sxs-lookup"><span data-stu-id="7b2c5-189">How is this different from Azure Active Directory’s Privileged Identity Management?</span></span>
<span data-ttu-id="7b2c5-p114">特権を持つ別のスコープで、ジャスト ・ イン ・ タイムのアクセス権を持つ Office 365 と[Azure AD 特権 Id 管理](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure)の補数制御のアクセスを提供することで互いの管理にアクセスします。一緒にデータを保護するためのコントロールの堅牢なセットを提供します。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-p114">Privileged access management in Office 365 and [Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure) complement each other by providing access control with just-in-time access at different scopes. Together they provide a robust set of controls for protecting your data.</span></span>

<span data-ttu-id="7b2c5-p115">管理者アクセス権を Office 365 の管理を定義し、Azure AD 管理者の Id 管理が複数のタスクを実行する機能をロール レベルで適用されるときに、タスク レベルでは、スコープです。 Azure AD 特権 Id の管理は主に AD の役割と権限の中に役割グループのアクセスを管理する、Office 365 でのアクセス管理をタスク レベルで適用します。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-p115">Privileged access management in Office 365 can be defined and scoped at the task level, while Azure AD Privileged Identity Management applies at the role level with the ability to execute multiple tasks.  Azure AD Privileged Identity Management primarily allows managing accesses for AD roles and role groups while privileged access management in Office 365 is applied at the task level.</span></span>

 - <span data-ttu-id="7b2c5-194">**特権を有効にする既に Azure AD 管理者の Id 管理を使用しているときに Office 365 の管理のアクセス:** Office 365 にアクセス権限の管理を追加すると、保護の別の細分化されたレイヤーを提供し、Office 365 のデータへのアクセス権限のための機能を監査できます。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-194">**Enabling privileged access management in Office 365 while already using Azure AD Privileged Identity Management:** Adding privileged access management in Office 365 can provide another granular layer of protection and audit capabilities for privileged access to Office 365 data.</span></span>

- <span data-ttu-id="7b2c5-195">**を既に使用しているときに、Azure AD の特権の有効にすると Id 管理特権を Office 365 にアクセス管理:** Azure AD 管理者の Id 管理を追加する特権を Office 365 でのアクセス管理は、Office 365 ユーザーのロールまたは id によって主に定義されている外部データへのアクセス権限を拡張できます。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-195">**Enabling Azure AD Privileged Identity Management while already using privileged access management in Office 365:**  Adding Azure AD Privileged Identity Management to privileged access management in Office 365 can extend privileged access to data outside of Office 365 that’s primarily defined by a user’s role or identity.</span></span> 

### <a name="do-i-need-to-be-a-global-admin-to-manage-privileged-access-in-office-365"></a><span data-ttu-id="7b2c5-196">Office 365 の管理者のアクセスを管理するためのグローバル管理者である必要がありますか。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-196">Do I need to be a Global Admin to manage privileged access in Office 365?</span></span>
<span data-ttu-id="7b2c5-p116">プレビュー中には、Office 365 の管理者のアクセスを管理することができるグローバル管理者権限を持っている必要があります。承認者のグループに含まれるユーザーに確認および承認の要求をグローバル管理者である必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-p116">During the preview you need to have Global Admin privilege to be able to manage privileged access in Office 365. Users who are included in an approvers’ group don't need to be a Global Admin to review and approve requests.</span></span> 

### <a name="how-is-privileged-access-management-in-office-365-related-to-customer-lockbox"></a><span data-ttu-id="7b2c5-199">ロック ボックスの顧客に関連する Office 365 にアクセス権限の管理ですか。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-199">How is privileged access management in Office 365 related to Customer Lockbox?</span></span>
<span data-ttu-id="7b2c5-p117">[お客様のロック ボックス](https://support.office.com/article/Office-365-Customer-Lockbox-Requests-36f9cdd1-e64c-421b-a7e4-4a54d16440a2)は、組織では、サービス プロバイダー、つまり Microsoft によってデータにアクセスするためのアクセス制御のレベルを使用できます。管理者アクセス権をすべての Office 365 の管理者権限を持って作業を組織内で、きめ細かなアクセス制御により、Office 365 の管理。</span><span class="sxs-lookup"><span data-stu-id="7b2c5-p117">[Customer Lockbox](https://support.office.com/article/Office-365-Customer-Lockbox-Requests-36f9cdd1-e64c-421b-a7e4-4a54d16440a2) allows a level of access control for organizations for access to to data by their service provider, i.e. Microsoft. Privileged access management in Office 365 allows granular access control within an organization for all Office 365 privileged tasks.</span></span>