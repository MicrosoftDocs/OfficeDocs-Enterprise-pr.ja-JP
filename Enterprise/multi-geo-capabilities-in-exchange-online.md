---
title: Exchange Multi-Geo
ms.reviewer: adwood
ms.author: chrisda
author: chrisda
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
localization_priority: Priority
description: Exchange Online の Multi-Geo 機能について説明します。
ms.openlocfilehash: 27b636e1fb7f209a425a070f8024a1cdd461f59b
ms.sourcegitcommit: 1c3aa0654336acec14098241f785ea1d8c6caf50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2020
ms.locfileid: "42890549"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a>Exchange Online の Multi-Geo 機能

Multi-Geo の環境では、Exchange Online メールボックスのコンテンツ (保管中のデータ) の場所をユーザー別に選択できます。

次の方法でメールボックスをサテライトの地理的位置に配置できます。

- サテライトの地理的位置に新しい Exchange Online メールボックスを直接作成します。

- ユーザーが希望するデータの場所を変更することで、既存の Exchange Online メールボックスをサテライトの地理的位置に移動します。

- メールボックスをオンプレミスの Exchange 組織から、サテライトの地理的位置に直接移動します。

## <a name="mailbox-placement-and-moves"></a>メールボックスの配置と移動

Microsoft が事前に必要な複数地域の構成手順を完了すると、Exchange Online は Azure AD のユーザーオブジェクトで **PreferredDataLocation** 属性を受け入れます。

Exchange online は、** PreferredDataLocation** プロパティを、Azure AD から Exchange online ディレクトリサービスの** MailboxRegion** プロパティに同期します。 **MailboxRegion**の値は、ユーザーのメールボックスと、関連付けられている アーカイブ メールボックス が配置されている地理的位置を決定します。 別の地理的位置に存在するユーザーの プライマリ メールボックス と アーカイブ メールボックス を構成することはできません。 ユーザーオブジェクトごとに構成できる地理的位置は1つだけです。

- ユーザーの既存のメールボックスを使用して **PreferredDataLocation** を構成した場合、メールボックスは再配置キューに入れられ、指定された地理的位置に自動的に移動されます。

- 既存のメールボックスを持たないユーザーに** PreferredDataLocation** を構成したてメールボックスをプロビジョンする場合、そのメールボックスは指定された地理的位置にプロビジョニングされます。

- **PreferredDataLocation**がユーザーに指定されていない場合、メールボックスは中央の地理的位置にプロビジョニングされます。

- **PreferredDataLocation**コードが誤っている場合 (たとえば、NAMでなくNANと入力した場合)、メールボックスは中央の 地理的位置にプロビジョニングされます。

**注**: 複数地域の機能と Skype for Business Online が地域的にホストする会議のいずれの場合も、ユーザーオブジェクトの **PreferredDataLocation** プロパティがサービスを見つけます。 地域的に管理されている会議用のユーザーオブジェクトに** PreferredDataLocation** の値を構成すると、そのユーザーのメールボックスは、Office 365 テナントで複数地域が有効になった後、指定した地理的位置に自動的に移動します。

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a>Exchange Online における複数地域の機能に関する制限

- Exchange 管理センター (EAC) で利用できるセキュリティ機能およびコンプライアンス機能（たとえば、監査や電子情報開示）は、複数地域の組織では利用できません。 セキュリティとコンプライアンスの機能を構成するには、[Office 365 セキュリティ/コンプライアンス センター](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8)を使用する必要があります。

- Outlook for Mac を使用している場合は、メールボックスを新しい地理的位置に移動する際、オンラインアーカイブ フォルダーに一時的にアクセスできなくなることがあります。 この状態は、ユーザーのプライマリメールボックスとアーカイブメールボックスが異なる地理的位置にある場合に発生します。これは、複数地域のメールボックスの移動が異なる時刻に完了する可能性があるためです。

- ユーザーは、Outlook on the web (旧 Outlook web App または OWA) の地理的位置を跨いで*メールボックスフォルダー*を共有できません。 たとえば、欧州連合のユーザーが Outlook on the web を使用して、米国にあるメールボックス内の共有フォルダーを開くことはできません。 ただし、Outlook on the Web では、 「[Outlook Web App の別のブラウザー ウィンドウで他のユーザーのメールボックスを開く](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362)」の説明に従って、別のブラウザー ウィンドウを使って異なる地理的位置にある*他のメールボックス*を開くことができます。

  **注**: 地域間のメールボックスフォルダーの共有は、Outlook on the Windows でサポートされています。

- 複数地域にある組織では、パブリックフォルダーがサポートされています。 ただし、パブリックフォルダーは中央の地理的位置に設定する必要があります。 パブリックフォルダーをサテライトの地理的位置に移動することはできません。

- 複数地域環境では、複数地域のメールボックスの監査はサポートされていません。 たとえば、異なる地理的位置にある共有メールボックスにアクセスする権限がユーザーに割り当てられている場合、そのユーザーが実行したメールボックス操作は、共有メールボックスのメールボックス監査ログに記録されません。 詳細については、「[メールボックスの監査を管理する](https://docs.microsoft.com/microsoft-365/compliance/enable-mailbox-auditing?view=o365-worldwide)」を参照してください。
