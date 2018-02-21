---
title: "分離した SharePoint Online チーム サイトの設計"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 775a4e9e-3135-4a48-b32f-bbdd9f2bd0aa
description: "概要: SharePoint Online の分離のチーム サイトの設計プロセス ステップ"
ms.openlocfilehash: efd55ce780cf2951bfafd31215201459965c0e78
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="design-an-isolated-sharepoint-online-team-site"></a>分離した SharePoint Online チーム サイトの設計

 **の概要:**分離のオンラインの SharePoint チーム サイトの設計プロセスをステップ実行します。
  
この記事では、分離した SharePoint Online チーム サイトを作成する前に行う必要がある設計上の主要な決定事項について説明します。
  
## <a name="phase-1-determine-your-sharepoint-groups-and-permission-levels"></a>フェーズ 1:SharePoint グループおよびアクセス許可レベルを決定します。

既定では、すべての SharePoint Online チーム サイトは次の SharePoint グループを使用して作成されます。
  
- \<サイト名 > のメンバー
    
- \<サイト名 > の訪問者
    
- \<サイト名 > の所有者
    
これらのグループは、Office 365 と Azure Active Directory (AD) のグループとは別であり、サイトのリソースにアクセス許可を割り当てるための基盤になります。
  
SharePoint グループのメンバーがサイトで実行できる内容を決定する特定のアクセス許可のセットが、アクセス許可レベルになります。SharePoint Online チーム サイトでは、既定では次の 3 つのアクセス許可レベルがあります。編集、読み取り、フル コントロールです。次の表は、SharePoint グループと割り当てられるアクセス許可レベルとの既定の相関関係を示しています。
  
|**SharePoint グループ**|**アクセス許可レベル**|
|:-----|:-----|
|\<サイト名 > のメンバー  <br/> |編集  <br/> |
|\<サイト名 > の訪問者  <br/> |読み取り  <br/> |
|\<サイト名 > の所有者  <br/> |フル コントロール  <br/> |
   
 **ベスト プラクティス:**追加の SharePoint グループおよびアクセス許可レベルを作成することができます。ただし、独立した SharePoint Online サイトの既定の SharePoint グループおよびアクセス許可レベルを使用するをお勧めします。
  
既定の SharePoint グループおよびアクセス許可レベルを次に示します。
  
![SharePoint Online サイトの既定の SharePoint グループおよびアクセス許可レベル。](images/3f892ab4-6479-42f0-a505-1ba0ef94b9c6.png)
  
## <a name="phase-2-assign-permissions-to-users-with-access-groups"></a>フェーズ 2:アクセス グループを使用してアクセス許可をユーザーに割り当てる

ユーザー アカウント、またはユーザー アカウントがメンバーである Office 365 グループまたは Azure AD グループを SharePoint グループに追加すると、ユーザーにアクセス許可を割り当てることができます。直接的に、または Office 365 グループか Azure AD グループのメンバーシップを通して間接的に追加されると、Office 365 ユーザー アカウントには、SharePoint グループに関連付けられているアクセス許可レベルが割り当てられます。
  
既定の SharePoint グループを使用した例:
  
- メンバー、**\<サイト名 > のメンバー** **の編集**のアクセス許可レベルを割り当てられた SharePoint グループは、ユーザー アカウントとグループの両方を含めることができます、
    
- メンバー、**\<サイト名 > の訪問者**SharePoint グループは、ユーザー アカウントとグループの両方を含めることができます、**読み取り**のアクセス許可レベルを割り当てられました。
    
- メンバー、**\<サイト名 > の所有者**SharePoint グループは、ユーザー アカウントとグループの両方を含めることができます、**フル コントロール**アクセス許可レベルを割り当てられました。
    
 **ベスト プラクティス:**1 つを使用することをお勧めの個々 のユーザー アカウントのアクセス許可を管理できますが、Azure AD グループ、代わりに、アクセス グループとして知られています。各 SharePoint グループにアカウントのユーザーのリストを管理するのではなく、アクセス グループのメンバーシップを介してアクセス許可の管理が簡略化されます。
  
Office 365 の azure の AD グループは、Office 365 のグループとは異なります。Azure AD グループは、**セキュリティ**の**種類**のセットを使用して Office の管理センターに表示され、電子メール アドレスがありません。Azure AD グループ内で管理できます。
  
- Windows Server Active Directory (AD)
    
    これらは、オンプレミス AD の Windows サーバー インフラストラクチャで作成され、Office 365 サブスクリプションを同期するグループです。Office 管理センターは、これらのグループは、 **active directory と Synched**の**状態**を持ちます。
    
- Office 365
    
    これらは、Office の管理センター、Azure ポータル、またはマイクロソフトの PowerShell を使用して作成されているグループです。Office 管理センターでは、これらのグループは、**クラウド**の**ステータス**を持ちます。
    
 **ベスト プラクティス:**AD の Windows サーバーの設置型を使用して、Office 365 サブスクリプションと同期している場合、ユーザーと Windows サーバーの AD とグループの管理を実行します。
  
分離した SharePoint Online チーム サイトの場合、推奨されるグループ構造は次のようになります。
  
