---
title: Office 365 コンテンツ配信ネットワーク (CDN) クイックスタート
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 06/04/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
description: Office 365 コンテンツ配信ネットワーク (CDN) クイックスタート
ms.openlocfilehash: 4abaaa5545bc807c4da297c66fd9ad1fb188adc7
ms.sourcegitcommit: 576c3dbdef535f952a861197dea5348908da9504
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "44561923"
---
# <a name="office-365-content-delivery-network-cdn-quickstart"></a>Office 365 コンテンツ配信ネットワーク (CDN) クイックスタート

組み込みの**Office 365 コンテンツ配信ネットワーク (CDN)** を使用して、静的なアセット (画像、JavaScript、スタイルシート、woff ファイル) をホストし、SharePoint Online ページのパフォーマンスを向上させることができます。 Office 365 CDN では、静的資産を要求しているブラウザーの近くに静的資産をキャッシュするとパフォーマンスが向上します。これにより、ダウンロードが速くなり、待ち時間が短縮されます。 また、Office 365 CDN は、強化された圧縮と HTTP パイプライン処理に HTTP/2 プロトコルを使用します。 Office 365 CDN サービスは、SharePoint Online サブスクリプションの一部として含まれます。

詳細については[、「SharePoint Online で Office 365 コンテンツ配信ネットワーク (CDN) を使用する](use-office-365-cdn-with-spo.md)」を参照してください。

>[!NOTE]
>Office 365 CDN は、運用環境 (世界規模) のクラウドのテナントでのみ使用できます。 米国政府機関のテナント、中国およびドイツのクラウドでは、現在 Office 365 CDN をサポートしていません。

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-identify-items-not-in-cdn"></a>SharePoint 用ページ診断ツールを使用して CDN に含まれていないアイテムを識別する

SharePoint ツールブラウザー拡張機能**のページ診断**を使用して、CDN の配信元に追加できる sharepoint Online ページのアセットを簡単に一覧表示できます。

**Sharepoint 用ページ診断ツール**は、新しい Microsoft Edge ( https://www.microsoft.com/edge) および sharepoint Online モダンポータルと従来の発行サイトページの両方を分析する Chrome ブラウザー) 用のブラウザー拡張機能です。 このツールでは、定義されている一連のパフォーマンス条件に対するページのパフォーマンスを示す分析済みの各ページのレポートが作成されます。 SharePoint 用ページ診断ツールのインストール方法と詳細については、「[SharePoint Online 用ページ診断ツールを使用する](https://aka.ms/perftool)」を参照してください。

SharePoint Online ページで SharePoint ツールのページ診断ツールを実行すると、[**診断テスト**] タブをクリックして、CDN によってホストされていないアセットの一覧を表示できます。 これらのアセットは、以下のスクリーンショットに示されているように、[見出し**コンテンツ配信ネットワーク (CDN)] チェック**の下に一覧表示されます。

![ページ診断](media/page-diagnostics-for-spo/pagediag-results-general.PNG)

>[!NOTE]
>ページ診断ツールは SharePoint Online でのみ機能し、SharePoint システム ページでは使用できません。

## <a name="cdn-overview"></a>CDN の概要

Office 365 CDN は、画像や javascript ファイルなど、頻繁にアクセスされるオブジェクトを高速なグローバルネットワーク経由で分散することによって、ユーザーのパフォーマンスを最適化するように設計されています。これにより、ページの読み込み時間が短縮され、ホストされたオブジェクトへのアクセスがユーザーにできるだけ近づけることができます。 CDN は、_送信元_と呼ばれる場所からアセットを取得します。 起点として、URL でアクセスできる SharePoint サイト、ドキュメントライブラリ、またはフォルダーを指定できます。

Office 365 CDN は、次の2つの基本的な種類に分けられます。

- **パブリック CDN**は、JS (JavaScript)、CSS (スタイルシート)、Web フォントファイル (woff、WOFF2)、会社のロゴなどの非所有の画像に使用するように設計されています。
- **プライベート CDN**は、画像 (PNG、JPG、JPEG など) に使用するように設計されています。

組織にパブリックまたはプライベートのどちらを使用するかを選択できます。 大部分の組織では、2つの組み合わせを実装することを選択します。 パブリックおよびプライベートのどちらのオプションもパフォーマンスの向上に似ていますが、それぞれに固有の属性と利点があります。 パブリックおよびプライベート CDN オリジンの詳細については、「[各配信元をパブリックまたはプライベートにする必要があるかどうかを選択](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)する」を参照してください。

## <a name="how-to-enable-public-and-private-cdn-with-the-default-configuration"></a>既定の構成を使用してパブリック CDN とプライベート CDN を有効にする方法
テナントの CDN 設定に変更を加える前に、組織のコンプライアンス、セキュリティ、プライバシーポリシーを満たしていることを確認する必要があります。

構成設定の詳細については、または既に CDN を有効にしていて、別の場所 (出所) を追加する場合は、「 [SharePoint Online 管理シェルを使用して Office 365 CDN をセットアップおよび構成](use-office-365-cdn-with-spo.md#set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell)する」を参照してください。

SharePoint Online 管理シェルを使用して、テナントに接続します。

```PowerShell
Connect-SPOService -Url https://<YourTenantName>-admin.sharepoint.com
```

既定の構成でパブリックとプライベートの両方のオリジンを組織で使用できるようにするには、次のコマンドを入力します。

```PowerShell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

これらのコマンドレットの出力は次のようになります。

![SPOTenantCdnEnabled の出力](media/O365-CDN/o365-cdn-enable-output.png)

## <a name="see-also"></a>関連項目

[SharePoint Online のページ診断ツールを使用する](https://aka.ms/perftool)

[SharePoint Online での Office 365 コンテンツ配信ネットワーク (CDN) の使用](use-office-365-cdn-with-spo.md)

[Content Delivery Network](https://aka.ms/o365cdns)

[Office 365 のネットワーク計画とパフォーマンス チューニング](https://aka.ms/tune)

[SharePoint パフォーマンスシリーズ-Office 365 CDN ビデオシリーズ](https://www.youtube.com/playlist?list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA)
