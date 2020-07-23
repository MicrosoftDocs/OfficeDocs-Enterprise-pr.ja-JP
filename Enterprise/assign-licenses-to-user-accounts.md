---
title: ユーザーアカウントに Microsoft 365 ライセンスを割り当てる
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Microsoft 365 ライセンスを個別に、またはグループメンバーシップに基づいてユーザーアカウントに割り当てる方法について説明します。
ms.openlocfilehash: 3a51f4966cdcfede57ad8a69546face160ae1750
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230003"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts"></a>ユーザーアカウントに Microsoft 365 ライセンスを割り当てる

*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*

クラウド専用の id モデルの場合は、作成方法に応じて、ユーザーアカウントの作成時に Microsoft 365 ライセンスを割り当てることができます。

ハイブリッド id モデルでは、Active Directory ドメインサービス (AD DS) ユーザーアカウントが初めて同期されるときに、Microsoft 365 ライセンスが自動的に割り当てられることはありません。 最初に、ユーザーの場所を使用して各ユーザーアカウントを構成する必要があります。

どちらの場合も、ユーザーが Microsoft 365 サービス (電子メールや Microsoft Teams など) にアクセスできるように、ユーザーアカウントにライセンスを割り当てる必要があります。

ユーザーアカウントには、個別に、またはグループメンバーシップを使用して、自動的にライセンスを割り当てることができます。

Microsoft 365 ライセンスを個々のユーザーアカウントに割り当てるには、次のものを使用できます。

- [Microsoft 365 管理センター](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users)
- [PowerShell for Microsoft 365](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell)

自動ライセンス割り当ての場合は、「 [AZURE AD でのグループベースのライセンス](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal)」を参照してください。

## <a name="next-steps"></a>次の手順

ライセンスが割り当てられているユーザーアカウントの完全なセットにより、次の準備が整いました。

- [セキュリティを実装する](https://docs.microsoft.com/microsoft-365/security/office-365-security/security-roadmap)
- [Microsoft 365 アプリなどのクライアントソフトウェアを展開する](https://docs.microsoft.com/DeployOffice/deployment-guide-microsoft-365-apps)
- [Microsoft 365 でモバイルデバイス管理をセットアップする](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)
- [サービスとアプリケーションを構成する](configure-services-and-applications.md)
