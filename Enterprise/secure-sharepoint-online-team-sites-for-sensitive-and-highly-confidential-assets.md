---
title: "センシティブなアセットや機密性の高いアセット用のセキュアな SharePoint Online チームサイト"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 8c088e88-a9ba-4044-bced-722196f4496d
description: "概要: ここでは、幹部や研究所が簡単かつセキュアにコラボレーションできるようにするために、Contoso 社がセンシティブな情報の保護と、機密性の高い SharePoint Online チーム サイトをどのように構築したかを説明します。"
ms.openlocfilehash: 1574babb54bfcb3fd74fb8ce4f31c364bb96b14a
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="secure-sharepoint-online-team-sites-for-sensitive-and-highly-confidential-assets"></a><span data-ttu-id="a5509-103">センシティブなアセットや機密性の高いアセット用のセキュアな SharePoint Online チームサイト</span><span class="sxs-lookup"><span data-stu-id="a5509-103">Secure SharePoint Online team sites for sensitive and highly confidential assets</span></span>

 <span data-ttu-id="a5509-104">**概要:** ここでは、幹部や研究所が簡単かつセキュアにコラボレーションできるようにするために、Contoso 社がセンシティブな情報の保護と、機密性の高い SharePoint Online チーム サイトをどのように構築したかを説明します。</span><span class="sxs-lookup"><span data-stu-id="a5509-104">**Summary:** How Contoso implemented sensitive protection and highly confidential SharePoint Online team sites for easier, yet secure, collaboration for executives and its research centers..</span></span>
  
<span data-ttu-id="a5509-p101">Contoso 社の経営幹部は、居場所に関係なく共同作業を行うために、Office 365 を使ってファイルを 1 か所にまとめて保存したいと考えていました。同様に、パリ、モスクワ、ニューヨーク、北京とバンガロールにも拠点がある Contoso 社の研究部門も、オンプレミスのデジタル アセットをクラウドに移行することで、アセットに容易にアクセスし、チーム間のオープン コラボレーションを推進したいと考えていました。</span><span class="sxs-lookup"><span data-stu-id="a5509-p101">The executive leadership of Contoso want to use Office 365 and store their files in a single location for collaboration, regardless of where an executive might be. Similarly, Contoso's research departments—with divisions in Paris, Moscow, New York, Beijing, and Bangalore—would like to transition their on-premises digital assets to the cloud for easier access and more open collaboration across teams.</span></span>
  
<span data-ttu-id="a5509-p102">しかし、いずれのケースでも、これらのリソースへのアクセスは、閲覧あるいは編集の権限を与えられた一定の人々に限定するとともに、IT スタッフが管理するサイトにおいて継続的にアクセス許可を設定する必要がありました。 また、リソースが意図的あるいは非意図的に配布されたとしても必ず暗号化し、アクセス許可を設定することで、権限を持っていない人々がコンテンツを閲覧あるいは編集できないようにする必要がありました。</span><span class="sxs-lookup"><span data-stu-id="a5509-p102">However, in both of these cases, access to these resources must be restricted to the subset of people who are allowed to view or change them, with ongoing permissions for the site administered by IT staff. Additionally, even if some resources are intentionally or unintentionally distributed, they must be encrypted and have permissions to prevent those who do not have access to view or change their contents.</span></span>
  
<span data-ttu-id="a5509-109">そこで、Contoso 社の IT 部門のセキュリティおよび SharePoint の管理者は、図 1 のように、センシティブな情報の保護と機密性の高い SharePoint Online チーム サイトを使用することにしました。</span><span class="sxs-lookup"><span data-stu-id="a5509-109">Security and SharePoint administrators in Contoso's IT department decided to use sensitive protection and highly-confidential SharePoint Online team sites, as shown in Figure 1.</span></span>
  
<span data-ttu-id="a5509-110">**図 1:センシティブな情報の保護と機密性の高い SharePoint Online チーム サイトの比較**</span><span class="sxs-lookup"><span data-stu-id="a5509-110">**Figure 1: Comparison of sensitive protection and highly confidential SharePoint Online team sites**</span></span>

![機密保護および高機密 SharePoint Online チーム サイト](images/Contoso_Poster/SP_Solution.png)
  
<span data-ttu-id="a5509-112">Contoso 社は次のようなステップで、経営幹部および研究チーム用にセキュアな SharePoint Online のチーム サイトを作成しました。</span><span class="sxs-lookup"><span data-stu-id="a5509-112">Contoso used these steps to create secure SharePoint Online team sites for their executives and research teams:</span></span>
  
