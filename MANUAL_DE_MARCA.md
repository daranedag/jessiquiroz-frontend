# Manual de marca — Jessica Quiróz

> Versión 1.0 · Basado en la implementación actual del sitio. Este documento registra el sistema visual vigente; no añade reglas de marca que aún no existan en el producto.

## Esencia visual

La identidad comunica bienestar holístico, cercanía y calma. Combina una base clara y serena con acentos orgánicos: verde para confianza, lila y rosa para sensibilidad, y amarillo para la acción principal. La interfaz debe sentirse liviana, cálida y humana, con mucho espacio en blanco, formas redondeadas y fotografías luminosas.

## Activos de marca

| Activo | Archivo | Uso actual |
| --- | --- | --- |
| Logotipo a color | [`public/logo_color.png`](public/logo_color.png) | Uso predeterminado en encabezado, pie de página y favicon. |
| Logotipo blanco | [`public/logo_blanco.png`](public/logo_blanco.png) | Variante para contextos oscuros; se activa con el modo oscuro. |
| Favicon vectorial | [`public/favicon.svg`](public/favicon.svg) | Recurso disponible; el sitio actualmente referencia el logotipo a color como favicon. |

El logotipo se muestra junto al nombre **Jessica Quiróz**. En el encabezado se usa a `64 px` de alto y en el pie a `40 px`. No existen todavía reglas definidas de área de seguridad, tamaño mínimo ni versiones monocromáticas adicionales; deberán acordarse antes de usarlas en nuevas piezas.

## Paleta cromática

Los colores son tokens CSS definidos en [`src/styles/global.css`](src/styles/global.css) y consumidos desde Tailwind. Las transparencias que se indican responden a usos actuales de la interfaz.

| Token | Hex | RGB | Rol y usos actuales |
| --- | --- | --- | --- |
| `background` | `#E6F4F9` | `230, 244, 249` | Fondo global azul muy claro; encabezado translúcido, fondos suaves y pantalla de pago. |
| `background-alt` | `#E8DCCB` | `232, 220, 203` | Fondo cálido alternativo para secciones, líneas de tiempo y estados de contexto. |
| `primary` | `#5B8C5A` | `91, 140, 90` | Color principal: identidad, enlaces, iconos, estados activos, bordes y CTA secundarios. |
| `secondary` | `#8E7DBE` | `142, 125, 190` | Acento editorial: etiquetas de sección, citas, avatares y elementos decorativos. |
| `accent` | `#F2B5C4` | `242, 181, 196` | Acento suave: destellos decorativos y una variante de tarjetas de reflexión. |
| `cta` | `#F4C430` | `244, 196, 48` | Llamada a la acción principal: botones de reserva y estado de pago pendiente. |
| `text-main` | `#2E2E2E` | `46, 46, 46` | Texto principal, especialmente sobre fondos claros y botones amarillos. |
| Blanco de interfaz | `#FFFFFF` | `255, 255, 255` | Superficie de tarjetas, formularios, menús y CTA secundarias. |

### Aplicación de color

- Usar `primary` para acciones y elementos de navegación que no sean la conversión principal.
- Reservar `cta` para acciones de reserva o pago. Sus botones usan texto `text-main`, sombra y, en la mayoría de los casos, anillo `cta` al 70 %.
- Usar `secondary` en sobrelíneas o etiquetas editoriales en mayúsculas; no compite con la acción principal.
- `background-alt` se aplica habitualmente al 40–60 % de opacidad. `primary` aparece en bordes al 10–30 % y en fondos de estado al 10 %.
- Los estados semánticos de error usan rojo del sistema (`red-50`, `red-200`, `red-700`); no forman parte de la paleta de marca.

## Tipografía

| Rol | Familia | Pesos cargados | Uso |
| --- | --- | --- | --- |
| Display | `Cormorant Garamond`, serif | 400, 600, 400 italic | Nombre de marca, titulares y citas destacadas. |
| Texto | `Montserrat`, sans-serif | 300, 400, 500, 600 | Navegación, cuerpo, botones, formularios y etiquetas. |

Las fuentes se cargan desde Google Fonts en las páginas. La configuración de Tailwind expone `font-display` y `font-sans`.

### Jerarquía tipográfica actual

| Elemento | Estilo base | Ajuste responsive / tratamiento |
| --- | --- | --- |
| Título principal | Display, `text-4xl` | Sube a `5xl` en `sm` y `6xl` en `lg`; interlineado ajustado. |
| Títulos de sección | Display, `text-3xl` | Sube a `4xl` en `sm`. |
| Títulos de tarjetas | Sans, `text-lg` o `text-xl`, semibold/bold | Breves y de alto contraste. |
| Cuerpo | Sans, `text-sm` | Color gris pizarra (`slate-600`) y lectura relajada; el hero alcanza `text-lg` en escritorio. |
| Sobrelínea / etiqueta | Sans, `text-xs`, semibold | Mayúsculas, tracking `0.3em`, normalmente en `secondary`. |
| Botones y navegación | Sans, `text-xs`, bold/semibold | Mayúsculas y tracking `0.2em`. |

## Retícula y composición

