---
title: Office 365 のディレクトリ同期に関する問題の修正
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
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
ms.openlocfilehash: a5c4b58dd856158b00605f39d8a66b48488086b2
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001840"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a><span data-ttu-id="d6572-103">Office 365 のディレクトリ同期に関する問題の修正</span><span class="sxs-lookup"><span data-stu-id="d6572-103">Fixing problems with directory synchronization for Office 365</span></span>

<span data-ttu-id="d6572-104">ディレクトリ同期を使用すると、ユーザーとグループを社内で管理し続け、追加、削除、および変更をクラウドに同期できます。</span><span class="sxs-lookup"><span data-stu-id="d6572-104">With directory synchronization, you can continue to manage users and groups on-premises and synchronize additions, deletions, and changes to the cloud.</span></span> <span data-ttu-id="d6572-105">しかし、セットアップは少し複雑で、問題の原因を特定するのが困難な場合があります。</span><span class="sxs-lookup"><span data-stu-id="d6572-105">But setup is a little complicated and it can sometimes be difficult to identify the source of problems.</span></span> <span data-ttu-id="d6572-106">潜在的な問題を特定して修正するのに役立つリソースが用意されています。</span><span class="sxs-lookup"><span data-stu-id="d6572-106">We have resources to help you identify potential issues and fix them.</span></span>
  
## <a name="how-do-i-know-if-something-is-wrong"></a><span data-ttu-id="d6572-107">問題があるかどうかを確認する方法</span><span class="sxs-lookup"><span data-stu-id="d6572-107">How do I know if something is wrong?</span></span>

<span data-ttu-id="d6572-108">最初に間違ったことが示されている場合は、Microsoft 365 管理センターの [DirSync Status] タイルに問題があることを示しています。</span><span class="sxs-lookup"><span data-stu-id="d6572-108">The first indication that something is wrong is when the DirSync Status tile in the Microsoft 365 admin center indicates there is a problem:</span></span>
  
