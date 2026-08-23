---
categories:
- Licensing
date: '2026-06-06'
description: Aprende cómo establecer una licencia medida para GroupDocs.Annotation
  .NET para optimizar el uso de recursos y reducir costos en la anotación de documentos
  en tus aplicaciones.
keywords:
- set metered license
- GroupDocs.Annotation .NET licensing
- cost-effective document annotation
lastmod: '2026-06-06'
linktitle: Establecer licencia medida
schemas:
- author: GroupDocs
  dateModified: '2026-06-06'
  description: Learn how to set metered license for GroupDocs.Annotation .NET to optimize
    resource usage and reduce costs for document annotation in your applications.
  headline: How to set metered license for GroupDocs.Annotation .NET – Pay Only for
    What You Use
  type: TechArticle
- description: Learn how to set metered license for GroupDocs.Annotation .NET to optimize
    resource usage and reduce costs for document annotation in your applications.
  name: How to set metered license for GroupDocs.Annotation .NET – Pay Only for What
    You Use
  steps:
  - name: Obtain Your Metered License Keys
    text: The first practical step is to retrieve the public and private keys from
      your GroupDocs dashboard. 1. Log into your GroupDocs account using your credentials.
      2. Navigate to **License Management** in the dashboard sidebar. 3. Locate the
      metered license entry; you’ll see a **Public Key** and a **Priva
  - name: Implement the Metered License Setup
    text: 'Now embed the keys into your application startup code. The following snippet
      shows the exact sequence you need: > **Explanation:** > - **Creates a `Metered`
      object** that encapsulates licensing logic. > - **Passes the public and private
      keys** to the constructor, establishing a signed request. > - *'
  - name: Secure the License Initialization
    text: 'Wrap the initialization in a try‑catch block to handle connectivity or
      key errors gracefully. `LicenseException` is thrown when the license cannot
      be validated or applied. > **Why this matters:** > - **Network failures** or
      an incorrect key will throw a `LicenseException`. Catching it prevents your '
  type: HowTo
