---
"description": "Explore o poder do GroupDocs.Annotation para .NET e adicione facilmente recursos de anotação de documentos aos seus aplicativos."
"linktitle": "Adicionar anotação de fragmento de texto de pesquisa ao documento"
"second_title": "API .NET do GroupDocs.Annotation"
"title": "Adicionar anotação de fragmento de texto de pesquisa ao documento"
"url": "/pt/net/unlocking-annotation-power/add-search-text-fragment-annotation/"
type: docs
"weight": 20
---

# Adicionar anotação de fragmento de texto de pesquisa ao documento

## Introdução
No âmbito do desenvolvimento .NET, o GroupDocs.Annotation se destaca como uma ferramenta poderosa para anotar documentos de forma integrada. Seja você um desenvolvedor experiente ou esteja apenas começando no mundo .NET, este tutorial abrangente o guiará pelos fundamentos do uso do GroupDocs.Annotation para .NET, desde a importação de namespaces até o domínio das complexidades da adição de anotações de fragmentos de texto de pesquisa aos seus documentos.
## Introdução
O GroupDocs.Annotation para .NET permite que os desenvolvedores incorporem recursos de anotação de documentos em seus aplicativos sem esforço. Com sua API intuitiva e recursos robustos, os desenvolvedores podem anotar vários formatos de documentos, incluindo PDFs, documentos do Microsoft Office, imagens e muito mais.
## Pré-requisitos
Antes de mergulhar no GroupDocs.Annotation para .NET, certifique-se de ter os seguintes pré-requisitos em vigor:

## Importar namespaces
Primeiro, importe os namespaces necessários para acessar as classes e métodos GroupDocs.Annotation no seu projeto .NET:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Etapa 1: Definir o caminho de saída
Comece definindo o caminho de saída onde o documento anotado será salvo:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Etapa 2: Inicializar o Annotator
Em seguida, inicialize uma instância do `Annotator` classe fornecendo o caminho para o documento que você deseja anotar:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Etapa 3: Criar anotação de fragmento de texto de pesquisa
Criar um `SearchTextFragment` objeto com as propriedades desejadas, como texto a ser pesquisado, tamanho da fonte, família da fonte, cor da fonte e cor de fundo:
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
## Etapa 4: Adicionar anotação
Adicione a anotação do fragmento de texto de pesquisa criado ao documento usando o `Add` método do anotador:
```csharp
annotator.Add(searchText);
```
## Etapa 5: Salvar documento anotado
Salve o documento anotado no caminho de saída especificado:
```csharp
annotator.Save(outputPath);
```
## Etapa 6: Exibir mensagem de sucesso
Informe ao usuário que o documento foi salvo com sucesso:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusão
Concluindo, o GroupDocs.Annotation para .NET simplifica o processo de adição de anotações a documentos, aprimorando os processos de colaboração e revisão de documentos. Seguindo os passos descritos neste guia, você pode integrar perfeitamente os recursos de anotação de documentos aos seus aplicativos .NET.
## Perguntas frequentes
### O GroupDocs.Annotation é compatível com todos os formatos de documento?
Sim, o GroupDocs.Annotation suporta uma ampla variedade de formatos de documentos, incluindo PDFs, documentos do Microsoft Office, imagens e muito mais.
### Posso personalizar a aparência das anotações?
Com certeza! O GroupDocs.Annotation oferece amplas opções de personalização para anotações, permitindo que você ajuste propriedades como tamanho da fonte, cor e estilo.
### Existe um teste gratuito disponível para o GroupDocs.Annotation?
Sim, você pode acessar uma avaliação gratuita do GroupDocs.Annotation para explorar seus recursos e capacidades antes de fazer uma compra [aqui](https://releases.groupdocs.com/)..
### Onde posso encontrar suporte para o GroupDocs.Annotation?
Para obter suporte e assistência com o GroupDocs.Annotation, você pode visitar o GroupDocs [fórum](https://forum.groupdocs.com/c/annotation/10) dedicado a consultas e discussões relacionadas a anotações.
### Como obtenho uma licença temporária para o GroupDocs.Annotation?
Você pode adquirir uma licença temporária para GroupDocs.Annotation através do GroupDocs [site](https://purchase.groupdocs.com/temporary-license/), permitindo que você avalie o produto completamente.