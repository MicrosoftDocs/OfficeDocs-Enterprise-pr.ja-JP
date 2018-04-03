---
title: ビジネスの複数の地域の OneDrive の計画
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: ビジネスの複数の地域、複数地域のしくみ、およびどのような地域の場所は、データ ストレージに使用できるは、OneDrive について説明します。
ms.openlocfilehash: 22ba0f4ebc3fb3c4e11bc0386a1479fa6a889ad8
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/03/2018
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a>ビジネスの複数の地域の OneDrive の計画

このガイドは、SharePoint Online のテナント データの常駐サービスの要件を満たすために会社の存在に基づいてその他の地域に展開する準備をしている多国籍企業 (MNCs) の管理者向けです。

OneDrive の複数の地域の設定を Office 365 テナントの中央の場所 (既定の場所とも呼ばれます) と 1 つまたは複数のサテライト地域の場所で構成されます。これは、複数の地域の拠点にまたがる単一のテナントです。OneDrive 複数の地域では、テナントについては、地域を含むには、Azure Active Directory (AAD) ではマスターです。 

構成の基本的な概念を理解するのに役立ついくつかのキーの複数地域用語を以下に示します。

-   **テナント**– 通常、それに関連付けられている 1 つまたは複数のドメインには、Office 365 の雲の中の組織の形式 (たとえば、 http://contoso.sharepoint.com)。 

-   **Geo の場所**テナントのデータをホストしている地理的な場所です。テナントの複数地域にまたがる複数の地域の場所、北アメリカやヨーロッパなどの。

-   **許可されるデータの場所 (ADL)** – geo の場所を OneDrive と SharePoint のデータをホストする、テナントが構成されています。

-   **優先データの場所 (PDL)** – 個々 のユーザーの OneDrive のデータが保存されている地域の場所です。テナントに対して構成されている許可されるデータの場所のいずれかを管理者が設定できます。OneDrive サイトを既に持っているユーザーは PDL を変更する場合、OneDrive のデータは地域の別の場所に自動的に移動されませんに注意してください。詳細については、[別の地理的な場所に OneDrive ライブラリを移動](move-onedrive-between-geo-locations.md)を参照してください。

複数地域を有効にするには、4 つの主要手順を実行する必要があります。

1.  _Office 365 の機能を複数の地域_のサービス プランを追加するのには、アカウント ・ チームと協力します。

2.  目的の地域の場所の衛星し、テナントに追加を選択します。

3.  必要なサテライト地域の場所に、ユーザーの希望するデータの場所を設定します。ユーザーの新しい OneDrive サイトを準備すると、ときに、PDL にプロビジョニングされます。

4.  ホームの場所から、ユーザーの既存の OneDrive サイトを必要に応じて、希望するデータの場所に移行します。

これらの各手順の詳細については[OneDrive を構成する複数の地域のビジネス](multi-geo-tenant-configuration.md)を参照してください。

> [!IMPORTANT]
> Office 365 の複数の地域の機能は、パフォーマンスの最適化の場合に設計されていないデータの常駐サービスの要件を満たすよう設計されていますが、注意してください。Office 365 のパフォーマンスを最適化する方法については、[ネットワークの計画と Office 365 のパフォーマンスの調整](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848)を参照するか、サポート グループに問い合わせてください。

OneDrive ファイルをホストしているサテライト地域の場所にするのには、次の場所のいずれかを設定できます。複数地域のことを計画する際、Office 365 テナントに追加する場所の一覧を確認します。お勧め 1 つまたは 2 つのサテライト オフィスで始まると、複数の地域の場所に徐々 に拡張が必要な場合です。

<table>
<thead>
<tr class="header">
<th align="left"><strong>場所</strong></th>
<th align="left"><strong>コード</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">アジア太平洋</td>
<td align="left">APC</td>
</tr>
<tr class="even">
<td align="left">ヨーロッパ東中央//アフリカ</td>
<td align="left">EUR</td>
</tr>
<tr class="odd">
<td align="left">北アメリカ</td>
<td align="left">名</td>
</tr>
<tr class="even">
<td align="left">オーストラリア</td>
<td align="left">オーストラリア</td>
</tr>
<tr class="odd">
<td align="left">カナダ</td>
<td align="left">できます。</td>
</tr>
<tr class="odd">
<td align="left">日本</td>
<td align="left">日本語版</td>
</tr>
<tr class="even">
<td align="left">韓国</td>
<td align="left">KOR</td>
</tr>
<tr class="odd">
<td align="left">英国</td>
<td align="left">GBR</td>
</tr>
</tbody>
</table>

今後提供予定の地理的な場所:
  
- フランス
- インド

複数地域を構成する場合は、Office 365 に移行するときに、オンプレミス インフラストラクチャを統合する機会を活用して検討してください。など、シンガポールとマレーシアでの設置のファームがあれば、しを統合できますに APC のサテライトの場所に常駐要件のデータを許可するよう指定しました。

## <a name="best-practices"></a>ベスト プラクティス

初期テストを実行するのには Office 365 では、テスト ユーザーを作成することをお勧めします。みましょういくつかのテストと検証の手順をこのユーザーに OneDrive の複数の地域の機能をオンボードの運用環境のユーザーに続行する前にします。

テスト ユーザーでテストが完了したら、おそらく最初に新規の地理的な場所で OneDrive を使用する: IT 部門から、パイロット グループを選択します。この最初のグループ、OneDrive を所有していないユーザーを選択します。この最初のグループ内の 5 つまでの人をお勧めしてバッチ処理の展開方法を段階的に展開します。

各ユーザーには、*希望するデータの場所*(PDL)、OneDrive を提供する地域の場所に Office 365 を判断できますように設定が必要です。ユーザーの希望するデータの場所を選択したサテライトの場所や、中央の場所のいずれかに一致しなければなりません。PDL のフィールドは必須ではありませんが、PDL は、すべてのユーザーに対して設定することをお勧めします。PDL のないユーザーの作業負荷は複数地域のロジックに基づいて、中央の場所で準備します。   

ユーザーのリストを作成し、ユーザー プリンシパル名 (UPN) および適切な優先データの場所の場所のコードが含まれます。まず、テスト ユーザーと、初期のパイロットのグループが含まれます。構成手順については、このリストする必要があります。

Azure Active Directory (AAD) に、ユーザーがオンプレミスの Active Directory (AD) システムから同期する場合は、Azure Active Directory の接続を使用して同期されたユーザーの希望するデータの場所を設定する必要があります。直接 Azure AD PowerShell を使用して同期のユーザーの希望するデータの場所を構成することはできません。AD の PDL の設定し、同期する手順は、「 [Azure Active Directory 接続の同期: Office 365 リソースの優先データのパスを構成する](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)です。

複数地域のテナントの管理とは異なる多くの SharePoint と OneDrive の設定として、複数地域ではないテナントとサービスは、複数の地域に注意してください。確認すること[、複数地域の環境を管理する](administering-a-multi-geo-environment.md)構成を続行する前にすることをお勧めします。

複数地域の環境で、ユーザーのエクスペリエンスの詳細について[multgeo 環境で発生するユーザー](multi-geo-user-experience.md)を参照してください。

OneDrive を構成する複数の地域のビジネスを始めるには、 [OneDrive を構成する複数の地域のビジネス](multi-geo-tenant-configuration.md)を参照してください。

構成が完了したらに注意して[、ユーザーの OneDrive ライブラリを移行](move-onedrive-between-geo-locations.md)するのには、希望するデータの場所からユーザーを取得する必要があります。
