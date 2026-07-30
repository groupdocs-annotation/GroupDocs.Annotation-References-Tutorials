---
categories:
- Java PDF Processing
date: '2026-07-30'
description: Aprenda como aplicar Watermark em todas as páginas a PDFs em Java usando
  GroupDocs.Annotation. Este tutorial passo a passo mostra como adicionar PDF Watermark
  em múltiplas páginas, com exemplos de código, dicas de solução de problemas e boas
  práticas.
keywords:
- apply watermark all pages
- pdf watermark multiple pages
- java add watermark pdf
- add pdf watermark java
lastmod: '2026-07-30'
linktitle: Guia Java PDF Watermark
og_description: Aplique Watermark em todas as páginas a PDFs usando GroupDocs.Annotation
  para Java. Este guia cobre PDF Watermark em múltiplas páginas, configuração, código
  e solução de problemas em um tutorial conciso.
og_image_alt: 'Guide: Apply watermark to all pages of a PDF using GroupDocs.Annotation
  Java'
og_title: Aplicar Watermark em Todas as Páginas – Java PDF Watermark Guide
schemas:
- author: GroupDocs
  dateModified: '2026-07-30'
  description: Learn how to apply watermark all pages to PDFs in Java using GroupDocs.Annotation.
    This step‑by‑step tutorial shows how to add pdf watermark multiple pages, with
    code examples, troubleshooting tips, and best practices.
  headline: Apply Watermark All Pages – Java PDF Watermark Guide
  type: TechArticle
- description: Learn how to apply watermark all pages to PDFs in Java using GroupDocs.Annotation.
    This step‑by‑step tutorial shows how to add pdf watermark multiple pages, with
    code examples, troubleshooting tips, and best practices.
  name: Apply Watermark All Pages – Java PDF Watermark Guide
  steps:
  - name: Import the Required Classes
    text: Before you can use the API, import the essential classes. **Definition:**
      Import statements bring the needed GroupDocs.Annotation classes into the current
      Java file, allowing you to reference them without fully qualified names.
  - name: Load the PDF Document
    text: Create the `Annotator` instance that points to your source PDF. **Definition:**
      The `Annotator` constructor loads the PDF file into a manageable object, preparing
      it for annotation operations. > **Pro tip:** For PDFs larger than 50 MB, consider
      increasing the JVM heap (`-Xmx4g`) and processing files
  - name: (Optional) Prepare Reply Metadata
    text: If you need to attach comments or approval notes to the watermark, create
      a `Reply` object. **Definition:** `Reply` stores user‑generated comments that
      accompany an annotation, useful for audit trails.
  - name: Configure the Watermark Appearance
    text: Set the visual properties such as text, color, rotation, size, and opacity.
      **Definition:** The following setters customize the watermark’s look and placement
      on each page.
  - name: Loop Through All Pages and Apply the Watermark
    text: To **apply watermark all pages**, iterate over the document’s page count
      and assign the annotation to each page. **Definition:** `annotator.getPageCount()`
      returns the total number of pages, enabling a loop that creates a separate `WatermarkAnnotation`
      per page.
  - name: Save the Watermarked PDF
    text: Finally, write the changes to a new file. The original PDF remains untouched.
      **Definition:** `annotator.save("output.pdf")` persists all added annotations
      into a new PDF file. That’s the complete flow for **apply watermark all pages**
      using GroupDocs.Annotation for Java.
  type: HowTo
- questions:
  - answer: Loop over the document’s page count, clone a configured `WatermarkAnnotation`
      for each page, set `setPageNumber(i)`, and add it with `annotator.add()`.
    question: How do I add watermarks to multiple pages in a PDF?
  - answer: GroupDocs.Annotation uses fonts installed on the host OS. Specify a font
      family that exists on the server; the library falls back to a default if the
      font isn’t found.
    question: Can I use custom fonts for my watermarks?
  - answer: Between **0.3** and **0.7** provides a balance—visible enough to be noticed
      but still allows underlying content to be read.
    question: What opacity setting works best for professional watermarks?
  - answer: Increase the JVM heap (`-Xmx4g` or more), process files one at a time,
      and always call `dispose()` after each document to free native resources.
    question: How should I handle very large PDF files?
  - answer: 'Yes—retrieve annotations with `annotator.get()`, filter for `WatermarkAnnotation`,
      then edit or delete as needed:'
    question: Is it possible to remove or modify existing watermarks?
  type: FAQPage
