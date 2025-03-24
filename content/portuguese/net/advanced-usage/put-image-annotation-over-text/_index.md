---
title: Colocar anotação de imagem sobre texto
linktitle: Colocar anotação de imagem sobre texto
second_title: API GroupDocs.Annotation .NET
description: Aprenda como adicionar anotações de imagem sobre texto no .NET usando GroupDocs.Annotation para gerenciamento e colaboração eficientes de documentos.
weight: 21
url: /pt/net/advanced-usage/put-image-annotation-over-text/
---

# Colocar anotação de imagem sobre texto

## Introdução
No mundo do desenvolvimento .NET, GroupDocs.Annotation oferece uma solução poderosa para adicionar anotações a documentos, tornando a colaboração e o gerenciamento de documentos mais eficientes. Um requisito comum é colocar anotações de imagem sobre texto, o que pode ser realizado perfeitamente usando GroupDocs.Annotation for .NET.
## Pré-requisitos
Antes de mergulhar no processo de colocar anotações de imagem sobre texto usando GroupDocs.Annotation for .NET, certifique-se de ter o seguinte:
1.  GroupDocs.Annotation for .NET Library: Baixe e instale a biblioteca em[aqui](https://releases.groupdocs.com/annotation/net/).
2. Ambiente de Desenvolvimento: Configure um ambiente de desenvolvimento adequado, como Visual Studio ou qualquer outro IDE .NET.
3. Arquivos de documentos e imagens: Prepare o arquivo do documento (PDF, DOCX, etc.) e o arquivo de imagem que deseja usar para anotações.
4. Compreensão básica de C#: É necessária familiaridade com a linguagem de programação C# para implementar os trechos de código fornecidos neste tutorial.

## Importar namespaces
Antes de prosseguir com o processo de anotação, certifique-se de importar os namespaces necessários em seu projeto C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Etapa 1: definir o caminho de saída
Primeiro, defina o caminho de saída onde o documento anotado será salvo:
```csharp
string outputPath = Path.Combine("Your Document Directory", "annotated_document.pdf");
```
## Etapa 2: inicializar o anotador
 Inicialize o`Annotator` objeto fornecendo o caminho do documento de entrada:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // O código da anotação irá aqui
}
```
## Etapa 3: criar anotação de imagem
 Criar um`ImageAnnotation` objeto com as propriedades desejadas, como dimensões da caixa, opacidade, número da página, caminho da imagem e índice z:
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png",
    ZIndex = 3
};
```
## Etapa 4: adicionar anotação
 Adicione a anotação da imagem ao documento usando o`Add` método do`Annotator` objeto:
```csharp
annotator.Add(image);
```
## Etapa 5: Salvar documento anotado
Salve o documento anotado no caminho de saída especificado:
```csharp
annotator.Save(outputPath);
```
## Etapa 6: exibir mensagem de sucesso
Exiba uma mensagem de sucesso com o caminho para o documento anotado:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusão
Concluindo, adicionar anotações de imagem sobre texto em aplicativos .NET usando GroupDocs.Annotation é um processo simples. Seguindo o guia passo a passo fornecido neste tutorial, você pode anotar documentos com eficiência e aprimorar os recursos de colaboração e gerenciamento de documentos em seus projetos .NET.
## Perguntas frequentes
### Posso anotar documentos que não sejam PDFs?
Sim, GroupDocs.Annotation oferece suporte a vários formatos de documento, como DOCX, XLSX, PPTX e muito mais.
### Existe uma avaliação gratuita disponível para GroupDocs.Annotation?
 Sim, você pode baixar uma versão de avaliação gratuita em[aqui](https://releases.groupdocs.com/).
### Como posso obter suporte para GroupDocs.Annotation?
 Você pode obter suporte no fórum da comunidade GroupDocs.Annotation[aqui](https://forum.groupdocs.com/c/annotation/10).
### Preciso de uma licença temporária para fins de teste?
 Sim, você pode obter uma licença temporária de[aqui](https://purchase.groupdocs.com/temporary-license/) para fins de teste.
### Posso personalizar a aparência das anotações?
Sim, GroupDocs.Annotation oferece várias opções para personalizar a aparência das anotações, como cor, opacidade, tamanho da fonte, etc.