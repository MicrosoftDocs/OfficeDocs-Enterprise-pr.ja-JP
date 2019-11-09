---
title: Office 365 SharePoint Online データの削除
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
- SPO_Content
description: SharePoint Online でのデータ削除についての説明。
ms.openlocfilehash: 94b70d34cb05f98dfa560761dec87a919720dca9
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "38078156"
---
# <a name="sharepoint-online-data-deletion-in-office-365"></a>Office 365 での SharePoint Online データの削除

SharePoint Online は、オブジェクトをアプリケーションデータベース内に抽象化されたコードとして格納します。 ユーザーがファイルを SharePoint Online にアップロードすると、そのファイルは逆アセンブルされ、複数のデータベースにわたって複数のテーブルに格納されて、アプリケーションコードに変換されます。 SharePoint Online では、お客様がアップロードしたすべてのコンテンツがチャンクに分割され、暗号化 (複数の AES 256 ビットキーを使用している可能性があります) され、データセンター全体に分散されます。 チャンク処理と暗号化プロセスの詳細については、「 [Microsoft Cloud での暗号化](https://docs.microsoft.com/microsoft-365/compliance/office-365-encryption-in-the-microsoft-cloud-overview)」を参照してください。 

SharePoint Online では、アイテムは元の場所から削除した時点から93日後に保持されます。 これらのユーザーは、そこから削除したりごみ箱を空にしたりしない限り、すべての時間をサイトのごみ箱に保持します。 その場合、アイテムはサイトコレクションのごみ箱に移動されます。その後、残りの93日間は保持されます。 削除済みアイテムの復元の詳細については、「 [SharePoint サイトのごみ箱のアイテムを復元](https://support.office.com/article/6df466b6-55f2-4898-8d6e-c0dff851a0be#ID0EAADAAA=Online
)する」と「[削除済みのアイテムをサイトコレクションのごみ箱から復元](https://support.office.com/article/5fa924ee-16d7-487b-9a0a-021b9062d14b)する」を参照してください。 ごみ箱の保存期間は、SharePoint Online では構成できません。

サイトコレクションを削除すると、コレクション内のサイトの階層とその中のすべてのコンテンツも削除されます。

- ドキュメントおよびドキュメント ライブラリ
- リストとリストデータ
- サイトの構成設定
- サイトまたはそのサブサイトに関連するロールおよびセキュリティ情報
- トップレベル web サイトのサブサイト、それらのコンテンツ、およびユーザー情報

サイトコレクションを誤って削除した場合は、SharePoint 管理センターを使用して、グローバルまたは SharePoint 管理者がサイトコレクションを復元できます。 

ハード削除は、ユーザーがサイトコレクションのごみ箱から削除されたアイテムを削除したとき、保持とバックアップの期間が経過したとき、または管理者が[remove-spodeletedsite コマンドレット](/powershell/module/sharepoint-online/Remove-SPODeletedSite?view=sharepoint-ps)を使用してサイトコレクションを完全に削除したときに発生します。 ユーザーが SharePoint Online からコンテンツを物理的に削除 (完全に削除、またはパージ) すると、削除されたチャンクのすべての暗号化キーも削除されます。 以前に削除されたチャンクを格納していたディスク上のブロックは未使用としてマークされ、再利用できるようになります。
