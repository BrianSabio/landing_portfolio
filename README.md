# PFO1 — Landing de Portafolio Personal

## Descripción

Este proyecto es una **landing page responsiva** que presenta el perfil profesional de Brian Ezequiel Sabio, desarrollador Backend especializado en Java, C# y APIs RESTful. La página funciona como portafolio personal, mostrando habilidades técnicas, proyectos destacados y una forma de contacto directo.

**Objetivo:** Crear una presencia web profesional que comunique de manera clara quién soy, qué tecnologías domino y cómo contactarme, manteniendo un diseño minimalista y funcional.

---

## Información del Proyecto

- **Materia:** Desarrollo de Sistemas Web Front End 2026 — 2do Cuatrimestre
- **Tipo:** Proyecto de Formación Obligatoria (PFO1)
- **Fecha de Entrega:** 24/08/2026
- **Repositorio:** https://github.com/BrianSabio/landing_portfolio
- **URL en Vercel:** *(pendiente de despliegue)*

---

## Decisiones de Diseño & Código

### 1. Identidad Visual: Estética Terminal/CLI

**Concepto:** Partiendo del perfil Backend del desarrollador (uso diario de Bash, PowerShell, Git), elegí una estética inspirada en **terminal/línea de comandos** como hilo conductor visual. Esto comunica "seriedad técnica" sin perder modernidad.

**Implementación:**
- **Tipografía monoespaciada (Fira Code)** para tags de skills y navegación, simulando comandos (`$ spring-boot`, `~/about`)
- **Logo personalizado** `[BS]` en formato monoespaciado en lugar de avatar
- **Ventana terminal visual** en sección hero con barra de colores (rojo, amarillo, verde) y prompt ficticio
- **Prefijos de directorio** en eyebrows: `~/skills`, `~/proyectos`, `~/formacion`

### 2. Paleta de Colores: Azul Marino/Cobalto + Toggle Dark/Light

**Dark Mode (por defecto):**
- Fondo: `#0a1420` (azul muy oscuro, casi negro)
- Superficie: `#101f35` (azul oscuro)
- Acento: `#2f6fed` (azul cobalto brillante)
- Texto: `#e8f1f8` (azul muy claro)

**Light Mode (toggle):**
- Fondo: `#eef3f9` (azul muy claro)
- Texto: `#0f2a4a` (azul oscuro)
- Acentos: mantienen saturación coherente

**Variables CSS (`:root`):** Todos los colores, espacios y tipografías están centralizados en `:root` para fácil mantenimiento y coherencia visual.

**Toggle persistente:** La preferencia de tema se guarda en `localStorage`, recordando la elección del usuario entre sesiones.

### 3. Maquetación: Flexbox + Grid (combinadas estratégicamente)

- **Header:** Flexbox (alineación horizontal con espacio entre elementos)
- **Skills (tarjetas):** Flexbox con `flex-wrap` para distribución fluida
- **Proyectos:** CSS Grid 3 columnas en desktop, 2 en tablet, 1 en mobile
- **Formación:** Flexbox con `flex: 1 1 320px` para cards adaptables
- **Contacto:** Grid 2 columnas (email directo + formulario)

**Justificación:** Grid brinda control preciso sobre proyectos (layout fijo); Flexbox da fluidez donde importa (skills, formación). Combinadas permiten responsiveness sin media queries excesivas.

### 4. Tipografía: Roboto + Fira Code (jerarquía clara)

- **Display (h1):** Roboto Bold 700, `clamp(2rem, 5vw, 3.2rem)` — responsive sin media queries
- **Títulos (h2, h3):** Roboto 500/700
- **Cuerpo:** Roboto 400, `line-height: 1.6`
- **Código/Tags:** Fira Code 400/500, `font-size: 0.8rem`

**Decisión:** Roboto es legible en cualquier tamaño; Fira Code refuerza identidad tech sin sobrecargar.

### 5. Responsive Design: 4 Breakpoints

```css
/* Mobile muy viejo (< 480px) */
/* Mobile estándar (480px - 767px) */
/* Tablet (768px - 1023px) */
/* Desktop (1024px+) */
```

- **Mobile-first:** CSS base es mobile, media queries amplían para pantallas mayores
- **`clamp()` para tipografía:** Evita multiplicar selectores media
- **Menú hamburguesa:** Oculto en desktop, visible en mobile (<768px)
- **Grid adaptable:** Proyectos pasan de 3 → 2 → 1 columna dinámicamente

### 6. Animaciones & Transiciones

- **Fade-in global:** `@keyframes fadeIn` en secciones para efecto de carga suave
- **Hover en tarjetas:** `transform: translateY(-6px)` + `box-shadow` (efecto levantamiento)
- **Transiciones CSS:** `transition: all 0.3s ease` en botones y links
- **Respeto a `prefers-reduced-motion`:** Si el usuario prefiere menos movimiento, se deshabilitan animaciones

**Decisión:** Efectos sutiles (8px, 0.3s) mejoran UX sin distracción. Cumple con "al menos una animación" y "supera" la rúbrica.

### 7. Formulario Accesible

