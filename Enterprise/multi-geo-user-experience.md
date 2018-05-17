---
title: 複数地域環境でのユーザー エクスペリエンス
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 複数地域環境での SharePoint および OneDrive のユーザー エクスペリエンスについて説明します。
ms.openlocfilehash: 3c7e4b6802bddc78db016c9c282f5add0c71c491
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="user-experience-in-a-multi-geo-environment"></a>複数地域環境でのユーザー エクスペリエンス

ここでは、OneDrive 複数地域構成でユーザーが確認できる内容について説明します。

#### <a name="users-onedrive-for-business-location"></a>ユーザーの OneDrive for Business の場所

ユーザーには、そのユーザーの優先されるデータの場所にプロビジョニングされた OneDrive for Business が提供されます。ユーザーが不適切な地域の場所を含む OneDrive URL に移動すると (以前の地域の場所からのブックマークなど)、適切な地域の場所にある OneDrive に自動的にリダイレクトされます。

#### <a name="sharing"></a>共有

ユーザー選択ウィンドウのエクスペリエンスでは、ユーザーの地域の場所に関係なく、すべてのユーザーが示されます。これにより、ユーザーは同じ地域またはテナントの地域の場所が異なる他のユーザーとの共有が可能になります。別の地域の場所からのコンテンツは、ユーザーの OneDrive for Business の **[共有相手]** ビューに表示され、そのコンテンツがホストされている地域の場所に関係なく、シングルサインオン エクスペリエンスに関連付けることができます。

#### <a name="office-applications"></a>Office アプリケーション

Office アプリケーション (Word、Excel、PowerPoint など) は、ユーザーがログインしたときに、ユーザーごとの適切な OneDrive for Business の地域の場所を自動的に検出します。ユーザーは、自分の OneDrive の地域固有の URL を入力する必要がありません。

#### <a name="onedrive-for-business-sync-client"></a>OneDrive for Business 同期クライアント

OneDrive for Business 同期クライアント (バージョン 17.3.6943.0625 以降) は、ユーザーにとって適切な OneDrive for Business の地域の場所を自動的に検出します。

#### <a name="office-365-app-launcher"></a>Office 365 アプリ起動ツール

アプリ起動ツールは、複数地域に対応していて、各タイルをワークロードの適切な地域の場所に差し向けます。OneDrive タイルは、ユーザーの OneDrive ライブラリがホストされている適切な地域の場所をポイントします。その一方で、SharePoint タイルは、すべてのユーザーを中央の場所に差し向けます (チーム サイトは引き続き中央の場所でホストされるため)。

#### <a name="delve-user-profiles"></a>Delve のユーザー プロファイル

ユーザー プロファイル情報は、ユーザーの地域の場所でマスター管理されます。ユーザーを選択すると、そのユーザーにとって適切な地域の場所に転送され、完全なプロファイルの詳細を確認できます。

Delve がオフの場合、SharePoint の従来の (複数地域に対応していない) プロファイル エクスペリエンスが表示されます。

#### <a name="delve"></a>Delve

サテライトのインスタンスに存在する Office 365 ユーザーの場合は、Delve 複数地域がサポートされますが、別の地域に存在するユーザーの記述した SharePoint ブログ投稿へのリンクが Delve に示されないという制限があります。そのユーザーの SharePoint ブログ サイトへのリンクのみが示されます。

#### <a name="search"></a>検索

各地域の場所には、独自の検索インデックスと検索センターがあります。ユーザーが検索を実行すると、クエリはすべての地域の場所に送信されます。返される結果はマージされてからランク付けされるため、ユーザーには統一された結果が示されます。ユーザーは、自分の地域の場所に関係なく、すべての地域の場所からの結果を取得します。詳細については、「[OneDrive for Business 複数地域の検索の構成](configure-search-for-multi-geo.md)」を参照してください。

サポートされている検索クライアントは、次のとおりです。

-   OneDrive for Business

-   Delve

-   SharePoint Home

-   検索センター

-   SharePoint 検索 API を使用するカスタムの検索アプリケーション

#### <a name="onedrive-ios-and-android"></a>OneDrive iOS および Android 

OneDrive iOS および Android モバイル アプリには、ユーザーの OneDrive ファイルと、ユーザーの地域の場所と関係なくユーザーが共有しているファイルが表示されます。OneDrive モバイル アプリからの検索では、すべての地域の場所から関連する結果が表示されます。これらのアプリの最新バージョンをダウンロードしてください。

詳細については、「[iOS で OneDrive を使う](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247)」および「[Android で OneDrive を使う](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36)」を参照してください。

#### <a name="teams-experience"></a>Teams のエクスペリエンス

Teams は、複数地域に対応しています。OneDrive ファイルとユーザーの地域の場所と関係なく最近表示したファイルが表示されます。@ は、すべての地域の場所からのユーザーと作業することを示します。
