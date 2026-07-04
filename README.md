# Jessica Quiroz Frontend

Frontend Astro para la landing y flujo de pre-agendamiento de Jessica Quiroz.

## Stack

- Astro 5
- Tailwind CSS
- pnpm como único gestor de paquetes
- Backend externo en Render como único punto de contacto para calendario, archivos y pagos
- GitHub Pages + GitHub Actions para publicación

## Requisitos

- Node.js compatible con Astro
- pnpm `10.12.1`

Este proyecto no debe usar Bun ni npm para instalar dependencias. Si se agregan paquetes, usar siempre `pnpm add`.

## Variables de entorno

Crear un archivo `.env` local con las variables públicas necesarias para el frontend:

```sh
PUBLIC_API_BASE_URL=https://tu-backend-en-render.onrender.com
PUBLIC_BOOKING_AVAILABILITY_PATH=/calendar/availability
PUBLIC_BOOKING_UPLOAD_PATH=/uploads
PUBLIC_BOOKING_PREBOOK_PATH=/appointments/prebook
PUBLIC_BOOKING_CONFIRM_PAYMENT_PATH=/appointments/confirm-payment
```

Las variables con prefijo `PUBLIC_` quedan expuestas al navegador. No guardar secretos, tokens privados ni credenciales de MercadoPago en el frontend.

Para producción en GitHub Pages, crear las mismas variables en GitHub como repository variables:

`Settings` -> `Secrets and variables` -> `Actions` -> `Variables`.

## Comandos

```sh
pnpm install
pnpm run dev
pnpm run build
pnpm run preview
```

## Flujo de agendamiento

El frontend solicita horarios disponibles al backend, toma los datos del cliente, sube archivos, crea una pre-reserva y redirige al pago de MercadoPago. Al volver desde el pago exitoso, confirma la reserva contra el backend.

El contrato exacto de endpoints se puede ajustar en `src/components/BookingFlow.astro` cuando estén definidas las rutas finales del backend.

## Deploy

El sitio se publica en GitHub Pages con el workflow `.github/workflows/deploy.yml`.

El deploy se ejecuta automáticamente en cada push a `main`, instala dependencias con pnpm, genera el build de Astro y publica el contenido de `dist`.

La configuración actual asume esta URL de GitHub Pages:

```text
https://daranedag.github.io/jessiquiroz-frontend/
```

En GitHub, configurar `Settings` -> `Pages` -> `Build and deployment` -> `Source` como `GitHub Actions`.

Si más adelante se usa dominio propio, hay que actualizar `site` y quitar `base` en `astro.config.mjs`.
