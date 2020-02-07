---
title: Office 365 とオンプレミス環境との統合
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 10/08/2019
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
search.appverid:
- MET150
- LYN150
- SPS150
- MOE150
- MED150
ms.assetid: 263faf8d-aa21-428b-aed3-2021837a4b65
description: Office 365 と既存のディレクトリサービスを統合する方法について説明します。
ms.openlocfilehash: 61feabb4d62b4b67538f45a3f827c746197b55d3
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844498"
---
# <a name="office-365-integration-with-on-premises-environments"></a>Office 365 とオンプレミス環境との統合

*この記事は、Office 365 Enterprise および Microsoft 365 Enterprise の両方に適用されます。*

Office 365 と既存のディレクトリサービス、および Exchange Server、Skype for Business Server 2015、または SharePoint Server のオンプレミスインストールを統合することができます。
  
 - ディレクトリサービスと統合すると、両方の環境のユーザーアカウントを同期して管理することができます。 また、ユーザーがオンプレミスの資格情報を使用して両方の環境にログオンできるように、パスワードハッシュ同期またはシングルサインオン (SSO) を追加することもできます。
 - オンプレミスのサーバー製品と統合する場合は、ハイブリッド環境を作成します。 ハイブリッド環境は、ユーザーまたは情報を Office 365 に移行する際に役立つことがあります。または、一部のユーザーまたは一部の情報を社内とクラウドに移行することができます。 ハイブリッド環境の詳細については、「[ハイブリッドクラウドの概要](https://docs.microsoft.com/Office365/Enterprise/hybrid-cloud-overview)」を参照してください。

カスタマイズしたセットアップガイダンスに Azure Active Directory (Azure AD) アドバイザーを使用することもできます (Office 365 にサインインする必要があります)。

- [Azure AD Connect advisor](https://aka.ms/aadconnectpwsync)
- [AD FS 展開アドバイザー](https://aka.ms/adfsguidance)
- [Azure AD Premium のセットアップガイダンス](https://aka.ms/aadpguidance)
   
## <a name="before-you-begin"></a>はじめに

Office 365 とオンプレミス環境を統合する前に、[ネットワーク計画とパフォーマンスチューニング](network-planning-and-performance.md)にも参加する必要があります。 利用可能な[id モデル](about-office-365-identity.md)についても理解しておく必要があります。 

Office 365 のユーザーおよびアカウントの管理に使用できるツールの一覧については、「 [office 365 アカウントの管理](manage-office-365-accounts.md)」を参照してください。 
  
## <a name="integrate-office-365-with-directory-services"></a>Office 365 とディレクトリサービスの統合
オンプレミスディレクトリに既存のユーザーアカウントがある場合は、それらのアカウントを Office 365 で再作成して、環境間での相違点やエラーを発生させないようにする必要があります。 ディレクトリ同期は、オンライン環境とオンプレミス環境との間でアカウントをミラーリングするのに便利です。 ディレクトリ同期を使用すると、ユーザーは環境ごとに新しい情報を記憶する必要がなくなります。また、アカウントを2回作成または更新する必要はありません。 ディレクトリ同期のために[オンプレミスのディレクトリを準備](prepare-for-directory-synchronization.md)する必要があります。これは手動で行うか、 [idfix](install-and-run-idfix.md)ツール (Active DIRECTORY ドメインサービス [AD DS] でのみ機能します) を使用して行うことができます。 
  
![ディレクトリ同期を使用してオンプレミスとオンラインのユーザーアカウント情報を同期された状態に保つ](media/a64af0d0-9be6-46b1-8727-277e683abf5e.png)
  
ユーザーがオンプレミスの資格情報を使用して Office 365 にログオンできるようにする場合は、SSO を構成することもできます。 SSO を使用すると、Office 365 は、ユーザー認証用にオンプレミス環境を信頼するように構成されます。
  
![シングルサインオンを使用すると、オンプレミスの環境とオンライン環境の両方で同じアカウントを使用できます。](media/d76235f2-8a53-405e-b8ef-dfa4cfc208b8.png)
  
次の表に示すように、ユーザーアカウントの管理方法によって、ユーザーに対して異なるエクスペリエンスが提供されます。
 
### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication"></a>パスワードのハッシュ同期またはパススルー認証の有無にかかわらずディレクトリ同期

ユーザーが自分のユーザーアカウント (domain\username) を使用してオンプレミス環境にログオンします。 Office 365 に移行する場合は、職場または学校のアカウント (user@domain.com) で再度ログオンする必要があります。 両方の環境で同じユーザー名が指定されています。 パスワードハッシュ同期またはパススルー認証を追加すると、ユーザーは両方の環境で同じパスワードを使用しますが、Office 365 にログオンするときにこれらの資格情報を再度提供する必要があります。 ディレクトリ同期とパスワードハッシュ同期は、最も一般的に使用されるディレクトリ同期のシナリオです。

ディレクトリ同期をセットアップするには、Azure Active Directory Connect を使用します。 手順については、「 [Set up directory synchronization For Office 365](set-up-directory-synchronization.md)」および「 [Azure AD Connect with express settings](https://go.microsoft.com/fwlink/p/?LinkId=698537)」を参照してください。

[Office 365 へのディレクトリ同期の準備](prepare-for-directory-synchronization.md)と[オンプレミスの統合](https://go.microsoft.com/fwlink/?LinkId=518101)の詳細については、「Azure Active directory」を参照してください。

### <a name="directory-synchronization-with-sso"></a>SSO を使用したディレクトリ同期

ユーザーが自分のユーザーアカウントを使用してオンプレミス環境にログオンします。 Office 365 に移行すると、それらのユーザーは自動的にログオンするか、オンプレミス環境 (domain\username) に使用したものと同じ資格情報を使用してログオンします。

SSO をセットアップするには、Azure AD Connect も使用します。 手順については、「 [AZURE AD Connect のカスタムインストール](https://go.microsoft.com/fwlink/p/?LinkID=698430)」を参照してください。

[Azure Active Directory でのアプリケーションへのシングルサインオン](https://go.microsoft.com/fwlink/p/?LinkId=698604)の詳細について説明します。

## <a name="azure-ad-connect"></a>Azure AD Connect

Azure AD Connect は、DirSync、Azure AD Sync などの id 統合ツールの以前のバージョンに置き換えられました。詳細については、「 [Azure Active Directory でのハイブリッド id とは](https://go.microsoft.com/fwlink/p/?LinkId=527969)」を参照してください。 Azure Active Directory 同期から Azure AD Connect に更新する場合は、[アップグレード手順](https://go.microsoft.com/fwlink/p/?LinkId=733240)を参照してください。 

「 [Deploy Office 365 Directory Synchronization In Microsoft Azure](https://go.microsoft.com/fwlink/?LinkId=517887)」も参照してください。

## <a name="see-also"></a>関連項目

[Microsoft 365 Enterprise の概要](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
