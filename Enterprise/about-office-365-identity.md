---
title: Office 365 identity モデルと Azure Active Directory
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
- M365-security-compliance
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: Office 365 でユーザー id を管理する方法について説明します。
ms.openlocfilehash: 1d4a2f40ebae9fa87d59ee3f7c9b621b40b03640
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2019
ms.locfileid: "34162390"
---
# <a name="office-365-identity-models-and-azure-active-directory"></a>Office 365 identity モデルと Azure Active Directory

Office 365 では、Azure Active Directory (Azure AD) を使用して、office 365 サブスクリプションに含まれているクラウドベースのユーザー id と認証サービスを使用して、Office 365 の id と認証を管理します。 Id インフラストラクチャを正しく構成することは、組織の Office 365 のユーザーアクセスとアクセス許可を管理するために不可欠です。

開始する前に、Office 365 と Microsoft 365 の id モデルと認証の概要に関するビデオをご覧ください。

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2Pjwu]

最初の計画の選択は、Office 365 id モデルです。

## <a name="office-365-identity-models"></a>Office 365 の id モデル

ユーザーアカウントを計画するには、まず、Microsoft 365 で2つの id モデルを理解する必要があります。 組織の id は、クラウド内でのみ管理できます。または、オンプレミスの Active Directory ドメインサービス (AD DS) の id を維持して、ユーザーが Microsoft 365 cloud services にアクセスするときの認証に使用することができます。  

ここでは、2種類の id と、それらのユーザーにとって最適なものと利点を示します。

|||
|:-------|:-----|:-----|
|  | **クラウド専用の id** | **ハイブリッド id** |
| **定義** | ユーザーアカウントは、Microsoft 365 サブスクリプションの Azure Active Directory (Azure AD) テナントにのみ存在します。 | ユーザーアカウントが AD DS に存在し、Microsoft 365 サブスクリプションの Azure AD テナントにもコピーがあります。 Azure AD のユーザーアカウントには、ユーザーアカウントのパスワードのハッシュ化されたバージョンも含まれる場合があります。 |
| **Microsoft 365 でユーザー資格情報を認証する方法** | Microsoft 365 サブスクリプションの Azure AD テナントは、クラウド id アカウントを使用して認証を実行します。 | Microsoft 365 サブスクリプションの Azure AD テナントは、認証プロセスを処理するか、またはユーザーを別の id プロバイダーにリダイレクトします。 |
| **最適シナリオ** | 社内の AD DS を必要としない、または必要としない組織。 | AD DS または別の id プロバイダーを使用している組織。 |
| **最大のメリット** | 簡単に使用できます。 その他のディレクトリツールやサーバーは必要ありません。 | ユーザーは、オンプレミスまたはクラウドベースのリソースにアクセスするときに同じ資格情報を使用できます。 |
||||

## <a name="cloud-only-identity"></a>クラウド専用の id

クラウド専用の id は、Azure AD のみに存在するユーザーアカウントを使用します。 クラウド id は、通常、オンプレミスサーバーを持たない小規模な組織、または AD DS を使用してローカル id を管理しない小規模な組織で使用されます。 

ここでは、クラウド専用の id の基本的なコンポーネントを示します。
 
![](./media/about-office-365-identity/cloud-only-identity.png)

オンプレミスとリモート (オンライン) の両方のユーザーは、Azure AD のユーザーアカウントとパスワードを使用して Office 365 cloud services にアクセスします。 Azure AD は、保存されたユーザーアカウントとパスワードに基づいてユーザー資格情報を認証します。

### <a name="administration"></a>管理
ユーザーアカウントは Azure AD のみに格納されているため、クラウド id は、 [Microsoft 365 管理センター](https://admin.microsoft.com)と Windows PowerShell のツールを使用して、graph モジュール用 Azure Active Directory PowerShell を使用して管理します。 

## <a name="hybrid-identity"></a>ハイブリッド id

ハイブリッド id は、オンプレミスの AD DS で開始され、Microsoft 365 サブスクリプションの Azure AD テナントにコピーを持つアカウントを使用します。 ただし、ほとんどの変更は1つの方法でのみフローします。 AD DS ユーザーアカウントに加えた変更は、Azure AD のコピーと同期されます。 しかし、新しいユーザーアカウントなどの Azure AD のクラウドベースのアカウントに加えられた変更は、AD DS と同期されません。

Azure AD Connect は、継続的なアカウント同期を提供します。 オンプレミスのサーバー上で実行され、AD DS の変更を確認し、それらの変更を Azure AD に転送します。 Azure AD Connect は、同期されているアカウントをフィルター処理する機能と、パスワードハッシュ同期 (PHS) と呼ばれるユーザーパスワードのハッシュバージョンを同期するかどうかを指定する機能を提供します。

ハイブリッド id を実装すると、オンプレミスの AD DS が、アカウント情報の権限のあるソースになります。 これは、ほとんどがオンプレミスの管理タスクを実行することを意味します。これは、Azure AD に同期されます。 

ハイブリッド id のコンポーネントを次に示します。

![](./media/about-office-365-identity/hybrid-identity.png)

Azure AD テナントには、AD DS アカウントのコピーがあります。 この構成では、オンプレミスのユーザーと Microsoft 365 cloud services にアクセスするリモートユーザーの両方が Azure AD に対して認証されます。

>[!Note]
>ハイブリッド id のユーザーアカウントを同期するには、常に Azure AD Connect を使用する必要があります。 ライセンスの割り当てとグループ管理、アクセス許可の構成、およびユーザーアカウントに関連するその他の管理タスクを実行するには、Azure AD の同期されたユーザーアカウントが必要です。
>

### <a name="administration"></a>管理

元のユーザーアカウントと権限のあるユーザーアカウントは、オンプレミスの AD DS に格納されるので、Active Directory ユーザーおよびコンピューターツールなどの AD DS と同じツールを使用して id を管理します。 

Microsoft 365 管理センターまたは Windows PowerShell を使用して、Azure AD で同期されたユーザーアカウントを管理することはありません。

## <a name="next-step"></a>次の手順

クラウド専用の id モデルが必要な場合は、「[クラウド専用](cloud-only-identities.md)の id」を参照してください。

ハイブリッド id モデルが必要な場合は、「[同期 id と認証方法の計画](plan-for-directory-synchronization.md)」を参照してください。
  

## <a name="video-training"></a>ビデオ トレーニング

「 [Office 365: AZURE AD Connect を使用して id を管理](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx)する」を参照して、LinkedIn Learning に連絡してください。
