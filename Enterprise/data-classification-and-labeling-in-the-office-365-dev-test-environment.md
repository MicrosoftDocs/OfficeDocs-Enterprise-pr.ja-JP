---
title: Office 365 開発/テスト環境でのデータ分類とラベルの作成
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 919b8fc7-b0bc-46db-91f5-37342564e01b
description: 概要：Office 365 開発/テスト環境で Azure Information Protection (AIP) クライアントを使用して、データ分類とラベルの設定とデモを行います。
ms.openlocfilehash: 66bdbb74ae88e10d5aa4fce2173f9a2b88a15e9b
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741353"
---
# <a name="data-classification-and-labeling-in-the-office-365-devtest-environment"></a>Office 365 開発/テスト環境でのデータ分類とラベルの作成

 **概要：** Office 365 開発/テスト環境で Azure Information Protection (AIP) クライアントを使用して、データ分類とラベルの設定とデモを行います。
  
Azure Information Protection クライアントを使用すると、Office 365 の SharePoint Online フォルダーにドキュメントをアップロードする前に、ドキュメントを分類できます。 この記事の指示に従って、Azure Information Protection クライアントをインストールし、データ分類をデモします。 詳細については、「 [Azure information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection)」を参照してください。
  
> [!TIP]
> Office 365 のテストラボガイドスタックにあるすべての記事のビジュアルマップについては、[ここ](http://aka.ms/catlgstack)をクリックしてください。
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>フェーズ 1: Office 365 開発/テスト環境を構成する

[Office 365 dev/test environment](office-365-dev-test-environment.md) の手順を実行します。
  
## <a name="phase-2-add-the-azure-information-protection-trial-subscription"></a>フェーズ 2:Azure Information Protection 試用版サブスクリプションを追加する

このフェーズでは、Azure Information Protection を Office 365 開発/テスト環境に追加して、お使いのユーザー アカウントで有効にします。 [Office 365 and EMS dev/test environment](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx) を構成した場合、このフェーズをスキップします。 Enterprise Mobility Suite 試用版サブスクリプションには、Azure Information Protection ライセンスが含まれます。
  
最初に、Azure Information Protection 試用版サブスクリプションの新規登録を行います。
  
### <a name="sign-up-for-an-azure-information-protection-trial-subscription"></a>Azure Information Protection 試用版サブスクリプションの新規登録

1. Internet Explorer またはブラウザーで、に[http://admin.microsoft.com](http://admin.microsoft.com)移動して、Office 365 のグローバル管理者アカウントでサインインします。
    
2. **[Microsoft Office Home]** タブで、**[管理者]** タイルをクリックします。
    
3. [Office 365 管理] タブの左側のナビゲーションで **[請求]、[サービスを購入する]** の順にクリックします。
    
4. **[サービスを購入]** ページで、**[Azure Information Protection Premium P2]** の項目を探します。マウスでポイントし、**[無料試用版の開始]** をクリックします。
    
5. **[注文の確認]** ページで、**[今すぐ実行]** をクリックします。
    
6. **[注文の受領書]** ページで、**[続行]** をクリックします。
    
次に、すべてのユーザー アカウントで Azure Information Protection  ライセンスを有効にします。
  
1. [Microsoft 365 管理センター] タブで、[**ユーザー**] をクリックします。
    
2.   ユーザー アカウントの一覧で、全体管理者アカウントを選択し、**[製品ライセンス]** で **[編集]** をクリックします。
    
3. **Azure Information Protection Premium P2** の製品ライセンスを **[オン]** にし、**[保存]** をクリックしてから、**[閉じる]** を 2 回クリックします。
    
4. 他のユーザー アカウント (ユーザー 1 ～ユーザー 5) について、手順 2 と 3 を繰り返します。
    
Office 365 開発/テスト環境には、以下が含まれるようになりました。
  
- Office 365 E5 Enterprise と Azure Information Protection の試用版サブスクリプション。
    
- すべてのユーザー アカウントで Office 365 E5 Enterprise と Azure Information Protection の両方が使用可能になっている。
    
## <a name="phase-3-demonstrate-data-classification"></a>フェーズ 3:データ分類のデモ 

このフェーズでは、Azure Information Protection クライアントと既定の Azure Information Protection ポリシーを使用してデータ分類をデモします。
  
シミュレーション エンタープライズの Office 365 開発/テスト環境を使用する場合は、最初に CLIENT1 で Office 2016 をインストールする必要があります。
  
1. ブラウザーを使用して、 [Azure portal](http://portal.azure.com)に移動します。
    
2. **[リソース グループ] > **[リソース グループ名] > **[クライアント 1] > **[コネクト] をクリックします。
    
3. CLIENT1 から Internet Explorer を実行し、Office ポータル[http://admin.microsoft.com](http://admin.microsoft.com)に移動して、User5 のアカウント名とパスワードを使用してサインインします。
    
4. **[Microsoft Office Home]** タブで、**[Office 2016 のインストール]** をクリックします。
    
5. 	画面の指示に従ってダウンロードを実行し、ユーザー アカウント制御のメッセージが表示されたら **[はい]** をクリックします。Office がインストールされるのを待ちます。完了したら、**[閉じる]** を 2 回クリックします。
    
次に、Azure Infomation Protection クライアントをインストールします。
  
1. ブラウザーまたは Internet Explorer で、 [Microsoft Azure Information Protection のダウンロードページ](https://www.microsoft.com/download/details.aspx?id=53018)に移動します。
    
  - Office 365 開発/テスト環境の簡易版を使用している場合は、ローカル コンピューターのブラウザーを使用します。
    
  - シミュレーション エンタープライズの Office 365 開発/テスト環境を使用している場合は、CLIENT1 から Internet Explorer を実行します。
    
2. **Microsoft Azure Information Protection** のダウンロード ページで、**[ダウンロード]**、**[AzInfoProtection.exe]**、**[次へ]** の順にクリックします。
    
3. 指示に従い、AzInfoProtection.exe を実行します。
    
4. **[Azure Information Protection のインストール]** クライアント ボックスで、**[同意します]** をクリックし、ユーザー アカウント制御のメッセージが表示されたら、**[はい]** をクリックします。
    
5. **[正常に完了しました]** ボックスで、**[閉じる]** をクリックします。
    
次に、ドキュメント分類をデモします。
  
1. タスクバーの **[Word]** アイコンをクリックします。
    
2. 指示に従い、User5 のアカウント名とパスワードでサインインします。
    
3. CLIENT1 で Office 2016 をインストールしたばかりの場合、**[はじめに]** のボックスで **[同意します]** をクリックします。
    
4. **[空白の文書]** をクリックします。  
    
    **[ホーム]** タブのリボンの **[保護]** セクションとドキュメント分類の行に注意します。
    
5. 空白の文書にテキストを入力します。
    
6. **[ファイル] > [保存]** をクリックし、名前として「**BeforeAIP**」を入力し、**[OK]** をクリックします。  
    
7. ドキュメント分類の行で、**[シークレット]** の下矢印をクリックし、**[すべての会社]** をクリックします。
    
8. **[ファイル] > [名前を付けて保存]** をクリックし、「**BeforeAIP**」と入力して **[OK]** をクリックします。
    
9. タスクバーの **[ファイル エクスプローラー]** をクリックして、**[ドキュメント]** フォルダーを開きます。
    
    **BeforeAIP** と **AfterAIP** のドキュメントのファイル サイズの違いに注意します。 beforeaip ドキュメントは、分類情報を持っているため、大きくなります。
    
次に、すべてのユーザーにサポート サイト コレクションへのアクセスを許可します。
  
1. **[Microsoft Office Home]** タブで **[SharePoint]** をクリックします。
    
2. **[SharePoint]** タブから **[サポート サイト コレクション]** をクリックします。
    
3. 右上部分の **[設定]** アイコンをクリックし、**[共有アイテム]** をクリックします。
    
4. [**共有 ' サポートサイトコレクション '**] で、[**詳細設定**] をクリックします。
    
5. SharePoint グループの一覧で **[サポート サイト コレクションのメンバー]** をクリックします。
    
6. **[ユーザーとグループ]** ページで、**[新規]** をクリックします。
    
7. [**共有 ' サポートサイトコレクション '**] で、「 **everyone**」と入力し、[**外部ユーザー以外のすべてのユーザー**] をクリックして、[共有] をクリックし**ます。**
    
8. **[ユーザーとグループ]** タブを閉じます。
    
次に、User5 のアカウントでサインインし、AIP で保護されたドキュメントをサポート サイト コレクションのドキュメント フォルダーにアップロードします。
  
1. **[Microsoft Office Home]** タブの右上部分の [ユーザー] アイコンをクリックし、**[サインアウト]** をクリックします。
    
2. [http://admin.microsoft.com](http://admin.microsoft.com) に移動します。
    
3. **Office 365 のサインイン**ページで、User5 のアカウント名をクリックして、サインインします。
    
4. **[Microsoft Office Home]** タブで、**[SharePoint] > [サポート サイト コレクション] > [ドキュメント]** をクリックします。
    
5. **[ドキュメント]** をクリックし、**[アップロード]** をクリックし、**AfterAIP** ドキュメントを選択して **[開く]** をクリックします。
    
    サポート サイト コレクションのドキュメント フォルダーの AfterAIP.docx を参照してください。
    
## <a name="see-also"></a>関連項目

[クラウド導入のテスト ラボ ガイド (TLG)](cloud-adoption-test-lab-guides-tlgs.md)

[Office 365 と EMS の開発/テスト環境](http://technet.microsoft.com/library/c76eea86-d4b6-4d35-ad89-341696e89ef7.aspx)
  
[Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection)


