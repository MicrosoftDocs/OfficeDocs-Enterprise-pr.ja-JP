---
title: SharePoint Online モダンポータルサイトの制限
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/9/2019
audience: Admin
ms.topic: interactive-tutorial
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Strat_O365_Enterprise
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
description: SharePoint Online のモダンサイトのパフォーマンスに関する推奨事項について説明します。
ms.openlocfilehash: 227eadd780acbe35456ca48204762411bed6c10f
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844788"
---
# <a name="sharepoint-online-modern-portal-site-limits"></a>SharePoint Online モダンポータルサイトの制限

この記事では、SharePoint Online のモダンポータルサイトのパフォーマンスに関する推奨事項について説明します。 この記事のガイドラインを使用して、最新のポータルサイトのパフォーマンスを最適化し、一般的なパフォーマンスの問題を回避します。

## <a name="performance-considerations-for-modern-portal-sites"></a>モダンポータルサイトのパフォーマンスに関する考慮事項

パフォーマンスの最適化の観点から、モダンポータルサイトを一意にするためのいくつかの特性があります。 SharePoint Online のグループ作業とポータルサイトの主な違いはスケールです。 一般に、ポータルサイトでは、グループ作業サイトより多くのユーザーに対してより多くのページビューを提供することが期待されます。多くの場合、より多くの静的コンテンツと編集可能なリソースが含まれている可能性があります。 さらに、モダンサイトのアーキテクチャは従来のサイトとは異なります。これは、レンダリングページに含まれる処理のほとんどが、サーバーではなくクライアントで行われることです。

モダンポータルサイトのパフォーマンスの最適化は、主にいくつかの全体的な目標に重点を置いています。

- 各サイトページのコンポーネントの合計サイズを小さくする
- 画像、スタイルシート、スクリプトなどの一般的な静的ファイルを CDN にオフロードする
- SharePoint および外部エンドポイントへの呼び出しを、必要なものだけに制限する
- 同じコンテンツに対して重複する要求を回避する

この記事のガイドラインの多くは、SharePoint Online への呼び出しを最小限に抑え、最適化することに重点を置いています。 ページが読み込まれるたびに反復呼び出しを行うと、情報が変更されていない場合でも、その情報が毎回サービスから取得されるため、ユーザーのパフォーマンスが低下します。 そのため、SharePoint への要求は、すべてのユーザーに共通の呼び出しとして、または個々のユーザーごとに必要な呼び出しとして分類できます。 これらの2つの呼び出しカテゴリからの結果は、ユーザーの利便性を最適化するためにキャッシュする必要があります。

