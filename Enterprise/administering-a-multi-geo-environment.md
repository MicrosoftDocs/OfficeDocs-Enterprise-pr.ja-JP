---
title: 複数地域環境の管理
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 複数地域環境での SharePoint サービスおよび OneDrive サービスの管理について説明します。
ms.openlocfilehash: 596db0e2cffedc74a4840ae4427a3350ba1e27d8
ms.sourcegitcommit: a4322cac992ce64b92f0335bf005a7420195d9be
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="administering-a-multi-geo-environment"></a>複数地域環境の管理

ここでは、複数地域環境で OneDrive および SharePoint のサービスが動作するしくみについて説明します。

#### <a name="onedrive-administrator-experience"></a>OneDrive 管理者のエクスペリエンス

[OneDrive 管理センター](https://admin.onedrive.com)の左側のナビゲーションには、**[地域の場所]** タブがあります。このタブには、地域の場所の地図があり、地域の場所を確認および管理できます。

#### <a name="taxonomy"></a>分類

企業の中央の場所でホストされるマスターと共に、複数の地域の場所にわたるエンタープライズ管理メタデータに対する統一された[分類](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC)がサポートされています。中央の場所からグローバルな分類を管理し、サテライト地域の場所の分類には地域に固有の用語のみを追加することをお勧めします。グローバルな分類の用語は、サテライト地域の場所に同期されます。

#### <a name="sharing"></a>共有

管理者は、共有ポリシーを場所ごとに設定および管理できます。各地域の場所の OneDrive サイトは、対応する地域の共有設定のみを優先します (たとえば、中央の場所とサテライトの場所のどちらか一方に[外部共有](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85)を許可することができます)。共有の設定では、地域の場所間での共有の制限を構成できない点に注意してください。

OneDrive 複数地域では、共有の設定がテナント全体には同期されないため、地域の場所ごとに管理する必要があります。共有を管理するには、[OneDrive 管理センターの共有設定](https://admin.onedrive.com/?v=SharingSettings)ページに移動します。既定では、各サテライトの場所の全員に外部共有が有効化されています。

#### <a name="user-profile-application"></a>ユーザー プロファイル アプリケーション

各地域の場所ごとに、[ユーザー プロファイル アプリケーション](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723)があります。それぞれのユーザーのプロファイル情報は、それらのユーザーの地域の場所でホストされ、その場所の管理者が利用できます。

カスタムのプロファイル プロパティがある場合は、すべての地域で同じプロファイル スキーマを使用して、すべての地域の場所または必要な場所のどちらかにカスタムのプロファイル プロパティを設定します。ユーザー プロファイル データをプログラムによって設定する方法のガイダンスについては、「[SharePoint Online 用カスタム ユーザー プロファイル プロパティの一括更新用 API の概要](https://docs.microsoft.com/ja-JP/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online)」を参照してください。

#### <a name="bcs-secure-store-apps"></a>BCS、Secure Store、Apps

BCS、Secure Store、および Apps のすべてに、個別の地域インスタンスがあります。そのため、SharePoint Online 管理者は、これらのサービスが存在する各地域インスタンスから、そのサービスを管理および構成する必要があります。

#### <a name="security-and-compliance-admin-center"></a>セキュリティ/コンプライアンス管理センター

複数地域テナントには、[Office 365 セキュリティ/コンプライアンス センター](https://protection.office.com/?rfr=AdminCenter\#/homepage)という 1 つの中心的なコンプライアンス センターがあります。

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a>Information Protection (IP) データ損失防止 (DLP) ポリシー

セキュリティ/コンプライアンス センターでは、ポリシーの適用範囲をテナント全体または該当するユーザーに設定することで、OneDrive for Business の IP DLP ポリシーを設定できます。たとえば、サテライトの場所の OneDrive ユーザーのポリシーを選択する場合、特定の OneDrive に適用するポリシーを選択して、ユーザーの OneDrive の URL を入力します。DLP ポリシーの作成に関する一般的なガイダンスについては、「[データ損失防止ポリシーの概要](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e)」を参照してください。

DLP ポリシーは、そのポリシーの適用性に基づいて各地域の場所に自動的に同期されます。

地域の場所のすべてのユーザーに対する Information Protection ポリシーとデータ損失防止ポリシーの実装は、UI で使用可能なオプションではありません。その代わりに、ポリシーの適用が可能な OneDrive アカウントを選択するか、すべての OneDrive アカウントにグローバルにポリシーを適用する必要があります。

#### <a name="ediscovery"></a>電子情報開示 

既定では、複数地域テナントの電子情報開示マネージャーまたは管理者は、テナントの中央の場所でのみ電子情報開示を実施できます。サテライトの場所で電子情報開示を実施できるようにするために、"Region" という新しいコンプライアンス セキュリティ フィルター パラメーターが PowerShell で使用できます。

Office 365 全体管理者は、別のユーザーが電子情報開示を実行できるように電子情報開示マネージャーのアクセス許可を割り当てる必要があります。また、サテライトの場所として電子情報開示を実施する地域を指定するために該当するコンプライアンス セキュリティ フィルターで "Region" パラメーターを割り当てる必要があります。それ以外の場合は、サテライトの場所で電子情報開示は実施されません。

電子情報開示マネージャーまたは管理者の役割が特定の地域の場所に設定されている場合、電子情報開示マネージャーまたは管理者は、その地域の場所にある SharePoint サイトと OneDrive サイトに対してのみ電子情報開示の検索操作を実行できます。電子情報開示マネージャーまたは管理者が、指定の地域外の SharePoint サイトまたは OneDrive サイトを検索しようとしても結果は返されません。さらに、ある地域の電子情報開示マネージャーまたは管理者がエクスポートをトリガーすると、データは、その地域の Azure インスタンスにエクスポートされます。制御された境界を越えたコンテンツのエクスポートが許可されなくなることで、これが組織のコンプライアンスの維持に役立ちます。

> [!NOTE]
> 電子情報開示マネージャーが複数の SharePoint 地域全体で検索する必要がない場合は、OneDrive サイトまたは SharePoint サイトがある別の地域を指定する電子情報開示マネージャー用の別のユーザー アカウントを作成する必要があります。

<table>
<thead>
<tr class="header">
<th align="left"><strong>複数地域でサポートされる地域の場所</strong></th>
<th align="left"><strong>SharePoint でエクスポートされた電子情報開示データが存在する Azure Blob データの場所</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><strong>NAM</strong></td>
<td align="left">米国のデータ センター</td>
</tr>
<tr class="even">
<td align="left"><strong>EUR</strong></td>
<td align="left">ヨーロッパのデータ センター</td>
</tr>
<tr class="odd">
<td align="left"><strong>APC</strong></td>
<td align="left">東南アジアまたは東アジアのデータ センター</td>
</tr>
<tr class="even">
<td align="left"><strong>CAN</strong></td>
<td align="left">米国のデータ センター</td>
</tr>
<tr class="odd">
<td align="left"><strong>AUS</strong></td>
<td align="left">東南アジアまたは東アジアのデータ センター</td>
</tr>
<tr class="even">
<td align="left"><strong>KOR</strong></td>
<td align="left">テナントの既定のデータの場所</td>
</tr>
<tr class="odd">
<td align="left"><strong>GBR</strong></td>
<td align="left">ヨーロッパのデータ センター</td>
</tr>
<tr class="even">
<td align="left"><strong>JPN </strong></td>
<td align="left">東南アジアまたは東アジアのデータ センター</td>
</tr>
</tbody>
</table>

地域のコンプライアンス セキュリティ フィルターを設定するには:

1.  Windows PowerShell を開きます。

2.  次のように入力します  
    $s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)

    $a = Import-PSSession $s -AllowClobber  

3.  **New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName

    例: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com

追加のパラメーターと構文については、「[New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx)」の記事を参照してください。

#### <a name="audit-log-search"></a>監査ログ検索

すべての地域の場所に対して統一された[監査ログ](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c)は、Office 365 の監査ログの検索ページから利用できます。すべての地域からの監査ログのエントリを参照できます。たとえば、NAM 地域と EUR 地域のユーザーのアクティビティが、1 つの組織ビューに表示され、既存のフィルターを適用することで特定のユーザーのアクティビティを確認できます。
