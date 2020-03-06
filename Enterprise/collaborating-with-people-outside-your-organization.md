---
title: 組織外のユーザーとの共同作業
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
ms.collection: SPO_Content
localization_priority: Normal
f1.keywords: NOCSH
description: 組織外のユーザーとのグループ作業用に Microsoft 365 を構成する方法について説明します。
ms.openlocfilehash: 4cfaabd04a1f66592ab558bdca964fb6a1042855
ms.sourcegitcommit: 4e50f43857f93f42b71650354d1aec9ed4cc7fe2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "42549086"
---
# <a name="collaborating-with-people-outside-your-organization"></a>組織外のユーザーとの共同作業

Microsoft 365 では、既定では、組織外のユーザーとの共有は SharePoint と OneDrive で有効になっていますが、Teams では無効になっています。 SharePoint および OneDrive の外部共有シナリオの多くは、それ以上の構成を行わなくても動作します。 使用しているシナリオの設定を確認するか、または新しいシナリオを有効にするには、次のオプションのいずれかを選択します。

- [ドキュメントに対して共同作業](collaborate-on-documents.md)を行う: Microsoft 365 を構成して、ファイルとフォルダーの組織外のユーザー (ゲストと認証されていないユーザーの両方) との共有と共同作業を可能にする方法について説明します。
- [サイトでの共同作業](collaborate-in-a-site.md)-ゲストを使用した SharePoint サイトの共有を有効にするように Microsoft 365 を構成する方法について説明します。
- [チームとしての共同作業](collaborate-as-a-team.md)-Teams でゲストコラボレーションを有効にするように Microsoft 365 を構成する方法について説明します。

Microsoft 365 で使用可能なゲスト共有設定の包括的な説明については、「 [microsoft 365 ゲスト共有設定のリファレンス](microsoft-365-guest-settings.md)」を参照してください。

## <a name="secure-your-environment"></a>環境をセキュリティで保護する

組織外のユーザーとの共有に使用するシナリオを有効にしたら、偶発的または故意に不適切な共有からコンテンツを保護するための追加の保護機能を検討します。

- 認証されていない[ユーザーとファイルやフォルダーを共有するためのベストプラクティス](best-practices-anonymous-sharing.md)-認証されていないユーザーとの共有のベストプラクティスについて説明します。
- [偶発的な公開を制限](sharing-limit-accidental-exposure.md)する: 機密コンテンツを誤って組織外のユーザーと共有する危険性を軽減する方法について説明します。
- [セキュリティで保護されたゲスト共有環境を作成する](create-a-secure-guest-sharing-environment.md))-組織外のユーザーとの共有が安全かつ安全な方法で行われ、ガバナンスの要件を満たしていることを確認するために、Microsoft 365 で提供されるツールについて説明します。

## <a name="collaborate-with-partner-companies"></a>パートナー企業との共同作業

他の組織から多数のゲストが参加している大規模なプロジェクトで作業している場合、またはゲストが頻繁に変更されている、継続的なベンダーの関係がある場合は、Azure Active Directory の資格管理を使用してゲスト管理を簡略化できます。パートナー企業がその責任で共有できるようにします。 詳細について[は、「管理されたゲストでの B2B エクストラネットの作成](b2b-extranet.md)」を参照してください。

## <a name="limit-sharing"></a>共有を制限する

Microsoft 365 の共有機能の一部がガバナンスポリシーと競合している場合は、「 [365 microsoft の](microsoft-365-limit-sharing.md)共有を制限する」を参照して、共有の制限のオプションについて確認してください。

## <a name="see-also"></a>関連項目

[Microsoft 365 でのファイルの共同作業の概要](https://docs.microsoft.com/sharepoint/intro-to-file-collaboration)

[Microsoft 365 を使用して SharePoint でファイルのコラボレーションを計画する](https://docs.microsoft.com/sharepoint/deploy-file-collaboration)
