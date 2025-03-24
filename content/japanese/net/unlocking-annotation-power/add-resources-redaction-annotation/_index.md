---
title: リソース墨消し注釈をドキュメントに追加
linktitle: リソース墨消し注釈をドキュメントに追加
second_title: GroupDocs.Annotation .NET API
description: GroupDocs.Annotation for .NET を使用してドキュメント管理ワークフローを強化します。 Resources Redaction Annotation を .NET にシームレスに統合して効率化します。
weight: 19
url: /ja/net/unlocking-annotation-power/add-resources-redaction-annotation/
---
## 導入
.NET 開発の領域では、ドキュメント注釈用の効率的なツールを統合すると、生産性が大幅に向上し、ワークフローが合理化されます。 GroupDocs.Annotation for .NET は堅牢なソリューションとして登場し、ドキュメントにシームレスに注釈を付けて操作するための豊富な機能を提供します。このチュートリアルでは、GroupDocs.Annotation for .NET 内の強力な機能である Resources Redaction Annotation を統合して利用するプロセスについて詳しく説明します。
## 前提条件
実装に入る前に、次の前提条件が満たされていることを確認してください。
### 1..NET開発環境
マシン上に機能的な .NET 開発環境がセットアップされていることを確認してください。そうでない場合は、Microsoft Web サイトから .NET SDK の最新バージョンをダウンロードしてインストールできます。
### 2. .NET 用の GroupDocs.Annotation
提供されている .NET ライブラリから GroupDocs.Annotation をダウンロードしてインストールします。[ダウンロードリンク](https://releases.groupdocs.com/annotation/net/)。シームレスに統合するには、ドキュメントに記載されているインストール手順に従ってください。
### 3. C# の基本的な理解
C# プログラミング言語の構文と概念を理解し、提供されたコード スニペットを効果的に実装します。

## 名前空間のインポート
GroupDocs.Annotation for .NET を使用して、ドキュメントの注釈に必要なクラスとメソッドにアクセスするために必要な名前空間を組み込みます。

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## ステップ 1: 出力パスを定義する
注釈付きドキュメントが保存される出力パスを指定します。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## ステップ 2: アノテーター オブジェクトを初期化する
入力ドキュメントへのパスを指定して、Annotator オブジェクトをインスタンス化します。
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    //ここに注釈コードが追加されます
}
```
## ステップ 3: リソースの編集アノテーションを作成する
ボックスの寸法、メッセージ、ページ番号、返信などの必要なプロパティを使用して ResourcesRedactionAnnotation オブジェクトを定義します。
```csharp
ResourcesRedactionAnnotation resourcesRedaction = new ResourcesRedactionAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is resources redaction annotation",
    PageNumber = 0,
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
アノテーター オブジェクトを使用して、作成したリソース リダクション アノテーションをドキュメントに追加します。
```csharp
annotator.Add(resourcesRedaction);
```
## ステップ 5: 注釈付きドキュメントを保存する
注釈付きドキュメントを指定された出力パスに保存します。
```csharp
annotator.Save(outputPath);
```
## ステップ 6: 成功メッセージを表示する
注釈プロセスが正常に完了したことをユーザーに通知し、注釈付きドキュメントへのパスを提供します。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
結論として、GroupDocs.Annotation for .NET は、ドキュメント アノテーション用の包括的なツール スイートを提供し、.NET 開発者がドキュメント管理ワークフローを効果的に強化できるようにします。このチュートリアルで概説されているステップバイステップのガイドに従うことで、Resources Redaction Annotation を .NET アプリケーションにシームレスに統合できるため、コラボレーションと生産性が向上します。
## よくある質問
### GroupDocs.Annotation for .NET はすべてのドキュメント形式と互換性がありますか?
GroupDocs.Annotation for .NET は、PDF、DOCX、PPTX、XLSX など、幅広いドキュメント形式をサポートしています。
### GroupDocs.Annotation for .NET を使用して作成された注釈の外観をカスタマイズできますか?
はい、色、不透明度、線の太さなどのプロパティを調整することで、注釈の外観をカスタマイズできます。
### GroupDocs.Annotation for .NET に利用できる無料試用版はありますか?
はい、提供されているから GroupDocs.Annotation for .NET の無料トライアルを利用できます。[リンク](https://releases.groupdocs.com/).
### GroupDocs.Annotation for .NET に関する支援やサポートを求めるにはどうすればよいですか?
 GroupDocs.Annotation フォーラムにアクセスしてください。[ここ](https://forum.groupdocs.com/c/annotation/10)コミュニティに支援を求めたり、質問を送信したりできます。
### GroupDocs.Annotation for .NET の一時ライセンスはどこで入手できますか?
GroupDocs.Annotation for .NET の一時ライセンスは、提供されているから取得できます。[リンク](https://purchase.groupdocs.com/temporary-license/).