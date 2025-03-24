---
title: FTPからドキュメントをロード
linktitle: FTPからドキュメントをロード
second_title: GroupDocs.Annotation .NET API
description: GroupDocs.Annotation を使用して .NET アプリケーションを強化し、シームレスなドキュメント注釈を追加します。ステップバイステップのチュートリアルが含まれています。
weight: 12
url: /ja/net/document-loading-essentials/load-document-from-ftp/
---
## 導入
GroupDocs.Annotation for .NET は、.NET アプリケーション内でドキュメントの注釈機能を簡単に利用できるように設計された多用途ライブラリです。 PDF、Microsoft Office ドキュメント、画像、その他の形式を扱う場合でも、このライブラリはコメント、ハイライト、図形などの注釈を追加してコラボレーションとドキュメント管理を強化するための統合ソリューションを提供します。
## 前提条件
チュートリアルに入る前に、次の前提条件が満たされていることを確認してください。
1. C# の知識: このチュートリアルで提供されるコード例を理解して実装するには、C# プログラミング言語の熟練度が不可欠です。
2.  GroupDocs.Annotation for .NET: GroupDocs.Annotation for .NET を次の場所からダウンロードしてインストールしてください。[ダウンロードリンク](https://releases.groupdocs.com/annotation/net/)。インストール手順に従って、ライブラリを .NET プロジェクトに正常に統合します。
## 名前空間のインポート
GroupDocs.Annotation for .NET 機能を利用するには、必要な名前空間を C# プロジェクトにインポートする必要があります。次の手順を実行します：

C# プロジェクト内で、コード ファイルの先頭に必要な名前空間を含めます。
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```

ここで、FTP からドキュメントをロードし、GroupDocs.Annotation for .NET を使用してそれに注釈を追加するプロセスを詳しく見てみましょう。
## ステップ 1: 出力パスを定義する
注釈付きドキュメントが保存される出力パスを指定します。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## ステップ 2: FTP からドキュメントをロードする
指定されたファイル パスを使用して、FTP サーバーからドキュメントを取得します。
```csharp
string filePath = "sample.pdf";
using (Annotator annotator = new Annotator(GetFileFromFtp(filePath)))
{
    //ここに注釈コードが追加されます
}
```
## ステップ 3: 注釈を追加する
領域注釈などの必要な注釈を定義してドキュメントに追加します。
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## ステップ 4: 注釈付きドキュメントを保存する
注釈付きドキュメントを指定された出力パスに保存します。
```csharp
annotator.Save(outputPath);
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
## ステップ 5: FTP からファイルを取得する
FTPサーバーからファイルを取得するメソッドを実装します。
```csharp
private static Stream GetFileFromFtp(string filePath)
{
    Uri uri = new Uri(filePath);
    FtpWebRequest request = CreateRequest(uri);
    using (WebResponse response = request.GetResponse())
        return GetFileStream(response);
}
```
## ステップ 6: FTP リクエストの作成
ファイルをダウンロードするための FTP リクエストを生成します。
```csharp
private static FtpWebRequest CreateRequest(Uri uri)
{
    FtpWebRequest request = (FtpWebRequest)WebRequest.Create(uri);
    request.Method = WebRequestMethods.Ftp.DownloadFile;
    return request;
}
```
## ステップ 7: ファイル ストリームを取得する
FTP 応答からファイル ストリームを取得します。
```csharp
private static Stream GetFileStream(WebResponse response)
{
    MemoryStream fileStream = new MemoryStream();
    using (Stream responseStream = response.GetResponseStream())
        responseStream.CopyTo(fileStream);
    fileStream.Position = 0;
    return fileStream;
}
```
## 結論
結論として、GroupDocs.Annotation for .NET を使用すると、開発者はドキュメントの注釈機能を .NET アプリケーションにシームレスに統合できます。このチュートリアルで概説されているステップバイステップのガイドに従うことで、FTP からドキュメントを効率的にロードし、注釈を簡単に追加して、アプリケーション内でのコラボレーションとドキュメント管理を強化できます。
## よくある質問
### GroupDocs.Annotation for .NET はすべてのドキュメント形式と互換性がありますか?
はい、GroupDocs.Annotation for .NET は、PDF、Microsoft Office ドキュメント、画像などを含む幅広いドキュメント形式をサポートしています。
### GroupDocs.Annotation for .NET を使用して追加された注釈の外観をカスタマイズできますか?
確かに、GroupDocs.Annotation for .NET は、色、スタイル、形状など、注釈の外観に関する広範なカスタマイズ オプションを提供します。
### GroupDocs.Annotation for .NET はクラウド ストレージ サービスをサポートしますか?
はい、GroupDocs.Annotation for .NET は一般的なクラウド ストレージ サービスとシームレスに統合されており、Dropbox、Google Drive、OneDrive などのサービスからドキュメントを読み込んだり保存したりできます。
### GroupDocs.Annotation for .NET で利用できる試用版はありますか?
はい。[リリースページ](https://releases.groupdocs.com/).
### GroupDocs.Annotation for .NET の技術サポートやサポートを受けるにはどうすればよいですか?
技術サポート、トラブルシューティング、または一般的な問い合わせについては、GroupDocs.Annotation for .NET にアクセスしてください。[サポートフォーラム](https://forum.groupdocs.com/c/annotation/10).