# GUÍA DE DISEÑO, SISTEMA DE DISEÑO Y ARQUITECTURA TÉCNICA
## Parra Cano Abogados · Medellín, Colombia
**Documento Fuente de Verdad (Single Source of Truth) para Agentes y Desarrolladores**  
*Ruta del archivo:* `.agents/DESIGN.md`  
*Dominio de producción:* `parracanoabogados.com` (Cloudflare Pages)

---

## 1. Visión General y Filosofía de Marca

**Parra Cano Abogados** es una firma jurídica boutique con sede en Medellín, Colombia, orientada a la estrategia legal de alto nivel, litigio, resolución de controversias y asesoría corporativa.

### Propuesta de Valor y Tono
* **Propósito:** *"Estrategia y defensa legal con excelencia."*
* **Tono de Marca:** Sofisticado, riguroso, contemporáneo, accesible y transparente. 
* **Equilibrio Visual:** La firma rompe con el cliché del despacho de abogados tradicional (oscuro, acartonado, cargado de mármol y tipografías pesadas del siglo XIX), pero mantiene la seriedad y el peso institucional de las grandes firmas colombianas (como Arrubla Devis). Adopta una estética editorial limpia, luminosa y moderna inspirada en referencias globales de vanguardia (como Aurex Law).
* **Demografía y Clientes:** Directores de empresas, fondos de inversión, directores jurídicos, familias empresarias y personas naturales que buscan asesoría estratégica de primer orden con contacto directo sin burocracia.

---

## 2. Sistema de Color y Tokens de Diseño

La paleta se deriva de los tres colores principales del isotipo de la firma (los tres rombos dinámicos entrelazados) y de la vestimenta ejecutiva sobria que proyectan los socios en sus sesiones fotográficas (traje azul marino y traje gris sastre).

### 2.1 Paleta Principal (Brand Colors)
| Token CSS | Hex | Rol y Uso | Ratio de Contraste |
| :--- | :--- | :--- | :--- |
| `--color-brand-primary` | `#2A3950` | **Azul Noche / Azul Oscuro Corporativo**. Utilizado en titulares clave, isotipo, botones primarios, header y footer estático de cierre. | 9.8:1 sobre blanco (AAA) |
| `--color-brand-secondary` | `#316789` | **Azul Pizarra Medio**. Color de acento para hover states, enlaces interactivos, tabs activas y detalles de rombos. | 5.2:1 sobre blanco (AA) |
| `--color-brand-neutral` | `#91908E` | **Gris Sastre / Warm Slate**. Utilizado en líneas divisorias sutiles, bordes de tarjetas, metadatos y etiquetas secundarias. | 3.1:1 sobre blanco (UI) |

### 2.2 Tokens de Superficie (Light Canvas & Paper)
El cliente especificó enfáticamente **fondos claros y máxima legibilidad**.
| Token CSS | Hex | Propósito |
| :--- | :--- | :--- |
| `--color-bg-base` | `#FFFFFF` | Fondo blanco puro para módulos de lectura densa (reseñas, artículos). |
| `--color-bg-paper` | `#FBFBFA` | Blanco hueso / papel tibio que evita el deslumbramiento y otorga sensación de despacho editorial. |
| `--color-bg-paper-warm` | `#F3F4F6` | Fondo secundario para tarjetas anidadas, cajas de testimonios o bloques de bio. |
| `--color-bg-paper-subtle` | `#EBEFF2` | Fondo frío sutil para contenedores técnicos (noticias judiciales, descargas). |
| `--color-bg-dark` | `#1A2433` | Azul muy profundo para el footer estático y banda de contacto global. |

