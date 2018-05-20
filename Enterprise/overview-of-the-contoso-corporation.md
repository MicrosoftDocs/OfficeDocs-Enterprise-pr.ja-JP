---
title: Contoso Corporation の概要
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 1de16e29-ac2e-40b5-bf13-9301a51e16a8
description: '概要: は、世界中のオフィスの階層型の構造と、企業として Contoso 社を理解します。'
ms.openlocfilehash: 30a6dd23271fbbd5599053b934e6a1af9dc14d12
ms.sourcegitcommit: 8fcf6fd9f0c45a5445654ef811410fca3f4f5512
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2018
---
# <a name="overview-of-the-contoso-corporation"></a>Contoso Corporation の概要

 **の概要:** ビジネスおよび世界中のオフィスの階層構造として Contoso 社を理解します。
  
Contoso Corporation は、フランス、パリに本社を持つグローバル企業です。同社は、100,000 を超える製品の製造、販売、およびサポートを行う複合企業組織です。  
  
## <a name="the-contoso-corporation"></a>Contoso Corporation

Contoso 社の世界規模の組織では、次の場所にオフィスがあります。
  
**世界中の図 1: contoso 社のオフィス**

![世界各国の Contoso 社のオフィス](images/Contoso_Poster/Contoso_WW_Org.png)

  
図 1 は、パリにある本社と、さまざまな大陸にある地域ハブおよびサテライト オフィスを示しています。
  
世界中の contoso 社のオフィスでは、次の 3 つの層のデザインに従います。
  
- 本社
    
    コントソ株式会社の本社は、数十種類の管理、エンジニア リング、および製造施設の建物でパリ郊外の大規模な企業のキャンパスです。パリ本社では、contoso 社のデータ センターとインターネット上のすべてが搭載されています。
    
    本社には 15,000 人のワーカーがいます。
    
- 地域ハブ
    
    地域ハブ オフィスでは、60% の販売およびサポート スタッフが世界の特定の地域にサービスを提供しています。各地域のハブは、高帯域幅の WAN リンクでパリの本社に接続されています。  
    
    各地域ハブには平均 2,000 人のワーカーがいます。
    
- サテライト オフィス
    
    サテライト オフィスは 80% の売上が含まれているサポート スタッフと、主要都市またはサブ領域の contoso 社の顧客の物理的およびオンサイトのプレゼンスを提供します。各サテライト オフィスは、高帯域幅の WAN リンクを使用して地域のハブに接続されています。
    
    各サテライト オフィスには平均 250 人のワーカーがいます。
    
contoso 社の従業員の 25% はモバイル専用、地域のハブやサテライト オフィスでモバイル専用の作業者の割合が高いのです。モバイル専用の作業者のより良いサポートを提供するは、contoso 社は、重要なビジネス目標です。
  
## <a name="elements-of-contosos-implementation-of-the-microsoft-cloud"></a>要素のマイクロソフトの実装を contoso 社のクラウドします。

Contoso 社の IT 設計者で次の要素が識別される場合、マイクロソフトのクラウド ソリューションの導入を計画するとき。
  
- ネットワーク
    
    ネットワークには、マイクロソフトのクラウド サービスと負荷のピーク時のパフォーマンスを十分な帯域幅への接続が含まれています。いくつかの接続がローカルのインターネット接続を経由して、contoso 社のプライベート ネットワークのインフラストラクチャ全体にわたっていくつかになります。
    
    詳細については、[エンタープライズ設計者向けのマイクロソフト クラウド ネットワーク](microsoft-cloud-networking-for-enterprise-architects.md)のポスターを参照してください。
   
- ID
    
    Contoso 社では、Windows サーバーの AD フォレストを使用して、その内部 id プロバイダーのと、サード パーティのプロバイダーの顧客やパートナーもフェデレーションします。Contoso 社では、マイクロソフトのクラウド サービスのアカウントの内部のセットを活用する必要があります。顧客やパートナーのクラウド ベースのアプリケーションへのアクセスには、サードパーティの id プロバイダーの場合にもを活用する必要があります。
    
    詳細については、[マイクロソフトのクラウド Id](microsoft-cloud-it-architecture-resources.md#identity)エンタープライズ設計者のポスターを参照してください。
    
- セキュリティ
    
    クラウドベースの ID とデータのセキュリティには、データ保護、管理権限の管理、脅威の認識、およびデータ ガバナンスとセキュリティ ポリシーの実装を含める必要があります。
    
    詳細については、[マイクロソフトのクラウド セキュリティ](http://aka.ms/cloudarchsecurity)エンタープライズ設計者のポスターを参照してください。
    
- 管理
    
    クラウドベースのアプリと SaaS のワークロードの管理には、設定、データ、アカウント、ポリシー、およびアクセス許可を維持し、継続的な正常性とパフォーマンスを監視する機能が必要となります。Azure IaaS での仮想マシンの管理には、既存のサーバー管理ツールが使用されます。
    
## <a name="see-also"></a>関連項目

[Microsoft Cloud の Contoso](contoso-in-the-microsoft-cloud.md)
  
[Microsoft クラウド IT アーキテクチャのリソース](microsoft-cloud-it-architecture-resources.md)

[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://sway.com/FJ2xsyWtkJc2taRD)
 


