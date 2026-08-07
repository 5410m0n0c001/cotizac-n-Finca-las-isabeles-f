# Cotizador Plantilla Universal — Primavera Events Group

Plantilla **estática** (sin base de datos, sin backend) para generar cotizaciones
personalizadas por cliente. Se usa **clonando este repositorio** por cada
cotización real y editando a mano el contenido específico de ese cliente.

## Flujo de uso

1. Te llega una solicitud de cotización: datos del cliente, venue, precios y servicios a dar.
2. Clonas este repositorio a un repo nuevo (uno por cotización).
3. Editas en `index.html` todo lo marcado entre `[CORCHETES]`: nombre del cliente,
   tipo de evento, venue, datos del recinto, y llenas la tabla de precios
   renglón por renglón con lo que le estás cotizando a ESE cliente.
4. Reemplazas las imágenes/video/audio genéricos (sueltos en la raíz del repo,
   sin subcarpeta `assets/`) por los reales del venue y del evento.
5. Ajustas `TOTAL_BASE` en el `<script>` al monto ya cotizado (el cotizador
   de extras se suma sobre ese número, nunca lo reemplaza).

## Qué incluye

- Preloader con video + audio de fondo (marca Primavera).
- Desglose de cotización editable a mano (igual que las cotizaciones anteriores tipo `cotizacion-presidente-`).
- **Cotizador dinámico de extras**: mismo mecanismo del cotizador de
  [INIT-IDEA](https://5410m0n0c001.github.io/INIT-IDEA/manual-comercial.html#cotizador)
  (checkboxes con `data-price` + recálculo en vivo), pero sin selector de
  plan base — el total ya viene precargado en `TOTAL_BASE`, y el cotizador
  solo SUMA extras opcionales, nunca lo reemplaza. Catálogo con precio real
  verificado: personal, entretenimiento, fotografía/video, coreografía y
  souvenirs. **Ya NO incluye mobiliario** (se quitó a propósito: el catálogo
  de 189 piezas hacía demasiado largo el cotizador). El resumen muestra el
  desglose de cada extra seleccionado.
- **Botones flotantes de redes + compartir** (copiado literal de `antonio-cotizacion`):
  grupo de iconos (Facebook, Instagram, TikTok, LinkedIn, YouTube) con las
  URLs reales de PEG, y botón de compartir nativo (Web Share API con
  fallback a copiar enlace).
- **Estructura obligatoria de `DIRECTIVES.md`** (guía maestra de cotizaciones de PEG):
  - Publicidad: grid de 4 imágenes reales (Bodas, XV Años, Graduaciones, Wedding Planning).
  - Tarjeta de publicidad Expo Boda y Quince Años (copiada literal de `antonio-cotizacion`).
  - Kit Planner: descarga real de `smart_event_planner_pro.xlsx` + `guia_maestra_primavera.pdf`.
  - Video de firma (`firma.mp4`).
  - CSS de impresión alineado a la sección 9 de `DIRECTIVES.md`.
- Botón de imprimir / guardar como PDF, con una vista de impresión limpia
  (solo el desglose de precios, sin fotos ni elementos interactivos).
- Enlaces oficiales reales (paquetes de fotografía, demo de invitación digital).

## Lo que NO hace (a propósito)

- No se conecta a ninguna base de datos ni API — es 100% estático.
- No selecciona el venue por ti — ya viene decidido cuando armas la cotización.
- No reemplaza el sitio web público (primaveraeventsgroup.com) — ese es para
  que el cliente explore venues, fotos y precios generales por su cuenta.

## Pendiente / por mejorar

- Banco de imágenes más completo por venue y por servicio (hoy solo trae
  fotos genéricas de textura — falta acervo real por locación).
- "Portada de revista" nunca se encontró con precio propio verificado —
  no incluir en el cotizador hasta confirmar que existe como servicio real.

## Desarrollo local

Archivo único `index.html`, sin build step:

```bash
python -m http.server 8080
```
