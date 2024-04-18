---
title: コメントなしでプレビューを生成
linktitle: コメントなしでプレビューを生成
second_title: GroupDocs.Annotation .NET API
description: GroupDocs.Annotation for .NET を使用して、ドキュメントの注釈機能を .NET アプリケーションにシームレスに統合する方法を学びます。
type: docs
weight: 14
url: /ja/net/advanced-usage/generate-preview-without-comments/
---
## 導入
GroupDocs.Annotation for .NET は、開発者が注釈機能を .NET アプリケーションにシームレスに組み込むことができる強力なツールです。ドキュメント管理システム、コラボレーション プラットフォーム、またはドキュメント注釈機能を必要とするその他のアプリケーションで作業しているかどうかに関係なく、GroupDocs.Annotation はアプリケーションの機能を強化するための包括的なツール セットを提供します。
## 前提条件
GroupDocs.Annotation for .NET の使用に入る前に、次の前提条件が設定されていることを確認してください。
### 1. GroupDocs.Annotation for .NET をインストールする
まず、GroupDocs.Annotation for .NET をダウンロードしてインストールする必要があります。ダウンロードリンクが見つかります[ここ](https://releases.groupdocs.com/annotation/net/)。セットアップ プロセスをスムーズに行うには、ドキュメントに記載されているインストール手順に従ってください。
### 2. ライセンスの取得
GroupDocs.Annotation for .NET を商用利用するにはライセンスが必要です。からライセンスを取得できます[ここ](https://purchase.groupdocs.com/buy)または一時ライセンスを選択する[ここ](https://purchase.groupdocs.com/temporary-license/)テスト目的のため。
### 3. .NET Framework に関する知識
GroupDocs.Annotation for .NET を効果的に利用するには、.NET Framework と C# プログラミング言語の基本的な知識が不可欠です。

## 名前空間のインポート
前提条件を設定したので、必要な名前空間を .NET アプリケーションにインポートしましょう。

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Options;
```

GroupDocs.Annotation for .NET を使用してコメントなしのプレビューを生成するには、次の段階的な手順に従ってください。
## ステップ 1: アノテーターを初期化する
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"_DOCX))
{
```
## ステップ 2: プレビュー オプションを構成する
```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
```
## ステップ 3: プレビュー形式とページ番号を指定する
```csharp
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2, 3, 4, 5, 6 };
```
## ステップ 4: コメントのレンダリングを無効にする
```csharp
    previewOptions.RenderComments = false;
```
## ステップ 5: プレビューを生成する
```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```
これらの手順を実行すると、.NET アプリケーションはコメントを表示せずに、ドキュメントから指定されたページのプレビューを生成できるようになります。

## 結論
GroupDocs.Annotation for .NET のおかげで、注釈機能を .NET アプリケーションに組み込むことがこれまでになく簡単になりました。このチュートリアルで概説されている手順に従うことで、ドキュメントの注釈機能をアプリケーションにシームレスに統合し、コラボレーションとドキュメント管理を強化できます。
## よくある質問
### GroupDocs.Annotation for .NET はすべてのドキュメント形式と互換性がありますか?
GroupDocs.Annotation for .NET は、PDF、DOCX、PPTX、XLSX など、幅広いドキュメント形式をサポートしています。
### GroupDocs.Annotation for .NET を使用して生成された注釈の外観をカスタマイズできますか?
はい、GroupDocs.Annotation for .NET には広範なカスタマイズ オプションが用意されており、アプリケーションのニーズに合わせて注釈の外観を調整できます。
### GroupDocs.Annotation for .NET はマルチユーザー コラボレーションをサポートしていますか?
はい、GroupDocs.Annotation for .NET は共同注釈機能を提供し、複数のユーザーが同時にドキュメントに注釈を付けることができます。
### GroupDocs.Annotation for .NET のテクニカル サポートは利用できますか?
はい、GroupDocs.Annotation for .NET のテクニカル サポートは、[サポートフォーラム](https://forum.groupdocs.com/c/annotation/10).
### 購入する前に GroupDocs.Annotation for .NET を無料で試すことはできますか?
はい、無料試用版をダウンロードすると、GroupDocs.Annotation for .NET の機能を探索できます。[ここ](https://releases.groupdocs.com/).