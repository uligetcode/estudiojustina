# Justina Abogados — CLAUDE.md

Guía de trabajo para gestionar el sitio web desde esta carpeta.

---

## Contexto del proyecto

Sitio web estático (landing page) para **Justina Abogados**, estudio jurídico de Elizabeth Ana María Silva, CABA.

- **URL producción:** https://estudiojustina.com
- **Repo GitHub:** https://github.com/uligetcode/estudiojustina
- **Hosting:** GitHub Pages (rama `main`, carpeta raíz)
- **Dominio:** gestionado en Squarespace (ex Google Domains)

---

## Estructura de archivos

```
estudiojustina-web/
├── index.html          ← landing page principal (todo en un solo archivo)
├── assets/
│   ├── logos/          ← SVGs del sistema de identidad visual
│   └── fotos/          ← Fotos de Elizabeth
├── CNAME               ← dominio personalizado (no tocar)
├── .gitignore
├── CLAUDE.md           ← este archivo
└── docs/
    ├── datos-negocio.md    ← datos del estudio (contacto, servicios, precios)
    ├── identidad-visual.md ← paleta, tipografías, guía de estilo
    └── prompt-landing.md   ← prompt original para regenerar/modificar la landing
```

---

## Datos del negocio

Ver [docs/datos-negocio.md](docs/datos-negocio.md) para referencia completa.

Resumen rápido:
- **Abogada:** Elizabeth Ana María Silva
- **Tel:** +54 11 6956-1265
- **WhatsApp Business:** +54 11 7826-0592
- **Email:** elizabeth.silva@estudiojustina.com
- **Dirección:** Cerrito 1054, 5to Piso, CABA (C.P. 1010)
- **Horario:** Lunes a Viernes 9:00–18:00

---

## Identidad visual

Ver [docs/identidad-visual.md](docs/identidad-visual.md) para referencia completa.

Paleta principal (variables CSS en `index.html`):
```
--navy:     #1C1F2E   ← color principal de fondo/header
--burgundy: #6B2C45   ← color de acento principal
--gold:     #C9A96E   ← color de acento secundario
--cream:    #F7F4EF   ← fondo claro
```

Tipografías:
- Títulos: **Playfair Display** (serif, elegante)
- Cuerpo: **Source Sans 3** (sans-serif, legible)
- Subtítulos: **Lora** (serif, transiciones)

---

## Cómo hacer cambios en el sitio

### Flujo estándar
```bash
# 1. Editá index.html (o cualquier archivo)
# 2. Subí los cambios
git add .
git commit -m "descripción breve del cambio"
git push
# El sitio se actualiza en ~1 minuto
```

### Tipos de cambios frecuentes

**Cambiar un texto:**
Buscá el texto en `index.html` y editalo directamente. El archivo está comentado por secciones (`<!-- HERO -->`, `<!-- SERVICIOS -->`, etc.).

**Cambiar colores:**
Las variables CSS están al inicio del `<style>` en `index.html`. Modificá las variables en `:root {}`.

**Agregar una foto:**
1. Copiá la foto a `assets/fotos/`
2. Referenciarla en el HTML con `src="assets/fotos/nombre-foto.jpg"`

**Cambiar logos:**
Los SVGs están en `assets/logos/`. Reemplazá el archivo manteniendo el mismo nombre, o actualizá la referencia en el HTML.

---

## Cómo pedir cambios de diseño a Claude

> **IMPORTANTE:** Siempre usar el skill `/frontend-design` para cualquier cambio visual en el sitio. Escribir `/frontend-design` al inicio del pedido o al comienzo de la sesión.

Cuando quieras modificar el diseño, podés pedirle a Claude directamente. Para que el resultado sea coherente con el sitio actual, siempre mencioná:

- Qué sección querés modificar
- Qué querés cambiar (texto, color, layout, nueva sección, etc.)
- Si tenés referencia visual o descripción de lo que buscás

Claude leerá `index.html` y los docs de esta carpeta para mantener coherencia.

### Sistema de logos

Los archivos en `assets/logos/` siguen esta convención:
- `isotipo-fondo-*.svg` → solo el isotipo circular con la J (el correcto a usar)
- `wordmark-fondo-*.svg` → solo el texto "JUSTINA ABOGADOS"
- `logo-horizontal-fondo-*.svg` → versión combinada (no usar, el isotipo puede diferir)
- `logo-apilado-fondo-*.svg` → versión apilada (para footer)

**Regla:** En el nav, siempre combinar `isotipo-fondo-navy.svg` + `wordmark-fondo-navy.svg` por separado. No usar `logo-horizontal-fondo-navy.svg`.

---

## Checklist antes de publicar cambios

- [ ] El sitio se ve bien en mobile (375px) — usá F12 en Chrome → modo mobile
- [ ] Los links de WhatsApp funcionan con el número correcto
- [ ] No hay textos de ejemplo o placeholders visibles
- [ ] Los colores y tipografías son coherentes con la identidad visual
- [ ] Corrí Lighthouse (F12 → Lighthouse) y el score de Performance y SEO está en verde

---

## Changelog

### 2026-03-28 — Primera sesión de mejoras post-lanzamiento

