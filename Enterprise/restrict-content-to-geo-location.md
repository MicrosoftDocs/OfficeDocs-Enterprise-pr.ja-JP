---
title: SharePoint サイトのコンテンツを地域の場所に制限する
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 複数地域環境で SharePoint サイトを指定の地域の場所に制限する方法について説明します。
ms.openlocfilehash: ca63f46ba45d1b3ddfdf4f676b678d62387b801f
ms.sourcegitcommit: 265cc03b600e9015a44c60c3f8bb9075b1c20888
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "41973959"
---
# <a name="restrict-sharepoint-site-content-to-a-geo-location"></a>SharePoint サイトのコンテンツを地域の場所に制限する

状況によっては、サイトが移動されないようにするか、サイトのファイル コンテンツが別の地域の場所にキャッシュされないようにすることで、サイトが作成された地域の場所にサイトとそのファイル コンテンツを保持するように選択できます。

これを行うには、[Set-SPOSite](https://docs.microsoft.com/powershell/module/sharepoint-online/set-sposite) コマンドレットを **RestrictedToGeo** パラメーターと共に使用します。 このパラメーターの既定値は NULL ですが、次のいずれかに変更できます。

|制限|説明|
|:----------|:----------|
|NoRestriction|サイトを別の地域の場所に移動できます。|
|BlockMoveOnly|サイトを別の地域の場所に移動することはできませんが、サイトのコンテンツを別の地域の場所にキャッシュすることができます。|
|BlockFull|サイトを別の地域の場所に移動することはできません。また、ファイルのすべてのコンテンツも他の地域の場所にキャッシュされません。 ファイルのタイトル (コンテンツから取得)、ファイル名、およびファイルの他のプロパティは、引き続き別の地域の場所にキャッシュできます。<br>BlockFull に構成される前にサイトに保存されたコンテンツは、引き続き他の地域の場所にキャッシュされる可能性があります。|

次の構文を使用します。

`Set-SPOSite -Identity <siteURL> -RestrictedToGeo <restriction>`

次に例を示します。

`Set-SPOSite -Identity https://contoso.sharepoint.com/sites/RegionRestrictedTeamSite -RestrictedToGeo BlockFull`