### 2.3 Tokens de Texto y Jerarquía
| Token CSS | Hex | Propósito |
| :--- | :--- | :--- |
| `--color-text-main` | `#161F2E` | Tinta oscura primaria con un matiz azul noche, legibilidad suprema. |
| `--color-text-muted` | `#4B5565` | Gris neutro para párrafos de descripción, subtítulos y biografías. |
| `--color-text-faint` | `#6E7787` | Gris tenue para números de sección (01, 02), fechas y metadatos. |
| `--color-text-inverse` | `#FFFFFF` | Texto blanco puro para bloques oscuros y botones primarios. |

### 2.4 Acentos y Estados
| Token CSS | Hex | Propósito |
| :--- | :--- | :--- |
| `--color-accent-bronze` | `#C5A880` | Bronce / dorado opaco utilizado para micro-badges, estrellas de prestigio y detalles finos. |
| `--color-state-success` | `#10B981` | Notificaciones de envío exitoso de hojas de vida y contacto. |
| `--color-state-error` | `#EF4444` | Validación de campos obligatorios en formularios. |

---

## 3. Estrategia Tipográfica y Evaluación Crítica

### 3.1 El Dilema de Montserrat
El isotipo actual de la firma utiliza **Montserrat** (`PARRA CANO` en peso SemiBold/Bold y `ABOGADOS` en peso Light con espaciado amplio).
* **Evaluación Crítica:** Usar Montserrat para todo el sitio (titulares largos, párrafos y enlaces) provocaría que la firma luzca como una plantilla genérica de startup de 2018 o un folleto publicitario estándar. En el sector legal de alto nivel, la tipografía debe comunicar **criterio, jurisprudencia y sofisticación intelectual**.
* **Solución de Armonía Tipográfica:**
  1. **Títulos Principales y Citas Editoriales:** Usar una serifa de corte moderno y elegante como **Instrument Serif** o **Newsreader / Cormorant Garamond**. Esto eleva inmediatamente la percepción de valor a nivel de firmas internacionales (Aurex Law, Arrubla Devis, Wachtell).
  2. **Cuerpo de Texto y UI:** Usar **Plus Jakarta Sans** o **Inter**, sans-serifs contemporáneas de excelente rendimiento tipográfico en pantallas Retina y móviles.
  3. **Presencia de Montserrat:** Se reserva de manera deliberada y quirúrgica para **Kickers, Eyebrows, Categorías, Badges y Monogramas en mayúsculas sostenidas con tracking amplio (`letter-spacing: 0.18em`)**, haciendo eco armónico con el logotipo sin contaminar la lectura corrida.

### 3.2 Escala Tipográfica (Fluid Typography)
| Elemento | Fuente | Tamaño (Desktop / Móvil) | Peso | Tracking & Leading |
| :--- | :--- | :--- | :--- | :--- |
| **Hero Display H1** | `Instrument Serif` / `Newsreader` | `clamp(2.8rem, 6.5vw, 4.8rem)` | 400 (Regular/Italic) | `-0.025em` / `0.98` |
| **Section H2** | `Instrument Serif` / `Newsreader` | `clamp(2.0rem, 4.2vw, 3.2rem)` | 400 / 500 | `-0.02em` / `1.08` |
| **Card H3 / Subtítulos** | `Plus Jakarta Sans` | `1.25rem - 1.5rem` | 600 (SemiBold) | `-0.01em` / `1.3` |
| **Body (Párrafos)** | `Plus Jakarta Sans` | `1.0rem (16px) - 1.0625rem (17px)` | 400 (Regular) | `0em` / `1.65` |
| **Kicker / Eyebrow (Eco Logo)** | `Montserrat` | `0.75rem (12px) - 0.8125rem (13px)` | 600 (SemiBold, UPPERCASE) | `0.18em` / `1.2` |
| **Micro Labels & Badges** | `Plus Jakarta Sans` / `Montserrat` | `0.6875rem (11px)` | 500 (Medium) | `0.12em` / `1.0` |

---

## 4. Retícula, Espaciado y Reglas de Layout

