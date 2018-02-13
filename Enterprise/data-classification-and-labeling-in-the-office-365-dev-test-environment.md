---
title: "Office 365 開発/テスト環境でのデータ分類とラベルの作成"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: TLG, Ent_TLGs
ms.assetid: 919b8fc7-b0bc-46db-91f5-37342564e01b
description: "概要: は、構成し、データのクラス分けと Azure の情報の保護 (AIP) クライアントを使用して、Office 365 の開発/テスト環境でのラベル付けについて説明します。"
ms.openlocfilehash: 84dc3b8d86a53f7c91d5c226b5c745f5d39731a9
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/13/2018
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a>Office 365 開発/テスト環境でのデータ分類とラベルの作成

 **の概要:**構成し、データのクラス分けと Azure の情報の保護 (AIP) クライアントを使用して、Office 365 の開発/テスト環境でのラベル付けについて説明します。
  
Azure の情報保護のクライアントを使用すると、Office 365 で SharePoint Online フォルダーにアップロードする前にドキュメントを分類できます。この資料の手順についてでは、Azure の情報保護のクライアントをインストールして、データのクラス分けを実演します。詳細については、 [Azure の情報の保護](https://www.microsoft.com/cloud-platform/azure-information-protection)を参照してください。
  
> [!TIP]
> 
            [ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>フェーズ 1: Office 365 開発/テスト環境を構築する

[Office 365 の開発/テスト環境](office-365-dev-test-environment.md)での指示に従います。
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a>フェーズ 2:Azure Information Protection 試用版サブスクリプションを追加する

このフェーズでは、Azure の情報の保護を Office 365 の開発/テスト環境に追加し、ユーザー アカウントを有効にします。[Office 365 と EMS の開発/テスト環境](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)を構成した場合は、このフェーズをスキップします。エンタープライズ ・ モビリティ ・ スイートの試用版サブスクリプションには、Azure の情報保護のライセンスが含まれています。
  
最初に、Azure Information Protection 試用版サブスクリプションの新規登録を行います。
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a>Azure Information Protection 試用版サブスクリプションの新規登録

1. Internet Explorer またはお使いのブラウザーでは、 [http://portal.office.com](http://portal.office.com)に移動し、Office 365 のグローバル管理者アカウントでサインインします。
    
2. **Microsoft Office ホーム**] タブで、**管理者**のタイルをクリックします。
    
3. Office 365 の管理] タブの左側のナビゲーションでをクリックして**請求 > サービスを購入する**です。
    
4. **購買サービス**] ページで、 **Azure の情報保護のプレミアム P2**の項目を検索します。上にマウス ポインターを置くし、**無料の試用期間の開始**] をクリックします。
    
5. **[注文の確認]** ページで、 **[今すぐ実行]** をクリックします。
    
6. **[注文の受領書]** ページで、**[続行]** をクリックします。
    
次に、すべてのユーザー アカウントで Azure Information Protection  ライセンスを有効にします。
  
1. [Office 365 管理センター] タブで、[**ユーザー**] をクリックします。
    
2.  、ユーザー アカウントの一覧でグローバル管理者アカウントを選択し、**製品ライセンス**の**編集**] をクリックします。
    
3. **上**に**情報保護プレミアム P2 の Azure**の製品のライセンスを有効にする**、保存**、**閉じる**を 2 回クリックします。
    
4. 他のユーザー アカウント (ユーザー 1 ～ユーザー 5) について、手順 2 と 3 を繰り返します。
    
Office 365 開発/テスト環境には、以下が含まれるようになりました。
  
- Office 365 E5 Enterprise と Azure Information Protection の試用版サブスクリプション。
    
- すべてのユーザー アカウントで Office 365 E5 Enterprise と Azure Information Protection の両方が使用可能になっている。
    
## <a name="phase-3-demonstrate-data-classification"></a>フェーズ 3:データ分類のデモ 

このフェーズでは、Azure Information Protection クライアントと既定の Azure Information Protection ポリシーを使用してデータ分類をデモします。
  
シミュレーション エンタープライズの Office 365 開発/テスト環境を使用する場合は、最初に CLIENT1 で Office 2016 をインストールする必要があります。
  
