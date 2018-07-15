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
# <a name="privileged-access-management-in-office-365"></a>特権にアクセス、Office 365 の管理

> [!IMPORTANT]
> このトピックでは、Office 365 の E5 と高度なコンプライアンスの Sku でのみ現在使用できるパブリック ベータ版の機能の展開と構成のガイダンスについて説明します。

管理者アクセス権を Office 365 の管理により、きめ細かなアクセス特権の管理タスクを制御します。 機密性の高いデータへのアクセスを位置または重要な構成設定へのアクセス権を持つ既存の権限を持つ管理者アカウントを使用するための侵害から組織を保護するために役立ちます。アクセス権限の管理を有効にすると、ユーザーは、承認のワークフローは、高度なスコープ設定と期限付きでの管理者特権、特権のあるタスクを完了する、ジャスト ・ イン ・ タイムのアクセス権を要求する必要があります。これにより、ユーザーだけからだけアクセスできる機密データや重要な構成設定の露出を危険にさらさず、当面のタスクを実行します。Office 365 にアクセス権限の管理を有効にすると、ゼロ位置の特権で実行され、このような地位の管理アクセスのために起因する脆弱性に対する防御層を提供する組織が有効になります。 

このトピックでは、有効にし、Office 365 の組織内のアクセス権限の管理について説明し、要求、承認、および機能を管理するための参考資料としてサービスを提供します。 

## <a name="before-you-begin"></a>はじめに

### <a name="limited-functionality"></a>限られた機能
パブリック ベータ版での管理者アクセス権管理機能は Office 365 では、 [Exchange オンライン PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps)を使用します。特権にアクセス Exchange 管理コマンドレットのレベルでのタスクの定義の管理について説明します。将来的に Office 365 を解放、特権のアクセス機能は、管理ポータルに表示され、他の Office 365 のワークロードのサービスでは、説明します。

### <a name="connecting-to-exchange-online-powershell"></a>PowerShell のオンラインの Exchange への接続
有効にして、Exchange のオンライン PowerShell を使用して Office 365 にアクセス権限を使用してには、このトピックの構成手順が説明します。 

[Exchange オンライン PowerShell への接続は、多要素認証を使用して](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell?view=exchange-ps)Office 365 のアカウント情報を有効にして、組織の管理者のアクセスを構成する Exchange のオンライン PowerShell に接続するための手順に従います。

> [!NOTE]
> オンライン PowerShell を Exchange に接続中にアクセス権限を有効にする手順を使用する Office 365 の組織の多要素認証を有効にする必要はありません。多要素認証で接続する、要求に署名するためのアクセス権限で使用される、OAuth トークンを作成します。

## <a name="enable-and-configure-privileged-access-management"></a>有効にして、アクセス権限の管理を構成します。

### <a name="step-1---create-an-approvers-group"></a>手順 1 - 承認者のグループを作成します。
Office 365 管理ポータルから**のグループ**を選択します > **グループの追加**、特権を持つ既定のアクセスの承認者のメールが有効なセキュリティ グループを作成します。完了したら、作成し、承認者のグループを保存するのには、**追加**を選択します。

![Office 365 管理ポータルにアクセス権限の承認者の画面](images/privileged-access-approvers-ui.png)

> [!NOTE] 
> この時点では、管理者アクセス権を持つユーザーだけできるは Office 365 の管理者のアクセスからの要求を承認します。将来的に、承認者グループの一部になっているユーザーはアクセス権の要求を承認することになります。

### <a name="step-2---enable-privileged-access-in-office-365"></a>手順 2 - Office 365 の管理者のアクセスを有効にします。
アクセス権限を明示的に有効にする既定の承認者グループとアクセス権限の管理アクセスの制御から除外することがシステム アカウントのセットを含む必要があります。 

アクセス権限を有効にして、承認者のグループを割り当てるには、Exchange オンライン PowerShell で次のコマンドを実行します。
```
Enable-ElevatedAccessControl -AdminGroup '<default approver group>' -SystemAccounts @('<systemAccountUPN1>','<systemAccountUPN2>')
```
例:
```
Enable-ElevatedAccessControl -AdminGroup 'pamapprovers@fabrikam.onmicrosoft.com' -SystemAccounts @('sys1@fabrikamorg.onmicrosoft.com', sys2@fabrikamorg.onmicrosoft.com')
```

> [!NOTE]
> システム アカウントの機能は、組織内の特定の自動化を確実に使用可能になりますが、アクセス権限の依存関係を持たない作業できますを推奨するこのような除外される例外的な許可承認および監査する必要があります。普段は。

### <a name="step-3---create-an-approval-policy"></a>手順 3 - 承認ポリシーを作成します。
承認ポリシーを使用すると、特定の承認の要件を個々 のタスクのスコープを定義できます。承認の種類のオプションは、**自動**または**手動**です。 

