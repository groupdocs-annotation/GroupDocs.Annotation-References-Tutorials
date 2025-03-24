---
title: .NET の保存オプションを使用して注釈を削除する
linktitle: .NET の保存オプションを使用して注釈を削除する
second_title: GroupDocs.Annotation .NET API
description: GroupDocs.Annotation を使用して .NET の PDF やその他のドキュメントから注釈を削除する方法を学びます。コード例を含むステップバイステップのガイド。
weight: 14
url: /ja/net/removing-annotations/remove-annotations-using-save-options/
---
## 導入

GroupDocs.Annotation for .NET は、開発者が .NET アプリケーションに注釈機能を簡単に追加できる強力なツールです。ドキュメント管理システム、コラボレーション プラットフォーム、またはドキュメント処理を伴うその他のアプリケーションで作業しているかどうかに関係なく、GroupDocs.Annotation は、PDF およびその他のドキュメント形式にシームレスに注釈を付けるための包括的な機能セットを提供します。

## 前提条件

GroupDocs.Annotation for .NET を使用してドキュメントに注釈を付ける世界に入る前に、次の前提条件が満たされていることを確認してください。

### 1. GroupDocs.Annotation for .NET をインストールする

まず、GroupDocs.Annotation for .NET をダウンロードしてインストールします。最新バージョンはからダウンロードできます。[download page](https://releases.groupdocs.com/annotation/net/).

## 名前空間のインポート

.NET プロジェクトで GroupDocs.Annotation の使用を開始するには、必要な名前空間をインポートする必要があります。一般的に使用する名前空間は次のとおりです。

```csharp
using GroupDocs.Annotation.Options;
using System;
using System.IO;
```


次に、.NET の保存オプション機能を使用してドキュメントから注釈を削除するプロセスを見てみましょう。

## ステップ 1: 出力パスを定義する

まず、注釈が削除されたドキュメントが保存される出力パスを定義します。使用できます`Path.Combine`ディレクトリ パスと出力ファイル名を組み合わせるメソッド。

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## ステップ 2: アノテーターを初期化する

次に、のインスタンスを初期化します。`Annotator`注釈を含むドキュメントへのパスを指定してクラスを作成します。

```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
{
    //注釈削除コードがここに挿入されます
}
```

## ステップ 3: 注釈を削除してドキュメントを保存する

ここで、`Save`の方法`Annotator`クラスと一緒に`SaveOptions`注釈を削除したドキュメントを保存します。の中に`SaveOptions`、 をセットする`AnnotationTypes`財産を`AnnotationType.None`すべての注釈を削除します。

```csharp
annotator.Save(outputPath, new SaveOptions() { AnnotationTypes = AnnotationType.None });
```

## ステップ 4: 成功メッセージを表示する

最後に、注釈が削除された状態でドキュメントが正常に保存されたことを示す成功メッセージを表示します。

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論

結論として、GroupDocs.Annotation for .NET はドキュメントから注釈を削除するプロセスを簡素化します。上記のステップバイステップ ガイドに従うことで、開発者は注釈削除機能を .NET アプリケーションにシームレスに統合できます。

## よくある質問

### Q: GroupDocs.Annotation は PDF 以外のドキュメント形式から注釈を削除できますか?

A: GroupDocs.Annotation は、PDF、Word、Excel、PowerPoint などのさまざまなドキュメント形式をサポートしているため、幅広いドキュメントから注釈を削除できます。

### Q: GroupDocs.Annotation は既存の .NET プロジェクトに簡単に統合できますか?

A: はい、GroupDocs.Annotation はシンプルな API と包括的なドキュメントを提供するため、開発者は注釈機能を .NET アプリケーションに簡単に統合できます。

### Q: GroupDocs.Annotation は注釈の選択的な削除をサポートしていますか?

A: はい、GroupDocs.Annotation を使用すると、開発者は削除する注釈の種類を指定できるため、ドキュメント内の注釈を柔軟に管理できます。

### Q: 購入する前に GroupDocs.Annotation を無料で試すことはできますか?

 A: はい、GroupDocs.Annotation の無料試用版を次のサイトからダウンロードできます。[リリースページ](https://releases.groupdocs.com/)購入を決定する前に、その機能を調べてください。

### Q: GroupDocs.Annotation のサポートはどこで入手できますか?

 A: 技術サポートとコミュニティ サポートについては、次のサイトにアクセスしてください。[GroupDocs.Annotation フォーラム](https://forum.groupdocs.com/c/annotation/10).