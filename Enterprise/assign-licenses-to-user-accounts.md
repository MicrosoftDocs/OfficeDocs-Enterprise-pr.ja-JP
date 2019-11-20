---
title: ユーザーアカウントに Office 365 ライセンスを割り当てる
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
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
description: ユーザーアカウントに Office 365 ライセンスを個別に、またはグループメンバーシップに基づいて割り当てる方法について説明します。
ms.openlocfilehash: bc736236f9371ee1372fd36af4a707aca2ee1408
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "38745710"
---
# <a name="assign-office-365-licenses-to-user-accounts"></a>ユーザーアカウントに Office 365 ライセンスを割り当てる

*この記事は、Office 365 Enterprise と Microsoft 365 Enterprise の両方に適用されます。*

クラウド専用の id モデルでは、作成方法に応じて、ユーザーアカウントの作成時に Office 365 ライセンスをユーザーアカウントに割り当てることができます。

ハイブリッド id モデルでは、Active Directory ドメインサービス (AD DS) ユーザーアカウントが初めて同期されるときに、Office 365 ライセンスが自動的に割り当てられることはありません。

どちらの場合も、ユーザーが Office 365 サービス (電子メールや Microsoft Teams など) にアクセスできるように、ユーザーアカウントにライセンスを割り当てる必要があります。

ユーザーアカウントには、個別に、またはグループメンバーシップを使用して、自動的にライセンスを割り当てることができます。

Office 365 ライセンスを個々のユーザーアカウントに割り当てるには、次のものを使用できます。

- [Microsoft 365 管理センター](https://docs.microsoft.com/office365/admin/subscriptions-and-billing/assign-licenses-to-users)
- [Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell)

自動ライセンス割り当ての場合は、「 [AZURE AD でのグループベースのライセンス](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal)」を参照してください。

## <a name="next-steps"></a>次の手順

ライセンスが割り当てられているユーザーアカウントの完全なセットにより、次の準備が整いました。

- [セキュリティを実装する](https://docs.microsoft.com/microsoft-365/security/office-365-security/security-roadmap)
- [Office 365 ProPlus などのクライアントソフトウェアを展開する](https://docs.microsoft.com/DeployOffice/deployment-guide-for-office-365-proplus)
- [モバイルデバイス管理を構成する](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)
- [サービスとアプリケーションを構成する](configure-services-and-applications.md)
