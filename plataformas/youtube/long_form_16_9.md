---
id: "spec-yt-longform-16-9"
plataforma: "youtube"
formato: "long_form_16_9"
orientacion: "horizontal"
relacion_aspecto: "16:9"
resolucion:
  ancho: 3840
  alto: 2160
  unidad: "px"
  alternativas_aceptadas:
    - { ancho: 2560, alto: 1440, nombre: "2K QHD (Upscale recomendado)" }
    - { ancho: 1920, alto: 1080, nombre: "Full HD Estándar" }
    - { ancho: 1280, alto: 720, nombre: "HD 720p" }
fps:
  recomendados: [24, 25, 30, 50, 60]
  permitidos: [23.976, 24, 25, 29.97, 30, 50, 59.94, 60]
  tipo_escaneo: "progresivo"
video:
  contenedor: ["mp4", "mov"]
  codecs_recomendados: ["h264", "hevc", "prores_422"]
  perfil_h264: "High"
  espacio_color: "Rec.709 (SDR) o Rec.2020 / HDR10 (HLG o PQ)"
  submuestreo_croma: "4:2:0"
  bitrate_mbps:
    minimo: 8.0
    target: 45.0
    maximo: 85.0
    modo_control: "VBR_2Pass"
  moov_atom_faststart: true
audio:
  codec: "AAC-LC"
  canales: "estéreo (2.0)"
  frecuencia_muestreo_hz: 48000
  bitrate_kbps: 320
  lufs_integrado_target: -14.0
  tolerancia_lufs: 1.0
  true_peak_max_dbtp: -1.0
  rango_dinamico_sugerido_lu: { min: 6.0, max: 14.0 }
limites:
  peso_maximo_mb: 262144
  duracion_minima_seg: 1
  duracion_maxima_seg: 43200
  duracion_recomendada_seg: { min: 480, max: 1200 }
zonas_seguras:
  margen_superior_px: 60
  margen_inferior_px: 120
  margen_izquierdo_px: 60
  margen_derecho_px: 60
  zona_critica_ui:
    - "Barra de progreso y reproducción inferior (evitar textos en los últimos 100px)"
    - "Botón de suscripción flotante inferior derecho (marca de agua del canal)"
    - "Tarjetas interactivas y pantallas finales (últimos 20 segundos del vídeo)"
tags: ["youtube", "long_form", "horizontal", "16:9", "4k", "1080p"]
---

# 🎬 YouTube Long-Form (16:9 Horizontal)

Guía canónica para la exportación y optimización de vídeos horizontales tradicionales en YouTube. Diseñado para maximizar la calidad de imagen frente a la doble compresión del servidor y asegurar un audio profesional y equilibrado.

---

## 📊 Matriz de Bitrates Recomendados por YouTube

| Resolución | Framerate Estándar (24, 25, 30 fps) | Framerate Alto (50, 60 fps) | HDR (10 bits Rec.2020) |
| :--- | :---: | :---: | :---: |
| **4K (3840×2160)** | **35 – 45 Mbps** | **53 – 68 Mbps** | **44 – 85 Mbps** |
| **2K (2560×1440)** | **16 Mbps** | **24 Mbps** | **20 – 30 Mbps** |
| **1080p (1920×1080)** | **8 – 10 Mbps** | **12 – 15 Mbps** | **10 – 18 Mbps** |

> [!TIP]
> **El Truco Pro:** Aunque grabes tu contenido en 1080p nativo, reescala (*upscale*) tu línea de tiempo o tu render a **2560×1440 (1440p)**. Al subir 1440p, los servidores de YouTube asignarán automáticamente el códec **VP9/AV1**, que cuenta con una tasa de bits de entrega significativamente más rica y menos artefactos de bloque en degradados y sombras.

---

## 🎛️ Parámetros Críticos de Renderizado

1. **GOP (Group of Pictures):** Establecer la distancia entre fotogramas clave (*Keyframes*) en la mitad de la tasa de fotogramas (ejemplo: cada 12 fotogramas en 24 fps, cada 15 en 30 fps, o un máximo absoluto de 2 segundos).
2. **Perfil de Codificación:** H.264 High Profile, Nivel 5.1 o 5.2.
3. **Control de Tasa:** VBR de 2 pases (o CRF 18 con motor x264/FFmpeg).
4. **Espacio de Color:** Matriz BT.709, Primarias BT.709, Transferencia BT.709 (evita el temido deslavado de gamma en navegadores Safari/QuickTime en macOS aplicando la etiqueta `-color_primaries bt709 -color_trc bt709 -colorspace bt709`).

---

## 🛡️ Zonas Seguras y Elementos de Pantalla

* **Pantallas Finales (End Screens):** Se activan en los últimos 5 a 20 segundos. Diseña una plantilla visual limpia al final del vídeo reservando espacio para:
  * 1 o 2 miniaturas de vídeo recomendado (16:9).
  * 1 botón circular de suscripción.
* **Márgenes de Títulos:** Mantén los subtítulos y rótulos al menos a 120px de la parte inferior para que la barra de reproducción móvil y de escritorio no los tape cuando el usuario toque la pantalla.
