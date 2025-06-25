---
"description": "GroupDocs.Annotation を使用して、.NET ドキュメントに楕円注釈を追加する方法を学びます。コラボレーションとコミュニケーションを簡単に強化できます。"
"linktitle": "ドキュメントに楕円注釈を追加する"
"second_title": "GroupDocs.Annotation .NET API"
"title": "ドキュメントに楕円注釈を追加する"
"url": "/ja/net/unlocking-annotation-power/add-ellipse-annotation/"
"weight": 13
---

# ドキュメントに楕円注釈を追加する

## 導入
このチュートリアルでは、GroupDocs.Annotation for .NET を使用してドキュメントに楕円注釈を追加する方法を学習します。このステップバイステップガイドでは、各ステップを明確に理解できるように、プロセスを順を追って説明します。
## 前提条件
始める前に、次のものがあることを確認してください。
1. GroupDocs.Annotation for .NET: GroupDocs.Annotation for .NETをダウンロードしてインストールしてください。ダウンロードはこちらから行えます。 [ここ](https://releases。groupdocs.com/annotation/net/).
2. IDE (統合開発環境): コードを記述して実行するには、Visual Studio などの IDE がシステムにインストールされている必要があります。

## 名前空間のインポート
まず、プロジェクトに必要な名前空間をインポートします。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## ステップ1: 出力パスを設定する
注釈付きドキュメントを保存する出力パスを定義します。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## ステップ2: アノテーターを初期化する
入力ドキュメントのパスを指定してアノテーターを初期化します。
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## ステップ3: 楕円注釈を作成する
インスタンスを作成する `EllipseAnnotation` クラスを作成し、そのプロパティを設定します。
```csharp
EllipseAnnotation ellipse = new EllipseAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is ellipse annotation",
    Opacity = 0.7,
    PageNumber = 0,
    PenColor = 65535,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
    Replies = new List<Reply>
    {
        new Reply
        {
            Comment = "First comment",
            RepliedOn = DateTime.Now
        },
        new Reply
        {
            Comment = "Second comment",
            RepliedOn = DateTime.Now
        }
    }
};
```
## ステップ4: 注釈を追加する
ドキュメントに楕円注釈を追加します。
```csharp
annotator.Add(ellipse);
```
## ステップ5: ドキュメントを保存する
注釈付きドキュメントを出力パスに保存します。
```csharp
annotator.Save(outputPath);
```

## 結論
おめでとうございます！GroupDocs.Annotation for .NET を使用して、ドキュメントに楕円注釈を追加することができました。この機能を .NET アプリケーションに統合することで、ドキュメントの共同作業とコミュニケーションを強化できます。
## よくある質問
### 楕円注釈の外観をカスタマイズできますか?
はい、背景色、境界線の色、不透明度など、さまざまなプロパティを要件に応じてカスタマイズできます。
### GroupDocs.Annotation for .NET はすべてのドキュメント形式と互換性がありますか?
GroupDocs.Annotation for .NET は、PDF、DOCX、PPTX、XLSX など、幅広いドキュメント形式をサポートしています。
### 1 つのドキュメントに複数の注釈を追加できますか?
はい、楕円、四角形、テキストなど、複数の注釈を 1 つのドキュメントに追加できます。
### テスト用に試用版はありますか?
はい、無料試用版をダウンロードできます。 [ここ](https://releases.groupdocs.com/) その機能を評価します。
### GroupDocs.Annotation for .NET のテクニカル サポートはどこで受けられますか?
GroupDocs.Annotationコミュニティフォーラムから技術サポートを受けることができます。 [ここ](https://forum。groupdocs.com/c/annotation/10).