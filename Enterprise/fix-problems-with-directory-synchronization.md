---
title: Microsoft 365 のディレクトリ同期に関する問題の解決
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
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
description: Office 365 のディレクトリ同期に関する問題の一般的な原因について説明し、トラブルシューティングと解決に役立ついくつかの方法について説明します。
ms.openlocfilehash: d9e390a7230499f724ebbdae592264a850dd9418
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998035"
---
# <a name="fixing-problems-with-directory-synchronization-for-microsoft-365"></a><span data-ttu-id="98ec5-103">Microsoft 365 のディレクトリ同期に関する問題の解決</span><span class="sxs-lookup"><span data-stu-id="98ec5-103">Fixing problems with directory synchronization for Microsoft 365</span></span>

<span data-ttu-id="98ec5-104">ディレクトリ同期を使用すると、ユーザーとグループを社内で管理し続け、追加、削除、および変更をクラウドに同期できます。</span><span class="sxs-lookup"><span data-stu-id="98ec5-104">With directory synchronization, you can continue to manage users and groups on-premises and synchronize additions, deletions, and changes to the cloud.</span></span> <span data-ttu-id="98ec5-105">しかし、セットアップは少し複雑で、問題の原因を特定するのが困難な場合があります。</span><span class="sxs-lookup"><span data-stu-id="98ec5-105">But setup is a little complicated and it can sometimes be difficult to identify the source of problems.</span></span> <span data-ttu-id="98ec5-106">潜在的な問題を特定して修正するのに役立つリソースが用意されています。</span><span class="sxs-lookup"><span data-stu-id="98ec5-106">We have resources to help you identify potential issues and fix them.</span></span>
  
## <a name="how-do-i-know-if-something-is-wrong"></a><span data-ttu-id="98ec5-107">問題があるかどうかを確認する方法</span><span class="sxs-lookup"><span data-stu-id="98ec5-107">How do I know if something is wrong?</span></span>

<span data-ttu-id="98ec5-108">最初に間違ったことが示されている場合は、Microsoft 365 管理センターの [DirSync Status] タイルに問題があることを示しています。</span><span class="sxs-lookup"><span data-stu-id="98ec5-108">The first indication that something is wrong is when the DirSync Status tile in the Microsoft 365 admin center indicates there is a problem.</span></span>
  
