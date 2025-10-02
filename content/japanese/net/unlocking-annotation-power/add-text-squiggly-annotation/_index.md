---
"description": "Groupdocs.Annotation for .NET を使用して、ドキュメントに波線テキスト注釈を簡単に追加する方法を学びましょう。共同作業とドキュメントレビューのプロセスを強化します。"
"linktitle": "ドキュメントにテキストの波線注釈を追加する"
"second_title": "GroupDocs.Annotation .NET API"
"title": "ドキュメントにテキストの波線注釈を追加する"
"url": "/ja/net/unlocking-annotation-power/add-text-squiggly-annotation/"
type: docs
"weight": 25
---

# ドキュメントにテキストの波線注釈を追加する

## 導入

Groupdocs.Annotation for .NETは、開発者が強力な注釈機能を.NETアプリケーションに簡単に統合できるようにする多用途ライブラリです。PDF、Word文書、その他の一般的なファイル形式を扱う場合でも、Groupdocs.Annotationは、ドキュメントへの注釈付けと共同作業の強化のためのシームレスなソリューションを提供します。

## 前提条件

チュートリアルに進む前に、次の前提条件が満たされていることを確認してください。

## 名前空間のインポート

Groupdocs.Annotation for .NET によって提供される機能にアクセスするには、必要な名前空間を必ずインポートしてください。

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

前提条件が満たされたので、テキストの波線注釈を追加するプロセスを複数のステップに分解してみましょう。

## ステップ1: 出力パスを定義する

注釈が付けられたドキュメントを保存するパスを定義します。

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## ステップ2: アノテーターを初期化する

入力ドキュメント パスを指定して Annotator オブジェクトを初期化します。

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // 注釈コードはここに記入します
}
```

## ステップ3：波線注釈を作成する

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

## ステップ4: 注釈を追加する

作成した波線注釈をドキュメントに追加します。

```csharp
annotator.Add(squiggly);
```

## ステップ5: ドキュメントを保存する

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

結論として、Groupdocs.Annotation for .NETは、開発者にドキュメント注釈機能を.NETアプリケーションにシームレスに統合するための強力なツールセットを提供します。このステップバイステップガイドに従うことで、ドキュメントに波線注釈を簡単に追加し、共同作業とドキュメントレビューのプロセスを強化することができます。

## よくある質問

### Q: Groupdocs.Annotation はさまざまなファイル形式の注釈をサポートできますか?

A: はい、Groupdocs.Annotation は、PDF、Word 文書、Excel シートなど、さまざまなファイル形式の注釈をサポートしています。

### Q: Groupdocs.Annotation はデスクトップ アプリケーションと Web アプリケーションの両方と互換性がありますか?

A: もちろんです! Groupdocs.Annotation はデスクトップ アプリケーションと Web アプリケーションの両方にシームレスに統合できるため、柔軟性と汎用性が向上します。

### Q: Groupdocs.Annotation にはライセンス オプションがありますか?

A: はい、Groupdocs.Annotation では、試用目的の一時ライセンスなど、個人または企業のニーズに合わせてカスタマイズされた柔軟なライセンス オプションを提供しています。

### Q: Groupdocs.Annotation を使用して作成された注釈はカスタマイズできますか?

A: もちろんです! Groupdocs.Annotation は、注釈の広範なカスタマイズ オプションを提供しており、開発者は特定の要件に合わせて注釈をカスタマイズできます。

### Q: Groupdocs.Annotation は開発者向けのサポートとドキュメントを提供していますか?

A: その通りです! Groupdocs.Annotation は、開発者がその機能を効果的に活用できるように支援するための包括的なドキュメントと専用のサポート フォーラムを提供しています。