---
title: Microsoft 365 のディレクトリ同期に関する問題の修正
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Priority
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: Office 365 のディレクトリ同期の問題の一般的な原因を示し、問題のトラブルシューティングと解決に役立ついくつかの方法を紹介します。
ms.openlocfilehash: faf0f061b8f2798054e63f3338b8076c0ec88f73
ms.sourcegitcommit: a9021ba0800ffc0da21cf2c4da67ab1da2d97099
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/05/2020
ms.locfileid: "46570970"
---
# <a name="fixing-problems-with-directory-synchronization-for-microsoft-365"></a><span data-ttu-id="08f2a-103">Microsoft 365 のディレクトリ同期に関する問題の修正</span><span class="sxs-lookup"><span data-stu-id="08f2a-103">Fixing problems with directory synchronization for Microsoft 365</span></span>

<span data-ttu-id="08f2a-104">ディレクトリ同期を使用することにより、社内のユーザーおよびグループを継続的に管理して、クラウドへの追加、削除、変更を同期することができます。</span><span class="sxs-lookup"><span data-stu-id="08f2a-104">With directory synchronization, you can continue to manage users and groups on-premises and synchronize additions, deletions, and changes to the cloud.</span></span> <span data-ttu-id="08f2a-105">ただし、セットアップは少し複雑であり、問題の原因を特定することが困難な場合があります。</span><span class="sxs-lookup"><span data-stu-id="08f2a-105">But setup is a little complicated and it can sometimes be difficult to identify the source of problems.</span></span> <span data-ttu-id="08f2a-106">潜在的な問題を特定してそれを修正するのに役立つリソースがあります。</span><span class="sxs-lookup"><span data-stu-id="08f2a-106">We have resources to help you identify potential issues and fix them.</span></span>
  
## <a name="how-do-i-know-if-something-is-wrong"></a><span data-ttu-id="08f2a-107">問題がある場合に確認する方法</span><span class="sxs-lookup"><span data-stu-id="08f2a-107">How do I know if something is wrong?</span></span>

<span data-ttu-id="08f2a-108">問題がある場合に最初の通知として、Microsoft 365 管理センターにある同期ツールの状態タイルに次のように問題があると示されます。</span><span class="sxs-lookup"><span data-stu-id="08f2a-108">The first indication that something is wrong is when the DirSync Status tile in the Microsoft 365 admin center indicates there is a problem.</span></span>
  
