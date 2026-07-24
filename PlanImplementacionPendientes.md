# Plan de puesta en producción — pendientes reales

Este documento vincula las respuestas entregadas con cada requisito de `PlanImplementacion.md`. Solo incluye trabajo que sigue pendiente; las decisiones cerradas quedan registradas para evitar pedirlas otra vez.

## Decisiones ya incorporadas

### Identidad de marca

- Nombre comercial y legal: **Jessica Quiróz**.
- Logotipos, colores y estilo visual: aprobados tal como están.
- Dominio objetivo: `jessicaquiroz.cl`, pendiente de confirmación y disponibilidad/propiedad por parte de la clienta.
- El frontend ya usa la escritura oficial en encabezado, pie de página y páginas de pago.

### Datos de contacto

- Modalidad: solo presencial.
- Horario general: 09:00 a 17:00 hrs.
- La dirección y el teléfono/WhatsApp se entregarán únicamente una vez pagada y confirmada la reserva.
- El correo e Instagram provisionales se retiraron de la interfaz pública.

### Formulario de reserva

- Campos confirmados: nombre, correo, teléfono y mensaje.
- Se permiten imágenes adjuntas, de forma opcional.
- Ya existen las rutas de retorno de pago: éxito, pendiente y error.

### Dominio, publicación y administración

- El frontend continuará en GitHub Pages.
- Se creará una organización de GitHub para alojar los repositorios.
- El panel de administración de contenidos se realizará en Retool con acceso a la base de datos.

## Pendientes

### Identidad de marca

- [ ] Confirmar la compra, propiedad y DNS de `jessicaquiroz.cl`.
- [ ] Crear el manual de marca a partir de la identidad visual aprobada.
- [ ] Cuando el dominio esté listo, configurar GitHub Pages, `site` y `base` de Astro, además de las URLs de retorno de Mercado Pago.

### Datos de contacto

- [ ] Definir el correo oficial para comunicaciones operativas y legales. No se publicará en el sitio hasta recibirlo.
- [ ] Definir usuario y enlace de Instagram, si se incorporará.

### Contenido del sitio

- [ ] Entregar o aprobar biografía, historia personal, estudios, certificaciones, método y servicios reales.
- [ ] Validar o reemplazar textos de reflexiones, tratamientos y afirmaciones de resultados físicos o de bienestar.
- [ ] Redactar descripción para buscadores; puede generarse con IA y requerirá aprobación de la clienta.
- [ ] Definir palabras clave y servicios prioritarios para SEO.
- [ ] Confirmar el alcance geográfico inicial: Santiago, Región Metropolitana.

### Fotografías y testimonios

- [ ] Entregar fotografías para portada, secciones y sesiones; confirmar sus derechos de publicación.
- [ ] Decidir si se usarán fotografías de antes y después y, de ser así, reunir autorizaciones explícitas.
- [ ] Entregar testimonios reales, con las iniciales que se mostrarán.
- [ ] Obtener autorización de publicación de cada testimonio.
- [ ] Crear o entregar imagen para compartir en WhatsApp y redes sociales.

### Formulario de reserva

- [ ] Definir qué imágenes pueden adjuntarse y su finalidad; reflejarlo junto al campo de carga.
- [ ] Redactar y aprobar el consentimiento específico para datos e imágenes. Un checkbox solo es suficiente si enlaza a un texto claro que describa finalidad, base de consentimiento, conservación, acceso y eliminación; no reemplaza la política de privacidad.
- [ ] Definir instrucciones previas a la reserva.
- [ ] Definir mensajes definitivos para pagos aprobados, pendientes y rechazados.
- [ ] Definir el canal de soporte para incidencias de pago o reserva, sin exponer datos que deban comunicarse tras la confirmación.

### Privacidad y condiciones

- [ ] Generar con IA un borrador de política de privacidad y revisarlo antes de publicar.
- [ ] Generar con IA un borrador de términos y condiciones y revisarlo antes de publicar.
- [ ] Consultar y definir políticas de cancelación, reprogramación y devoluciones.
- [ ] Definir el plazo de conservación de datos e imágenes.
- [ ] Generar procedimiento para solicitar eliminación de información.
- [ ] Consultar a la clienta el alcance de los servicios de bienestar y redactar el descargo correspondiente.
- [ ] Definir los datos legales o tributarios que aparecerán en el sitio.

### Dominio, publicación y medición

- [ ] Crear la organización de GitHub y transferir o publicar el repositorio allí.
- [ ] Decidir si se implementará analítica y crear/configurar la cuenta elegida.
- [ ] Definir banner de cookies: no es necesario mientras no se usen cookies no esenciales. Si se activa analítica o marketing que use cookies o tecnologías equivalentes, implementar consentimiento previo y el banner.
- [ ] Establecer la fecha prevista de publicación.

### Posicionamiento y difusión

- [ ] Crear metadatos SEO definitivos una vez aprobados los contenidos y palabras clave.
- [ ] Crear metadatos sociales (Open Graph/Twitter) y asociar la imagen social definitiva.
- [ ] Configurar el panel Retool y sus permisos cuando el backend y la base de datos estén disponibles.
