# Jessica Quiróz Frontend

Frontend Astro para la landing y flujo de pre-agendamiento de Jessica Quiróz.

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
PUBLIC_API_V1_PATH=/api/v1
PUBLIC_APP_TIMEZONE=America/Santiago
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

El frontend sigue el contrato de `BACKEND_CONTRACT.md`:

1. `GET /api/v1/services`
2. `GET /api/v1/availability?serviceId=<id>&from=<iso>&to=<iso>&timezone=America/Santiago`
3. `POST /api/v1/pre-reservations`
4. Guardar `preReservation.id` y `customerToken` en `sessionStorage`
5. `POST /api/v1/pre-reservations/:id/images` con `X-Reservation-Token`
6. `POST /api/v1/pre-reservations/:id/payment` con `X-Reservation-Token`
7. Redirigir a `initPoint` o `sandboxInitPoint`
8. Al volver desde Mercado Pago, consultar `GET /api/v1/pre-reservations/:id/payment-status`

El frontend publico no debe usar `X-Admin-Api-Key` ni `X-Internal-Job-Secret`.

## Rutas de retorno de pagos

Configurar estas URLs como `back_urls` en Mercado Pago, respetando el dominio final y el `base` de GitHub Pages:

```txt
success: https://daranedag.github.io/jessiquiroz-frontend/pagos/exito
pending: https://daranedag.github.io/jessiquiroz-frontend/pagos/pendiente
failure: https://daranedag.github.io/jessiquiroz-frontend/pagos/error
```

Las rutas tambien aceptan los parametros que agregue Mercado Pago y consultan el estado con `GET /pre-reservations/:id/payment-status` cuando existe la informacion local de la pre-reserva en `sessionStorage`.

## Endpoints Consumidos

Todos los endpoints se construyen con:

```txt
PUBLIC_API_BASE_URL + PUBLIC_API_V1_PATH
```

Endpoints publicos usados por el frontend:

```txt
GET  /services
GET  /availability
POST /pre-reservations
POST /pre-reservations/:id/images
POST /pre-reservations/:id/payment
GET  /pre-reservations/:id/payment-status
```

## Deploy

El sitio se publica en GitHub Pages con el workflow `.github/workflows/deploy.yml`.

El deploy se ejecuta automáticamente en cada push a `main`, instala dependencias con pnpm, genera el build de Astro y publica el contenido de `dist`.

La configuración actual asume esta URL de GitHub Pages:

```text
https://daranedag.github.io/jessiquiroz-frontend/
```

En GitHub, configurar `Settings` -> `Pages` -> `Build and deployment` -> `Source` como `GitHub Actions`.

Si más adelante se usa dominio propio, hay que actualizar `site` y quitar `base` en `astro.config.mjs`.
