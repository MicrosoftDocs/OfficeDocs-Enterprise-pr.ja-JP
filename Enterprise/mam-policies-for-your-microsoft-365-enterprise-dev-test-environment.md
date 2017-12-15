---
title: "Microsoft 365 エンタープライズ開発/テスト環境の MAM のポリシー"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_TLGs
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: "概要: は、Microsoft 365 の開発/テスト環境に EMS のモバイル アプリケーションの管理 (MAM) ポリシーを追加するのには、このテスト ラボ ガイド 』 を使用します。"
ms.openlocfilehash: d088970dca1ec55212642f16d0519e89bd9591e5
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="mam-policies-for-your-microsoft-365-enterprise-devtest-environment"></a>Microsoft 365 エンタープライズ開発/テスト環境の MAM のポリシー

 **の概要:**Microsoft 365 開発/テスト環境に EMS のモバイル アプリケーションの管理 (MAM) ポリシーを追加するのにには、このテスト ラボ ガイド 』 を使用します。
  
Microsoft エンタープライズ モビリティとセキュリティ (EMS) は、組織のデータを保護しながら、お気に入りのアプリケーションとデバイスを使用して生産性の高い従業員を保つことができます。詳細については、[エンタープライズ ・ モビリティとセキュリティ (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)を参照してください。
  
この資料の手順についてで Microsoft 365 の開発/テスト環境にモバイル アプリケーションの管理 (MAM) ポリシーを追加します。
  
## <a name="phase-1-build-out-your-microsoft-365-devtest-environment"></a>フェーズ 1: Microsoft 365 の開発/テスト環境を構築します。

[[Microsoft 365 エンタープライズ開発/テスト環境](the-microsoft-365-enterprise-dev-test-environment.md)での指示に従います。
  
## <a name="phase-2-create-and-deploy-mam-policies-for-ios-and-android-devices"></a>フェーズ 2:iOS デバイスと Android デバイス用の MAM ポリシーを作成し展開する

このフェーズでは、2 つの異なる MAM ポリシー (1 つは iOS デバイス用、もう 1 つは Android デバイス用) を作成し展開します。
  
1. Office 365 ポータル ([https://portal.office.com](https://portal.office.com)) に移動し、グローバル管理者アカウントで Office 365 試用版サブスクリプションにサインインします。
    
2. 、お使いのブラウザーの新しいタブで、Azure ポータル ([https://azure.portal.com](https://azure.portal.com)) を開き、Office 365 のグローバル管理者アカウントを使用してサインインします。
    
3. [Azure ポータル] タブで、Internet Explorer のナビゲーション ウィンドウで**その他のサービス**(または右矢印) をクリックしてし、入力**Intune**、 **Intune**] をクリックします。
    
4. 左側のナビゲーション ウィンドウで、**[グループ]** をクリックします。
    
5. **ユーザーおよびグループのすべてのグループ**のブレードでは、[**追加**] をクリックします。
    
6. **グループ**ブレードの**名前**、 **iOS デバイスのユーザーの管理**を入力**割り当て****メンバーシップの種類**を選択**[はい]**の**を有効にする Office 機能ですか?**、し、[**作成**] をクリックします。 
    
7. **グループ**のブレードを閉じます。
    
8. **ユーザーおよびグループのすべてのグループ**のブレードでは、[**追加**] をクリックします。
    
9. **グループ**のブレードで**Android 管理デバイスのユーザー** **名**、入力**割り当てられた****メンバーシップの種類**を選択**[はい]**の**を有効にする Office 機能ですか?**、し、[**作成**] をクリックします。
    
10. **ユーザーとグループのグループのすべての**ブレードを閉じます。
    
11. **クイック タスク**の一覧で、 **Intune**ブレードの**コンプライアンス ポリシーの作成**をクリックします。
    
12. **コンプライアンス ・ ポリシーのプロファイル**のブレードでは、**ポリシーの作成**をクリックします。
    
13. **ポリシーの作成**・ ブレードの**名前**、 **iOS**を入力します。**プラットフォーム**では、 **iOS**を選択、 **iOS コンプライアンス ・ ポリシー** ・ ブレードの上の [ **OK** ] をクリックでし、[**作成**] をクリックします。
    
14. **コンプライアンス ・ ポリシーのプロファイル**のブレードでは、**ポリシーの作成**をクリックします。
    
15. **ポリシーの作成**のブレードで [**名前**を入力**Android**。**プラットフォーム**、 **Android**を選択、 **Android のコンプライアンス ・ ポリシー** ・ ブレードの上の [ **OK** ] をクリックでし、[**作成**] をクリックします。
    
16. **コンプライアンス ポリシーのプロファイル**のブレード、 **Android**のポリシー名をクリックします。
    
17. **Android - プロパティ**のブレードの左側のナビゲーションでは、**割り当て**をクリックし、**グループの選択**] をクリックします。
    
18. **グループを選択して**ブレードの**Android 管理デバイスのユーザー**グループをクリックし、**選択**] をクリックします。
    
19. **保存**] をクリックして、**アプリの割り当て**のブレードを閉じます。
    
20. **コンプライアンス ・ ポリシーのプロファイル**のブレードでは、 **iOS**のポリシー名をクリックします。
    
21. **IOS - プロパティ**のブレードの左側のナビゲーションでは、**割り当て**をクリックし、**グループの選択**] をクリックします。
    
22. **グループを選択して**ブレードの**iOS デバイスのユーザーを管理**グループをクリックし、**選択**] をクリックします。
    
23. **保存**] をクリックし、 **iOS の割り当て**のブレードを閉じます。
    
