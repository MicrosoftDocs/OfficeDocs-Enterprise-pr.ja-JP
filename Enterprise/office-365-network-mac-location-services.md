---
title: Microsoft 365 ネットワーク接続ロケーションサービス (プレビュー)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/31/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Microsoft 365 ネットワーク接続ロケーションサービス (プレビュー)
ms.openlocfilehash: 13ca35afe4bd375482a9fc924801e240c361bb6b
ms.sourcegitcommit: 6508db0a839427e1a21b1cde883d828e3c8886c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "43185728"
---
# <a name="microsoft-365-network-connectivity-location-services-preview"></a>Microsoft 365 ネットワーク接続ロケーションサービス (プレビュー)

Microsoft 365 管理センターには、Microsoft 365 テナントから収集され、テナントの管理ユーザーのみが閲覧できるライブパフォーマンス指標である、**ネットワークの洞察とパフォーマンスに関する推奨事項**が表示されます。 組織のネットワーク接続は、ネットワークの出口からインターネットへの場所によって、オフィスの場所ごとに設計されています。 Microsoft 365 クライアント接続は、そのルートを使用して、インターネットを介して Microsoft サービスのフロントドアサーバーに接続します。 Office の場所を特定することは、これらのネットワーク洞察を表示できることを示す鍵となります。

## <a name="location-in-network-measurements"></a>ネットワーク測定の場所

組織の管理者は、この機能で使用されるネットワーク測定に含める場所をオプトインすることができます。 これにより、各オフィスが配置されている都市の自動検出が有効になります。 場所情報が正確ではなく、300m にわかりにくくなり、都市ごとに分類されています。 場所が Windows デバイスでキャプチャされているときには、ツールトレイに**使用中の場所**のアイコンが表示されるため、管理者はそのことをユーザーに通知する必要があります。 この処理では、場所はユーザーまたはデバイスの場所ではなく、組織のオフィスの場所として扱われます。 ネットワーク insights は、検出されたオフィスの場所の都市に表示することができます。 推奨事項の正確性が向上している場合は、管理者が特定のオフィスの場所のアドレスを入力すると、その場所にネットワーク洞察が集約されます。 Office の場所を300メートルよりも詳細に集計することはできません。

## <a name="location-in-the-microsoft-365-admin-center"></a>Microsoft 365 管理センターの場所

Microsoft 365 管理センターでは、Bing マップコントロールを使用して、組織の場所の場所を示し、選択したオフィスの場所のネットワーク境界トポロジを表示します。 管理者が office の場所に特定の住所の詳細を追加すると、データ入力を簡単にするためにアドレスを提案するために Bing Maps も使用されます。

## <a name="terms-of-use"></a>使用条件

Geocodes を含む Bing Maps で提供されるコンテンツは、そのコンテンツが提供される製品内でのみ使用できます。 お客様による Microsoft 365 管理センターの場所サービス機能の使用 (Bing Maps による) は、 _Bing Maps エンドユーザー使用許諾契約_書<https://go.microsoft.com/?linkid=9710837> () およびで提供される_Microsoft のプライバシー_に関する声明に準拠しています。<https://go.microsoft.com/fwlink/?LinkID=248686.>

Bing Maps で提供されるこの機能は、この**テクノロジ**でもサポートされています。 Bing Maps_は、ここ_で提供される場所サービスを活用する方法について説明<https://legal.here.com/en-gb/terms>します。