<span data-ttu-id="08f2a-109">Microsoft 365 からディレクトリの同期エラーが発生したテナントを示すメール (連絡用メール アドレスと管理者メール宛) も受信します。</span><span class="sxs-lookup"><span data-stu-id="08f2a-109">You will also receive a mail (to the alternate email and to your admin email) from Microsoft 365 that indicates your tenant has encountered directory synchronization errors.</span></span> <span data-ttu-id="08f2a-110">詳細については、「[Microsoft 365 でディレクトリ同期エラーを特定する](identify-directory-synchronization-errors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08f2a-110">For details see [Identify directory synchronization errors in Microsoft 365](identify-directory-synchronization-errors.md).</span></span>
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a><span data-ttu-id="08f2a-111">Azure Active Directory Connect ツールを入手する方法</span><span class="sxs-lookup"><span data-stu-id="08f2a-111">How do I get Azure Active Directory Connect tool?</span></span>

<span data-ttu-id="08f2a-112">[Microsoft 365 管理センター](https://admin.microsoft.com) では、**[ユーザー]** \> **[アクティブ ユーザー]** の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="08f2a-112">In the [Microsoft 365 admin center](https://admin.microsoft.com), navigate to **Users** \> **Active users**.</span></span> <span data-ttu-id="08f2a-113">**[その他]** メニュー (3つの点) をクリックして、**[ディレクトリ同期]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="08f2a-113">Click the **More** menu (three dots) and select **Directory synchronization**.</span></span> 
  
<span data-ttu-id="08f2a-114">[ウィザードの指示](set-up-directory-synchronization.md) に従って、Azure AD Connect をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="08f2a-114">Follow the [instructions in the wizard](set-up-directory-synchronization.md) to download Azure AD Connect.</span></span> 
  
<span data-ttu-id="08f2a-115">まだ Azure Active Directory (Azure AD) Sync (DirSync) を使用している場合、dirsync をインストールするためのシステム要件、必要なアクセス許可、一般的なエラーのトラブルシューティング方法については、[「Azure Active Directory 同期ツールのインストールと Microsoft 365 の構成ウィザードのエラー メッセージをトラブルシューティングする方法」](https://go.microsoft.com/fwlink/p/?LinkId=396717) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08f2a-115">If you are still using Azure Active Directory (Azure AD) Sync (DirSync), take a look at [How to troubleshoot Azure Active Directory Sync Tool installation and Configuration Wizard error messages in Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) for information about the system requirements to install dirsync, the permissions you need, and how to troubleshoot common errors.</span></span> 
  
<span data-ttu-id="08f2a-116">Azure AD Sync から Azure AD Connect に更新するには、「[アップグレード手順](https://go.microsoft.com/fwlink/p/?LinkId=733240)」 を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08f2a-116">To update from Azure AD Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-microsoft-365"></a><span data-ttu-id="08f2a-117">Microsoft 365 でのディレクトリ同期の問題の一般的な原因</span><span class="sxs-lookup"><span data-stu-id="08f2a-117">Resolving common causes of problems with directory synchronization in Microsoft 365</span></span>

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a><span data-ttu-id="08f2a-118">同期対象オブジェクトがオンラインで表示または更新されない場合、サービスから同期エラー レポートを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="08f2a-118">Synchronized objects aren't appearing or updating online, or I'm getting synchronization error reports from the Service.</span></span>

- [<span data-ttu-id="08f2a-119">ID 同期と重複属性の回復性</span><span class="sxs-lookup"><span data-stu-id="08f2a-119">Identity synchronization and duplicate attribute resiliency</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a><span data-ttu-id="08f2a-120">管理センターで警告を受け取ったか、または最近、同期イベントがないという自動メールを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="08f2a-120">I have an alert in the admin center, or am receiving automated emails that there hasn't been a recent synchronization event</span></span>
- [<span data-ttu-id="08f2a-121">Azure AD Connect での接続に関する問題のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="08f2a-121">Troubleshoot connectivity issues with Azure AD Connect</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [<span data-ttu-id="08f2a-122">Azure AD Connect: アカウントとアクセス許可</span><span class="sxs-lookup"><span data-stu-id="08f2a-122">Azure AD Connect Accounts and permissions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [<span data-ttu-id="08f2a-123">Azure AD Connect 同期: Azure AD サービス アカウントを管理する方法</span><span class="sxs-lookup"><span data-stu-id="08f2a-123">Azure AD Connect sync: How to manage the Azure AD service account</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [<span data-ttu-id="08f2a-124">Azure Active Directory 同期ツールによる同期処理が停止する、または同期が 24 時間以上実行されていないという内容のメッセージを受け取る</span><span class="sxs-lookup"><span data-stu-id="08f2a-124">Directory synchronization to Azure Active Directory stops or you're warned that sync hasn't registered in more than a day</span></span>](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a><span data-ttu-id="08f2a-125">パスワードが同期されていないか、またはパスワード ハッシュの同期がないという警告が最近管理センターに表示される</span><span class="sxs-lookup"><span data-stu-id="08f2a-125">Password hashes aren't synchronizing, or I'm seeing an alert in the admin center that there hasn't been a recent password hash synchronization</span></span>
- [<span data-ttu-id="08f2a-126">Azure AD Connect Sync を使用してパスワード ハッシュの同期を実装する</span><span class="sxs-lookup"><span data-stu-id="08f2a-126">Implementing password hash synchronization with Azure AD Connect sync</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a><span data-ttu-id="08f2a-127">オブジェクト クォータの超過通知が表示される</span><span class="sxs-lookup"><span data-stu-id="08f2a-127">I'm seeing an alert that Object quota exceeded</span></span>
- <span data-ttu-id="08f2a-128">サービスを保護するのに役立つ、組み込みのオブジェクト クォータがあります。</span><span class="sxs-lookup"><span data-stu-id="08f2a-128">We have a built-in object quota to help protect the service.</span></span> <span data-ttu-id="08f2a-129">Microsoft 365 に同期する必要があるオブジェクトの数が多すぎる場合、クォータを増やすために [一般法人向け製品のサポートに連絡](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) する必要があります。</span><span class="sxs-lookup"><span data-stu-id="08f2a-129">If you have too many objects in your directory that need to sync to Microsoft 365, you'll have to [Contact support for business products](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) to increase your quota.</span></span>

### <a name="i-need-to-know-which-attributes-are-synchronized"></a><span data-ttu-id="08f2a-130">どの属性が同期されているか知る必要があります。</span><span class="sxs-lookup"><span data-stu-id="08f2a-130">I need to know which attributes are synchronized</span></span>
- <span data-ttu-id="08f2a-131">オンプレミス環境とクラウドとの間で同期されるすべての属性の一覧については、[このページ](https://go.microsoft.com/fwlink/p/?LinkId=396719) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08f2a-131">You can find a list of all the attributes that are synced between on-premises and the cloud [right here](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a><span data-ttu-id="08f2a-132">クラウドに同期されたオブジェクトを管理または削除できない</span><span class="sxs-lookup"><span data-stu-id="08f2a-132">I can't manage or remove objects that were synchronized to the cloud</span></span>
- <span data-ttu-id="08f2a-133">クラウドのみでオブジェクトを管理する準備ができていますか。</span><span class="sxs-lookup"><span data-stu-id="08f2a-133">Are you ready to manage objects in the cloud only?</span></span> <span data-ttu-id="08f2a-134">あるいは、社内で削除されたものの、クラウドでスタックしているオブジェクトがありますか。</span><span class="sxs-lookup"><span data-stu-id="08f2a-134">Or is there an object that was deleted on-premises, but is stuck in the cloud?</span></span> <span data-ttu-id="08f2a-135">このような問題を解決する方法については、[「同期中に発生したエラーのトラブルシューティング」](https://go.microsoft.com/fwlink/p/?linkid=842044) と [サポート記事](https://go.microsoft.com/fwlink/p/?LinkId=396720) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08f2a-135">Take a look at this [Troubleshooting Errors during synchronization](https://go.microsoft.com/fwlink/p/?linkid=842044) and [support article](https://go.microsoft.com/fwlink/p/?LinkId=396720) for guidance on how to resolve these issues.</span></span>

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a><span data-ttu-id="08f2a-136">会社で同期可能なオブジェクトの数を超えたというエラー メッセージが表示されました。</span><span class="sxs-lookup"><span data-stu-id="08f2a-136">I got an error message that my company has exceeded the number of objects that can be synchronized</span></span>
- <span data-ttu-id="08f2a-137">この問題の詳細については、[このページ](https://go.microsoft.com/fwlink/p/?LinkId=396721) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08f2a-137">You can read more about this issue [here](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span></span>
   
## <a name="other-resources"></a><span data-ttu-id="08f2a-138">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="08f2a-138">Other resources</span></span>

- [<span data-ttu-id="08f2a-139">ユーザー プリンシパル名の重複を修正するためのスクリプト</span><span class="sxs-lookup"><span data-stu-id="08f2a-139">Script to fix duplicate user principal names</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [<span data-ttu-id="08f2a-140">ディレクトリ同期用に (.local ドメインなどの) 非ルーティング ドメインを準備する方法</span><span class="sxs-lookup"><span data-stu-id="08f2a-140">How to prepare a non-routable domain (such as .local domain) for directory synchronization</span></span>](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [<span data-ttu-id="08f2a-141">同期されたオブジェクトの総数を取得するためのスクリプト</span><span class="sxs-lookup"><span data-stu-id="08f2a-141">Script to count total synchronized objects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [<span data-ttu-id="08f2a-142">AD FS 2.0 のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="08f2a-142">Troubleshoot AD FS 2.0</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [<span data-ttu-id="08f2a-143">PowerShell を使ってメールが有効なグループの空の DisplayName 属性を修正する</span><span class="sxs-lookup"><span data-stu-id="08f2a-143">Use PowerShell to fix empty DisplayName attributes for mail-enabled groups</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [<span data-ttu-id="08f2a-144">PowerShell を使ってユーザー プリンシパル名の重複を修正する</span><span class="sxs-lookup"><span data-stu-id="08f2a-144">Use PowerShell to fix duplicate UPN</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [<span data-ttu-id="08f2a-145">PowerShell を使ってメール アドレスの重複を修正する</span><span class="sxs-lookup"><span data-stu-id="08f2a-145">Use PowerShell to fix duplicate email addresses</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
