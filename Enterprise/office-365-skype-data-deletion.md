---
title: Office 365 Skype for Business データ削除
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
f1.keywords:
- NOCSH
description: Skype for Business でのデータ削除についての説明。
ms.openlocfilehash: 33fbb91d2fbfd0e3133bfa2cca2118643b702d95
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844308"
---
# <a name="skype-for-business-data-deletion-in-office-365"></a><span data-ttu-id="6f6eb-103">Office 365 での Skype for Business データの削除</span><span class="sxs-lookup"><span data-stu-id="6f6eb-103">Skype for Business Data Deletion in Office 365</span></span>

<span data-ttu-id="6f6eb-p101">Skype for Business は、ピアツーピアのインスタント メッセージ、マルチパーティのインスタント メッセージ、および会議中にアップロードされたコンテンツのアーカイブを提供します。アーカイブ機能には Exchange が必要で、ユーザーの Exchange メールボックスのインプレース ホールド属性によって制御されます。この属性は、電子メールと Skype for Business のコンテンツの両方をアーカイブします。</span><span class="sxs-lookup"><span data-stu-id="6f6eb-p101">Skype for Business provides archiving of peer-to-peer instant messages, multiparty instant messages, and content upload activities in meetings. The archiving capability requires Exchange and is controlled by the user's Exchange mailbox In-Place Hold attribute, which archives both email and Skype for Business contents.</span></span>

<span data-ttu-id="6f6eb-p102">ユーザーレベルのアーカイブ ポリシーを作成、構成、適用することで、特定のユーザーまたはユーザー グループに対するアーカイブ処理を有効または無効にするため、Skype for Business のアーカイブはすべて「ユーザーレベル アーカイブ」と見なされます。Skype for Business 管理センター内部からはアーカイブ設定を直接管理できません。</span><span class="sxs-lookup"><span data-stu-id="6f6eb-p102">All archiving in Skype for Business is considered "user-level archiving" because you enable or disable it for one or more specific users or groups of users by creating, configuring, and applying a user-level archiving policy for those users. There is no direct control of archiving settings from within the Skype for Business admin center.</span></span>

<span data-ttu-id="6f6eb-108">Skype for Business では、次の種類のコンテンツはアーカイブされません。</span><span class="sxs-lookup"><span data-stu-id="6f6eb-108">The following types of content are not archived in Skype for Business:</span></span>

- <span data-ttu-id="6f6eb-109">ピアツーピア ファイル転送</span><span class="sxs-lookup"><span data-stu-id="6f6eb-109">Peer-to-peer file transfers</span></span>
- <span data-ttu-id="6f6eb-110">ピアツーピア インスタント メッセージおよび電話会議のオーディオ/ビデオ</span><span class="sxs-lookup"><span data-stu-id="6f6eb-110">Audio/video for peer-to-peer instant messages and conferences</span></span>
- <span data-ttu-id="6f6eb-111">ピアツーピアのインスタント メッセージおよび会議のアプリケーション共有</span><span class="sxs-lookup"><span data-stu-id="6f6eb-111">Application sharing for peer-to-peer instant messages and conferences</span></span>
- <span data-ttu-id="6f6eb-112">会議のコメント</span><span class="sxs-lookup"><span data-stu-id="6f6eb-112">Conferencing annotations</span></span> 

## <a name="meeting-content-retention"></a><span data-ttu-id="6f6eb-113">会議コンテンツの保存</span><span class="sxs-lookup"><span data-stu-id="6f6eb-113">Meeting Content Retention</span></span>

<span data-ttu-id="6f6eb-114">Skype for Business を使用しているお客様は、PowerPoint プレゼンテーション、OneNote ファイル、その他のファイルなどの添付ファイルとして Skype for Business 会議にコンテンツをアップロードできます。</span><span class="sxs-lookup"><span data-stu-id="6f6eb-114">Customers using Skype for Business can upload content to a Skype for Business meeting as attachments, such as PowerPoint presentations, OneNote files, and other files.</span></span> <span data-ttu-id="6f6eb-115">会議にアップロードされたコンテンツの保持期間は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6f6eb-115">The retention period for content that has been uploaded to a meeting is as follows:</span></span>