24. **コンプライアンス ポリシーのプロファイル**のブレードを閉じます。
    
25. **Intune**ブレードの左側のナビゲーションで [**管理アプリケーション**] をクリックします。
    
26. **モバイル アプリケーション**のブレードでは、**アプリケーション**をクリックします。
    
27. アプリケーションの一覧で、 **PowerPoint**をクリックします。 
    
28. **PowerPoint 概要**ブレードでは、をクリックして**の割り当て > グループを選択して > iOS デバイスを管理する > を選択して**。**型**の場合は、**利用可能**時間を選択し、し、[**保存**] をクリックします。
    
29. 以下のアプリで、手順 28 を繰り返します。
    
  - Outlook for Android
    
  - Word for iOS
    
  - Excel for iOS
    
  - iOS 版 Outlook
    
  - Microsoft Dynamics CRM on iPad for iOS
    
  - Microsoft Dynamics CRM on iPhone for iOS
    
  - 電話用 Dynamics CRM for Android
    
  - タブレット用 Dynamics CRM for Android
    
  - Excel for Android
    
  - Word for Android
    
  - OneNote for iOS
    
30. **モバイル アプリケーション - アプリケーション**のブレードを閉じます。
    
31. **モバイル アプリケーション**のブレードでは、**アプリケーション保護ポリシー**をクリックします。
    
32. **アプリケーション保護ポリシー** ・ ブレードの上には、**ポリシーの追加**をクリックします。
    
33. **ポリシーの追加**のブレードでは、 **iOS**を入力し、**必要なアプリケーションの選択**] をクリックします。
    
34. **アプリ**のブレードでは、 **PowerPoint** **iPhone 上の Microsoft Dynamics CRM**、 **Excel** **iPhone 上の Microsoft Dynamics CRM**、 **Word**、 **OneNote**、および**Outlook**をクリックし、**選択**] をクリックします。
    
35. **追加ポリシー**ブレードの**作成**を] をクリックします。
    
36. **アプリケーション保護ポリシー** ・ ブレードの上には、**ポリシーの追加**をクリックします。
    
37. **追加ポリシー**ブレード、 **Android**を入力、**プラットフォーム**、 **Android**を選択および**必要なアプリケーションの選択**] をクリックします。
    
38. **アプリ**のブレードでは、 **PowerPoint****タブレットの Dynamics CRM**、 **Excel**、 **Word**、 **Outlook**、および**電話の Dynamics CRM**をクリックし、**選択**] をクリックします。
    
39. **追加ポリシー**ブレードの**作成**を] をクリックします。
    
これで、2 つの MAM ポリシー (1 つは iOS デバイス用、もう 1 つは Android デバイス用) が設定され、選択されたアプリの設定をテストする用意ができました。
  
> [!TIP]
> クリックしては、[ここで](http://aka.ms/catlgstack)1 つのマイクロソフト クラウド テスト ラボ ガイド スタック内のアーティクルのすべてのビジュアル マップです。
  
## <a name="see-also"></a>See Also

[Microsoft 365 Enterprise 開発/テスト環境](the-microsoft-365-enterprise-dev-test-environment.md)
  
[あっ、マイクロソフトのエンタープライズ 365 の開発/テスト環境でを登録します。](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[クラウド導入のテスト ラボ ガイド (TLG)](cloud-adoption-test-lab-guides-tlgs.md)

[エンタープライズ モビリティとセキュリティ (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


