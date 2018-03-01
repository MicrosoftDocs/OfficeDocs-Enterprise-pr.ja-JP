---
title: "OneDrive の複数地域機能および Office 365 の SharePoint Online"
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 1/24/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: "OneDrive と SharePoint Online での複数地域の機能により、組織は複数の地域や国に加え、既存のテナントに、Office 365 のプレゼンスを展開できます。"
ms.openlocfilehash: d53da13d5a6a6d5add9da69a3bca9fcdfa39bbd0
ms.sourcegitcommit: 38d43444cf5e03527aa75f670efb2de0f48f847d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2018
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365"></a>OneDrive の複数地域機能および Office 365 の SharePoint Online

OneDrive の複数地域機能と SharePoint Online を使用すれば、組織はその組織の Office 365 のプレゼンスを、その既存のテナント内の複数の地域または国に対して展開することができます。この機能は現在プレビューの段階です。お客様の Microsoft アカウント チームと連絡を取って、OneDrive の複数地域プレビューを入手するためにお客様の多国籍の企業をサインアップしてください。
  
OneDrive 複数の地域でのプロビジョニングしデータ常駐サービスの要件を満たすために選択した地域の場所にデータの両方を格納して、従業員に最新の生産性エクスペリエンスをグローバルの展開のロックを解除を同時にできます。
  
複数地域の機能による組織にとってのメリットを以下に示します。
  
- 複数の地理的な場所にわたる単一の Office 365 テナントで、1 つのグローバルに接続された組織として事業活動を行う。
    
- 指定した地理的な場所内で保存データを作成してホストすることによって、データの常駐に関連する要件を満たす。
    
- 中央の場所のユーザーが恩恵を受けているモダンな生産性向上エクスペリエンスと同じエクスペリエンスをサテライトのユーザーに提供する。
    
- ユーザーのロールが変更された場合に、そのユーザーのコンテンツへのアクセスをそのまま維持した状態で、ユーザーが地理的な場所を超えて移動することを可能にする。
    
- 地理的な場所ごとのポリシーと、サイトごとのデータ損失防止ポリシーの共有を調整する。
    
- 地理的な場所ごとに電子情報開示マネージャー (管理者) を指定し、自分の地理的な場所に合わせた問題に適用される原則を許可する。
    
- 追加の地理的な場所に対して固有の URL 名前空間 (たとえば、ContosoEUR.sharepoint.com) を選択する。
    
- 地域のオンプレミス データを Office 365 の複数地域テナントに統合する。
    
詳細については、およびデモを参照するには、 [Office 365 の機能を複数の地域の導入とそれを構成する方法](https://youtu.be/3d9-Vt2fArk)」および「[複数地域の概要のポスター](https://technet.microsoft.com/library/dn782272.aspx)を参照してください。
  
複数地域構成では、Office 365 テナントは「既定の位置」とも呼ばれる中央の場所と、1 つ以上のサテライトの地理的な場所から構成されます。複数地域の重要な概念は、単一のテナントが複数の地理的な場所全体に及ぶことです。複数地域テナント内では、地理的な場所、グループ、およびユーザー情報に関する情報が、Azure Active Directory (AAD) 内でマスター管理されます。テナント情報が集中的にマスター管理され、個々の地理的な場所に同期されるので、その企業のすべてのユーザーが関わる共有とエクスペリエンスにグローバルな情報が含まれています。
  
## <a name="sample-multi-geo-tenant-configuration"></a>複数地域のテナント構成の例

北アメリカに中央拠点がある Contoso は、複数地域テナントを使用して、Contoso.com という単一組織の傘下のヨーロッパおよびオーストラリアにあるサテライトの地理的な場所に展開することができます。自分の優先されるデータの場所がヨーロッパに設定されているユーザーはヨーロッパに自分の OneDrive を保持している一方、自分の優先されるデータの場所が北アメリカにあるユーザーは米国に自分の OneDrive を保持しています。
  
![Contoso 社の地域の場所とその他の利用可能な地域の場所を示す、世界中のマップ](images/df317ccc-2e53-411d-9211-a5aee63ca1e5.png)
  
## <a name="get-multi-geo-features-in-three-simple-steps"></a>3 つの簡単な手順で複数地域機能を入手する

複数地域の構成は次のように簡単です。
  
1. 複数地域用に Office 365 テナントを有効にします。
    
2. サテライトの場所を追加します。
    
3. 該当する場所用のユーザー アカウントを構成します。
    
## <a name="multi-geo-status-and-availability"></a>複数地域の状態と可用性

OneDrive の複数地域は、現在次の地域と国で提供されています。
  
- アジア太平洋
    
- オーストラリア
    
- カナダ
    
- 欧州連合 (EMEA)
    
- インド
    
- 日本
    
- 英国
    
- 米国 (北アメリカ)
    
- 韓国
    
> [!NOTE]
> インドと韓国は、現在それらの地理的な場所内にライセンスと請求先の住所を持つお客様のみ利用できます。 
  
今後提供予定の地理的な場所:
  
- フランス
    
利用できるサービス:
  
- Exchange Online (プレビュー中)
    
- OneDrive for Business (プレビュー中)
    
- SharePoint Online (開発中)
    

