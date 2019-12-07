---
title: ゲストと共同でドキュメントの作業をする
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
ms.collection: SPO_Content
localization_priority: Normal
description: SharePoint および OneDrive のドキュメントでゲストと共同作業する方法について説明します。
ms.openlocfilehash: 20b97ed6e232385500e74adcaa11378252167c26
ms.sourcegitcommit: 7e65640fb1a86858a95c9ef0edbb58d0f171c5ee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/06/2019
ms.locfileid: "39886496"
---
# <a name="collaborate-with-guests-on-a-document"></a>ゲストと共同でドキュメントの作業をする

SharePoint または OneDrive のドキュメントでゲストと共同作業を行う必要がある場合は、ドキュメントへの共有リンクを送信することができます。 この記事では、組織のニーズに合わせて SharePoint と OneDrive の共有リンクを設定するために必要な、Microsoft 365 の構成手順について説明します。

## <a name="video-demonstration"></a>ビデオ デモンストレーション

このビデオでは、このドキュメントで説明されている構成手順を示します。</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE450Vt?autoplay=false]

## <a name="azure-organizational-relationships-settings"></a>Azure の組織上の関係の設定

Microsoft 365 での共有は、Azure Active Directory の組織上の関係の設定によって最上位レベルで管理されます。 Azure AD でゲストの共有が無効または制限されている場合、これは Microsoft 365 で構成した共有設定よりも優先されます。

組織上の関係の設定を確認して、ゲストとの共有がブロックされないようにしてください。

![Azure Active Directory における組織の関係の設定ページのスクリーンショット](media/azure-ad-organizational-relationships-settings.png)

組織上の関係の設定を設定するには

1. Microsoft Azure にログイン[https://portal.azure.com](https://portal.azure.com)します。
2. 左側のナビゲーションで、[ **Azure Active Directory**] をクリックします。
3. [**概要**] ウィンドウで、[組織上の**関係**] をクリックします。
4. [組織上の**関係**] ウィンドウで、[**設定**] をクリックします。
5. **管理者とゲスト招待元役割のユーザーが招待できる**ことと、**メンバーが招待**できることを確認します。どちらも **[はい]** に設定されています。
6. 変更を加えた場合は、[**保存**] をクリックします。

[**共同作業の制限**] セクションの設定に注意してください。 共同作業を行うゲストのドメインがブロックされていないことを確認します。

## <a name="sharepoint-organization-level-sharing-settings"></a>SharePoint 組織レベルの共有設定

ゲストが SharePoint または OneDrive のドキュメントにアクセスできるようにするには、SharePoint および OneDrive の組織レベルの共有設定でゲストとの共有が許可されている必要があります。

SharePoint の組織レベルの設定により、個々の SharePoint サイトで使用できる設定が決定されます。 サイトの設定は、組織レベルの設定よりも制限することはできません。 OneDrive の組織レベルの設定により、ユーザーの OneDrive ライブラリで利用可能な共有のレベルが決定されます。

SharePoint と OneDrive の場合は、認証されていないファイルとフォルダーの共有を許可する場合は、[**すべて**] を選択します。 すべてのゲストが認証を必要とするようにするには、[**新規および既存のゲスト**] を選択します。 *[すべてのユーザー]* リンクは、最も簡単な共有方法です。ゲストは認証なしでリンクを開くことができ、そのリンクを他のユーザーに自由に渡すことができます。

SharePoint の場合は、組織内のすべてのサイトで必要とされる最も寛容な設定を選択します。

![SharePoint 組織レベルの共有設定のスクリーンショット](media/sharepoint-organization-external-sharing-controls.png)


SharePoint 組織レベルの共有設定を設定するには

1. Microsoft 365 管理センターで、左側のナビゲーションの [**管理センター**] の下にある [ **SharePoint**] をクリックします。
2. SharePoint 管理センターの左側のナビゲーションで、[**共有**] をクリックします。
3. SharePoint または OneDrive の外部共有が [すべての**ユーザー** ] または **[既存のゲスト**] に設定されていることを確認します。 (OneDrive の設定は、SharePoint の設定よりも制限がないことに注意してください)。
4. 変更を加えた場合は、[**保存**] をクリックします。

## <a name="sharepoint-organization-level-default-link-settings"></a>SharePoint 組織レベルの既定のリンク設定

既定のファイルとフォルダーのリンク設定によって、ユーザーがファイルまたはフォルダーを共有するときに、どのリンクオプションが既定で表示されるかが決まります。 ユーザーは、必要に応じて、共有する前に、リンクの種類を他のオプションのいずれかに変更できます。

この設定は、組織内の SharePoint サイトや OneDrive に影響を与えることに注意してください。

ユーザーがファイルやフォルダーを共有するときに既定で選択されるリンクの種類を選択します。

- **リンクを持つすべてのユーザー** -認証されていないファイルとフォルダーの共有が頻繁に行われるようにする場合は、このオプションを選択します。 *すべて*のリンクを許可し、偶発的な認証されていない共有について懸念している場合は、他のオプションのいずれかを既定値として検討します。 このリンクの種類は、**すべて**の共有を有効にした場合にのみ使用できます。
- [**組織内のユーザーのみ**]-ほとんどのファイルとフォルダーの共有が組織内のユーザーと想定される場合は、このオプションを選択します。
- **特定のユーザー** -多数のファイルとフォルダーをゲストで共有することが予想される場合は、このオプションを検討してください。 この種類のリンクはゲストと連動しており、認証を必要とします。
 
![SharePoint における組織レベルのファイルとフォルダー設定のスクリーンショット](media/sharepoint-organization-files-folders-sharing-settings.png)


SharePoint と OneDrive の組織レベルの既定のリンク設定を設定するには

1. SharePoint 管理センターの [共有] ページに移動します。
2. [**ファイルとフォルダーのリンク**] で、使用する既定の共有リンクを選択します。
3. 変更を加えた場合は、[**保存**] をクリックします。

## <a name="sharepoint-site-level-sharing-settings"></a>SharePoint サイトレベルの共有設定

SharePoint サイトにあるファイルや dler を共有している場合は、そのサイトのサイトレベルでの共有設定も確認する必要があります。

![SharePoint サイトの外部共有設定のスクリーンショット](media/sharepoint-site-external-sharing-settings.png)

サイトレベルの共有設定を設定するには
1. SharePoint 管理センターの左側のナビゲーションで、[**サイト**] を展開して [**アクティブなサイト**] をクリックします。
2. 作成したサイトを選択します。
3. リボンで [**共有**] をクリックします。
4. 共有が [**すべてのユーザー** ] または **[既存のゲスト**] に設定されていることを確認します。
5. 変更を加えた場合は、[**保存**] をクリックします。

## <a name="invite-users"></a>ユーザーを招待する

ゲスト共有の設定が構成されるようになったため、ユーザーはゲストでファイルやフォルダーを共有できるようになりました。 詳細については、「 [OneDrive ファイルとフォルダーを共有](https://support.office.com/article/9fcc2f7d-de0c-4cec-93b0-a82024800c07)する」および「 [SharePoint ファイルまたはフォルダーを共有](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c)する」を参照してください。

## <a name="see-also"></a>関連項目

[認証されていないユーザーとファイルやフォルダーを共有するためのベストプラクティス](best-practices-anonymous-sharing.md)

[ゲストと共有するときにファイルの偶発的な公開を制限する](sharing-limit-accidental-exposure.md)