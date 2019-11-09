---
title: SharePoint Online 最新版と従来版の発行サイト ページで iFrame を最適化する
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/17/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: SharePoint Online 最新版と従来版の発行サイト ページで iFrame のパフォーマンスを最適化する方法について説明します。
ms.openlocfilehash: 97848d28277f19e8984f1f08e90f07236fd5c85b
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "38078436"
---
# <a name="optimize-iframes-in-sharepoint-online-modern-and-classic-publishing-site-pages"></a>SharePoint Online 最新版と従来版の発行サイト ページで iFrame を最適化する

iFrame は、動画やその他のメディアなどのリッチ コンテンツをプレビューするのに便利です。 ただし、iFrame には SharePoint サイト ページ内の別個のページが読み込まれるため、iFrame に読み込まれるコンテンツには大きな画像、動画、またはページの読み込み時間全体に影響する可能性のある他の要素が含まれていることがあり、ページで制御できません。 この記事では、ページ内の iFrame がユーザーに発生する可能性のある待ち時間や、一般的な問題の解決方法を判断する方法について説明します。

>[!NOTE]
>Sharepoint Online の最新版サイトでのパフォーマンスの詳細については、「[SharePoint のモダン エクスペリエンスにおけるパフォーマンス](https://docs.microsoft.com/sharepoint/modern-experience-performance)」を参照してください。

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-web-parts-using-iframes"></a>SharePoint 用ページ診断ツールを使用して iFrame を使用する Web パーツを分析する

**SharePoint 用ページ診断ツール**は、Chrome と [Microsoft Edge バージョン 77 以降](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8)のブラウザー拡張機能であり、SharePoint の最新版と従来版両方の発行サイト ページを使用できます。 このツールでは、定義されている一連のパフォーマンス条件に対するページのパフォーマンスを示す分析済みの各ページのレポートが作成されます。 SharePoint 用ページ診断ツールのインストール方法と詳細については、「[SharePoint Online 用ページ診断ツールを使用する](page-diagnostics-for-spo.md)」を参照してください。

SharePoint のサイト ページを SharePoint 用ページ診断ツールを使用して分析すると、[_診断テスト_] ウィンドウに iFrame を含む Web パーツに関する情報が表示されます。 ベースライン メトリックは、最新版ページと従来版ページで同じです。

考えられる結果は次のとおりです。

- **要注意** (赤): このページには、iFrameを使用する Web パーツが **3 つ以上**含まれています
- **改善の余地あり** (黄): このページには、iFrameを使用する Web パーツが **1 つまたは 2 つ**含まれています
- **操作は不要** (緑): このページには iFrame を使用する Web パーツが含まれていません

[**iFrame を使用する Web パーツが検出されました**] の結果が、結果の [**改善の余地あり**] セクションまたは [**要注意**] セクションのいずれかに表示されている場合は、結果をクリックして iframe が含まれる Web パーツを表示できます。

![ページ診断ツールの結果](media/modern-portal-optimization/pagediag-iframe-yellow.png)

## <a name="remediate-iframe-performance-issues"></a>iFrame のパフォーマンスの問題を修復する

ページ診断ツールの [**iFrame を使用する Web パーツが検出されました**] の結果を使用して、iFrame を含み、ページの読み込み時間を遅らせる可能性のある Web パーツを特定します。

iFrame は本来、javascript、CSS、framework の要素など、関連付けられているすべてのコンテンツを含む別個の外部ページを読み込むために遅く、サイト ページのオーバーヘッドが 2 倍以上になる可能性があります。

以下のガイドラインに従って、iFrame の使用を最適にしてください。

- プレビューのサイズが開始するには小さく、または非対話型の場合、可能であれば iFrame の代わりに画像を使用します。
- iFrame を使用する必要がある場合は、数値を最小限に抑えるか、ビューポートから移動させます。
- Word、Excel、PowerPoint などの埋め込まれた Office ファイルは対話型ですが、読み込みは遅くなります。 ドキュメント全体へのリンクが含まれている画像のサムネイルは、多くの場合パフォーマンスが向上します。
- 埋め込みの YouTube ビデオと Twitter フィードにより、iFrame でのパフォーマンスは向上する傾向がありますが、こういった埋め込みは慎重に使用してください。
- 分離された Web パーツは当然例外ですが、ビューポートの数と配置は最小限に抑えます。
- iFrame がビューポートの外にある場合は、_IntersectionObserver_ を使用し、iFrame が表示されるまでレンダリングを遅らせることを検討してください。

ページの変更を行ってパフォーマンスの問題を修復する前に、分析結果のページの読み込み時間をメモします。 修正後にツールをもう一度実行して新しい結果がベースライン基準内にあるかどうかを確認し、新しいページ読み込み時間をチェックして改善されたかどうかを確認します。

![ページ読み込み時間の結果](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
>ページ読み込み時間は、ネットワーク負荷、時間帯、その他の一時的な状態など、さまざまな要素によって異なります。 結果を平均化するために、変更の前後に数回に渡ってページ読み込み時間をテストする必要があります。

## <a name="related-topics"></a>関連項目

[SharePoint Online のパフォーマンスをチューニングする](tune-sharepoint-online-performance.md)

[Office 365 のパフォーマンスをチューニングする](tune-office-365-performance.md)

[SharePoint のモダン エクスペリエンスにおけるパフォーマンス](https://docs.microsoft.com/sharepoint/modern-experience-performance.md)
