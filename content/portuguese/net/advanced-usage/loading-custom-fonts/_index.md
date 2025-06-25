---
"description": "Aprenda a carregar fontes personalizadas no GroupDocs.Annotation para .NET sem problemas para aprimorar as anotações em documentos. Siga nosso passo a passo para uma integração fácil."
"linktitle": "Carregando fontes personalizadas"
"second_title": "API .NET do GroupDocs.Annotation"
"title": "Carregando fontes personalizadas"
"url": "/pt/net/advanced-usage/loading-custom-fonts/"
"weight": 20
---

# Carregando fontes personalizadas

## Introdução
GroupDocs.Annotation para .NET é uma biblioteca poderosa que permite aos desenvolvedores adicionar recursos de anotação aos seus aplicativos .NET sem esforço. Uma das principais funcionalidades que oferece é a capacidade de carregar fontes personalizadas, permitindo maior personalização e flexibilidade na anotação de documentos.
## Pré-requisitos
Antes de prosseguir com o tutorial, certifique-se de ter os seguintes pré-requisitos:
1. GroupDocs.Annotation para biblioteca .NET: Baixe e instale a biblioteca em [aqui](https://releases.groupdocs.com/annotation/net/).
2. Ambiente de desenvolvimento .NET: certifique-se de ter um ambiente de trabalho configurado para o desenvolvimento .NET.
3. Acesso a fontes personalizadas: prepare as fontes personalizadas que você deseja carregar no seu aplicativo.

## Importar namespaces
No seu projeto .NET, importe os namespaces necessários para utilizar GroupDocs.Annotation:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Options;
```
## Etapa 1: Instanciar o objeto Annotator
Crie uma instância do `Annotator` classe fornecendo o caminho para o documento PDF de entrada junto com os diretórios de fontes personalizadas:
```csharp
using (Annotator annotator = new Annotator("input.pdf", new LoadOptions { FontDirectories = new List<string> { Constants.GetFontDirectory() } }))
{
    // Seu código para operações futuras irá aqui
}
```
## Etapa 2: Configurar opções de visualização
Defina as opções de pré-visualização para especificar como as pré-visualizações do documento serão geradas. Você pode definir opções como formato de pré-visualização, números de página, etc.:
```csharp
PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
{
    var pagePath = Path.Combine("Your Document Directory", $"result_with_font_{pageNumber}.png");
    return File.Create(pagePath);
});
previewOptions.PreviewFormat = PreviewFormats.PNG;
previewOptions.PageNumbers = new int[] { 1, 2, 3, 4 };
```
## Etapa 3: gerar visualizações de documentos
Utilize o `GeneratePreview` método do `Document` propriedade para gerar pré-visualizações com fontes personalizadas:
```csharp
annotator.Document.GeneratePreview(previewOptions);
```
## Etapa 4: Exibir caminho de saída
Por fim, exiba uma mensagem indicando a geração bem-sucedida de visualizações de documentos, juntamente com o caminho do diretório de saída:
```csharp
Console.WriteLine($"\nDocument previews generated successfully.\nCheck output in {"Your Document Directory"}.");
```

## Conclusão
Concluindo, carregar fontes personalizadas no GroupDocs.Annotation para .NET oferece aos desenvolvedores a flexibilidade de personalizar as anotações em documentos de acordo com suas necessidades. Seguindo os passos descritos neste tutorial, você pode integrar fontes personalizadas perfeitamente aos seus aplicativos .NET e aprimorar a experiência de anotação para os usuários.
## Perguntas frequentes
### Posso carregar várias fontes personalizadas simultaneamente?
Sim, você pode especificar vários diretórios de fontes ao instanciar o `Annotator` objeto.
### Há alguma limitação quanto aos tipos de fontes suportadas?
O GroupDocs.Annotation for .NET oferece suporte a uma ampla variedade de tipos de fonte, incluindo fontes TrueType (.ttf) e OpenType (.otf).
### Posso alterar dinamicamente as fontes carregadas durante o tempo de execução?
Sim, você pode modificar dinamicamente os diretórios de fontes e recarregar as anotações do documento conforme necessário.
### GroupDocs.Annotation oferece suporte à incorporação de fontes em documentos de saída?
Sim, você pode incorporar fontes personalizadas nos documentos de saída para garantir uma renderização consistente em diferentes plataformas.
### Existe uma maneira de lidar com o licenciamento de fontes dentro do aplicativo?
O GroupDocs.Annotation oferece opções para gerenciar o licenciamento de fontes, incluindo licenças temporárias para fins de avaliação.