- <span data-ttu-id="6f6eb-116">**1 回限りの会議**-最後のユーザーが会議から退席してから15日後にコンテンツが保持されます。</span><span class="sxs-lookup"><span data-stu-id="6f6eb-116">**One-time meeting** - Content is retained for 15 days starting from when the last person leaves the meeting.</span></span>
- <span data-ttu-id="6f6eb-117">**定期的な会議**-最後のユーザーが会議の最後のセッションを終了してから15日後にコンテンツが保持されます。</span><span class="sxs-lookup"><span data-stu-id="6f6eb-117">**Recurring meeting** - Content is retained for 15 days after the last person leaves the last session of the meeting.</span></span> <span data-ttu-id="6f6eb-118">だれかが 15 日以内に同じ会議セッションに参加した場合、保存タイマーがリセットされます。</span><span class="sxs-lookup"><span data-stu-id="6f6eb-118">The retention timer resets if someone joins the same meeting session within 15 days.</span></span> <span data-ttu-id="6f6eb-119">たとえば、Skype for Business 会議が1年の週単位で実行するようにスケジュールされており、最初のインスタンスの間にファイルが会議にアップロードされるとします。</span><span class="sxs-lookup"><span data-stu-id="6f6eb-119">For example, assume a Skype for Business meeting is scheduled to occur on a weekly basis for one year, and a file is uploaded to the meeting during the first instance.</span></span> <span data-ttu-id="6f6eb-120">少なくとも1人のユーザーが会議セッションに毎週参加している場合、そのファイルは、年全体の Skype for Business Online サーバーに保存され、最後のユーザーがシリーズの最後の会議を終了してから15日後に保持されます。</span><span class="sxs-lookup"><span data-stu-id="6f6eb-120">If at least one person joins the meeting session every week, the file is retained in Skype for Business Online servers for the entire year plus 15 days after the last person leaves the last meeting of the series.</span></span>
- <span data-ttu-id="6f6eb-121">**Meet Now ミーティング**-会議の終了時間の8時間後にコンテンツが保持されます。</span><span class="sxs-lookup"><span data-stu-id="6f6eb-121">**Meet Now meeting** - Content is retained for 8 hours after the meeting end time.</span></span>

> [!NOTE]
> <span data-ttu-id="6f6eb-122">ユーザーがライセンス認証されていない場合、または無効になっている場合 (たとえば、 **msRTCSIP-userenabled**が*False*に設定されている場合)、再ライセンスまたは再度許可された場合、会議コンテンツは保持されません。</span><span class="sxs-lookup"><span data-stu-id="6f6eb-122">If a user is unlicensed or disabled (e.g., if **msRTCSIP-userenabled** is set to *False*), and is then re-licensed or reenabled, meeting content is not retained.</span></span>

## <a name="meeting-expiration"></a><span data-ttu-id="6f6eb-123">会議の有効期限</span><span class="sxs-lookup"><span data-stu-id="6f6eb-123">Meeting Expiration</span></span>

<span data-ttu-id="6f6eb-124">ユーザーは、以下の有効期間に応じて会議の終了後に、特定の会議にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="6f6eb-124">Users can access a specific meeting after the meeting has ended, subject to the following expiration time periods:</span></span>

- <span data-ttu-id="6f6eb-125">**1 回限り**の会議の会議出席依頼は、予定された会議の終了時刻の14日後に期限切れになります。</span><span class="sxs-lookup"><span data-stu-id="6f6eb-125">**One-time meeting** - Meeting expires 14 days after the scheduled meeting end time.</span></span>
- <span data-ttu-id="6f6eb-126">**終了日が**指定された定期的な会議-会議の期限は、最後の会議の予定終了時刻の14日後になります。</span><span class="sxs-lookup"><span data-stu-id="6f6eb-126">**Recurring meeting with end date** - Meeting expires 14 days after the scheduled end time of the last meeting occurrence.</span></span>
- <span data-ttu-id="6f6eb-127">**Meet Now ミーティング**-会議は8時間後に期限切れになります。</span><span class="sxs-lookup"><span data-stu-id="6f6eb-127">**Meet Now meeting** - Meeting expires after 8 hours.</span></span>

## <a name="whiteboard-collaboration"></a><span data-ttu-id="6f6eb-128">ホワイトボードのグループ作業</span><span class="sxs-lookup"><span data-stu-id="6f6eb-128">Whiteboard Collaboration</span></span>

