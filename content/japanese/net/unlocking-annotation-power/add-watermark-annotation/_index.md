---
title: 文書に透かし注釈を追加する
linktitle: 文書に透かし注釈を追加する
second_title: GroupDocs.Annotation .NET API
description: GroupDocs.Annotation for .NET を使用して、ドキュメントに透かし注釈を簡単に追加する方法を学びます。文書の明瞭さとセキュリティを強化します。
type: docs
weight: 28
url: /ja/net/unlocking-annotation-power/add-watermark-annotation/
---
## 導入
このチュートリアルでは、GroupDocs.Annotation for .NET を使用してドキュメントにウォーターマーク注釈を追加するプロセスを説明します。透かし注釈は、文書のステータスを示したり、文書を機密としてマークしたり、その他の関連情報を追加したりするのに役立ちます。

## 前提条件

始める前に、以下のものがあることを確認してください。

1.  GroupDocs.Annotation for .NET: 次からダウンロードできます。[ここ](https://releases.groupdocs.com/annotation/net/).
2. Visual Studio: システムに Visual Studio がインストールされていることを確認します。
3. C# の基本知識: コード例を理解して実装するには、C# プログラミング言語に精通している必要があります。

## 名前空間のインポート

コーディングを開始する前に、必要な名前空間をインポートしましょう。

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

ここで、透かし注釈を追加するプロセスを複数のステップに分けてみましょう。

## ステップ 1: 出力パスを定義する

まず、注釈付きドキュメントが保存される出力パスを定義する必要があります。を使用します。`Path`からのクラス`System.IO`名前空間を使用して、出力ディレクトリのパスとファイル名を結合します。

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## ステップ 2: アノテーターを初期化する

次に、入力ドキュメントのパスを指定してアノテーターを初期化します。これにより、ドキュメントに注釈を追加できるようになります。

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    //注釈コードがここに挿入されます
}
```

## ステップ 3: 透かし注釈を作成する

次に、角度、位置、テキスト、フォントの色、不透明度などの必要なプロパティを備えた透かし注釈オブジェクトを作成しましょう。

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

## ステップ 4: 透かし注釈を追加する

次に、透かし注釈をドキュメントに追加します。`Add`アノテーター オブジェクトのメソッド。

```csharp
annotator.Add(watermark);
```

## ステップ 5: ドキュメントを保存する

最後に、注釈付きドキュメントを指定された出力パスに保存します。

```csharp
annotator.Save(outputPath);
```

## 結論

このチュートリアルでは、GroupDocs.Annotation for .NET を使用してドキュメントにウォーターマーク注釈を追加する方法を学びました。透かし注釈は、文書に関連情報をマークしたり、文書のステータスを示したりするための貴重なツールです。

## よくある質問

### Q: 透かし注釈の外観をカスタマイズできますか?

A: はい、テキスト、フォント サイズ、色、不透明度、位置などのさまざまなプロパティをカスタマイズして、要件に応じて透かしを調整できます。

### Q: GroupDocs.Annotation for .NET はさまざまなドキュメント形式と互換性がありますか?

A: はい、GroupDocs.Annotation は、PDF、Microsoft Word、Excel、PowerPoint、画像形式などの幅広いドキュメント形式をサポートしています。

### Q: 1 つのドキュメントに複数の注釈を追加できますか?

A: 確かに、GroupDocs.Annotation を使用すると、さまざまなタイプの複数の注釈を 1 つのドキュメントに追加でき、包括的なドキュメント マークアップが可能になります。

### Q: GroupDocs.Annotation は共同アノテーションをサポートしますか?

A: はい、GroupDocs.Annotation を使用すると、ユーザーがコメント、返信、注釈を追加できるようになり、チーム メンバー間の効果的なコラボレーションが促進されるため、共同での注釈付けが容易になります。

### Q: GroupDocs.Annotation for .NET の試用版はありますか?

 A: はい、以下から無料試用版をダウンロードできます。[ここ](https://releases.groupdocs.com/).