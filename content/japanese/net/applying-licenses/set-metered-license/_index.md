---
"description": ".NET アプリケーションのリソース使用とドキュメント注釈機能のために GroupDocs.Annotation .NET の従量制ライセンスを設定する方法を学習します。"
"linktitle": "従量制ライセンスの設定"
"second_title": "GroupDocs.Annotation .NET API"
"title": "従量制ライセンスの設定"
"url": "/ja/net/applying-licenses/set-metered-license/"
type: docs
"weight": 12
---

# 従量制ライセンスの設定

## 導入
GroupDocs.Annotation for .NETは、開発者が.NETアプリケーションにドキュメント注釈機能を簡単に追加できるようにする強力なライブラリです。ドキュメント管理システム、コラボレーションプラットフォーム、あるいはドキュメントのレビューとマークアップを伴うあらゆるアプリケーションを構築する場合でも、GroupDocs.Annotation for .NETはプロセスを効率化するための包括的なツールセットを提供します。
このチュートリアルでは、GroupDocs.Annotation .NETの従量制ライセンスの設定手順について詳しく説明します。従量制ライセンスでは、使用したリソースに対してのみ料金が発生するため、あらゆる規模のプロジェクトにおいて費用対効果の高いソリューションとなります。以下の手順に従うことで、リソース使用率を最適化し、予算管理を維持しながら、GroupDocs.Annotationを.NETアプリケーションにシームレスに統合できます。
## 前提条件
チュートリアルに進む前に、次の前提条件が満たされていることを確認してください。
1. GroupDocs.Annotation for .NETライブラリ:ライブラリを以下からダウンロードしてください。 [Webサイト](https://releases。groupdocs.com/annotation/net/).
2. GroupDocsアカウントへのアクセス：従量制ライセンスの設定に必要な公開鍵と秘密鍵を取得するには、GroupDocsアカウントが必要です。まだアカウントをお持ちでない場合は、無料トライアルにご登録ください。 [ここ](https://releases。groupdocs.com/).
3. C# と .NET Framework の基本的な理解: C# プログラミング言語と .NET Framework の知識は、このチュートリアルで説明する手順を実装するのに役立ちます。

## 名前空間のインポート
まず、C#プロジェクトに必要な名前空間をインポートしてください。これらの名前空間は、GroupDocs.Annotationの機能とやり取りするために不可欠です。
```csharp
using System;
```
## ステップ1: 公開鍵と秘密鍵を取得する
従量制ライセンスを設定する前に、GroupDocs アカウント ダッシュボードから公開キーと秘密キーを取得する必要があります。
1. GroupDocs アカウントにログインします。
2. ライセンス管理セクションに移動します。
3. GroupDocs から提供された公開鍵と秘密鍵をコピーします。
## ステップ2: 従量制ライセンスを設定する
公開キーと秘密キーを取得したら、.NET アプリケーションで従量制ライセンスを設定できます。
```csharp
string publicKey = "*****"; // *****を公開鍵に置き換えてください
string privateKey = "*****"; // *****を秘密鍵に置き換えてください
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

## 結論
結論として、GroupDocs.Annotation .NETの従量制ライセンスの設定は、ドキュメントアノテーションプロジェクトにおけるリソースの効率的な活用と費用対効果を保証する簡単なプロセスです。このチュートリアルで概説されている手順に従うことで、GroupDocs.Annotationを.NETアプリケーションにシームレスに統合し、ドキュメントの共同作業とレビュー機能を強化できます。
## よくある質問
### GroupDocs.Annotation for .NET を商用プロジェクトで使用できますか?
はい、GroupDocs.Annotation for .NETは商用プロジェクトと非商用プロジェクトの両方でご利用いただけます。ただし、プロジェクトの要件に応じて適切なライセンスを取得する必要があります。
### GroupDocs.Annotation for .NET の試用版はありますか?
はい、GroupDocs.Annotation for .NETの無料トライアルを以下のサイトからご利用いただけます。 [このリンク](https://releases。groupdocs.com/).
### GroupDocs.Annotation for .NET のテクニカル サポートを受けるにはどうすればよいですか?
GroupDocsフォーラムにアクセスして技術サポートを受けることができます。 [ここ](https://forum。groupdocs.com/c/annotation/10).
### 利用できる一時ライセンスのオプションはありますか?
はい、短期間の使用や評価目的でGroupDocsから一時ライセンスを取得できます。 [このリンク](https://purchase.groupdocs.com/temporary-license/) 詳細についてはこちらをご覧ください。
### プロジェクトの要件に応じて注釈機能をカスタマイズできますか?
はい、GroupDocs.Annotation for .NET には広範なカスタマイズ オプションが用意されており、特定のプロジェクトのニーズに合わせて注釈機能をカスタマイズできます。