---
title: Adicionar anotação de fragmento de texto de pesquisa ao documento
linktitle: Adicionar anotação de fragmento de texto de pesquisa ao documento
second_title: API GroupDocs.Annotation .NET
description: Explore o poder do GroupDocs.Annotation for .NET e adicione facilmente recursos de anotação de documentos aos seus aplicativos.
weight: 20
url: /pt/net/unlocking-annotation-power/add-search-text-fragment-annotation/
---

# Adicionar anotação de fragmento de texto de pesquisa ao documento

## Introdução
No domínio do desenvolvimento .NET, GroupDocs.Annotation se destaca como uma ferramenta poderosa para anotar documentos de forma integrada. Quer você seja um desenvolvedor experiente ou esteja apenas entrando no mundo do .NET, este tutorial abrangente irá guiá-lo pelos fundamentos do uso do GroupDocs.Annotation for .NET, desde a importação de namespaces até o domínio das complexidades da adição de anotações de fragmentos de texto de pesquisa ao seu documentos.
## Introdução
GroupDocs.Annotation for .NET capacita os desenvolvedores a incorporar recursos de anotação de documentos em seus aplicativos sem esforço. Com sua API intuitiva e recursos robustos, os desenvolvedores podem fazer anotações em vários formatos de documentos, incluindo PDFs, documentos do Microsoft Office, imagens e muito mais.
## Pré-requisitos
Antes de mergulhar no GroupDocs.Annotation for .NET, certifique-se de ter os seguintes pré-requisitos em vigor:

## Importar namespaces
Primeiramente, importe os namespaces necessários para acessar classes e métodos GroupDocs.Annotation em seu projeto .NET:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Etapa 1: definir o caminho de saída
Comece definindo o caminho de saída onde o documento anotado será salvo:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Etapa 2: inicializar o anotador
 Em seguida, inicialize uma instância do`Annotator` class fornecendo o caminho para o documento que você deseja anotar:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Etapa 3: criar anotação de fragmento de texto de pesquisa
 Criar uma`SearchTextFragment` objeto com as propriedades desejadas, como texto a ser pesquisado, tamanho da fonte, família da fonte, cor da fonte e cor de fundo:
```csharp
SearchTextFragment searchText = new SearchTextFragment()
{
    Text = "Welcome to GroupDocs",
    FontSize = 10,
    FontFamily = "Calibri",
    FontColor = 65535,
    BackgroundColor = 16761035,
};
```
## Etapa 4: adicionar anotação
 Adicione a anotação do fragmento de texto de pesquisa criado ao documento usando o`Add` método do anotador:
```csharp
annotator.Add(searchText);
```
## Etapa 5: Salvar documento anotado
Salve o documento anotado no caminho de saída especificado:
```csharp
annotator.Save(outputPath);
```
## Etapa 6: exibir mensagem de sucesso
Informe ao usuário que o documento foi salvo com sucesso:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusão
Concluindo, GroupDocs.Annotation for .NET simplifica o processo de adição de anotações a documentos, aprimorando os processos de colaboração e revisão de documentos. Seguindo as etapas descritas neste guia, você pode integrar perfeitamente recursos de anotação de documentos em seus aplicativos .NET.
## Perguntas frequentes
### O GroupDocs.Annotation é compatível com todos os formatos de documento?
Sim, GroupDocs.Annotation oferece suporte a uma ampla variedade de formatos de documentos, incluindo PDFs, documentos do Microsoft Office, imagens e muito mais.
### Posso personalizar a aparência das anotações?
Absolutamente! GroupDocs.Annotation oferece amplas opções de personalização para anotações, permitindo ajustar propriedades como tamanho da fonte, cor e estilo.
### Existe uma avaliação gratuita disponível para GroupDocs.Annotation?
 Sim, você pode acessar uma avaliação gratuita do GroupDocs.Annotation para explorar seus recursos e capacidades antes de fazer uma compra[aqui](https://releases.groupdocs.com/)..
### Onde posso encontrar suporte para GroupDocs.Annotation?
 Para suporte e assistência com GroupDocs.Annotation, você pode visitar o GroupDocs[fórum](https://forum.groupdocs.com/c/annotation/10) dedicado a consultas e discussões relacionadas a anotações.
### Como obtenho uma licença temporária para GroupDocs.Annotation?
 Você pode adquirir uma licença temporária para GroupDocs.Annotation através do GroupDocs[local na rede Internet](https://purchase.groupdocs.com/temporary-license/), permitindo que você avalie o produto completamente.