1. お使いのブラウザーを使用し、 [Azure ポータル](http://portal.azure.com)に移動します。
    
2. クリックして**リソース グループ >** [リソース グループ名] **> CLIENT1 > 接続**。
    
3. CLIENT1 で、Internet Explorer を実行で[http://portal.office.com](http://portal.office.com)Office のポータルに移動し、User5 アカウント名とパスワードを使用してサインインしています。
    
4. **Microsoft Office ホーム**] タブ、[ **Office 2016 のインストール**] をクリックします。
    
5. クリックするとメッセージが表示されたら [**はい]**ユーザー アカウント制御によって、ダウンロードを実行します。Office をインストールするを待ちます。完了したら、**閉じる**を 2 回クリックします。
    
次に、Azure Infomation Protection クライアントをインストールします。
  
1. ブラウザーまたは Internet Explorer、 [Microsoft Azure の情報保護のダウンロード ページ](https://www.microsoft.com/download/details.aspx?id=53018)に移動します。
    
  - Office 365 開発/テスト環境の簡易版を使用している場合は、ローカル コンピューターのブラウザーを使用します。
    
  - シミュレーション エンタープライズの Office 365 開発/テスト環境を使用している場合は、CLIENT1 から Internet Explorer を実行します。
    
2. **Microsoft Azure の情報保護**のダウンロード] ページで、[**ダウンロード**] をクリックして**AzInfoProtection.exe**、[**次へ**] をクリックします。
    
3. 指示に従い、AzInfoProtection.exe を実行します。
    
4. **Azure の情報保護をインストールする**クライアント] ボックスで [**同意する**] をクリックし、 **[はい]**で [ユーザー アカウント制御メッセージが表示されたら。
    
5. [**正常に完了しました**] ボックスに、**閉じる**。
    
次に、ドキュメント分類をデモします。
  
1. タスク バーの**Word**アイコンをクリックします。
    
2. 指示に従い、User5 のアカウント名とパスワードでサインインします。
    
3. だけで client1 で、2016 を Office をインストールしたかどうか、**まず最初**ボックスで、[**承諾**] をクリックします。
    
4. [**白紙の文書**] をクリックします。 
    
    **リボンの**[ホーム**] タブ、ドキュメントの分類の行のセクション**に注意してください。
    
5. 空白の文書にテキストを入力します。
    
6. クリックして**ファイル > 保存**、 **BeforeAIP**名前を入力し、し、[ **OK**] をクリックします。 
    
7. ドキュメント クラスの行の**シークレット**の下向き矢印をクリックし、**すべての会社**です。
    
8. クリックして**ファイル > 名前を付けて保存**、 **AfterAIP**名前を入力し、し、[ **OK**] をクリックします。
    
9. タスク バーに、**ファイル エクスプ ローラー**をクリックし、[**ドキュメント**] フォルダーを開きます。
    
    **BeforeAIP**と**AfterAIP**のドキュメントの別のファイルのサイズに注意してください。AfterAIP ドキュメントは、分類情報が含まれているために大きくなります。
    
次に、すべてのユーザーにサポート サイト コレクションへのアクセスを許可します。
  
1. **Microsoft Office ホーム**] タブ、[ **SharePoint**を] をクリックします。
    
2. [ **SharePoint** ] タブで、**サポートのサイト コレクション**をクリックします。
    
3. 、右上の**設定**アイコンをクリックする**と共有**] をクリックします。
    
4. **共有 'サポート サイト コレクション'**の場合は、[**詳細**] をクリックします。
    
5. SharePoint グループのリストでは、**サポート サイト コレクションのメンバー**をクリックします。
    
6. **[ユーザーとグループ]** ページで、 **[新規]** をクリックします。
    
7. **共有 'サポート サイト コレクション'**、**すべてのユーザー**を入力、**外部のユーザーを除くすべて**] をクリックし、**共有します**。
    
8. **ユーザーとグループ**] タブを閉じます。
    
次に、User5 のアカウントでサインインし、AIP で保護されたドキュメントをサポート サイト コレクションのドキュメント フォルダーにアップロードします。
  
1. [**マイクロソフト オフィス ホーム**] タブの右上にユーザー アイコンをクリックして [**サインアウト**] をクリックします。
    
2. [Http://portal.office.com](http://portal.office.com)に移動します。
    
3. * * Office 365 のサインイン * * ページ、User5 のアカウント名をクリックし、サインインします。
    
4. [ **Microsoft Office のホーム**] タブをクリックして**SharePoint > サイト コレクションをサポートする**です。
    
5. **ドキュメント**] をクリックして、[**アップロード**] をクリックして、 **AfterAIP**のドキュメント] をクリックし、し、[**開く**] をクリックします。
    
    サポート サイト コレクションのドキュメント フォルダーの AfterAIP.docx を参照してください。
    
## <a name="see-also"></a>関連項目

[クラウド導入のテスト ラボ ガイド (TLG)](cloud-adoption-test-lab-guides-tlgs.md)

[Office 365 と EMS の開発/テスト環境](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[Azure の情報の保護](https://www.microsoft.com/cloud-platform/azure-information-protection)


