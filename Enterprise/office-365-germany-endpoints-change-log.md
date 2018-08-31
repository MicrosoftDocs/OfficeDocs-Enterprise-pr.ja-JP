---
title: Office 365 のドイツのエンドポイントを変更するログ
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/13/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid: MOE150
ms.assetid: 980041c9-7984-44b2-95f0-af66743543a1
ms.openlocfilehash: e77d6fc3b8136f39ed75ef21b0ff417a4ad6465a
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541750"
---
# <a name="office-365-germany-endpoints-change-log"></a>Office 365 のドイツのエンドポイントを変更するログ

*Office 365 の管理者用に適用されます。*

## <a name="list-of-changes-to-the-endpoints-required-for-office-365-germany"></a>Office 365 のドイツのために必要なエンドポイントへの変更の一覧

次の表に、 [Office 365 のドイツのエンドポイント](office-365-germany-endpoints.md)への変更を示します。
  
|**日付**|**変更**|
|:-----|:-----|
|1/24/2017  <br/> |資料の最初の文書です。  <br/> |
|2017/2/28  <br/> |3 Fqdn を追加します。1/[効果的な 4/1/2017。必須: Office 365 ポータルと共有します。ExpressRoute: いいえwww.office.de]、2/[効果的な 4/1/2017。必須: Office 365 ポータルと共有します。ExpressRoute: いいえoffice.de] では、3/[効果的な 4/1/2017。必須: Office 365 ポータルと共有します。ExpressRoute: いいえofficehome.msocdn.de]. メモ: を追加する追加ポータルの Fqdn; 2 つの IP_Sets を追加します。。1/[効果的な 4/1/2017。必須: Office 365 ポータルと共有します。ExpressRoute: いいえ 51.5.245.67/32] 2、または [有効な 4/1/2017。必須: Office 365 ポータルと共有します。ExpressRoute: いいえ 51.4.227.178/32]。メモ: は、ポータルの追加のエンドポイントを追加します。2 IP_Sets を追加します。1/[効果的な 4/1/2017。必須: Office 365 ポータルと共有します。ExpressRoute: いいえ 2a01:4180:2001::92] 2、または [有効な 4/1/2017。必須: Office 365 ポータルと共有します。ExpressRoute: 2a01:4180:2401::11f の [いいえ] です。メモ: は、ポータルの追加のエンドポイントを追加します。  <br/> |
|2017/3/8  <br/> |1 Fqdn; を追加します。1/[効果的な 3/8/2017。ビジネスの必要な: OneDrive。ExpressRoute: いいえspoprod-a.akamaihd.net] をします。メモ: を追加すると、CDN エンドポイントを追加します。  <br/> |
|3/31/2017  <br/> |3 Fqdn を追加します。1/[効果的な 5/1/2017。: 必須の SharePoint オンライン ハイブリッド。\*です。 search.production.de.azuretrafficmanager.de] 2、または [有効な 5/1/2017。: 必須の SharePoint オンライン ハイブリッド。login.microsoftonline.de] では、3/[効果的な 5/1/2017。: 必須の SharePoint オンライン ハイブリッド。provisioningapi.microsoftonline.de]. メモ: 追加の Sharepoint のハイブリッドの Fqdn です。  <br/> |
|2017/6/1  <br/> |2 つの Fqdn を追加する効果的な 7/1、2017  <br/> shellprod.msocdn.de  <br/> r1.res.office365.com  <br/> |
|2017/6/26  <br/> |自動検出を交換してください\*です。 Autodiscover.outlook.de と自動検出 outlook.office.de と outlook.de。  <br/> |
|2017/9/29  <br/> |3 Fqdn を追加します。1/[効果的な 11/1/2017。  <br/> cegsignup.microsoft.de  <br/> negsignup.microsoft.de  <br/> \*。 svc.ms  <br/> |
|2018/1/16  <br/> |1 Fqdn; を追加します。1/[効果的な 2/1/2018。Office 365 ポータルの: が必要です。ExpressRoute: いいえwebshell.suite.office.de]. メモ: スイートのシェルを Office 365 に追加の FQDN を追加します。4 IP_Sets を追加します。1/[効果的な 2/1/2018。Office 365 ポータルの: が必要です。ExpressRoute: いいえ 51.5.242.163/32] 2、または [有効な 2/1/2018。Office 365 ポータルの: が必要です。ExpressRoute: いいえ 51.4.226.115/32] 3、または [有効な 2/1/2018。Office 365 ポータルの: が必要です。ExpressRoute: いいえ 2a01:4180:2401::33b/4/[効果的な 2/1/2018。Office 365 ポータルの: が必要です。ExpressRoute: いいえ 2a01:4180:2001::234/メモ: スイートのシェルを Office 365 に追加の IP アドレスを追加します。  <br/> |
|2018/2/5  <br/> |1 FQDN を追加する; 1/[効果的な 3/1/2018。: に必要なポータルと共有します。ExpressRoute: はい。webshell.suite.office.de]. メモ: ポータルと共有の Fqdn です; 2 つの IP_Sets を追加する URL を追加する。1/[効果的な 3/1/2018。: に必要なポータルと共有します。ExpressRoute: はい。51.5.242.163/32]. 2、または [有効な 3/1/2018。: に必要なポータルと共有します。ExpressRoute: はい。51.4.226.115/32]。メモ: 追加の新しいポータルの前にされ、共有されます。2 IP_Sets を追加します。1/[効果的な 3/1/2018。: に必要なポータルと共有します。ExpressRoute: はい。2a01:4180:2401::33b × 128]. 2、または [有効な 3/1/2018。: に必要なポータルと共有します。ExpressRoute: はい。2a01:4180:2001::234/128]。メモ: 追加の新しいポータルの前にされ、共有されます。1 IP_Sets を追加します。1/[効果的な 3/1/2018。必要です。 Office オンライン。ExpressRoute: はい。51.18.16.0/23]。事項では、Office オンラインの新しいプレフィックスを追加します。  <br/> |
|3/15/2018  <br/> |1 IP_Set を追加します。1/[効果的な 4/15/2018。必須: Office 365 用リソースです。ExpressRoute: いいえ 51.18.0.0/21]。メモ: は、Office 365 用リソースのエンドポイントを追加します。  <br/> |
|2018/7/2  <br/> |1 FQDN を削除しています。1/[効果的な 8/1/2018。ビジネスの必要な: OneDrive。ExpressRoute: いいえlogin.microsoftonline.de]. メモ: ビジネス エンドポイントの OneDrive を削除します。11 Fqdn を削除しています。1/[効果的な 8/1/2018。必要です。 Office のモバイル。ExpressRoute: いいえhttps://excelps.osi.office.de/exlps/excelprint.svc/exlPrint] 2、または [有効な 8/1/2018。必要です。 Office のモバイル。ExpressRoute: いいえhttps://wordps.osi.office.de/wrdps/wordprint.svc/wrdprint] 3、または [有効な 8/1/2018。必要です。 Office のモバイル。ExpressRoute: いいえhttps://wordcs.osi.office.de/wordauto/wordautomation.svc/wordautomation] 4、または [有効な 8/1/2018。必要です。 Office のモバイル。ExpressRoute: いいえhttps://wordcs.osi.office.de/wordauto/wordautomation.svc/rest] 5、または [有効な 8/1/2018。必要です。 Office のモバイル。ExpressRoute: いいえhttps://pptps.osi.office.de/pptps/powerpointprint.svc/PptPrint] 6、または [有効な 8/1/2018。必要です。 Office のモバイル。ExpressRoute: いいえhttps://pptcs.osi.office.de/pptauto/PowerpointAutomation.svc/PptAutomation] 7、または [有効な 8/1/2018。必要です。 Office のモバイル。ExpressRoute: いいえhttps://pptcs.osi.office.de/pptauto/PowerpointAutomation.svc/rest] 8、または [有効な 8/1/2018。必要です。 Office のモバイル。ExpressRoute: いいえhttps://ols.osi.office.de/] 9、または [有効な 8/1/2018。必要です。 Office のモバイル。ExpressRoute: いいえhttps://ols.osi.office.de/olsc/OlsClient.svc/OlsClient] 10、または [有効な 8/1/2018。必要です。 Office のモバイル。ExpressRoute: いいえhttps://excelcs.osi.office.de/xlauto/excelautomation.svc/XlAutomation] 11、または [有効な 8/1/2018。必要です。 Office のモバイル。ExpressRoute: いいえhttps://excelcs.osi.office.de/xlauto/excelautomation.svc/rest]。メモ: は、Office のモバイルのエンドポイントを削除しています。  <br/> |
   

