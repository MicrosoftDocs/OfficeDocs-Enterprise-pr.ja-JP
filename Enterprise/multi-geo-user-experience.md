---
title: 複数地域環境でのユーザー エクスペリエンス
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: Strat_SP_gtc
f1.keywords:
- NOCSH
ms.custom: ''
localization_priority: Priority
description: 複数地域環境での SharePoint、OneDrive、および Exchange のユーザー エクスペリエンスについて説明します。
ms.openlocfilehash: 21858989f853b2a8c87808e38763068631173f7f
ms.sourcegitcommit: 012bf4d8ad132435f9baeffd6f7e5ed264a8bfe0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/06/2020
ms.locfileid: "44057753"
---
# <a name="user-experience-in-a-multi-geo-environment"></a>複数地域環境でのユーザー エクスペリエンス

ここでは、OneDrive 複数地域構成でユーザーが確認できる内容について説明します。

## <a name="exchange-mailbox"></a>Exchange メールボックス

ユーザーの Exchange メールボックスは、優先されるデータの場所にプロビジョニングされ、PDLが変更されると自動的に移動されます。 ユーザーは、複数地域の環境でユーザー エクスペリエンスを変えることなく、Outlook および Web 上の Outlook を通常どおりに使用できます。

## <a name="hub-sites"></a>ハブ サイト

SharePoint ハブ サイトは、プロジェクト、部門、または地域の完全で一貫した表現を作成しながら、従業員のためのコンテンツの発見とエンゲージメントを強化します。 複数地域の環境では、ハブ サイトの地理的な場所に関係なく、サテライトの場所のサイトをハブ サイトに簡単に関連付けることができます。 ユーザーは、サイトの地理的な場所に関係なく、単一の検索エクスペリエンスを通じてハブ全体で検索して結果を得ることができます。

## <a name="microsoft-365-app-launcher"></a>Microsoft 365 アプリ起動ツール

アプリ起動ツールは、Multi-Geo に対応していて、各タイルをワークロードの適切な地域の場所に差し向けます。 SharePoint と OneDrive のタイルは、ユーザーにプロビジョニングされた地理的な場所に対応する場所をポイントします。 つまり、ユーザーは中央の場所に OneDrive を持っており、その SharePoint タイルは中央の場所にある SP Home をポイントしますが、グループ サイトは PDL に対応する場所にプロビジョニングされます。 

## <a name="office-applications"></a>Office アプリケーション

Office アプリケーション (Word、Excel、PowerPoint など) は、ユーザーがログインしたときに、ユーザーごとの適切な OneDrive for Business の地域の場所を自動的に検出します。 ユーザーは、自分の OneDrive または SharePoint サイトの地域固有の URL を入力する必要がありません。

## <a name="onedrive-for-business-sync-client"></a>OneDrive for Business 同期クライアント

OneDrive for Business 同期クライアント (バージョン 17.3.6943.0625 以降) は、ユーザーにとって適切な OneDrive for Business の地域の場所を自動的に検出します。 同期クライアントのサポートには、地理的な場所に関係なくグループベースのサイトを同期する機能が含まれています。 Groove 同期クライアントは複数地域ではサポートされていません。 

## <a name="onedrive-for-business-location"></a>OneDrive for Business の場所

ユーザーには、そのユーザーの優先されるデータの場所にプロビジョニングされた OneDrive for Business が提供されます。ユーザーが不適切な地域の場所を含む OneDrive URL に移動すると (以前の地域の場所からのブックマークなど)、適切な地域の場所にある OneDrive に自動的にリダイレクトされます。

## <a name="onedrive-ios-and-android"></a>OneDrive iOS および Android 

OneDrive iOS および Android モバイル アプリには、ユーザーの OneDrive ファイルと、ユーザーの地域の場所と関係なくユーザーが共有しているファイルが表示されます。OneDrive モバイル アプリからの検索では、すべての地域の場所から関連する結果が表示されます。これらのアプリの最新バージョンをダウンロードしてください。

詳細については、「[iOS で OneDrive を使う](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247)」および「[Android で OneDrive を使う](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36)」を参照してください。

## <a name="onedrive-mobile-client"></a>OneDrive モバイル アプリ 

OneDriveモバイル クライアントは複数地域に対応し、すべての地理的位置から関連コンテンツと結果を表示します。

## <a name="search"></a>検索

各地域の場所には、独自の検索インデックスと検索センターがあります。ユーザーが検索を実行すると、クエリはすべての地域の場所に送信されます。返される結果はマージされてからランク付けされるため、ユーザーには統一された結果が示されます。ユーザーは、自分の地域の場所に関係なく、すべての地域の場所からの結果を取得します。詳細については、「[OneDrive for Business 複数地域の検索の構成](configure-search-for-multi-geo.md)」を参照してください。

サポートされている検索クライアントは、次のとおりです。

-   OneDrive for Business

-   Delve

-   SharePoint Home

-   検索センター

-   SharePoint 検索 API を使用するカスタムの検索アプリケーション

## <a name="sharepoint-home"></a>SharePoint Home 

SharePoint ホームの SharePoint Multi-Geo では、OneDrive for businessの場所によって決定されるユーザーが存在する場所でホストされます。 たとえば、ユーザーが自分の OneDrive をヨーロッパのサテライトの場所でホストしている場合、その SharePoint ホームはヨーロッパからレンダリングされます。 SharePoint ホームには、地理的な場所に関係なく、ユーザーに関連するすべてのコンテンツが含まれています。 

**フォローしているサイト、サイトからのニュース、最近のサイト、よく使うサイト、そしておすすめのサイト**

ユーザーが当該コンテンツに対する権限を持っている限り、コンテンツがホストされている地理的な場所に関係なく、これらすべてのコンポーネントが表示されます。 

**おすすめリンク**

管理者は、各地理的な場所に対応して、SharePoint ホームのおすすめリンクを構成できます。 これにより、管理者は各地域の SP ホームでその地域のユーザーに適したリンクをおすすめできます。 

## <a name="sharepoint-mobile-client"></a>SharePoint モバイル クライアント 

SharePoint モバイル クライアントは複数地域に対応し、すべての地理的位置から関連コンテンツと結果を表示します。

## <a name="sharing"></a>共有

連絡先の選択のエクスペリエンスでは、地理的な場所に関係なくすべてのユーザーが表示されます。 これにより、ユーザーは、同じ地域または他のテナントの地域内の他のユーザーと共有できます。 さまざまな地域のコンテンツが、ユーザーの OneDrive for Business の[**自分と共有**] ビューに表示され、どの地域でホストされているかにかかわらず、シングル サインオン エクスペリエンスでアクセスできます。

## <a name="teams-experience"></a>Teams のエクスペリエンス

チームは複数地域に対応しています。 OneDrive ファイルと最近表示したファイルは、ユーザーの地理的な場所に関係なく表示されます。 @メンションはすべての地理的な場所からのユーザーに機能します。

## <a name="user-profiles"></a>ユーザー プロファイル

ユーザー プロファイル情報は、ユーザーの地域の場所でマスター管理されます。ユーザーを選択すると、そのユーザーにとって適切な地域の場所に転送され、完全なプロファイルの詳細を確認できます。

Delve がオフの場合、SharePoint の従来の (複数地域に対応していない) プロファイル エクスペリエンスが表示されます。