### 4.1 Contenedores y Bordes Redondeados (Aurex Law Influence)
* **Contenedor Maestro:** Ancho máximo de `1240px` centrado con padding horizontal de `20px` (móvil) a `48px` (desktop).
* **Radio de Bordes (Border-Radius Hierarchy):**
  * Grandes contenedores de sección (Wrapper exterior): `28px` a `32px`.
  * Tarjetas de servicios, equipo y noticias: `18px` a `22px`.
  * Botones y pastillas (Pill buttons): `9999px` (Full rounded).
  * Avatares e insignias circulares: `50%`.
* **Micro-Bordes (Hairline Borders):** Todas las tarjetas sobre fondo claro deben utilizar un borde ultra-fino de `1px solid rgba(42, 57, 80, 0.08)`. Prohibido el uso de bordes negros o sombras excesivamente oscuras.
* **Elevación y Sombras:**
  * Base: `box-shadow: 0 4px 20px -6px rgba(42, 57, 80, 0.04);`
  * Hover: `box-shadow: 0 16px 36px -12px rgba(42, 57, 80, 0.10); transform: translateY(-3px);`

### 4.2 Breakpoints Responsivos
* `sm`: `640px` (Teléfonos en apaisado / tablets pequeñas)
* `md`: `768px` (Tablets / iPad vertical)
* `lg`: `1024px` (Laptops estándar / tablets horizontales)
* `xl`: `1280px` (Monitores de escritorio estándar)
* `2xl`: `1536px` (Pantallas panorámicas de alta resolución)

---

## 5. Especificaciones del Hero y Video Aéreo de Medellín

El cliente solicitó un Hero visualmente imponente con un video aéreo en bucle de Medellín y el texto *"Estrategia y defensa legal con excelencia."*

### 5.1 Decisión Crítica de Arquitectura Visual: ¿Full-Bleed vs. Split Hero?
* **Riesgo del Video Full-Bleed en Fondos Claros:** Un video de fondo completo con edificios, calles en movimiento y luz solar diurna genera ruido visual extremo y arruina el contraste del texto oscuro, obligando a oscurecerlo con filtros negros que contradicen la preferencia de la firma por fondos claros.
* **Solución Óptima Recomendada (Split Framing Hero):**
  * **Columna Izquierda:** Título editorial de alto impacto (`Estrategia y defensa legal con excelencia`), subtítulo de contexto, botones de acción (Agendar consulta / WhatsApp), y pastilla de confianza (ej. *"Firma con sede en Medellín · Litigio & Derecho de los Negocios"*).
  * **Columna Derecha (Video Card con Marco Curvo):** Un contenedor redondeado (`border-radius: 24px`) con ratio `4:5` o `16:10` donde corre el video aéreo de Medellín con esquinas suaves, superposición de un badge flotante en glassmorphism (*"Medellín, Antioquia · Milla de Oro"*), y una tarjeta flotante de contacto o especialidades.
  * **Alternativa Aceptable (Full-Width Framed Window):** Un contenedor curvo con video aéreo que posee un overlay degradado semitransparente con `backdrop-filter: blur(2px)` y una capa blanca al 65%-75% de opacidad, asegurando un contraste AAA para el texto en azul `#2A3950`.

### 5.2 Directrices para la Grabación/Selección del Video Aéreo (Para el Cliente)
1. **Locación / Encuadre:**
   * Milla de Oro (El Poblado), Centro Financiero, Avenida El Poblado o panorámica del Valle de Aburrá al amanecer o atardecer (hora dorada/azul).
   * Tomas lentas y fluidas: *Slow forward dolly* o *slow high-altitude pan*. Prohibir vuelos rápidos tipo FPV o movimientos bruscos de dron.
2. **Color Grading & Luz:**
   * Tonos arquitectónicos templados (vidrio, verde de los cerros de Medellín, ladrillo elegante).
   * Evitar saturación excesiva de verdes o amarillos; buscar un acabado neutro y cinematográfico tipo documental de alta gama.
