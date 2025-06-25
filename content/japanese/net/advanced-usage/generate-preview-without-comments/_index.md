---
"description": "GroupDocs.Annotation for .NET を使用して、ドキュメント注釈機能を .NET アプリケーションにシームレスに統合する方法を学びます。"
"linktitle": "コメントなしでプレビューを生成する"
"second_title": "GroupDocs.Annotation .NET API"
"title": "コメントなしでプレビューを生成する"
"url": "/ja/net/advanced-usage/generate-preview-without-comments/"
"weight": 14
---

# コメントなしでプレビューを生成する

## 導入
GroupDocs.Annotation for .NETは、開発者が.NETアプリケーションにアノテーション機能をシームレスに組み込むことを可能にする強力なツールです。ドキュメント管理システム、コラボレーションプラットフォーム、あるいはドキュメントアノテーション機能を必要とするその他のアプリケーションを開発している場合でも、GroupDocs.Annotationはアプリケーションの機能を強化するための包括的なツールセットを提供します。
## 前提条件
GroupDocs.Annotation for .NET の使用を開始する前に、次の前提条件が設定されていることを確認してください。
### 1. GroupDocs.Annotation for .NET をインストールする
まず、GroupDocs.Annotation for .NETをダウンロードしてインストールする必要があります。ダウンロードリンクは以下にあります。 [ここ](https://releases.groupdocs.com/annotation/net/)スムーズなセットアッププロセスのために、ドキュメントに記載されているインストール手順に従ってください。
### 2. ライセンスを取得する
GroupDocs.Annotation for .NETを商用利用するにはライセンスが必要です。ライセンスは以下から取得できます。 [ここ](https://purchase.groupdocs.com/buy) または一時ライセンスを選択する [ここ](https://purchase.groupdocs.com/temporary-license/) テスト目的のため。
### 3. .NET Framework に関する知識
GroupDocs.Annotation for .NET を効果的に活用するには、.NET Framework と C# プログラミング言語に関する基本的な知識が不可欠です。

## 名前空間のインポート
前提条件が設定されたので、必要な名前空間を .NET アプリケーションにインポートしましょう。

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Options;
```

GroupDocs.Annotation for .NET を使用してコメントなしのプレビューを生成するには、次の手順に従います。
## ステップ1: アノテーターを初期化する
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"_DOCX))
{
```
## ステップ2: プレビューオプションを設定する
```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
```
## ステップ3: プレビュー形式とページ番号を指定する
```csharp
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2, 3, 4, 5, 6 };
```
## ステップ4: コメントのレンダリングを無効にする
```csharp
    previewOptions.RenderComments = false;
```
## ステップ5: プレビューを生成する
```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```
これらの手順を実行すると、.NET アプリケーションはコメントをレンダリングせずに、ドキュメントから指定されたページのプレビューを生成できるようになります。

## 結論
GroupDocs.Annotation for .NET を使えば、.NET アプリケーションへの注釈機能の組み込みがこれまでになく簡単になります。このチュートリアルで説明する手順に従うことで、ドキュメント注釈機能をアプリケーションにシームレスに統合し、コラボレーションとドキュメント管理を強化できます。
## よくある質問
### GroupDocs.Annotation for .NET はすべてのドキュメント形式と互換性がありますか?
GroupDocs.Annotation for .NET は、PDF、DOCX、PPTX、XLSX など、幅広いドキュメント形式をサポートしています。
### GroupDocs.Annotation for .NET を使用して生成された注釈の外観をカスタマイズできますか?
はい、GroupDocs.Annotation for .NET には広範なカスタマイズ オプションが用意されており、アプリケーションのニーズに合わせて注釈の外観をカスタマイズできます。
### GroupDocs.Annotation for .NET は複数ユーザーのコラボレーションをサポートしていますか?
はい、GroupDocs.Annotation for .NET は共同注釈機能を提供しており、複数のユーザーが同時にドキュメントに注釈を付けることができます。
### GroupDocs.Annotation for .NET のテクニカル サポートは受けられますか?
はい、GroupDocs.Annotation for .NETのテクニカルサポートは、 [サポートフォーラム](https://forum。groupdocs.com/c/annotation/10).
### 購入前に GroupDocs.Annotation for .NET を無料で試すことはできますか?
はい、無料トライアルをダウンロードして、GroupDocs.Annotation for .NET の機能を試すことができます。 [ここ](https://releases。groupdocs.com/).