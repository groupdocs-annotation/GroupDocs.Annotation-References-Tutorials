---
"description": "GroupDocs.Annotation を使用して、.NET で PDF やその他のドキュメントから注釈を削除する方法を学びます。コード例を交えたステップバイステップのガイドです。"
"linktitle": ".NET の保存オプションを使用して注釈を削除する"
"second_title": "GroupDocs.Annotation .NET API"
"title": ".NET の保存オプションを使用して注釈を削除する"
"url": "/ja/net/removing-annotations/remove-annotations-using-save-options/"
type: docs
"weight": 14
---

# .NET の保存オプションを使用して注釈を削除する

## 導入

GroupDocs.Annotation for .NETは、開発者が.NETアプリケーションに簡単に注釈機能を追加できる強力なツールです。ドキュメント管理システム、コラボレーションプラットフォーム、あるいはドキュメント処理を伴うその他のアプリケーションを開発している場合でも、GroupDocs.AnnotationはPDFやその他のドキュメント形式にシームレスに注釈を付けるための包括的な機能セットを提供します。

## 前提条件

GroupDocs.Annotation for .NET を使用してドキュメントに注釈を付ける世界に飛び込む前に、次の前提条件が満たされていることを確認してください。

### 1. GroupDocs.Annotation for .NET をインストールする

まず、GroupDocs.Annotation for .NETをダウンロードしてインストールします。最新バージョンは以下からダウンロードできます。 [ダウンロードページ](https://releases。groupdocs.com/annotation/net/).

## 名前空間のインポート

.NETプロジェクトでGroupDocs.Annotationを使用するには、必要な名前空間をインポートする必要があります。一般的に使用される名前空間は以下のとおりです。

```csharp
using GroupDocs.Annotation.Options;
using System;
using System.IO;
```


ここで、.NET の保存オプション機能を使用してドキュメントから注釈を削除するプロセスを見ていきましょう。

## ステップ1: 出力パスを定義する

まず、注釈を削除した文書を保存する出力パスを定義します。 `Path.Combine` ディレクトリ パスと出力ファイル名を結合する方法。

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## ステップ2: アノテーターを初期化する

次に、 `Annotator` 注釈を含むドキュメントへのパスを提供することにより、クラスを作成します。

```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
{
    // 注釈削除コードはここに記入します
}
```

## ステップ3: 注釈を削除してドキュメントを保存する

さて、 `Save` の方法 `Annotator` クラスと一緒に `SaveOptions` 注釈を削除した文書を保存します。 `SaveOptions`、設定します `AnnotationTypes` 財産に `AnnotationType.None` すべての注釈を削除します。

```csharp
annotator.Save(outputPath, new SaveOptions() { AnnotationTypes = AnnotationType.None });
```

## ステップ4: 成功メッセージを表示する

最後に、注釈が削除された状態でドキュメントが正常に保存されたことを示す成功メッセージを表示します。

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論

結論として、GroupDocs.Annotation for .NETはドキュメントから注釈を削除するプロセスを簡素化します。上記のステップバイステップガイドに従うことで、開発者は注釈削除機能を.NETアプリケーションにシームレスに統合できます。

## よくある質問

### Q: GroupDocs.Annotation は PDF 以外のドキュメント形式から注釈を削除できますか?

A: GroupDocs.Annotation は、PDF、Word、Excel、PowerPoint など、さまざまなドキュメント形式をサポートしており、幅広いドキュメントから注釈を削除できます。

### Q: GroupDocs.Annotation は既存の .NET プロジェクトに簡単に統合できますか?

A: はい、GroupDocs.Annotation はシンプルな API と包括的なドキュメントを提供するため、開発者は簡単に注釈機能を .NET アプリケーションに統合できます。

### Q: GroupDocs.Annotation は注釈の選択的な削除をサポートしていますか?

A: はい、GroupDocs.Annotation を使用すると、開発者は削除する注釈の種類を指定できるため、ドキュメント内の注釈を柔軟に管理できます。

### Q: 購入前に GroupDocs.Annotation を無料で試すことはできますか?

A: はい、GroupDocs.Annotationの無料試用版は、 [リリースページ](https://releases.groupdocs.com/) 購入を決定する前にその機能を調べます。

### Q: GroupDocs.Annotation のサポートはどこで受けられますか?

A: 技術的なサポートやコミュニティサポートについては、 [GroupDocs.Annotation フォーラム](https://forum。groupdocs.com/c/annotation/10).