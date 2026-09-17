---
categories:
- Java Development
date: '2026-09-10'
description: Aprenda como usar a pdf annotation library java para adicionar anotações
  interativas de polilinhas, integrar com serviços de anotação PDF spring boot e gerar
  caminhos SVG em Java.
keywords:
- pdf annotation library java
- spring boot pdf annotation
- generate svg path java
- polyline annotation java
- groupdocs annotation java
lastmod: '2026-09-10'
linktitle: Guia de Anotação de Polilinhas Java
og_description: Aprenda como usar a pdf annotation library java para adicionar anotações
  interativas de polilinhas, integrar com serviços de anotação PDF spring boot e gerar
  caminhos SVG em Java.
og_image_alt: Guide to adding interactive polyline annotations using a pdf annotation
  library java
og_title: Como usar a pdf annotation library java para PDFs com polilinhas
schemas:
- author: GroupDocs
  dateModified: '2026-09-10'
  description: Learn how to use a pdf annotation library java to add interactive polyline
    annotations, integrate with spring boot pdf annotation services, and generate
    SVG paths in Java.
  headline: How to use a pdf annotation library java for polyline PDFs
  type: TechArticle
- description: Learn how to use a pdf annotation library java to add interactive polyline
    annotations, integrate with spring boot pdf annotation services, and generate
    SVG paths in Java.
  name: How to use a pdf annotation library java for polyline PDFs
  steps:
  - name: '**Create the annotation replies collection** – this gives reviewers a place
      to add comments.'
    text: '**Create the annotation replies collection** – this gives reviewers a place
      to add comments.'
  - name: '**Organize the replies** into a list that the annotation will reference.'
    text: '**Organize the replies** into a list that the annotation will reference.'
  - name: '**Configure the polyline** – set the bounding box, pen color, opacity,
      and most importantly the `SVGPath` that draws the line.'
    text: '**Configure the polyline** – set the bounding box, pen color, opacity,
      and most importantly the `SVGPath` that draws the line.'
  - name: '**Add the annotation to the document** via `annotator.addAnnotation(polyline)`.'
    text: '**Add the annotation to the document** via `annotator.addAnnotation(polyline)`.'
  - name: '**Save and clean up** – persist the PDF and dispose of the `Annotator`
      instance.'
    text: '**Save and clean up** – persist the PDF and dispose of the `Annotator`
      instance.'
  - name: '**Trim coordinate precision** – round to two decimal places.'
    text: '**Trim coordinate precision** – round to two decimal places.'
  - name: '**Prefer relative commands (`l`)** – they reduce string length by up to
      30 %.'
    text: '**Prefer relative commands (`l`)** – they reduce string length by up to
      30 %.'
  - name: '**Group similar annotations** – apply the same style to multiple polylines
      to reuse resources.'
    text: '**Group similar annotations** – apply the same style to multiple polylines
      to reuse resources.'
  type: HowTo
- questions:
  - answer: It connects multiple points to form complex, interactive paths in a PDF.
    question: What is the primary purpose of a polyline annotation?
  - answer: GroupDocs.Annotation for Java, a leading pdf annotation library java.
    question: Which library makes this easiest in Java?
  - answer: Yes – see the Spring Boot integration section.
    question: Can I use it with Spring Boot?
  - answer: By providing an SVG path string (e.g., using `generate svg path java`).
    question: How do I define the line shape?
  - answer: A trial license works for development; a production license is required
      for deployment.
    question: Do I need a license?
  type: FAQPage
tags:
- pdf annotation
- java
- groupdocs
- spring boot
title: Como usar a pdf annotation library java para PDFs com polilinhas
type: docs
---

# Como usar uma pdf annotation library java para PDFs de polilinha

Neste tutorial abrangente, você descobrirá como **usar uma pdf annotation library java** para criar anotações de polilinha interativas, incorporá‑las em serviços Spring Boot e gerar strings de caminho SVG programaticamente. Seja você está construindo uma plataforma de revisão de documentos, uma ferramenta de e‑learning ou um gerador de diagramas técnicos, os passos abaixo fornecem uma solução pronta para produção que escala.

