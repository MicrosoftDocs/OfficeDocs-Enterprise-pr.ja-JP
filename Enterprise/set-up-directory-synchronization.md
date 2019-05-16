---
title: Office 365 のディレクトリ同期をセットアップする
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED15
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: Office 365 とオンプレミスの Active Directory との間のディレクトリ同期をセットアップする方法について説明します。
ms.openlocfilehash: d5c09b006c4e4b9ca9fbe3b0d673435a8ea6637e
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070873"
---
# <a name="set-up-directory-synchronization-for-office-365"></a>Office 365 のディレクトリ同期をセットアップする

Office 365 は、クラウドベースのユーザー id 管理サービス Azure Active Directory を使用してユーザーを管理します。 オンプレミスの環境と Office 365 を同期することによって、オンプレミスの Active Directory を Azure AD と統合することもできます。 同期を設定すると、ユーザーの認証を Azure AD 内で行うか、オンプレミスのディレクトリ内で行うかを決定できます。
  
## <a name="office-365-directory-synchronization"></a>Office 365 ディレクトリ同期

オンプレミスの組織と Office 365 の間で、同期された id またはフェデレーション id を使用できます。 同期された id を使用すると、オンプレミスのユーザーを管理できます。また、クラウドでオンプレミスと同じパスワードを使用する場合は、Azure AD によって認証されます。 これは、最も一般的なディレクトリ同期のシナリオです。 パススルー認証またはフェデレーション id を使用して、オンプレミスのユーザーを管理し、オンプレミスのディレクトリによって認証されます。 フェデレーション id には追加の構成が必要であり、ユーザーは一度だけサインインできるようになります。 詳細については、「 [Office 365 id と Azure Active Directory について](about-office-365-identity.md)」を参照してください。
  
## <a name="want-to-upgrade-from-windows-azure-active-directory-sync-dirsync-to-azure-active-directory-connect"></a>Windows Azure Active Directory 同期 (DirSync) から Azure Active Directory Connect へのアップグレードを希望する場合

現在 DirSync を使用していて、アップグレードする場合は、 [azure.com](https://azure.com)に移動して[アップグレード手順](https://go.microsoft.com/fwlink/p/?LinkId=733240)を確認してください。
  
## <a name="prerequisites-for-azure-ad-connect"></a>Azure AD Connect の前提条件

Office 365 サブスクリプションを使用して Azure AD への無料サブスクリプションを取得します。 ディレクトリ同期をセットアップすると、オンプレミスサーバーの1つに Azure Active Directory Connect がインストールされます。
  
Office 365 の場合は、次の操作を行う必要があります。
  
- オンプレミスのドメインを確認します (手順を追って説明します)。
- Office 365 で office 365 テナントとオンプレミスの Active Directory のビジネスアクセス許可に対して[管理者ロールを割り当て](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504)ます。

Azure AD Connect をインストールするオンプレミスサーバーでは、次のソフトウェアが必要になります。
  
|**サーバー OS**|**その他のソフトウェア**|
|:-----|:-----|
|**Windows Server 2012 R2** | -PowerShell は既定でインストールされます。既定では、アクションは必要ありません。  <br> -Net 4.5.1 以降のリリースは、Windows Update を通じて提供されます。 コントロールパネルで、Windows Server に最新の更新プログラムがインストールされていることを確認してください。 |
|**Windows server 2008 R2 Service Pack 1 (SP1)** または**windows server 2012** | -最新バージョンの PowerShell は、Windows Management Framework 4.0 で利用できます。 [Microsoft ダウンロードセンター](https://go.microsoft.com/fwlink/p/?LinkId=717996)で検索します。  <br> -.Net 4.5.1 以降のリリースは、 [Microsoft ダウンロードセンター](https://go.microsoft.com/fwlink/p/?LinkId=717996)から入手できます。 |
|**Windows Server 2008** | -最新サポートされている PowerShell のバージョンは、 [Microsoft ダウンロードセンター](https://go.microsoft.com/fwlink/p/?LinkId=717996)で利用可能な Windows Management Framework 3.0 で利用できます。  <br> -.Net 4.5.1 以降のリリースは、 [Microsoft ダウンロードセンター](https://go.microsoft.com/fwlink/p/?LinkId=717996)から入手できます。 |

> [!NOTE]
> Azure Active Directory DirSync を使用している場合、オンプレミスの Active Directory から Azure Active Directory に同期できる配布グループメンバーの最大数は15000です。 Azure AD Connect の場合、この番号は5万です。
  
ハードウェア、ソフトウェア、アカウントとアクセス許可の要件、SSL 証明書の要件、および Azure AD Connect のオブジェクト制限を慎重に確認するには、「 [Azure Active Directory Connect の前提条件](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites)」を参照してください。
  
また、Azure AD Connect[バージョンのリリース履歴](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history)で、各リリースに含まれているものを確認することもできます。

## <a name="to-set-up-directory-synchronization"></a>ディレクトリ同期をセットアップするには

1. [Microsoft 365 管理センター](https://admin.microsoft.com)にサインインし、左側のナビゲーションで [**ユーザー** \>の**アクティブなユーザー** ] を選択します。
2. 管理センターの [**アクティブなユーザー** ] ページで、[**その他** \>の**ディレクトリ同期**] を選択します。

    ![[その他] メニューで、[ディレクトリ同期] を選択します。](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. [ **Active directory の準備**] ページで、[ **Microsoft Azure Active directory Connect ツールのダウンロード**] リンクをクリックして開始します。 Azure Active Directory 接続のインストールプロセスの詳細については、「 [AZURE Ad connect と AZURE Ad Connect 正常性インストールのロードマップ](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap)」を参照してください。

## <a name="assign-licenses-to-synchronized-users"></a>同期されたユーザーにライセンスを割り当てる

ユーザーを Office 365 に同期した後は、それらのユーザーが作成されますが、メールなどの Office 365 機能を使用できるようにするためにライセンスを割り当てる必要があります。 手順については、「一般[法人向け Office 365 のユーザーにライセンスを割り当てる](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc)」を参照してください。

## <a name="finish-setting-up-domains"></a>ドメインのセットアップを完了する

DNS レコードを管理するときに、「 [CREATE dns records For Office 365](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) 」の手順に従って、ドメインの設定を完了します。