3. **Optimización Técnica (Web Performance):**
   * Duración máxima del bucle: `8 a 12 segundos` (seamless loop, sin saltos notables).
   * Resolución de entrega: `1920x1080` (Desktop) y `1080x1350` (Móvil vertical opcional).
   * Códec: **WebM** (prioritario para Chrome/Firefox) con fallback a **MP4 (H.264/H.265 baseline)** para Safari/iOS.
   * Peso objetivo: **Menor a 3.5 MB** comprimido mediante herramientas como Handbrake o FFmpeg (`crf 28`).
   * Atributos obligatorios en la etiqueta: `<video autoplay loop muted playsinline poster="/assets/hero-medellin-poster.webp">`.

---

## 6. Arquitectura de la Información y Mapa de Rutas

El sitio cuenta con arquitectura bilingüe completa (**Español** como idioma principal y **English** como secundario).

```
parracanoabogados.com/
├── / (Home)                          -> Hero video, diferenciales, 10 soluciones, equipo, actualidad, contacto
├── /nosotros                         -> Filosofía, historia, rigor académico y visión estratégica
├── /soluciones                       -> Índice de las 10 áreas de práctica
│   ├── /soluciones/[slug]            -> Detalle individual de la solución (alcance, abogados a cargo)
├── /equipo                           -> Cuícula de socios fundadores, asociados y of counsel
│   ├── /equipo/[slug]                -> Perfil profesional (Layout Arrubla Devis: foto izq + bio der)
├── /actualidad                       -> Noticias jurídicas automáticas + Podcast "Las cosas como son"
│   ├── /actualidad/[slug]            -> Artículo de análisis o episodio de podcast
├── /trabaja-con-nosotros             -> Formulario de postulación con carga de CV en PDF
├── /contacto                         -> Formulario directo, ubicación en Medellín, canales inmediatos
├── /admin                            -> Dashboard privado para actualización de contenidos
│
└── /en/...                           -> Espejo completo en idioma inglés
    ├── /en
    ├── /en/about
    ├── /en/practices
    ├── /en/team
    ├── /en/insights
    ├── /en/contact
    └── /en/careers
```

---

## 7. Especificación Detallada de Componentes Clave

### 7.1 Barra de Navegación Flotante (Floating Island Navbar)
* **Forma:** Pastilla flotante con ancho máximo de `1200px` fijada en la parte superior (`top: 16px`), con `border-radius: 9999px`, fondo blanco semitransparente (`rgba(255, 255, 255, 0.88)`), desenfoque de fondo `backdrop-filter: blur(16px)` y borde fino `1px solid rgba(42, 57, 80, 0.08)`.
* **Elementos:**
  1. **Logotipo a la izquierda:** Isotipo de rombos + texto Parra Cano Abogados en SVG nítido.
  2. **Enlaces centrales:** Inicio, Soluciones (con dropdown o enlace directo), Equipo, Actualidad, Nosotros.
  3. **Acciones a la derecha:** Selector de idioma pill (`ES · EN`), enlace telefónico/WhatsApp y botón primario destacado (`Agendar consulta`).
* **Interacción Móvil:** Botón hamburguesa redondo que despliega un menú a pantalla completa con tipografía de gran formato y enlaces táctiles generosos.

### 7.2 Módulo de Equipo y Perfil de Miembro (Estilo Arrubla Devis)
* **Página de Listado (`/equipo`):**
  * Grid de tarjetas con fotos de los socios fundadores en proporción `3:4`.
  * Tratamiento de imagen: Fotos recortadas profesionalmente con iluminación de estudio, fondo neutro o desenfocado de despacho.
  * Texto inferior: Nombre en H3 (`Plus Jakarta Sans 600`), cargo (*Socio Fundador / Director*), y áreas de práctica asociadas en letra chica con enlace sutil.