## Respostas rápidas
- **Qual é o objetivo principal de uma anotação de polilinha?** Ela conecta múltiplos pontos para formar caminhos complexos e interativos em um PDF.  
- **Qual biblioteca torna isso mais fácil em Java?** GroupDocs.Annotation for Java, uma das principais pdf annotation library java.  
- **Posso usá‑la com Spring Boot?** Sim – veja a seção de integração com Spring Boot.  
- **Como defino a forma da linha?** Fornecendo uma string de caminho SVG (por exemplo, usando `generate svg path java`).  
- **Preciso de uma licença?** Uma licença de avaliação funciona para desenvolvimento; uma licença de produção é necessária para implantação.

## Por que escolher GroupDocs.Annotation para Java?

GroupDocs.Annotation oferece um conjunto abrangente de recursos que simplificam o desenvolvimento de anotações PDF, incluindo processamento de alto desempenho, amplo suporte a formatos e tipos de anotação interativos incorporados, tudo enquanto minimiza a complexidade do código e o consumo de memória. Isso a torna ideal para aplicações corporativas que exigem manipulação de documentos confiável e escalável em ambientes diversos.

GroupDocs.Annotation é uma **pdf annotation library java** que supera kits genéricos de PDF. Ela oferece:
- **Mais de 50 formatos de entrada e saída** – incluindo DOCX, XLSX, PPTX, HTML e tipos comuns de imagem – processando PDFs com centenas de páginas sem carregar o arquivo inteiro na memória.  
- **Tipos de anotação incorporados** (polyline, highlight, comment, etc.) que são renderizados de forma consistente em todos os principais visualizadores de PDF.  
- **Processamento no lado do servidor**, eliminando preocupações de segurança no cliente e garantindo a mesma renderização em todas as plataformas.  
- **Desempenho nível empresarial** – a biblioteca pode anotar um PDF de 300 páginas em menos de 2 segundos em VMs de nuvem típicas.  

Em comparação com iText ou PDFBox, você escreve muito menos código boilerplate; comparado com soluções JavaScript do lado do cliente, você mantém o processamento pesado no servidor, onde tem controle total sobre licenciamento e uso de recursos.

## O que você aprenderá

Ao final deste guia, você será capaz de:
- Instalar e configurar a pdf annotation library java em um projeto Maven ou Gradle.  
- Criar anotações PDF de polilinha interativas com cores personalizadas, opacidade e geometria definida por SVG.  
- Anexar respostas de comentário às anotações para fluxos de trabalho colaborativos de revisão.  
- Otimizar o uso de memória e processar em lote grandes coleções de documentos.  
- Expor a criação de anotações através de uma API REST Spring Boot.

## Pré‑requisitos e configuração do ambiente

**Requisitos essenciais**
- JDK 8 ou superior (JDK 11+ recomendado)  
- Maven 3.6+ ou Gradle 6+  
- Uma IDE como IntelliJ IDEA ou Eclipse  
- Familiaridade básica com Java e gerenciamento de dependências Maven  

**Desejável**
- Compreensão dos sistemas de coordenadas de página PDF  
- Experiência com a sintaxe de caminho SVG (útil para `generate svg path java`)

### Configuração do Maven

Adicione a dependência GroupDocs.Annotation ao seu `pom.xml`:

```xml
<!-- placeholder for Maven dependency -->
```

**Dica profissional**: Sempre verifique se está usando a versão estável mais recente no site da GroupDocs. A versão 25.2 introduziu um aumento de velocidade de 30 % na renderização de polilinhas.

### Configuração de licença

GroupDocs.Annotation requer uma licença para uso em produção.

