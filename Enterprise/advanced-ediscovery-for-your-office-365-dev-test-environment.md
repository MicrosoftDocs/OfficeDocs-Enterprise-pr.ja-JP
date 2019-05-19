---
title: Office 365 の開発/テスト環境のアドバンスト eDiscovery
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: d4c49a6f-abfd-4d68-b353-259b4eefb033
description: '概要: Office 365 の開発/テスト環境で、サンプル データを使用して Office 365 アドバンスト eDiscovery を構成し、デモンストレーションします。'
ms.openlocfilehash: dc783672f8f667e424ad738d8eb9091732537ebe
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2019
ms.locfileid: "34162410"
---
# <a name="advanced-ediscovery-for-your-office-365-devtest-environment"></a>Office 365 の開発/テスト環境の Advanced eDiscovery

 **概要:** Office 365 の開発/テスト環境で、サンプル データを使用して Office 365 アドバンスト eDiscovery を構成し、デモンストレーションします。
  
Office 365 Advanced 電子情報開示を使用すると、電子メールやドキュメントなど、Office 365 に保存されているデータに関する関連情報をすばやく検索して分析できます。 これにより、特に訴訟の状況では、時間と経費を大幅に節約できます。 詳細については、「[Office 365 の高度な電子情報開示](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)」をご覧ください。
  
この記事の手順では、架空の契約問題に関するデータの小さなセットを作成し、そのデータをアドバンスト eDiscovery で分析します。
  
> [!TIP]
> [ここ](http://aka.ms/catlgstack)をクリックして、Office 365 のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップを確認してください。
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a>フェーズ 1: Office 365 の開発/テスト環境を作成する

最小限の要件で高度な電子情報開示をテストする場合は、「フェーズ2」と「フェーズ 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md)」の手順に従ってください。
  
シミュレートされたエンタープライズで高度な電子情報開示をテストする場合は、「365 Office のディレクトリ同期の開発/テスト環境」の手順に従ってください。
  
> [!NOTE]
> 高度な電子情報開示のテストでは、インターネットに接続されたシミュレートされたイントラネットと Active Directory ドメインサービス (AD DS) フォレストのディレクトリ同期を含む、シミュレートされたエンタープライズ環境を必要としません。 この記事は、一般的な組織を表す環境でテストと実験を実行できるようにするためのオプションとして提供されています。 
  
## <a name="phase-2-create-example-data-for-advanced-ediscovery"></a>フェーズ 2:アドバンスト eDiscovery 用のサンプル データを作成する

この手順では、電子メール メッセージを作成します。このメッセージをアドバンスト eDiscovery のケースで分析することになります。
  