* **Página de Detalle de Abogado (`/equipo/[slug]`):**
  * **Layout de 2 Columnas (Arrubla Devis Reference):**
    * **Columna Izquierda (Sticky / Ancla Visual, aprox. 38% del ancho):**
      * Fotografía vertical en alta resolución con esquinas redondeadas (`20px`).
      * Datos de contacto directo: Email profesional con botón de copia rápida, perfil de LinkedIn verificado y botón directo de WhatsApp.
      * Idiomas de práctica (ej. *Español · Inglés*).
    * **Columna Derecha (Contenido Estructurado, aprox. 62% del ancho):**
      * Kicker superior: Cargo (*Socio Fundador*).
      * Nombre en H1 editorial de gran porte.
      * **Semblanza / Perfil Profesional:** Párrafos con su enfoque estratégico y trayectoria.
      * **Formación Académica:** Lista estructurada (Universidad, Especializaciones, Maestrías, reconocimientos).
      * **Áreas de Especialidad:** Tags con enlaces a las soluciones correspondientes que atiende este abogado.
      * **Publicaciones y Docencia:** Mención de cátedras universitarias y artículos.
      * Botón directo: *"Agendar consulta con [Nombre]"*.

### 7.3 Módulo de 10 Soluciones / Áreas de Práctica
* Se presentan las 10 especialidades legales en una cuadrícula interactiva de 2x5 o 3x3+1 en desktop, o mediante pestañas de filtrado (ej. *Litigio & Controversias*, *Derecho Corporativo*, *Sector Público*).
* Cada tarjeta contiene:
  * Número correlativo con tracking (`01`, `02`, ..., `10`) en Montserrat.
  * Título conciso del área legal.
  * Breve descripción de valor (2-3 líneas).
  * Enlace con flecha diagonal animada (`lucide-arrow-up-right`) que se eleva en `:hover`.

### 7.4 Sección de Actualidad Jurídica & Podcast "Las cosas como son"
* **Pestaña 1: Actualidad Jurídica Automatizada (Corte Suprema y Consejo de Estado):**
  * Tarjetas de boletín con badge distintivo según la fuente (*Sala Civil*, *Sala Laboral*, *Consejo de Estado*).
  * Fecha de emisión del fallo o comunicado.
  * Titular del pronunciamiento judicial con enlace al texto completo o resumen del equipo.
* **Pestaña 2: Podcast "Las cosas como son":**
  * Tarjeta destacada con cover art del podcast (diseñado acorde a la paleta azul y gris).
  * Reproductor de audio HTML5 personalizado o widget embebido de Spotify / Apple Podcasts.
  * Lista de episodios con duración, título y breve sumario.

### 7.5 Módulo Estático de Cierre y Contacto (Persistent Global Contact Band)
Presente en todas las páginas justo antes del pie de página tradicional:
* **Fondo:** Azul Profundo (`#1A2433` o `#2A3950`) con texto en blanco hueso.
* **Titular:** *"Estrategia legal sin dilaciones. Conversemos sobre su caso."*
* **Información Directa:**
  * Dirección de oficina: Medellín, Colombia (Milla de Oro / El Poblado).
  * Teléfono fijo y celular de atención.
  * Acceso directo a WhatsApp empresarial con mensaje predefinido.
  * Correo electrónico corporativo (`contacto@parracanoabogados.com`).
  * Enlace al perfil de LinkedIn de la firma y de los socios.
* **Formulario Exprés o Botón de Agendamiento:** Modal o redirección directa a `/contacto`.

### 7.6 Sección "Trabaja con Nosotros" (`/trabaja-con-nosotros`)
* Propósito: Captación de talento joven y abogados asociados con criterio de diseño de soluciones.
* Formulario interactivo:
  * Nombre completo y cédula/tarjeta profesional (opcional).
  * Correo electrónico y teléfono de contacto.
  * Área de interés jurídico (selector de las 10 soluciones).
  * Campo para URL de LinkedIn.
  * **Carga de Hoja de Vida:** Zona drag & drop para archivos `.pdf` o `.docx` (máx. 5MB) conectada a Cloudflare R2 con validación estricta de extensiones y peso.
  * Checkbox de aceptación de política de tratamiento de datos personales (Habeas Data Ley 1581 de 2012).

