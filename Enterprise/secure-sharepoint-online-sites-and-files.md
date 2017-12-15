---
title: "SharePoint Online サイトとファイルをセキュリティで保護する"
ms.author: bcarter
author: bcarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: concetpual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- Ent_Architecture
ms.assetid: 1d51bd87-17bf-457c-b698-61821de3afa0
description: "SharePoint Online および Office 365 内のファイルを保護するための概要: 構成の推奨事項です。"
ms.openlocfilehash: 0657ff5f3b6668d8cd5ae361bd890ef35c23608b
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="secure-sharepoint-online-sites-and-files"></a><span data-ttu-id="f0e07-103">SharePoint Online サイトとファイルをセキュリティで保護する</span><span class="sxs-lookup"><span data-stu-id="f0e07-103">Secure SharePoint Online sites and files</span></span>

 <span data-ttu-id="f0e07-104">**概要:**SharePoint Online および Office 365 内のファイルを保護するために推奨されている構成を取り上げます。</span><span class="sxs-lookup"><span data-stu-id="f0e07-104">**Summary:** Configuration recommendations for protecting files in SharePoint Online and Office 365.</span></span>
  
<span data-ttu-id="f0e07-p101">この記事では、SharePoint Online チーム サイトとファイルの保護を、セキュリティとコラボレーションのしやすさのバランスを取りながら構成するための推奨事項を示します。この記事では、4 つの異なる構成を定義します。最初は、最もオープンな共有ポリシーを使用した、組織内のパブリック サイトです。それ以外の各構成は、保護のセットアップには有効な手段ですが、リソースへのアクセスやリソース上でのコラボレーションは、関連したユーザーのセットに限定されます。これらの推奨事項を開始点として使用し、組織のニーズを満たすように構成を調整してください。</span><span class="sxs-lookup"><span data-stu-id="f0e07-p101">This article provides recommendations for configuring SharePoint Online team sites and file protection that balances security with ease of collaboration. This article defines four different configurations, starting with a public site within your organization with the most open sharing policies. Each additional configuration represents a meaningful step up in protection, but the ability to access and collaborate on resources is reduced to the relevant set of users. Use these recommendations as a starting point and adjust the configurations to meet the needs of your organization.</span></span> 
  
<span data-ttu-id="f0e07-109">この記事で示されている構成は、データ、ID、デバイスを保護するための 3 つの層に関する Microsoft の推奨事項と調和しています。</span><span class="sxs-lookup"><span data-stu-id="f0e07-109">The configurations in this article align with Microsoft's recommendations for three tiers of protection for data, identities, and devices:</span></span>
  
- <span data-ttu-id="f0e07-110">ベースライン保護</span><span class="sxs-lookup"><span data-stu-id="f0e07-110">Baseline protection</span></span>
    
- <span data-ttu-id="f0e07-111">機密保護</span><span class="sxs-lookup"><span data-stu-id="f0e07-111">Sensitive protection</span></span>
    
- <span data-ttu-id="f0e07-112">高機密保護</span><span class="sxs-lookup"><span data-stu-id="f0e07-112">Highly confidential protection</span></span>
    
<span data-ttu-id="f0e07-113">これらの層およびそれぞれの層に関して推奨されている機能については、次の資料を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0e07-113">For more information about these tiers and capabilities recommended for each tier, see the following resources.</span></span> 
  
