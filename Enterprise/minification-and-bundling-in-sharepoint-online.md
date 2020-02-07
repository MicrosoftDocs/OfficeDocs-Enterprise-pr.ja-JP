---
title: SharePoint Online での縮小とバンドル
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 3/1/2017
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 87a52468-994e-43a2-b155-7229ed659291
description: この記事では、Web Essentials での縮小とバンドルの手法を使用して、HTTP 要求の数を減らし、SharePoint Online でページを読み込むのにかかる時間を短縮する方法について説明します。
ms.openlocfilehash: ca0ad53f2c854226b729a94e345a553850517eaf
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844898"
---
# <a name="minification-and-bundling-in-sharepoint-online"></a>SharePoint Online での縮小とバンドル

この記事では、Web Essentials での縮小とバンドルの手法を使用して、HTTP 要求の数を減らし、SharePoint Online でページを読み込むのにかかる時間を短縮する方法について説明します。
  
Web サイトをカスタマイズする場合は、カスタマイズをサポートするために、多数の追加ファイルをサーバーに追加する必要があります。 JavaScript、CSS、画像を追加すると、サーバーに対する HTTP 要求の数が増加し、web ページの表示にかかる時間が長くなります。 同じ種類のファイルが複数ある場合は、これらのファイルをバンドルして、これらのファイルをすばやくダウンロードすることができます。
  
JavaScript ファイルと CSS ファイルでは、必要のないスペースやその他の文字を削除することで、ファイルの合計サイズを小さくするために、縮小というアプローチを使用することもできます。
  
## <a name="minification-and-bundling-javascript-and-css-files-with-web-essentials"></a>Web Essentials を使用した JavaScript および CSS ファイルの縮小とバンドル

Web Essentials などのサードパーティ製ソフトウェアを使用して、CSS ファイルと JavaScript ファイルをバンドルできます。
  
> [!IMPORTANT]
> Web エッセンシャルは、サードパーティのオープンソースのコミュニティベースのプロジェクトです。 このソフトウェアは、Visual Studio 2012 と Visual Studio 2013 の拡張機能であり、Microsoft ではサポートされていません。 Web Essentials をダウンロードするには、の[https://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629)web サイトにアクセスしてください。 
  
Web Essentials には、次の2つのバンドル形式が用意されています。
  
- . バンドル: CSS および JavaScript ファイル用
    
- sprite: 画像の場合 (Visual Studio 2013 でのみ使用可能)
    
既存のフィーチャーに、次のようなカスタムマスターページの内部で参照されている一部のブランド要素がある場合は、Web Essentials を使用できます。
  
![ユーザー設定のマスター ページ内のブランド要素のスクリーンショット](media/3a6eba36-973d-482b-8556-a9394b8ba19f.png)
  
 **Web Essentials で TE000127218 および CSS バンドルを作成するには**
  
1. Visual Studio の [ソリューションエクスプローラー] で、バンドルに含めるファイルを選択します。
    
2. 選択したファイルを右クリックし、コンテキストメニューから [ **Web Essentials** \> **作成 JavaScript バンドルファイル**] を選択します。 次に例を示します。 
    
    ![Web Essentials のメニュー オプションが表示されているスクリーンショット](media/41aac84c-4538-4f78-b454-46e651f868a3.png)
  
## <a name="viewing-the-results-of-bundling-javascript-and-css-files"></a>JavaScript ファイルと CSS ファイルをバンドルした結果の表示

JavaScript と CSS のバンドルを作成する場合、Web Essentials は、JavaScript ファイルと CSS ファイル、およびその他の構成情報を識別するレシピファイルと呼ばれる XML ファイルを作成します。 
  
![JavaScript と CSS レシピ ファイルのスクリーンショット](media/7ba891f8-52d8-467b-a0f6-b062dd1137a4.png)
  
また、[バンドル] で [縮小フラグ] が true に設定されている場合は、ファイルがバンドルされるだけでなく、サイズが小さくなります。 これは、マスターページで参照できる、新しい縮小版の JavaScript ファイルが作成されたことを意味します。
  
![true に設定された minify フラグのスクリーンショット](media/50523af2-6412-4117-ac3d-5bd26f6d562e.png)
  
Web サイトからページを読み込む場合、Internet Explorer 11 などの web ブラウザーの開発者ツールを使用して、サーバーに送信された要求の数と、各ファイルの読み込みにかかった時間を確認できます。
  
次の図は、縮小前に JavaScript および CSS ファイルを読み込んだ結果です。
  
![ダウンロードされている 80 のアイテムが表示されているスクリーンショット](media/e2df3912-1923-46e6-8cf2-3015a31554e1.png)
  
CSS ファイルと JavaScript ファイルを一緒にバンドルした後、要求数が74に落ち、各ファイルは、元のファイルを個別にダウンロードするよりわずかに時間がかかりすぎたことになります。
  
![ダウンロードされている 74 のアイテムが表示されているスクリーンショット](media/686c4387-70e8-4a74-9d45-059f33a91184.png)
  
バンドル後、JavaScript バンドルファイルは815KB から365KB に大幅に減少します。
  
![削減されたダウンロード サイズを示すスクリーンショット](media/5e7dbd98-faff-4f68-b320-108fb252e395.png)
  
## <a name="bundling-images-by-creating-an-image-sprite"></a>イメージスプライトを作成してイメージをバンドルする

JavaScript ファイルと CSS ファイルをバンドルする方法と同様に、多くの小さいアイコンやその他の一般的な画像を大きなスプライトシートに結合し、CSS を使用して個々の画像を表示することができます。 個々の画像をダウンロードするのではなく、ユーザーの web ブラウザーはスプライトシートを一度ダウンロードしてからローカルコンピューターにキャッシュします。 これにより、web サーバーへのダウンロード回数とラウンドトリップを減らすことで、ページの読み込みのパフォーマンスが向上します。
  
 **Web Essentials でイメージスプライトを作成するには**
  
1. Visual Studio の [ソリューションエクスプローラー] で、バンドルに含めるファイルを選択します。
    
2. 選択したファイルを右クリックし、コンテキストメニューから [ **Web Essentials** \> **Create image sprite** ] を選択します。 次に例を示します。 
    
    ![画像のスプライトを作成する方法を示したスクリーンショット](media/de0fe741-4ef7-4e3b-bafa-ef9f4822dac6.png)
  
3. スプライトファイルを保存する場所を選択します。 Sprite ファイルは、スプライト内の設定とファイルを記述する XML ファイルです。 次の図は、sprite PNG ファイルとそれに対応する sprite XML ファイルの例を示しています。
    
    ![スプライト ファイルのスクリーンショット](media/0876bb2a-d1b9-4169-8e95-9c290d628d90.png)
  
    ![スプライト XML ファイルのスクリーンショット](media/d1f94776-280d-4d56-abb5-384f145d9989.png)
  