---

## 8. Arquitectura Técnica y Stack Tecnológico

Evaluando los requisitos del usuario (**máximo rendimiento, bilingüe, desplegado en Cloudflare, dominio comprado y vinculado a Cloudflare, dashboard para que ellos editen textos fácilmente**), se establece la siguiente arquitectura técnica definitiva:

### 8.1 Stack Recomendado y Justificación Crítica
* **Framework:** **Astro 5** (Modo SSR / Hybrid con adaptador `@astrojs/cloudflare`).
  * *¿Por qué Astro y no Next.js clásico?*
    * Arrubla Devis está desarrollado con Astro debido a su velocidad implacable y arquitectura de islas (zero JS por defecto).
    * En Cloudflare Pages, Astro genera páginas con tiempos de respuesta menores a 100ms a nivel global y puntuación de 100/100 en Google Lighthouse (Core Web Vitals).
    * Manejo nativo de internacionalización (i18n) para `/` y `/en`.
* **Componentes Interactivos:** **React / Preact** únicamente en islas donde se requiere estado del cliente (formulario de postulación, reproductor de podcast, modal de contacto, buscador).
* **Gestor de Paquetes:** `pnpm` exclusivamente (regla estricta del proyecto).
* **Estilos:** Vanilla CSS con variables CSS nativas y utilidades bien estructuradas, garantizando control total sin sobrecargar hojas de estilo innecesarias.
* **Infraestructura Cloudflare:**
  * **Cloudflare Pages:** Hosting global con despliegue continuo desde Git.
  * **Cloudflare R2 Bucket:** Almacenamiento de archivos PDF de hojas de vida y activos de audio/video.
  * **Cloudflare D1 (SQLite en el Edge):** Base de datos relacional ultraligera para almacenar formularios de contacto, postulaciones de empleo y caché de noticias jurídicas.
  * **Cloudflare Turnstile:** Protección invisible contra bots y spam en los formularios sin fastidiosos captchas.

### 8.2 Arquitectura del Dashboard / CMS Privado
Para que los abogados puedan actualizar noticias, bios, textos y enlaces sin tocar código:
* **Solución Óptima:** **Decap CMS / TinaCMS** configurado sobre Git, o un **Dashboard Administrativo Personalizado con Cloudflare Access**:
  * Los abogados acceden a `/admin` mediante autenticación segura por correo (Magic Link de Cloudflare Access o contraseña segura hash en D1).
  * Interfaz intuitiva tipo Notion/Formulario con campos organizados:
    * *Textos de la página de inicio* (Hero, misión, números).
    * *Gestión de Equipo* (Subir foto, editar semblanza, formación).
    * *Gestión de Soluciones* (Editar títulos y alcances de las 10 áreas).
    * *Gestión de Noticias y Podcast* (Agregar enlaces de Spotify, títulos y reflexiones).
  * Los cambios se persisten inmediatamente en D1 o realizan un commit automático que redespliega en Cloudflare Pages en segundos.

---

## 9. Automatización de Actualidad Jurídica (Corte Suprema y Consejo de Estado)

Para cumplir con el requerimiento de noticias automáticas sobre la Corte Suprema de Justicia (Salas Civil y Laboral) y el Consejo de Estado:

### 9.1 Flujo de Ingesta Automatizada
1. **Cloudflare Scheduled Worker (Cron Job Diario):**
   * Se ejecuta una vez al día (ej. 06:00 AM hora de Colombia).
   * Consulta las fuentes oficiales de RSS o endpoints de prensa de la Rama Judicial de Colombia (`cortesuprema.gov.co` y `consejodeestado.gov.co`).
