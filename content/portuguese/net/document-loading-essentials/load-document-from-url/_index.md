---
title: Carregar documento do URL
linktitle: Carregar documento do URL
second_title: API GroupDocs.Annotation .NET
description: Aprenda como anotar documentos PDF programaticamente usando GroupDocs.Annotation for .NET. Tutorial passo a passo com exemplos de código.
weight: 15
url: /pt/net/document-loading-essentials/load-document-from-url/
---

# Carregar documento do URL

## Introdução
GroupDocs.Annotation for .NET é uma biblioteca rica em recursos que permite aos desenvolvedores adicionar recursos de anotação a seus aplicativos .NET sem esforço. Com GroupDocs.Annotation, você pode anotar documentos PDF de forma programática, permitindo aos usuários destacar texto, adicionar comentários, desenhar formas e muito mais. Este tutorial orientará você nas etapas de carregamento de um documento de uma URL, adição de anotações e salvamento do documento anotado usando GroupDocs.Annotation for .NET.
## Pré-requisitos
Antes de começar, certifique-se de ter os seguintes pré-requisitos:
1. Visual Studio: certifique-se de ter o Visual Studio instalado em sua máquina de desenvolvimento.
2.  GroupDocs.Annotation for .NET: Baixe e instale GroupDocs.Annotation for .NET a partir do[local na rede Internet](https://releases.groupdocs.com/annotation/net/).
3. Conhecimento básico de C#: Familiarize-se com a linguagem de programação C#.
4. Conexão com a Internet: você precisará de uma conexão com a Internet para acessar recursos externos e baixar arquivos de amostra.

## Importar namespaces
Primeiro, vamos importar os namespaces necessários em seu projeto C#:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```
## Etapa 1: carregar o documento do URL
Para anotar um documento PDF a partir de um URL, siga estas etapas:
### Etapa 1.1: Definir caminho de saída
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### Etapa 1.2: Especifique o URL
```csharp
string url = "https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET/blob/master/Examples/Resources/SampleFiles/input.pdf?raw=true";
```
### Passo 1.3: Carregar Documento
```csharp
using (Annotator annotator = new Annotator(GetRemoteFile(url)))
{
    // Adicione anotações aqui
    annotator.Save(outputPath);
}
```
## Etapa 2: adicionar anotações
Agora, vamos adicionar anotações ao documento carregado. Neste exemplo, adicionaremos uma anotação de área:
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## Etapa 3: Salvar documento anotado
Finalmente, salve o documento anotado no caminho de saída especificado:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusão
Neste tutorial, aprendemos como fazer anotações em documentos PDF usando GroupDocs.Annotation for .NET. Seguindo o guia passo a passo, você pode integrar perfeitamente a funcionalidade de anotação em seus aplicativos .NET, capacitando os usuários a colaborar de forma eficaz em arquivos PDF.

## Perguntas frequentes
### O GroupDocs.Annotation for .NET é compatível com todas as estruturas .NET?
Sim, GroupDocs.Annotation for .NET é compatível com várias estruturas .NET, incluindo .NET Framework, .NET Core e .NET Standard.
### Posso personalizar a aparência das anotações?
Absolutamente! GroupDocs.Annotation for .NET oferece amplas opções de personalização, permitindo modificar a aparência e o comportamento das anotações de acordo com seus requisitos.
### Existe uma avaliação gratuita disponível para GroupDocs.Annotation for .NET?
 Sim, você pode baixar uma versão de avaliação gratuita do GroupDocs.Annotation for .NET no site[local na rede Internet](https://releases.groupdocs.com/).
### Como posso obter suporte técnico para GroupDocs.Annotation for .NET?
 Se você encontrar algum problema técnico ou tiver dúvidas sobre GroupDocs.Annotation for .NET, você pode procurar assistência do[Fórum de suporte](https://forum.groupdocs.com/c/annotation/10).
### Onde posso adquirir uma licença do GroupDocs.Annotation for .NET?
 Você pode adquirir uma licença do GroupDocs.Annotation for .NET no site[página de compra](https://purchase.groupdocs.com/buy).