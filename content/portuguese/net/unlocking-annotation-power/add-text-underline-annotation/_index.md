---
"description": "Aprenda a adicionar anotações de sublinhado de texto a documentos usando o GroupDocs.Annotation para .NET. Aprimore a colaboração e a comunicação sem esforço."
"linktitle": "Adicionar anotação de sublinhado de texto ao documento"
"second_title": "API .NET do GroupDocs.Annotation"
"title": "Adicionar anotação de sublinhado de texto ao documento"
"url": "/pt/net/unlocking-annotation-power/add-text-underline-annotation/"
type: docs
"weight": 27
---

# Adicionar anotação de sublinhado de texto ao documento

## Introdução
Neste tutorial, mostraremos o processo de adição de uma anotação de sublinhado de texto a um documento usando o GroupDocs.Annotation para .NET. Anotações de sublinhado de texto podem ser úteis para enfatizar partes específicas de um documento, como passagens importantes ou pontos-chave.
## Pré-requisitos
Antes de começar, certifique-se de ter os seguintes pré-requisitos instalados:
1. GroupDocs.Annotation para .NET: Baixe e instale o GroupDocs.Annotation para .NET em [aqui](https://releases.groupdocs.com/annotation/net/).
2. .NET Framework: certifique-se de ter o .NET Framework instalado no seu sistema.

## Importando namespaces
Primeiro, vamos importar os namespaces necessários para o nosso projeto:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Agora, vamos dividir o exemplo em várias etapas:
## Etapa 1: Definir o caminho de saída
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Nesta etapa, definimos o caminho de saída onde o documento anotado será salvo.
## Etapa 2: Inicializar o Annotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Aqui, inicializamos uma instância do `Annotator` classe fornecendo o caminho do documento de entrada.
## Etapa 3: Criar anotação sublinhada
```csharp
UnderlineAnnotation underline = new UnderlineAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is underline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    UnderlineColor = 1422623, // funciona apenas com documentos Word e PDF
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
Esta etapa envolve a criação de um `UnderlineAnnotation` objeto com várias propriedades, como cor da fonte, mensagem, opacidade, número da página, cor de fundo, cor do sublinhado, pontos e respostas.
## Etapa 4: Adicionar anotação ao documento
```csharp
annotator.Add(underline);
```
Aqui, adicionamos a anotação sublinhada ao documento.
## Etapa 5: Salvar documento anotado
```csharp
annotator.Save(outputPath);
```
Por fim, salvamos o documento anotado no caminho de saída especificado.

## Conclusão
Neste tutorial, aprendemos como adicionar uma anotação de sublinhado de texto a um documento usando o GroupDocs.Annotation para .NET. Esta poderosa biblioteca oferece diversas opções de anotação para aprimorar a colaboração e a comunicação em documentos.
## Perguntas frequentes
### Posso personalizar a aparência da anotação sublinhada?
Sim, você pode personalizar propriedades como cor, opacidade e posição de acordo com suas necessidades.
### O GroupDocs.Annotation é compatível com diferentes formatos de documentos?
Sim, o GroupDocs.Annotation suporta uma ampla variedade de formatos de documentos, incluindo Word e PDF.
### Posso adicionar várias anotações a um único documento?
Com certeza, o GroupDocs.Annotation permite que você adicione diversas anotações de diferentes tipos a um documento.
### Existe um teste gratuito disponível para o GroupDocs.Annotation?
Sim, você pode acessar a versão de teste gratuita em [aqui](https://releases.groupdocs.com/).
### Onde posso obter suporte para o GroupDocs.Annotation?
Você pode obter suporte no fórum da comunidade GroupDocs.Annotation [aqui](https://forum.groupdocs.com/c/annotation/10).