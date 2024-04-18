---
title: Carregar documento do stream
linktitle: Carregar documento do stream
second_title: API GroupDocs.Annotation .NET
description: Aprenda como anotar documentos em .NET sem esforço com GroupDocs.Annotation. Melhore a colaboração e a produtividade.
type: docs
weight: 14
url: /pt/net/document-loading-essentials/load-document-from-stream/
---
## Introdução
GroupDocs.Annotation for .NET é uma biblioteca poderosa que permite aos desenvolvedores integrar recursos de anotação de documentos em seus aplicativos .NET sem esforço. Esteja você construindo um sistema de gerenciamento de documentos, uma plataforma de colaboração ou um aplicativo de e-learning, GroupDocs.Annotation fornece um conjunto versátil de ferramentas para fazer anotações em PDFs, documentos do Word, planilhas do Excel e muito mais.
## Pré-requisitos
Antes de mergulharmos no processo de anotação, certifique-se de ter os seguintes pré-requisitos:
1. Instalação do GroupDocs.Annotation for .NET: Baixe e instale GroupDocs.Annotation for .NET em[aqui](https://releases.groupdocs.com/annotation/net/).
2. Compreensão básica de programação C#: Familiaridade com a linguagem de programação C# e o framework .NET é essencial.
3. Configuração do ambiente de desenvolvimento: configure seu ambiente de desenvolvimento preferido com suporte ao .NET framework.

## Importando Namespaces
Para começar a anotar documentos usando GroupDocs.Annotation for .NET, importe os namespaces necessários para seu projeto C#:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

Agora, vamos dividir o processo de anotação em várias etapas:
## Etapa 1: carregar o documento do stream
Primeiramente, você precisa carregar o documento de um fluxo. Veja como você pode conseguir isso:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator(File.OpenRead("input.pdf")))
{
```
## Etapa 2: adicionar anotações
A seguir, você pode adicionar anotações ao documento. Vamos criar uma anotação de área como exemplo:
```csharp
	AreaAnnotation area = new AreaAnnotation()
	{
		Box = new Rectangle(100, 100, 100, 100),
		BackgroundColor = 65535,
	};
	annotator.Add(area);
```
## Etapa 3: Salvar documento com anotações
Após adicionar anotações, salve o documento anotado:
```csharp
	annotator.Save(File.Create(outputPath));
}
```
## Etapa 4: exibir mensagem de confirmação
Por fim, exiba uma mensagem confirmando o salvamento bem-sucedido do documento anotado:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusão
Concluindo, GroupDocs.Annotation for .NET fornece uma solução abrangente para anotação de documentos em aplicativos .NET. Seguindo as etapas descritas neste tutorial, você pode integrar perfeitamente a funcionalidade de anotação de documentos em seus projetos, melhorando a colaboração e a produtividade.
## Perguntas frequentes
### O GroupDocs.Annotation for .NET é compatível com todos os formatos de documentos?
GroupDocs.Annotation oferece suporte a uma ampla variedade de formatos de documentos, incluindo PDF, Word, Excel, PowerPoint e muito mais.
### As anotações podem ser personalizadas de acordo com requisitos específicos?
Sim, GroupDocs.Annotation oferece amplas opções de personalização para anotações, incluindo cores, formas e propriedades.
### GroupDocs.Annotation oferece suporte a recursos de anotação colaborativa?
Sim, GroupDocs.Annotation facilita a anotação colaborativa, permitindo que vários usuários anotem documentos simultaneamente.
### O suporte técnico está disponível para usuários do GroupDocs.Annotation?
 Sim, o GroupDocs fornece suporte técnico dedicado por meio de seu fórum. Visita[aqui](https://forum.groupdocs.com/c/annotation/10) para suporte.
### Posso experimentar GroupDocs.Annotation antes de comprar?
 Sim, você pode explorar GroupDocs.Annotation por meio de uma avaliação gratuita disponível[aqui](https://releases.groupdocs.com/).