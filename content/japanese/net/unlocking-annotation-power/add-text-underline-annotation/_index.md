---
title: テキストの下線注釈をドキュメントに追加する
linktitle: テキストの下線注釈をドキュメントに追加する
second_title: GroupDocs.Annotation .NET API
description: GroupDocs.Annotation for .NET を使用してドキュメントにテキストの下線注釈を追加する方法を学習します。コラボレーションとコミュニケーションを簡単に強化します。
weight: 27
url: /ja/net/unlocking-annotation-power/add-text-underline-annotation/
---

# テキストの下線注釈をドキュメントに追加する

## 導入
このチュートリアルでは、GroupDocs.Annotation for .NET を使用してドキュメントにテキストの下線注釈を追加するプロセスを説明します。テキストの下線注釈は、重要な箇所や重要なポイントなど、文書の特定の部分を強調するのに役立ちます。
## 前提条件
始める前に、次の前提条件がインストールされていることを確認してください。
1.  GroupDocs.Annotation for .NET: GroupDocs.Annotation for .NET をダウンロードしてインストールします。[ここ](https://releases.groupdocs.com/annotation/net/).
2. .NET Framework: システムに .NET Framework がインストールされていることを確認してください。

## 名前空間のインポート
まず、必要な名前空間をプロジェクトにインポートしましょう。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

ここで、例を複数のステップに分けてみましょう。
## ステップ 1: 出力パスを定義する
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
このステップでは、注釈付きドキュメントが保存される出力パスを定義します。
## ステップ 2: アノテーターを初期化する
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
ここでは、のインスタンスを初期化します。`Annotator`入力ドキュメントのパスを指定してクラスを作成します。
## ステップ 3: 下線注釈を作成する
```csharp
UnderlineAnnotation underline = new UnderlineAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is underline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    UnderlineColor = 1422623, //Word および PDF ドキュメントのみサポートされている作品
    Points = new List<Point>
    {
        new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
    },
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
このステップには、`UnderlineAnnotation`フォントの色、メッセージ、不透明度、ページ番号、背景色、下線の色、ポイント、返信などのさまざまなプロパティを持つオブジェクト。
## ステップ 4: ドキュメントに注釈を追加する
```csharp
annotator.Add(underline);
```
ここでは、文書に下線の注釈を追加します。
## ステップ 5: 注釈付きドキュメントを保存する
```csharp
annotator.Save(outputPath);
```
最後に、注釈付きドキュメントを指定された出力パスに保存します。

## 結論
このチュートリアルでは、GroupDocs.Annotation for .NET を使用してドキュメントにテキストの下線注釈を追加する方法を学びました。この強力なライブラリは、ドキュメントのコラボレーションとコミュニケーションを強化するためのさまざまな注釈オプションを提供します。
## よくある質問
### 下線注釈の外観をカスタマイズできますか?
はい、要件に応じて色、不透明度、位置などのプロパティをカスタマイズできます。
### GroupDocs.Annotation はさまざまなドキュメント形式と互換性がありますか?
はい、GroupDocs.Annotation は Word や PDF を含む幅広いドキュメント形式をサポートしています。
### 1 つのドキュメントに複数の注釈を追加できますか?
確かに、GroupDocs.Annotation を使用すると、さまざまなタイプの複数の注釈をドキュメントに追加できます。
### GroupDocs.Annotation に利用できる無料トライアルはありますか?
はい、無料試用版には次からアクセスできます。[ここ](https://releases.groupdocs.com/).
### GroupDocs.Annotation のサポートはどこで入手できますか?
 GroupDocs.Annotation コミュニティ フォーラムからサポートを受けることができます。[ここ](https://forum.groupdocs.com/c/annotation/10).