---
"description": "効率的なドキュメント管理と共同作業のために、GroupDocs.Annotation を使用して .NET でテキストに画像注釈を追加する方法を学習します。"
"linktitle": "テキストの上に画像注釈を付ける"
"second_title": "GroupDocs.Annotation .NET API"
"title": "テキストの上に画像注釈を付ける"
"url": "/ja/net/advanced-usage/put-image-annotation-over-text/"
"weight": 21
---

# テキストの上に画像注釈を付ける

## 導入
.NET開発の世界では、GroupDocs.Annotationはドキュメントに注釈を追加するための強力なソリューションを提供し、共同作業とドキュメント管理の効率化を実現します。よくある要件の一つとして、テキストの上に画像注釈を追加することが挙げられますが、GroupDocs.Annotation for .NETを使用すれば、シームレスに実現できます。
## 前提条件
GroupDocs.Annotation for .NET を使用してテキストの上に画像注釈を追加するプロセスに進む前に、次のものを用意してください。
1. GroupDocs.Annotation for .NETライブラリ: ライブラリをダウンロードしてインストールします。 [ここ](https://releases。groupdocs.com/annotation/net/).
2. 開発環境: Visual Studio やその他の .NET IDE などの適切な開発環境をセットアップします。
3. ドキュメントおよび画像ファイル: 注釈に使用するドキュメント ファイル (PDF、DOCX など) と画像ファイルを準備します。
4. C# の基本的な理解: このチュートリアルで提供されるコード スニペットを実装するには、C# プログラミング言語の知識が必要です。

## 名前空間のインポート
注釈付けのプロセスを進める前に、C# プロジェクトに必要な名前空間をインポートしていることを確認してください。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## ステップ1: 出力パスを定義する
まず、注釈付きドキュメントを保存する出力パスを定義します。
```csharp
string outputPath = Path.Combine("Your Document Directory", "annotated_document.pdf");
```
## ステップ2: アノテーターを初期化する
初期化する `Annotator` 入力ドキュメントのパスを指定してオブジェクトを作成します。
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // 注釈コードはここに記入します
}
```
## ステップ3: 画像注釈を作成する
作成する `ImageAnnotation` ボックスのサイズ、不透明度、ページ番号、画像パス、Z インデックスなどの必要なプロパティを持つオブジェクト:
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png",
    ZIndex = 3
};
```
## ステップ4: 注釈を追加する
ドキュメントに画像注釈を追加するには、 `Add` の方法 `Annotator` 物体：
```csharp
annotator.Add(image);
```
## ステップ5: 注釈付きドキュメントを保存する
注釈付きドキュメントを指定された出力パスに保存します。
```csharp
annotator.Save(outputPath);
```
## ステップ6: 成功メッセージを表示する
注釈が付けられたドキュメントへのパスを含む成功メッセージを表示します。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
結論として、GroupDocs.Annotation を使用して .NET アプリケーションでテキストに画像注釈を追加するのは簡単です。このチュートリアルのステップバイステップガイドに従うことで、ドキュメントに効率的に注釈を付け、.NET プロジェクトにおけるコラボレーションとドキュメント管理機能を強化できます。
## よくある質問
### PDF 以外のドキュメントに注釈を付けることはできますか?
はい、GroupDocs.Annotation は DOCX、XLSX、PPTX など、さまざまなドキュメント形式をサポートしています。
### GroupDocs.Annotation の無料トライアルはありますか?
はい、無料試用版をダウンロードできます。 [ここ](https://releases。groupdocs.com/).
### GroupDocs.Annotation のサポートを受けるにはどうすればよいですか?
GroupDocs.Annotationコミュニティフォーラムからサポートを受けることができます [ここ](https://forum。groupdocs.com/c/annotation/10).
### テスト目的で一時ライセンスは必要ですか?
はい、臨時免許証は以下から取得できます。 [ここ](https://purchase.groupdocs.com/temporary-license/) テスト目的のため。
### 注釈の外観をカスタマイズできますか?
はい、GroupDocs.Annotation には、色、不透明度、フォント サイズなど、注釈の外観をカスタマイズするためのさまざまなオプションが用意されています。