>[!NOTE]
>Sharepoint Online サイトページで特定のパフォーマンス指標を分析するための開始点として、 [sharepoint 用ページ診断ツール](https://aka.ms/perftool)を使用します。

## <a name="modern-portal-site-limits-and-recommendations"></a>モダンポータルサイトの制限と推奨事項

|**制限**|**推奨される最大値**|**メモ**|
|:-----|:-----|:-----|:-----|
|ページとニュースアイテム  <br/> |サイトごとに 5,000 件  <br/> |モダンポータルサイトのページ数とニュースアイテム数を5000以下に制限することをお勧めします。  <br/> |
|ページ上の Web パーツ  <br/> |ページごとに20個  <br/> |標準の Microsoft web パーツとカスタム web パーツの両方を含む、ページごとに20以下の web パーツを使用することをお勧めします。 <br/> 詳細については、「 [SharePoint Online モダンサイトページで web パーツのパフォーマンスを最適化](modern-web-part-optimization.md)する」を参照してください。  <br/> |
|ページ上の動的 web パーツ  <br/> |ページごとに4個  <br/> |SharePoint に対して1つ以上のクエリを作成して最新のデータをフェッチする動的 web パーツは、1ページあたり4個に制限する必要があります。 _ニュース_web パーツは、動的な web パーツの例です。 <br/> 詳細については、「 [SharePoint Online モダンサイトページで web パーツのパフォーマンスを最適化](modern-web-part-optimization.md)する」を参照してください。    <br/> |
|セキュリティ グループ  <br/> |サイトごとに20個  <br/> |セキュリティグループの数は、モダンポータルサイトの多くのクエリのスケールに影響します。 セキュリティグループの数は、サイトごとに20を超えないように、できるだけ小さなセットに制限することをお勧めします。  <br/> |
|サイトナビゲーション内のアイテム  <br/> |サイトごとに100  <br/> |サイトナビゲーションには100未満のアイテムを追加し、すぐに使用できるナビゲーションコントロールを使用することをお勧めします。  <br/> 詳細については、「 [SharePoint Online モダンサイトページでページのウエイトを最適化](modern-page-weight-optimization.md)する」を参照してください。 <br/> |
|画像の最大サイズ  <br/> |画像ごとに 300 Kb  <br/> |画像のサイズを300kb 以下に制限し、CDN を使用して画像、スタイルシート、スクリプトをホストすることをお勧めします。 <br/>詳細については、「 [Sharepoint online モダンサイトページで画像を最適化](modern-image-optimization.md)する」と「 [Sharepoint online で Office 365 コンテンツ配信ネットワーク (CDN) を使用する](use-office-365-cdn-with-spo.md)」を参照してください。  <br/> |
|編集権限を持つユーザー  <br/> |サイトごとに200ユーザー  <br/> |SharePoint ポータルサイトは、コンテンツを表示および使用できるように最適化されています。 [編集] アクセス許可は、追加のコントロールをダウンロードするため、アクセス許可を制限するユーザーのグループに制限する必要があります。そのため、これらのユーザーに対しては実行速度が遅くなります。 このため、編集アクセス許可を持つユーザーの数が多すぎると、全体的な操作に影響します。 <br/> |
|サードパーティの Iframe  <br/> |ページごとに2個  <br/> |iFrames は、javascript、CSS、フレームワーク要素などの関連付けられたすべてのコンテンツを含む個別の外部ページを読み込むため、予想には時間がかかります。 Iframe を使用する必要がある場合は、ページごとに2個以下に制限します。<br/> 詳細については、「 [SharePoint Online モダンおよび従来の発行サイトページで iframe を最適化](modern-iframe-optimization.md)する」を参照してください。 <br/> |
|UPA サービスの呼び出し  <br/> |ユーザーごとに1時間ごとに1回  <br/> |UPA (User Profile Application) サービスへの_要求ごと_に電話をかけないことをお勧めします。 [Microsoft GRAPH API](https://docs.microsoft.com/graph/call-api)と[pagecontext](https://docs.microsoft.com/javascript/api/sp-page-context/pagecontext?view=sp-typescript-latest)を使用して、ユーザー情報のクエリを実行できます。  <br/> UPA サービス呼び出しが必要な場合は、必要に応じて1つの呼び出しを行ってから、同じセッションで再利用するために情報をキャッシュします。 |
|分類サービスの呼び出し  <br/> |1時間あたりのユーザーごとに5個  <br/> |分類サービスへの_要求ごと_に呼び出しを行うことをお勧めします。 分類サービスの呼び出しが必要な場合は、同じセッションで再利用するために情報をキャッシュします。 <br/> 詳細については、「 [SharePoint Online モダンおよび従来の発行サイトページでページ呼び出しを最適化](modern-page-call-optimization.md)する」を参照してください。 <br/> |

## <a name="related-topics"></a>関連項目

[正常な SharePoint ポータルを作成する](https://docs.microsoft.com/sharepoint/portal-health)

[SharePoint Online のパフォーマンスをチューニングする](tune-sharepoint-online-performance.md)

[Office 365 のパフォーマンスをチューニングする](tune-office-365-performance.md)

[SharePoint Online の制限](https://docs.microsoft.com/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits)

[SharePoint のモダン エクスペリエンスにおけるパフォーマンス](https://docs.microsoft.com/sharepoint/modern-experience-performance)

[SharePoint Online ポータル パフォーマンス ガイダンス](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-performance)