次のコマンドを実行 Exchange オンライン PowerShell の承認ポリシーを定義します。
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\<exchange management cmdlet name>' -ApprovalType <Manual, Auto> -ApproverGroup '<default/custom approver group>'
```
例:
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\New-MoveRequest' -ApprovalType Manual -ApproverGroup 'mbmanagers@fabrikamorg.onmicrosoft.com'
```

## <a name="using-privileged-access-in-your-office-365-organization"></a>Office 365 組織内のアクセス権限を使用します。

### <a name="requesting-elevation-authorization-to-execute-tasks"></a>タスクを実行する昇格の承認を要求します。
いったん有効に、特権を持つアクセスでは、定義されている関連する承認ポリシーを持つ任意のタスクを実行するための承認が必要です。含まれているタスクを実行するために必要とするユーザーの承認ポリシーが要求する必要があり、タスクを実行するために必要なアクセス許可を持つために、アクセスの承認を付与します。

次のコマンドを実行 Exchange オンライン PowerShell を作成し、承認者のグループに承認依頼を送信します。
```
New-ElevatedAccessRequest -Task 'Exchange\<exchange management cmdlet name>' -Reason '<appropriate reason>' -DurationHours <duration in hours>
```
例:
```
New-ElevatedAccessRequest -Task 'Exchange\New-MoveRequest' -Reason 'Attempting to fix the user mailbox error' -DurationHours 4
```
### <a name="view-status-of-elevation-requests"></a>昇格の要求のステータスを表示
要求 ID に関連付けられているを使用して、昇格の要求の状態を確認できる承認要求が作成されると、

次のコマンドを実行 Exchange オンライン PowerShell は、特定の要求 ID の承認の要求の状態を表示するのには。
```
Get-ElevatedAccessRequest -Identity <request ID> | select RequestStatus
```
例:
```
Get-ElevatedAccessRequest -Identity 28560ed0-419d-4cc3-8f5b-603911cbd450 | select RequestStatus
```

### <a name="approving-an-elevation-authorization-request"></a>昇格の承認要求を承認します。
承認要求が作成されると、関連する承認者グループのメンバーは電子メール通知が表示され、要求 ID に関連付けられている要求を承認することができます。 

次のコマンドを実行 Exchange オンラインの昇格の承認要求を承認する PowerShell:
```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
例:
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```
### <a name="denying-an-elevation-authorization-request"></a>昇格の承認要求を拒否します。
承認要求が作成されると、関連する承認者グループのメンバーは、要求 ID に関連付けられている要求を拒否できます。 

次のコマンドを実行 Exchange オンラインの昇格の承認要求を拒否する PowerShell:
```
Deny-ElevatedAccessRequest -RequestId <request id> -Comment '<denial comment>'
```
例:
```
Deny-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<denial comment>'
```

### <a name="running-the-task"></a>タスクを実行します。
承認を付与すると、要求元のユーザーは、目的のタスクを実行できるとアクセス権限は承認され、ユーザーの代わりにタスクを実行します。承認は、要求の有効期間 (既定の期間は、4 時間) 中に、依頼者が目的のタスクを複数回実行します。このようなすべての実行はログに記録したり、セキュリティとコンプライアンスの監査に使用可能です。 

### <a name="disable-privileged-access-in-office-365"></a>Office 365 の管理者のアクセスを無効にします。
必要な場合は、Office 365 にアクセス権限の管理を無効にできます。特権を無効にするとアクセスは削除されません、関連付けられている承認ポリシーや承認者のグループです。

次のコマンドを実行 Exchange オンライン Powershell へのアクセス権限を無効にします。

```
Disable-ElevatedAccessControl
```
## <a name="managed-access-to-microsoft-graph-in-microsoft-azure"></a>グラフで、Microsoft Azure へのアクセスを管理

> [!IMPORTANT]
> このセクションでは、Office 365 の E5 と高度なコンプライアンスの Sku でのみ現在使用できるパブリック ベータ版の Microsoft Graph 機能の展開と構成のガイダンスについて説明します。

グラフで、Microsoft Azure にアクセスを管理より細かいレベルの Office 365 のデータを細かく制御をより細かく組織を支援するサービスです。このシステムは、アプリケーション開発者はそのデータの分析を偽造できます。 

このシステムでは、管理者による監視を使用してデータを Office 365 にスコープ指定されたアクセスを許可する、承認のワークフローを使用してデータの制御をアサートするのに Office 365 の管理者権限を持ってアクセスを使用します。データに対する要求は、アプリケーションがインストールされ、Office 365 のデータへのアクセスが必要になっています。

