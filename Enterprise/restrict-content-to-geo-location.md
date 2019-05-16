---
title: 地域の場所にコンテンツを制限する
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 複数地域環境で SharePoint サイトを指定の地域の場所に制限する方法について説明します。
ms.openlocfilehash: 42c382abd254afcf74dd6bdd15e4c69f65b64f85
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070993"
---
# <a name="restrict-content-to-a-geo-location"></a>地域の場所にコンテンツを制限する

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
