---
"description": "GroupDocs.Annotation for .NET を使用してドキュメントに画像注釈を追加する方法を学びます。強力な注釈機能でドキュメント管理を強化します。"
"linktitle": "ドキュメントに画像注釈を追加する（リモートパス）"
"second_title": "GroupDocs.Annotation .NET API"
"title": "ドキュメントに画像注釈を追加する（リモートパス）"
"url": "/ja/net/unlocking-annotation-power/add-image-annotation-remote-path/"
"weight": 15
---

# ドキュメントに画像注釈を追加する（リモートパス）

## 導入
このチュートリアルでは、GroupDocs.Annotation for .NET を使用してドキュメントに画像注釈を追加する手順を説明します。このライブラリは、さまざまな種類のドキュメントにプログラムで注釈を付けるための強力なツールを提供します。
## 前提条件
始める前に、以下のものを用意してください。
1. GroupDocs.Annotation for .NET: ライブラリをダウンロードしてインストールします。 [ここ](https://releases。groupdocs.com/annotation/net/).
2. 開発環境: .NET 開発用に動作する開発環境が設定されていることを確認します。
3. 文書: 注釈を付けたい文書を用意します。このチュートリアルでは、次のようなPDF文書があると仮定します。 `input。pdf`.
4. 注釈用画像：注釈に使用する画像を選択します。画像のURLまたはローカルパスを用意してください。

## 名前空間のインポート
コーディングを始める前に、必要な名前空間をインポートしましょう。
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## ステップ1: 出力パスを設定する
まず、注釈付きドキュメントを保存する出力パスを定義します。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## ステップ2: アノテーターを初期化する
インスタンスを作成する `Annotator` クラスを作成し、入力ドキュメントを指定します。
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // 注釈コードはここに記入します
}
```
## ステップ3: 画像注釈を追加する
それでは、ドキュメントに画像注釈を追加してみましょう。画像注釈の位置、不透明度、ページ番号、画像パスなどのプロパティを指定します。
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100), // 注釈の位置を指定する
    CreatedOn = DateTime.Now, // 作成日を設定する
    Opacity = 0.7, // 不透明度を設定する（0～1）
    PageNumber = 0, // ページ番号を指定する
    ImagePath = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" // 画像のURLを入力してください
};
annotator.Add(image); // 画像注釈を追加する
```
## ステップ4: ドキュメントを保存する
注釈付きドキュメントを指定された出力パスに保存します。
```csharp
annotator.Save(outputPath);
```
## ステップ5: 出力パスを表示する
ドキュメントの保存操作が成功したことをユーザーに通知し、出力パスを表示します。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
このチュートリアルでは、GroupDocs.Annotation for .NET を使用してドキュメントに画像注釈を追加する方法を学習しました。これらの手順に従うことで、強力な注釈機能を活用してドキュメント管理アプリケーションを強化できます。
## よくある質問
### GroupDocs.Annotation は PDF 以外のドキュメント形式でも使用できますか?
はい、GroupDocs.Annotation は、Word、Excel、PowerPoint など、さまざまなドキュメント形式をサポートしています。
### GroupDocs.Annotation は .NET Core と互換性がありますか?
はい、GroupDocs.Annotation は .NET Framework と .NET Core の両方と互換性があります。
### 注釈の外観をカスタマイズできますか?
はい、色、不透明度、サイズなど、注釈の外観をカスタマイズできます。
### GroupDocs.Annotation は共同注釈機能をサポートしていますか?
はい、GroupDocs.Annotation は、ドキュメントのリアルタイム共同作業を可能にする共同注釈機能を提供します。
### テスト用に試用版はありますか?
はい、GroupDocs.Annotationの無料トライアルは以下から入手できます。 [ここ](https://releases。groupdocs.com/).