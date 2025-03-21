---
title: head
slug: Web/HTML/Element/head
tags:
  - HTML
  - HTML:Elemento
  - Metadatos de documento HTML
  - Todas_las_Categorías
translation_of: Web/HTML/Element/head
original_slug: Web/HTML/Elemento/head
---
{{HTMLRef}}

El **elemento HTML `<head>`** provee información general (metadatos) acerca del documento, incluyendo su título y enlaces a scripts y hojas de estilos.

| [Categorías de contenido](/es/docs/Web/Guide/HTML/categorias_de_contenido) | Ninguna.                                                                                                                                                                                                                                                                                                                                        |
| -------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Contenido permitido                                                        | Si el elemento es un {{htmlattrxref("srcdoc", "iframe")}} de un {{HTMLElement("iframe")}} , o si la información de título está disponible desde un protocolo de nivel superior, cero o más elementos de metadatos. De otro modo, uno o más elementos de metadatos donde exactamente uno es {{HTMLElement("title")}}. |
| Omisión de etiqueta                                                        | La etiqueta de inicio puede ser omitida si lo primero dentro del elemento head es un elemento. La etiqueta de cierre puede ser omitida si lo primero después del elemento head no es un espacio o un comentario.                                                                                                                                |
| Elementos padre permitidos                                                 | Un elemento {{HTMLElement("html")}}, pues éste es su primer hijo.                                                                                                                                                                                                                                                                      |
| Interfaz DOM                                                               | {{domxref("HTMLHeadElement")}}                                                                                                                                                                                                                                                                                                        |

## Atributos

Este elemento incluye los [atributos globales](/es/docs/Web/HTML/Global_attributes).

- {{htmlattrdef("profile")}} {{obsolete_inline}}
  - : Los URIs de uno o más perfiles de metadatos, separados por un espacio en blanco.

## Ejemplo

```html
<html>
  <head>
    <title>Document title</title>
  </head>
</html>
```

## Notas

Navegadores modernos que cumplen con el estándar HTML5 construyen automáticamente un elemento `<head>` si las etiquetas son omitidas en el código. [Este comportamiento no puede ser garantizado en navegadores antiguos](http://www.stevesouders.com/blog/2010/05/12/autohead-my-first-browserscope-user-test/).

## Especificaciones

| Especificación                                                                                                   | Estatus                          | Comentarios                         |
| ---------------------------------------------------------------------------------------------------------------- | -------------------------------- | ----------------------------------- |
| {{SpecName('HTML WHATWG', 'semantics.html#the-head-element', '&lt;head&gt;')}}         | {{Spec2('HTML WHATWG')}} | Sin cambios desde la última versión |
| {{SpecName('HTML5 W3C', 'document-metadata.html#the-head-element', '&lt;head&gt;')}} | {{Spec2('HTML5 W3C')}}     | Atributo `profile` obsoleto         |
| {{SpecName('HTML4.01', 'struct/global.html#h-7.4.1', '&lt;head&gt;')}}                     | {{Spec2('HTML4.01')}}     |                                     |

## Compatibilidad de navegadores

{{Compat("html.elements.head")}}

## Véase también

- Elementos que pueden ser usados dentro de un elemento `<head>:` {{HTMLElement("title")}}, {{HTMLElement("base")}}, {{HTMLElement("link")}}, {{HTMLElement("style")}}, {{HTMLElement("meta")}}, {{HTMLElement("script")}}, {{HTMLElement("noscript")}}
