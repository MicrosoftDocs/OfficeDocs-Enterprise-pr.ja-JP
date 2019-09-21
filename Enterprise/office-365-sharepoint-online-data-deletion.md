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
description: SharePoint Online でのデータ削除についての説明。
ms.openlocfilehash: ff219654387a17598f1ada8c866a005d8d4f5449
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067629"
---
# <a name="sharepoint-online-data-deletion-in-office-365"></a><span data-ttu-id="becc1-103">Office 365 での SharePoint Online データの削除</span><span class="sxs-lookup"><span data-stu-id="becc1-103">SharePoint Online Data Deletion in Office 365</span></span>

<span data-ttu-id="becc1-104">SharePoint Online は、オブジェクトをアプリケーションデータベース内に抽象化されたコードとして格納します。</span><span class="sxs-lookup"><span data-stu-id="becc1-104">SharePoint Online stores objects as abstracted code within application databases.</span></span> <span data-ttu-id="becc1-105">ユーザーがファイルを SharePoint Online にアップロードすると、そのファイルは逆アセンブルされ、複数のデータベースにわたって複数のテーブルに格納されて、アプリケーションコードに変換されます。</span><span class="sxs-lookup"><span data-stu-id="becc1-105">When a user uploads a file to SharePoint Online, that file is disassembled and translated into application code and stored in multiple tables across multiple databases.</span></span> <span data-ttu-id="becc1-106">SharePoint Online では、お客様がアップロードしたすべてのコンテンツがチャンクに分割され、暗号化 (複数の AES 256 ビットキーを使用している可能性があります) され、データセンター全体に分散されます。</span><span class="sxs-lookup"><span data-stu-id="becc1-106">In SharePoint Online, all content that a customer uploads is broken into chunks, encrypted (potentially with multiple AES 256-bit keys), and distributed across the datacenter.</span></span> <span data-ttu-id="becc1-107">チャンク処理と暗号化プロセスの詳細については、「 [Microsoft Cloud での暗号化](/microsoft-365/compliance/office-365-encryption-in-the-microsoft-cloud-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="becc1-107">For specific details about the chunking and encryption process, see [Encryption in the Microsoft Cloud](/microsoft-365/compliance/office-365-encryption-in-the-microsoft-cloud-overview.md).</span></span> 

<span data-ttu-id="becc1-108">SharePoint Online では、アイテムは元の場所から削除した時点から93日後に保持されます。</span><span class="sxs-lookup"><span data-stu-id="becc1-108">In SharePoint Online, items are retained for 93 days from the time you delete them from their original location.</span></span> <span data-ttu-id="becc1-109">これらのユーザーは、そこから削除したりごみ箱を空にしたりしない限り、すべての時間をサイトのごみ箱に保持します。</span><span class="sxs-lookup"><span data-stu-id="becc1-109">They stay in the site Recycle Bin the entire time, unless someone deletes them from there or empties that Recycle Bin.</span></span> <span data-ttu-id="becc1-110">その場合、アイテムはサイトコレクションのごみ箱に移動されます。その後、残りの93日間は保持されます。</span><span class="sxs-lookup"><span data-stu-id="becc1-110">In that case, the items go to the site collection Recycle Bin, where they stay for the remainder of the 93 days.</span></span> <span data-ttu-id="becc1-111">削除済みアイテムの復元の詳細については、「 [SharePoint サイトのごみ箱のアイテムを復元](https://support.office.com/en-us/article/6df466b6-55f2-4898-8d6e-c0dff851a0be#ID0EAADAAA=Online
)する」と「[削除済みのアイテムをサイトコレクションのごみ箱から復元](https://support.office.com/article/5fa924ee-16d7-487b-9a0a-021b9062d14b)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="becc1-111">For info about restoring deleted items, see [Restore items in the Recycle Bin of a SharePoint site](https://support.office.com/en-us/article/6df466b6-55f2-4898-8d6e-c0dff851a0be#ID0EAADAAA=Online
) and [Restore deleted items from the site collection recycle bin](https://support.office.com/article/5fa924ee-16d7-487b-9a0a-021b9062d14b).</span></span> <span data-ttu-id="becc1-112">ごみ箱の保存期間は、SharePoint Online では構成できません。</span><span class="sxs-lookup"><span data-stu-id="becc1-112">The Recycle Bin retention time is not configurable in SharePoint Online.</span></span>

<span data-ttu-id="becc1-113">サイトコレクションを削除すると、コレクション内のサイトの階層とその中のすべてのコンテンツも削除されます。</span><span class="sxs-lookup"><span data-stu-id="becc1-113">When you delete a site collection, you're also deleting the hierarchy of sites in the collection, and all content within them:</span></span>
- <span data-ttu-id="becc1-114">ドキュメントおよびドキュメント ライブラリ</span><span class="sxs-lookup"><span data-stu-id="becc1-114">Documents and document libraries</span></span>
- <span data-ttu-id="becc1-115">リストとリストデータ</span><span class="sxs-lookup"><span data-stu-id="becc1-115">Lists and list data</span></span>
- <span data-ttu-id="becc1-116">サイトの構成設定</span><span class="sxs-lookup"><span data-stu-id="becc1-116">Site configuration settings</span></span>
- <span data-ttu-id="becc1-117">サイトまたはそのサブサイトに関連するロールおよびセキュリティ情報</span><span class="sxs-lookup"><span data-stu-id="becc1-117">Role and security information that is related to the site or its subsites</span></span>
- <span data-ttu-id="becc1-118">トップレベル web サイトのサブサイト、それらのコンテンツ、およびユーザー情報</span><span class="sxs-lookup"><span data-stu-id="becc1-118">Subsites of the top-level website, their contents, and user information</span></span>

<span data-ttu-id="becc1-119">サイトコレクションを誤って削除した場合は、SharePoint 管理センターを使用して、グローバルまたは SharePoint 管理者がサイトコレクションを復元できます。</span><span class="sxs-lookup"><span data-stu-id="becc1-119">If you accidentally delete a site collection, it can be restored by a global or SharePoint admin using the SharePoint admin center.</span></span> 

<span data-ttu-id="becc1-120">ハード削除は、ユーザーがサイトコレクションのごみ箱から削除されたアイテムを削除したとき、保持とバックアップの期間が経過したとき、または管理者が[remove-spodeletedsite コマンドレット](/powershell/module/sharepoint-online/Remove-SPODeletedSite?view=sharepoint-ps)を使用してサイトコレクションを完全に削除したときに発生します。</span><span class="sxs-lookup"><span data-stu-id="becc1-120">Hard deletion occurs when a user purges deleted items from the site collection Recycle Bin, when the retention and backup periods expire, or when an administrator permanently deletes a site collection using the [Remove-SPODeletedSite cmdlet](/powershell/module/sharepoint-online/Remove-SPODeletedSite?view=sharepoint-ps).</span></span> <span data-ttu-id="becc1-121">ユーザーが SharePoint Online からコンテンツを物理的に削除 (完全に削除、またはパージ) すると、削除されたチャンクのすべての暗号化キーも削除されます。</span><span class="sxs-lookup"><span data-stu-id="becc1-121">When a user hard deletes (permanently deletes, or purges) content from SharePoint Online, all encryption keys for the deleted chunks are also deleted.</span></span> <span data-ttu-id="becc1-122">以前に削除されたチャンクを格納していたディスク上のブロックは未使用としてマークされ、再利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="becc1-122">The blocks on the disks that previously stored the deleted chunks are marked as unused and available for re-use.</span></span>