<span data-ttu-id="98ec5-109">また、テナントでディレクトリ同期エラーが検出されたことを示すメール (連絡用メールと管理者向けメール) も Microsoft 365 から受け取ります。</span><span class="sxs-lookup"><span data-stu-id="98ec5-109">You will also receive a mail (to the alternate email and to your admin email) from Microsoft 365 that indicates your tenant has encountered directory synchronization errors.</span></span> <span data-ttu-id="98ec5-110">詳細については、「 [Microsoft 365 でのディレクトリ同期エラーの識別](identify-directory-synchronization-errors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98ec5-110">For details see [Identify directory synchronization errors in Microsoft 365](identify-directory-synchronization-errors.md).</span></span>
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a><span data-ttu-id="98ec5-111">Azure Active Directory Connect ツールを入手するにはどうすればよいですか?</span><span class="sxs-lookup"><span data-stu-id="98ec5-111">How do I get Azure Active Directory Connect tool?</span></span>

<span data-ttu-id="98ec5-112">[Microsoft 365 管理センター](https://admin.microsoft.com)で、[**ユーザー** ] [ \> **アクティブなユーザー**] に移動します。</span><span class="sxs-lookup"><span data-stu-id="98ec5-112">In the [Microsoft 365 admin center](https://admin.microsoft.com), navigate to **Users** \> **Active users**.</span></span> <span data-ttu-id="98ec5-113">[**その他**] メニュー (3 つのドット) をクリックし、[**ディレクトリ同期**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="98ec5-113">Click the **More** menu (three dots) and select **Directory synchronization**.</span></span> 
  
<span data-ttu-id="98ec5-114">ウィザードの[指示](set-up-directory-synchronization.md)に従って、Azure AD Connect をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="98ec5-114">Follow the [instructions in the wizard](set-up-directory-synchronization.md) to download Azure AD Connect.</span></span> 
  
<span data-ttu-id="98ec5-115">まだ Azure Active Directory (Azure AD) Sync (DirSync) を使用している場合は、「 [Microsoft 365 の Azure Active Directory 同期ツールのインストールと構成ウィザードのエラーメッセージ](https://go.microsoft.com/fwlink/p/?LinkId=396717)」を参照してください。 dirsync をインストールするためのシステム要件、必要なアクセス許可、および一般的なエラーのトラブルシューティング方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="98ec5-115">If you are still using Azure Active Directory (Azure AD) Sync (DirSync), take a look at [How to troubleshoot Azure Active Directory Sync Tool installation and Configuration Wizard error messages in Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) for information about the system requirements to install dirsync, the permissions you need, and how to troubleshoot common errors.</span></span> 
  
<span data-ttu-id="98ec5-116">Azure AD Sync から Azure AD Connect に更新するには、[アップグレード手順](https://go.microsoft.com/fwlink/p/?LinkId=733240)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98ec5-116">To update from Azure AD Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-microsoft-365"></a><span data-ttu-id="98ec5-117">Microsoft 365 でのディレクトリ同期に関する問題の一般的な原因の解決</span><span class="sxs-lookup"><span data-stu-id="98ec5-117">Resolving common causes of problems with directory synchronization in Microsoft 365</span></span>

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a><span data-ttu-id="98ec5-118">**同期されたオブジェクトは、オンラインで表示または更新されません。または、サービスから同期エラーレポートを取得しています。**</span><span class="sxs-lookup"><span data-stu-id="98ec5-118">**Synchronized objects aren't appearing or updating online, or I'm getting synchronization error reports from the Service.**</span></span>

- [<span data-ttu-id="98ec5-119">ID 同期と重複属性の回復性</span><span class="sxs-lookup"><span data-stu-id="98ec5-119">Identity synchronization and duplicate attribute resiliency</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a><span data-ttu-id="98ec5-120">**管理センターに通知があります。または、最近の同期イベントが発生していない自動メールを受信しています。**</span><span class="sxs-lookup"><span data-stu-id="98ec5-120">**I have an alert in the admin center, or am receiving automated emails that there hasn't been a recent synchronization event**</span></span>
- [<span data-ttu-id="98ec5-121">Azure AD Connect での接続に関する問題のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="98ec5-121">Troubleshoot connectivity issues with Azure AD Connect</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [<span data-ttu-id="98ec5-122">Azure AD Connect: アカウントとアクセス許可</span><span class="sxs-lookup"><span data-stu-id="98ec5-122">Azure AD Connect Accounts and permissions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [<span data-ttu-id="98ec5-123">Azure AD Connect 同期: Azure AD サービス アカウントを管理する方法</span><span class="sxs-lookup"><span data-stu-id="98ec5-123">Azure AD Connect sync: How to manage the Azure AD service account</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [<span data-ttu-id="98ec5-124">Azure Active Directory 同期ツールによる同期処理が停止する、または同期が 24 時間以上実行されていないという内容のメッセージを受け取る</span><span class="sxs-lookup"><span data-stu-id="98ec5-124">Directory synchronization to Azure Active Directory stops or you're warned that sync hasn't registered in more than a day</span></span>](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a><span data-ttu-id="98ec5-125">**パスワードハッシュが同期されていない、または管理センターに最近のパスワードハッシュ同期がないことを示すアラートが表示されている**</span><span class="sxs-lookup"><span data-stu-id="98ec5-125">**Password hashes aren't synchronizing, or I'm seeing an alert in the admin center that there hasn't been a recent password hash synchronization**</span></span>
- [<span data-ttu-id="98ec5-126">Azure AD Connect Sync を使用してパスワード ハッシュの同期を実装する</span><span class="sxs-lookup"><span data-stu-id="98ec5-126">Implementing password hash synchronization with Azure AD Connect sync</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a><span data-ttu-id="98ec5-127">**オブジェクトクォータを超えたという警告が表示されています**</span><span class="sxs-lookup"><span data-stu-id="98ec5-127">**I'm seeing an alert that Object quota exceeded**</span></span>
- <span data-ttu-id="98ec5-128">サービスを保護するために、組み込みのオブジェクトクォータが用意されています。</span><span class="sxs-lookup"><span data-stu-id="98ec5-128">We have a built-in object quota to help protect the service.</span></span> <span data-ttu-id="98ec5-129">Microsoft 365 に同期する必要があるディレクトリ内のオブジェクトが多すぎる場合は、予算を増やすために、[ビジネス製品のサポートに連絡](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)する必要があります。</span><span class="sxs-lookup"><span data-stu-id="98ec5-129">If you have too many objects in your directory that need to sync to Microsoft 365, you'll have to [Contact support for business products](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) to increase your quota.</span></span>

### <a name="i-need-to-know-which-attributes-are-synchronized"></a><span data-ttu-id="98ec5-130">**どの属性が同期されているかを知る必要がある**</span><span class="sxs-lookup"><span data-stu-id="98ec5-130">**I need to know which attributes are synchronized**</span></span>
- <span data-ttu-id="98ec5-131">オンプレミスとクラウドの間で同期されているすべての属性の一覧については、[こちら](https://go.microsoft.com/fwlink/p/?LinkId=396719)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98ec5-131">You can find a list of all the attributes that are synced between on-premises and the cloud [right here](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a><span data-ttu-id="98ec5-132">**クラウドに同期されたオブジェクトを管理または削除できません**</span><span class="sxs-lookup"><span data-stu-id="98ec5-132">**I can't manage or remove objects that were synchronized to the cloud**</span></span>
- <span data-ttu-id="98ec5-133">クラウド内のオブジェクトのみを管理する準備はできていますか。</span><span class="sxs-lookup"><span data-stu-id="98ec5-133">Are you ready to manage objects in the cloud only?</span></span> <span data-ttu-id="98ec5-134">または、オンプレミスで削除されたオブジェクトは存在しますか。クラウドに保持されていますか?</span><span class="sxs-lookup"><span data-stu-id="98ec5-134">Or is there an object that was deleted on-premises, but is stuck in the cloud?</span></span> <span data-ttu-id="98ec5-135">これらの問題を解決する方法については、「同期とサポート」の[記事に記載](https://go.microsoft.com/fwlink/p/?LinkId=396720)されている[トラブルシューティングエラー](https://go.microsoft.com/fwlink/p/?linkid=842044)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98ec5-135">Take a look at this [Troubleshooting Errors during synchronization](https://go.microsoft.com/fwlink/p/?linkid=842044) and [support article](https://go.microsoft.com/fwlink/p/?LinkId=396720) for guidance on how to resolve these issues.</span></span>

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a><span data-ttu-id="98ec5-136">**会社が同期できるオブジェクトの数を超えたというエラーメッセージが表示されました**</span><span class="sxs-lookup"><span data-stu-id="98ec5-136">**I got an error message that my company has exceeded the number of objects that can be synchronized**</span></span>
- <span data-ttu-id="98ec5-137">この問題の詳細については、[こちら](https://go.microsoft.com/fwlink/p/?LinkId=396721)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98ec5-137">You can read more about this issue [here](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span></span>
   
## <a name="other-resources"></a><span data-ttu-id="98ec5-138">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="98ec5-138">Other resources</span></span>

- [<span data-ttu-id="98ec5-139">ユーザー プリンシパル名の重複を修正するためのスクリプト</span><span class="sxs-lookup"><span data-stu-id="98ec5-139">Script to fix duplicate user principal names</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [<span data-ttu-id="98ec5-140">ディレクトリ同期にルーティング可能ではないドメイン (たとえば、ローカルドメイン) を準備する方法</span><span class="sxs-lookup"><span data-stu-id="98ec5-140">How to prepare a non-routable domain (such as .local domain) for directory synchronization</span></span>](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [<span data-ttu-id="98ec5-141">同期されたオブジェクトの合計数をカウントするためのスクリプト</span><span class="sxs-lookup"><span data-stu-id="98ec5-141">Script to count total synchronized objects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [<span data-ttu-id="98ec5-142">AD FS 2.0 のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="98ec5-142">Troubleshoot AD FS 2.0</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [<span data-ttu-id="98ec5-143">PowerShell を使用して、メールが有効なグループの空の DisplayName 属性を修正する</span><span class="sxs-lookup"><span data-stu-id="98ec5-143">Use PowerShell to fix empty DisplayName attributes for mail-enabled groups</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [<span data-ttu-id="98ec5-144">PowerShell を使用して重複した UPN を修正する</span><span class="sxs-lookup"><span data-stu-id="98ec5-144">Use PowerShell to fix duplicate UPN</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [<span data-ttu-id="98ec5-145">PowerShell を使用して重複した電子メールアドレスを修正する</span><span class="sxs-lookup"><span data-stu-id="98ec5-145">Use PowerShell to fix duplicate email addresses</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a><span data-ttu-id="98ec5-146">診断ツール</span><span class="sxs-lookup"><span data-stu-id="98ec5-146">Diagnostic tools</span></span>

<span data-ttu-id="98ec5-147">[Idfix ツール](prepare-directory-attributes-for-synch-with-idfix.md)は、Microsoft 365 への移行の準備として、オンプレミスの Active Directory 環境での id オブジェクトとその属性の検出と修復を実行するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="98ec5-147">[IDFix tool](prepare-directory-attributes-for-synch-with-idfix.md) is used to perform discovery and remediation of identity objects and their attributes in an on-premises Active Directory environment in preparation for migration to Microsoft 365.</span></span> <span data-ttu-id="98ec5-148">IDFix は、Microsoft 365 サービスとのディレクトリ同期を担当する Active Directory 管理者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="98ec5-148">IDFix is intended for the Active Directory administrators responsible for directory synchronization with the Microsoft 365 service.</span></span> 

<span data-ttu-id="98ec5-149">[IDFix ツール](https://go.microsoft.com/fwlink/p/?LinkId=396718)を Microsoft ダウンロードセンターからダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="98ec5-149">[Download the IDFix tool](https://go.microsoft.com/fwlink/p/?LinkId=396718) from the Microsoft download center.</span></span>