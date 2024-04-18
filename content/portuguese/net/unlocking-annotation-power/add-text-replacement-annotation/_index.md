---
title: Adicionar anotação de substituição de texto ao documento
linktitle: Adicionar anotação de substituição de texto ao documento
second_title: API GroupDocs.Annotation .NET
description: Aprenda como adicionar anotações de substituição de texto aos seus documentos .NET sem esforço usando GroupDocs.Annotation for .NET. Aprimore seus recursos de manipulação de documentos.
type: docs
weight: 24
url: /pt/net/unlocking-annotation-power/add-text-replacement-annotation/
---
## Introdução
Neste tutorial, orientaremos você no processo de adição de uma anotação de substituição de texto aos seus documentos usando GroupDocs.Annotation for .NET. Esta poderosa biblioteca permite aos desenvolvedores manipular e anotar vários tipos de documentos de forma programática. Ao final deste tutorial, você estará equipado com o conhecimento necessário para integrar perfeitamente anotações de substituição de texto em seus aplicativos .NET.
## Pré-requisitos
Antes de começarmos, certifique-se de ter os seguintes pré-requisitos instalados:
### 1. .NET Framework instalado
Certifique-se de ter o .NET Framework instalado em sua máquina de desenvolvimento. Você pode baixá-lo no site da Microsoft.
### 2. GroupDocs.Annotation para biblioteca .NET
 Baixe e instale a biblioteca GroupDocs.Annotation for .NET do[local na rede Internet](https://releases.groupdocs.com/annotation/net/). Esta biblioteca fornece as ferramentas e funcionalidades necessárias para trabalhar com anotações em diversos formatos de documentos.
### 3. Configuração do ambiente de desenvolvimento
Configure seu ambiente de desenvolvimento preferido, como Visual Studio, para criar e executar aplicativos .NET.

## Importar namespaces
Antes de mergulhar na parte de codificação, vamos importar os namespaces necessários para trabalhar com GroupDocs.Annotation for .NET:
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
using Point = GroupDocs.Annotation.Models.Point;
```
## Etapa 1: definir o caminho de saída
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Aqui definimos o caminho de saída onde o documento anotado será salvo.
## Etapa 2: inicializar o anotador
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // O código da anotação será colocado aqui
}
```
Inicializamos o objeto Annotator especificando o documento de entrada ("input.pdf") dentro de um bloco using para garantir o descarte adequado de recursos.
## Etapa 3: criar anotação de substituição
```csharp
ReplacementAnnotation replacement = new ReplacementAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = Color.Blue.ToArgb(),
    Message = "This is replacement annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = Color.Red.ToArgb(),
    Points = new List<Point>
    {
        new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
    },
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
    },
    TextToReplace = "replaced text"
};
```
Aqui, criamos um objeto ReplacementAnnotation com várias propriedades como data de criação, cor da fonte, mensagem, opacidade, número da página, cor de fundo, pontos (coordenadas), respostas (comentários) e o texto a ser substituído.
## Etapa 4: adicionar anotação
```csharp
annotator.Add(replacement);
```
Adicionamos a anotação de substituição criada ao anotador.
## Etapa 5: Salvar documento
```csharp
annotator.Save(outputPath);
```
Finalmente, salvamos o documento anotado no caminho de saída especificado.
## Etapa 6: exibir mensagem de sucesso
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Uma mensagem de sucesso é exibida indicando que o documento foi salvo com sucesso.

## Conclusão
Neste tutorial, abordamos o processo de adição de anotações de substituição de texto a documentos usando GroupDocs.Annotation for .NET. Seguindo o guia passo a passo e compreendendo os pré-requisitos, você pode integrar facilmente essa funcionalidade aos seus aplicativos .NET.
## Perguntas frequentes
### Posso anotar documentos de diferentes formatos usando GroupDocs.Annotation for .NET?
Sim, GroupDocs.Annotation for .NET oferece suporte à anotação de vários formatos de documentos, como PDF, DOCX, PPTX, XLSX e muito mais.
### O GroupDocs.Annotation for .NET é adequado para aplicativos de desktop e web?
Sim, o GroupDocs.Annotation for .NET pode ser usado em aplicativos desktop e web, proporcionando flexibilidade aos desenvolvedores.
### Posso personalizar a aparência das anotações adicionadas usando GroupDocs.Annotation for .NET?
Com certeza, você pode personalizar a aparência das anotações modificando propriedades como cor, opacidade, fonte, etc.
### O GroupDocs.Annotation for .NET oferece suporte para recursos de anotação colaborativa?
Sim, o GroupDocs.Annotation for .NET fornece recursos para anotações colaborativas, permitindo que vários usuários façam anotações em documentos simultaneamente.
### Existe uma avaliação gratuita disponível para GroupDocs.Annotation for .NET?
Sim, você pode aproveitar uma avaliação gratuita do GroupDocs.Annotation for .NET no site[local na rede Internet](https://releases.groupdocs.com/).