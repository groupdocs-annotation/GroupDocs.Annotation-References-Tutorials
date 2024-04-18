---
title: 距離の注釈をドキュメントに追加
linktitle: 距離の注釈をドキュメントに追加
second_title: GroupDocs.Annotation .NET API
description: GroupDocs.Annotation for .NET を使用してドキュメントに距離の注釈を追加する方法を学びます。コラボレーションとコミュニケーションを簡単に強化します。
type: docs
weight: 12
url: /ja/net/unlocking-annotation-power/add-distance-annotation/
---
## 導入
このチュートリアルでは、GroupDocs.Annotation for .NET を使用してドキュメントに距離の注釈を追加する方法を学習します。タスクを完了するには、次の手順に従います。
## 前提条件

続行する前に、次の前提条件が満たされていることを確認してください。

-  GroupDocs.Annotation for .NET ライブラリ: GroupDocs.Annotation for .NET ライブラリを次からダウンロードしてインストールします。[このリンク](https://releases.groupdocs.com/annotation/net/).
- 注釈を付けるドキュメント: 距離の注釈を追加するドキュメント (PDF など) を準備します。
- 開発環境: Visual Studio またはその他の任意の IDE を使用して開発環境をセットアップします。

## 名前空間のインポート

始める前に、コードに必要な名前空間を必ず含めてください。これらの名前空間は、必要なクラスやメソッドにアクセスするために不可欠です。

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## ステップ 1: アノテーターを初期化する

初期化から始めます`Annotator`オブジェクトに注釈を付けたいドキュメントへのパスを指定します。

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    //注釈コードがここに挿入されます
}
```

## ステップ 2: 距離の注釈を作成する

ここで、`DistanceAnnotation`オブジェクトを作成し、ボックスの寸法、メッセージ、不透明度、ペンの色などのプロパティを設定します。

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

## ステップ 3: 注釈を追加する

作成した距離の注釈をドキュメントに追加します。`Add`アノテーター オブジェクトのメソッド。

```csharp
annotator.Add(distance);
```

## ステップ 4: ドキュメントを保存する

注釈付きドキュメントをシステム上の目的の場所に保存します。

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

GroupDocs.Annotation for .NET を使用してドキュメントに距離の注釈を追加するのは簡単なプロセスです。このチュートリアルで概説されている手順に従うことで、貴重な注釈を追加してドキュメントを強化し、コラボレーションとコミュニケーションを促進することができます。

## よくある質問

### Q: 距離の注釈の外観をカスタマイズできますか?

A: はい、要件に合わせて色、不透明度、線のスタイルなどのさまざまなプロパティをカスタマイズできます。

### Q: GroupDocs.Annotation はさまざまな種類のドキュメントの注釈をサポートしていますか?

A: はい、GroupDocs.Annotation は、PDF、Word、Excel、PowerPoint などを含む幅広いドキュメント形式の注釈をサポートしています。

### Q: GroupDocs.Annotation に利用できる無料トライアルはありますか?

 A: はい、次のサイトから GroupDocs.Annotation の無料トライアルにアクセスできます。[このリンク](https://releases.groupdocs.com/).

### Q: GroupDocs.Annotation for .NET のドキュメントはどこで見つけられますか?

 A: 詳細なドキュメントを参照してください。[ここ](https://reference.groupdocs.com/annotation/net/).

### Q: GroupDocs.Annotation に関するサポートや支援を受けるにはどうすればよいですか?

 A: GroupDocs.Annotation コミュニティ フォーラムからサポートと支援を求めることができます。[ここ](https://forum.groupdocs.com/c/annotation/10).