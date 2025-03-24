---
title: Adicionar anotação de link ao documento
linktitle: Adicionar anotação de link ao documento
second_title: API GroupDocs.Annotation .NET
description: Aprenda como adicionar anotações de link a documentos usando Groupdocs.Annotation for .NET. Melhore a colaboração e a interatividade sem esforço.
weight: 16
url: /pt/net/unlocking-annotation-power/add-link-annotation/
---
## Introdução
Groupdocs.Annotation for .NET é uma biblioteca poderosa que permite aos desenvolvedores integrar funcionalidades de anotação abrangentes em seus aplicativos .NET sem esforço. Um dos principais recursos que oferece é a capacidade de adicionar anotações de links a documentos, melhorando a colaboração e a interatividade.
## Pré-requisitos
Antes de mergulhar no processo de adição de anotações de link, certifique-se de ter os seguintes pré-requisitos:
- Compreensão básica da linguagem de programação C#.
- Biblioteca Groupdocs.Annotation para .NET instalada.
- Acesso a um documento que você deseja anotar.

## Importar namespaces
Em primeiro lugar, você precisa importar os namespaces necessários para utilizar as funcionalidades do Groupdocs.Annotation for .NET. Isso permite que seu aplicativo acesse as classes e métodos necessários para anotar documentos.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Etapa 1: definir caminho de saída
Defina o caminho onde deseja salvar o documento anotado.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Etapa 2: inicializar o anotador
 Crie uma instância do`Annotator` classe, fornecendo o caminho do documento que você deseja anotar.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // O código da anotação irá aqui
}
```
## Etapa 3: criar anotação de link
 Defina um`LinkAnnotation` objeto e especifique suas propriedades, como mensagem, opacidade, número da página, cor de fundo, pontos, respostas e URL.
```csharp
LinkAnnotation link = new LinkAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is link annotation",
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
    },
    Url = "https://www.google.com"
};
```
## Etapa 4: adicionar anotação
 Adicione a anotação do link criado ao documento usando o`Add` método da instância do anotador.
```csharp
annotator.Add(link);
```
## Etapa 5: Salvar documento
Salve o documento anotado no caminho de saída especificado.
```csharp
annotator.Save(outputPath);
```
## Etapa 6: exibir mensagem de sucesso
Informe o usuário sobre o salvamento bem-sucedido do documento anotado.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusão
Concluindo, seguindo as etapas acima, você pode adicionar facilmente anotações de link a documentos usando Groupdocs.Annotation for .NET. Isso aprimora a colaboração de documentos e fornece aos usuários recursos interativos.
## Perguntas frequentes
### O Groupdocs.Annotation for .NET é compatível com todos os tipos de documentos?
Groupdocs.Annotation for .NET oferece suporte a uma ampla variedade de formatos de documentos, incluindo PDF, Word, Excel e muito mais.
### Posso personalizar a aparência das anotações?
Sim, você pode personalizar várias propriedades de anotações, como cor, opacidade e tamanho, para atender às suas necessidades.
### O Groupdocs.Annotation for .NET oferece recursos de colaboração em tempo real?
Sim, o Groupdocs.Annotation for .NET fornece recursos de colaboração em tempo real, permitindo que vários usuários façam anotações em documentos simultaneamente.
### O suporte técnico está disponível para produtos Groupdocs?
 Sim, o suporte técnico para produtos Groupdocs está disponível através do fórum e suporte[aqui](https://forum.groupdocs.com/c/annotation/10).
### Posso experimentar o Groupdocs.Annotation for .NET antes de comprar?
Sim, você pode aproveitar uma avaliação gratuita do Groupdocs.Annotation for .NET para explorar seus recursos antes de fazer uma compra[aqui](https://purchase.groupdocs.com/temporary-license/).