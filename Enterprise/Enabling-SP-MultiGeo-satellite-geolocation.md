---
title: サテライト地域で SharePoint Multi-Geo の有効化
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Normal
description: この記事では、グローバルまたは SharePoint 管理者向けに、サテライトの地理的な場所で SharePoint の複数地域を有効にする方法について説明します。
ms.openlocfilehash: dc2cd3eeb4c7e74d8dbfee1070338e0e243b0519
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605853"
---
# <a name="enabling-sharepoint-multi-geo-in-your-satellite-geo-location"></a>サテライト地域で SharePoint Multi-Geo の有効化

この記事は、2019 年 3 月 27日に SharePoint Multi-Geo の機能が一般的に利用できるようになる**前に**、Multi-Geo のサテライト地域を作成した Global または SharePoint の管理者、およびサテライト地域で SharePoint Multi-Geo を有効にしていないユーザー向けのものです。 

>[!Note]
>**3 月 27日以降**に新しい地域を追加した場合、OneDrive と SharePoint Multi-Geo でその新しい地域がすでに有効になっていれば、以下の手順を実行する必要はありません。

以下の手順により、ユーザーのサテライト地域で SharePoint を有効にできるため、Multi-Geo サテライト ユーザーは O365 で、OneDrive と SharePoint Multi-Geo 両方の機能を利用できるようになります。 

>[!IMPORTANT]
>これは有効化の方法の 1 つであることに注意してください。 SPO モードを設定したら、サポートによるエスカレーションなしでテナントを OneDrive の Multi-Geo モードに戻すことだけはできません。 

## <a name="to-set-a-geo-location-into-spo-mode"></a>SPO モードに地域を設定するには

SPO モードに地域を設定するには、SPO モードで設定する地域に接続します。

1.    SharePoint Online 管理シェルを開く 
2.    Connect-SPOService -URL "https://$tenantGeo-admin.sharepoint.com" -Credential $credential
3.    Set-SPOMultiGeoExperience</br></br>
![Set-SPOMultiGeoExperience](media/Set-SPO-MultiGeo.jpg)
4.    この操作は通常 1 時間程度かかり、その間、サービス内でさまざまな発行バックを実行し、テナントに再度スタンプを付けます。 少なくとも 1 時間後に Get-SPOMultiGeoExperience を実行してください。  実行すると、SPO モードにこの地域があるかどうかが表示されます。</br></br>
![Set-SPOMultiGeoExperience](media/Get-SPO-MultiGeo.jpg)

 
 
 
>[!Note]
>サービスの特定のキャッシュは 24 時間ごとに更新するため、最大で 24 時間、ODB モードのままであるかのように、サテライト地域が断続的に動作する可能性があります。 この動作により技術的な問題が発生することはありません。 
 
SharePoint Multi-Geo に関する詳細については [aka.ms/sharepointmultigeo](https://docs.microsoft.com/office365/enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365) を参照してください。


