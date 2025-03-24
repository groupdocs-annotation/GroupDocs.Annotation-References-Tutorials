---
title: Adicionar anotação riscada de texto ao documento
linktitle: Adicionar anotação riscada de texto ao documento
second_title: API GroupDocs.Annotation .NET
description: Aprenda como adicionar anotações de texto riscado a documentos usando GroupDocs.Annotation for .NET. Aprimore os processos de colaboração e revisão de documentos com eficiência.
weight: 26
url: /pt/net/unlocking-annotation-power/add-text-strikeout-annotation/
---

# Adicionar anotação riscada de texto ao documento

## Introdução
Neste tutorial, exploraremos como adicionar uma anotação de texto riscado a um documento usando GroupDocs.Annotation for .NET. Esta biblioteca fornece ferramentas poderosas para anotar vários tipos de documentos, melhorando a colaboração e os processos de revisão de documentos.
## Pré-requisitos
Antes de começarmos, certifique-se de ter os seguintes pré-requisitos:
1.  GroupDocs.Annotation para .NET: Instale a biblioteca. Você pode baixá-lo em[aqui](https://releases.groupdocs.com/annotation/net/).
2. Ambiente de desenvolvimento: Configure um ambiente de desenvolvimento adequado para o desenvolvimento .NET.
3. Documento: tenha um documento pronto para anotar, como um arquivo PDF.

## Importando Namespaces
Primeiro, importe os namespaces necessários para acessar as funcionalidades do GroupDocs.Annotation:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Agora, vamos dividir o processo de adição de uma anotação riscada de texto em várias etapas:
## Etapa 1: definir o caminho de saída
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Aqui definimos o caminho de saída onde o documento anotado será salvo.
## Etapa 2: inicializar o anotador
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Inicialize o objeto Annotator fornecendo o caminho para o documento de entrada (arquivo PDF neste caso).
## Etapa 3: criar anotação riscada
```csharp
StrikeoutAnnotation strikeout = new StrikeoutAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is strikeout annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
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
    }
};
```
Crie um objeto StrikeoutAnnotation com propriedades desejadas, como mensagem, opacidade, número de página, cor de fundo, pontos (coordenadas) e respostas.
## Etapa 4: adicionar anotação
```csharp
annotator.Add(strikeout);
```
Adicione a anotação riscada criada ao documento.
## Etapa 5: Salvar documento
```csharp
annotator.Save(outputPath);
```
Salve o documento anotado no caminho de saída especificado.

## Conclusão
Neste tutorial, aprendemos como adicionar uma anotação de texto riscado a um documento usando GroupDocs.Annotation for .NET. Esta poderosa biblioteca permite anotações eficientes em documentos, aprimorando os processos de colaboração e revisão de documentos.
## Perguntas frequentes
### O GroupDocs.Annotation é compatível com vários formatos de documentos?
Sim, GroupDocs.Annotation oferece suporte a uma ampla variedade de formatos de documentos, incluindo PDF, Word, Excel, PowerPoint e muito mais.
### Posso personalizar a aparência das anotações?
Com certeza, você pode personalizar as propriedades da anotação, como cor, opacidade, tamanho da fonte e muito mais, de acordo com suas necessidades.
### O GroupDocs.Annotation fornece recursos de colaboração?
Sim, GroupDocs.Annotation facilita a colaboração permitindo que os usuários adicionem comentários, respostas e anotações aos documentos.
### Existe um teste gratuito disponível?
 Sim, você pode aproveitar um teste gratuito em[aqui](https://releases.groupdocs.com/).
### Onde posso obter suporte para GroupDocs.Annotation?
 Você pode obter suporte do[Fórum GroupDocs.Annotation](https://forum.groupdocs.com/c/annotation/10).