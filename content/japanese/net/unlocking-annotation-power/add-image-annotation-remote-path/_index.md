---
title: 画像注釈をドキュメントに追加 (リモート パス)
linktitle: 画像注釈をドキュメントに追加 (リモート パス)
second_title: GroupDocs.Annotation .NET API
description: GroupDocs.Annotation for .NET を使用してドキュメントに画像注釈を追加する方法を学びます。強力な注釈機能でドキュメント管理を強化します。
type: docs
weight: 15
url: /ja/net/unlocking-annotation-power/add-image-annotation-remote-path/
---
## 導入
このチュートリアルでは、GroupDocs.Annotation for .NET を使用してドキュメントに画像注釈を追加するプロセスを説明します。このライブラリは、さまざまな種類のドキュメントにプログラムで注釈を付けるための強力なツールを提供します。
## 前提条件
始める前に、以下のものがあることを確認してください。
1.  GroupDocs.Annotation for .NET: からライブラリをダウンロードしてインストールします。[ここ](https://releases.groupdocs.com/annotation/net/).
2. 開発環境: .NET 開発用に動作する開発環境がセットアップされていることを確認します。
3. ドキュメント: 注釈を付けたいドキュメントを準備します。このチュートリアルでは、次の名前の PDF ドキュメントがあると仮定します。`input.pdf`.
4. 注釈用の画像: 注釈に使用する画像を選択します。画像の URL またはローカル パスを準備していることを確認してください。

## 名前空間のインポート
コーディングを開始する前に、必要な名前空間をインポートしましょう。
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## ステップ 1: 出力パスを設定する
まず、注釈付きドキュメントが保存される出力パスを定義します。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## ステップ 2: アノテーターを初期化する
のインスタンスを作成します。`Annotator`クラスを指定し、入力ドキュメントを指定します。
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    //注釈コードがここに挿入されます
}
```
## ステップ 3: 画像の注釈を追加する
次に、画像注釈をドキュメントに追加しましょう。位置、不透明度、ページ番号、画像パスなどの画像注釈のプロパティを指定します。
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100), //注釈の位置を指定する
    CreatedOn = DateTime.Now, //作成日を設定する
    Opacity = 0.7, //不透明度を設定します (0 ～ 1)
    PageNumber = 0, //ページ番号を指定してください
    ImagePath = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" // 画像の URL を指定します
};
annotator.Add(image); //画像の注釈を追加する
```
## ステップ 4: ドキュメントを保存する
注釈付きドキュメントを指定された出力パスに保存します。
```csharp
annotator.Save(outputPath);
```
## ステップ 5: 出力パスを表示する
ドキュメントの保存操作が成功したことをユーザーに通知し、出力パスを表示します。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
このチュートリアルでは、GroupDocs.Annotation for .NET を使用してドキュメントに画像注釈を追加する方法を学習しました。これらの手順に従うことで、強力な注釈機能を使用して文書管理アプリケーションを強化できます。
## よくある質問
### GroupDocs.Annotation は PDF 以外のドキュメント形式でも使用できますか?
はい。GroupDocs.Annotation は、Word、Excel、PowerPoint などを含むさまざまなドキュメント形式をサポートしています。
### GroupDocs.Annotation は .NET Core と互換性がありますか?
はい、GroupDocs.Annotation は .NET Framework と .NET Core の両方と互換性があります。
### 注釈の外観をカスタマイズできますか?
はい、色、不透明度、サイズなどの注釈の外観をカスタマイズできます。
### GroupDocs.Annotation は共同注釈機能をサポートしていますか?
はい、GroupDocs.Annotation は、ドキュメント上でリアルタイムに共同作業を行うための共同注釈機能を提供します。
### テスト用に利用できる試用版はありますか?
はい、GroupDocs.Annotation の無料トライアルを次のサイトから入手できます。[ここ](https://releases.groupdocs.com/).