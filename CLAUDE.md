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

## Stack técnico

- HTML5 + CSS3 + JavaScript vanilla (sin frameworks, sin build tools)
- Un solo archivo `index.html` con CSS y JS embebidos
- Google Fonts (Playfair Display, Lora, Source Sans 3)
- Formspree para el formulario de contacto
- Schema.org JSON-LD para SEO local
