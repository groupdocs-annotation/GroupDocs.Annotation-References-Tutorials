---
title: Adicionar componente de caixa de seleção ao documento PDF
linktitle: Adicionar componente de caixa de seleção ao documento PDF
second_title: API GroupDocs.Annotation .NET
description: Aprenda como adicionar um componente Checkbox a documentos PDF usando Groupdocs.Annotation for .NET. Aprimore seus PDFs com elementos interativos.
weight: 11
url: /pt/net/document-components/add-checkbox-component-to-pdf/
---
## Introdução
Neste tutorial, orientaremos você no processo de adição de um componente Checkbox a um documento PDF usando Groupdocs.Annotation for .NET.
## Pré-requisitos
Antes de começarmos, certifique-se de ter o seguinte:
1.  Groupdocs.Annotation para .NET SDK: você pode baixá-lo em[aqui](https://releases.groupdocs.com/annotation/net/).
2. Ambiente de desenvolvimento: certifique-se de ter um ambiente de desenvolvimento .NET configurado.

## Importar namespaces
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```
Agora, vamos dividir o exemplo em várias etapas:
## Etapa 1: definir o caminho de saída
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Aqui definimos o caminho de saída onde o documento PDF modificado será salvo.
## Etapa 2: inicializar o anotador
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 Inicialize o`Annotator` objeto passando o caminho do documento PDF de entrada.
## Etapa 3: Criar componente de caixa de seleção
```csharp
CheckBoxComponent checkBox = new CheckBoxComponent
{
    Checked = true,
    Box = new Rectangle(100, 100, 100, 100),
    PenColor = 65535,
    Style = BoxStyle.Star,
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
 Criar uma`CheckBoxComponent` objeto e personalizar suas propriedades como`Checked`, `Box` dimensões,`PenColor`, `Style`adicione algumas respostas.
## Etapa 4: adicionar componente de caixa de seleção
```csharp
annotator.Add(checkBox);
```
Adicione o componente de caixa de seleção criado ao documento PDF.
## Etapa 5: Salvar documento
```csharp
annotator.Save("result.pdf");
```
Salve o documento PDF modificado com o componente de caixa de seleção.
## Etapa 6: Exibir caminho de saída
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Exiba o caminho onde o documento PDF modificado foi salvo.

## Conclusão
Neste tutorial, aprendemos como adicionar um componente Checkbox a um documento PDF usando Groupdocs.Annotation for .NET. Com esse conhecimento, você pode aprimorar seus documentos PDF com elementos interativos.
## Perguntas frequentes
### Posso personalizar a aparência da caixa de seleção?
Sim, você pode personalizar várias propriedades, como cor, estilo e tamanho, de acordo com suas necessidades.
### O Groupdocs.Annotation for .NET é adequado para uso comercial?
Sim, Groupdocs.Annotation for .NET oferece licenças comerciais para empresas.
### Posso experimentar o Groupdocs.Annotation for .NET antes de comprar?
 Sim, você pode aproveitar um teste gratuito em[aqui](https://releases.groupdocs.com/).
### Onde posso encontrar suporte para Groupdocs.Annotation for .NET?
 Você pode encontrar suporte e recursos no site[Fórum de documentos de grupo](https://forum.groupdocs.com/c/annotation/10).
### Preciso de uma licença temporária para fins de teste?
 Você pode obter uma licença temporária para testes em[aqui](https://purchase.groupdocs.com/temporary-license/).