|**SharePoint グループ**|**Azure AD ベースのアクセス グループ**|**アクセス許可レベル**|
|:-----|:-----|:-----|
|\<サイト名 > のメンバー  <br/> |\<サイト名 > のメンバー  <br/> |編集  <br/> |
|\<サイト名 > の訪問者  <br/> |\<サイト名 > の閲覧者  <br/> |読み取り  <br/> |
|\<サイト名 > の所有者  <br/> |\<サイト名 > 管理者  <br/> |フル コントロール  <br/> |
   
 **ベスト プラクティス:**Office 365 または Azure AD のいずれかのグループは、SharePoint グループのメンバーとして使用できますが、Azure AD グループを使用することをお勧めします。Azure の AD グループは、Windows サーバーの AD または、Office 365 の管理では、ネストされたグループを使用して、アクセス許可を割り当てるには高い柔軟性を提供します。
  
ここでは、既定の SharePoint グループの Azure AD ベースのアクセス グループを使用するように構成します。
  
![既定の SharePoint Online サイト グループのメンバーとしてアクセス グループを使用する。](images/50a76328-ae69-483e-9029-ac4e7357b5ef.png)
  
3 つのアクセス グループを設計するときは、以下の点にご注意ください。
  
- 内のいくつかのメンバーのみが存在する必要があります、**\<サイト名 > 管理者**アクセス グループ、チーム サイトの管理は、SharePoint Online の管理者の数が少ないに対応します。
    
- サイトのメンバーのほとんど、**\<サイト名 > のメンバー**または**\<サイト名 > ビューアー**グループにアクセスします。サイト内のメンバー、**\<サイト名 > のメンバー**アクセス グループが削除、またはサイト内のリソースを変更、そのメンバーシップを慎重に検討することにあります。判断に迷う場合、サイト メンバーの追加、**\<サイト名 > の閲覧者**アクセス グループ。
    
ここでは、SharePoint グループおよび ProjectX という名前の独立したサイトのアクセス グループの例です。
  
![ProjectX という名前の SharePoint Online サイトのアクセス グループを使用する場合の例。](images/13afe542-9ffd-4671-9f48-210a0e2a502a.png)
  
## <a name="phase-3-use-nested-azure-ad-groups"></a>フェーズ 3: ネストされた Azure AD グループを使用する

少数のユーザーに限定されるプロジェクトの場合、ほとんどのシナリオはサイトの SharePoint グループに追加される単一レベルの Azure AD ベースのアクセス グループに収まります。ただし、多数のユーザーがおり、それらのユーザーが既に確立された Azure AD グループのメンバーである場合、ネストされたグループ、つまり他のグループがメンバーとして含まれるグループを使用することで簡単に SharePoint アクセス許可を割り当てることができます。
  
たとえば、営業部門、マーケティング部門、エンジニアリング部門、法律部門の役員間でコラボレーションするための分離した SharePoint Online チーム サイトを作成したいと考えており、それらの部門には既に役員のユーザー アカウントのメンバーシップを持つ独自のグループが存在するとします。この場合、新しいサイト メンバー用に新しいグループを作成して、それぞれの役員ユーザー アカウントをすべてそこに含めるのではなく、各部門の既存の役員グループを新しいグループに入れます。
  
  複数の組織間で 1 つの Office 365 サブスクリプションを共有している場合、1 つの組織の 1 つの分離したサイトに単一レベルのグループ メンバーシップが存在することになり、膨大な数のユーザー アカウントを処理しなければならないため、管理が難しくなる可能性があります。この場合、組織内のグループが含まれるネストされた Azure AD グループを組織ごとに使用して、アクセス許可を管理することができます。
  
ネストされた Azure AD グループを使用するには、以下を実行します。
  
1. ユーザー アカウントを含める Azure AD グループを特定するか作成し、適切なユーザー アカウントをメンバーとして追加します。
    
2. 他の Azure AD グループを含めるコンテナーとなる Azure AD ベースのアクセス グループを作成し、それらのグループをメンバーとして追加します。
    
3.   コンテナー アクセス グループの適切なアクセス レベルについては、SharePoint グループと、対応するアクセス許可レベルを識別します。
    
> [!NOTE]
> ネストされた Office 365 グループを使用することはできません。 
  
ProjectX メンバー アクセス グループのグループの入れ子になった Azure AD の例を次のとおりです。
  
![ProjectX サイトのメンバー アクセス グループの入れ子になったアクセス グループを使用する場合の例。](images/2abca710-bf9e-4ce8-9bcd-a8e128264fb1.png)
  
研究、エンジニア リング、およびプロジェクト内のユーザー アカウントのすべての潜在顧客のため、チーム サイトのメンバーにするものでは、ProjectX のメンバーのアクセス グループに、Azure AD グループを追加する方が簡単です。
  
## <a name="next-step"></a>次の手順

作成し、運用環境で分離されたサイトを構成する準備ができたら、 [SharePoint Online の分離のチーム サイトの展開](deploy-an-isolated-sharepoint-online-team-site.md)を参照してください。
  
## <a name="see-also"></a>関連項目

[分離した SharePoint Online チーム サイト](isolated-sharepoint-online-team-sites.md)
  
[分離した SharePoint Online チーム サイトの管理](manage-an-isolated-sharepoint-online-team-site.md)
  
[セキュリティ ソリューション](security-solutions.md)

[分離した SharePoint Online チーム サイトの展開](deploy-an-isolated-sharepoint-online-team-site.md)