### <a name="view-request-details"></a>要求の詳細の表示
Office 365 のデータのアクセス権の要求の詳細を表示します。

次のコマンドを実行 Exchange オンライン Powershell のデータ要求を表示するのには。
```
Get-ElevatedAccessRequest | where {$_.RequestedAccess -like '*Data Access Request*'} | select RequestorUPN, Service, RequestedAccess | fl
```
出力の例:
```
RequestorUPN    : admin@contoso.com
Service         : Office365
RequestedAccess : Data Access Request
```

### <a name="approve-data-access-requests"></a>データ アクセス要求を承認します。
すべてのデータ アクセス要求を承認するには標準のアクセス権限の承認のコマンドレットを使用します。

次のコマンドを実行 Exchange オンライン特定のリクエスターのすべてのデータ要求を承認する Powershell:

```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
例:
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```

## <a name="getting-help-and-providing-feedback"></a>ヘルプを表示し、フィードバックを提供します。
あるパブリック ベータ版の中に、臨時のバグに遭遇は、必要フィードバックとアクセス権限の管理の改善のご提案を認識しています。フィードバックは大切にする私たちと共有することを推奨します。
- [Office プレビュー Yammer グループ](https://www.yammer.com/officeenterprisenda/#/threads/inGroup?type=in_group&feedId=14435206)でのご意見広告のご提案を転記します。
- [Office プレビュー VSO](https://office-previews.visualstudio.com/previews)の区分パス「Office 365 管理者アクセス管理」の下、バグ レポートをファイルします。

## <a name="frequently-asked-questions"></a>よく寄せられる質問

### <a name="what-skus-do-i-need-to-use-privileged-access-in-office-365"></a>Office 365 にアクセス権限を使用する必要があるどのような Sku をしますか。
管理者アクセス権を Office 365 の管理は、現在のみ E5 と高度なコンプライアンスの Sku をご利用できます。

### <a name="when-will-privileged-access-be-available-for-office-365-workloads-beyond-exchange"></a>特権を持つアクセス可能になります Exchange 以外の Office 365 の作業負荷でしょうか。
その他の Office 365 のワークロードでは、この機能をすぐに提供する予定です。タイムラインを共有する準備ができました、Office 365 のロードマップを使用可能ながあります。

### <a name="how-is-this-different-from-azure-active-directorys-privileged-identity-management"></a>どのようにするには Azure Active Directory の管理者の Id 管理とは異なる
特権を持つ別のスコープで、ジャスト ・ イン ・ タイムのアクセス権を持つ Office 365 と[Azure AD 特権 Id 管理](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure)の補数制御のアクセスを提供することで互いの管理にアクセスします。一緒にデータを保護するためのコントロールの堅牢なセットを提供します。

管理者アクセス権を Office 365 の管理を定義し、Azure AD 管理者の Id 管理が複数のタスクを実行する機能をロール レベルで適用されるときに、タスク レベルでは、スコープです。 Azure AD 特権 Id の管理は主に AD の役割と権限の中に役割グループのアクセスを管理する、Office 365 でのアクセス管理をタスク レベルで適用します。

 - **特権を有効にする既に Azure AD 管理者の Id 管理を使用しているときに Office 365 の管理のアクセス:** Office 365 にアクセス権限の管理を追加すると、保護の別の細分化されたレイヤーを提供し、Office 365 のデータへのアクセス権限のための機能を監査できます。

- **を既に使用しているときに、Azure AD の特権の有効にすると Id 管理特権を Office 365 にアクセス管理:** Azure AD 管理者の Id 管理を追加する特権を Office 365 でのアクセス管理は、Office 365 ユーザーのロールまたは id によって主に定義されている外部データへのアクセス権限を拡張できます。 

### <a name="do-i-need-to-be-a-global-admin-to-manage-privileged-access-in-office-365"></a>Office 365 の管理者のアクセスを管理するためのグローバル管理者である必要がありますか。
プレビュー中には、Office 365 の管理者のアクセスを管理することができるグローバル管理者権限を持っている必要があります。承認者のグループに含まれるユーザーに確認および承認の要求をグローバル管理者である必要はありません。 

### <a name="how-is-privileged-access-management-in-office-365-related-to-customer-lockbox"></a>ロック ボックスの顧客に関連する Office 365 にアクセス権限の管理ですか。
[お客様のロック ボックス](https://support.office.com/article/Office-365-Customer-Lockbox-Requests-36f9cdd1-e64c-421b-a7e4-4a54d16440a2)は、組織では、サービス プロバイダー、つまり Microsoft によってデータにアクセスするためのアクセス制御のレベルを使用できます。管理者アクセス権をすべての Office 365 の管理者権限を持って作業を組織内で、きめ細かなアクセス制御により、Office 365 の管理。