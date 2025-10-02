---
"date": "2025-05-06"
"description": "Aprenda a adicionar e remover anotações sublinhadas em documentos Java usando GroupDocs.Annotation. Aprimore seu gerenciamento de documentos com este guia detalhado."
"title": "Adicionar e remover anotações sublinhadas em Java usando GroupDocs - Um guia completo"
"url": "/pt/java/annotation-management/java-groupdocs-annotate-add-remove-underline/"
type: docs
"weight": 1
---

# Como implementar Java: adicionar e remover anotações sublinhadas com GroupDocs

## Introdução

Quer aprimorar seu sistema de gerenciamento de documentos adicionando ou removendo anotações programaticamente? Este tutorial o guiará pelo uso da poderosa biblioteca GroupDocs.Annotation em Java para adicionar anotações sublinhadas e removê-las de documentos como PDFs.

**O que você aprenderá:**
- Inicialize a classe Annotator.
- Adicione uma anotação sublinhada com comentários usando GroupDocs.Annotation para Java.
- Remover todas as anotações de um documento.
- Configure seu ambiente para usar o GroupDocs.Annotation com eficiência.

Vamos explorar como essas funcionalidades podem ser aproveitadas em seus projetos. Certifique-se de atender aos pré-requisitos necessários antes de começar.

## Pré-requisitos

### Bibliotecas e dependências necessárias
Para seguir este tutorial de forma eficaz, certifique-se de ter:
- **GroupDocs.Annotation para Java**: Recomenda-se a versão 25.2 ou posterior.
- **Kit de Desenvolvimento Java (JDK)**: É necessária a versão 8 ou superior.

### Requisitos de configuração do ambiente
Certifique-se de que seu ambiente de desenvolvimento inclua um IDE como IntelliJ IDEA ou Eclipse e uma ferramenta de construção como Maven.

### Pré-requisitos de conhecimento
Um conhecimento básico de programação Java, especialmente trabalhando com bibliotecas via Maven, será benéfico.

## Configurando GroupDocs.Annotation para Java

Para começar a usar GroupDocs.Annotation em seus projetos Java, siga estas etapas de configuração:

**Configuração do Maven:**
Adicione a seguinte configuração ao seu `pom.xml` arquivo para baixar e integrar o GroupDocs.Annotation.

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

**Aquisição de licença:**
Comece baixando uma versão de avaliação gratuita ou obtendo uma licença temporária do GroupDocs para explorar todos os recursos da biblioteca. Para uso em produção, é necessário adquirir uma licença.

## Guia de Implementação

### Recurso 1: Inicializar o Anotador e Adicionar Anotação Sublinhada

Esta seção orienta você na inicialização do `Annotator` classe e adicionar uma anotação de sublinhado ao seu documento.

#### Visão geral
Adicionar anotações ajuda a destacar partes específicas de um documento. Aqui, focamos em sublinhar o texto com comentários para esclarecimento ou feedback.

#### Implementação passo a passo

**1. Inicializar o Annotator**
Criar um `Annotator` objeto e carregue seu arquivo PDF.

```java
import com.groupdocs.annotation.Annotator;

// Carregue o documento que você deseja anotar
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**2. Crie comentários com respostas**
Defina comentários associados à anotação sublinhada.

```java
import com.groupdocs.annotation.models.Reply;
import java.util.Calendar;
import java.util.ArrayList;
import java.util.List;

Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);
```

**3. Defina pontos para anotação sublinhada**
Defina coordenadas para determinar onde o sublinhado deve aparecer.

```java
import com.groupdocs.annotation.models.Point;

Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
Point point3 = new Point(80, 650);
Point point4 = new Point(240, 650);

List<Point> points = new ArrayList<>();
points.add(point1);
points.add(point2);
points.add(point3);
points.add(point4);
```

**4. Criar e configurar anotação sublinhada**
Crie a anotação sublinhada e defina suas propriedades como cor, opacidade e comentários.

```java
import com.groupdocs.annotation.models.annotationmodels.UnderlineAnnotation;

UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setFontColor(65535); // Amarelo em formato ARGB
underline.setMessage("This is an underline annotation");
underline.setOpacity(0.7f);
underline.setPageNumber(0);
underline.setPoints(points);
underline.setReplies(replies);

annotator.add(underline);
```

**5. Salve o documento anotado**
Salve suas alterações em um novo arquivo.

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

#### Dicas para solução de problemas
- Certifique-se de que todas as coordenadas dos pontos estejam dentro dos limites do documento.
- Verifique se o `outputPath` o diretório existe e é gravável.

### Recurso 2: Salvar documento sem anotações

Esta seção aborda como remover todas as anotações de um documento anotado anteriormente.

#### Visão geral
Talvez seja necessário salvar uma versão limpa do seu documento, sem anotações, para fins de compartilhamento ou arquivamento.

#### Implementação passo a passo

**1. Inicialize o Annotator com o documento anotado**
Carregue o documento que possui anotações existentes.

```java
Annotator annotator = new Annotator(outputPath);
```

**2. Configure as opções de salvamento para remover anotações**
Especifique que nenhuma anotação deve ser salva no arquivo de saída.

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**3. Salve o documento sem anotações**
Defina o caminho para o documento limpo e salve-o.

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

## Aplicações práticas

Aqui estão alguns cenários do mundo real onde esses recursos podem ser benéficos:
1. **Revisão de documentos**: Destacar e comentar seções de um contrato ou relatório para revisão.
2. **Ferramentas educacionais**: Anotar livros didáticos com notas ou correções para os alunos.
3. **Edição Colaborativa**: Compartilhamento de rascunhos anotados entre os membros da equipe para feedback.
4. **Documentação Legal**: Sublinhar cláusulas-chave em documentos legais durante discussões.
5. **Materiais de Marketing**: Destacar informações importantes em folhetos antes da distribuição.

## Considerações de desempenho
Ao trabalhar com GroupDocs.Annotation, considere estas dicas para otimizar o desempenho:
- **Gerenciamento de memória**: Descarte adequadamente `Annotator` objetos para liberar recursos.
- **Processamento em lote**: Se estiver anotando vários documentos, processe-os em lotes para gerenciar a carga do sistema de forma eficaz.
- **Alocação de Recursos**: Certifique-se de que seu ambiente tenha memória e poder de processamento suficientes para lidar com arquivos grandes.

## Conclusão
Você aprendeu a adicionar e remover anotações sublinhadas usando GroupDocs.Annotation para Java. Este tutorial abordou a inicialização da classe Annotator, a configuração de anotações com comentários e o salvamento de documentos sem anotações. 

Para uma exploração mais aprofundada, considere integrar esses recursos aos seus sistemas de gerenciamento de documentos existentes ou experimentar outros tipos de anotação fornecidos pelo GroupDocs.

## Seção de perguntas frequentes
1. **Como configuro várias anotações de sublinhado em uma única execução?**
   - Crie múltiplos `UnderlineAnnotation` objetos e adicioná-los sequencialmente usando o `annotator.add()` método.
2. **Posso anotar imagens em PDFs usando esta biblioteca?**
   - Sim, o GroupDocs.Annotation suporta anotações em imagens em documentos como PDFs.
3. **Quais formatos de arquivo o GroupDocs.Annotation suporta?**
   - Ele suporta vários formatos de documentos, incluindo PDF, Word, Excel e muito mais.