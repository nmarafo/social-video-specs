---
id: "spec-x-video-feed"
plataforma: "x_twitter"
formato: "video_feed"
orientacion: "vertical"
relacion_aspecto: "9:16"
resolucion:
  ancho: 1080
  alto: 1920
  unidad: "px"
  alternativas_aceptadas:
    - { ancho: 1920, alto: 1080, nombre: "Horizontal 16:9" }
    - { ancho: 1080, alto: 1080, nombre: "Cuadrado 1:1" }
fps:
  recomendados: [30, 60]
  permitidos: [24, 25, 30, 60]
video:
  contenedor: ["mp4", "mov"]
  codecs_recomendados: ["h264"]
  perfil_h264: "High"
  espacio_color: "Rec.709"
  submuestreo_croma: "4:2:0"
  bitrate_mbps:
    minimo: 5.0
    target: 12.0
    maximo: 25.0
    modo_control: "VBR_1Pass"
  moov_atom_faststart: true
audio:
  codec: "AAC-LC"
  canales: "estéreo (2.0)"
  frecuencia_muestreo_hz: 48000
  bitrate_kbps: 192
  lufs_integrado_target: -14.0
  true_peak_max_dbtp: -1.0
limites:
  peso_maximo_mb: 512
  duracion_minima_seg: 1
  duracion_maxima_seg: 140
zonas_seguras:
  margen_superior_px: 120
  margen_inferior_px: 240
  margen_izquierdo_px: 50
  margen_derecho_px: 100
tags: ["x", "twitter", "video_feed", "16:9", "9:16", "1:1"]
---

# ✖️ X (Twitter) Vídeo en Feed y Modo Inmersivo

Especificación técnica de vídeo para X. En móvil, los vídeos verticales se abren en un feed de deslizamiento continuo similar a TikTok, mientras que en el timeline cronológico aparecen embebidos dentro de la tarjeta de publicación.

---

## 🎯 Puntos Clave

1. **Auto-Play sin Audio:** Por defecto los vídeos se reproducen mudos en el timeline. Incorpora subtítulos o un titular gráfico explicativo.
2. **Duración en Cuentas Gratuitas:** Respeta el límite duro de **140 segundos (2:20)**. Si el vídeo mide 2:21, la app te obligará a recortarlo antes de publicar.
3. **Optimización con FastStart:** La bandera `-movflags +faststart` es crítica en X para evitar que el reproductor web se quede en buffer inicial.