tags:
- java pdf watermark
- groupdocs annotation
- document security
- apply watermark all pages
- pdf processing
title: Aplicar Watermark em Todas as Páginas – Java PDF Watermark Guide
type: docs
url: /pt/java/graphical-annotations/groupdocs-java-watermark-annotations-pdf-guide/
weight: 1
---

# Aplicar Marca d'água em Todas as Páginas – Guia de Marca d'água PDF em Java

Neste tutorial abrangente você aprenderá **como aplicar marca d'água em todas as páginas** a um documento PDF usando Java e GroupDocs.Annotation. Seja para proteger relatórios confidenciais, marcar PDFs de marketing ou adicionar um selo “CONFIDENCIAL” em todo o arquivo, os passos abaixo orientam você em tudo—desde a configuração do Maven até personalizações avançadas—para que possa implementar uma solução confiável em minutos.

## Respostas Rápidas
- **Qual biblioteca pode adicionar marca d'água em PDF em várias páginas em Java?** GroupDocs.Annotation for Java.  
- **Preciso de uma licença?** Sim, um teste gratuito funciona para desenvolvimento; uma licença completa é necessária para produção.  
- **Posso aplicar marca d'água em todas as páginas de uma vez?** Sim – crie uma anotação de marca d'água para cada página em um loop.  
- **Qual versão do Java é necessária?** JDK 8+ (JDK 11+ recomendado).  
- **Como controlo a opacidade?** Use `setOpacity(double)` onde 0.0 é totalmente transparente e 1.0 é totalmente opaco.

## Por que Você Precisa de Marcas d'água em PDF (E Como o Java Facilita)

Já se preocupou que um PDF confidencial possa ser compartilhado sem sua permissão? Ou precisou de uma maneira rápida de marcar cada página de um folheto de vendas? Adicionar marcas d'água programaticamente elimina o esforço manual, garante consistência e reforça a segurança do documento. Com Java e GroupDocs.Annotation—uma das bibliotecas **java add watermark pdf** mais robustas—você obtém controle detalhado sobre posicionamento, rotação, cor e opacidade, tudo enquanto manipula arquivos grandes de forma eficiente.

**O que você dominará ao final deste guia:**
- Configurar o GroupDocs.Annotation para marcas d'água em Java  
- Criar anotações de marca d'água personalizadas que se aplicam a **todas as páginas**  
- Manipular PDFs grandes sem esgotar a memória  
- Solucionar armadilhas comuns e otimizar o desempenho  

## O que é uma Marca d'água em PDF e Por que Usá‑la em Múltiplas Páginas?

Uma marca d'água em PDF é uma sobreposição que aparece sobre o conteúdo do documento sem alterar o texto ou imagens subjacentes. Aplicar uma marca d'água a **todas as páginas** garante que cada página carregue a mesma identidade visual ou aviso de confidencialidade, evitando a distribuição acidental de páginas sem marca.

## Pré‑requisitos

### Requisitos Essenciais
- **Ambiente Java:** JDK 8 ou superior (JDK 11+ recomendado), Maven 3.6+, qualquer IDE (IntelliJ, Eclipse, VS Code).  
- **Pré‑requisitos de Conhecimento:** Sintaxe básica de Java, I/O de arquivos, gerenciamento de dependências Maven.  
- **Permissões do Projeto:** Acesso de escrita ao diretório de saída e RAM suficiente para PDFs grandes (≥ 4 GB recomendado para arquivos com > 200 páginas).

## Configurando Seu Ambiente de Marca d'água PDF em Java

### Adicionando GroupDocs.Annotation ao Seu Projeto

Primeiro, adicione o artefato Maven do GroupDocs.Annotation. Esta dependência traz todos os binários necessários e bibliotecas transitivas.

**Definição:** O elemento `<dependency>` do Maven declara a biblioteca GroupDocs.Annotation para seu projeto, permitindo que o compilador localize os arquivos JAR durante a compilação.  