**WhatsApp Business**
- Número actualizado: `5491178260592` (WhatsApp Business oficial)
- Mensaje inicial: `"Hola! Me gustaría hacer una consulta con el estudio."` — natural, deja apertura para bot de recepción (pendiente de implementar)

**Google Maps**
- Link oficial de Google Business: `https://share.google/4Beh5J4lklKKfh1wc`
- Usado en: botón "Ver en Google Maps" de sección Ubicación + item de dirección en Contacto
- El embed del mapa en `<iframe>` sigue usando URL estándar de Google Maps (share.google no es embebible)

**Sistema de logos**
- SVGs editados para eliminar `<rect fill="#1C1F2E">` de fondo (isotipo, wordmark, apilado)
- Isotipo del nav: **inlineado como SVG** en el HTML → usa Playfair Display cargado por la página → J idéntica al diseño original
- Footer logo apilado: también inlineado
- Nav: solo muestra el isotipo circular (wordmark removido del nav)
- Wordmark aparece grande en el hero como brand statement principal
- Ver regla en sección "Sistema de logos" más arriba

**Foto**
- `assets/fotos/foto-a.jpeg` en sección "Sobre el Estudio" (antes sin imagen)
- Fotos renombradas de "WhatsApp Image..." a `foto-a.jpeg` … `foto-j.jpeg`

**Nueva sección: Ubicación**
- Franja entre FAQ y Contacto
- Split: info institucional (dirección, zona, horario) + mapa prominente
- "En el corazón del microcentro porteño, a pasos del Palacio de Tribunales"
- CTA "Ver en Google Maps" → link oficial de Google Business
- Mapa movido de fondo de Contacto a esta nueva sección
- Agregado "Ubicación" al menú de navegación

**Formulario de contacto**
- Formspree ID: `xpqoqbnr` (cuenta: `ulises.silva@estudiojustina.com`)
- CC automático a: `elizabeth.silva@estudiojustina.com`
- Asunto automático: "Nueva consulta — Justina Abogados"
- Submit vía AJAX: no redirige a Formspree, muestra confirmación inline
- Estado de éxito: "Consulta recibida / 24hs hábiles"

**Favicon**
- Archivo: `favicon.png` en raíz del repo (isotipo circular con J)
- También declarado como `apple-touch-icon`

---

### 2026-04-09 — Segunda sesión de mejoras

**Áreas de práctica — nuevo contenido**
- Orden nuevo: Daños, Salud, Familia, Sucesorio, Laboral, Societario
- "Amparos de Salud" → "Derecho a la Salud" (nuevo contenido y nombre)
- "Derecho Comercial" → "Derecho Societario" (foco en IGJ y estructura societaria)
- "Cartas Documento" → "Derecho Sucesorio" (testamentos, donaciones, inscripción de bienes)
- Derecho de Familia: texto actualizado con compensaciones económicas y enfoque interdisciplinario
- Derecho Laboral: texto actualizado con SECLO, Ministerio de Trabajo, intercambio telegráfico

**Cards expandibles en servicios**
- Cada card muestra resumen corto + botón "Ver más" que expande el texto completo
- Animación CSS `max-height` transition (0.48s)
- Precios (`svc-fee`) eliminados de todas las cards
- Badge "Primera consulta gratuita · Sin compromiso" debajo del grid
- Dropdown del formulario de contacto actualizado con las nuevas áreas

**Reducción de "+20 años" repetitivo**
- Meta description: "con amplia trayectoria profesional"
- OG description: "Asesoramiento jurídico integral... Visión estratégica del conflicto."
- "Por Qué Elegirnos": "Trayectoria probada en el fuero porteño"
- Schema.org JSON-LD: mantenido sin cambios

**Testimonios — swipe táctil y mouse drag**
- Touch: swipe horizontal > 50px avanza/retrocede slide + resetea autoplay
- Mouse: drag horizontal > 50px igual comportamiento
- Cursor `grab`/`grabbing` visual en el carrusel

**Animación scroll en servicios — reveal suave**
- Observer dedicado para `.svc-reveal` (threshold 0.15, rootMargin -60px)
- Delays escalonados por card: svc-d0 (0s) → svc-d5 (0.60s)
- Evita el efecto de "aparición súbita" que ocurría con el grid de columnas múltiples

---

### 2026-04-16 — Tercera sesión: ajustes de redacción

**Tuteo en el hero**
- "Defendemos sus derechos" → "Defendemos tus derechos"

**Sobre el Estudio**
- Quitada la palabra "legal" de "todo conflicto legal" → "todo conflicto"

**Servicios — Derecho de Daños**
- "reparación que merecés" → "reparación integral que merecés"

**FAQ — honorarios a resultado**
- "lo recuperado, según la complejidad" → "lo reconocido en el acuerdo privado, judicial o por sentencia"

**Menú de navegación**
- "FAQ" → "Preguntas frecuentes" (en desktop y mobile)

---

## Stack técnico

- HTML5 + CSS3 + JavaScript vanilla (sin frameworks, sin build tools)
- Un solo archivo `index.html` con CSS y JS embebidos
- Google Fonts (Playfair Display, Lora, Source Sans 3)
- Formspree para el formulario de contacto
- Schema.org JSON-LD para SEO local
