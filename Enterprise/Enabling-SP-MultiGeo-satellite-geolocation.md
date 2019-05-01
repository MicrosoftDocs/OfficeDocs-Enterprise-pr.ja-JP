---
title: サテライト地域で SharePoint Multi-Geo の有効化
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: サテライト地域で SharePoint Multi-Geo を有効にします。
ms.openlocfilehash: 98666f76a5b3ec055a6f26d30f502c3cc6b6d3bb
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487877"
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

1.  SharePoint Online 管理シェルを開く 
2.  Connect-SPOService -URL "https://$tenantGeo-admin.sharepoint.com" -Credential $credential
3.  Set-SPOMultiGeoExperience</br></br>
![Set-SPOMultiGeoExperience](media/Set-SPO-MultiGeo.jpg)
4.  この操作は通常 1 時間程度かかり、その間、サービス内でさまざまな発行バックを実行し、テナントに再度スタンプを付けます。 少なくとも 1 時間後に Get-SPOMultiGeoExperience を実行してください。  実行すると、SPO モードにこの地域があるかどうかが表示されます。</br></br>
![Set-SPOMultiGeoExperience](media/Get-SPO-MultiGeo.jpg)

 
 
 
>[!Note]
>サービスの特定のキャッシュは 24 時間ごとに更新するため、最大で 24 時間、ODB モードのままであるかのように、サテライト地域が断続的に動作する可能性があります。 この動作により技術的な問題が発生することはありません。 
 
SharePoint Multi-Geo に関する詳細については [aka.ms/sharepointmultigeo](https://docs.microsoft.com/ja-JP/office365/enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365) を参照してください。


