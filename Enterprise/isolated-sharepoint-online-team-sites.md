---
title: "分離した SharePoint Online チーム サイト"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 71250a04-fd2d-4c3c-a32b-b8a838b19a54
description: "概要: 分離した SharePoint Online チーム サイトの使用方法について説明します。"
ms.openlocfilehash: 907959e1ad693e710a2a84d0bd0ffd0804ac3ddf
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="isolated-sharepoint-online-team-sites"></a><span data-ttu-id="bdd4f-103">分離した SharePoint Online チーム サイト</span><span class="sxs-lookup"><span data-stu-id="bdd4f-103">Isolated SharePoint Online team sites</span></span>

 <span data-ttu-id="bdd4f-104">**概要:** 分離した SharePoint Online チーム サイトの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bdd4f-104">**Summary:** Learn about the uses for isolated SharePoint Online team sites.</span></span>
  
<span data-ttu-id="bdd4f-p101">SharePoint Online チーム サイトは、Microsoft Office 365 のノート、ドキュメント、記事、予定表、およびその他のリソースのコラボレーション用のスペースを素早く作成する簡単な方法です。SharePoint Online チーム サイトは、Office 365 グループをベースとしており、グループ メンバーや組織全体の非公開セットを使用したオープンなコラボレーションを可能にする簡略化された管理モデルを備えています。既定の SharePoint Online チーム サイトでは、Office 365 のグループのメンバーが他のユーザーを招待し、アクセス許可の設定を制御することが可能です。</span><span class="sxs-lookup"><span data-stu-id="bdd4f-p101">SharePoint Online team sites are an easy way to quickly create a space for collaboration of notes, documents, articles, a calendar, and other resources in Microsoft Office 365. SharePoint Online team sites are based on an Office 365 group and have a simplified administration model to allow open collaboration with a private set of group members or the entire organization. A default SharePoint Online team site allows members of the Office 365 group to invite other users and control permissions settings.</span></span>
  
<span data-ttu-id="bdd4f-p102">しかし、コラボレーション用の SharePoint Online チーム サイトを作成し、グループのメンバーシップや SharePoint Online のアクセス許可レベルという SharePoint 管理者しか管理できない手段を通して、サイトのアクセス許可をより厳しく制御する必要が生じる場合もあります。これは、分離したサイトと呼ばれ、コラボレーション、コンテンツの表示、またはサイトの管理を実行するユーザーのセットに分離されています。以下を対象として、分離したサイトが必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="bdd4f-p102">However, in some cases, you want to create a SharePoint Online team site for collaboration where the permissions of that site are more tightly controlled through group membership and SharePoint Online permission levels, which are only managed by SharePoint administrators. We call this an isolated site, which is isolated to the set of users that are either collaborating, viewing its contents, or administering the site. You might need an isolated site for the following:</span></span>
  
- <span data-ttu-id="bdd4f-111">組織内での機密プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="bdd4f-111">A secret project within your organization.</span></span>
    
- <span data-ttu-id="bdd4f-112">組織にとって機密度が高い、または知的財産となる場所。</span><span class="sxs-lookup"><span data-stu-id="bdd4f-112">The location for highly-sensitive or valuable intellectual property for your organization.</span></span>
    
- <span data-ttu-id="bdd4f-113">組織によって実施された、または現在遵守されている法的措置のリソース。</span><span class="sxs-lookup"><span data-stu-id="bdd4f-113">The resources for a legal action taken by your organization or that to which it is being subjected.</span></span>
    
- <span data-ttu-id="bdd4f-114">一部が重複する複数の組織間で Office 365 サブスクリプションを共有するものの、ほとんどの部分は個別のビジネス エンティティとして存在する場合。</span><span class="sxs-lookup"><span data-stu-id="bdd4f-114">To share an Office 365 subscription between multiple organizations that have some overlap, but for the most part exist as separate business entities.</span></span>
    
<span data-ttu-id="bdd4f-115">分離したサイトの要件を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="bdd4f-115">Here are the requirements of an isolated site:</span></span>
  
- <span data-ttu-id="bdd4f-116">SharePoint Online 管理者だけが、サイトの管理を実行できます。これには、サイトにアクセスし、カスタム アクセス許可を構成するためのグループ メンバーシップが含まれます。</span><span class="sxs-lookup"><span data-stu-id="bdd4f-116">Only SharePoint Online administrators can perform site administration, which includes group membership for access to the site and configuring custom permissions.</span></span>
    
