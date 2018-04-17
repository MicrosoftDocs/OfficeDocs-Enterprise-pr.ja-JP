---
title: OneDrive の複数地域機能および Office 365 の SharePoint Online
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: Expand your Office 365 presence to multiple geographic regions with multi-geo capabilities in OneDrive and SharePoint Online.
ms.openlocfilehash: 3f72158fe05aadfe8a08a5520bf65cd2d0aaa1c6
ms.sourcegitcommit: a81d08c7e8771cb2c232435971e3169d4f7428dc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365"></a>OneDrive の複数地域機能および Office 365 の SharePoint Online

With multi-geo capabilities in OneDrive and SharePoint Online, your organization can expand its Office 365 presence to multiple geographic regions and/or countries within your existing tenant. Reach out to your Microsoft Account Team to sign up your Multi-National Company for OneDrive for Business Multi-Geo.
  
With OneDrive Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.
  
Here's how multi-geo features can benefit your organization:
  
- 複数の地理的な場所にわたる単一の Office 365 テナントで、1 つのグローバルに接続された組織として事業活動を行う。
    
- 指定した地理的な場所内で保存データを作成してホストすることによって、データの常駐に関連する要件を満たす。
    
- 中央の場所のユーザーが恩恵を受けているモダンな生産性向上エクスペリエンスと同じエクスペリエンスをサテライトのユーザーに提供する。
    
- ユーザーのロールが変更された場合に、そのユーザーのコンテンツへのアクセスをそのまま維持した状態で、ユーザーが地理的な場所を超えて移動することを可能にする。
    
- 地理的な場所ごとのポリシーと、サイトごとのデータ損失防止ポリシーの共有を調整する。
    
- 地理的な場所ごとに電子情報開示マネージャー (管理者) を指定し、自分の地理的な場所に合わせた問題に適用される原則を許可する。
    
- 追加の地理的な場所に対して固有の URL 名前空間 (たとえば、ContosoEUR.sharepoint.com) を選択する。
    
- 地域のオンプレミス データを Office 365 の複数地域テナントに統合する。
    
In a multi-geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. The key concept of multi-geo is that a single tenancy will span across one multiple geo locations. In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD). Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.
  
## <a name="sample-multi-geo-tenant-configuration"></a>Sample multi-geo tenant configuration

北アメリカに中央拠点がある Contoso は、複数地域テナントを使用して、Contoso.com という単一組織の傘下のヨーロッパおよびオーストラリアにあるサテライトの地理的な場所に展開することができます。自分の優先されるデータの場所がヨーロッパに設定されているユーザーはヨーロッパに自分の OneDrive を保持している一方、自分の優先されるデータの場所が北アメリカにあるユーザーは米国に自分の OneDrive を保持しています。
  
![Map of the world, showing geo locations for Contoso and other available geo locations](images/df317ccc-2e53-411d-9211-a5aee63ca1e5.png)
  
## <a name="get-multi-geo-features-in-three-simple-steps"></a>3 つの簡単な手順で複数地域機能を入手する

複数地域の構成は次のように簡単です。
  
1. Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan. They will guide you to add the number of licenses needed.
    
2. サテライトの場所を追加します。
    
3. 該当する場所用のユーザー アカウントを構成します。
    
## <a name="multi-geo-status-and-availability"></a>複数地域の状態と可用性

OneDrive の複数地域は、現在次の地域と国で提供されています。
  
- アジア太平洋
    
- オーストラリア
    
- カナダ
    
- 欧州連合 (EMEA)
    
- 日本
    
- 英国
    
- 米国 (北アメリカ)
    
- 韓国
      
今後提供予定の地理的な場所:
  
- フランス
- インド
    
## <a name="getting-started"></a>はじめに

To get started with OneDrive for Business Multi-Geo, the first step is to [plan your OneDrive for Business Multi-Geo environment](plan-for-multi-geo.md). Next, [learn about administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience a multi-geo environment](multi-geo-user-experience.md). When you are ready to set up OneDrive for Business Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md), then [move any existing OneDrive sites to thier new geo-locations](move-onedrive-between-geo-locations.md) and [set up search](configure-search-for-multi-geo.md).
