# Tu landing page para tu negocio — Landing page

Landing page estática y completamente editable para **Giselle Kaplun**. Su objetivo comercial es vender el servicio de **desarrollo de landing pages** ($450.000): dar a emprendedores y pequeñas empresas una dirección propia en internet, clara, propia y que trabaje como vidriera digital.

## Estructura del proyecto

```
/landing-web/
  index.html     → estructura y contenido de la landing
  styles.css     → estilos (paleta, tipografías, responsive)
  script.js      → menú móvil, preguntas frecuentes, formulario a WhatsApp
  logo.png       → logo del header
  giselle-kaplun.jpg → retrato de la sección "Quién está detrás"
  favicon-*.png / apple-touch-icon.png → íconos del navegador
  README.md      → esta guía
```

- Sin frameworks: solo HTML, CSS y JavaScript puro.
- Tipografías: **DM Serif Display** (títulos) y **Manrope** (textos y botones), cargadas desde Google Fonts.
- Iconos: **Lucide** mediante CDN.
- La landing funciona abriendo directamente el archivo `index.html`, sin servidor.

---

## Cómo abrir la landing localmente

### Opción A: doble clic (la más simple)
1. Abrí la carpeta `landing-web`.
2. Hacé doble clic sobre `index.html`. Se abre en tu navegador y funciona sin instalar nada.

> Nota: la imagen del retrato y los iconos vienen de internet (Lucide, Google Fonts). Si abrís el archivo sin conexión, esos recursos no cargarán, pero el diseño no se rompe gracias al fallback incluido.

### Opción B: con un servidor local (recomendada)

```bash
cd landing-web
python3 -m http.server 8000
```

Luego abrí en el navegador: `http://localhost:8000`

---

## Secciones de la landing

| Sección | `id` | Contenido |
|---|---|---|
| Navbar | — | Links ancla + CTA a WhatsApp |
| 01 · Hero | `inicio` | Propuesta de valor, CTA, badges de entrega |
| 02 · El problema | `problema` | 5 problemas numerados |
| 03 · La solución | `incluye` | Precio, qué incluye, qué NO incluye |
| 04 · Cómo trabajamos | — | 4 pasos del proceso |
| 05 · Quién está detrás | — | Perfil de Giselle |
| 06 · Preguntas frecuentes | `preguntas` | 5 preguntas en acordeón |
| 07 · El próximo paso | `contacto` | Datos de contacto + formulario |
| Footer | — | Marca, enlace a WhatsApp, copyright |

---

## Cómo cambiar textos

Todos los textos están en `index.html`, escritos en español y fáciles de encontrar.

Ejemplos:
- **Título del hero**: buscá `<h1>Tu negocio merece...`.
- **Texto introductorio**: buscá `class="hero-lead"`.
- **WhatsApp y teléfono**: buscá `+54 9 11 4948 7553`.
- **Sección Problema**: buscá `id="problema"`. Cada problema es un `<div>` con `<b>01</b>` a `<b>05</b>`; agregás o quitás uno copiando esa misma estructura.
- **Precio**: buscá `class="price-feature"` y el `<strong>$450.000</strong>`.
- **Qué incluye**: cada línea es `<div><i data-lucide="check"></i> ...</div>` dentro de `.included`.
- **Qué NO incluye**: cada línea es `<div><i data-lucide="x"></i> ...</div>` dentro de `.excluded`.
- **Proceso**: buscá `class="steps"`; hay 4 pasos numerados (`01` a `04`).
- **Preguntas frecuentes**: cada pregunta tiene este formato dentro del bloque FAQ:

```html
<div class="faq-item">
  <button aria-expanded="false">¿Tu pregunta?</button>
  <div class="faq-answer"><p>Tu respuesta.</p></div>
</div>
```

Buscá `class="faq-item"` para ver las 5 existentes. La primera tiene la clase `open` para aparecer desplegada.

---

## Cómo cambiar colores

Todos los colores están definidos como variables al inicio de `styles.css`:

```css
:root {
  --ink: #1f3d2b;        /* Verde oscuro (antes negro tinta) */
  --paper: #f4f0e8;      /* Marfil (fondo claro) */
  --terracotta: #b9573f; /* Terracota (acento) */
  --rose: #e8c9be;       /* Rosa suave */
  --gold: #c49c4a;       /* Dorado */
  --sand: #e3d8c7;       /* Beige arena */
}
```

