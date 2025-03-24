---
title: 注釈なしでプレビューを生成
linktitle: 注釈なしでプレビューを生成
second_title: GroupDocs.Annotation .NET API
description: GroupDocs.Annotation for .NET を使用して、.NET アプリケーション内でのドキュメントのコラボレーションと注釈を強化します。この強力なライブラリを使用すると、ドキュメントに簡単に注釈を付け、マークアップし、レビューできます。
weight: 13
url: /ja/net/advanced-usage/generate-preview-without-annotations/
---

# 注釈なしでプレビューを生成

## 導入
今日のデジタル時代では、ドキュメント上での効率的なコラボレーションが生産性と成功の鍵となります。世界中に散らばるチームメンバーとプロジェクトに取り組んでいる場合でも、重要な契約に関してクライアントと協力している場合でも、ドキュメントにシームレスに注釈を付けてレビューできる機能は非常に重要です。 GroupDocs.Annotation for .NET を使用すると、ドキュメントのコラボレーションを次のレベルに引き上げ、.NET アプリケーション内で直接簡単に注釈、マークアップ、レビューを行うことができます。
## 前提条件
GroupDocs.Annotation for .NET を使用してドキュメント アノテーションの世界に飛び込む前に、いくつかの前提条件を満たしている必要があります。
### 1. GroupDocs.Annotation for .NET をインストールする
何よりもまず、GroupDocs.Annotation for .NET をダウンロードしてインストールする必要があります。ダウンロードリンクが見つかります[ここ](https://releases.groupdocs.com/annotation/net/)。提供されるインストール手順に従って、.NET 環境にライブラリをセットアップします。
### 2. ライセンスの取得 (オプション)
GroupDocs.Annotation for .NET は無料試用版を提供していますが、その機能に完全にアクセスするにはライセンスの取得を検討することをお勧めします。ライセンスを購入できます[ここ](https://purchase.groupdocs.com/buy)または一時ライセンスをリクエストする[ここ](https://purchase.groupdocs.com/temporary-license/)テスト目的のため。
### 3. C# および .NET 開発に関する知識
GroupDocs.Annotation for .NET を最大限に活用するには、C# と .NET 開発の基本を理解しておくと役立ちます。これにより、ライブラリを既存のアプリケーションやワークフローにシームレスに統合できるようになります。
### 4. PDF ビューアをインストールする
GroupDocs.Annotation for .NET は PDF ドキュメントで動作するため、注釈付きドキュメントをプレビューするには、システムに PDF ビューアがインストールされている必要があります。 Adobe Acrobat Reader またはその他の PDF ビューアで十分です。

## 名前空間のインポート
ドキュメントへの注釈付けを開始する前に、必要な名前空間を .NET プロジェクトにインポートする必要があります。これにより、GroupDocs.Annotation for .NET によって提供されるクラスとメソッドにアクセスできるようになります。

```csharp
using System.IO;
using GroupDocs.Annotation.Options;
```

すべての設定が完了したので、注釈のないドキュメントのプレビューを生成してみましょう。これを行うには、次の手順に従います。
## ステップ 1: アノテーターを初期化する
まず、のインスタンスを作成します。`Annotator`クラスに、注釈を付けたいドキュメントへのパスを渡します。
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
{
```
## ステップ 2: プレビュー オプションを構成する
次に、要件に応じてプレビュー オプションを構成します。プレビューに含めるページ番号、プレビュー形式 (PNG など)、および注釈をレンダリングするかどうかを指定できます。
```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] {1, 2, 3, 4, 5, 6};
    previewOptions.RenderAnnotations = false;
```
## ステップ 3: プレビューを生成する
最後に、次のコマンドを使用してプレビューを生成します。`GeneratePreview`の方法`Document`クラスに、構成されたプレビュー オプションを渡します。
```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```
これらの簡単な手順に従うことで、GroupDocs.Annotation for .NET を使用して、注釈なしのドキュメントのプレビューを生成できます。

## 結論
結論として、GroupDocs.Annotation for .NET は、.NET アプリケーション内でのドキュメントのコラボレーションと注釈のための強力なソリューションを提供します。このチュートリアルで概説されている手順に従うことで、ドキュメントの注釈機能をプロジェクトにシームレスに統合し、コラボレーションと生産性を向上させることができます。
## よくある質問
### Q: GroupDocs.Annotation for .NET を PDF 以外のドキュメント形式で使用できますか?
はい。GroupDocs.Annotation for .NET は、DOCX、XLSX、PPTX などのさまざまなドキュメント形式をサポートしています。
### Q: GroupDocs.Annotation for .NET は .NET Core と互換性がありますか?
はい。GroupDocs.Annotation for .NET は、.NET Framework 環境と .NET Core 環境の両方と互換性があります。
### Q: GroupDocs.Annotation for .NET はカスタマイズ可能な注釈ツールを提供しますか?
はい、GroupDocs.Annotation for .NET は、特定の要件に合わせてカスタマイズできるさまざまな注釈ツールを提供します。
### Q: GroupDocs.Annotation for .NET を Web アプリケーションに統合できますか?
はい、GroupDocs.Annotation for .NET はデスクトップ アプリケーションと Web アプリケーションの両方に統合でき、シームレスなドキュメント コラボレーション機能を提供します。
### Q: GroupDocs.Annotation for .NET に関するサポートや支援が受けられるコミュニティ フォーラムはありますか?
はい、GroupDocs.Annotation フォーラムでサポートと支援を見つけることができます。[ここ](https://forum.groupdocs.com/c/annotation/10).