1. <span data-ttu-id="a5509-113">**経営幹部** のセンシティブ情報を保護するための SharePoint Online チーム サイトを作成する</span><span class="sxs-lookup"><span data-stu-id="a5509-113">Create an **Executives** sensitive SharePoint Online team site</span></span>
    
    <span data-ttu-id="a5509-114">この新しいチーム サイトでは、既存の Azure Active Directory (AD) グループを使い、経営幹部をメンバーとして SharePoint アクセス許可レベルを「編集」に設定し、一部のメンバーを「所有者」としてフルコントロールのアクセス許可レベルを設定した SharePoint Administrator アカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="a5509-114">The new team site uses existing Azure Active Directory (AD) groups for executives as members with the Edit SharePoint permission level and a small set of SharePoint administrator accounts as owners with the Full Control permission level.</span></span>
    
2. <span data-ttu-id="a5509-115">経営幹部のファイルを移行する</span><span class="sxs-lookup"><span data-stu-id="a5509-115">Migrate executives files</span></span>
    
    <span data-ttu-id="a5509-116">既存のオンプレミスの経営幹部のファイルとフォルダーを新しい Executives SharePoint Online チーム サイトに移動します。</span><span class="sxs-lookup"><span data-stu-id="a5509-116">Move existing on-premises executive files and folders to the new Executives SharePoint Online team site.</span></span>
    
3. <span data-ttu-id="a5509-117">**研究所** の機密性の高い SharePoint Online チーム サイトを作成する</span><span class="sxs-lookup"><span data-stu-id="a5509-117">Create a **Research** highly confidential SharePoint Online team site</span></span>
    
    <span data-ttu-id="a5509-p103">この新しいチーム サイトでは、既存の Azure AD 研究チーム グループをメンバーとしてアクセス許可レベルを「編集」に設定し、一部のメンバーを「所有者」としてフルコントロールのアクセス許可レベルを設定した SharePoint Administrator アカウントを作成します。研究所ファイルに割り当てられる AIP ラベルにより、これらのファイルは暗号化され、研究グループのメンバーのみが開くことができます。</span><span class="sxs-lookup"><span data-stu-id="a5509-p103">The new team site uses existing Azure AD research team groups as members with the Edit permission level and a small set of SharePoint administrator accounts as owners with the Full Control permission level. An AIP label assigned to research files ensures that they are encrypted and only members of a research group can open them.</span></span>
    
4. <span data-ttu-id="a5509-120">研究所ファイルを移行する</span><span class="sxs-lookup"><span data-stu-id="a5509-120">Migrate research files</span></span>
    
    <span data-ttu-id="a5509-121">既存のオンプレミスの研究チーム ファイルとフォルダーを新しい Research SharePoint Online チーム サイトに移動します。</span><span class="sxs-lookup"><span data-stu-id="a5509-121">Move existing research team on-premises files and folders to the new Research SharePoint Online team site.</span></span>
    
<span data-ttu-id="a5509-p104">最終的に、セキュリティと SharePoint 管理者によってアクセスが厳密に管理される 2 つのコラボレーション サイトが作成されます。高機密 AIP ラベルの付いたファイルは、Research チーム サイト外に配布されたとしても暗号化されているため、研究チームのメンバー以外は開くことができません。</span><span class="sxs-lookup"><span data-stu-id="a5509-p104">The result is two collaboration sites whose access is tightly controlled by security and SharePoint administrators. For files with the Highly Confidential AIP label, even if they are distributed outside the Research team site, they are encrypted and can only be opened by a member of a research team.</span></span>
  
<span data-ttu-id="a5509-124">詳細については、[セキュアな SharePoint Online サイトとファイル]((https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-and-files))を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5509-124">For more information, see [Secure SharePoint Online sites and files]((https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-and-files)).</span></span>
  
 <span data-ttu-id="a5509-125">デモや概念実証、開発/テストのために設定する場合は、[開発/テスト環境でのセキュアな SharePoint Online サイト]((https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-dev-test))を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5509-125">To set this up for demonstration, proof-of-concept, or dev/test, see[Secure SharePoint Online sites in a dev/test environment]((https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-dev-test)).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a5509-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="a5509-126">See Also</span></span>

[<span data-ttu-id="a5509-127">Contoso Corporation のエンタープライズのシナリオ</span><span class="sxs-lookup"><span data-stu-id="a5509-127">Enterprise scenarios for the Contoso Corporation</span></span>](enterprise-scenarios-for-the-contoso-corporation.md)
  
[<span data-ttu-id="a5509-128">Microsoft Cloud の Contoso</span><span class="sxs-lookup"><span data-stu-id="a5509-128">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="a5509-129">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="a5509-129">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

<span data-ttu-id="a5509-130">[Stretch Database]((https://msdn.microsoft.com/library/dn935011.aspx))</span><span class="sxs-lookup"><span data-stu-id="a5509-130">[Stretch Database]((https://msdn.microsoft.com/library/dn935011.aspx))</span></span>
  
<span data-ttu-id="a5509-131">[Microsoft の Enterprise Cloud ロードマップ:IT の意思決定者向けのリソース]((https://sway.com/FJ2xsyWtkJc2taRD))</span><span class="sxs-lookup"><span data-stu-id="a5509-131">[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers]((https://sway.com/FJ2xsyWtkJc2taRD))</span></span>




