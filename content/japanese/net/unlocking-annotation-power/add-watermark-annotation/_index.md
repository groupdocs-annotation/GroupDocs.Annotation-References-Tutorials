---
"description": "GroupDocs.Annotation for .NET を使って、ドキュメントに透かし注釈を簡単に追加する方法を学びましょう。ドキュメントの明瞭性とセキュリティを強化します。"
"linktitle": "ドキュメントに透かし注釈を追加する"
"second_title": "GroupDocs.Annotation .NET API"
"title": "ドキュメントに透かし注釈を追加する"
"url": "/ja/net/unlocking-annotation-power/add-watermark-annotation/"
type: docs
"weight": 28
---

# ドキュメントに透かし注釈を追加する

## 導入
このチュートリアルでは、GroupDocs.Annotation for .NET を使用してドキュメントに透かし注釈を追加する手順を説明します。透かし注釈は、ドキュメントのステータスを示したり、機密としてマークしたり、その他の関連情報を追加したりするのに役立ちます。

## 前提条件

始める前に、以下のものを用意してください。

1. GroupDocs.Annotation for .NET: ダウンロードはこちらから [ここ](https://releases。groupdocs.com/annotation/net/).
2. Visual Studio: システムに Visual Studio がインストールされていることを確認します。
3. C# の基礎知識: コード例を理解して実装するには、C# プログラミング言語の知識が必要です。

## 名前空間のインポート

コーディングを始める前に、必要な名前空間をインポートしましょう。

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

ここで、透かし注釈を追加するプロセスを複数のステップに分解してみましょう。

## ステップ1: 出力パスを定義する

まず、注釈付き文書を保存する出力パスを定義する必要があります。 `Path` クラスから `System.IO` 出力ディレクトリ パスとファイル名を結合するための名前空間。

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## ステップ2: アノテーターを初期化する

次に、入力ドキュメントのパスを指定してアノテーターを初期化します。これにより、ドキュメントにアノテーションを追加できるようになります。

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // 注釈コードはここに記入します
}
```

## ステップ3：透かし注釈を作成する

ここで、角度、位置、テキスト、フォント色、不透明度などの必要なプロパティを持つ透かし注釈オブジェクトを作成しましょう。

```csharp
WatermarkAnnotation watermark = new WatermarkAnnotation
{
    Angle = 75,
    Box = new Rectangle(200, 200, 100, 50),
    CreatedOn = DateTime.Now,
    Text = "Watermark",
    FontColor = 65535,
    FontSize = 12,
    Message = "This is watermark annotation",
    Opacity = 0.7,
    PageNumber = 0,
    AutoScale = true,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
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

## ステップ4：透かし注釈を追加する

次に、透かし注釈をドキュメントに追加します。 `Add` アノテーター オブジェクトのメソッド。

```csharp
annotator.Add(watermark);
```

## ステップ5: ドキュメントを保存する

最後に、注釈付きのドキュメントを指定された出力パスに保存します。

```csharp
annotator.Save(outputPath);
```

## 結論

このチュートリアルでは、GroupDocs.Annotation for .NET を使用してドキュメントに透かし注釈を追加する方法を学習しました。透かし注釈は、ドキュメントに関連情報をマークしたり、ドキュメントのステータスを示すのに役立つ便利なツールです。

## よくある質問

### Q: 透かし注釈の外観をカスタマイズできますか?

A: はい、テキスト、フォント サイズ、色、不透明度、位置などのさまざまなプロパティをカスタマイズして、要件に応じて透かしをカスタマイズできます。

### Q: GroupDocs.Annotation for .NET はさまざまなドキュメント形式と互換性がありますか?

A: はい、GroupDocs.Annotation は、PDF、Microsoft Word、Excel、PowerPoint、画像形式など、幅広いドキュメント形式をサポートしています。

### Q: 1 つのドキュメントに複数の注釈を追加できますか?

A: もちろんです。GroupDocs.Annotation を使用すると、1 つのドキュメントに異なるタイプの複数の注釈を追加して、包括的なドキュメント マークアップを実現できます。

### Q: GroupDocs.Annotation は共同注釈付けをサポートしていますか?

A: はい、GroupDocs.Annotation は、ユーザーがコメント、返信、注釈を追加できるようにすることで共同注釈を容易にし、チーム メンバー間の効果的なコラボレーションを促進します。

### Q: GroupDocs.Annotation for .NET の試用版はありますか?

A: はい、無料試用版は以下からダウンロードできます。 [ここ](https://releases。groupdocs.com/).