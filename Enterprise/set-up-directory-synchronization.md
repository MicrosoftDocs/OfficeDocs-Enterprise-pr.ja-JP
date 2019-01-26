---
title: Office 365 のディレクトリ同期のセットアップ
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED15
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: Office 365 と、オンプレミスの Active Directory のディレクトリ同期をセットアップする方法について説明します。
ms.openlocfilehash: f2cd29e7a81854bb64f6317aa2b41e674ae22df4
ms.sourcegitcommit: a4546e1f3fe9e8e25a56ed350400d51eb7dd7f83
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "29555443"
---
# <a name="set-up-directory-synchronization-for-office-365"></a>Office 365 のディレクトリ同期のセットアップ

Office 365 は、ユーザーを管理するのにクラウド ベースのユーザー id の管理の Azure Active Directory サービスを使用します。Azure AD を Office 365 で、オンプレミス環境を同期することにより、オンプレミスの Active Directory を統合することも。同期を設定すると、Azure AD 内で、または、設置ディレクトリ内のユーザー認証を決定できます。
  
## <a name="office-365-directory-synchronization"></a>Office 365 ディレクトリ同期

同期の id や、設置型の組織と Office 365 の間でフェデレーション id を使用することができます。同期の id で、ユーザー設置を管理すると、同じパスワードを使用、クラウドでオンプレミスと Azure の AD によって認証します。これは、最も一般的なディレクトリ同期シナリオです。パススルー認証] または [フェデレーション id は、ユーザーの設置型を管理することをでき、オンプレミス ディレクトリで認証します。フェデレートされた識別情報は、追加の構成を必要とし、のみ 1 回サインインすることができます。詳細については、 [Office 365 の Id を理解して Azure Active Directory](about-office-365-identity.md)を読み取る。
  
## <a name="want-to-upgrade-from-windows-azure-active-directory-sync-dirsync-to-azure-active-directory-connect"></a>Azure Active Directory に接続するのには、Windows Azure Active Directory 同期 (DirSync) からアップグレードする場合は、

ディレクトリ同期を現在使用してアップグレードする場合、ヘッドを[azure.com](https://azure.com)に[アップグレード手順](https://go.microsoft.com/fwlink/p/?LinkId=733240)の。
  
## <a name="prerequisites-for-azure-ad-connect"></a>Azure AD の前提条件を接続します。

Azure AD に Office 365 サブスクリプションと無料サブスクリプションを取得します。、ディレクトリ同期をセットアップすると、Azure Active Directory の接続をインストール、オンプレミスのサーバーのいずれかにされます。
  
Office 365 用に必要になります。
  
- (手順に従って、この)、オンプレミス ドメインを確認します。
- [ビジネス向けの Office 365 の管理者の役割を割り当てる](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504)アクセス許可を持つ、Office 365 テナントとオンプレミスの Active Directory です。

Azure AD 接続をインストールする、設置型サーバーの次のソフトウェアが必要になります。
  
|**サーバ OS**|**その他のソフトウェア**|
|:-----|:-----|
|**Windows Server 2012 R2** | で PowerShell は、既定でインストール、操作する必要はありません。  <br> Net 4.5.1 以降のリリースが Windows Update で提供されているとします。コントロール パネルの Windows サーバーに最新の更新プログラムがインストールされていることを確認します。 |
|**パック 1 (SP1) のサービスを Windows Server 2008 R2**または**Windows Server 2012** | -PowerShell の最新バージョンは、Windows Management Framework 4.0 で使用できます。[Microsoft ダウンロード センター](https://go.microsoft.com/fwlink/p/?LinkId=717996)で検索します。<br> -.Net 4.5.1 およびそれ以降のリリースでは、 [Microsoft ダウンロード センター](https://go.microsoft.com/fwlink/p/?LinkId=717996)で利用可能です。 |
|**Windows Server 2008** | -サポートされる最新バージョンの PowerShell は、Windows Management Framework 3.0 では、 [Microsoft ダウンロード センター](https://go.microsoft.com/fwlink/p/?LinkId=717996)で利用可能な時間があります。  <br> -.Net 4.5.1 およびそれ以降のリリースでは、 [Microsoft ダウンロード センター](https://go.microsoft.com/fwlink/p/?LinkId=717996)で利用可能です。 |

> [!NOTE]
> Azure Active Directory のディレクトリ同期を使用している場合は、Azure Active Directory に、オンプレミスの Active Directory から同期することができる配布グループのメンバーの最大数が 15,000 です。Azure AD 接続では、その番号は 50,000 です。 
  
Azure AD 接続のハードウェア、ソフトウェア、アカウントとアクセス許可の要件、SSL 証明書の要件、およびオブジェクトの制限をより慎重に確認、 [Azure Active Directory に接続するための前提条件](https://go.microsoft.com/fwlink/p/?LinkId=716896)を参照してください。
  
Azure AD 接続[リリースのバージョン履歴](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history)に含まれており、各リリースでの修正内容を参照してくださいかを確認することもできます。

## <a name="to-set-up-directory-synchronization"></a>ディレクトリ同期を設定するには

1. Office 365 の管理センターにサインインし、**ユーザー**の選択\>左のナビゲーションには、**アクティブなユーザー**です。
2. Office 365 管理センターで、[**アクティブ ユーザ**] ページで [**詳細** \> **ディレクトリ同期**します。

    ![[詳細] メニューの [ディレクトリ同期を選択します](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. [ **Active Directory の準備**] ページでは、**ツールのダウンロード Microsoft Azure Active Directory 接続**のリンクを開始するを選択します。Azure Active Directory 接続のインストール プロセスに関する詳細については、 [Azure 接続する AD と AD の Azure の接続の状態のインストール ・ ロードマップ](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap)を参照してください。

## <a name="assign-licenses-to-synchronized-users"></a>同期されたユーザーにライセンスを割り当てる

同期したら、ユーザーが Office 365 は、作成されるが、メールなど、Office 365 の機能を使用するためにライセンスを割り当てる必要があります。手順については、[ビジネス向けの Office 365 のユーザーにライセンスを割り当てる](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc)を参照してください。

## <a name="finish-setting-up-domains"></a>ドメインのセットアップを完了します。

自分のドメインの設定を完了するのには[Office 365 の DNS レコードを管理するときに作成する DNS レコード](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23)の手順を実行します。