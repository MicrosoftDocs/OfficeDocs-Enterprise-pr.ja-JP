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
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: Office 365 のディレクトリ同期の問題の一般的な原因を説明し、トラブルシューティングし、解決に役立ついくつかのメソッドを提供します。
ms.openlocfilehash: 2d567daa370d651a6eb9180db2f729d09b380226
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897310"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a><span data-ttu-id="959d0-103">Office 365 のディレクトリ同期に関する問題の修正</span><span class="sxs-lookup"><span data-stu-id="959d0-103">Fixing problems with directory synchronization for Office 365</span></span>

<span data-ttu-id="959d0-p101">ディレクトリ同期によって、ユーザーとグループの設置を管理し、追加、削除、およびクラウドへの変更の同期を続行できます。セットアップは少し複雑な問題の原因を特定することは困難があります。潜在的な問題を識別し、それらを修正するためのリソースがあります。</span><span class="sxs-lookup"><span data-stu-id="959d0-p101">With directory synchronization, you can continue to manage users and groups on-premises and synchronize additions, deletions, and changes to the cloud. But setup is a little complicated and it can sometimes be difficult to identify the source of problems. We have resources to help you identify potential issues and fix them.</span></span>
  
## <a name="how-do-i-know-if-something-is-wrong"></a><span data-ttu-id="959d0-107">何かが間違った方法を教えてください。</span><span class="sxs-lookup"><span data-stu-id="959d0-107">How do I know if something is wrong?</span></span>

<span data-ttu-id="959d0-108">何かが間違っていることを示す最初の兆候は、Office 365 の管理センターのディレクトリ同期の状態のタイルでは、問題が示されている場合です。</span><span class="sxs-lookup"><span data-stu-id="959d0-108">The first indication that something is wrong is when the DirSync Status tile in the Office 365 admin center indicates there is a problem:</span></span>
  
