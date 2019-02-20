---
title: オンプレミスのメール (たとえば、ディレクトリ サービスの使用) を使って統合するためにドメインを使用する
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
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
ms.openlocfilehash: 112f543a9c647ea850d5e43bc14483308da0b2c7
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085336"
---
# <a name="office-365-integration-with-on-premises-environments"></a>オンプレミスのメール (たとえば、ディレクトリ サービスの使用) を使って統合するためにドメインを使用する

Office 365 を既存のディレクトリサービスに統合できます。また、Exchange server、Skype for business server 2015、または SharePoint server 2013 の社内インストールを使用することもできます。
  
 - ディレクトリサービスと統合すると、両方の環境のユーザーアカウントを同期して管理することができます。また、ユーザーがオンプレミスの資格情報を使用して両方の環境にログオンできるように、パスワードハッシュ同期またはシングルサインオン (SSO) を追加することもできます。
 - オンプレミスのサーバー製品と統合する場合は、ハイブリッド環境を作成します。ハイブリッド環境は、ユーザーまたは情報を Office 365 に移行する際に役立つことがあります。または、一部のユーザーまたは一部の情報を社内とクラウドに移行することができます。ハイブリッド環境の詳細については、「 [Office 365 ハイブリッドクラウドソリューションの概要](https://support.office.com/article/59616fab-acdb-40e9-b414-cf0c965c80b7)」を参照してください。

また、カスタマイズしたセットアップガイダンスに Azure AD アドバイザーを使用することもできます。
- [Azure AD Connect advisor](https://aka.ms/aadconnectpwsync)
- [AD FS 展開アドバイザー](https://aka.ms/adfsguidance)
- [Azure RMS 展開ウィザード](https://aka.ms/azuremsguidance)
- [Azure AD Premium のセットアップガイダンス](https://aka.ms/aadpguidance)
   
## <a name="before-you-begin"></a>始める前に
office 365 とオンプレミス環境を統合する前に、 [office 365 のネットワーク計画とパフォーマンスチューニング](network-planning-and-performance.md)にも参加する必要があります。Office 365 で利用可能な[id モデル](about-office-365-identity.md)についても理解しておく必要があります。 

office 365 のユーザーおよびアカウントの管理に使用できるツールの一覧については、「 [office のユーザーアカウントを管理する場所](manage-office-365-accounts.md)」を参照してください。 
  
## <a name="integrate-office-365-with-directory-services"></a>Office 365 とディレクトリサービスの統合
オンプレミスディレクトリに既存のユーザーアカウントがある場合は、それらのアカウントを Office 365 で再作成して、環境間での相違点やエラーを発生させないようにする必要があります。ディレクトリ同期は、オンライン環境とオンプレミス環境との間でアカウントをミラーリングするのに便利です。ディレクトリ同期を使用すると、ユーザーは環境ごとに新しい情報を記憶する必要がなくなります。また、アカウントを2回作成または更新する必要はありません。ディレクトリ同期のために[オンプレミスのディレクトリを準備](prepare-for-directory-synchronization.md)する必要があります。これは手動で行うか、 [idfix](install-and-run-idfix.md)ツール (idfix ツールは Active directory でのみ動作) を使用することができます。 
  
![ディレクトリ同期を使用してオンプレミスとオンラインのユーザーアカウント情報を同期された状態に保つ](media/a64af0d0-9be6-46b1-8727-277e683abf5e.png)
  
ユーザーがオンプレミスの資格情報を使用して Office 365 にログオンできるようにする場合は、SSO を構成することもできます。SSO を使用すると、Office 365 は、ユーザー認証用にオンプレミス環境を信頼するように構成されます。
  
![シングルサインオンを使用すると、オンプレミスの環境とオンライン環境の両方で同じアカウントを使用できます。](media/d76235f2-8a53-405e-b8ef-dfa4cfc208b8.png)
  
次の表に示すように、ユーザーアカウントの管理方法によって、ユーザーに対して異なるエクスペリエンスが提供されます。
 
### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication"></a>**パスワードのハッシュ同期またはパススルー認証の有無にかかわらずディレクトリ同期**
ユーザーが自分のユーザーアカウント (domain\username) を使用してオンプレミス環境にログオンします。Office 365 に移行する場合は、職場または学校のアカウント (user@domain.com) で再度ログオンする必要があります。両方の環境で同じユーザー名が指定されています。パスワードハッシュ同期またはパススルー認証を追加すると、ユーザーは両方の環境で同じパスワードを使用しますが、Office 365 にログオンするときにこれらの資格情報を再度提供する必要があります。ディレクトリ同期とパスワードハッシュ同期は、最も一般的に使用されるディレクトリ同期のシナリオです。

ディレクトリ同期をセットアップするには、Azure Active directory Connect を使用します。手順については、「 [Office 365 のディレクトリ同期をセットアップ](set-up-directory-synchronization.md)する」と「 [Azure AD Connect with express settings](https://go.microsoft.com/fwlink/p/?LinkId=698537)」を参照してください。

[Office 365 にディレクトリ同期を使用してユーザーをプロビジョニングするための準備](prepare-for-directory-synchronization.md)の詳細と、[オンプレミスと Azure Active directory の識別を統合](https://go.microsoft.com/fwlink/?LinkId=518101)する方法について説明します。

### <a name="directory-synchronization-with-sso"></a>**SSO を使用したディレクトリ同期**
ユーザーが自分のユーザーアカウントを使用してオンプレミス環境にログオンします。Office 365 に移行すると、それらのユーザーは自動的にログオンするか、オンプレミス環境 (domain\username) に使用したものと同じ資格情報を使用してログオンします。

SSO をセットアップするには、Azure AD Connect も使用します。手順については、「 [Azure AD Connect でカスタム設定を使用する](https://go.microsoft.com/fwlink/p/?LinkID=698430)」を参照してください。

[Azure Active Directory を使用したアプリケーションアクセスとシングルサインオン](https://go.microsoft.com/fwlink/p/?LinkId=698604)の詳細について説明します。

## <a name="azure-ad-connect"></a>Azure AD Connect
azure ad Connect は、DirSync、azure ad Sync などの id 統合ツールの以前のバージョンに置き換えられました。詳細については、「[オンプレミス id と Azure Active Directory の統合](https://go.microsoft.com/fwlink/p/?LinkId=527969)」を参照してください。azure Active Directory 同期から azure AD Connect に更新する場合は、[アップグレード手順](https://go.microsoft.com/fwlink/p/?LinkId=733240)を参照してください。[Microsoft Azure で Office 365 ディレクトリ同期 (DirSync)](https://go.microsoft.com/fwlink/?LinkId=517887)用に構築されたソリューションアーキテクチャを参照してください。