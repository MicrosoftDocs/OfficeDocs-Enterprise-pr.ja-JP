---
title: Multgeo 環境でのユーザー エクスペリエンス
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: マルチ geo 環境で SharePoint と OneDrive のユーザー エクスペリエンスについて説明します。
ms.openlocfilehash: 42e384d3e93ca3f5a06a8ee07a37b10e21477038
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="user-experience-in-a-multi-geo-environment"></a>マルチ地域環境でのユーザー エクスペリエンス

ここでは、OneDrive の複数の地域の構成では、ユーザーが表示されます。

#### <a name="users-onedrive-for-business-location"></a>業務の場所のユーザーの OneDrive

ユーザーには、希望するデータの場所を提供するビジネス用の OneDrive があります。場合は、正しくない地理的な場所 (以前の地理的な場所からブックマーク) などが含まれている OneDrive の URL にユーザーが移動した、適切な地理的な場所に OneDrive を自動的にリダイレクトされます。

#### <a name="sharing"></a>共有

ユーザー選択ウィンドウの操作性は、その地域の場所に関係なくすべてのユーザーを示します。これにより、ユーザーは、同じ地域でも、他のテナントの geo の場所の他のユーザーと共有できます。場所、**自分と共有**ビューでのビジネス ユーザーの OneDrive が表示され、アクセスするのには、シングル ・ サインオン環境でホストされている地理的な場所に関係なく、異なる地域からのコンテンツします。

#### <a name="office-applications"></a>Office アプリケーション

Word、Excel、PowerPoint などの Office アプリケーションにログインするとき、各ユーザーのビジネスの地理的な場所に適切な OneDrive が自動的に検出します。ユーザーは、OneDrive の地域に固有の URL を入力する必要はありません。

#### <a name="onedrive-for-business-sync-client"></a>同期クライアントのビジネスの OneDrive

同期クライアントのビジネスの OneDrive (バージョン 17.3.6943.0625 以降では)、ユーザーの業務地域の場所の正しい OneDrive を自動的に検出されます。

#### <a name="office-365-app-launcher"></a>Office 365 アプリ起動ツール

アプリケーション起動プログラムは複数の地域に注意してください、作業負荷の適切な地域の場所には、各タイルを紹介OneDrive では、ユーザーの OneDrive ライブラリをホストしている、SharePoint のタイルのすべてのユーザーを指す中央の場所では、チーム サイトは引き続きホストされているが、中に地域の正しい場所を並べて表示します。

#### <a name="delve-user-profiles"></a>ユーザー プロファイルを説明します。

ユーザー プロファイル情報はユーザーの地域の場所で習得します。ユーザーを選択すると、表示される、適切な地域の場所に、ユーザーの場所の完全なプロファイルの詳細が表示されます。

Delve がオフの場合は、複数地域の対応ではありませんが発生する SharePoint で、従来のプロファイルが表示されます。

#### <a name="delve"></a>Delve

Office 365 ユーザーに対しては衛星の場合に、複数の地域の説明はサポートされて Delve が SharePoint の SharePoint ブログ サイトにのみ、その他の地域のユーザーが作成したブログの投稿にリンクしないこと。

#### <a name="search"></a>検索

各地域の場所では、独自の検索インデックスと検索センターがあります。ユーザーが検索するときに、すべての場所の地域では、クエリが送信されると返される結果がマージされ、ユーザーは統一された結果を取得するために、ランク付けします。ユーザーは、独自の地域の場所に関係なくすべての地域の場所からの結果を取得します。詳細については、 [OneDrive 複数の地域のビジネスを検索する構成](configure-search-for-multi-geo.md)を参照してください。

次の検索クライアントがサポートされています。

-   OneDrive for Business

-   Delve

-   SharePoint ホーム

-   検索センター

-   SharePoint 検索 API を使用するカスタムの検索アプリケーション

#### <a name="onedrive-ios-and-android"></a>OneDrive iOS および Android 

OneDrive iOS および Android モバイル アプリケーションが表示されます、OneDrive ファイルとファイルを共有する地域の保存場所を問わない。OneDrive のモバイル アプリケーションからの検索には、地域のすべての場所から関連する検索結果が表示されます。これらのアプリケーションの最新バージョンをダウンロードしてください。

詳細については、 [iOS の OneDrive](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247)の使用と[アプリの使用 OneDrive](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36)を参照してください。

#### <a name="teams-experience"></a>チームの経験

チームは、複数の地域に注意してください。OneDrive ファイルおよび最近表示したファイルは、ユーザーの地域の場所に関係なく表示されます。@ すべての地域の場所からユーザーの作業を参照。
