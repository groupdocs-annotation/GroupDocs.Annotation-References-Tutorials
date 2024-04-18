---
title: 楕円注釈をドキュメントに追加
linktitle: 楕円注釈をドキュメントに追加
second_title: GroupDocs.Annotation .NET API
description: GroupDocs.Annotation を使用して .NET のドキュメントに楕円注釈を追加する方法を学びます。コラボレーションとコミュニケーションを簡単に強化します。
type: docs
weight: 13
url: /ja/net/unlocking-annotation-power/add-ellipse-annotation/
---
## 導入
このチュートリアルでは、GroupDocs.Annotation for .NET を使用してドキュメントに楕円注釈を追加する方法を学習します。このステップバイステップのガイドではプロセスを順を追って説明し、各ステップを明確に理解できるようにします。
## 前提条件
始める前に、以下のものがあることを確認してください。
1.  GroupDocs.Annotation for .NET: GroupDocs.Annotation for .NET をダウンロードしてインストールしていることを確認してください。からダウンロードできます[ここ](https://releases.groupdocs.com/annotation/net/).
2. IDE (統合開発環境): コードを作成して実行するには、Visual Studio などの IDE がシステムにインストールされている必要があります。

## 名前空間のインポート
まず、必要な名前空間をプロジェクトにインポートします。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## ステップ 1: 出力パスを設定する
注釈付きドキュメントが保存される出力パスを定義します。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## ステップ 2: アノテーターを初期化する
入力ドキュメントのパスを指定してアノテーターを初期化します。
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## ステップ 3: 楕円注釈を作成する
のインスタンスを作成します。`EllipseAnnotation`クラスを作成し、そのプロパティを設定します。
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
## ステップ 4: 注釈を追加する
楕円の注釈をドキュメントに追加します。
```csharp
annotator.Add(ellipse);
```
## ステップ 5: ドキュメントを保存する
注釈付きドキュメントを出力パスに保存します。
```csharp
annotator.Save(outputPath);
```

## 結論
おめでとう！ GroupDocs.Annotation for .NET を使用して、ドキュメントに楕円注釈を正常に追加しました。この機能を .NET アプリケーションに統合して、ドキュメントのコラボレーションとコミュニケーションを強化できるようになりました。
## よくある質問
### 楕円注釈の外観をカスタマイズできますか?
はい、要件に応じて、背景色、境界線の色、不透明度などのさまざまなプロパティをカスタマイズできます。
### GroupDocs.Annotation for .NET はすべてのドキュメント形式と互換性がありますか?
GroupDocs.Annotation for .NET は、PDF、DOCX、PPTX、XLSX などの幅広いドキュメント形式をサポートしています。
### 1 つのドキュメントに複数の注釈を追加できますか?
はい、楕円、長方形、テキストなどを含む複数の注釈を 1 つのドキュメントに追加できます。
### テスト目的で利用できる試用版はありますか?
はい、無料試用版を次からダウンロードできます。[ここ](https://releases.groupdocs.com/)その機能を評価します。
### GroupDocs.Annotation for .NET のテクニカル サポートはどこで受けられますか?
 GroupDocs.Annotation コミュニティ フォーラムから技術サポートを受けることができます。[ここ](https://forum.groupdocs.com/c/annotation/10).