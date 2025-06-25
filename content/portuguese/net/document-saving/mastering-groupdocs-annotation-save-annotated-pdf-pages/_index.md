---
"date": "2025-05-06"
"description": "Aprenda a salvar com eficiência apenas as páginas anotadas de um PDF usando o GroupDocs.Annotation para .NET. Aprimore o gerenciamento de documentos e a colaboração com este guia detalhado."
"title": "Como salvar páginas anotadas em PDF usando GroupDocs.Annotation para .NET"
"url": "/pt/net/document-saving/mastering-groupdocs-annotation-save-annotated-pdf-pages/"
"weight": 1
---

# Como salvar páginas anotadas em PDF usando GroupDocs.Annotation para .NET

## Introdução

Com dificuldades para salvar páginas anotadas específicas de seus documentos PDF? Este guia completo demonstra como fazer isso de forma eficiente usando o GroupDocs.Annotation para .NET. Aproveitando os recursos de anotação, simplifique o gerenciamento de documentos e aprimore a colaboração, concentrando-se em conteúdo relevante.

Neste tutorial, você aprenderá:
- Configurando seu ambiente de desenvolvimento com GroupDocs.Annotation
- Adicionando vários tipos de anotações
- Salvando apenas páginas anotadas de forma eficaz

Pronto para começar? Vamos garantir que você tenha tudo pronto.

### Pré-requisitos

Antes de começar, certifique-se de ter o seguinte:
- **Estrutura .NET** (versão 4.6 ou posterior) ou **.NET Core/5+**
- Um editor de código como o Visual Studio
- Conhecimento básico de configuração de projetos C# e .NET

## Configurando GroupDocs.Annotation para .NET

Para começar a usar o GroupDocs.Annotation, instale-o via NuGet.

**Console do gerenciador de pacotes NuGet**

```plaintext
Install-Package GroupDocs.Annotation -Version 25.4.0
```

**\.NET CLI**

```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

### Aquisição de Licença

O GroupDocs oferece um teste gratuito para você explorar o software por completo. Para uso prolongado, adquira uma licença ou solicite uma temporária:
- **Teste grátis**: Explore recursos sem limitações por um período inicial.
- **Licença Temporária**: Use GroupDocs.Annotation em produção temporariamente.
- **Comprar**Proteja suas necessidades de longo prazo com uma licença comercial.

Uma vez instalada, inicialize a biblioteca da seguinte maneira:

```csharp
using GroupDocs.Annotation;

// Configuração básica para carregar e anotar documentos
Annotator annotator = new Annotator("path/to/your/document.pdf");
```

## Guia de Implementação

### Adicionando Anotações

#### Visão geral

As anotações ajudam a destacar áreas importantes do seu documento. Vamos explorar como adicionar uma `AreaAnnotation` e um `EllipseAnnotation`.

**Etapa 1: Criar anotação de área**

```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;

// Definir a anotação da área
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Posição e tamanho
    BackgroundColor = 65535,                // Valor de cor ARGB para destaque
    PageNumber = 1                          // Número de página específico
};
```

O `AreaAnnotation` destaca uma área retangular no documento. Personalize sua posição (`Box`) e cor de fundo.

**Etapa 2: Criar anotação de elipse**

```csharp
// Defina a anotação de elipse
EllipseAnnotation ellipse = new EllipseAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Posição e tamanho
    BackgroundColor = 123456,                // Valor de cor ARGB para destaque
    PageNumber = 1                           // Número de página específico
};
```

O `EllipseAnnotation` permite desenhar uma forma oval no documento. Ajuste a posição e as dimensões usando o `Box` propriedade.

**Etapa 3: Adicionar anotações**

```csharp
// Adicionando anotações à instância do Annotator
annotator.Add(new List<AnnotationBase>() { area, ellipse });
```

Usando o `Add` método, inclui vários tipos de anotações. Esta etapa adiciona ambos `AreaAnnotation` e `EllipseAnnotation`.

### Salvando apenas páginas anotadas

#### Visão geral

Para salvar apenas páginas que contêm anotações, configure suas opções de salvamento adequadamente.

**Etapa 4: Salvar páginas anotadas**

```csharp
using GroupDocs.Annotation.Options;

// Configure opções de salvamento para incluir apenas páginas anotadas
annotator.Save("path/to/output/document.pdf\