- **Labels vinculados:** `<label for="name">` vinculada a `<input id="name">`
- **Método `mailto:`:** Abre cliente de mail del usuario en lugar de requerir backend
- **Validación HTML5:** `required`, `type="email"` proporcionan feedback nativo
- **Alternativa directa:** Email visible también como link (`href="mailto:"`) para máxima accesibilidad

### 8. Imágenes con `alt` Descriptivo

Aunque no hay fotos de perfil (se optó por logo `[BS]`), se incluyen:
- **Ícono GitHub (SVG)** en header, footer y cada proyecto
- **Ícono Email (SVG)** en sección contacto
- Todos con `alt="Ícono del logo de GitHub"` y `alt="Ícono de sobre de correo"`

---

## Stack Técnico

| Componente | Tecnología |
|-----------|-----------|
| **HTML** | HTML5 semántico (header, nav, main, footer, section) |
| **CSS** | CSS3 puro (sin frameworks) — Flexbox, Grid, variables, `@keyframes` |
| **JavaScript** | Vanilla JS (toggle tema, menú mobile, localStorage) |
| **Tipografía** | Google Fonts (Roboto + Fira Code) |
| **Iconografía** | SVG custom (GitHub, Email) |
| **Hosting** | Vercel (despliegue) |

---

## Estructura de Archivos

```
landing_portfolio/
├── index.html          # Estructura HTML semántica
├── styles.css          # Estilos CSS3 (variables, Flexbox, Grid, media queries)
├── script.js           # JavaScript vanilla (toggle tema, menú)
├── icons/
│   ├── github.svg      # Ícono GitHub
│   └── mail.svg        # Ícono correo electrónico
└── README.md           # Este archivo
```

---

## Declaración de Uso de IA

### Herramienta(s) Utilizada(s): Claude (Anthropic)

**Plan:** Claude en claude.ai (acceso gratuito)

**Experiencia previa:** Se ah usado Claude para este tipo de proyectos pero acostumbo usar más Gemini Pro.

### Tareas Específicas donde se usó IA:

1. **Generación de estructura HTML semántica** ← Claude propuso estructura base respetando requisitos (header, nav, main, footer)
2. **CSS: Variables, Flexbox, Grid y media queries** ← Claude escribió la maquetación completa y ajustes responsive
3. **JavaScript: Toggle tema (dark/light) y menú mobile** ← Claude generó lógica funcional y localStorage
4. **Decisiones de diseño: Concepto visual (terminal/CLI)** ← Ideé la dirección; Claude la implementó
5. **Creación de README.md detallado** ← Claude estructuró la documentación a partir de mis lineamientos de contenido

### Qué se Revisó, Modificó o Adaptó con Criterio Propio:

**Decisión de paleta azul cobalto:** Partiendo de preferencia personal, elegí tonos específicos (#0F2A4A, #2F6FED)

**Concepto terminal/CLI:** Idea original que Claude ayudó a materializar técnicamente (eyebrows `~/about`, logo `[BS]`, ventana terminal en hero)

**Selección de 6 proyectos destacados:** Revisé todos mis repos en GitHub y elegí los más sólidos técnicamente (ClinicaSePrise con DDD, Sitio_NatAstral en Vercel, etc.)

**Énfasis en accesibilidad:** Agregué `alt` en íconos, `aria-label` en botones, respeto a `prefers-reduced-motion` — Claude generó base, yo solicité mejoras

**Escritura de descripciones de proyectos:** Adapté descripciones para que sean precisas y coherentes con mi CV

**Optimizaciones CSS:** Revisé variable naming, orden de selectores y media queries para claridad y performance

---

## Checklist de Requisitos (PFO1)

- **HTML semántico:** `<header>`, `<nav>`, `<main>`, `<footer>`, `<section>`
- **CSS propio:** Sin frameworks; variables CSS, Flexbox, Grid
- **Google Fonts:** Roboto + Fira Code
- **Maquetación Flexbox/Grid:** Ambas combinadas
- **Responsive:** 4 breakpoints (320px, 480px, 768px, 1024px)
- **Animaciones:** Fade-in + hover (supera mínimo)
- **Imágenes con `alt`:** SVG con alt descriptivo
- **Formulario con `<label>` vinculadas:** Presente en sección contacto
- **Enlace visible a GitHub:** Header + Footer + Hero
- **Despliegue Vercel:** Pendiente
- **README.md con declaración IA:** Este archivo

---

## Notas Finales

Este proyecto demuestra:

1. **Dominio técnico:** Uso avanzado de CSS (variables, Grid/Flexbox, media queries)
2. **Decisiones visuales propias:** Concepto terminal no es estándar; comunica identidad personal
3. **Accesibilidad:** Labels vinculados, `alt` text, `aria-label`, respeto a preferencias del usuario
4. **Responsiveness:** Funciona fluidamente en móviles viejos (320px) hasta 4K
5. **Profundidad:** Combinación de Flexbox + Grid justificada; animaciones que suman valor

**Autoría:** La estructura y concepto son míos; Claude facilitó la implementación técnica, que revisé y ajusté según mi criterio profesional.

---

**Brian Ezequiel Sabio**  
[GitHub](https://github.com/BrianSabio) | [Email](mailto:brianez.sa.ba@gmail.com)

