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
# <a name="secure-sharepoint-online-team-sites-for-sensitive-and-highly-confidential-assets"></a>センシティブなアセットや機密性の高いアセット用のセキュアな SharePoint Online チームサイト

 **概要:** ここでは、幹部や研究所が簡単かつセキュアにコラボレーションできるようにするために、Contoso 社がセンシティブな情報の保護と、機密性の高い SharePoint Online チーム サイトをどのように構築したかを説明します。
  
Contoso 社の経営幹部は、居場所に関係なく共同作業を行うために、Office 365 を使ってファイルを 1 か所にまとめて保存したいと考えていました。同様に、パリ、モスクワ、ニューヨーク、北京とバンガロールにも拠点がある Contoso 社の研究部門も、オンプレミスのデジタル アセットをクラウドに移行することで、アセットに容易にアクセスし、チーム間のオープン コラボレーションを推進したいと考えていました。
  
しかし、いずれのケースでも、これらのリソースへのアクセスは、閲覧あるいは編集の権限を与えられた一定の人々に限定するとともに、IT スタッフが管理するサイトにおいて継続的にアクセス許可を設定する必要がありました。 また、リソースが意図的あるいは非意図的に配布されたとしても必ず暗号化し、アクセス許可を設定することで、権限を持っていない人々がコンテンツを閲覧あるいは編集できないようにする必要がありました。
  
そこで、Contoso 社の IT 部門のセキュリティおよび SharePoint の管理者は、図 1 のように、センシティブな情報の保護と機密性の高い SharePoint Online チーム サイトを使用することにしました。
  
**図 1:センシティブな情報の保護と機密性の高い SharePoint Online チーム サイトの比較**

![機密保護および高機密 SharePoint Online チーム サイト](images/Contoso_Poster/SP_Solution.png)
  
Contoso 社は次のようなステップで、経営幹部および研究チーム用にセキュアな SharePoint Online のチーム サイトを作成しました。
  
1. **経営幹部** のセンシティブ情報を保護するための SharePoint Online チーム サイトを作成する
    
    この新しいチーム サイトでは、既存の Azure Active Directory (AD) グループを使い、経営幹部をメンバーとして SharePoint アクセス許可レベルを「編集」に設定し、一部のメンバーを「所有者」としてフルコントロールのアクセス許可レベルを設定した SharePoint Administrator アカウントを作成します。
    
2. 経営幹部のファイルを移行する
    
    既存のオンプレミスの経営幹部のファイルとフォルダーを新しい Executives SharePoint Online チーム サイトに移動します。
    
3. **研究所** の機密性の高い SharePoint Online チーム サイトを作成する
    
    この新しいチーム サイトでは、既存の Azure AD 研究チーム グループをメンバーとしてアクセス許可レベルを「編集」に設定し、一部のメンバーを「所有者」としてフルコントロールのアクセス許可レベルを設定した SharePoint Administrator アカウントを作成します。研究所ファイルに割り当てられる AIP ラベルにより、これらのファイルは暗号化され、研究グループのメンバーのみが開くことができます。
    
4. 研究所ファイルを移行する
    
    既存のオンプレミスの研究チーム ファイルとフォルダーを新しい Research SharePoint Online チーム サイトに移動します。
    
最終的に、セキュリティと SharePoint 管理者によってアクセスが厳密に管理される 2 つのコラボレーション サイトが作成されます。高機密 AIP ラベルの付いたファイルは、Research チーム サイト外に配布されたとしても暗号化されているため、研究チームのメンバー以外は開くことができません。
  
詳細については、[セキュアな SharePoint Online サイトとファイル]((https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-and-files))を参照してください。
  
 デモや概念実証、開発/テストのために設定する場合は、[開発/テスト環境でのセキュアな SharePoint Online サイト]((https://docs.microsoft.com/microsoft-365-enterprise/secure-sharepoint-online-sites-dev-test))を参照してください。
  
## <a name="see-also"></a>関連項目

[Contoso Corporation のエンタープライズのシナリオ](enterprise-scenarios-for-the-contoso-corporation.md)
  
[Microsoft Cloud の Contoso](contoso-in-the-microsoft-cloud.md)
  
[Microsoft クラウド IT アーキテクチャのリソース](microsoft-cloud-it-architecture-resources.md)

[Stretch Database]((https://msdn.microsoft.com/library/dn935011.aspx))
  
[Microsoft の Enterprise Cloud ロードマップ:IT の意思決定者向けのリソース]((https://sway.com/FJ2xsyWtkJc2taRD))