<span data-ttu-id="6f6eb-129">ホワイトボード上に作成されるコメントは、すべての参加者が見ることになります。</span><span class="sxs-lookup"><span data-stu-id="6f6eb-129">Annotations made on whiteboards will be seen by all participants.</span></span> <span data-ttu-id="6f6eb-130">ホワイトボードを保存すると、ホワイトボードとすべての注釈が Skype for Business server に保存され、管理者が設定した会議コンテンツの有効期限ポリシーに従ってサーバー上に保持されます。</span><span class="sxs-lookup"><span data-stu-id="6f6eb-130">When saving a whiteboard, the whiteboard and all annotations will be stored on a Skype for Business server, and it will be retained on the server according to meeting content expiration policies set by the administrator.</span></span>

## <a name="audio-test-service"></a><span data-ttu-id="6f6eb-131">オーディオテストサービス</span><span class="sxs-lookup"><span data-stu-id="6f6eb-131">Audio Test Service</span></span>

<span data-ttu-id="6f6eb-132">音声テストサービスの呼び出し中に、短い (約5秒) の音声のサンプルが記録されます。</span><span class="sxs-lookup"><span data-stu-id="6f6eb-132">A short (approximately 5 seconds) sample of your voice is recorded during the Audio Test Service call.</span></span> <span data-ttu-id="6f6eb-133">音声サンプルは、レコーディングの品質に基づいて Skype for Business 通話の音質をチェックまたは検証するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="6f6eb-133">The voice sample is used by you to check and/or verify the sound quality of your Skype for Business call based on the quality of the recording.</span></span> <span data-ttu-id="6f6eb-134">Audio Test Service の呼び出しが終了すると、音声サンプルが削除されます。</span><span class="sxs-lookup"><span data-stu-id="6f6eb-134">When the Audio Test Service call ends, the voice sample is deleted.</span></span>

## <a name="persistent-group-chat"></a><span data-ttu-id="6f6eb-135">常設グループチャット</span><span class="sxs-lookup"><span data-stu-id="6f6eb-135">Persistent Group Chat</span></span>

<span data-ttu-id="6f6eb-136">常設グループチャットは、グループチャットの会話の内容を格納します。</span><span class="sxs-lookup"><span data-stu-id="6f6eb-136">Persistent Group Chat stores the content of group chat conversations.</span></span> <span data-ttu-id="6f6eb-137">有効にすると、管理者は保持期間、この情報が格納されるサーバー、コンプライアンスまたはその他の目的のためにグループチャット履歴がアーカイブされている場合は、会議室のプロパティを管理/変更できるかどうかを制御できます。</span><span class="sxs-lookup"><span data-stu-id="6f6eb-137">If enabled, the administrator can control the retention period, the server on which this information is stored, if Group Chat history is archived for compliance or other purposes, and manage/modify any properties on a room.</span></span> <span data-ttu-id="6f6eb-138">さまざまな役割を持つユーザーは、次のように、保存されたデータへのアクセス方法が異なります。</span><span class="sxs-lookup"><span data-stu-id="6f6eb-138">Users with different roles have different access to the persisted data, as follows:</span></span>

- <span data-ttu-id="6f6eb-139">管理者は、古いコンテンツ (特定の日付前に投稿されたコンテンツなど) を任意のチャットルームから削除して、データベースのサイズが大幅に増加するのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="6f6eb-139">Administrators can delete older content (for example, content posted before a certain date) from any chat room to keep the size of the database from growing greatly.</span></span> <span data-ttu-id="6f6eb-140">または、特定のチャットルームにとって不適切と見なされるメッセージを削除または置換することができます (または不適切であると見なされます)。</span><span class="sxs-lookup"><span data-stu-id="6f6eb-140">Or, they can remove or replace messages considered inappropriate for a given chat room (or considered unsuitable).</span></span>
- <span data-ttu-id="6f6eb-141">エンドユーザー (メッセージの作成者を含む) は、チャットルームからコンテンツを削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="6f6eb-141">End-users, including message authors, cannot delete content from any chat room.</span></span>
- <span data-ttu-id="6f6eb-142">チャットルーム管理者は、会議室を無効にすることはできますが、ルームは削除できません。</span><span class="sxs-lookup"><span data-stu-id="6f6eb-142">Chat room managers can disable rooms but cannot delete rooms.</span></span> <span data-ttu-id="6f6eb-143">作成後にチャットルームを削除できるのは管理者のみです。</span><span class="sxs-lookup"><span data-stu-id="6f6eb-143">Only administrators can delete a chat room after it is created.</span></span>