- Contenedor principal: `max-w-7xl` con `px-6`. Las secciones de contenido más concentrado usan `max-w-4xl`, `5xl` o `6xl`.
- Ritmo vertical: las secciones regulares usan `py-16`; el bloque de contacto y las pantallas de pago amplían a `py-24`.
- El encabezado es fijo, de `80 px` de alto, y el contenido principal compensa con `pt-20`.
- Las tarjetas se organizan en una columna móvil, dos columnas desde `sm` o `md`, y tres desde `lg` según el contenido.
- El hero emplea dos columnas desde `md`; se prioriza siempre la lectura vertical en móvil.

No hay una escala de espaciado de marca propia: se utiliza la escala estándar de Tailwind. Al extender el sitio, conservar los valores ya recurrentes (`gap-4`, `gap-6`, `gap-8`, `p-6`, `p-8`) para mantener consistencia.

## Componentes visuales

### Encabezado y navegación

- Fondo `background` con 80 % de opacidad, desenfoque y borde inferior `primary/10`.
- Navegación de escritorio en mayúsculas; el hover cambia a `primary`.
- El menú desplegable es una tarjeta blanca con radio `2xl`, borde `primary/10` y sombra `xl`.
- En móvil se reemplaza por un botón de borde verde y menú expandible.

### Botones

| Variante | Construcción | Uso |
| --- | --- | --- |
| Principal / reserva | Píldora `rounded-full`, fondo `cta`, texto `text-main`, `px-7` u `8`, `py-3`; sombra `lg` | Reservar sesión, ir al pago, acciones de conversión. |
| Principal reforzado | Igual a la anterior, con `ring-2 ring-cta/70` y sombra mayor al hover | Reserva desde header, contacto, formulario y retornos de pago. |
| Secundario | Píldora blanca, borde `primary` o `primary/20`, texto `primary` | Ver trabajos, volver al inicio, acciones alternativas. |
| Navegación móvil | Píldora con borde `primary`, texto `primary` | Abrir menú y submenú. |

Los botones usan transición; al pasar el cursor se elevan `-translate-y-0.5` o cambian a fondo `primary` cuando son secundarios. Se acompañan de iconos Material Icons cuando el significado se beneficia de ello.

### Tarjetas

- Base: fondo blanco, radio `rounded-3xl` (`24 px`) y sombra suave (`shadow-sm`).
- Contenido habitual: `p-6`; testimonios y algunas experiencias usan `p-8`.
- Las tarjetas de formulario y estado reducido usan `rounded-2xl` (`16 px`).
- Las imágenes de tarjeta redondean solo los bordes superiores (`rounded-t-3xl`) y emplean `object-cover`.
- Las reflexiones incorporan giro 3D al hover; su reverso puede ser `primary`, `secondary` o `accent` al 90 %.

### Formularios y estados

- Campos blancos con radio `2xl`, borde `primary/20`, relleno horizontal y vertical generoso.
- Foco: borde `primary` y anillo `primary/10` de cuatro unidades.
- La acción de envío mantiene el patrón de botón principal y ocupa todo el ancho.
- Los mensajes neutros son blancos con borde `primary/10`; el éxito usa `primary/10`; el error usa la escala roja de interfaz; pendiente usa `cta/15`.

### Carruseles y línea de tiempo

- Los carruseles mantienen tarjetas blancas y separación `gap-8`; avanzan automáticamente, admiten arrastre y se detienen durante la interacción.
- La línea de tiempo usa una línea central de `2 px` en `primary/30`, nodos verdes y anillo `background-alt`.

## Iconografía e imágenes

- Iconos: **Material Icons** con trazo/estilo estándar de la librería. Se usan para navegación, categorías, información y estados, casi siempre en `primary`.
- Fotografía: imágenes de bienestar, tratamientos y retratos con iluminación suave y aspecto natural. Predominan encuadres verticales o rectangulares con recorte `object-cover`.
- Decoración: masas circulares desenfocadas en `accent/40` y `secondary/30`; son apoyo visual y no deben obstaculizar la legibilidad.

## Movimiento e interacción

- Desplazamiento suave activado para los enlaces internos.
- Transiciones breves en color, sombra y posición para botones y navegación.
- Tarjetas de reflexión: giro de 180° al hover.
- Carruseles: transición de desplazamiento de `700 ms` con curva `ease-in-out` y avance automático cada `3.5 s`.

Al crear interacciones nuevas, mantener el movimiento sutil y funcional. Considerar una alternativa sin movimiento para personas con `prefers-reduced-motion`, que aún no está implementada de forma global.

## Accesibilidad y contraste

- La tipografía principal sobre fondos claros usa `text-main`; los textos secundarios usan tonos `slate`.
- Los botones de CTA mantienen texto oscuro sobre amarillo. Los botones verdes usan texto blanco.
- Las imágenes informativas incluyen texto alternativo descriptivo y los controles de navegación exponen atributos `aria` básicos.
- Antes de introducir combinaciones nuevas de color, validar el contraste de texto, estados de foco y legibilidad en dispositivos móviles.

## Referencia de implementación

La fuente técnica de estos tokens es [`src/styles/global.css`](src/styles/global.css), complementada por [`tailwind.config.cjs`](tailwind.config.cjs). Si se modifica cualquiera de esos archivos, actualizar este manual en el mismo cambio para que siga siendo la referencia vigente.