> El verde oscuro `#1f3d2b` es el mismo "verde profundo" (`--green-deep`) que usa la web [gkaplunconsultora.com.ar](https://gkaplunconsultora.com.ar/). Alcanza con cambiarlo acá y se actualiza en textos, botones, la franja de pilares, el formulario y el footer.

Cambiá el valor de cualquier variable y se actualiza en toda la landing automáticamente.

---

## Cómo cambiar precios

La landing vende un único servicio: **desarrollo de landing page** ($450.000). Los precios y costos relacionados aparecen en:

1. **Precio principal**: buscá `class="price-feature"` y el `<strong>$450.000</strong>`.
2. **Costo del dominio** ($8.500/año): aparece en la lista de "Qué no incluye" y en la primera respuesta del acordeón de preguntas frecuentes.
3. **Costo de ediciones posteriores** ($20.000 por intervención): aparece en "Qué no incluye" y en la respuesta de "¿Qué pasa si necesito cambiar algo después de la entrega?".
4. **Tiempo de entrega** (15 días): aparece en el badge del hero, en la última línea de "Qué incluye", en la respuesta de "¿Cuánto tarda?" y en el círculo de la sección "Cómo trabajamos".

> Si cambiás un valor, no olvides actualizar **todas** las apariciones: el diseño repite los datos clave en varios lugares para que se entiendan sin tener que leer toda la página.

---

## Cómo cambiar imágenes

La landing usa dos imágenes:

### 1. Logo del header
1. El logo vive en la **raíz** de la landing: `logo.png` (reemplazá ese archivo por tu nuevo logo, manteniendo el mismo nombre).
2. Si el archivo falta, el header muestra el círculo vacío sin romper el diseño.
3. En `index.html`, buscá `class="brand-logo"`.

### 2. Retrato de Giselle (sección "Quién está detrás")
1. La foto vive **en la raíz**: `giselle-kaplun.jpg` (al lado de `index.html`). Reemplazá ese archivo por tu nueva foto, manteniendo el mismo nombre.
2. En `index.html`, buscá `class="portrait"`.

Si la imagen no carga, el diseño no se rompe: se mantiene el espacio reservado con un fondo editorial neutro y un mensaje que indica dónde se reemplaza.

---

## Cómo modificar el número de WhatsApp

El número está en dos lugares:

1. **`script.js`** (lo usa el formulario): en la primera línea, cambiá el número manteniendo el formato `http://wa.me/CÓDIGOPAÍSNÚMERO` sin `+`, sin guiones ni espacios:

```js
const WHATSAPP_URL = "http://wa.me/541149487553";
```

2. **`index.html`** (lo usan todos los botones "Quiero...", el menú, el teléfono y el botón flotante `.wa-float`): buscá y reemplazá todas las apariciones de `http://wa.me/541149487553`. El teléfono visible `+54 9 11 4948 7553` también aparece en la sección de contacto.

> **Botón flotante de WhatsApp:** es el círculo verde fijo abajo a la derecha. Está al final del `index.html` (clase `wa-float`) y su estilo (color, tamaño, posición) en `styles.css`. El verde es `#25d366`; podés cambiarlo ahí.

---

## Cómo subir los archivos a un hosting

La landing es un sitio 100% estático, por lo que no necesita backend ni base de datos. Cualquier hosting sirve.

### Opciones simples
- **Netlify / Vercel**: creá una cuenta y arrastrá la carpeta `landing-web` a la zona de "Deploy" (Netlify) o usá su CLI. Obtenés un enlace público en segundos.
- **Hosting clásico (cPanel / Hostgator / DonWeb / etc.)**: subí los archivos de la carpeta con el administrador de archivos o con FTP a la carpeta `public_html`.

### Pasos generales
1. Entrá a la consola/panel de tu hosting.
2. Subí `index.html`, `styles.css`, `script.js`, `logo.png` y `giselle-kaplun.jpg` a la raíz del sitio.
3. Visitá tu dominio para verificar.

> **¿Necesito un certificado SSL?** Sí es recomendable; hoy casi todos los hostings lo ofrecen gratis (Let's Encrypt) y los mensajes de WhatsApp igual funcionan con cualquier hosting.
> **¿Qué pasa con las letras acentuadas?** `index.html` ya está en UTF-8, no hay que hacer nada.

---

## Funcionalidades incluidas

- Todos los botones y CTA abren WhatsApp (`wa.me/541149487553`).
- El formulario no envía datos a ningún backend: al enviarlo, abre WhatsApp con un mensaje predargado de consulta comercial.
- Menú responsive con hamburguesa en pantallas pequeñas.
- Acordeón funcional en preguntas frecuentes (con estados `aria-expanded`).
- Scroll suave entre secciones.
- Iconos con Lucide (CDN).
- Año automático en el footer.
- Accesibilidad básica: textos alternativos, labels en el formulario, contraste y navegación por teclado.
- Diseño responsive en desktop, tablet y mobile, con `prefers-reduced-motion` respetado.
