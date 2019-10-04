---
title: Office 365 のメールボックスの移行
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: Office 365 メールボックスの移行に使用されるコマンドレットの概要を簡単に説明します。
ms.openlocfilehash: bdd4d6eb68a8727dc26a693f2716ed602e7a5a60
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067582"
---
# <a name="office-365-mailbox-migrations"></a><span data-ttu-id="0987c-103">Office 365 のメールボックスの移行</span><span class="sxs-lookup"><span data-stu-id="0987c-103">Office 365 Mailbox Migrations</span></span>
<span data-ttu-id="0987c-104">Exchange ベースのハイブリッド展開では、オンプレミスの Exchange メールボックスを[Exchange online](https://docs.microsoft.com/Exchange/exchange-online)組織に移動するか、exchange online メールボックスを exchange[のオンプレミス](https://docs.microsoft.com/Exchange/exchange-server)の組織に移動するかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="0987c-104">With an Exchange-based hybrid deployment, customers can choose to either move on-premises Exchange mailboxes to an [Exchange Online](https://docs.microsoft.com/Exchange/exchange-online) organization or move Exchange Online mailboxes to an [Exchange on-premises](https://docs.microsoft.com/Exchange/exchange-server) organization.</span></span> <span data-ttu-id="0987c-105">移行バッチは、オンプレミスの組織と Exchange Online 組織間でメールボックスを移動するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="0987c-105">Migration batches are used when moving mailboxes between on-premises and Exchange Online organizations.</span></span>

<span data-ttu-id="0987c-106">お客様は、次のコマンドレットを使用して、メールボックスの移行に関する統計情報やその他の情報を確認できます。</span><span class="sxs-lookup"><span data-stu-id="0987c-106">Customers can review statistics and other information about mailbox migrations with the following cmdlets:</span></span>

- <span data-ttu-id="0987c-107">[Get-moverequeststatistics](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MoveRequestStatistics?view=exchange-ps): ユーザーメールボックスの既定の統計情報を提供します。これには、ステータス、メールボックスのサイズ、アーカイブメールボックスのサイズ、完了率が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0987c-107">[Get-MoveRequestStatistics](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MoveRequestStatistics?view=exchange-ps): Provides default statistics for a user mailbox, which includes the status, mailbox size, archive mailbox size, and percentage complete.</span></span>
- <span data-ttu-id="0987c-108">[Get メールボックス](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Get-Mailbox?view=exchange-ps
): 組織内のメールボックスオブジェクトと属性の要約リストを提供します。</span><span class="sxs-lookup"><span data-stu-id="0987c-108">[Get-Mailbox](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Get-Mailbox?view=exchange-ps
): Provides a summary list of mailbox objects and attributes in the organization.</span></span>
- <span data-ttu-id="0987c-109">[Get-Recipient](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient?view=exchange-ps): メールボックス、メールユーザー、連絡先、配布グループなどの既存のメールが有効なオブジェクトの一覧を提供します。</span><span class="sxs-lookup"><span data-stu-id="0987c-109">[Get-Recipient](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient?view=exchange-ps): Provides a list of existing mail-enabled objects such as mailboxes, mail users, contacts, and distribution groups.</span></span>
- <span data-ttu-id="0987c-110">[New-moverequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MoveRequest?view=exchange-ps): 継続的なメールボックスの移行の詳細な状態を提供します。</span><span class="sxs-lookup"><span data-stu-id="0987c-110">[Get-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MoveRequest?view=exchange-ps): Provides a detailed status of an ongoing mailbox migration.</span></span>
- <span data-ttu-id="0987c-111">[MigrationUser](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MigrationUser?view=exchange-ps): メールボックスの移動と移行のユーザーに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="0987c-111">[Get-MigrationUser](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MigrationUser?view=exchange-ps): Provides information about the mailbox move and migration users.</span></span>
- <span data-ttu-id="0987c-112">[New-migrationbatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MigrationBatch?view=exchange-ps): 現在の移行バッチの状態に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="0987c-112">[Get-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MigrationBatch?view=exchange-ps): Provides information on the status of current migration batch.</span></span>
- <span data-ttu-id="0987c-113">[Get-migrationuserstatistics](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MigrationUserStatistics?view=exchange-ps): 特定のユーザーの移行状態に関する詳細情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="0987c-113">[Get-MigrationUserStatistics](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MigrationUserStatistics?view=exchange-ps): Provides detailed information about the migration status for a specific user.</span></span>
- <span data-ttu-id="0987c-114">[Get-mailboxstatistics](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Get-MailboxStatistics?view=exchange-ps): サイズ、メッセージ数、最終アクセス日時などのメールボックスに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="0987c-114">[Get-MailboxStatistics](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Get-MailboxStatistics?view=exchange-ps): Provides information about mailboxes, such as size, the number of messages, and the last accessed time.</span></span>

<span data-ttu-id="0987c-115">コマンドレットの詳細については、「[移動と移行のコマンドレット (Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0987c-115">For more information about cmdlets, see [Move and Migration cmdlets in Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps).</span></span>