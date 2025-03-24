---
title: Adicionar anotação de polilinha ao documento
linktitle: Adicionar anotação de polilinha ao documento
second_title: API GroupDocs.Annotation .NET
description: Aprenda como adicionar anotações de polilinha a documentos usando GroupDocs.Annotation for .NET. Aprimore os processos de colaboração e revisão de documentos sem esforço.
weight: 18
url: /pt/net/unlocking-annotation-power/add-polyline-annotation/
---

# Adicionar anotação de polilinha ao documento

## Introdução
GroupDocs.Annotation for .NET é uma ferramenta poderosa que permite aos desenvolvedores anotar documentos PDF e Microsoft Office de forma programática. Entre seus recursos está a capacidade de adicionar anotações polilinhas aos documentos, aprimorando os processos de colaboração e revisão de documentos.
## Pré-requisitos
Antes de prosseguir com este tutorial, certifique-se de ter o seguinte:
- Visual Studio instalado em seu sistema.
- Conhecimento básico da linguagem de programação C#.
-  Biblioteca GroupDocs.Annotation para .NET instalada. Você pode baixá-lo em[aqui](https://releases.groupdocs.com/annotation/net/).

## Importar namespaces
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Etapa 1: definir o caminho de saída
Primeiro, defina o caminho de saída onde o documento anotado será salvo.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Etapa 2: inicializar o anotador
Inicialize o anotador fornecendo o nome do documento de entrada.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Etapa 3: Criar objeto de anotação de polilinha
Crie um objeto de anotação de polilinha e defina suas propriedades como posição, mensagem, opacidade, cor da caneta, estilo da caneta e largura da caneta.
```csharp
PolylineAnnotation polyline = new PolylineAnnotation
{
    Box = new Rectangle(250, 35, 102, 12),
    CreatedOn = DateTime.Now,
    Message = "This is polyline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    PenColor = 65535,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
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
    SvgPath = "M250.8280751173709,48.209295774647885l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793l1.3973708920187793,-0.6986854460093896l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0l2.096056338028169,-1.3973708920187793l3.493427230046948,-1.3973708920187793l0.6986854460093896,-0.6986854460093896l1.3973708920187793,-1.3973708920187793l0.6986854460093896,0l1.3973708920187793,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0l0,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l0,-0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l2.096056338028169,-0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l1.3973708920187793,0l1.3973708920187793,0l2.096056338028169,0l5.589483568075117,0l1.3973708920187793,0l2.096056338028169,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l1.3973708920187793,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0l2.096056338028169,1.3973708920187793l0.6986854460093896,0l0.6986854460093896,0l0,0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0.6986854460093896l0,0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0.6986854460093896l1.3973708920187793,0.6986854460093896l3.493427230046948,0.6986854460093896l1.3973708920187793,0.6986854460093896l2.096056338028169,0.6986854460093896l1.3973708920187793,0.6986854460093896l1.3973708920187793,0l1.3973708920187793,0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l2.7947417840375586,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.698685
4460093896,0l0.6986854460093896,0l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0"
};
```
## Etapa 4: adicionar anotação de polilinha
Adicione a anotação de polilinha ao documento usando o objeto anotador.
```csharp
annotator.Add(polyline);
```
## Etapa 5: Salvar documento
Salve o documento anotado no caminho de saída especificado.
```csharp
annotator.Save(outputPath);
```
## Etapa 6: exibir mensagem de sucesso
Exiba uma mensagem confirmando o salvamento bem-sucedido do documento.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusão
Neste tutorial, aprendemos como adicionar uma anotação de polilinha a um documento usando GroupDocs.Annotation for .NET. Esse recurso aprimora os processos de colaboração e revisão de documentos, facilitando a comunicação eficaz de comentários e sugestões pelos usuários.
## Perguntas frequentes
### O GroupDocs.Annotation for .NET é compatível com todos os formatos de documentos?
GroupDocs.Annotation for .NET oferece suporte a formatos de documentos populares, como PDF e formatos do Microsoft Office, incluindo Word, Excel e PowerPoint.
### Posso personalizar a aparência das anotações?
Sim, você pode personalizar várias propriedades de anotações, como cor, opacidade, estilo e largura, para atender às suas necessidades.
### O GroupDocs.Annotation for .NET oferece uma avaliação gratuita?
 Sim, você pode aproveitar uma avaliação gratuita do GroupDocs.Annotation for .NET visitando[esse link](https://releases.groupdocs.com/).
### Onde posso encontrar documentação para GroupDocs.Annotation for .NET?
 Você pode encontrar a documentação do GroupDocs.Annotation for .NET[aqui](https://tutorials.groupdocs.com/annotation/net/).
### Como posso obter suporte para quaisquer problemas ou dúvidas relacionadas ao GroupDocs.Annotation for .NET?
 Você pode obter suporte visitando o fórum GroupDocs.Annotation[aqui](https://forum.groupdocs.com/c/annotation/10).