---
title: Exchange Multi-Geo
ms.author: chrisda
author: chrisda
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: Exchange Online の複数地域機能について説明します。
ms.openlocfilehash: 60d25cab08ada195d1b189b30bdce8ea505f1d19
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "30931776"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a>Exchange Online の複数地域機能

複数地域環境では、ユーザーごとに Exchange Online メールボックスコンテンツ (rest のデータ) の場所を選択できます。

メールボックスは、次の方法でサテライトの場所に配置できます。

- サテライトの場所に新しい Exchange Online メールボックスを直接作成する

- ユーザーの優先するデータの場所を変更することにより、既存の Exchange Online メールボックスをサテライトの場所に移動する

- オンプレミスの Exchange 組織からメールボックスを直接サテライトの場所にオンボードする

## <a name="mailbox-placement-and-moves"></a>メールボックスの配置と移動
Microsoft が前提条件となる複数地域構成手順を完了すると、Exchange Online は Azure AD のユーザーオブジェクトに対して**PreferredDataLocation**属性を優先します。

exchange online は、 **PreferredDataLocation**プロパティを Azure AD から exchange online ディレクトリサービスの**MailboxRegion**プロパティに同期します。 **MailboxRegion**の値は、ユーザーのメールボックスと、関連付けられたアーカイブメールボックスが配置される地域を決定します。 ユーザーのプライマリメールボックスとアーカイブメールボックスを異なる地域の場所に配置するように構成することはできません。 ユーザーオブジェクトごとに構成できる geo の場所は1つだけです。

- 既存のメールボックスを持つユーザーに対して**PreferredDataLocation**が構成されている場合、メールボックスは再配置キューに入れられ、指定した地域の場所に自動的に移動されます。 

- 既存のメールボックスがないユーザーに対して**PreferredDataLocation**が構成されている場合、メールボックスのプロビジョニング時に、指定された地理的位置にプロビジョニングされます。 

- **PreferredDataLocation**がユーザーに対して指定されていない場合、メールボックスを準備すると、そのメールボックスは中央の場所にプロビジョニングされます。

- **PreferredDataLocation**のコードが正しくない場合 (たとえば、タイプが NAN ではなく NAN)、メールボックスは中央の場所にプロビジョニングされます。

**注**: 複数地域機能と Skype for business Online 地域的 hosted 会議の両方で、ユーザーオブジェクトの**PreferredDataLocation**プロパティを使用してサービスを検索します。 地域的でホストされている会議のユーザーオブジェクトに対して**PreferredDataLocation**値を構成すると、そのユーザーのメールボックスは、Office 365 テナントで複数地域を有効にした後、指定した地域の場所に自動的に移動されます。

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a>Exchange Online の複数地域における機能上の制限

1. Exchange 管理センター (EAC) で使用可能なセキュリティおよびコンプライアンス機能 (監査、電子情報開示など) は、複数地域の組織では使用できません。 代わりに、 [Office 365 security & コンプライアンスセンター](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8)を使用して、セキュリティとコンプライアンスの機能を構成する必要があります。

2. Outlook for Mac のユーザーは、自分のメールボックスを新しい地域の場所に移動している間、オンラインアーカイブフォルダーへのアクセスが一時的に失われる可能性があります。 この条件は、ユーザーのプライマリメールボックスとアーカイブメールボックスが異なる地域の場所にある場合に発生します。これは、異なる地域間メールボックスの移動が異なる時間に完了する可能性があるためです。

3. ユーザーが*メールボックスフォルダー*を web 上の outlook (旧称 outlook web App または OWA) の地理的な場所の間で共有することはできません。 たとえば、欧州連合のユーザーは、Outlook on the web を使用して、米国にあるメールボックス内の共有フォルダーを開くことができません。 ただし、Web 上の outlook では、「[別のユーザーのメールボックスを outlook Web App の別のブラウザーウィンドウで開く](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362)」の説明に従って、別の geo で*他のメールボックス*を開くことができます。

    **注**: 地域間メールボックスフォルダーの共有は、Outlook on Windows でサポートされています。

