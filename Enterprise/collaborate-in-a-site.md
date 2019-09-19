---
title: サイト内のゲストと共同作業する
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: SharePoint サイトでゲストと共同作業する方法について説明します。
ms.openlocfilehash: 4b68b50fec4322f12c24969bdd71e7d9c0fda245
ms.sourcegitcommit: d388c76d25ca67f240db97f7bfc90f0991b0e7f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "37017315"
---
# <a name="collaborate-with-guests-in-a-site"></a>サイト内のゲストと共同作業する

ドキュメント、データ、およびリスト間でゲストと共同作業を行う必要がある場合は、SharePoint サイトを使用できます。 モダン SharePoint サイトは Office 365 グループに接続されており、サイトメンバーシップを管理したり、共有メールボックスや予定表などのその他のコラボレーションツールを提供したりできます。

この記事では、ゲストとのグループ作業のために SharePoint サイトをセットアップするために必要な Microsoft 365 の構成手順について説明します。

## <a name="azure-organizational-relationships-settings"></a>Azure の組織上の関係の設定

Microsoft 365 での共有は、Azure Active Directory の組織上の関係の設定によって最上位レベルで管理されます。 Azure AD でゲストの共有が無効または制限されている場合、これは Microsoft 365 で構成した共有設定よりも優先されます。

組織上の関係の設定を確認して、ゲストとの共有がブロックされないようにしてください。

![Azure Active Directory の組織上の関係の設定ページのスクリーンショット](media/azure-ad-organizational-relationships-settings.png)

組織上の関係の設定を設定するには

1. Microsoft Azure にログイン[https://portal.azure.com](https://portal.azure.com)します。
2. 左側のナビゲーションで、[ **Azure Active Directory**] をクリックします。
3. [**概要**] ウィンドウで、[組織上の**関係**] をクリックします。
4. [組織上の**関係**] ウィンドウで、[**設定**] をクリックします。
5. **管理者とゲスト招待元役割のユーザーが招待できる**ことと、**メンバーが招待**できることを確認します。どちらも **[はい]** に設定されています。
6. 変更を加えた場合は、[**保存**] をクリックします。

[**共同作業の制限**] セクションの設定に注意してください。 共同作業を行うゲストのドメインがブロックされていないことを確認します。

## <a name="office-365-groups-guest-settings"></a>Office 365 グループのゲスト設定

モダン SharePoint サイトは、Office 365 グループを使用してサイトアクセスを制御します。 SharePoint サイトでゲストアクセスを機能させるには、Office 365 グループのゲスト設定をオンにする必要があります。

![Microsoft 365 管理センターの Office 365 グループのゲスト設定のスクリーンショット](media/office-365-groups-guest-settings.png)

Office 365 グループのゲスト設定を設定するには

1. Microsoft 365 管理センターの左側のナビゲーションで、[**設定**] を展開します。
2. [**サービス] [& アドイン**] をクリックします。
3. リストで、[ **Office 365 グループ**] をクリックします。
4. [組織外のユーザーにグループの**コンテンツへのアクセス**を許可する] および [**グループの所有者に組織外のユーザーをグループに追加する**] チェックボックスの両方がオンになっていることを確認します。
5. 変更を加えた場合は、[**変更の保存**] をクリックします。


## <a name="sharepoint-organization-level-sharing-settings"></a>SharePoint 組織レベルの共有設定

ゲストが SharePoint サイトにアクセスできるようにするには、SharePoint の組織レベルの共有設定でゲストとの共有が許可されている必要があります。

組織レベルの設定によって、個々のサイトで使用可能な設定が決まります。 サイトの設定は、組織レベルの設定よりも制限することはできません。

匿名ユーザーとのファイルとフォルダーの共有を許可する場合は、[**すべて**のユーザー] を選択します。 すべてのゲストが認証を必要とするようにするには、[**新規および既存のゲスト**] を選択します。 組織内のすべてのサイトで必要とされる最も厳しい設定を選択します。

![SharePoint 組織レベルの共有設定のスクリーンショット](media/sharepoint-organization-external-sharing-controls.png)


SharePoint 組織レベルの共有設定を設定するには

1. Microsoft 365 管理センターで、左側のナビゲーションの [**管理センター**] の下にある [ **SharePoint**] をクリックします。
2. SharePoint 管理センターの左側のナビゲーションで、[**共有**] をクリックします。
3. SharePoint の外部共有が [**すべてのユーザー** ] または **[既存のゲスト**] に設定されていることを確認します。
4. 変更を加えた場合は、[**保存**] をクリックします。

## <a name="create-a-site"></a>サイトを作成する

次の手順では、ゲストとの共同作業に使用する予定のサイトを作成します。

サイトを作成するには
1. SharePoint 管理センターの [**サイト**] で、[**アクティブなサイト**] をクリックします。
2. [**作成**] をクリックします。
3. [**チームサイト**] をクリックします。
4. サイト名を入力し、グループの所有者 (サイト所有者) の名前を入力します。
5. [**詳細設定**] で、これをパブリックサイトまたはプライベートサイトにするかどうかを選択します。
6. [ **次へ**] をクリックします。
7. [**完了**] をクリックします。

後でユーザーを招待します。 次に、このサイトのサイトレベルでの共有設定を確認することが重要です。

## <a name="sharepoint-site-level-sharing-settings"></a>SharePoint サイトレベルの共有設定

サイトレベルの共有設定をチェックして、このサイトに必要なアクセスの種類が許可されていることを確認してください。 たとえば、組織レベルの設定をすべての**ユーザー**に設定した場合に、すべてのゲストがこのサイトの認証を行うようにするには、サイトレベルの共有設定が**新規および既存のゲスト**に設定されていることを確認します。

匿名ユーザー (**すべて**のユーザーの設定) とサイトを共有することはできませんが、個別のファイルとフォルダーを使用することはできます。

![SharePoint サイトの外部共有設定のスクリーンショット](media/sharepoint-site-external-sharing-settings.png)

サイトレベルの共有設定を設定するには
1. SharePoint 管理センターの左側のナビゲーションで、[**サイト**] を展開し、[**アクティブなサイト**] をクリックします。
2. 作成したサイトを選択します。
3. リボンの [**共有**] をクリックします。
4. 共有が [**すべてのユーザー** ] または **[既存のゲスト**] に設定されていることを確認します。
5. 変更を加えた場合は、[**保存**] をクリックします。

## <a name="invite-users"></a>ユーザーを招待する

ゲスト共有の設定が構成されるようになったため、内部ユーザーとゲストのサイトへの追加を開始できます。 サイトアクセスは、関連付けられた Office 365 グループを通じて制御されるため、ユーザーを追加します。

内部ユーザーをグループに招待するには
1. ユーザーを追加するサイトに移動します。
2. 右上の [**メンバー** ] をクリックします。
3. **[メンバーの追加]** をクリックします。
4. サイトに招待するユーザーの名前または電子メールアドレスを入力し、[**保存**] をクリックします。

ゲストユーザーをサイトから追加することはできません。 Web 上の Outlook を使用してそれらを追加する必要があります。

サイトにゲストを招待するには
1. Web 上の Outlook の [**グループ**] で、メンバーを追加するグループをクリックします。
2. グループの連絡先カードを開いて、[**その他のオプション**(...)] の下にある [**メンバーの追加**] をクリックします。
3. 招待するゲストの電子メールアドレスを入力し、[**追加**] をクリックします。
4. **[閉じる]** をクリックします。

## <a name="see-also"></a>関連項目