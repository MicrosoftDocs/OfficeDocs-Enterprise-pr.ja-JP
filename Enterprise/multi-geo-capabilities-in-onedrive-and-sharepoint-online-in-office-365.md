---
title: OneDrive および SharePoint Online の複数地域機能
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: OneDrive Online の複数地域機能を使用して、複数の地域に Office 365 のプレゼンスを展開します。
ms.openlocfilehash: ce5a846391fd62daafd174baea4144ac1d1aba37
ms.sourcegitcommit: 509bcf92580d7a0bcebbf6f1d10311d6b0014984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "31992847"
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online"></a>OneDrive および SharePoint Online の複数地域機能

OneDrive および SharePoint Online の複数地域機能を使用すると、SharePoint チーム サイトや Office 365 グループ メールボックスなどの共有リソースを保存する国または地域をコントロールすることができます。

ユーザー、グループ メールボックス、SharePoint サイトごとに、関連データが格納される地域の場所を示す PDL (Preferred Data Location、優先されるデータの場所) があります。 ユーザーの個人データ (Exchange メールボックスと OneDrive) を、本人が作成した Office 365 グループまたは SharePoint サイトと共に指定された地域の場所に格納して、データ所在地の要件を満たすことができます。 [地域の場所ごとに異なる管理者を指定する](add-a-sharepoint-geo-admin.md)ことができます。

ユーザーが Office アプリケーション、OneDrive、Search などの Office 365 サービスを使用するとき、シームレスなエクスペリエンスが可能になります。 詳細については、「[複数地域環境でのユーザー エクスペリエンス](multi-geo-user-experience.md)」を参照してください。

## <a name="onedrive"></a>OneDrive

各ユーザーの OneDrive は、ユーザーの PDL に従ってサテライトの場所でプロビジョニングされるか、または[管理者が移動させる](move-onedrive-between-geo-locations.md)ことができます。 個人用ファイルはその地域の場所に保存されますが、他の地域の場所にいるユーザーと共有することも可能です。

## <a name="sharepoint-sites-and-groups"></a>SharePoint サイトとグループ

複数地域機能の管理は、SharePoint管理センターから利用できます。 詳細な情報は[対応するブログ記事](https://techcommunity.microsoft.com/t5/Office-365-Blog/Now-available-Multi-Geo-in-SharePoint-and-Office-365-Groups/ba-p/263302)にあります。

ユーザーが SharePoint グループに接続されたサイトを作成する場合、サイトおよび関連付けられているグループ メールボックスが作成される地域の場所を決定するのに、PDL が使用されます。 (ユーザーの PDL 値が設定されていない場合、またはサテライトの場所として構成されていない地域の場所に設定されている場合、サイトとメールボックスは中央の場所に作成されます)。

Exchange、OneDrive、SharePoint 以外の Office 365 サービスは複数地域機能に対応していません。 ただし、これらのサービスによって作成された Office 365 グループには作成者の PDL がスタンプされ、Exchange グループ メールボックスと SharePoint O365 グループ サイトは対応する地域でプロビジョニングされます。 

## <a name="managing-the-multi-geo-environment"></a>複数地域環境の管理

複数地域環境の設定と管理は、SharePoint 管理センターで行います。 

![SharePoint 管理センターの [地域の場所] ページのスクリーン ショット](media/sharepoint-multi-geo-admin-center.png)

(SharePoint サイトや OneDrive サイトを移動するなど、一部の操作では Microsoft PowerShell が必要です。)

## <a name="see-also"></a>関連項目

[SharePointおよびOffice 365グループでの複数地域機能](https://techcommunity.microsoft.com/t5/Office-365-Blog/Now-available-Multi-Geo-in-SharePoint-and-Office-365-Groups/ba-p/263302)

[複数地域環境の管理](administering-a-multi-geo-environment.md)

[複数地域環境における SharePoint ストレージ クォータ](sharepoint-multi-geo-storage-quota.md)

[複数地域環境での Exchange Online メールボックスの管理](administering-exchange-online-multi-geo.md)
