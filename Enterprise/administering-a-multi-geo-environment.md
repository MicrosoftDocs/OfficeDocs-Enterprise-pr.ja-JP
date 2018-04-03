---
title: 複数地域の環境を管理します。
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: マルチ geo 環境で SharePoint と OneDrive のサービスの管理について説明します。
ms.openlocfilehash: f49cf35503ee6495b5982dc7d72f9b1936f564c6
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/03/2018
---
# <a name="administering-a-multi-geo-environment"></a>複数地域の環境を管理します。

OneDrive と SharePoint のサービスが複数地域環境で作業する方法を見てです。

#### <a name="onedrive-administrator-experience"></a>OneDrive 管理者の経験

[OneDrive 管理センター](https://admin.onedrive.com)では、左側のナビゲーション機能 geo の場所にマップを表示し、地域、サイトの管理の**Geo の場所**] タブがあります。地域、テナントの場所を追加、削除するには、このページを使用します。

#### <a name="taxonomy"></a>分類

サポート統一された[分類](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC)管理エンタープライズ メタデータの地域拠点には、会社の中央の場所でホストされているマスターとします。中央の場所から、グローバルの分類を管理し、サテライト地域場所の分類にのみの場所に固有の用語を追加することをお勧めします。グローバル分類の用語は、サテライトの地域の場所に同期されます。

#### <a name="sharing"></a>共有

管理者が設定し、それぞれの場所の共有ポリシーを管理できます。各地域拠点の OneDrive サイトには、のみ、対応する地域特定共有の設定を優先します。たとえば、ことができます[外部共有](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85)用ではなく、サテライトの場所またはその逆の場合ですが、中央の場所です。OneDrive の複数の地域、テナント間でこれらが同期するいないと、各地域の拠点で、共有の設定を管理する必要があります。

共有のアクセス、 [OneDrive 管理センターの共有の設定](https://admin.onedrive.com/?v=SharingSettings)] ページを管理します。既定で外部の共有は各サテライト サイト内の全員が有効になります。

#### <a name="user-profile-application"></a>ユーザー プロファイル アプリケーション

各地域拠点では、[ユーザー プロファイル アプリケーション](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723)を使用です。各ユーザーのプロファイル情報は、geo の場所とその地域の場所の管理者に使用可能なホストされています。

カスタム プロファイルのプロパティがある場合同じプロファイル スキーマを使用して、地理的に分散し、地域のすべての場所のいずれか、カスタム プロファイル プロパティを設定することを推奨し、または必要な場所です。

#### <a name="bcs-secure-store-apps"></a>BCS では、セキュリティで保護されたストアは、アプリケーション

BCS、セキュリティで保護されたストアおよびアプリケーションは、別の地域のインスタンスを持つ、したがって SharePoint Online の管理者が管理し、必要な場所に存在する各地理インスタンスからこれらのサービスを構成する必要があります。

#### <a name="security-and-compliance-admin-center"></a>セキュリティおよびコンプライアンス管理センター

複数地域のテナントの 1 つの中心的なコンプライアンス センターがある: [Office 365 のセキュリティとコンプライアンスの中心](https://protection.office.com/?rfr=AdminCenter\#/homepage)です。

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a>情報 (IP) の保護データの損失防止 (DLP) のポリシー

ポリシーを設定できます、IP DLP OneDrive ビジネスのためのセキュリティとコンプライアンス ・ センターの全体のテナントまたは該当するユーザーに必要なポリシーのスコープの設定です。たとえば:、サテライトの場所に OneDrive のユーザーのポリシーを選択するには、特定の OneDrive にポリシーを適用し、ユーザー名を入力する場合に選択の OneDrive の url です。DLP ポリシーを作成する一般的な方法については、[データ損失防止ポリシーの概要](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e)を参照してください。

DLP ポリシーは、各地域の場所に適用性に基づいて自動的に同期されます。

地域の場所にすべてのユーザー情報の保護とデータ損失の防止ポリシーを実装することは、UI で使用可能なオプションではありませんが、代わりに、ポリシーの適用可能な OneDrive のアカウントを選択してか OneDrive のすべてのアカウントをグローバルにポリシーを適用する必要があります。

#### <a name="ediscovery"></a>電子情報開示 

既定では、マネージャーまたは多地域のテナントの管理者、電子的証拠開示は、テナントの中央の場所にのみ電子的証拠開示を行うことが可能になります。サテライト オフィスの電子的証拠開示を実施する機能をサポートするために「領域」と呼ばれる新しいコンプライアンス セキュリティ フィルター パラメーターは、PowerShell を使用して利用可能です。

Office 365 のグローバル管理者は、電子的証拠開示を実行し、サテライトとして電子的証拠開示を実施するための領域を指定するのには、適用可能なコンプライアンス セキュリティ フィルターで「地域」パラメーターを指定するようにするのには、電子的証拠開示マネージャーのアクセス許可を割り当てる必要があります。場所、それ以外の場合サテライトの場所に電子的証拠開示が実行されるなし。

特定の地域の場所を電子的証拠開示マネージャー ロールまたは管理者ロールを設定すると、マネージャーまたは管理者、電子的証拠開示のみできるようになります、SharePoint サイトとその地理的な場所にある OneDrive サイトに対して電子的証拠開示検索の操作を実行します。電子的証拠開示マネージャーまたは管理者は、指定した領域の外側の SharePoint または OneDrive サイトの検索を試みると、結果は返されません。また、電子的証拠開示マネージャーまたは管理者の領域には、エクスポートがトリガーされた場合は、その地域の Azure のインスタンスにデータがエクスポートされます。これにより、組織を対象となるコントロールの境界線の間でコンテンツを許可しないことによって、コンプライアンスを維持します。

> [!NOTE]
> 電子的証拠開示マネージャーが複数の SharePoint の領域全体を検索するために必要な場合は、別のユーザー アカウントは、電子的証拠開示マネージャー、OneDrive または SharePoint サイトが配置されている別の領域を指定するために作成する必要があります。

<table>
<thead>
<tr class="header">
<th align="left"><strong>複数地域は、地域の場所をサポートします。</strong></th>
<th align="left"><strong>SharePoint にエクスポートされたデータの電子的証拠開示は、この Azure Blob データの場所になります.</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><strong>名</strong></td>
<td align="left">米国のデータ ・ センター</td>
</tr>
<tr class="even">
<td align="left"><strong>EUR</strong></td>
<td align="left">ヨーロッパのデータ ・ センター</td>
</tr>
<tr class="odd">
<td align="left"><strong>APC</strong></td>
<td align="left">東の南または東アジアのデータ ・ センター</td>
</tr>
<tr class="even">
<td align="left"><strong>できます。</strong></td>
<td align="left">米国のデータ ・ センター</td>
</tr>
<tr class="odd">
<td align="left"><strong>オーストラリア</strong></td>
<td align="left">東の南または東アジアのデータ ・ センター</td>
</tr>
<tr class="even">
<td align="left"><strong>KOR</strong></td>
<td align="left">テナントの既定のデータの場所</td>
</tr>
<tr class="odd">
<td align="left"><strong>GBR</strong></td>
<td align="left">ヨーロッパのデータ ・ センター</td>
</tr>
<tr class="even">
<td align="left"><strong>日本語版</strong></td>
<td align="left">東の南または東アジアのデータ ・ センター</td>
</tr>
</tbody>
</table>

地域のコンプライアンス ・ セキュリティ ・ フィルターを設定します。

1.  開いている Windows PowerShell の

2.  「  
    $s = Microsoft.Exchange を新規 PSSession ConfigurationName ConnectionUri - <https://ps.compliance.protection.outlook.com/powershell-liveid> -$cred に資格情報の AllowRedirection では基本認証-SessionOption (新規 PSSessionOption SkipCACheck-サーバー-SkipRevocationCheck)

    $を = $s のインポート-PSSession AllowClobber  

3.  **新しい-ComplianceSecurityFilter****-アクション**すべて**のフィルター名**EnterTheNameYouWantToAssign **-地域**EnterTheRegionParameter **-ユーザー** EnterTheUserPrincipalName

    例を示します**ComplianceSecurityFilter で新しい-アクション**すべて**のフィルター名**NAMEDISCOVERYMANAGERS **-地域**名**・ ユーザー** adwood@contosodemosx.onmicrosoft.com。

[新規 ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx)この資料は、追加のパラメーターと構文を参照してください。

#### <a name="audit-log-search"></a>監査ログ検索

統一された[監査ログ](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c)のすべての地域の場所に、Office 365 の監査ログの検索ページから利用可能です。地域全体からのすべての監査ログ エントリを表示できます、やなどの名と EUR 地域ユーザーの活動は、組織の 1 つのビューに表示し、特定のユーザーの活動を確認する既存のフィルターを適用できます。