![管理センターのプレビュー] で、ディレクトリ同期の状態を並べて表示します。](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
<span data-ttu-id="959d0-p102">Office 365 のテナントには、ディレクトリ同期のエラーが発生したためであることを示すからメールを別の電子メールなど、管理者の電子メールにも表示されます。詳細については、 [Office 365 のディレクトリ同期エラーを識別する](identify-directory-synchronization-errors.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="959d0-p102">You will also receive a mail (to the alternate email and to your admin email) from Office 365 that indicates your tenant has encountered directory synchronization errors. For details see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a><span data-ttu-id="959d0-112">Azure Active Directory 接続ツールを取得する方法は?</span><span class="sxs-lookup"><span data-stu-id="959d0-112">How do I get Azure Active Directory Connect tool?</span></span>

<span data-ttu-id="959d0-p103">Office 365 管理センターで、[に移動 \* \* ユーザー \* \* \> **アクティブなユーザー**です。[**詳細**] メニューのをクリックし、**ディレクトリ同期**を選択します。</span><span class="sxs-lookup"><span data-stu-id="959d0-p103">In the Office 365 admin center, navigate to \*\* Users \*\* \> **Active users**. Click the **More** menu and select **Directory synchronization**.</span></span> 
  
![[詳細] メニューの [ディレクトリ同期を選択します](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
<span data-ttu-id="959d0-116">古い Office 365 管理センターでは、**ユーザー**に移動\>**アクティブなユーザー**、および選択**の設定\*\*\*\*作業中のディレクトリ同期**の横にあります。</span><span class="sxs-lookup"><span data-stu-id="959d0-116">In the old Office 365 admin center, navigate to **USERS** \> **Active Users**, and select **Set up** next to **Active Directory synchronization**.</span></span> 
  
![Active Directory の同期の横のセットを選択します。](media/bd95492b-d65e-4072-a6ee-e562f5f566c3.png)
  
<span data-ttu-id="959d0-118">Azure AD 接続をダウンロードするのには[、ウィザードの指示](set-up-directory-synchronization.md)に従います。</span><span class="sxs-lookup"><span data-stu-id="959d0-118">Follow the [instructions in the wizard](set-up-directory-synchronization.md) to download Azure AD Connect.</span></span> 
  
<span data-ttu-id="959d0-119">まだ Azure Active ディレクトリ同期 (ディレクトリ同期) を使用している場合を見て[Azure Active Directory 同期ツールのインストールと Office 365 の構成ウィザードのエラー メッセージをトラブルシューティングする方法](https://go.microsoft.com/fwlink/p/?LinkId=396717)をインストールするシステムの要件についてディレクトリ同期、必要なアクセス許可および一般的なエラーのトラブルシューティングを行う方法です。</span><span class="sxs-lookup"><span data-stu-id="959d0-119">If you are still using Azure Active Directory Sync (DirSync), take a look at [How to troubleshoot Azure Active Directory Sync Tool installation and Configuration Wizard error messages in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) for information about the system requirements to install dirsync, the permissions you need, and how to troubleshoot common errors.</span></span> 
  
<span data-ttu-id="959d0-120">Azure Active Directory 同期から Azure AD 接続を更新するには、[アップグレードの手順](https://go.microsoft.com/fwlink/p/?LinkId=733240)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="959d0-120">To update from Azure Active Directory Sync to Azure AD Connect, see [the upgrade instructions](https://go.microsoft.com/fwlink/p/?LinkId=733240).</span></span>
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a><span data-ttu-id="959d0-121">Office 365 のディレクトリ同期の問題の原因は一般的な解決</span><span class="sxs-lookup"><span data-stu-id="959d0-121">Resolving common causes of problems with directory synchronization in Office 365</span></span>

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a><span data-ttu-id="959d0-122">**同期されたオブジェクトは表示されないようにしたり、オンラインで更新またはサービスから同期エラーのレポートを取得します。**</span><span class="sxs-lookup"><span data-stu-id="959d0-122">**Synchronized objects aren't appearing or updating online, or I'm getting synchronization error reports from the Service.**</span></span>

- [<span data-ttu-id="959d0-123">アイデンティティの同期化と重複している属性の弾力性</span><span class="sxs-lookup"><span data-stu-id="959d0-123">Identity synchronization and duplicate attribute resiliency</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-office-365-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a><span data-ttu-id="959d0-124">**Office 365 管理センターで、アラートがあるか、または最新の同期イベントが発生されていない自動の電子メールを受信しています。**</span><span class="sxs-lookup"><span data-stu-id="959d0-124">**I have an alert in the Office 365 admin center, or am receiving automated emails that there hasn't been a recent synchronization event**</span></span>
- [<span data-ttu-id="959d0-125">Azure AD 接続と接続の問題のトラブルシューティングを行う</span><span class="sxs-lookup"><span data-stu-id="959d0-125">Troubleshoot connectivity issues with Azure AD Connect</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [<span data-ttu-id="959d0-126">Azure AD 接続アカウントとアクセス許可</span><span class="sxs-lookup"><span data-stu-id="959d0-126">Azure AD Connect Accounts and permissions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [<span data-ttu-id="959d0-127">Azure AD 接続の同期: Azure AD のサービス アカウントを管理する方法</span><span class="sxs-lookup"><span data-stu-id="959d0-127">Azure AD Connect sync: How to manage the Azure AD service account</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [<span data-ttu-id="959d0-128">Azure Active Directory が停止するか、またはディレクトリ同期は 1 日以上で、同期していない登録されている警告メッセージが表示しています。</span><span class="sxs-lookup"><span data-stu-id="959d0-128">Directory synchronization to Azure Active Directory stops or you're warned that sync hasn't registered in more than a day</span></span>](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-office-365-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a><span data-ttu-id="959d0-129">**パスワード ハッシュが同期されていない、または最近使用したパスワード ハッシュの同期がありますされていない Office 365 管理センターの警告が表示**</span><span class="sxs-lookup"><span data-stu-id="959d0-129">**Password hashes aren't synchronizing, or I'm seeing an alert in the Office 365 admin center that there hasn't been a recent password hash synchronization**</span></span>
- [<span data-ttu-id="959d0-130">Azure AD 接続の同期でのパスワード ハッシュの同期を実装します。</span><span class="sxs-lookup"><span data-stu-id="959d0-130">Implementing password hash synchronization with Azure AD Connect sync</span></span>](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a><span data-ttu-id="959d0-131">**オブジェクト クォータを超過したアラートが表示します。**</span><span class="sxs-lookup"><span data-stu-id="959d0-131">**I'm seeing an alert that Object quota exceeded**</span></span>
- <span data-ttu-id="959d0-p104">サービスを保護するための組み込みオブジェクトのクォータがあります。Office 365 に同期する必要のあるディレクトリに多数のオブジェクトがある場合は、クォータを増やすには、[ビジネス製品に関するサポートの連絡先](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)に必要があります。</span><span class="sxs-lookup"><span data-stu-id="959d0-p104">We have a built-in object quota to help protect the service. If you have too many objects in your directory that need to sync to Office 365, you'll have to [Contact support for business products](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) to increase your quota.</span></span>

### <a name="i-need-to-know-which-attributes-are-synchronized"></a><span data-ttu-id="959d0-134">**どの属性が同期されているか知る必要があります。**</span><span class="sxs-lookup"><span data-stu-id="959d0-134">**I need to know which attributes are synchronized**</span></span>
- <span data-ttu-id="959d0-135">オンプレミスとクラウド[は、ここで右](https://go.microsoft.com/fwlink/p/?LinkId=396719)の間で同期されるすべての属性の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="959d0-135">You can find a list of all the attributes that are synced between on-premises and the cloud [right here](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a><span data-ttu-id="959d0-136">**管理またはクラウドに同期されたオブジェクトを削除できません。**</span><span class="sxs-lookup"><span data-stu-id="959d0-136">**I can't manage or remove objects that were synchronized to the cloud**</span></span>
- <span data-ttu-id="959d0-p105">クラウドのみでオブジェクトを管理する準備ができて、ですか。または、オブジェクトを削除した設置が、クラウドに詰まっているではないでしょうか。見てこの[同期中にエラーのトラブルシューティング](https://go.microsoft.com/fwlink/p/?linkid=842044)とガイダンスの[サポート資料](https://go.microsoft.com/fwlink/p/?LinkId=396720)をこれらの問題を解決する方法にします。</span><span class="sxs-lookup"><span data-stu-id="959d0-p105">Are you ready to manage objects in the cloud only? Or is there an object that was deleted on-premises, but is stuck in the cloud? Take a look at this [Troubleshooting Errors during synchronization](https://go.microsoft.com/fwlink/p/?linkid=842044) and [support article](https://go.microsoft.com/fwlink/p/?LinkId=396720) for guidance on how to resolve these issues.</span></span>

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a><span data-ttu-id="959d0-140">**会社で同期可能なオブジェクトの数を超えたというエラー メッセージが表示されました。**</span><span class="sxs-lookup"><span data-stu-id="959d0-140">**I got an error message that my company has exceeded the number of objects that can be synchronized**</span></span>
- <span data-ttu-id="959d0-141">詳細を読み取ることができますこの問題について[は、ここ](https://go.microsoft.com/fwlink/p/?LinkId=396721)です。</span><span class="sxs-lookup"><span data-stu-id="959d0-141">You can read more about this issue [here](https://go.microsoft.com/fwlink/p/?LinkId=396721).</span></span>
   
## <a name="other-resources"></a><span data-ttu-id="959d0-142">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="959d0-142">Other resources</span></span>

- [<span data-ttu-id="959d0-143">ユーザー プリンシパル名の重複を修正するためのスクリプト</span><span class="sxs-lookup"><span data-stu-id="959d0-143">Script to fix duplicate user principal names</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [<span data-ttu-id="959d0-144">ディレクトリ同期 (.local ドメイン) などのルーティング不可能なドメインを準備する方法</span><span class="sxs-lookup"><span data-stu-id="959d0-144">How to prepare a non-routable domain (such as .local domain) for directory synchronization</span></span>](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [<span data-ttu-id="959d0-145">同期オブジェクトの総数をカウントするためのスクリプト</span><span class="sxs-lookup"><span data-stu-id="959d0-145">Script to count total synchronized objects</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [<span data-ttu-id="959d0-146">AD FS 2.0 のトラブルシューティングを行う</span><span class="sxs-lookup"><span data-stu-id="959d0-146">Troubleshoot AD FS 2.0</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [<span data-ttu-id="959d0-147">PowerShell を使用して、メールが有効なグループを空の DisplayName 属性を修正するには</span><span class="sxs-lookup"><span data-stu-id="959d0-147">Use PowerShell to fix empty DisplayName attributes for mail-enabled groups</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [<span data-ttu-id="959d0-148">PowerShell を使用して、重複する UPN を解決するには</span><span class="sxs-lookup"><span data-stu-id="959d0-148">Use PowerShell to fix duplicate UPN</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [<span data-ttu-id="959d0-149">PowerShell を使用して、重複する電子メール アドレスを修正するには</span><span class="sxs-lookup"><span data-stu-id="959d0-149">Use PowerShell to fix duplicate email addresses</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a><span data-ttu-id="959d0-150">診断ツール</span><span class="sxs-lookup"><span data-stu-id="959d0-150">Diagnostic tools</span></span>

<span data-ttu-id="959d0-p106">[IDFix ツール](prepare-directory-attributes-for-synch-with-idfix.md)を使用して、Office 365 への移行の準備として、オンプレミス Active Directory 環境での検出と id オブジェクトとその属性の修復を実行します。IDFix は、Active Directory の管理者は、Office 365 サービスとディレクトリ同期の責任です。</span><span class="sxs-lookup"><span data-stu-id="959d0-p106">[IDFix tool](prepare-directory-attributes-for-synch-with-idfix.md) is used to perform discovery and remediation of identity objects and their attributes in an on-premises Active Directory environment in preparation for migration to Office 365. IDFix is intended for the Active Directory administrators responsible for DirSync with the Office 365 service.</span></span> 

<span data-ttu-id="959d0-153">Microsoft ダウンロード センターから[IDFix ツールをダウンロード](https://go.microsoft.com/fwlink/p/?LinkId=396718)をしてください。</span><span class="sxs-lookup"><span data-stu-id="959d0-153">[Download the IDFix tool](https://go.microsoft.com/fwlink/p/?LinkId=396718) from the Microsoft download center.</span></span>