1. Internet Explorer を開き、 [https://outlook.com](https://outlook.com) [Office 365 開発/テスト環境](office-365-dev-test-environment.md)のフェーズ2で作成した Outlook アカウントにサインインします。
    
  - ライトウェイトの開発/テスト環境を使用している場合は、Internet Explorer のプライベート セッションを開いて、ローカル コンピューターからサインインします。
    
  - シミュレートされたエンタープライズ開発/テスト環境を使用している場合は、[https://portal.azure.com](https://portal.azure.com)Azure portal () を使用して client1 仮想マシンに接続し、client1 からサインインします。
    
2. **[Outlook メール]** タブで、**[新規作成]** をクリックします。
    
3. [**宛先**] に、試用版サブスクリプションの User6 アカウントの電子メールアドレスを入力し**ます (User6 @。**<organization name> **. onmicrosoft.com**)。
    
4. 件名に、「**Test email 1**」と入力します。
    
5. 本文に、「**Tailspin contract draft**」と入力して、**[送信]** をクリックします。
    
6. **[Outlook メール]** タブで、**[新規作成]** をクリックします。
    
7. **[宛先]** に、試用版サブスクリプションの User6 アカウントの電子メール アドレスを入力します。
    
8. 件名に、「**Test email 2**」と入力します。
    
9. 本文に、「**Tailspin lunch meeting**」と入力して、**[送信]** をクリックします。
    
10. **[Outlook メール]** タブで、**[新規作成]** をクリックします。
    
11. **[宛先]** に、試用版サブスクリプションの User6 アカウントの電子メール アドレスを入力します。
    
12. 件名に、「**Test email 3**」と入力します。
    
13. 本文に、「**Tailspin contract disagreement**」と入力して、**[送信]** をクリックします。
    
14. 右上の隅にあるユーザー アイコンをクリックして、**[サインアウト]** をクリックします。
    
15. 新しいタブを開き、試用版サブスクリプションの User6 アカウントのアカウント[https://www.office.com](https://www.office.com)名とパスワードを使用して、Office 365 ポータル () にサインインします。
    
16. **[Office 365 ポータル]** タブで、**[メール]** をクリックします。
    
17. [ **User6** ] タブで、User6 が outlook の電子メールアカウントから3通のメールをすべて受信していることを確認します。
    
18. User6 の **Office 365 ポータルのタブ**に戻ります。
    
19. 右上の隅にあるユーザー アイコンをクリックして、**[サインアウト]** をクリックします。
    
この手順では、2 つの Word 文書を作成します。この文書をアドバンスト eDiscovery のケースで分析することになります。
  
1. **[Office]** ページで **[サインイン]** をクリックし、グローバル管理者アカウントの認証情報でサインインします。
    
2. 新しいタブで、運用中の SharePoint サイトの URL にアクセスします: **https://** <fictional organization name> **。 sharepoint.com/sites/production**
    
3. **[実稼働サイト コレクション]** タブの **[ドキュメント]** で **[新規] > [Word 文書]** をクリックします。
    
4. **[Word Online]** ページで、「**Tailspin draft contract**」と入力して、タイトルに **[保存済み]** と表示されるまで待ってから、**[Word Online]** ページのタブを閉じます。
    
5. **[実稼働サイト コレクション]** タブの **[ドキュメント]** で **[新規] > [Word 文書]** をクリックします。
    
6. **[Word Online]** タブで、「**Tailspin contract dispute notes**」と入力して、タイトルに **[保存済み]** と表示されるまで待ってから、**[Word Online]** タブを閉じます。
    
7. **[運用サイト コレクション]** タブのドキュメントの一覧に、**Document** および **Document1** が表示されます。
    
8. **[運用サイト コレクション]** タブを閉じます。
    
## <a name="phase-3-use-advanced-ediscovery-for-a-legal-dispute"></a>フェーズ 3: 法的な争議に高度な電子情報開示を使用する

残念なことに、Tailspin Toys との契約問題が訴訟にまで達してしまいました。 この手順では、「Tailspin contract」というテキストを含む電子メールとドキュメントを検索して分析するための高度な電子情報開示ケースを作成して構成します。
  
アドバンスト eDiscovery を使用するためのプロセスは、次のとおりです。
  
- セキュリティ&amp; /コンプライアンスセンターで検索を作成し、その結果を分析して、上級電子情報開示のために結果を準備します。
    
- アドバンスト eDiscovery でケースを作成して構成し、検索結果を分析します。
    
この手順では、「Tailspin contract」のセキュリティ&amp;コンプライアンスセンターで検索を作成し、結果を確認してから、高度な電子情報開示のために結果を準備します。
  
1. **Office 365 ポータル**のタブで、**[管理者]** をクリックします
    
2. 管理センターのタブにある左側のナビゲーションで、**[管理センター]、[コンプライアンス]** をクリックします。
    
3. [**セキュリティ&amp;のコンプライアンス**] タブで、[**アクセス許可**] をクリックします。
    
4. **[アクセス許可]** リストで、**[Organization Management]** をダブルクリックします。
    
5. **[役割グループ]** ウィンドウで、**[メンバー]** のプラス記号をクリックします。
    
6. **[メンバーの選択]** ウィンドウで、管理者アカウントの名前をダブルクリックして、**[OK]** をクリックします。
    
7. **[役割グループ]** ウィンドウで、**[保存]** をクリックします。
    
8. **[アクセス許可]** リストで、**[電子情報開示マネージャー]** をダブルクリックします。
    
9. **[役割グループ]** ウィンドウで、**[電子情報開示の管理者]** のプラス記号のアイコンをクリックします。
    
10. **[メンバーの選択]** ウィンドウで、管理者アカウントの名前をダブルクリックして、**[OK]** をクリックします。
    
11. **[役割グループ]** ウィンドウで、**[保存]** をクリックします。
    
12. 左側のナビゲーションで、[**検索&amp;調査 > コンテンツ検索**] をクリックします。
    
13. プラス記号のアイコンをクリックして、検索を追加します。
    
14. **[新規検索]** ウィンドウで、**[名前]** に「**Tailspin contract search**」と入力します。
    
15. **[どこを調べますか?]** で、**[すべての場所の検索]** をクリックし、**[Exchange]**、**[SharePoint]**、および **[パブリック フォルダー]** を選択して、**[次へ]** をクリックします。
    
16. **[どこを調べますか?]** で、「**Tailspin contract**」と入力して、**[検索]** をクリックします。
    
17. 検索のリストで、名前 **[Tailspin contract search]** をクリックします。
    
18. **[Tailspin contract search]** ウィンドウで、**[結果]** の **[検索結果のプレビュー]** をクリックします。 作業中の SharePoint サイト (**ドキュメント**と**文書**1) に2つのドキュメントが一覧表示され、User6 への電子メールの**テスト**と**電子メール 3**の電子メールのテストが表示されます。 ウィンドウを閉じます。
    
19. **[コンテンツ検索]** ウィンドウで、**[アドバンスト eDiscovery による結果の分析]** の **[分析用の結果のプレビュー]** をクリックします。
    
20. **[Tailspin contract search の検索結果の準備]** ウィンドウで、**[準備]** をクリックして完了まで待機します。
    
この手順では、アドバンスト eDiscovery の新しケースを作成し、Tailspin contract search の結果を分析します。
  
1. 左側のナビゲーションで、[**検索&amp;調査**] の下にある [**電子情報開示**] をクリックします。
    
2. **[電子情報開示]** ウィンドウで、**[アドバンスト eDiscovery に移動]** をクリックします。
    
3. **[アドバンスト eDiscovery]** タブで、プラス記号のアイコンをクリックして、新しいケースを追加します。
    
4. **[ケースの追加]** ウィンドウで、**[名前]** に「**Tailspin contract dispute**」と入力して **[OK]** をクリックします。ケースが作成されるまで待機します。
    
5. リスト内の **[Tailspin contract dispute]** ケースをダブルクリックします。 
    
6. [**コンテナー** ] ボックスの一覧で、[ **Tailspin contract] 検索**コンテナーをクリックし、[**プロセス**] をクリックします。 処理が完了するまで待機します。
    
7. ウィンドウの下側に **[処理: 完了]** が表示されたら、左側のナビゲーションで **[プロセスの概要]** をクリックして概要を確認します。
    
8. 上部のナビゲーションで、**[分析]** をクリックします。
    
9. **[セットアップ]** ページで、**[テーマ]** の **[最大テーマ数]** に「**3**」と入力します。
    
10. **[分析]** をクリックして、分析が完了するまで待機します。 対象になる母集団、文書、電子メール、および添付ファイルの分析による一連の円グラフが表示されます。 詳細については、「 [Analyze 結果の表示](https://support.office.com/article/Viewing-Analyze-results-5974f3c2-89fe-4c5f-ac7b-57f214437f7e)」を参照してください。
    
この環境を使用して、新しいコンテンツ、新しい検索およびケースを作成できるようになりました。また、Office 365 のアドバンスト eDiscovery の実験をさらに進めることができるようになりました。
  
## <a name="see-also"></a>関連項目

[クラウド導入のテスト ラボ ガイド (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基本構成開発/テスト環境](base-configuration-dev-test-environment.md)
  
[Office 365 開発/テスト環境](office-365-dev-test-environment.md)
  
[Office 365 開発/テスト環境の DirSync](dirsync-for-your-office-365-dev-test-environment.md)
  
[クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.md)

[Office 365 Advanced eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)


