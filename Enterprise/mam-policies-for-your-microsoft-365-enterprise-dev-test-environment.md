---
title: Microsoft 365 Enterprise 開発/テスト環境の MAM のポリシー
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: '概要: は、Microsoft 365 の開発/テスト環境に EMS のモバイル アプリケーションの管理 (MAM) ポリシーを追加するのには、このテスト ラボ ガイド 』 を使用します。'
ms.openlocfilehash: 0a5c81665edf06631b8cebc57c9e715c78d3d85e
ms.sourcegitcommit: c23b95d32a865e45be7843f38a1f23b5693ba76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "20188155"
---
# <a name="mam-policies-for-your-microsoft-365-enterprise-devtest-environment"></a>Microsoft 365 Enterprise 開発/テスト環境の MAM のポリシー

 **の概要:** Microsoft 365 開発/テスト環境に EMS のモバイル アプリケーションの管理 (MAM) ポリシーを追加するのにには、このテスト ラボ ガイド 』 を使用します。
  
Microsoft エンタープライズ モビリティとセキュリティ (EMS) は、組織のデータを保護しながら、お気に入りのアプリケーションとデバイスを使用して生産性の高い従業員を保つことができます。詳細については、[エンタープライズ ・ モビリティとセキュリティ (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)を参照してください。
  
この資料の手順についてで Microsoft 365 の開発/テスト環境にモバイル アプリケーションの管理 (MAM) ポリシーを追加します。
  
## <a name="phase-1-build-out-your-microsoft-365-devtest-environment"></a>フェーズ 1: Microsoft 365 の開発/テスト環境を構築します。

[[Microsoft 365 エンタープライズ開発/テスト環境](the-microsoft-365-enterprise-dev-test-environment.md)での指示に従います。
  
## <a name="phase-2-create-and-deploy-mam-policies-for-ios-and-android-devices"></a>フェーズ 2:iOS デバイスと Android デバイス用の MAM ポリシーを作成し展開する

このフェーズでは、2 つの異なる MAM ポリシー (1 つは iOS デバイス用、もう 1 つは Android デバイス用) を作成し展開します。
  
1. Office 365 ポータルに移動 ([https://portal.office.com](https://portal.office.com)) し、グローバル管理者アカウントを使用して、Office 365 の試用版サブスクリプションにサインインします。
    
2. 、お使いのブラウザーの新しいタブで開くには、Azure ポータル ([https://azure.portal.com](https://azure.portal.com)) し、Office 365 のグローバル管理者アカウントを使用してサインインします。
    
3. [Azure ポータル] タブで、Internet Explorer のナビゲーション ウィンドウで**すべてのサービス**] をクリックし、入力**Intune**、 **Intune**] をクリックします。
    
4. 左側のナビゲーション ウィンドウで、**[グループ]** をクリックします。
    
5. **グループのグループのすべての**ブレードでは、[ **+ 新しいグループ**をクリックします。
    
6. **グループ**・ ブレードの上の**Office 365**を選択**グループの種類ですか?** **iOS デバイスのユーザーの管理****名**、**メンバーシップの種類**、**割り当て**を選択して入力し、[**作成**] をクリックします。 
    
7. **[グループ]** ブレードを閉じます。
    
8. **グループのグループのすべての**ブレードでは、[**追加**] をクリックします。
    
9. **グループ**・ ブレードの上の**Office 365**を選択**グループの種類ですか?** **Android 管理デバイスのユーザー** **名**、**メンバーシップの種類**、**割り当て**を選択して入力し、[**作成**] をクリックします。
    
10. **グループのグループのすべての**ブレードを閉じます。
    
11. **[Intune]** ブレードの **[クイック タスク]** 一覧で、**[コンプライアンス ポリシーの作成]** をクリックします。
    
12. **[コンプライアンス ポリシー プロファイル]** ブレードで、**[ポリシーの作成]** をクリックします。
    
13. **[ポリシーの作成]** ブレードの **[名前]** で、「**iOS**」と入力します。**[プラットフォーム]** で **[iOS]** を選択し、**[iOS コンプライアンス ポリシー]** ブレードで **[OK]** をクリックし、次いで **[作成]** をクリックします。
    
14. **[コンプライアンス ポリシー プロファイル]** ブレードで、**[ポリシーの作成]** をクリックします。
    
15. **[ポリシーの作成]** ブレードの **[名前]** で、「**Android**」と入力します。**[プラットフォーム]** で **[Android]** を選択し、**[Android コンプライアンス ポリシー]** ブレードで **[OK]** をクリックし、次いで **[作成]** をクリックします。
    
16. **[コンプライアンス ポリシー プロファイル]** ブレードで、**Android** のポリシー名をクリックします。
    
17. **[Android - プロパティ]** ブレードの左側のナビゲーションで、**[割り当て]**、**[グループの選択]** の順にクリックします。
    
18. **[グループの選択]** ブレードで、**[管理された Android デバイス ユーザー]** グループをクリックし、**[選択]** をクリックします。
    
19. **保存**] をクリックして、**アプリの割り当て**のブレードを閉じます。
    
20. **[コンプライアンス ポリシー プロファイル]** ブレードで、**iOS** のポリシー名をクリックします。
    
21. **[iOS - プロパティ]** ブレードの左側のナビゲーションで、**[割り当て]**、**[グループの選択]** の順にクリックします。
    
22. **[グループの選択]** ブレードで、**[管理された iOS デバイス ユーザー]** グループをクリックし、**[選択]** をクリックします。
    
23. **保存**] をクリックし、 **iOS の割り当て**のブレードを閉じます。
    
24. **[コンプライアンス ポリシー プロファイル]** ブレードを閉じます。
    
25. **[Intune]** ブレードの左側のナビゲーションで、**[アプリの管理]** をクリックします。
    
26. **[モバイル アプリ]** ブレードで、**[アプリ]** をクリックします。
    
27. アプリの一覧で、**[PowerPoint]** をクリックします。  
    
28. **[PowerPoint の概要]** ブレードで、**[割り当て] > [グループの選択] > [iOS デバイスの管理] > [選択]** の順にクリックします。**[種類]** で、**[利用可能]** を選択して、**[保存]** をクリックします。
    
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
    
30. **[モバイル アプリ - アプリ]** ブレードを閉じます。
    
31. **[モバイル アプリ]** ブレードで、**[アプリ保護ポリシー]** をクリックします。
    
32. **[アプリ保護ポリシー]** ブレードで、**[ポリシーの追加]** をクリックします。
    
33. **[ポリシーの追加]** ブレードで、「**iOS**」と入力して、**[必要なアプリの選択]** をクリックします。
    
34. **[アプリ]** ブレードで、**[PowerPoint]**、**[Microsoft Dynamics CRM on iPhone]**、**[Excel]**、**[Microsoft Dynamics CRM on iPhone]**、**[Word]**、**[OneNote]**、**[Outlook]** をクリックし、**[選択]** をクリックします。
    
35. **[ポリシーの追加]** ブレードで、**[作成]** をクリックします。
    
36. **[アプリ保護ポリシー]** ブレードで、**[ポリシーの追加]** をクリックします。
    
37. **[ポリシーの追加]** ブレードで、「**Android**」と入力します。**[プラットフォーム]** で **[Android]** を選択して、**[必要なアプリの選択]** をクリックします。
    
38. **[アプリ]** ブレードで、**[PowerPoint]**、**[タブレット用 Dynamics CRM]**、**[Excel]**、**[Word]**、**[Outlook]**、**[電話用 Dynamics CRM]** をクリックし、**[選択]** をクリックします。
    
39. **[ポリシーの追加]** ブレードで、**[作成]** をクリックします。
    
これで、2 つの MAM ポリシー (1 つは iOS デバイス用、もう 1 つは Android デバイス用) が設定され、選択されたアプリの設定をテストする用意ができました。
  
> [!TIP]
> [ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。
  
## <a name="see-also"></a>関連項目

[Microsoft 365 Enterprise 開発/テスト環境](the-microsoft-365-enterprise-dev-test-environment.md)
  
[Microsoft 365 Enterprise 開発/テスト環境に iOS および Android デバイスを登録する](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[クラウド導入のテスト ラボ ガイド (TLG)](cloud-adoption-test-lab-guides-tlgs.md)

[エンタープライズ モビリティとセキュリティ (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