2. **Filtrado y Procesamiento:**
   * Filtra comunicados y sentencias de relevancia en las salas Civil, Laboral y Sección Tercera/Técnica del Consejo de Estado.
   * Almacena los registros con título, fecha, sala judicial, resumen y enlace al documento oficial en la tabla `judicial_news` de Cloudflare D1.
3. **Control Editorial Opcional:**
   * En el dashboard `/admin`, los abogados tienen un interruptor para *Aprobar / Destacar* noticias relevantes para que aparezcan en la portada con su propio comentario o análisis experto.

---

## 10. Reglas de Animación y Micro-Interacciones (Aurex Law Inspiration)

Las animaciones deben ser sutiles, elegantes y de ritmo natural (*whisper animations*, no rebotes agresivos de videojuego):
* **Aparición de Textos y Títulos (Blur + Slide Up):**
  * Transición inicial: `opacity: 0; filter: blur(6px); transform: translateY(18px);`
  * Estado final: `opacity: 1; filter: blur(0); transform: translateY(0);`
  * Timing: `duration: 650ms; ease: cubic-bezier(0.16, 1, 0.3, 1);`
* **Botones e Íconos Magnéticos:**
  * Al pasar el ratón por los botones con flecha diagonal (`lucide-arrow-up-right`), la flecha sale por la esquina superior derecha (`translate(5px, -5px)`) y reaparece desde la esquina inferior izquierda con suavidad.
* **Transiciones de Tarjetas:**
  * Efecto hover con micro-elevación de `translateY(-3px)` y oscurecimiento muy leve del borde perimetral.
* **Accesibilidad Obligatoria:** Todas las animaciones deben deshabilitarse automáticamente si el usuario tiene activado `@media (prefers-reduced-motion: reduce)`.

---

## 11. Rendimiento, SEO y Accesibilidad (Estándares Obligatorios)

* **Performance:** 
  * Puntuación mínima en Google PageSpeed Insights: **95+ en Mobile y 98+ en Desktop**.
  * Imágenes convertidas automáticamente a formatos modernos **AVIF y WebP** con tamaños explícitos (`width` y `height`) para prevenir Cumulative Layout Shift (CLS = 0).
* **SEO Especializado en Sector Legal Colombiano:**
  * Marcado estructurado Schema.org en formato JSON-LD:
    * `LegalService` para la entidad corporativa principal (dirección en Medellín, teléfono, logo, fundadores, geolocalización).
    * `Person` para las páginas individuales de cada abogado en `/equipo/[slug]`.
    * `Article` / `PodcastSeries` para las publicaciones y episodios de "Las cosas como son".
* **Accesibilidad (WCAG 2.1 Nivel AA):**
  * Todo texto sobre fondo claro debe cumplir con un ratio de contraste mínimo de `4.5:1` para texto normal y `3:1` para texto grande.
  * Focus visible en todos los botones y campos de formulario para navegación por teclado.
  * Etiquetas `aria-label` en enlaces de sólo icono (WhatsApp, LinkedIn, selector de idioma).

---

## 12. Reglas de Implementación para Futuros Agentes

Cualquier agente que trabaje en este repositorio debe respetar estrictamente:
1. **Fidelidad al archivo:** Este archivo `.agents/DESIGN.md` es la norma arquitectónica. No improvisar nuevos esquemas de color ni meter librerías de estilos pesadas sin justificación.
2. **Uso de pnpm:** Ejecutar siempre comandos con `pnpm` (nunca `npm` ni `yarn`).
3. **Fondo Claro:** La interfaz principal es de fondo claro y aireado. El fondo oscuro queda reservado para la banda de contacto y pie de página.
4. **Respeto a las Fotos Reales:** Tratar las imágenes de los socios con recorte impecable, sin distorsión de relación de aspecto (`object-fit: cover`).
5. **No Mermaid:** Prohibido insertar diagramas Mermaid en respuestas del chat o documentación markdown, ya que rompen la interfaz.