- <span data-ttu-id="bdd4f-117">サイトのメンバーは、他のメンバーをチーム サイトに招待することはできません。</span><span class="sxs-lookup"><span data-stu-id="bdd4f-117">Members of the site cannot invite other members to the team site.</span></span>
    
- <span data-ttu-id="bdd4f-p103">分離したサイトのメンバーではないユーザーは、サイトへのアクセスを要求できません。サイトに関連付けられているいずれかの URL にアクセスしようとすると、アクセスが拒否された Web ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bdd4f-p103">Users who are not members of the isolated site cannot request access to the site. They will receive an access denied web page when they attempt to access any URL associated with the site.</span></span>
    
<span data-ttu-id="bdd4f-p104">一元的なアクセス制御を必要とすることと SharePoint Online 管理者によるカスタム アクセス許可とのトレードオフは、時間が経過してもサイトが分離されたままであるということです。たとえば、現在のメンバーは、意図的であれ偶然であれ、サイトのメンバーではない Office 365 サブスクリプション内の他のユーザーを招待したり、他のユーザーのためにカスタムのアクセス許可を構成したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="bdd4f-p104">The tradeoff of requiring centralized access control and custom permissions by SharePoint Online administrators is that the site remains isolated over time. For example, current members cannot, either intentionally or accidentally, invite or configure custom permissions for other users within the Office 365 subscription who should not be members of the site.</span></span>
  
<span data-ttu-id="bdd4f-122">分離したサイトは次のようにその他の機能と一緒に使用できます。</span><span class="sxs-lookup"><span data-stu-id="bdd4f-122">An isolated site can be used with other features, such as:</span></span>
  
- <span data-ttu-id="bdd4f-123">Information Rights Management。ローカルにダウンロードしたり、組織全体で利用可能な別のサイトにアップロードしたりする場合でも、サイト上のリソースを暗号化されたままにします。</span><span class="sxs-lookup"><span data-stu-id="bdd4f-123">Information Rights Management to ensure that the resources on the site remain encrypted, even if they are downloaded locally and uploaded to another site that is available to the entire organization.</span></span>
    
- <span data-ttu-id="bdd4f-124">データ損失防止。ユーザーがファイルなどのサイトのリソースを電子メールで送信できないようにします。</span><span class="sxs-lookup"><span data-stu-id="bdd4f-124">Data loss prevention to prevent users from sending the resources of the site, such as files, in email.</span></span>
    
## <a name="next-steps"></a><span data-ttu-id="bdd4f-125">次の手順</span><span class="sxs-lookup"><span data-stu-id="bdd4f-125">Next steps</span></span>

<span data-ttu-id="bdd4f-126">SharePoint Online チーム サイトを試用サブスクリプションで使用するには、「[Office 365 開発/テスト環境での分離した SharePoint Online チーム サイト](isolated-sharepoint-online-team-site-dev-test-environment.md)」にあるステップごとの指示を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdd4f-126">To try out an isolated SharePoint Online team site in a trial subscription, see the step-by-step instructions in [Isolated SharePoint Online team site dev/test environment](isolated-sharepoint-online-team-site-dev-test-environment.md).</span></span>
  
<span data-ttu-id="bdd4f-127">分離した SharePoint Online チーム サイトを実稼働に展開する準備ができたら、「[分離した SharePoint Online チーム サイトの設計](design-an-isolated-sharepoint-online-team-site.md)」にある設計に関するステップバイステップの考慮事項を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdd4f-127">When you are ready to deploy an isolated SharePoint Online team site in production, see the step-by-step design considerations in [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bdd4f-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="bdd4f-128">See Also</span></span>

[<span data-ttu-id="bdd4f-129">分離した SharePoint Online チーム サイトの設計</span><span class="sxs-lookup"><span data-stu-id="bdd4f-129">Design an isolated SharePoint Online team site</span></span>](design-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="bdd4f-130">分離した SharePoint Online チーム サイトの管理</span><span class="sxs-lookup"><span data-stu-id="bdd4f-130">Manage an isolated SharePoint Online team site</span></span>](manage-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="bdd4f-131">セキュリティ ソリューション</span><span class="sxs-lookup"><span data-stu-id="bdd4f-131">Security solutions</span></span>](security-solutions.md)

[<span data-ttu-id="bdd4f-132">分離した SharePoint Online チーム サイトの展開</span><span class="sxs-lookup"><span data-stu-id="bdd4f-132">Deploy an isolated SharePoint Online team site</span></span>](deploy-an-isolated-sharepoint-online-team-site.md)


