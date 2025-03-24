---
title: テキストの波線注釈をドキュメントに追加
linktitle: テキストの波線注釈をドキュメントに追加
second_title: GroupDocs.Annotation .NET API
description: Groupdocs.Annotation for .NET を使用して、テキストの波線注釈をドキュメントに簡単に追加する方法を学びます。コラボレーションと文書レビューのプロセスを強化します。
weight: 25
url: /ja/net/unlocking-annotation-power/add-text-squiggly-annotation/
---

# テキストの波線注釈をドキュメントに追加

## 導入

Groupdocs.Annotation for .NET は、開発者が堅牢な注釈機能を .NET アプリケーションに簡単に統合できる多用途ライブラリです。 PDF、Word ドキュメント、その他の一般的なファイル形式を使用している場合でも、Groupdocs.Annotation は注釈を付けてドキュメントのコラボレーションを強化するためのシームレスなソリューションを提供します。

## 前提条件

チュートリアルに入る前に、次の前提条件が満たされていることを確認してください。

## 名前空間のインポート

Groupdocs.Annotation for .NET によって提供される機能にアクセスするために、必要な名前空間を必ずインポートしてください。

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

前提条件を説明したので、テキストの波線注釈を追加するプロセスを複数のステップに分けてみましょう。

## ステップ 1: 出力パスを定義する

注釈付きドキュメントを保存するパスを定義します。

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## ステップ 2: アノテーターを初期化する

入力ドキュメント パスを指定して Annotator オブジェクトを初期化します。

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    //注釈コードはここに記述されます
}
```

## ステップ 3: 波線の注釈を作成する

SquigglyAnnotation オブジェクトを作成し、そのプロパティを指定します。

```csharp
SquigglyAnnotation squiggly = new SquigglyAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is squiggly annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    SquigglyColor = 1422623,
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

## ステップ 4: 注釈を追加する

作成した波線注釈をドキュメントに追加します。

```csharp
annotator.Add(squiggly);
```

## ステップ 5: ドキュメントを保存する

注釈付きドキュメントを指定された出力パスに保存します。

```csharp
annotator.Save(outputPath);
```

## ステップ6: 確認を表示する

注釈付きドキュメントが正常に保存されたことを確認するメッセージを表示します。

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論

結論として、Groupdocs.Annotation for .NET は、ドキュメントの注釈機能を .NET アプリケーションにシームレスに統合するための強力なツール セットを開発者に提供します。このステップバイステップのガイドに従うことで、文書にテキストの波線注釈を簡単に追加して、コラボレーションと文書レビューのプロセスを強化することができます。

## よくある質問

### Q: Groupdocs.Annotation はさまざまなファイル形式の注釈をサポートできますか?

A: はい、Groupdocs.Annotation は、PDF、Word ドキュメント、Excel シートなどを含む幅広いファイル形式での注釈をサポートしています。

### Q: Groupdocs.Annotation はデスクトップ アプリケーションと Web アプリケーションの両方と互換性がありますか?

A: もちろんです！ Groupdocs.Annotation は、デスクトップ アプリケーションと Web アプリケーションの両方にシームレスに統合でき、柔軟性と多用途性を提供します。

### Q: Groupdocs.Annotation で利用できるライセンス オプションはありますか?

A: はい、Groupdocs.Annotation は、試用目的の一時ライセンスなど、個人または企業のニーズに合わせてカスタマイズされた柔軟なライセンス オプションを提供します。

### Q: Groupdocs.Annotation を使用して作成された注釈はカスタマイズできますか?

A：確かに！ Groupdocs.Annotation は注釈の広範なカスタマイズ オプションを提供し、開発者が注釈を特定の要件に合わせて調整できるようにします。

### Q: Groupdocs.Annotation は開発者にサポートとドキュメントを提供しますか?

A：確かに！ Groupdocs.Annotation は、開発者がその機能を効果的に利用できるように、包括的なドキュメントと専用のサポート フォーラムを提供します。