```xml
<!-- Maven dependency for GroupDocs.Annotation -->
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-annotation</artifactId>
    <version>25.2</version>
</dependency>
```
```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/annotation/java/</url>
   </repository>
</repositories>
<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-annotation</artifactId>
      <version>25.2</version>
   </dependency>
</dependencies>
```

**Dica profissional:** Sempre use a versão mais recente lançada (o exemplo mostra 25.2, a mais recente em 2025) para aproveitar correções de bugs e melhorias de desempenho.

### Obtendo Sua Licença

Você precisa de uma licença válida para implantações em produção. Escolha a opção que se adequa ao seu cronograma:

1. **Teste Gratuito:** Ideal para desenvolvimento e testes. Baixe em [GroupDocs Downloads](https://releases.groupdocs.com/annotation/java/)  
2. **Licença Temporária:** Conjunto completo de recursos para avaliação. Obtenha uma na [Temporary License Page](https://purchase.groupdocs.com/temporary-license/)  
3. **Licença Completa:** Necessária para uso comercial. Compre através da [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy)

### Configuração Básica que Realmente Funciona

Após adicionar a dependência e obter o arquivo de licença, inicialize o objeto `Annotator`. Este objeto carrega o PDF na memória e fornece a API para criar anotações.

**Definição:** `Annotator` é o ponto de entrada principal do GroupDocs.Annotation; ele gerencia o carregamento de PDFs, criação de anotações e salvamento.  

```java
// Initialize Annotator with a license and input PDF
Annotator annotator = new Annotator("input.pdf", "GroupDocs.Annotation.lic");
```
```java
import com.groupdocs.annotation.Annotator;

public class WatermarkSetup {
    public static void main(String[] args) {
        String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/input.pdf";
        Annotator annotator = new Annotator(inputFilePath);
        
        // Your watermark code goes here...
        // Always remember to dispose!
        annotator.dispose();
    }
}
```

**Erro comum a evitar:** Esquecer de chamar `annotator.dispose()` após o processamento; isso pode causar vazamentos de memória, especialmente ao lidar com muitos documentos em lote.

## Como Aplicar Marca d'água em Todas as Páginas em Java

Para aplicar uma marca d'água em cada página, você cria um `WatermarkAnnotation`, define suas propriedades visuais e, em seguida, adiciona uma instância separada dessa anotação a cada página em um loop. O loop usa a contagem de páginas do documento, atribui o número correto da página e, finalmente, salva o PDF modificado.

### Entendendo Anotações de Marca d'água

Um `WatermarkAnnotation` representa uma camada de sobreposição que pode conter texto, cores personalizadas, rotação e opacidade. Ao contrário de uma simples adição de texto, ele é armazenado como uma anotação, tornando‑o removível ou editável posteriormente.

**Definição:** `WatermarkAnnotation` é uma classe no GroupDocs.Annotation que encapsula todas as propriedades visuais de uma sobreposição de marca d'água.  

```java
WatermarkAnnotation watermark = new WatermarkAnnotation();
```
```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.models.Reply;
import com.groupdocs.annotation.models.Rectangle;
import com.groupdocs.annotation.models.annotationmodels.WatermarkAnnotation;
import java.util.ArrayList;
import java.util.Calendar;
```

### Etapa 1: Importar as Classes Necessárias

Antes de usar a API, importe as classes essenciais.

**Definição:** As declarações de importação trazem as classes necessárias do GroupDocs.Annotation para o arquivo Java atual, permitindo referenciá‑las sem nomes totalmente qualificados.  

```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.models.annotation.WatermarkAnnotation;
import com.groupdocs.annotation.models.common.Rectangle;
import com.groupdocs.annotation.models.annotation.Reply;
```
```java
String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/input.pdf";
String outputPath = "YOUR_OUTPUT_DIRECTORY/AddWatermarkAnnotation.pdf";

final Annotator annotator = new Annotator(inputFilePath);
```

### Etapa 2: Carregar o Documento PDF

Crie a instância `Annotator` que aponta para o seu PDF de origem.

**Definição:** O construtor `Annotator` carrega o arquivo PDF em um objeto manipulável, preparando‑o para operações de anotação.  

```java
Annotator annotator = new Annotator("sample.pdf");
```
```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());
```

> **Dica profissional:** Para PDFs maiores que 50 MB, considere aumentar o heap da JVM (`-Xmx4g`) e processar arquivos sequencialmente para manter o uso de memória baixo.

### Etapa 3: (Opcional) Preparar Metadados de Resposta

Se precisar anexar comentários ou notas de aprovação à marca d'água, crie um objeto `Reply`.

**Definição:** `Reply` armazena comentários gerados pelo usuário que acompanham uma anotação, útil para trilhas de auditoria.  

```java
Reply reply = new Reply();
reply.setComment("Confidential – Internal Use Only");
```
```java
ArrayList<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);

WatermarkAnnotation watermark = new WatermarkAnnotation();
watermark.setAngle(75.0); // Set the angle of the watermark.
watermark.setBox(new Rectangle(200, 200, 100, 50)); // Define position and size with a rectangle.
watermark.setCreatedOn(Calendar.getInstance().getTime());
watermark.setText("Watermark");
watermark.setFontColor(65535); // Yellow color in ARGB format
watermark.setFontSize(12.0);
watermark.setMessage("This is a watermark annotation");
watermark.setOpacity(0.7);
watermark.setPageNumber(0);
watermark.setReplies(replies);
```

### Etapa 4: Configurar a Aparência da Marca d'água

Defina as propriedades visuais como texto, cor, rotação, tamanho e opacidade.

**Definição:** Os setters a seguir personalizam a aparência e o posicionamento da marca d'água em cada página.  

```java
watermark.setText("CONFIDENTIAL");
watermark.setAngle(75.0);                     // Diagonal orientation
watermark.setBox(new Rectangle(200, 200, 300, 100)); // Position & size
watermark.setFontColor(65535);               // Yellow (ARGB)
watermark.setOpacity(0.7);                   // 70% opacity
watermark.setReply(reply);                   // Attach the optional reply
```
```java
annotator.add(watermark);
annotator.save(outputPath);
annotator.dispose();
```

### Etapa 5: Percorrer Todas as Páginas e Aplicar a Marca d'água

Para **aplicar marca d'água em todas as páginas**, itere sobre a contagem de páginas do documento e atribua a anotação a cada página.

**Definição:** `annotator.getPageCount()` retorna o número total de páginas, permitindo um loop que cria um `WatermarkAnnotation` separado por página.  

```java
int pageCount = annotator.getPageCount();
for (int i = 0; i < pageCount; i++) {
    WatermarkAnnotation pageWatermark = watermark.clone(); // Duplicate settings
    pageWatermark.setPageNumber(i);                       // Zero‑based index
    annotator.add(pageWatermark);                         // Add to current page
}
```
```java
// Get total page count first
int pageCount = annotator.getDocument().getPages().size();

for (int i = 0; i < pageCount; i++) {
    WatermarkAnnotation watermark = new WatermarkAnnotation();
    // Reuse the same configuration or customize per page
    watermark.setAngle(45.0);
    watermark.setText("CONFIDENTIAL");
    watermark.setFontColor(16711680); // Red
    watermark.setOpacity(0.3);
    watermark.setFontSize(24.0);
    watermark.setBox(new Rectangle(100, 300, 400, 100));
    watermark.setPageNumber(i);
    annotator.add(watermark);
}
annotator.save(outputPath);
annotator.dispose();
```

### Etapa 6: Salvar o PDF com Marca d'água

Finalmente, grave as alterações em um novo arquivo. O PDF original permanece intacto.

**Definição:** `annotator.save("output.pdf")` persiste todas as anotações adicionadas em um novo arquivo PDF.  

```java
annotator.save("output_watermarked.pdf");
annotator.dispose(); // Release resources
```
```java
// Better error handling approach
try {
    File inputFile = new File(inputFilePath);
    if (!inputFile.exists()) {
        throw new FileNotFoundException("Input PDF not found: " + inputFilePath);
    }
    
    Annotator annotator = new Annotator(inputFilePath);
    // ... your watermark code
} catch (Exception e) {
    System.err.println("Error processing PDF: " + e.getMessage());
}
```

Esse é o fluxo completo para **aplicar marca d'água em todas as páginas** usando GroupDocs.Annotation para Java.

## Problemas Comuns e Como Corrigi‑los

### Erros “File Not Found”

```java
// Example of handling missing file paths
File inputFile = new File("nonexistent.pdf");
if (!inputFile.exists()) {
    throw new IllegalArgumentException("Input PDF not found at: " + inputFile.getAbsolutePath());
}
```
```java
WatermarkAnnotation confidentialWatermark = new WatermarkAnnotation();
confidentialWatermark.setAngle(45.0);
confidentialWatermark.setText("CONFIDENTIAL");
confidentialWatermark.setFontColor(16711680); // Red
confidentialWatermark.setOpacity(0.3); // Subtle but visible
confidentialWatermark.setFontSize(24.0);
confidentialWatermark.setBox(new Rectangle(100, 300, 400, 100));
```

- Verifique caminhos absolutos e assegure que o arquivo exista.  
- Verifique permissões de leitura/escrita nos diretórios de entrada e saída.  
- Crie a pasta de saída antecipadamente se ela não existir.

### Problemas de Memória com PDFs Grandes

- Sempre invoque `annotator.dispose()` após o processamento.  
- Processar PDFs um de cada vez; evite streams paralelos a menos que a biblioteca seja comprovadamente thread‑safe.  
- Aumente o heap da JVM (`-Xmx4g` ou superior) para arquivos com mais de 200 páginas.

### Posicionamento da Marca d'água Não Conforme o Esperado

- A origem das coordenadas do PDF é **bottom‑left**; ajuste os valores de `Rectangle` adequadamente.  
- Teste com diferentes tamanhos de página (A4 vs. Letter) pois as dimensões afetam o posicionamento.  
- Use `setOpacity(0.5)` se a marca d'água aparecer muito fraca em fundos de alto contraste.

### Problemas de Cor de Fonte

GroupDocs.Annotation espera valores inteiros ARGB. Cores comuns:

- Vermelho: `16711680`  
- Azul: `255`  
- Verde: `65280`  
- Preto: `0`  
- Branco: `16777215`  
- Amarelo: `65535` (usado no exemplo)

## Casos de Uso Reais para Marcas d'água em PDF com Java

### Proteção de Documentos Empresariais

```java
// Apply a corporate logo watermark across all pages of a contract
watermark.setText("© Acme Corp – Confidential");
```
```java
WatermarkAnnotation brandWatermark = new WatermarkAnnotation();
brandWatermark.setText("© YourCompany 2025");
brandWatermark.setFontColor(0); // Black
brandWatermark.setOpacity(0.6);
brandWatermark.setFontSize(10.0);
brandWatermark.setBox(new Rectangle(400, 50, 150, 30));
```

### Material de Marketing com Identidade Visual

```java
// Use a semi‑transparent brand slogan as a watermark
watermark.setText("Acme Marketing 2026");
watermark.setOpacity(0.4);
```
```java
WatermarkAnnotation versionWatermark = new WatermarkAnnotation();
versionWatermark.setText("DRAFT - v2.1");
versionWatermark.setFontColor(255); // Blue
versionWatermark.setOpacity(0.8);
versionWatermark.setBox(new Rectangle(50, 750, 100, 30));
```

### Controle de Versão de Documentos

```java
// Append version number dynamically
watermark.setText("Version 3.2 – Reviewed");
```
```java
public void processMultiplePDFs(List<String> pdfPaths) {
    for (String path : pdfPaths) {
        Annotator annotator = null;
        try {
            annotator = new Annotator(path);
            // Add your watermark logic here
            annotator.save(path.replace(".pdf", "_watermarked.pdf"));
        } finally {
            if (annotator != null) {
                annotator.dispose(); // Always dispose, even if exceptions occur
            }
        }
    }
}
```

## Dicas de Otimização de Desempenho

### Melhores Práticas de Gerenciamento de Memória

```java
// Explicitly release resources after each document
annotator.dispose();
System.gc(); // Hint to the JVM (optional)
```
```java
public class WatermarkTemplates {
    public static WatermarkAnnotation createConfidentialWatermark() {
        WatermarkAnnotation watermark = new WatermarkAnnotation();
        watermark.setAngle(45.0);
        watermark.setText("CONFIDENTIAL");
        watermark.setFontColor(16711680);
        watermark.setOpacity(0.3);
        watermark.setFontSize(24.0);
        return watermark;
    }
    
    public static WatermarkAnnotation createBrandWatermark(String companyName) {
        WatermarkAnnotation watermark = new WatermarkAnnotation();
        watermark.setText("© " + companyName + " 2025");
        watermark.setFontColor(0);
        watermark.setOpacity(0.6);
        watermark.setFontSize(10.0);
        return watermark;
    }
}
```

- Processar documentos sequencialmente para manter a pegada de heap baixa.  
- Use um indicador de progresso para trabalhos em lote para monitorar o uso de memória.  
- Evite carregar o PDF inteiro na memória quando apenas um subconjunto de páginas precisa de marca d'água; a biblioteca suporta carregamento por página.

### Dicas de Organização de Código

- Encapsule a criação de marca d'água em um método utilitário: `createWatermark(String text, double opacity, int angle)`.  
- Mantenha a configuração (cores, fontes, opacidade) externalizada em um arquivo de propriedades para fácil ajuste entre ambientes.

## Perguntas Frequentes

**Q: Como adiciono marcas d'água a várias páginas em um PDF?**  
A: Percorra a contagem de páginas do documento, clone um `WatermarkAnnotation` configurado para cada página, defina `setPageNumber(i)` e adicione‑o com `annotator.add()`.

**Q: Posso usar fontes personalizadas nas minhas marcas d'água?**  
A: O GroupDocs.Annotation usa fontes instaladas no sistema operacional host. Especifique uma família de fontes que exista no servidor; a biblioteca recorre a um padrão se a fonte não for encontrada.

**Q: Qual configuração de opacidade funciona melhor para marcas d'água profissionais?**  
A: Entre **0.3** e **0.7** oferece um equilíbrio—visível o suficiente para ser notado, mas ainda permite que o conteúdo subjacente seja lido.

**Q: Como devo lidar com arquivos PDF muito grandes?**  
A: Aumente o heap da JVM (`-Xmx4g` ou mais), processe arquivos um de cada vez e sempre chame `dispose()` após cada documento para liberar recursos nativos.

**Q: É possível remover ou modificar marcas d'água existentes?**  
A: Sim—recupere anotações com `annotator.get()`, filtre por `WatermarkAnnotation` e então edite ou exclua conforme necessário:  

```java
List<AnnotationBase> watermarks = annotator.get().stream()
    .filter(a -> a instanceof WatermarkAnnotation)
    .collect(Collectors.toList());
annotator.delete(watermarks.get(0)); // Example: delete first watermark
```
```java
// Get existing annotations
List<AnnotationBase> annotations = annotator.get();
// Filter and modify as needed
```

## Recursos Adicionais

- **Documentação:** [GroupDocs Annotation Java Docs](https://docs.groupdocs.com/annotation/java/)  
- **Referência Completa da API:** [GroupDocs Annotation Java API](https://reference.groupdocs.com/annotation/java/)  
- **Download da Versão Mais Recente:** [GroupDocs Downloads](https://releases.groupdocs.com/annotation/java/)  
- **Licenciamento Comercial:** [Purchase GroupDocs](https://purchase.groupdocs.com/buy)  
- **Suporte da Comunidade:** [GroupDocs Forums](https://forum.groupdocs.com/c/annotation/10)

---

**Última Atualização:** 2026-07-30  
**Testado com:** GroupDocs.Annotation 25.2  
**Autor:** GroupDocs  

---

## Tutoriais Relacionados

- [Carregar PDF Java com GroupDocs Annotation: Guia de Carregamento de Documento](/annotation/java/document-loading/)
- [Adicionar Anotação PDF Java – Guia Completo do GroupDocs](/annotation/java/annotation-management/java-pdf-annotation-groupdocs-java/)
- [Como adicionar imagem ao PDF usando Java e GroupDocs Annotation](/annotation/java/image-annotations/annotate-pdfs-java-groupdocs-image-annotations/)