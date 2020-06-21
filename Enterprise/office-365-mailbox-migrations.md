---
title: Microsoft 365 メールボックスの移行
ms.author: josephd
author: JoeDavies-MSFT
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
f1.keywords:
- NOCSH
description: Microsoft 365 メールボックスの移行に使用されるコマンドレットの簡単な概要。
ms.openlocfilehash: 4c53737f4047df0751c4216b57d772bd6fe8acad
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774902"
---
# <a name="microsoft-365-mailbox-migrations"></a>Microsoft 365 メールボックスの移行

Exchange ベースのハイブリッド展開では、オンプレミスの Exchange メールボックスを[Exchange online](https://docs.microsoft.com/Exchange/exchange-online)組織に移動するか、exchange online メールボックスを exchange[のオンプレミス](https://docs.microsoft.com/Exchange/exchange-server)の組織に移動するかを選択できます。 移行バッチは、オンプレミスの組織と Exchange Online 組織間でメールボックスを移動するときに使用されます。

お客様は、次のコマンドレットを使用して、メールボックスの移行に関する統計情報やその他の情報を確認できます。

- [Get-moverequeststatistics](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MoveRequestStatistics?view=exchange-ps): ユーザーメールボックスの既定の統計情報を提供します。これには、ステータス、メールボックスのサイズ、アーカイブメールボックスのサイズ、完了率が含まれます。
- [Get メールボックス](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Get-Mailbox?view=exchange-ps
): 組織内のメールボックスオブジェクトと属性の要約リストを提供します。
- [Get-Recipient](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/Get-Recipient?view=exchange-ps): メールボックス、メールユーザー、連絡先、配布グループなどの既存のメールが有効なオブジェクトの一覧を提供します。
- [New-moverequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MoveRequest?view=exchange-ps): 継続的なメールボックスの移行の詳細な状態を提供します。
- [MigrationUser](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MigrationUser?view=exchange-ps): メールボックスの移動と移行のユーザーに関する情報を提供します。
- [New-migrationbatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MigrationBatch?view=exchange-ps): 現在の移行バッチの状態に関する情報を提供します。
- [Get-migrationuserstatistics](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/Get-MigrationUserStatistics?view=exchange-ps): 特定のユーザーの移行状態に関する詳細情報を提供します。
- [Get-mailboxstatistics](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Get-MailboxStatistics?view=exchange-ps): サイズ、メッセージ数、最終アクセス日時などのメールボックスに関する情報を提供します。

コマンドレットの詳細については、「[移動と移行のコマンドレット (Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps))」を参照してください。