![管理センタープレビューの [DirSync Status] タイル](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
<span data-ttu-id="d6572-110">また、テナントがディレクトリ同期エラーを検出したことを示す、Office 365 からのメール (連絡メールと管理者の電子メールへ) を受信することになります。</span><span class="sxs-lookup"><span data-stu-id="d6572-110">You will also receive a mail (to the alternate email and to your admin email) from Office 365 that indicates your tenant has encountered directory synchronization errors.</span></span> <span data-ttu-id="d6572-111">詳細については、「 [Office 365 でのディレクトリ同期エラーの識別](identify-directory-synchronization-errors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6572-111">For details see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a><span data-ttu-id="d6572-112">Azure Active Directory Connect ツールを入手するにはどうすればよいですか?</span><span class="sxs-lookup"><span data-stu-id="d6572-112">How do I get Azure Active Directory Connect tool?</span></span>

<span data-ttu-id="d6572-113">[Microsoft 365 管理センター](https://admin.microsoft.com)で、[\* \* ユーザー \> ]、[**アクティブユーザー**] の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="d6572-113">In the [Microsoft 365 admin center](https://admin.microsoft.com), navigate to \*\* Users \*\* \> **Active users**.</span></span> <span data-ttu-id="d6572-114">[**その他**] メニューをクリックし、[**ディレクトリ同期**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="d6572-114">Click the **More** menu and select **Directory synchronization**.</span></span> 
  
![[その他] メニューで、[ディレクトリ同期] を選択します。](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
<span data-ttu-id="d6572-116">ウィザードの[指示](set-up-directory-synchronization.md)に従って、Azure AD Connect をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="d6572-116">Follow the [instructions in the wizard](set-up-directory-synchronization.md) to download Azure AD Connect.</span></span> 
  
<span data-ttu-id="d6572-117">まだ azure active directory 同期 (DirSync) を使用している場合は、「 [Office 365 の azure active directory 同期ツールのインストールと構成ウィザードのエラーメッセージ」](https://go.microsoft.com/fwlink/p/?LinkId=396717)を参照してください。インストールするシステム要件については、dirsync、必要なアクセス許可、および一般的なエラーのトラブルシューティング方法。</span><span class="sxs-lookup"><span data-stu-id="d6572-117">If you are still using Azure Active Directory Sync (DirSync), take a look at [How to troubleshoot Azure Active Directory Sync Tool installation and Configuration Wizard error messages in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) for information about the system requirements to install dirsync, the permissions you need, and how to troubleshoot common errors.</span></span> 
  
<span data-ttu-id="d6572-118">azure Active Directory 同期から azure AD Connect に更新するには、[アップグレード手順](https://go.microsoft.com/fwlink/p/?LinkId=733240)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6572-118">To update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a><span data-ttu-id="d6572-119">Office 365 でのディレクトリ同期に関する問題の一般的な原因の解決</span><span class="sxs-lookup"><span data-stu-id="d6572-119">Resolving common causes of problems with directory synchronization in Office 365</span></span>

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a><span data-ttu-id="d6572-120">**同期されたオブジェクトは、オンラインで表示または更新されません。または、サービスから同期エラーレポートを取得しています。**</span><span class="sxs-lookup"><span data-stu-id="d6572-120">**Synchronized objects aren't appearing or updating online, or I'm getting synchronization error reports from the Service.**</span></span>

- [<span data-ttu-id="d6572-121">id 同期と重複属性の復元</span><span class="sxs-lookup"><span data-stu-id="d6572-121">Identity synchronization and duplicate attribute resiliency</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a><span data-ttu-id="d6572-122">**管理センターに通知があります。または、最近の同期イベントが発生していない自動メールを受信しています。**</span><span class="sxs-lookup"><span data-stu-id="d6572-122">**I have an alert in the admin center, or am receiving automated emails that there hasn't been a recent synchronization event**</span></span>
- [<span data-ttu-id="d6572-123">Azure AD Connect による接続の問題のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="d6572-123">Troubleshoot connectivity issues with Azure AD Connect</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [<span data-ttu-id="d6572-124">Azure AD Connect のアカウントとアクセス許可</span><span class="sxs-lookup"><span data-stu-id="d6572-124">Azure AD Connect Accounts and permissions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [<span data-ttu-id="d6572-125">azure ad Connect sync: azure ad サービスアカウントを管理する方法</span><span class="sxs-lookup"><span data-stu-id="d6572-125">Azure AD Connect sync: How to manage the Azure AD service account</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [<span data-ttu-id="d6572-126">Azure Active Directory とのディレクトリ同期が停止するか、同期が1日以上登録されていないことを示す警告が表示される</span><span class="sxs-lookup"><span data-stu-id="d6572-126">Directory synchronization to Azure Active Directory stops or you're warned that sync hasn't registered in more than a day</span></span>](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a><span data-ttu-id="d6572-127">**パスワードハッシュが同期されていない、または管理センターに最近のパスワードハッシュ同期がないことを示すアラートが表示されている**</span><span class="sxs-lookup"><span data-stu-id="d6572-127">**Password hashes aren't synchronizing, or I'm seeing an alert in the admin center that there hasn't been a recent password hash synchronization**</span></span>
- [<span data-ttu-id="d6572-128">Azure AD Connect 同期を使用したパスワードハッシュ同期の実装</span><span class="sxs-lookup"><span data-stu-id="d6572-128">Implementing password hash synchronization with Azure AD Connect sync</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a><span data-ttu-id="d6572-129">**オブジェクトクォータを超えたという警告が表示されています**</span><span class="sxs-lookup"><span data-stu-id="d6572-129">**I'm seeing an alert that Object quota exceeded**</span></span>
- <span data-ttu-id="d6572-130">サービスを保護するために、組み込みのオブジェクトクォータが用意されています。</span><span class="sxs-lookup"><span data-stu-id="d6572-130">We have a built-in object quota to help protect the service.</span></span> <span data-ttu-id="d6572-131">Office 365 と同期する必要があるディレクトリ内のオブジェクトが多すぎる場合は、[ビジネス製品のサポートに連絡](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)してクォータを増やす必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6572-131">If you have too many objects in your directory that need to sync to Office 365, you'll have to [Contact support for business products](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) to increase your quota.</span></span>

### <a name="i-need-to-know-which-attributes-are-synchronized"></a><span data-ttu-id="d6572-132">**どの属性が同期されているかを知る必要がある**</span><span class="sxs-lookup"><span data-stu-id="d6572-132">**I need to know which attributes are synchronized**</span></span>
- <span data-ttu-id="d6572-133">オンプレミスとクラウドの間で同期されているすべての属性の一覧については、[こちら](https://go.microsoft.com/fwlink/p/?LinkId=396719)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6572-133">You can find a list of all the attributes that are synced between on-premises and the cloud [right here](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a><span data-ttu-id="d6572-134">**クラウドに同期されたオブジェクトを管理または削除できません**</span><span class="sxs-lookup"><span data-stu-id="d6572-134">**I can't manage or remove objects that were synchronized to the cloud**</span></span>
- <span data-ttu-id="d6572-135">クラウド内のオブジェクトのみを管理する準備はできていますか。</span><span class="sxs-lookup"><span data-stu-id="d6572-135">Are you ready to manage objects in the cloud only?</span></span> <span data-ttu-id="d6572-136">または、オンプレミスで削除されたオブジェクトは存在しますか。クラウドに保持されていますか?</span><span class="sxs-lookup"><span data-stu-id="d6572-136">Or is there an object that was deleted on-premises, but is stuck in the cloud?</span></span> <span data-ttu-id="d6572-137">これらの問題を解決する方法については、「同期とサポート」の[記事に記載](https://go.microsoft.com/fwlink/p/?LinkId=396720)されている[トラブルシューティングエラー](https://go.microsoft.com/fwlink/p/?linkid=842044)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6572-137">Take a look at this [Troubleshooting Errors during synchronization](https://go.microsoft.com/fwlink/p/?linkid=842044) and [support article](https://go.microsoft.com/fwlink/p/?LinkId=396720) for guidance on how to resolve these issues.</span></span>

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a><span data-ttu-id="d6572-138">**会社が同期できるオブジェクトの数を超えたというエラーメッセージが表示されました**</span><span class="sxs-lookup"><span data-stu-id="d6572-138">**I got an error message that my company has exceeded the number of objects that can be synchronized**</span></span>
- <span data-ttu-id="d6572-139">この問題の詳細については、[こちら](https://go.microsoft.com/fwlink/p/?LinkId=396721)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6572-139">You can read more about this issue [here](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span></span>
   
## <a name="other-resources"></a><span data-ttu-id="d6572-140">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="d6572-140">Other resources</span></span>

- [<span data-ttu-id="d6572-141">ユーザー プリンシパル名の重複を修正するためのスクリプト</span><span class="sxs-lookup"><span data-stu-id="d6572-141">Script to fix duplicate user principal names</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [<span data-ttu-id="d6572-142">ディレクトリ同期にルーティング可能ではないドメイン (たとえば、ローカルドメイン) を準備する方法</span><span class="sxs-lookup"><span data-stu-id="d6572-142">How to prepare a non-routable domain (such as .local domain) for directory synchronization</span></span>](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [<span data-ttu-id="d6572-143">同期されたオブジェクトの合計数をカウントするためのスクリプト</span><span class="sxs-lookup"><span data-stu-id="d6572-143">Script to count total synchronized objects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [<span data-ttu-id="d6572-144">AD FS 2.0 のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="d6572-144">Troubleshoot AD FS 2.0</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [<span data-ttu-id="d6572-145">PowerShell を使用して、メールが有効なグループの空の DisplayName 属性を修正する</span><span class="sxs-lookup"><span data-stu-id="d6572-145">Use PowerShell to fix empty DisplayName attributes for mail-enabled groups</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [<span data-ttu-id="d6572-146">PowerShell を使用して重複した UPN を修正する</span><span class="sxs-lookup"><span data-stu-id="d6572-146">Use PowerShell to fix duplicate UPN</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [<span data-ttu-id="d6572-147">PowerShell を使用して重複した電子メールアドレスを修正する</span><span class="sxs-lookup"><span data-stu-id="d6572-147">Use PowerShell to fix duplicate email addresses</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a><span data-ttu-id="d6572-148">診断ツール</span><span class="sxs-lookup"><span data-stu-id="d6572-148">Diagnostic tools</span></span>

<span data-ttu-id="d6572-149">[idfix ツール](prepare-directory-attributes-for-synch-with-idfix.md)は、Office 365 への移行の準備として、オンプレミスの Active Directory 環境での id オブジェクトとその属性の検出と修復を実行するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="d6572-149">[IDFix tool](prepare-directory-attributes-for-synch-with-idfix.md) is used to perform discovery and remediation of identity objects and their attributes in an on-premises Active Directory environment in preparation for migration to Office 365.</span></span> <span data-ttu-id="d6572-150">idfix は、Office 365 サービスとの DirSync を担当する Active Directory 管理者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="d6572-150">IDFix is intended for the Active Directory administrators responsible for DirSync with the Office 365 service.</span></span> 

<span data-ttu-id="d6572-151">[idfix ツール](https://go.microsoft.com/fwlink/p/?LinkId=396718)を Microsoft ダウンロードセンターからダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="d6572-151">[Download the IDFix tool](https://go.microsoft.com/fwlink/p/?LinkId=396718) from the Microsoft download center.</span></span>