- [<span data-ttu-id="f0e07-114">Office 365 の ID とデバイス保護</span><span class="sxs-lookup"><span data-stu-id="f0e07-114">Identity and Device Protection for Office 365</span></span>](microsoft-cloud-it-architecture-resources.md#BKMK_O365IDP)
    
- [<span data-ttu-id="f0e07-115">Office 365 のファイル保護ソリューション</span><span class="sxs-lookup"><span data-stu-id="f0e07-115">File Protection Solutions in Office 365</span></span>](microsoft-cloud-it-architecture-resources.md#BKMK_O365fileprotect)
    
## <a name="capability-overview"></a><span data-ttu-id="f0e07-116">機能の概要</span><span class="sxs-lookup"><span data-stu-id="f0e07-116">Capability overview</span></span>

<span data-ttu-id="f0e07-p102">SharePoint Online チーム サイトの推奨事項は、Office 365 のさまざまな機能に基づいています。高機密サイトに関しては、Azure Information Protection が推奨されています。これは Enterprise Mobility + Security (EMS) に含まれています。</span><span class="sxs-lookup"><span data-stu-id="f0e07-p102">Recommendations for SharePoint Online team sites draw on a variety of Office 365 capabilities. For highly confidential sites, Azure Information Protection is recommended. This is included in Enterprise Mobility + Security (EMS).</span></span> 
  
<span data-ttu-id="f0e07-120">次の図は、4 つの SharePoint Online チーム サイトについて推奨されている構成を示しています。</span><span class="sxs-lookup"><span data-stu-id="f0e07-120">The following illustration shows the recommended configurations for four SharePoint Online team sites.</span></span>
  
![SharePoint サイトの推奨構成](images/ad0dcd70-f6f5-465c-8d16-1889481ca07a.png)
  
<span data-ttu-id="f0e07-122">次の点が示されています。</span><span class="sxs-lookup"><span data-stu-id="f0e07-122">As illustrated:</span></span>
  
- <span data-ttu-id="f0e07-p103">ベースライン保護には、SharePoint Online チーム サイト用の 2 つのオプション、つまりパブリック サイトとプライベート サイトが含まれます。パブリック サイトは、組織内のだれもが検出およびアクセスできます。プライベート サイトは、サイトのメンバーのみが検出とアクセスを行うことができます。どちらのサイト構成においても、グルーブの外部との共有を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="f0e07-p103">Baseline protection includes two options for SharePoint Online team sites — a public site and private site. Public sites can be discovered and accessed by anybody in the organization. Private sites can only be discovered and accessed by members of the site. Both of these site configurations allow for sharing outside the group.</span></span> 
    
- <span data-ttu-id="f0e07-127">機密および高機密保護のためのサイトは、アクセスを特定のグループのメンバーのみに限定しているプライベート サイトになります。</span><span class="sxs-lookup"><span data-stu-id="f0e07-127">Sites for sensitive and highly confidential protection are private sites with access limited only to members of specific groups.</span></span>
    
- <span data-ttu-id="f0e07-p104">Office 365 ラベルでは、必要な保護レベルを使用してデータを分類できます。それぞれの SharePoint Online チーム サイトは、サイトの既定ラベルを使用して、ドキュメント ライブラリ内のファイルに自動的にラベルを適用するよう構成されています。4 つのサイト構成に応じて、この例ではラベルを内部パブリック、プライベート、機密、高機密としています。ユーザーはラベルを変更できますが、この構成ではすべてのファイルに既定ラベルが適用されます。</span><span class="sxs-lookup"><span data-stu-id="f0e07-p104">Office 365 labels provide a way to classify data with a needed protection level. Each of the SharePoint Online team sites are configured to automatically label files in document libraries with a default label for the site. Corresponding to the four site configurations, the labels in this example are Internal Public, Private, Sensitive, and Highly Confidential. Users can change the labels, but this configuration ensures all files receive a default label.</span></span>
    
- <span data-ttu-id="f0e07-132">データ損失防止 (DLP) ポリシーは、Office 365 の機密および高機密ラベル向けに構成されており、これらのタイプのファイルをユーザーが組織外に送信しようとすると警告を表示したり、その処理を防止したりします。</span><span class="sxs-lookup"><span data-stu-id="f0e07-132">Data loss prevention (DLP) policies are configured for the Sensitive and Highly Confidential Office 365 labels to either warn or prevent users when they attempt to send these types of files outside the organization.</span></span>
    
- <span data-ttu-id="f0e07-133">高機密保護で構成されているサイトの場合、Azure Information Protection はファイルの暗号化とファイルへのアクセス許可の付与を行います。</span><span class="sxs-lookup"><span data-stu-id="f0e07-133">For sites configured with highly confidential protection, Azure Information Protection encrypts and grants permissions for files.</span></span>
    
## <a name="tenant-wide-settings-for-sharepoint-online-and-onedrive-for-business"></a><span data-ttu-id="f0e07-134">SharePoint Online と OneDrive for Business に関するテナント全体の設定</span><span class="sxs-lookup"><span data-stu-id="f0e07-134">Tenant-wide settings for SharePoint Online and OneDrive for Business</span></span>

<span data-ttu-id="f0e07-p105">SharePoint Online と OneDrive for Business には、すべてのサイトとユーザーに影響を及ぼすテナント全体の設定が含まれています。これらの設定の中には、サイト レベルにおいてより制限の強いもの (ただし、既定以下にはできません) に調整できるものもあります。このセクションでは、セキュリティとコラボレーションに影響を与えるテナント全体の設定について取り上げます。</span><span class="sxs-lookup"><span data-stu-id="f0e07-p105">SharePoint Online and OneDrive for Business include tenant-wide settings that affect all sites and users. Some of these settings can also be adjusted at the site level to be more restrictive (but not less). This section discusses tenant-wide settings that affect security and collaboration.</span></span> 
  
### <a name="sharing"></a><span data-ttu-id="f0e07-138">共有</span><span class="sxs-lookup"><span data-stu-id="f0e07-138">Sharing</span></span>

<span data-ttu-id="f0e07-139">このソリューションでは、次のようなテナント全体の設定をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f0e07-139">For this solution, we recommend the following tenant-wide settings:</span></span>
  
- <span data-ttu-id="f0e07-140">すべてのアカウントの種類によるすべての共有 (匿名の共有を含む) を許可する既定の共有ポリシーを保持します。</span><span class="sxs-lookup"><span data-stu-id="f0e07-140">Keep the default sharing policy that allows all sharing with all account types, including anonymous sharing.</span></span>
    
- <span data-ttu-id="f0e07-141">必要に応じて、匿名リンクの有効期間を設定します。</span><span class="sxs-lookup"><span data-stu-id="f0e07-141">Set anonymous links to expire, if desired.</span></span>
    
- <span data-ttu-id="f0e07-p106">既定のリンクの種類を「内部」に変更します。これにより、組織外で意図せずデータが漏洩する事態を避けることができます。</span><span class="sxs-lookup"><span data-stu-id="f0e07-p106">Change the default link type for sharing to Internal. This helps prevent accidental data leakage outside your organization.</span></span>
    
<span data-ttu-id="f0e07-p107">外部共有を許可することは直感に反しているように思えるかもしれませんが、これは電子メールでファイルを送信するよりもファイル共有をより制御できます。SharePoint Online と Outlook は連携して、セキュリティで保護されたファイルのコラボレーションを提供します。</span><span class="sxs-lookup"><span data-stu-id="f0e07-p107">While it might seem counterintuitive to allow external sharing, this approach provides more control over file sharing compared to sending files in email. SharePoint Online and Outlook work together to provide secure collaboration on files.</span></span> 
  
- <span data-ttu-id="f0e07-146">既定では、Outlook は、電子メールでファイルを送信する代わりに、ファイルへのリンクを共有します。</span><span class="sxs-lookup"><span data-stu-id="f0e07-146">By default, Outlook shares a link to a file instead of sending the file in email.</span></span> 
    
- <span data-ttu-id="f0e07-147">SharePoint Online と OneDrive for Business を使用すると、組織の内部と外部の共同作成者にファイルへのリンクを簡単に共有できます。</span><span class="sxs-lookup"><span data-stu-id="f0e07-147">SharePoint Online and OneDrive for Business make it easy to share links to files with contributors who are both inside and outside your organization</span></span>
    
<span data-ttu-id="f0e07-p108">また、外部共有を管理することもできます。たとえば、以下の事柄が可能です。</span><span class="sxs-lookup"><span data-stu-id="f0e07-p108">You also have controls to help govern external sharing. For example, you can:</span></span>
  
- <span data-ttu-id="f0e07-150">匿名ゲスト リンクを無効にします。</span><span class="sxs-lookup"><span data-stu-id="f0e07-150">Disable an anonymous guest link.</span></span>
    
- <span data-ttu-id="f0e07-151">サイトへのユーザー アクセスを取り消します。</span><span class="sxs-lookup"><span data-stu-id="f0e07-151">Revoke user access to a site.</span></span>
    
- <span data-ttu-id="f0e07-152">特定のサイトまたはドキュメントへのアクセス権を持つユーザーを確認します。</span><span class="sxs-lookup"><span data-stu-id="f0e07-152">See who has access to a specific site or document.</span></span>
    
- <span data-ttu-id="f0e07-153">匿名リンクの有効期間を設定します (テナント設定)。</span><span class="sxs-lookup"><span data-stu-id="f0e07-153">Set anonymous sharing links to expire (tenant setting).</span></span>
    
- <span data-ttu-id="f0e07-154">組織外で共有できるユーザーを限定します (テナント設定)。</span><span class="sxs-lookup"><span data-stu-id="f0e07-154">Limit who can share outside your organization (tenant setting).</span></span>
    
### <a name="use-external-sharing-together-with-data-loss-prevention-dlp"></a><span data-ttu-id="f0e07-155">データ損失防止 (DLP) を外部共有と併用します。</span><span class="sxs-lookup"><span data-stu-id="f0e07-155">Use external sharing together with data loss prevention (DLP)</span></span>

<span data-ttu-id="f0e07-p109">外部共有を許可しない場合、ビジネスで必要なユーザーは、代替のツールと手段を使用することになります。Microsoft は、機密ファイルおよび高機密ファイルを保護するために DLP ポリシーと外部共有を組み合わせることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f0e07-p109">If you don't allow external sharing, users with a business need will find alternate tools and methods. Microsoft recommends you combine external sharing with DLP policies to protect sensitive and highly confidential files.</span></span>
  
### <a name="device-access-settings"></a><span data-ttu-id="f0e07-158">デバイス アクセスの設定</span><span class="sxs-lookup"><span data-stu-id="f0e07-158">Device access settings</span></span>

<span data-ttu-id="f0e07-p110">SharePoint Online と OneDrive for Business のデバイス アクセスの設定では、アクセスを参照のみ (ファイルをダウンロードすることはできません) に限定するか、アクセスをブロックするかを指定できます。現在これらの設定は先行リリースに含まれ、テナント全体で適用されます。まもなく、デバイス アクセス ポリシーをサイト レベルで構成できるようになります。このソリューションの場合、テナント全体で適用されるデバイス アクセスの設定を使用しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f0e07-p110">Device access settings for SharePoint Online and OneDrive for Business let you determine whether access is limited to browser only (files can't be downloaded) or if access is blocked. These settings are currently in First Release and apply tenant-wide. Coming soon is the ability to configure device access policies at the site level. For this solution, we recommend not using device access settings that apply tenant-wide.</span></span>
  
<span data-ttu-id="f0e07-163">先行リリースのデバイス アクセスの設定を使用するには、「[Office 365 で標準または先行リリース オプションを設定する](https://support.office.com/article/Set-up-the-Standard-or-First-Release-options-in-Office-365-3B3ADFA4-1777-4FF0-B606-FB8732101F47)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0e07-163">To use device access settings while these are in first release: [Set up the Standard or First Release Options in Office 365](https://support.office.com/article/Set-up-the-Standard-or-First-Release-options-in-Office-365-3B3ADFA4-1777-4FF0-B606-FB8732101F47).</span></span>
  
### <a name="onedrive-for-business"></a><span data-ttu-id="f0e07-164">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="f0e07-164">OneDrive for Business</span></span>

<span data-ttu-id="f0e07-p111">これらの設定を確認し、OneDrive for Business サイトの既定の設定を変更するかどうかを判断してください。現在、共有とデバイス アクセスの設定は SharePoint Online 管理センターの設定からコピーされており、両方の環境に適用されます。</span><span class="sxs-lookup"><span data-stu-id="f0e07-p111">Visit these settings to decide if you want to change the default settings for OneDrive for Business sites. Currently, the sharing and device access settings are duplicated from the SharePoint Online admin center and apply to both environments.</span></span>
  
## <a name="sharepoint-team-site-configuration"></a><span data-ttu-id="f0e07-167">SharePoint チーム サイトの構成</span><span class="sxs-lookup"><span data-stu-id="f0e07-167">SharePoint team site configuration</span></span>

<span data-ttu-id="f0e07-p112">次の表に、この記事で前述した各チーム サイトの構成をまとめます。これらの構成を開始点の推奨事項として使用し、組織のニーズに合うようサイトの種類と構成を調整します。すべての組織がすべてのサイトの種類を必要とするわけではありません。高機密保護が必要となる組織はごくわずかです。</span><span class="sxs-lookup"><span data-stu-id="f0e07-p112">The following table summarizes the configuration for each of the team sites described earlier in this article. Use these configurations as starting point recommendations and adjust the site types and configurations to meet the needs of your organization. Not every organization needs every type of site. Only a small number of organizations require highly confidential protection.</span></span>
  
||||||
|:-----|:-----|:-----|:-----|:-----|
||<span data-ttu-id="f0e07-172">**ベースライン保護 1**</span><span class="sxs-lookup"><span data-stu-id="f0e07-172">**Baseline protection #1**</span></span> <br/> |<span data-ttu-id="f0e07-173">**ベースラン保護 2**</span><span class="sxs-lookup"><span data-stu-id="f0e07-173">**Baseline protection #2**</span></span> <br/> |<span data-ttu-id="f0e07-174">**機密保護**</span><span class="sxs-lookup"><span data-stu-id="f0e07-174">**Sensitive protection**</span></span> <br/> |<span data-ttu-id="f0e07-175">**高機密**</span><span class="sxs-lookup"><span data-stu-id="f0e07-175">**Highly confidential**</span></span> <br/> |
|<span data-ttu-id="f0e07-176">説明</span><span class="sxs-lookup"><span data-stu-id="f0e07-176">Description</span></span>  <br/> |<span data-ttu-id="f0e07-177">組織内でのオープンな検出と共同作業。</span><span class="sxs-lookup"><span data-stu-id="f0e07-177">Open discovery and collaboration within the organization.</span></span>  <br/> |<span data-ttu-id="f0e07-178">グループ外で共有が許可されている、プライベート サイトとグループ。</span><span class="sxs-lookup"><span data-stu-id="f0e07-178">Private site and group with sharing allowed outside the group.</span></span>  <br/> |<span data-ttu-id="f0e07-p113">アクセス レベルが特定のグループのメンバーシップによって定義されている、独立したサイト。共有はサイトのメンバーにのみ許可されます。組織外にファイルを送信しようとすると、DLP はユーザーに警告します。</span><span class="sxs-lookup"><span data-stu-id="f0e07-p113">Isolated site, in which levels of access are defined by membership in specific groups. Sharing is only allowed to members of the site. DLP warns users when attempting to send files outside the organization.</span></span>  <br/> |<span data-ttu-id="f0e07-p114">独立したサイトと、Azure Information Protection によるファイルの暗号化とアクセス許可。DLP はユーザーがファイルを組織の外部に送信できないようにします。</span><span class="sxs-lookup"><span data-stu-id="f0e07-p114">Isolated site + file encryption and permissions with Azure Information Protection. DLP prevents users from sending files outside the organization.</span></span>  <br/> |
|<span data-ttu-id="f0e07-184">プライベート サイトまたはパブリック チーム サイト</span><span class="sxs-lookup"><span data-stu-id="f0e07-184">Private or public team site</span></span>  <br/> |<span data-ttu-id="f0e07-185">パブリック</span><span class="sxs-lookup"><span data-stu-id="f0e07-185">Public</span></span>  <br/> |<span data-ttu-id="f0e07-186">プライベート</span><span class="sxs-lookup"><span data-stu-id="f0e07-186">Private</span></span>  <br/> |<span data-ttu-id="f0e07-187">プライベート</span><span class="sxs-lookup"><span data-stu-id="f0e07-187">Private</span></span>  <br/> |<span data-ttu-id="f0e07-188">プライベート</span><span class="sxs-lookup"><span data-stu-id="f0e07-188">Private</span></span>  <br/> |
|<span data-ttu-id="f0e07-189">アクセス権を持つユーザー</span><span class="sxs-lookup"><span data-stu-id="f0e07-189">Who has access?</span></span>  <br/> |<span data-ttu-id="f0e07-190">B2B のユーザーとゲスト ユーザーを含む、組織の全員。</span><span class="sxs-lookup"><span data-stu-id="f0e07-190">Everybody in the organization, including B2B users and guest users.</span></span>  <br/> |<span data-ttu-id="f0e07-p115">サイトのメンバーのみ。他のユーザーは、アクセス権を要求できます。</span><span class="sxs-lookup"><span data-stu-id="f0e07-p115">Members of the site only. Others can request access.</span></span>  <br/> |<span data-ttu-id="f0e07-p116">サイトのメンバーのみ。他のユーザーは、アクセス権を要求できます。</span><span class="sxs-lookup"><span data-stu-id="f0e07-p116">Members of the site only. Others can request access.</span></span>  <br/> |<span data-ttu-id="f0e07-p117">メンバーのみ。他のユーザーは、アクセス権を要求できません。</span><span class="sxs-lookup"><span data-stu-id="f0e07-p117">Members only. Others cannot request access.</span></span>  <br/> |
|<span data-ttu-id="f0e07-197">サイト レベルの共有制御</span><span class="sxs-lookup"><span data-stu-id="f0e07-197">Site-level sharing controls</span></span>  <br/> |<span data-ttu-id="f0e07-p118">すべてのユーザーと共有できます。既定の設定です。</span><span class="sxs-lookup"><span data-stu-id="f0e07-p118">Sharing allowed with anybody. Default settings.</span></span>  <br/> |<span data-ttu-id="f0e07-p119">すべてのユーザーと共有できます。既定の設定です。</span><span class="sxs-lookup"><span data-stu-id="f0e07-p119">Sharing allowed with anybody. Default settings.</span></span>  <br/> |<span data-ttu-id="f0e07-202">メンバーはサイトへのアクセスを共有できません。</span><span class="sxs-lookup"><span data-stu-id="f0e07-202">Members cannot share access to the site.</span></span>  <br/> <span data-ttu-id="f0e07-203">メンバーでなくてもサイトへのアクセスを要求できますが、これらの要求はサイト管理者が対応する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0e07-203">Non-members can request access to the site, but these requests need to be addressed by a site administrator.</span></span>  <br/> |<span data-ttu-id="f0e07-204">メンバーはサイトへのアクセスを共有できません。</span><span class="sxs-lookup"><span data-stu-id="f0e07-204">Members cannot share access to the site.</span></span>  <br/> <span data-ttu-id="f0e07-205">メンバーでなければ、サイトやコンテンツへのアクセス権を要求できません。</span><span class="sxs-lookup"><span data-stu-id="f0e07-205">Non-members cannot request access to the site or contents.</span></span>  <br/> |
|<span data-ttu-id="f0e07-206">サイト レベルのデバイス アクセス制御</span><span class="sxs-lookup"><span data-stu-id="f0e07-206">Site-level device access controls</span></span>  <br/> |<span data-ttu-id="f0e07-207">追加制御はありません。</span><span class="sxs-lookup"><span data-stu-id="f0e07-207">No additional controls.</span></span>  <br/> |<span data-ttu-id="f0e07-208">追加制御はありません。</span><span class="sxs-lookup"><span data-stu-id="f0e07-208">No additional controls.</span></span>  <br/> |<span data-ttu-id="f0e07-p120">サイト レベルの制御は準備中です。ユーザーは、非対応デバイスまたはドメインに参加していないデバイスにファイルをダウンロードできません。他のすべてのデバイスからは参照専用のアクセスが許可されます。</span><span class="sxs-lookup"><span data-stu-id="f0e07-p120">Site-level controls are coming soon, which prevents users from downloading files to non-compliant or non-domain joined devices. This allows browser-only access from all other devices.</span></span>  <br/> |<span data-ttu-id="f0e07-211">サイト レベルの制御は準備中です。非対応デバイスまたはドメインに参加していないデバイスへのファイルのダウンロードをブロックします。</span><span class="sxs-lookup"><span data-stu-id="f0e07-211">Site-level controls are coming soon, which blocks downloading of files to non-compliant or non-domain joined devices.</span></span>  <br/> |
|<span data-ttu-id="f0e07-212">Office 365 のラベル</span><span class="sxs-lookup"><span data-stu-id="f0e07-212">Office 365 labels</span></span>  <br/> |<span data-ttu-id="f0e07-213">内部パブリック</span><span class="sxs-lookup"><span data-stu-id="f0e07-213">Internal Public</span></span>  <br/> |<span data-ttu-id="f0e07-214">プライベート</span><span class="sxs-lookup"><span data-stu-id="f0e07-214">Private</span></span>  <br/> |<span data-ttu-id="f0e07-215">機密</span><span class="sxs-lookup"><span data-stu-id="f0e07-215">Sensitive</span></span>  <br/> |<span data-ttu-id="f0e07-216">高機密</span><span class="sxs-lookup"><span data-stu-id="f0e07-216">Highly Confidential</span></span>  <br/> |
|<span data-ttu-id="f0e07-217">DLP ポリシー</span><span class="sxs-lookup"><span data-stu-id="f0e07-217">DLP policies</span></span>  <br/> |||<span data-ttu-id="f0e07-218">機密のラベルが付いているファイルを組織の外部に送信するときにユーザーに警告を表示します。</span><span class="sxs-lookup"><span data-stu-id="f0e07-218">Warn users when sending files that are labeled as Sensitive outside the organization.</span></span>  <br/> <span data-ttu-id="f0e07-219">クレジット カード番号や他の個人データなど、機密データの種類の外部共有をブロックするには、これらのデータの種類 (自分で構成したカスタム データの種類を含む) に追加の DLP ポリシーを構成できます。</span><span class="sxs-lookup"><span data-stu-id="f0e07-219">To block external sharing of sensitive data types, such as credit card numbers or other personal data, you can configure additional DLP policies for these data types (including custom data types you configure).</span></span>  <br/> |<span data-ttu-id="f0e07-p121">ユーザーが高機密のラベルが付けられているファイルを組織の外部に送信できないようにします。ファイルの共有相手など、理由を提供することよって、ユーザーはこの設定を上書きできます。</span><span class="sxs-lookup"><span data-stu-id="f0e07-p121">Block users from sending files that are labeled as highly confidential outside organization. Allow users to override this by providing justification, including who they are sharing the file with.</span></span>  <br/> |
|<span data-ttu-id="f0e07-222">Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="f0e07-222">Azure Information Protection</span></span>  <br/> ||||<span data-ttu-id="f0e07-p122">Azure Information Protection を使用して、ファイルの暗号化とファイルへのアクセス許可の付与を自動化します。この保護は、リークが発生した場合に備えて、移動するファイルに適用されます。</span><span class="sxs-lookup"><span data-stu-id="f0e07-p122">Use Azure Information Protection to automatically encrypt and grant permissions to files. This protection travels with the files in case they are leaked.</span></span>  <br/> <span data-ttu-id="f0e07-p123">Office 365 は、Azure Information Protection で暗号化されたファイルを読み取ることができません。さらに、DLP ポリシーが操作できるのはメタデータ (ラベルを含む) のみで、これらのファイルのコンテンツ (ファイル内のクレジット カード番号など) を操作することはできません。</span><span class="sxs-lookup"><span data-stu-id="f0e07-p123">Office 365 cannot read files encrypted with Azure Information Protection. Additionally, DLP policies can only work with the metadata (including labels) but not the contents of these files (such as credit card numbers within files).</span></span>  <br/> |
   
<span data-ttu-id="f0e07-p124">このソリューションで 4 つの異なる種類の SharePoint Online チーム サイトを展開する手順については、「[3 つの層による保護用のサイトを展開する](deploy-sharepoint-online-sites-for-three-tiers-of-protection.md)」を参照してください。開発/テスト環境の作成手順については、「[開発/テスト環境の SharePoint Online サイトをセキュリティで保護する](secure-sharepoint-online-sites-in-a-dev-test-environment.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0e07-p124">For the steps to deploy the four different types of SharePoint Online team sites in this solution, see [Deploy SharePoint Online sites for three tiers of protection](deploy-sharepoint-online-sites-for-three-tiers-of-protection.md). For the steps to create a dev/test environment, see [Secure SharePoint Online sites in a dev/test environment](secure-sharepoint-online-sites-in-a-dev-test-environment.md).</span></span> 
  
## <a name="office-365-classification-and-labels"></a><span data-ttu-id="f0e07-229">Office 365 の分類とラベル</span><span class="sxs-lookup"><span data-stu-id="f0e07-229">Office 365 classification and labels</span></span>

<span data-ttu-id="f0e07-p125">機密データを含む環境では、Office 365 のラベルを使用することをお勧めします。Office 365 ラベルの構成と発行が完了した後、次のことを行えるようになります。</span><span class="sxs-lookup"><span data-stu-id="f0e07-p125">Using Office 365 labels is recommended for environments with sensitive data. After you configure and publish Office 365 labels:</span></span>
  
- <span data-ttu-id="f0e07-232">SharePoint Online チーム サイトのドキュメント ライブラリに既定のラベルを適用することにより、それらのライブラリ内のすべてのドキュメントに既定のラベルを適用することができます。</span><span class="sxs-lookup"><span data-stu-id="f0e07-232">You can apply a default label to a document library in a SharePoint Online team site, so that all documents in that library get the default label.</span></span> 
    
- <span data-ttu-id="f0e07-233">コンテンツが特定の条件に一致するときには、ラベルを自動的に適用できます。</span><span class="sxs-lookup"><span data-stu-id="f0e07-233">You can apply labels to content automatically if it matches specific conditions.</span></span>
    
- <span data-ttu-id="f0e07-234">Office 365 のラベルに基づいた DLP ポリシーを適用できます。</span><span class="sxs-lookup"><span data-stu-id="f0e07-234">You can apply DLP policies that are based on Office 365 labels.</span></span>
    
- <span data-ttu-id="f0e07-p126">組織内のユーザーは、Outlook on the web、Outlook 2010 以降、OneDrive for Business、SharePoint Online、Office 365 グループのコンテンツに手動でラベルを適用できます。ユーザーは自分が操作するコンテンツの種類を最もよく知っているので、コンテンツを分類して適切な DLP ポリシーを適用できます。</span><span class="sxs-lookup"><span data-stu-id="f0e07-p126">People in your organization can apply a label manually to content in Outlook on the web, Outlook 2010 and later, OneDrive for Business, SharePoint Online, and Office 365 groups. Users often know best what type of content they're working with, so they can classify it and have the appropriate DLP policy applied.</span></span>
    
![SharePoint サイトの推奨構成](images/7fed0126-ab4a-4480-922c-681970642339.png)
  
<span data-ttu-id="f0e07-238">示されているように、このソリューションでは次のラベルを作成します。</span><span class="sxs-lookup"><span data-stu-id="f0e07-238">As illustrated, this solution includes creating the following labels:</span></span>
  
- <span data-ttu-id="f0e07-239">高機密</span><span class="sxs-lookup"><span data-stu-id="f0e07-239">Highly Confidential</span></span>
    
- <span data-ttu-id="f0e07-240">機密</span><span class="sxs-lookup"><span data-stu-id="f0e07-240">Sensitive</span></span>
    
- <span data-ttu-id="f0e07-241">プライベート</span><span class="sxs-lookup"><span data-stu-id="f0e07-241">Private</span></span>
    
- <span data-ttu-id="f0e07-242">内部パブリック</span><span class="sxs-lookup"><span data-stu-id="f0e07-242">Internal Public</span></span>
    
<span data-ttu-id="f0e07-p127">これらのラベルは、図で推奨されているサイトと、この記事で前述したグラフにマップされます。このソリューションでは、機密および高機密というラベルの付いたファイルの漏洩を防ぐために DLP ポリシーを構成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f0e07-p127">These labels are mapped to the recommended sites in the illustrations and charts earlier in this article. This solution recommends configuring DLP policies to help prevent the leakage of files labeled as Sensitive and Highly Confidential.</span></span>
  
<span data-ttu-id="f0e07-245">このソリューションで Office 365 のラベルと DLP ポリシーを構成する手順については、「[Office 365 のラベルと DLP の SharePoint Online のファイルを保護します。](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0e07-245">For the steps to configure Office 365 labels and DLP policies in this solution, see [Protect SharePoint Online files with Office 365 labels and DLP](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md).</span></span>
  
## <a name="azure-information-protection"></a><span data-ttu-id="f0e07-246">Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="f0e07-246">Azure Information Protection</span></span>

<span data-ttu-id="f0e07-p128">Azure Information Protection を使用して、ファイルが移動する場所に関係なく、ラベルと保護を適用します。このソリューションでは、スコープ付きの Azure Information Protection ポリシーと高機密ラベルのサブラベルを使用して、最高レベルのセキュリティによる保護が必要なファイルを暗号化して、それらのファイルにアクセス許可を付与することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f0e07-p128">Use Azure Information Protection to apply labels and protections that follow the files wherever they go. For this solution, we recommend you use a scoped Azure Information Protection policy and a sub-label of the Highly Confidential label to encrypt and grant permissions to files that need to be protected with the highest level of security.</span></span> 
  
<span data-ttu-id="f0e07-p129">Azure Information Protection 暗号化が Office 365 に格納されているファイルに適用される場合、このサービスはこれらのファイルのコンテンツを処理することはできないことにご注意ください。共同編集、電子情報開示、検索、Delve、他の共同作業機能は動作しません。DLP ポリシーが操作できるのはメタデータ (Office 365 ラベルを含む) のみで、それらのファイルのコンテンツ (ファイル内のクレジットカード番号など) を操作することはできません。</span><span class="sxs-lookup"><span data-stu-id="f0e07-p129">Be aware that when Azure Information Protection encryption is applied to files stored in Office 365, the service cannot process the contents of these files. Co-authoring, eDiscovery, search, Delve, and other collaborative features do not work. DLP policies can only work with the metadata (including Office 365 labels) but not the contents of these files (such as credit card numbers within files).</span></span>
  
![Azure Information Protection は Azure で設定され、ラベルはクライアント ツールバーに表示される](images/1266a7a0-5078-49ab-bbf1-b0cf41451f62.png)
  
<span data-ttu-id="f0e07-253">次の点が示されています。</span><span class="sxs-lookup"><span data-stu-id="f0e07-253">As illustrated:</span></span>
  
- <span data-ttu-id="f0e07-p130">Azure Information Protection ポリシーとラベルは Microsoft Azure ポータルで構成します。スコープ付きの Azure Information Protection ポリシーのサブラベルを構成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f0e07-p130">You configure Azure Information Protection policies and labels in the Microsoft Azure portal. Configuring a sub-label of a scoped Azure Information Protection policy is recommended.</span></span>
    
- <span data-ttu-id="f0e07-256">Azure Information Protection のラベルは、Office アプリケーションで **[Information Protection]** バーとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="f0e07-256">Azure Information Protection labels show up as an **Information protection** bar in Office applications.</span></span>
    
### <a name="adding-permissions-for-external-users"></a><span data-ttu-id="f0e07-257">外部ユーザーに対するアクセス許可の追加</span><span class="sxs-lookup"><span data-stu-id="f0e07-257">Adding permissions for external users</span></span>

<span data-ttu-id="f0e07-p131">Azure Information Protection で保護されているファイルにアクセス権を外部ユーザーに付与するためには 2 つの方法があります。どちらの場合も、外部ユーザーは Azure AD アカウントが必要です。外部ユーザーが Azure AD を使用する組織のメンバーではない場合、サインアップ ページ ([https://aka.ms/aip-signup](https://aka.ms/aip-signup)) を使用して個人で Azure AD アカウントを取得できます。</span><span class="sxs-lookup"><span data-stu-id="f0e07-p131">There are two ways you can grant external users access to files protected with Azure Information Protection. In both these cases, external users must have an Azure AD account. If external users aren't members of an organization that uses Azure AD, they can obtain an Azure AD account as an individual by using this sign-up page: [https://aka.ms/aip-signup](https://aka.ms/aip-signup).</span></span>
  
- <span data-ttu-id="f0e07-261">外部ユーザーを、ラベルの保護の構成に使用する Azure AD グループに追加します。</span><span class="sxs-lookup"><span data-stu-id="f0e07-261">Add external users to an Azure AD group that is used to configure protection for a label</span></span>
    
     <span data-ttu-id="f0e07-p132">最初のディレクトリで B2B のユーザーとしてアカウントを追加する必要があります。いくつかの[グループ メンバーシップのキャッシュ Azure 著作権管理で](https://docs.microsoft.com/information-protection/plan-design/prepare#group-membership-caching-by-azure-rights-management)の時間がかかります。この方法ではラベル (Azure AD グループにユーザーを追加する前に保護されたファイルであっても) で保護されているすべての既存のファイルにアクセス許可が与えられます。</span><span class="sxs-lookup"><span data-stu-id="f0e07-p132">You'll need to first add the account as a B2B user in your directory. It can take a couple of hours for [group membership caching by Azure Rights Management](https://docs.microsoft.com/information-protection/plan-design/prepare#group-membership-caching-by-azure-rights-management). With this method, permissions are granted to all existing files protected with the label (even files protected before a user is added to the Azure AD group).</span></span>
    
- <span data-ttu-id="f0e07-265">外部ユーザーを、ラベル保護に直接追加します。</span><span class="sxs-lookup"><span data-stu-id="f0e07-265">Add external users directly to the label protection</span></span>
    
     <span data-ttu-id="f0e07-p133">組織 (例: Fabrikam.com) のすべてのユーザー、Azure AD グループ (例: 組織内の財務グループ)、個々のユーザーを追加できます。たとえば、ラベルの保護に、規制機関の外部ユーザーを追加できます。この方法を使用すると、外部エンティティが保護に追加された後にラベルを使用して保護されたファイルにのみ、アクセス許可が付与されます。</span><span class="sxs-lookup"><span data-stu-id="f0e07-p133">You can add all users from an organization (e.g. Fabrikam.com), an Azure AD group (such as a finance group within an organization), or an individual user. For example, you can add an external team of regulators to the protection for a label. With this method, permissions are granted only to files protected with the label after the external entity is added to the protection.</span></span>
    
### <a name="deploying-and-using-azure-information-protection"></a><span data-ttu-id="f0e07-269">Azure Information Protection の展開と使用</span><span class="sxs-lookup"><span data-stu-id="f0e07-269">Deploying and using Azure Information Protection</span></span>

<span data-ttu-id="f0e07-270">このソリューションで Azure Information Protection を構成する手順については、「[Azure Information Protection を使用して SharePoint Online ファイルを保護する](protect-sharepoint-online-files-with-azure-information-protection.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0e07-270">For the steps to configure Azure Information Protection in this solution, see [Protect SharePoint Online files with Azure Information Protection](protect-sharepoint-online-files-with-azure-information-protection.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f0e07-271">See Also</span><span class="sxs-lookup"><span data-stu-id="f0e07-271">See Also</span></span>

[<span data-ttu-id="f0e07-272">選挙運動、非営利組織、およびその他のアジャイル組織のための Microsoft Security ガイダンス</span><span class="sxs-lookup"><span data-stu-id="f0e07-272">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="f0e07-273">セキュリティ ソリューション</span><span class="sxs-lookup"><span data-stu-id="f0e07-273">Security solutions</span></span>](security-solutions.md)
  
[<span data-ttu-id="f0e07-274">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="f0e07-274">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="f0e07-275">開発/テスト環境の SharePoint Online サイトをセキュリティで保護する</span><span class="sxs-lookup"><span data-stu-id="f0e07-275">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)