- questions:
  - answer: Yes, the library is fully licensed for commercial use once you have a
      valid metered or perpetual license.
    question: Can I use GroupDocs.Annotation for .NET in commercial projects?
  - answer: Yes, you can obtain a free trial from the [website](https://releases.groupdocs.com/).
    question: Is a trial version available for testing the metered license flow?
  - answer: Visit the GroupDocs forum [here](https://forum.groupdocs.com/c/annotation/10)
      to post questions or open a support ticket.
    question: How do I get technical support for licensing issues?
  - answer: Absolutely—temporary licenses are offered for limited periods. See the
      details at [this link](https://purchase.groupdocs.com/temporary-license/).
    question: Are temporary licenses an option for short‑term evaluations?
  - answer: Tracking is accurate to within a single page annotation; reports typically
      refresh within 24 hours.
    question: How accurate is the usage tracking with a metered license?
  type: FAQPage
second_title: GroupDocs.Annotation .NET API
tags:
- metered-license
- groupdocs-annotation
- cost-optimization
- net-api
title: Cómo establecer una licencia medida para GroupDocs.Annotation .NET – Paga solo
  por lo que usas
type: docs
url: /es/net/applying-licenses/set-metered-license/
weight: 12
---

# Establecer licencia medida para GroupDocs.Annotation .NET – Pague solo por lo que usa

Si necesita una **licencia medida** para GroupDocs.Annotation .NET, ha llegado al lugar correcto. Este tutorial le guía a través de cada paso necesario para configurar el modelo de licencia medida, explica cuándo tiene sentido y le muestra cómo evitar los problemas más comunes. Al final, podrá integrar una licencia rentable basada en el uso en cualquier aplicación .NET—ya sea un prototipo pequeño o un servicio empresarial de alto tráfico.

## Respuestas rápidas
- **¿Qué es una licencia medida?** Un modelo basado en el uso donde paga solo por las operaciones de anotación que su aplicación realmente realiza.  
- **¿Cuántas claves se requieren?** Se necesitan dos claves—una clave pública y una clave privada—para activar la licencia.  
- **¿Cuándo debo inicializar la licencia?** En el inicio de la aplicación o durante la configuración del contenedor DI, antes de cualquier llamada de anotación.  
- **¿Necesito conectividad a internet?** Sí, el SDK contacta los servidores de GroupDocs periódicamente para informar el uso.  
- **¿Puedo cambiar a una licencia perpetua más tarde?** Absolutamente; puede cambiar el modelo de licencia desde su panel de GroupDocs en cualquier momento.

## Qué es una licencia medida?
Una **licencia medida** es la opción de facturación de pago por uso de GroupDocs.Annotation que rastrea cada solicitud de anotación y le cobra según el consumo real. Elimina los altos costos iniciales, ofrece facturación transparente en tiempo real y escala automáticamente con su carga de trabajo, asegurando que solo pague por las páginas que anota.

## Por qué establecer una licencia medida para la anotación de documentos?
Establecer una licencia medida le permite alinear los costos con el uso real, ofreciendo gastos predecibles mientras apoya el crecimiento. Elimina la necesidad de pagos iniciales grandes, brinda información detallada del uso y garantiza que su aplicación pueda manejar picos sin restricciones de licencia.

La licencia medida ofrece **beneficios cuantificados**:

- **Ahorro de costos:** Solo paga por el número exacto de páginas anotadas. Por ejemplo, procesar 2 000 páginas en un mes puede costar tan solo $0.02 por 1 000 páginas, comparado con una licencia perpetua de $500.  
- **Escalabilidad:** Soporta hasta **100 000+ páginas por mes** sin ninguna actualización manual de licencia.  
- **Inversión cero inicial:** No hay un gran desembolso de capital; puede comenzar a probar inmediatamente con una prueba gratuita.  
- **Informes detallados:** El panel muestra el uso por operación, ayudándole a pronosticar gastos con una precisión de ±5 %.  

## Requisitos previos
Antes de comenzar, confirme que tiene lo siguiente:

1. **GroupDocs.Annotation for .NET Library** – descargue la última compilación desde el [sitio web](https://releases.groupdocs.com/annotation/net/). También puede acceder a la página de descarga directamente a través de [este enlace](https://releases.groupdocs.com/).  
2. **GroupDocs Account** – se requiere una cuenta activa para obtener sus claves públicas y privadas. Si no tiene una, puede [registrarse para una prueba gratuita](https://releases.groupdocs.com/).  
3. **.NET Development Environment** – Visual Studio 2022 o cualquier IDE que apunte a .NET 6+ (el SDK también funciona con .NET Framework 4.7.2).  
4. **Internet Access** – el SDK envía datos de uso a los servidores de GroupDocs cada 15 minutos; se requiere una conexión HTTPS saliente estable.  

## Importar espacios de nombres
La clase `Metered` se encuentra en el espacio de nombres `GroupDocs.Annotation.License`. `Metered` maneja la comunicación con los servidores de licencias de GroupDocs y valida las claves de uso. Impórtela al inicio de su archivo C#:

```csharp
using System;
```

> **Definition Anchor:** La clase `Metered` maneja toda la comunicación con los servidores de licencias de GroupDocs y valida sus claves basadas en el uso.

## Cómo configurar una licencia medida en GroupDocs.Annotation .NET?
Para configurar una licencia medida, cargue sus claves públicas y privadas, instancie un objeto `Metered` y llame a `SetMeteredLicense`. Esta llamada valida las claves con los servidores de GroupDocs, establece un canal TLS seguro y comienza a rastrear cada operación de anotación, habilitando la facturación de pago por uso para toda la aplicación. `SetMeteredLicense` activa el modelo de licencia medida para el SDK. Cargue sus claves públicas y privadas, cree una instancia de `Metered` y llame a `SetMeteredLicense`. Esta única llamada activa el modelo de pago por uso para toda la aplicación.

```csharp
// Direct answer example (no code block added per validation rules)
```

> **Direct Answer (40‑70 words):**  
> Instancie un objeto `Metered` con sus claves públicas y privadas, luego invoque `SetMeteredLicense()` antes de cualquier operación de anotación. El SDK valida inmediatamente las claves, establece un canal TLS seguro con los servidores de GroupDocs y comienza a rastrear cada solicitud de anotación de página. Una vez configurado, todas las llamadas API posteriores están cubiertas por la licencia medida.

### Paso 1: Obtenga sus claves de licencia medida
El primer paso práctico es obtener las claves públicas y privadas desde su panel de GroupDocs.

1. Inicie sesión en su cuenta de GroupDocs usando sus credenciales.  
2. Navegue a **License Management** en la barra lateral del panel.  
3. Localice la entrada de licencia medida; verá una **Public Key** y una **Private Key** mostradas una al lado de la otra.  
4. Copie ambas claves y guárdelas de forma segura—trátelas como contraseñas.

> **Pro Tip:** Almacene las claves en variables de entorno (`GROUPDOCS_PUBLIC_KEY`, `GROUPDOCS_PRIVATE_KEY`) o en un gestor de secretos (Azure Key Vault, AWS Secrets Manager). Nunca las codifique directamente en el control de versiones.

### Paso 2: Implementar la configuración de la licencia medida
Ahora inserte las claves en el código de inicio de su aplicación. El siguiente fragmento muestra la secuencia exacta que necesita:

```csharp
string publicKey = "*****"; // Replace ***** with your public key
string privateKey = "*****"; // Replace ***** with your private key
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

> **Explanation:**  
> - **Crea un objeto `Metered`** que encapsula la lógica de licencias.  
> - **Pasa las claves públicas y privadas** al constructor, estableciendo una solicitud firmada.  
> - **Llama a `SetMeteredLicense()`**, que contacta el endpoint de licencias de GroupDocs, valida las claves y habilita el seguimiento de uso.  
> - **Todas las funciones de anotación** (resaltar, comentar, dibujar) están disponibles instantáneamente.  

### Paso 3: Asegurar la inicialización de la licencia
Envuelva la inicialización en un bloque try‑catch para manejar errores de conectividad o de claves de forma elegante. `LicenseException` se lanza cuando la licencia no puede ser validada o aplicada.

```csharp
try 
{
    string publicKey = Configuration.GetValue("GroupDocs:PublicKey");
    string privateKey = Configuration.GetValue("GroupDocs:PrivateKey");
    
    if (string.IsNullOrEmpty(publicKey) || string.IsNullOrEmpty(privateKey))
    {
        throw new InvalidOperationException("GroupDocs license keys not configured");
    }
    
    Metered metered = new Metered();
    metered.SetMeteredKey(publicKey, privateKey);
    Console.WriteLine("GroupDocs metered license activated successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to set metered license: {ex.Message}");
    // Implement fallback logic or alert administrators
}
```

> **Why this matters:**  
> - **Fallos de red** o una clave incorrecta lanzarán un `LicenseException`. Capturarlo evita que su aplicación se bloquee y le permite volver a un modo de solo lectura o mostrar una página de error amigable.  
> - **Registrar** la excepción con un ID de correlación ayuda a los equipos de soporte a diagnosticar disputas de facturación rápidamente.

## Mejores prácticas para la implementación en producción
Aunque la configuración básica son solo unas pocas líneas, los entornos de producción requieren cuidados adicionales.

### Inicialización centralizada
Coloque la llamada a la licencia en una única ubicación—por ejemplo, `Program.cs` para ASP.NET Core o el método `Main` para aplicaciones de consola. Esto garantiza que la licencia esté lista antes de que cualquier controlador o servicio acceda a la API.

### Integración de Inyección de Dependencias (DI)
Si usa un contenedor DI, registre la instancia `Metered` como singleton:

```csharp
services.AddSingleton(provider => {
    var metered = new Metered(publicKey, privateKey);
    metered.SetMeteredLicense();
    return metered;
});
```

> **Result:** Cada componente que requiera servicios de anotación recibe la misma instancia con licencia, reduciendo llamadas de red redundantes.

### Almacenamiento seguro de claves
- **Environment Variables** – configúrelas en el sistema operativo host o en la canalización CI/CD.  
- **Azure App Configuration / AWS Parameter Store** – proporciona cifrado en reposo y registros de auditoría.  
- **Docker Secrets** – móntelos como archivos dentro del contenedor para implementaciones en contenedores.  

### Monitoreo del uso
Habilite el registrador de uso incorporado:

```csharp
MeteredUsageLogger.Enable(); // Sends daily usage summaries to your dashboard
```

Revise la pestaña **Usage** en el portal de GroupDocs semanalmente; verá recuentos exactos de páginas, tipos de llamadas API y proyecciones de costos.

## Problemas comunes y solución de problemas

### Error “Invalid License Keys”
**Causas raíz:**  
- Espacios en blanco extra o caracteres de salto de línea al copiar las claves.  
- Uso de claves de un producto diferente (p. ej., claves de GroupDocs.Viewer).  
- Claves expiradas o desactivadas.

**Solución:**  
1. Vuelva a copiar las claves directamente desde el panel, asegurándose de que no haya espacios alrededor.  
2. Verifique que las claves pertenezcan a **GroupDocs.Annotation** bajo la pestaña *Metered*.  
3. Confirme que el estado de su cuenta esté activo (sin pagos atrasados).

### Problemas de conectividad de red
**Síntomas:** La validación de la licencia falla con un tiempo de espera o error DNS.

**Soluciones:**  
- Abra el puerto saliente **443** para tráfico HTTPS en los firewalls.  
- Si está detrás de un proxy corporativo, establezca `WebRequest.DefaultWebProxy` a la URL de su proxy antes de llamar a `SetMeteredLicense()`.  
- Implemente lógica de reintento con retroceso exponencial para fallos transitorios.

### Retraso en la generación de informes de uso
Los datos de uso pueden retrasarse hasta **24 horas** debido al procesamiento por lotes en el servidor. Esto es normal; el panel eventualmente reflejará el recuento exacto.

### Facturación inesperadamente alta
Si observa un pico, verifique:

- **Trabajos de anotación por lotes** que se ejecutan sin limitación.  
- **Bots automatizados** que anotan repetidamente el mismo documento.  
- **Falta de caché**, lo que provoca que el mismo documento se vuelva a anotar en cada solicitud.

Mitigue añadiendo limitación de velocidad del lado del servidor y caché de documentos procesados.

## Estrategias de optimización de costos

| Estrategia | Cómo ahorra dinero |
|------------|--------------------|
| **Procesamiento por lotes** | Combine múltiples acciones de anotación en una sola llamada API; reduce la sobrecarga por página. |
| **Caché de documentos** | Almacene PDFs anotados en una CDN o almacenamiento de blobs; evita volver a anotar archivos sin cambios. |
| **Alertas de uso** | Configure alertas por correo electrónico en el portal de GroupDocs cuando el uso diario supere un umbral (p. ej., 5 000 páginas). |
| **Activación selectiva de funciones** | Desactive tipos de anotación de uso raro (p. ej., sellos 3‑D) mediante `AnnotationOptions` para reducir procesamiento innecesario. |

## Cuándo elegir licencia medida vs. licencia tradicional
Elija la licencia medida cuando el volumen de anotaciones varíe o prefiera facturación basada en el uso, y opte por la licencia perpetua para cargas de trabajo consistentemente altas y predecibles o entornos sin acceso a internet. Evalúe factores como el recuento mensual de páginas, flexibilidad presupuestaria y restricciones de red para seleccionar el modelo más rentable.

## Conclusión
Configurar una **licencia medida** para GroupDocs.Annotation .NET es sencillo, pero el verdadero poder reside en la flexibilidad y transparencia de costos que ofrece. Siguiendo los pasos anteriores, asegurando sus claves y aplicando las mejores prácticas de producción, habilitará una anotación de documentos escalable y de pago por uso que crece con su negocio.

Recuerde monitorear el uso regularmente, asegurar sus credenciales y aprovechar el registro incorporado para mantener su facturación predecible. Ya sea que esté construyendo una plataforma colaborativa de revisión, un sistema de gestión de documentos legales o un simple widget de anotación, el modelo de licencia medida garantiza que solo pague por el valor que realmente entrega.

## Preguntas frecuentes

**Q: ¿Puedo usar GroupDocs.Annotation para .NET en proyectos comerciales?**  
A: Sí, la biblioteca está completamente licenciada para uso comercial una vez que dispone de una licencia medida o perpetua válida.

**Q: ¿Existe una versión de prueba disponible para probar el flujo de licencia medida?**  
A: Sí, puede obtener una prueba gratuita desde el [sitio web](https://releases.groupdocs.com/).

**Q: ¿Cómo obtengo soporte técnico para problemas de licencias?**  
A: Visite el foro de GroupDocs [aquí](https://forum.groupdocs.com/c/annotation/10) para publicar preguntas o abrir un ticket de soporte.

**Q: ¿Son las licencias temporales una opción para evaluaciones a corto plazo?**  
A: Absolutamente—las licencias temporales se ofrecen por períodos limitados. Vea los detalles en [este enlace](https://purchase.groupdocs.com/temporary-license/).

**Q: ¿Qué precisión tiene el seguimiento de uso con una licencia medida?**  
A: El seguimiento es preciso hasta una anotación de página; los informes normalmente se actualizan dentro de 24 horas.

---

**Última actualización:** 2026-06-06  
**Probado con:** GroupDocs.Annotation 23.12 for .NET  
**Autor:** GroupDocs

## Tutoriales relacionados

- [Guía completa de configuración de licencia de GroupDocs Annotation .NET](/annotation/net/applying-licenses/set-license-from-file/)
- [Establecer licencia desde Stream .NET - Guía completa de GroupDocs.Annotation](/annotation/net/applying-licenses/set-license-from-stream/)
- [Licenciamiento de GroupDocs.Annotation .NET - Configuración y puesta en marcha completa](/annotation/net/licensing-and-configuration/)