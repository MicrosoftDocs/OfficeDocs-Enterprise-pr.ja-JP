---
title: Microsoft 365 Enterprise 開発/テスト環境に iOS および Android デバイスを登録する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/20/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: '概要: ガイドを使用してこのテスト ラボ Microsoft 365、開発/テスト環境でデバイスを登録し、それらをリモートで管理します。'
ms.openlocfilehash: e4b8491a70d0d0177e0a434d228136243201e788
ms.sourcegitcommit: c3869a332512dd1cc25cd5a92a340050f1da0418
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/20/2018
ms.locfileid: "20720413"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-enterprise-devtest-environment"></a>Microsoft 365 Enterprise 開発/テスト環境に iOS および Android デバイスを登録する

 **の概要:** Microsoft 365、開発/テスト環境でデバイスを登録し、それらをリモートで管理するには、このテスト ラボ ガイド 』 を使用します。
  
Microsoft エンタープライズ モビリティ スイート (EMS) では、組織のデータを保護しながら、お気に入りのアプリケーションとデバイスを使用して生産性の高い従業員を保つことができます。詳細については、[エンタープライズ ・ モビリティとセキュリティ (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)を参照してください。
  
デバイス ・ レベルでセキュリティを適用する場合は、Microsoft Intune にデバイスを登録する必要があります。デバイスの登録を組織が所有するデバイスを管理するために役立つだけでなく個人 (BYOD) と共有デバイスには、組織が法的なのもいますが、ポリシーです。
  
によって、この資料に記載されている手順に従うことができます登録し、iOS および Android デバイスの基本的なモバイル デバイス管理の機能を Microsoft 365 開発/テスト環境でテストします。
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a>フェーズ 1: Microsoft 365 の開発/テスト環境を作成します。

[[Microsoft 365 エンタープライズ開発/テスト環境](the-microsoft-365-enterprise-dev-test-environment.md)での指示に従います。
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a>フェーズ 2: iOS および Android デバイスを登録します。

指示を使用して、最初に、[をインストールし、会社のポータル アプリケーションにサインイン](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios)、テスト環境を Microsoft Intune 会社のポータル アプリケーションをカスタマイズするのには。

次に、手順を使用[、会社のリソースへのアクセス権を設定](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios)iOS デバイスを登録します。

次に、手順を使用[Intune に Android デバイスの登録](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android)Android のデバイスを登録します。

## <a name="phase-3-manage-your-ios-and-android-devices-remotely"></a>フェーズ 3: は、iOS および Android のデバイスをリモートで管理します。

Microsoft Intune では、リモート ロックとパスコードの両方のリセット機能を提供します。他のユーザーを失った場合、デバイス、デバイスをリモートでロックできます。パスコードを忘れてしまった人の場合リモートでリセットすることができます。
  
IOS または Android デバイスをリモートでロック。

1. Azure ポータルにサインインするのに[https://portal.azure.com](https://portal.azure.com)のグローバル管理者アカウントの資格情報を使用します。
2. **すべてのサービス**をクリックして、 **Intune**を入力し、 **Intune**] をクリックします。
3. クリックして**デバイス > のすべてのデバイス**。
4. デバイスの一覧で、iOS または Android デバイスをクリック**リモート ロック**の動作です。

    
パスコードをリモートからリセットするには、

1. 必要な場合がある Azure ポータルにサインイン[https://portal.azure.com](https://portal.azure.com)のグローバル管理者アカウントの資格情報を使用します。
2. **すべてのサービス**をクリックして、 **Intune**を入力し、 **Intune**] をクリックします。
3. クリックして**デバイス > のすべてのデバイス**。
4. デバイスの一覧から管理、iOS または Android デバイスをクリックして**を選択.詳細**。**パスコードを削除する**デバイスのリモート操作を選択します。

追加の実験を行うには、[利用可能なデバイスの操作](https://docs.microsoft.com/intune/device-management#available-device-actions)を参照してください。

    

> [!TIP]
> [ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。
  
## <a name="see-also"></a>関連項目

[Microsoft 365 Enterprise 開発/テスト環境](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Microsoft 365 エンタープライズ開発/テスト環境の MAM のポリシー](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[クラウド導入のテスト ラボ ガイド (TLG)](cloud-adoption-test-lab-guides-tlgs.md)

[エンタープライズ モビリティとセキュリティ (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