- **Desenvolvimento/teste** – comece com uma [licença de avaliação gratuita](https://releases.groupdocs.com/annotation/java/) que fornece funcionalidade completa por 30 dias.  
- **Avaliação estendida** – solicite uma [licença temporária](https://purchase.groupdocs.com/temporary-license/) se precisar de mais tempo.  
- **Produção** – adquira uma assinatura na [página de compra da GroupDocs](https://purchase.groupdocs.com/buy). O licenciamento é escalonado por tamanho de implantação (aplicação única vs. site‑wide).

### Inicialização básica do ambiente

A classe `Annotator` é o ponto de entrada para todas as operações de anotação:

```java
// placeholder for Annotator initialization
```

**Importante**: Use try‑with‑resources ou chame explicitamente `close()` no `Annotator` para evitar vazamentos de memória, especialmente em serviços de longa duração.

## Como criar uma anotação de polilinha usando uma pdf annotation library java?

`PolylineAnnotation` representa uma forma de linha de múltiplos segmentos cuja geometria é definida por uma string de caminho SVG.

Carregue o PDF alvo, instancie um `PolylineAnnotation`, defina suas propriedades visuais, anexe quaisquer respostas de comentário e, em seguida, salve o documento. Esse fluxo de ponta a ponta requer apenas três chamadas de API e executa em menos de um segundo para arquivos típicos de 10 páginas, processando de forma eficiente.

### Âncora de definição

`PolylineAnnotation` é a classe GroupDocs.Annotation que representa uma forma de linha de múltiplos segmentos cuja geometria é definida por uma string de caminho SVG. Ela herda propriedades comuns de anotação, como cor, opacidade e localização da página.

### Guia passo a passo

1. **Criar a coleção de respostas de anotação** – isso fornece aos revisores um local para adicionar comentários.  
2. **Organizar as respostas** em uma lista que a anotação referenciará.  
3. **Configurar a polilinha** – definir a caixa delimitadora, cor da caneta, opacidade e, mais importante, o `SVGPath` que desenha a linha.  
4. **Adicionar a anotação ao documento** via `annotator.addAnnotation(polyline)`.  
5. **Salvar e limpar** – persistir o PDF e descartar a instância `Annotator`.  

Os marcadores abaixo indicam onde você normalmente colaria os trechos reais de Java:

```text
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
```

```text
```java
import com.groupdocs.annotation.Annotator;

// Initialize Annotator with your document
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```
```

```text
```java
import com.groupdocs.annotation.models.Reply;
import java.util.Calendar;

// Create reply instances with comments
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());
```
```

```text
```java
import java.util.ArrayList;
import java.util.List;

// Add replies to a list
List<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);
```
```

```text
```java
import com.groupdocs.annotation.models.PenStyle;
import com.groupdocs.annotation.models.Rectangle;
import com.groupdocs.annotation.models.annotationmodels.PolylineAnnotation;

// Initialize polyline annotation
PolylineAnnotation polyline = new PolylineAnnotation();
polyline.setBox(new Rectangle(250, 35, 102, 12)); // Position and size
polyline.setMessage("This is a polyline annotation"); // Annotation message
polyline.setOpacity(0.7); // Opacity (0-1)
polyline.setPageNumber(0); // Page index (0-based)
polyline.setPenColor(65535); // Color in ARGB format
polyline.setPenStyle(PenStyle.DOT); // Pen style options
polyline.setPenWidth((byte) 3); // Pen width in pixels

// Associate replies and define the path
polyline.setReplies(replies);
polyline.setSvgPath("M250.8280751173709,48.209295774647885l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793...");
```
```

```text
```java
// Add the annotation using Annotator
annotator.add(polyline);
```
```

```text
```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/Annotated.pdf";
annotator.save(outputPath); // Save annotated document

// Dispose of annotator resources
annotator.dispose();
```
```

## Trabalhando com caminhos SVG

A string de caminho SVG define a forma exata da polilinha. Ela usa uma linguagem de comandos compacta que a pdf annotation library java interpreta para desenhar linhas.

### Comandos básicos de caminho

- **M** – mover para (ponto inicial)  
- **L** – linha para (coordenadas absolutas)  
- **l** – linha para (coordenadas relativas)  

Um caminho simples em forma de L parece assim:

```text
```
M10,10 L50,10 L50,50
```
```

### Gerando caminhos programaticamente

Quando precisar construir caminhos a partir de pontos fornecidos pelo usuário, gere a string SVG em Java:

```text
```java
public String generatePolylinePath(Point[] points) {
    if (points.length == 0) return "";
    
    StringBuilder path = new StringBuilder();
    path.append("M").append(points[0].x).append(",").append(points[0].y);
    
    for (int i = 1; i < points.length; i++) {
        path.append("L").append(points[i].x).append(",").append(points[i].y);
    }
    
    return path.toString();
}
```
```

Esta técnica é ideal para cenários `generate svg path java` como editores de diagramas dinâmicos.

## Casos de uso e aplicações reais

### Documentação técnica

```text
```java
// Create annotation for data flow path
PolylineAnnotation dataFlow = new PolylineAnnotation();
dataFlow.setMessage("Data flow from API to Database");
dataFlow.setPenColor(0xFF0000FF); // Blue for data flow
dataFlow.setPenStyle(PenStyle.SOLID);
dataFlow.setPenWidth((byte) 2);
// SVG path would show the actual route through your architecture
```
```

### Materiais educacionais

```text
```java
// Highlight geometric proof steps
PolylineAnnotation proofStep = new PolylineAnnotation();
proofStep.setMessage("Proof step 3: Angle bisector construction");
proofStep.setPenColor(0xFF00FF00); // Green for completed steps
proofStep.setOpacity(0.8); // Slightly transparent to not obscure text
```
```

### Revisão de documentos legais

```text
```java
// Connect related contract sections
PolylineAnnotation clauseConnection = new PolylineAnnotation();
clauseConnection.setMessage("This clause relates to section 4.2");
clauseConnection.setPenStyle(PenStyle.DASH); // Dashed for suggestions
clauseConnection.setPenColor(0xFFFF9900); // Orange for attention
```
```

## Integração com frameworks Java populares

### Integração de anotação PDF Spring boot

Exponha a criação de anotações através de um serviço Spring:

```text
```java
@Service
public class DocumentAnnotationService {
    
    public String addPolylineAnnotation(String documentPath, 
                                       PolylineConfig config) {
        try (Annotator annotator = new Annotator(documentPath)) {
            PolylineAnnotation polyline = createPolylineFromConfig(config);
            annotator.add(polyline);
            
            String outputPath = generateOutputPath(documentPath);
            annotator.save(outputPath);
            return outputPath;
        }
    }
    
    private PolylineAnnotation createPolylineFromConfig(PolylineConfig config) {
        // Implementation details based on your config structure
        // This pattern keeps your annotation logic organized and testable
    }
}
```
```

### Integração de API REST

Defina endpoints que aceitam payloads JSON descrevendo coordenadas de polilinha:

```text
```java
@RestController
@RequestMapping("/api/annotations")
public class AnnotationController {
    
    @Autowired
    private DocumentAnnotationService annotationService;
    
    @PostMapping("/polyline")
    public ResponseEntity<String> addPolylineAnnotation(
            @RequestBody PolylineRequest request) {
        
        try {
            String result = annotationService.addPolylineAnnotation(
                request.getDocumentPath(), 
                request.getConfig()
            );
            return ResponseEntity.ok(result);
        } catch (Exception e) {
            return ResponseEntity.badRequest()
                .body("Error adding annotation: " + e.getMessage());
        }
    }
}
```
```

## Otimização de desempenho e boas práticas

### Gerenciamento de memória

Para cenários de alto volume, reutilize uma única instância `Annotator` por thread e feche‑a prontamente:

```text
```java
// Use try-with-resources for automatic cleanup
public void processMultipleDocuments(List<String> documentPaths) {
    for (String path : documentPaths) {
        try (Annotator annotator = new Annotator(path)) {
            // Process document
            addPolylineAnnotations(annotator);
            annotator.save(generateOutputPath(path));
        } // Automatic disposal happens here
    }
}
```
```

### Processamento em lote

Ao lidar com milhares de PDFs, processe‑os em lotes para manter o uso de heap baixo:

```text
```java
public void batchAddPolylines(String documentPath, 
                             List<PolylineConfig> configs) {
    try (Annotator annotator = new Annotator(documentPath)) {
        // Add all annotations before saving
        for (PolylineConfig config : configs) {
            PolylineAnnotation polyline = createFromConfig(config);
            annotator.add(polyline);
        }
        // Single save operation is more efficient
        annotator.save(generateOutputPath(documentPath));
    }
}
```
```

### Otimização de caminho SVG

Caminhos complexos podem prejudicar a velocidade de renderização. Siga estas diretrizes:
1. **Reduzir a precisão das coordenadas** – arredondar para duas casas decimais.  
2. **Preferir comandos relativos (`l`)** – eles reduzem o comprimento da string em até 30 %.  
3. **Agrupar anotações semelhantes** – aplicar o mesmo estilo a várias polilinhas para reutilizar recursos.

```text
```java
// Optimize coordinate precision
public String optimizePath(String svgPath) {
    return svgPath.replaceAll("(\\d+\\.\\d{3})\\d+", "$1");
}
```
```

## Problemas comuns e soluções

### Problema 1: anotação não visível

Causas típicas incluem um índice de página incorreto (as páginas são baseadas em zero), coordenadas SVG fora dos limites da página ou opacidade definida muito baixa. Ajuste o número da página e verifique se o caminho SVG permanece dentro do retângulo da página.

```text
```java
// Debug your annotation placement
PolylineAnnotation polyline = new PolylineAnnotation();
polyline.setPageNumber(0); // Ensure correct page
polyline.setOpacity(1.0); // Full opacity for testing
polyline.setPenWidth((byte) 5); // Thicker line for visibility

// Log the bounding box to verify coordinates
Rectangle box = polyline.getBox();
System.out.println("Annotation bounds: " + box.getX() + "," + box.getY());
```
```

### Problema 2: OutOfMemoryError com documentos grandes

Process PDFs grandes em modo streaming e evite carregar o documento inteiro na memória:

```text
```java
// Implement proper memory management
public void processLargeDocument(String documentPath) {
    // Process in smaller batches
    int maxAnnotationsPerBatch = 50;
    List<PolylineConfig> allConfigs = getAnnotationConfigs();
    
    for (int i = 0; i < allConfigs.size(); i += maxAnnotationsPerBatch) {
        try (Annotator annotator = new Annotator(documentPath)) {
            int end = Math.min(i + maxAnnotationsPerBatch, allConfigs.size());
            List<PolylineConfig> batch = allConfigs.subList(i, end);
            
            processBatch(annotator, batch);
            annotator.save(generateBatchOutputPath(documentPath, i));
        }
        // Force garbage collection between batches if needed
        System.gc();
    }
}
```
```

### Problema 3: Formato de caminho SVG inválido

Certifique‑se de que o caminho começa com um comando de movimento (`M`) e que todos os valores numéricos são doubles válidos.

```text
```java
// Validate SVG path before using
public boolean isValidSVGPath(String path) {
    // Basic validation - should start with M or m
    if (!path.matches("^[Mm]\\d+.*")) {
        return false;
    }
    
    // Additional validation logic here
    return true;
}

// Use validated paths only
if (isValidSVGPath(pathString)) {
    polyline.setSvgPath(pathString);
} else {
    throw new IllegalArgumentException("Invalid SVG path: " + pathString);
}
```
```

### Problema 4: Falha na verificação da licença

Coloque o arquivo `GroupDocs.Annotation.lic` no classpath ou defina a licença programaticamente na inicialização da aplicação.

```text
```java
// Proper license initialization
public class AnnotationConfig {
    
    @PostConstruct
    public void initializeLicense() {
        try {
            // Load license from classpath or file system
            String licensePath = getClass().getClassLoader()
                .getResource("GroupDocs.Annotation.lic").getPath();
            
            License license = new License();
            license.setLicense(licensePath);
            
            System.out.println("GroupDocs.Annotation license loaded successfully");
        } catch (Exception e) {
            System.err.println("Failed to load license: " + e.getMessage());
            // Handle license failure appropriately
        }
    }
}
```
```

## Técnicas avançadas de personalização

### Atribuição dinâmica de cor

`ColorHelper` fornece métodos utilitários para mapear categorias de anotação para valores de cor ARGB.

```text
```java
public class ColorHelper {
    private static final Map<String, Integer> CATEGORY_COLORS = Map.of(
        "error", 0xFFFF0000,      // Red
        "warning", 0xFFFF9900,    // Orange  
        "info", 0xFF0099FF,       // Blue
        "success", 0xFF00FF00     // Green
    );
    
    public static int getColorForCategory(String category) {
        return CATEGORY_COLORS.getOrDefault(category, 0xFF000000); // Default black
    }
}
```
```

### Anotações interativas com propriedades personalizadas

Adicione metadados como `authorId` ou `timestamp` para enriquecer o payload da anotação:

```text
```java
// Create custom annotation with metadata
PolylineAnnotation polyline = new PolylineAnnotation();
polyline.setMessage("Process Flow: " + processName);

// Add custom properties (stored in message or replies)
Reply metadataReply = new Reply();
metadataReply.setComment("metadata:{\"processId\":\"12345\",\"priority\":\"high\"}");
polyline.setReplies(Arrays.asList(metadataReply));
```
```

## Testando sua implementação

### Testes unitários

Simule o `Annotator` e verifique se `addAnnotation` recebe um `PolylineAnnotation` configurado corretamente.

```text
```java
@Test
public void testPolylineAnnotationCreation() {
    // Arrange
    String documentPath = "test-documents/sample.pdf";
    PolylineConfig config = new PolylineConfig();
    config.setMessage("Test polyline");
    config.setPath("M10,10L50,50");
    
    // Act
    try (Annotator annotator = new Annotator(documentPath)) {
        PolylineAnnotation polyline = createPolylineFromConfig(config);
        annotator.add(polyline);
        
        // Assert
        assertNotNull(polyline);
        assertEquals("Test polyline", polyline.getMessage());
        assertEquals(0.7, polyline.getOpacity(), 0.01);
    }
}
```
```

### Testes de integração

Execute testes de ponta a ponta em arquivos PDF reais para garantir que a polilinha apareça como esperado em vários visualizadores.

```text
```java
@Test
public void testEndToEndAnnotationWorkflow() {
    // Test complete process from document input to annotated output
    String inputPath = "test-documents/input.pdf";
    String outputPath = "test-output/annotated.pdf";
    
    DocumentAnnotationService service = new DocumentAnnotationService();
    String result = service.addPolylineAnnotation(inputPath, createTestConfig());
    
    // Verify output file exists and contains annotations
    assertTrue(Files.exists(Paths.get(result)));
    
    // Additional verification logic
    verifyAnnotationExists(result);
}
```
```

## Conclusão

Agora você tem uma abordagem sólida e pronta para produção para usar uma **pdf annotation library java** para criar PDFs de polilinha interativos. A solução escala de um protótipo de documento único para processamento em lote de nível empresarial, integra‑se perfeitamente com Spring Boot e oferece controle total sobre a geometria baseada em SVG.

## Próximos passos

- Explore **area annotations** para destacar regiões irregulares.  
- Adicione **arrow annotations** para indicar direcionalidade.  
- Implemente **edição em tempo real** expondo metadados de anotação através de endpoints WebSocket.  
- Revise a [documentação](https://docs.groupdocs.com/annotation/java/) do GroupDocs.Annotation para recursos de API mais avançados.

## Recursos e leituras adicionais

- **Documentação**: [Documentação do GroupDocs.Annotation para Java](https://docs.groupdocs.com/annotation/java/)  
- **Referência de API**: [Referência completa da API](https://reference.groupdocs.com/annotation/java/)  
- **Projetos de exemplo**: Navegue no repositório GitHub da GroupDocs para aplicativos de exemplo completos.  
- **Fórum de suporte**: Faça perguntas e compartilhe soluções com a comunidade e especialistas da GroupDocs.  
- **Opções de compra e licenciamento**: Revise as [Opções de compra e licenciamento](https://purchase.groupdocs.com/buy) para detalhes.

---

**Última atualização:** 2026-09-10  
**Testado com:** GroupDocs.Annotation 25.2 for Java  
**Autor:** GroupDocs  

---

## Tutoriais relacionados

- [Adicionar anotação PDF Java – Guia completo da GroupDocs](/annotation/java/annotation-management/java-pdf-annotation-groupdocs-java/)
- [Carregar PDF Java com GroupDocs Annotation: Guia de carregamento de documento](/annotation/java/document-loading/)
- [Guia de anotações de marca d'água PDF Java da GroupDocs](/annotation/java/graphical-annotations/groupdocs-java-watermark-annotations-pdf-guide/)