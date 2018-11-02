---
title: OneDrive の複数地域機能および Office 365 の SharePoint Online
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: OneDrive と SharePoint Online の複数地域機能を使用して、複数の地域に Office 365 のプレゼンスを展開します。
ms.openlocfilehash: 725a7a88e3459f73ff00554b14afc740db1244b3
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849823"
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365"></a>OneDrive の複数地域機能および Office 365 の SharePoint Online

OneDrive の複数地域機能と SharePoint Online を使用すれば、組織はその組織の Office 365 のプレゼンスを、その既存のテナント内の複数の地域または国に対して展開することができます。お客様の Microsoft アカウント チームと連絡を取って、OneDrive for Business 複数地域用にお客様の多国籍企業のサインアップを行ってください。
  
OneDrive の複数地域機能を使用すれば、データの常駐に関連する要件を満たすと同時に、モダンな生産性向上エクスペリエンスのグローバル展開を要員に開放するために、選択した地理的な場所に保存 (休眠) データをプロビジョニングして蓄えることができます。
  
複数地域機能が組織にどのようにメリットをもたらすことができるかを次に示します。
  
- 複数の地理的な場所にわたる単一の Office 365 テナントで、1 つのグローバルに接続された組織として事業活動を行う。
    
- 指定した地理的な場所内で保存データを作成してホストすることによって、データの常駐に関連する要件を満たす。
    
- 中央の場所のユーザーが恩恵を受けているモダンな生産性向上エクスペリエンスと同じエクスペリエンスをサテライトのユーザーに提供する。
    
- ユーザーのロールが変更された場合に、そのユーザーのコンテンツへのアクセスをそのまま維持した状態で、ユーザーが地理的な場所を超えて移動することを可能にする。
    
- 地理的な場所ごとのポリシーと、サイトごとのデータ損失防止ポリシーの共有を調整する。
    
- 地理的な場所ごとに電子情報開示マネージャー (管理者) を指定し、自分の地理的な場所に合わせた問題に適用される原則を許可する。
    
- 追加の地理的な場所に対して固有の URL 名前空間 (たとえば、ContosoEUR.sharepoint.com) を選択する。
    
- 地域のオンプレミス データを Office 365 の複数地域テナントに統合する。
    
Multi-Geo 構成では、Office 365 テナントは中央の場所 (Office 365 サブスクリプションが最初にプロビジョニングされた場所) と、1 つ以上のサテライトの地理的な場所から構成されます。Multi-Geo の重要な概念は、単一のテナントが複数の地理的な場所全体に及ぶことです。複数地域テナント内では、地理的な場所、グループ、およびユーザー情報に関する情報が、Azure Active Directory (AAD) 内でマスター管理されます。テナント情報が集中的にマスター管理され、個々の地理的な場所に同期されるので、その企業のすべてのユーザーが関わる共有とエクスペリエンスにグローバルな情報が含まれています。

## <a name="video-introducing-office-365-multi-geo"></a>ビデオ: Office 365 複数地域の紹介

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE1Yk6B?autoplay=false]
  
## <a name="get-multi-geo-features-in-three-simple-steps"></a>3 つの簡単な手順で複数地域機能を入手する

複数地域の構成は次のように簡単です。
  
1. アカウント チームと協力して、_Office 365 複数地域機能_サービス プランを追加します。チームから、必要な数のライセンスを追加するように説明があります。
    
2. サテライトの場所を追加します。
    
3. 該当する場所用のユーザー アカウントを構成します。
    
## <a name="multi-geo-status-and-availability"></a>複数地域の状態と可用性

OneDrive の複数地域は、現在次の地域と国で提供されています。
  
- アジア太平洋
    
- オーストラリア
    
- カナダ
    
- 欧州連合 (EMEA)

- フランス
    
- 日本
    
- 英国
    
- 米国 (北アメリカ)
    
- 韓国
      
今後提供予定の地域の場所:
  
- インド
    
## <a name="getting-started"></a>はじめに

OneDrive for Business 複数地域を開始するには、まず [OneDrive for Business 複数地域の環境を計画](plan-for-multi-geo.md)します。次に、[複数地域の環境の管理について](administering-a-multi-geo-environment.md)と、[ユーザーが複数地域の環境を体験する方法](multi-geo-user-experience.md)について説明します。OneDrive for Business 複数地域を設定する準備ができたら、[複数地域のテナントを構成](multi-geo-tenant-configuration.md)し、[既存の OneDrive サイトを新しい場所に移動](move-onedrive-between-geo-locations.md)して、[検索を設定](configure-search-for-multi-geo.md)します。
