# 🎬 social-video-specs (Open Knowledge Framework - Especificaciones de Vídeo para Redes Sociales)

[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC_BY--SA_4.0-lightgrey.svg)](https://creativecommons.org/licenses/by-sa/4.0/deed.es)
[![Framework: OKF](https://img.shields.io/badge/Framework-OKF_v1.3-blue.svg)](estandares/arquitectura_okf.md)
[![Cobertura: 8 Plataformas](https://img.shields.io/badge/Cobertura-8_Plataformas_RRSS-green.svg)](#-matriz-de-referencia-rápida-por-plataforma)
[![Audio: EBU R128](https://img.shields.io/badge/Audio-EBU_R128_%7C_-14_LUFS-orange.svg)](estandares/audio_lufs_y_masterizacion.md)
[![Presets: FFmpeg | DaVinci | Premiere](https://img.shields.io/badge/Presets-FFmpeg_|_DaVinci_|_Premiere-purple.svg)](presets/)
[![Herramienta: HTML Autocontenido](https://img.shields.io/badge/Herramienta-HTML_Autocontenido-indigo.svg)](herramientas/calculadora_video_rrss.html)

Base de conocimiento abierta y estructurada basada en el estándar **Open Knowledge Framework (OKF v1.3)** que cataloga y estandariza todos los parámetros técnicos, relaciones de aspecto, resoluciones, perfiles de códec, tasas de bits, zonas seguras contra interfaces móviles y normas de sonoridad (LUFS) para optimizar la postproducción y publicación de vídeo en redes sociales.

Diseñado con una arquitectura dual: **100% legible para editores humanos** y **optimizado deterministamente para Agentes de Inteligencia Artificial** (Gemini, Claude, GPT, DeepSeek, Ollama/Llama) sin requerir bases de datos vectoriales complejas ni sufrir alucinaciones de parámetros.

---

## 🤖 Prompt Maestro de Arranque para Agentes de IA

Para instruir a cualquier agente de Inteligencia Artificial y convertirlo en un editor técnico de élite basado en este repositorio, **copia y pega el siguiente bloque** indicando tu plataforma y formato:

```markdown
Eres un Ingeniero y Editor Audiovisual Senior especializado en la optimización, postproducción y distribución técnica de vídeo para redes sociales, fundamentado en la base de conocimiento abierta OKF social-video-specs (https://github.com/nmarafo/social-video-specs).

TU MISIÓN:
Guiar, calcular, auditar y generar especificaciones técnicas exactas, recetas de transcodificación (FFmpeg, DaVinci Resolve, Premiere Pro), guiones adaptados a retención vertical y subtitulado respetando estrictamente las zonas seguras de cada plataforma.

PRINCIPIOS DETERMINISTAS DE OPERACIÓN:
1. FUENTE DE VERDAD: Fundamenta cada parámetro en 'plataformas/' y 'estandares/' del estándar OKF; prohibido inventar códecs no estándar, niveles de sonoridad arbitrarios o márgenes de interfaz incorrectos.
2. REGLA CANÓNICA DE AUDIO: Toda masterización debe situar la sonoridad integrada en -14.0 LUFS (±1.0 LUFS) y True Peak en -1.0 dBTP (estándar ITU-R BS.1770 / EBU R128 a 48 kHz).
3. REGLA UNIVERSAL DE ZONAS SEGURAS: En vídeo vertical 9:16 (1080×1920), ningún subtítulo, titular ni elemento esencial puede situarse fuera de la ventana Y: 220px a 1500px, ni colisionar con el margen lateral derecho de interacción (160px en TikTok / 130px en Reels).
4. STREAMING INMEDIATO (FASTSTART): Todo flujo de trabajo en contenedor MP4 debe exigir la reubicación del átomo 'moov' al inicio del archivo (-movflags +faststart).
5. BITRATE SWEET SPOT: Advierte siempre contra el mito de superar los 20 Mbps en Reels o TikTok (activa la re-compresión destructiva del servidor). Recomienda entre 12 y 15 Mbps en H.264 High Profile para 1080p.

FLUJO DE TRABAJO CON EL USUARIO:
- Paso 1: Identifica plataforma, formato y objetivo. Si falta información, solicítala de inmediato.
- Paso 2: Proporciona la ficha técnica resumida (Resolución, FPS, Bitrate Target, LUFS y Zonas Seguras).
- Paso 3: Proporciona la receta de render (Comando FFmpeg o ruta exacta de ajustes en DaVinci Resolve / Premiere Pro).
- Paso 4: Si se solicita guion o subtítulos, desglosa el ritmo en micro-fragmentos (1-3 palabras por pantalla) con gancho en los primeros 2.5 segundos.
- Paso 5: Concluye con un Checklist de Control de Calidad (QA) de 3 puntos antes de publicar.
```

---

## 📊 Matriz de Referencia Rápida por Plataforma

| Plataforma | Formato Principal | Aspecto | Resolución Óptima | Bitrate Target | Límite Duración | Límite Peso | Sonoridad Target |
| :--- | :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **YouTube** | Shorts | `9:16` | 1080×1920 | 12 – 18 Mbps | 60 seg | 2 GB | -14.0 LUFS / -1.0 dBTP |
| **YouTube** | Long-Form Horizontal | `16:9` | 3840×2160 / 2560×1440 | 45 Mbps (4K) / 16 Mbps (2K) | 12 horas | 256 GB | -14.0 LUFS / -1.0 dBTP |
| **Instagram** | Reels | `9:16` | 1080×1920 | 12 – 15 Mbps | 90 seg (hasta 15 min) | 4 GB | -14.0 LUFS / -1.0 dBTP |
| **Instagram** | Feed Vertical | `4:5` | 1080×1350 | 10 Mbps | 60 min | 4 GB | -14.0 LUFS / -1.0 dBTP |
| **TikTok** | Feed Vertical | `9:16` | 1080×1920 | 10 – 15 Mbps | 10 min | 287 MB | -14.0 LUFS / -1.0 dBTP |
| **TikTok** | Modo Horizontal | `16:9` | 1920×1080 | 15 Mbps | 10 – 60 min | 512 MB | -14.0 LUFS / -1.0 dBTP |
| **Facebook** | Reels & Stories | `9:16` | 1080×1920 | 12 Mbps | 90 seg | 4 GB | -14.0 LUFS / -1.0 dBTP |
| **Facebook** | Feed / Watch | `16:9` / `4:5` | 1920×1080 / 1080×1350 | 12 – 15 Mbps | 240 min | 10 GB | -14.0 LUFS / -1.0 dBTP |
| **X (Twitter)**| Vídeo en Feed | `9:16` / `16:9` | 1080×1920 / 1920×1080 | 12 Mbps | 140 seg (3h en Premium) | 512 MB (16 GB en Prem.) | -14.0 LUFS (AAC estricto) |
| **LinkedIn** | Vídeo Feed Cuadrado | `1:1` | 1080×1080 | 10 Mbps | 10 – 15 min | 5 GB | -14.0 LUFS / -1.0 dBTP |
| **Twitch / Kick**| Clips Verticales | `9:16` | 1080×1920 | 14 Mbps (60 fps) | 60 seg | N/A | -14.0 LUFS / -1.0 dBTP |
| **Pinterest** | Video Pins | `2:3` | 1000×1500 | 8 – 12 Mbps | 15 min (6-15 s ideal) | 2 GB | -14.0 LUFS / -1.0 dBTP |

---

## 📁 Estructura del Repositorio OKF

```text
social-video-specs/
├── README.md                            # Presentación, matriz rápida, prompt maestro y licencia
├── LICENSE.md                           # Licencia CC BY-SA 4.0 con cláusula de atribución
├── .gitignore                           # Exclusiones de archivos multimedia y del sistema operativo
├── manifest.json                        # Manifiesto formal OKF v1.3 con catálogo de entidades
├── schema/                              # Esquemas formales JSON Schema (Draft-07)
│   ├── social_video_spec_schema.json    # Validación de especificaciones técnicas por plataforma
│   ├── safe_zone_schema.json            # Validación de zonas seguras y áreas de interfaz
│   └── export_preset_schema.json        # Validación de recetas de codificación y render
├── plataformas/                         # Fichas técnicas detalladas por red social con YAML Frontmatter
│   ├── youtube/                         # Long-form 16:9, Shorts 9:16 y Miniaturas/Thumbnails
│   ├── instagram/                       # Reels 9:16, Stories 9:16 y Feed Posts 4:5/1:1
│   ├── tiktok/                          # Feed vertical nativo 9:16 y Modo horizontal 16:9
│   ├── facebook/                        # Reels, Stories y Vídeo en Feed/Watch
│   ├── x_twitter/                       # Vídeo estándar (140s) vs X Premium (hasta 3h)
│   ├── linkedin/                        # Vídeo corporativo 1:1, 9:16 y 16:9 con subtítulos obligatorios
│   ├── twitch_kick/                     # Clips verticales de directos y momentos destacados
│   └── pinterest/                       # Pines de vídeo en ratio canónico 2:3 y 9:16
├── estandares/                          # Fundamentos técnicos de ingeniería audiovisual
│   ├── arquitectura_okf.md              # Especificación del estándar OKF aplicado a vídeo digital
│   ├── codificacion_y_codecs.md         # H.264, HEVC, AV1, VP9, átomo moov faststart y gamma shift
│   ├── audio_lufs_y_masterizacion.md    # Estándar EBU R128 (-14 LUFS / -1.0 dBTP) y ecualización móvil
│   ├── zonas_seguras_y_composicion.md   # Metodología de safe zones y capas de interfaz móvil
│   ├── subtitulado_y_accesibilidad.md   # Subtítulos kinetic de alta retención (micro-chunking)
│   └── checklist_qa_pre_publicacion.md  # Protocolo de control de calidad previo a exportar y subir
├── presets/                             # Perfiles y recetas de exportación listos para usar
│   ├── ffmpeg/recetas_ffmpeg.md         # Comandos de transcodificación, faststart y loudnorm
│   ├── davinci_resolve/guia_exportacion_davinci.md # Render settings, color Rec.709-A y Fairlight
│   └── premiere_pro/guia_exportacion_premiere.md   # Media Encoder, VBR y normalización ITU BS.1770
├── plantillas/prompts/                  # Biblioteca modular de prompts para Agentes de IA
│   ├── prompt_maestro_editor_video_rrss.md    # Prompt maestro para configurar a cualquier agente
│   ├── prompt_01_analisis_formato_plataforma.md # Selección automática de especificaciones técnicas
│   ├── prompt_02_ritmo_y_storyboarding.md       # Escaleta de retención segundo a segundo
│   ├── prompt_03_generacion_subtitulos_safe_zones.md # Subtítulos kinetic en zona segura
│   └── prompt_04_control_calidad_qa.md        # Auditoría técnica pre-render
└── herramientas/                        # Herramienta web local autocontenida
    └── calculadora_video_rrss.html      # Aplicación interactiva con visor visual de UI, calculadora de peso y generador FFmpeg
```

---

## 📱 La Regla Universal de Zonas Seguras: 220 / 420 px

Al editar un vídeo vertical en **1080×1920** para publicación simultánea (*cross-posting*) en **TikTok, Instagram Reels y YouTube Shorts**:

```text
┌──────────────────────────────────────────────┐ 0px
│ [ CABECERA DE LA APP Y BÚSQUEDA ]            │ ◄── Margen Superior (220 px)
├──────────────────────────────────────────────┤ 220px
│                                              │
│               ZONA SEGURA                    │
│                UNIVERSAL                     │
│                                              │
│        (Subtítulos dinámicos,                │ ◄── Margen Lateral Derecho (160 px)
│         rostro principal,                    │     Ocupado por botones flotantes
│         titulares y llamadas a la acción)    │     (Like, Comentarios, Compartir)
│                                              │
├──────────────────────────────────────────────┤ 1500px
│ [ NOMBRE DE USUARIO, DESCRIPCIÓN Y AUDIO ]   │ ◄── Margen Inferior (420 px)
└──────────────────────────────────────────────┘ 1920px
  0px                    920px              1080px
```

* **Límite Superior:** Mantén los elementos clave por debajo de **Y: 220 px**.
* **Límite Inferior:** Mantén los elementos clave por encima de **Y: 1500 px**.
* **Límite Derecho:** Deja un margen libre de **160 px** a la derecha (máximo X: 920 px).

---

## ⚡ Herramienta Web Interactiva Autocontenida

En el directorio [`herramientas/calculadora_video_rrss.html`](herramientas/calculadora_video_rrss.html) dispones de una aplicación web completa desarrollada en un **único archivo HTML autónomo** (Tailwind CSS CDN + JavaScript modular, sin dependencias de servidor ni Node.js):

* **Simulador de Pantalla Móvil en Tiempo Real:** Visualiza las capas reales de interfaz de TikTok, Reels y Shorts sobre tu contenido, con alertas visuales automáticas si tus subtítulos colisionan con botones o leyendas.
* **Calculadora Matemática de Bitrate:** Introduce duración y tasa de bits para predecir el peso exacto en MB/GB y comprobar compatibilidad con los topes de subida.
* **Generador de Comandos FFmpeg con 1 Clic:** Transcodificación con FastStart, normalización LUFS y reencuadres automáticos de 16:9 a 9:16 con desenfoque de fondo.
* **Inspector Rápido de Plataformas:** Comparativa instantánea de resoluciones, límites y particularidades.

*Para utilizarla, simplemente haz doble clic sobre el archivo `calculadora_video_rrss.html` para abrirlo en cualquier navegador web.*

---

## 📄 Licencia y Atribución

Este repositorio y todos sus contenidos se distribuyen bajo los términos de la licencia **[Creative Commons Atribución-CompartirIgual 4.0 Internacional (CC BY-SA 4.0)](https://creativecommons.org/licenses/by-sa/4.0/deed.es)**.

### Cláusula de Atribución Obligatoria
En cualquier obra derivada, adaptación o integración en sistemas informáticos, modelos RAG o agentes de Inteligencia Artificial, **debe incluirse la siguiente mención explícita**:

> *Basado en el proyecto de código y conocimiento abierto [social-video-specs](https://github.com/nmarafo/social-video-specs), creado por **Norberto Martín Afonso**, distribuido bajo licencia Creative Commons Atribución-CompartirIgual 4.0 Internacional (CC BY-SA 4.0).*
