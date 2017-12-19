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
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 71250a04-fd2d-4c3c-a32b-b8a838b19a54
description: "概要: 分離した SharePoint Online チーム サイトの使用方法について説明します。"
ms.openlocfilehash: 3de60bb19498d9f84c18e51181a3fedda9846bdf
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="isolated-sharepoint-online-team-sites"></a>分離した SharePoint Online チーム サイト

 **概要:** 分離した SharePoint Online チーム サイトの使用方法について説明します。
  
SharePoint Online チーム サイトは、Microsoft Office 365 のノート、ドキュメント、記事、予定表、およびその他のリソースのコラボレーション用のスペースを素早く作成する簡単な方法です。SharePoint Online チーム サイトは、Office 365 グループをベースとしており、グループ メンバーや組織全体の非公開セットを使用したオープンなコラボレーションを可能にする簡略化された管理モデルを備えています。既定の SharePoint Online チーム サイトでは、Office 365 のグループのメンバーが他のユーザーを招待し、アクセス許可の設定を制御することが可能です。
  
しかし、コラボレーション用の SharePoint Online チーム サイトを作成し、グループのメンバーシップや SharePoint Online のアクセス許可レベルという SharePoint 管理者しか管理できない手段を通して、サイトのアクセス許可をより厳しく制御する必要が生じる場合もあります。これは、分離したサイトと呼ばれ、コラボレーション、コンテンツの表示、またはサイトの管理を実行するユーザーのセットに分離されています。以下を対象として、分離したサイトが必要になることがあります。
  
- 組織内での機密プロジェクト。
    
- 組織にとって機密度が高い、または知的財産となる場所。
    
- 組織によって実施された、または現在遵守されている法的措置のリソース。
    
- 一部が重複する複数の組織間で Office 365 サブスクリプションを共有するものの、ほとんどの部分は個別のビジネス エンティティとして存在する場合。
    
分離したサイトの要件を以下に示します。
  
- SharePoint Online 管理者だけが、サイトの管理を実行できます。これには、サイトにアクセスし、カスタム アクセス許可を構成するためのグループ メンバーシップが含まれます。
    
- サイトのメンバーは、他のメンバーをチーム サイトに招待することはできません。
    
- 分離したサイトのメンバーではないユーザーは、サイトへのアクセスを要求できません。サイトに関連付けられているいずれかの URL にアクセスしようとすると、アクセスが拒否された Web ページが表示されます。
    
一元的なアクセス制御を必要とすることと SharePoint Online 管理者によるカスタム アクセス許可とのトレードオフは、時間が経過してもサイトが分離されたままであるということです。たとえば、現在のメンバーは、意図的であれ偶然であれ、サイトのメンバーではない Office 365 サブスクリプション内の他のユーザーを招待したり、他のユーザーのためにカスタムのアクセス許可を構成したりすることはできません。
  
分離したサイトは次のようにその他の機能と一緒に使用できます。
  
- Information Rights Management。ローカルにダウンロードしたり、組織全体で利用可能な別のサイトにアップロードしたりする場合でも、サイト上のリソースを暗号化されたままにします。
    
- データ損失防止。ユーザーがファイルなどのサイトのリソースを電子メールで送信できないようにします。
    
## <a name="next-steps"></a>次の手順

SharePoint Online チーム サイトを試用サブスクリプションで使用するには、「[Office 365 開発/テスト環境での分離した SharePoint Online チーム サイト](isolated-sharepoint-online-team-site-dev-test-environment.md)」にあるステップごとの指示を参照してください。
  
分離した SharePoint Online チーム サイトを実稼働に展開する準備ができたら、「[分離した SharePoint Online チーム サイトの設計](design-an-isolated-sharepoint-online-team-site.md)」にある設計に関するステップバイステップの考慮事項を参照してください。
  
## <a name="see-also"></a>関連項目

[分離した SharePoint Online チーム サイトの設計](design-an-isolated-sharepoint-online-team-site.md)
  
[分離した SharePoint Online チーム サイトの管理](manage-an-isolated-sharepoint-online-team-site.md)
  
[セキュリティ ソリューション](security-solutions.md)

[分離した SharePoint Online チーム サイトの展開](deploy-an-isolated-sharepoint-online-team-site.md)


