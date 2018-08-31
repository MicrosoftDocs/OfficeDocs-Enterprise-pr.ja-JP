---
title: オンプレミス環境と office 365 の統合
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- LYN150
- SPS150
- MOE150
- MED150
ms.assetid: 263faf8d-aa21-428b-aed3-2021837a4b65
description: Office 365 を既存のディレクトリ サービスに統合する方法について説明します。
ms.openlocfilehash: b660dda74303a3bf0fa92bc8e3146cd2c9add662
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541674"
---
# <a name="office-365-integration-with-on-premises-environments"></a>オンプレミス環境と office 365 の統合

ビジネス サーバー 2015、または SharePoint Server 2013 は、既存のディレクトリ サービスおよび Exchange Server、Skype のオンプレミスのインストールと Office 365 を統合できます。
  
 - ディレクトリ サービスと統合するときに同期し、両方の環境のユーザー アカウントを管理できます。追加することもパスワード ハッシュの同期またはシングル サインオン (SSO) のユーザーがログオンできるように、設置型の資格情報を持つ両方の環境にします。
 - オンプレミスのサーバー製品と統合する場合に、ハイブリッド環境を作成します。ハイブリッド環境は、ユーザーや情報を Office 365 に移行するか、一部のユーザーまたはいくつかについては、オンプレミスとクラウドの一部を続行するようにできます。ハイブリッド環境の詳細については、 [Office 365 のハイブリッド クラウド ソリューションの概要](https://support.office.com/article/59616fab-acdb-40e9-b414-cf0c965c80b7)を参照してください。

Azure AD アドバイザーは、カスタマイズされたセットアップ ガイドのも使用できます。
- [Azure AD 接続アドバイザー](https://aka.ms/aadconnectpwsync)
- [AD FS 展開アドバイザー](https://aka.ms/adfsguidance)
- [Azure の RMS の展開ウィザード](https://aka.ms/azuremsguidance)
- [Azure AD プレミアム セットアップ ガイド](https://aka.ms/aadpguidance)
   
## <a name="before-you-begin"></a>はじめに
Office 365 と設置環境を統合すると、前に、[ネットワークの計画と Office 365 のパフォーマンスの調整](network-planning-and-performance.md)に参加する必要があります。Office 365 で利用可能な[識別情報モデル](about-office-365-identity.md)を理解するができます。 

[アカウントを Office 365 のユーザーを管理するのには、](manage-office-365-accounts.md) Office 365 ユーザー アカウントとアカウントを管理するために使用できるツールの一覧についてを参照してください。 
  
## <a name="integrate-office-365-with-directory-services"></a>Office 365 ディレクトリ サービスと統合します。
設置ディレクトリに既存のユーザー アカウントがあれば、すべての Office 365 との違いや環境間でのエラーを導入することのリスクでこれらのアカウントを再作成したくないです。ディレクトリ同期、オンラインの間でそれらのアカウントをミラー化することが、オンプレミス環境です。ディレクトリ同期によって、ユーザーは、環境ごとに新しい情報を記憶する必要はありません、作成またはアカウントを 2 回更新する必要はありません。ディレクトリ同期のため[のオンプレミス ディレクトリの準備](prepare-for-directory-synchronization.md)をする必要がありますは手動でまたは[IdFix ツール](install-and-run-idfix.md)(IdFix ツールでのみ機能する Active Directory) を使用できます。 
  
![ディレクトリ同期を使用して、設置し、オンラインのユーザー アカウント情報を同期させる](media/a64af0d0-9be6-46b1-8727-277e683abf5e.png)
  
ユーザーが Office 365 の設置型の資格情報でログオンできる場合は、SSO を構成することもできます。SSO では、Office 365 は、オンプレミス環境にユーザーの認証を信頼するように構成します。
  
![シングル サインオンで、同じアカウントがオンプレミスとオンライン環境の両方で使用可能です](media/d76235f2-8a53-405e-b8ef-dfa4cfc208b8.png)
  
別のユーザー アカウント管理の手法は、次の表に示すように、ユーザー エクスペリエンスを提供します。
 
### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication"></a>**ディレクトリ同期のパスワード ハッシュの同期またはパススルー認証の有無**
ユーザーが、ユーザー アカウント (ドメイン \ ユーザー名) に、オンプレミス環境にログオンするとします。Office 365 に移動するとする必要がありますもう一度アカウントでログオン、職場または学校 (user@domain.com)。ユーザー名は、両方の環境で同じです。パスワード ハッシュの同期またはパススルー認証を追加するとユーザーの両方の環境では、同じパスワードが Office 365 にログオンするときに、それらの資格情報を再度入力する必要があります。パスワード ハッシュの同期とのディレクトリ同期は、最も一般的に使用されるディレクトリ同期シナリオです。

ディレクトリ同期をセットアップするには、Azure Active Directory の接続を使用します。手順については、 [Office 365 のディレクトリ同期の設定](set-up-directory-synchronization.md)、および[高速の設定で、Azure を使用して AD 接続](https://go.microsoft.com/fwlink/p/?LinkId=698537)」を参照します。

詳細について[Office 365 のディレクトリ同期を使用してユーザーをプロビジョニングするための準備](prepare-for-directory-synchronization.md)と、 [Azure Active Directory で、設置型の識別と統合します](https://go.microsoft.com/fwlink/?LinkId=518101)。

### <a name="directory-synchronization-with-sso"></a>**SSO とのディレクトリ同期**
ユーザーは、オンプレミス環境のユーザー アカウントでログオンします。Office 365 に移動するとと、か、ログオンしている、自動的にまたはの設置環境 (ドメイン \ ユーザー名) を使用して、これらと同じ資格情報を使用してログオンします。

SSO を設定するのには、Azure AD 接続も使用します。手順については、[カスタム設定で Azure を使用して AD の接続](https://go.microsoft.com/fwlink/p/?LinkID=698430)を参照してください。

[アプリケーションへのアクセスと Azure Active Directory でのシングル サインオン](https://go.microsoft.com/fwlink/p/?LinkId=698604)の詳細について説明します。

## <a name="azure-ad-connect"></a>Azure AD Connect
Azure AD 接続には、ディレクトリ同期、Azure AD 同期などの id の統合ツールの以前のバージョンが置き換えられます。詳細については[、オンプレミス ユーザーは、Azure Active Directory との統合](https://go.microsoft.com/fwlink/p/?LinkId=527969)」を参照してください。Azure Active Directory 同期から Azure AD 接続へ更新する場合は、[アップグレードの手順](https://go.microsoft.com/fwlink/p/?LinkId=733240)を参照してください。[Office 365 ディレクトリ同期 (DirSync) で、Microsoft Azure](https://go.microsoft.com/fwlink/?LinkId=517887)用に作成されたソリューションのアーキテクチャを参照してください。