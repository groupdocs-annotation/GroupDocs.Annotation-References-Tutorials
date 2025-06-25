---
"description": "GroupDocs.Annotation for .NET を使用してドキュメントに距離注釈を追加する方法を学びましょう。コラボレーションとコミュニケーションを簡単に強化できます。"
"linktitle": "ドキュメントに距離注釈を追加する"
"second_title": "GroupDocs.Annotation .NET API"
"title": "ドキュメントに距離注釈を追加する"
"url": "/ja/net/unlocking-annotation-power/add-distance-annotation/"
"weight": 12
---

# ドキュメントに距離注釈を追加する

## 導入
このチュートリアルでは、GroupDocs.Annotation for .NET を使用してドキュメントに距離注釈を追加する方法を学習します。タスクを実行するには、以下の手順に従ってください。
## 前提条件

続行する前に、次の前提条件が満たされていることを確認してください。

- GroupDocs.Annotation for .NETライブラリ: GroupDocs.Annotation for .NETライブラリを以下のサイトからダウンロードしてインストールします。 [このリンク](https://releases。groupdocs.com/annotation/net/).
- 注釈を付けるドキュメント: 距離注釈を追加するドキュメント (PDF など) を準備します。
- 開発環境: Visual Studio または任意の他の IDE を使用して開発環境をセットアップします。

## 名前空間のインポート

始める前に、コードに必要な名前空間が含まれていることを確認してください。これらの名前空間は、必要なクラスやメソッドにアクセスするために不可欠です。

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## ステップ1: アノテーターを初期化する

まず初期化する `Annotator` 注釈を付けるドキュメントへのパスを持つオブジェクト。

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // 注釈コードはここに記入します
}
```

## ステップ2: 距離注釈を作成する

さて、 `DistanceAnnotation` オブジェクトを作成し、ボックスのサイズ、メッセージ、不透明度、ペンの色などのプロパティを構成します。

```csharp
DistanceAnnotation distance = new DistanceAnnotation
{
    Box = new Rectangle(200, 150, 200, 30),
    CreatedOn = DateTime.Now,
    Message = "This is distance annotation",
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

## ステップ3: 注釈を追加する

作成した距離注釈をドキュメントに追加するには、 `Add` アノテーター オブジェクトのメソッド。

```csharp
annotator.Add(distance);
```

## ステップ4: ドキュメントを保存する

注釈を付けたドキュメントをシステム上の目的の場所に保存します。

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```

## ステップ5: 確認を表示する

最後に、注釈付きドキュメントが正常に保存されたことを確認するメッセージを表示します。

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論

GroupDocs.Annotation for .NET を使ってドキュメントに距離注釈を追加するのは簡単です。このチュートリアルで説明する手順に従うことで、価値ある注釈でドキュメントを強化し、コラボレーションとコミュニケーションを促進できます。

## よくある質問

### Q: 距離注釈の外観をカスタマイズできますか?

A: はい、色、不透明度、線のスタイルなど、さまざまなプロパティを要件に合わせてカスタマイズできます。

### Q: GroupDocs.Annotation はさまざまな種類のドキュメントの注釈をサポートしていますか?

A: はい、GroupDocs.Annotation は、PDF、Word、Excel、PowerPoint など、さまざまなドキュメント形式の注釈をサポートしています。

### Q: GroupDocs.Annotation の無料トライアルはありますか?

A: はい、GroupDocs.Annotationの無料トライアルは以下からご利用いただけます。 [このリンク](https://releases。groupdocs.com/).

### Q: GroupDocs.Annotation for .NET のドキュメントはどこにありますか?

A: 詳細なドキュメントを参照してください。 [ここ](https://tutorials。groupdocs.com/annotation/net/).

### Q: GroupDocs.Annotation に関するサポートや支援を受けるにはどうすればよいですか?

A: GroupDocs.Annotationコミュニティフォーラムでサポートや支援を求めることができます。 [ここ](https://forum。groupdocs.com/c/annotation/10).