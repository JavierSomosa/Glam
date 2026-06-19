# CLAUDE.md — Glam Hair Design

Contexto del proyecto para Claude Code. Leer antes de hacer cualquier cambio.

## Qué es este proyecto

Sitio web multi-página para **Glam Hair Design**, una peluquería premium en Avellaneda, Buenos Aires, con 3 sedes. El sitio combina presencia institucional (servicios, sedes, equipo, reserva de turnos) con una sección de cursos (presenciales y online).

Cliente real, en producción. Los cambios deben ser cuidadosos y mantener la consistencia visual existente.

## Stack

- **HTML/CSS/JavaScript puro** — sin frameworks, sin build, sin npm
- Sitio estático, multi-página (cada sección es su propio `.html`)
- Se sirve estático (hosting tipo Render Static Site)
- Para probar localmente: `npx serve .` y abrir el localhost (NO abrir los HTML con doble click, las features que llaman APIs externas no funcionan con `file://`)

## Estructura de archivos

```
Glam desing/
├── index.html            # Home — hero, 3 sedes con mapas, preview de secciones
├── quienes-somos.html    # Equipo dividido por sede, valores, mención Glam & Coffee
├── servicios.html        # Grilla de servicios
├── turnos.html           # Reserva vía Fresha (botón a nueva pestaña, no iframe)
├── cursos.html           # Cursos presenciales (Nivel 1, Nivel 2, Perfeccionamiento)
├── cursos-online.html    # Cursos online + modal login/registro (Supabase)
├── css/
│   └── style.css         # TODOS los estilos del sitio acá
├── js/
│   └── main.js           # JS compartido (navbar, menú mobile, etc.)
└── assets/
    ├── hero-home.png
    ├── cursos-hero.png
    └── team-photo.png
```

## Identidad visual (NO cambiar sin pedido explícito)

- **Negro:** `#0A0A0A`
- **Dorado:** `#C9A84C`
- **Blanco:** `#FAFAFA`
- Estética: elegante, minimalista, femenina, premium
- Tipografía: serif para títulos, sans-serif para cuerpo
- Logo: "Glam" en script + "HAIR DESIGN" en versalitas

## Las 3 sedes

- **Glam Avellaneda** — Gral. Lavalle 92
- **Glam Gerli** — Lacarra 1495
- **Glam & Coffee** — Av. Mitre 5943 (es una sede que además sirve café, NO una cafetería aparte)

## Integraciones

- **Fresha** (turnos): el botón abre Fresha en nueva pestaña. NO usar iframe (lo bloquea por CORS).
  Link: `https://www.fresha.com/es/providers/glam-hair-design-t6yixtg3`
- **Supabase** (auth en cursos-online.html): registro/login de alumnos. Solo usar la **anon key** pública en el frontend, NUNCA la service_role/secret.
- **Instagram:** `https://www.instagram.com/glam_hairdesign`

## Convenciones

- Todos los estilos van en `css/style.css` — no usar `<style>` inline ni CSS por archivo
- JS compartido va en `js/main.js`
- El sitio es responsive mobile-first; mantener navbar fija con hamburger en mobile
- Español rioplatense en todos los textos visibles

## Estado actual

- Secciones institucionales (1-5): **diseño aprobado por el cliente**
- Cursos online: modal de login/registro conectado a Supabase Auth (registro funciona, llega email de confirmación). Falta pagos (MercadoPago) y acceso a videos (Vimeo) — eso es fase 2, NO está contratado todavía.

## Reglas para cambios

- No tocar la paleta ni la tipografía sin pedido explícito
- No agregar dependencias ni frameworks
- No reescribir secciones aprobadas salvo que se pida
- Antes de un cambio grande, confirmá qué archivos vas a tocar
- Mantener consistencia con lo que ya existe
