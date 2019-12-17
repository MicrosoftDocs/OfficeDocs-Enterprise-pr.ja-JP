---
title: Office 365 のクラウド専用の id
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Office 365 サブスクリプションがクラウド専用の id を使用している場合に、ユーザーとグループを作成する方法について説明します。
ms.openlocfilehash: 5991ec838321187b58f913e1707efb2ede9912fb
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072279"
---
# <a name="office-365-cloud-only-identities"></a>Office 365 のクラウド専用の id

*この記事は、Office 365 Enterprise および Microsoft 365 Enterprise の両方に適用されます。*

クラウド専用の id を使用すると、すべてのユーザー、グループ、および連絡先が Office 365 サブスクリプションの Azure Active Directory (Azure AD) テナントに格納されます。 ここでは、クラウド専用の id の基本的なコンポーネントを示します。
 
![クラウド専用の id の基本コンポーネント](./media/about-office-365-identity/cloud-only-identity.png)

組織内のユーザーとユーザーアカウントは、さまざまな方法で分類できます。 たとえば、一部は従業員で、恒久的な状態になっています。 一部のベンダー、請負業者、またはパートナーは、一時的な状態になっています。 ユーザーアカウントを持たない外部ユーザーも、対話とコラボレーションをサポートするために特定のサービスやリソースへのアクセスを引き続き付与する必要があります。 次に例を示します。

- テナント アカウントは、組織内でクラウド サービスのライセンスを付与したユーザーを表します。

- ビジネスツービジネス (B2B) アカウントは、グループ作業への参加を招待する組織外のユーザーを表します。組織内のユーザーの種類のストックを取得します。 グループ化とは たとえば、組織に対して、レベルの高い機能または目的によってユーザーをグループ化することができます。

また、一部のクラウド サービスを、ユーザー アカウントを持たない組織外のユーザーと共有できます。この場合、このような外部ユーザーのグループも指定する必要があります。

Azure AD のグループは、クラウド環境の管理を簡素化するいくつかの目的に使用できます。 たとえば、Azure AD グループでは、次のことを行うことができます。

- グループベースのライセンスを使用して、Office 365 のライセンスを追加後すぐに自動的にユーザーアカウントに割り当てます。
- ユーザー アカウントの属性 (部門など) に基づいて、ユーザー アカウントを特定のグループに動的に追加する。
- Software as a Service (SaaS) アプリケーションのユーザーを自動的にプロビジョニングし、多要素認証やその他の条件付きアクセス ルールでこれらのアプリケーションへのアクセスを保護する。
- SharePoint Online チームサイトのアクセス許可とアクセス許可のレベルをプロビジョニングします。

次の方法で新しい***ユーザー***を作成できます。

- [Microsoft 365 管理センター](https://docs.microsoft.com/office365/admin/add-users/add-users)
- [Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)

次の方法で新しい***グループ***を作成できます。

- [Microsoft 365 管理センター](https://docs.microsoft.com/office365/admin/create-groups/create-groups)
- [Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-groups-with-powershell)


## <a name="next-step-for-cloud-only-identities"></a>クラウド専用の id の次の手順

[ユーザー アカウントにライセンスを割り当てる](assign-licenses-to-user-accounts.md)
