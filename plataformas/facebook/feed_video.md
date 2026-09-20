---
id: "spec-fb-feed-video"
plataforma: "facebook"
formato: "feed_video"
orientacion: "horizontal"
relacion_aspecto: "16:9"
resolucion:
  ancho: 1920
  alto: 1080
  unidad: "px"
  alternativas_aceptadas:
    - { ancho: 1080, alto: 1350, nombre: "Vertical Feed 4:5" }
    - { ancho: 1080, alto: 1080, nombre: "Cuadrado Feed 1:1" }
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
    minimo: 6.0
    target: 12.0
    maximo: 25.0
    modo_control: "VBR_1Pass"
  moov_atom_faststart: true
audio:
  codec: "AAC-LC"
  canales: "estéreo (2.0)"
  frecuencia_muestreo_hz: 48000
  bitrate_kbps: 256
  lufs_integrado_target: -14.0
  true_peak_max_dbtp: -1.0
limites:
  peso_maximo_mb: 10240
  duracion_minima_seg: 1
  duracion_maxima_seg: 14400
tags: ["facebook", "feed", "watch", "16:9", "4:5", "1:1"]
---

# 📺 Facebook Vídeo en Feed y Watch

Especificación técnica para vídeos publicados en páginas, perfiles, grupos y la sección Facebook Watch.

---

## 💡 Claves de Alto Rendimiento

1. **Subtítulos Obligatorios (Diseño para Ver en Silencio):**
   * El **85% de los vídeos en el feed de Facebook se reproducen en silencio** mediante la función de auto-play.
   * Si el vídeo no cuenta con subtítulos grandes, de alto contraste o texto explicativo en los primeros 3 segundos, la retención cae en picado.
2. **El Formato 4:5 para Campañas Publicitarias y Móvil:**
   * Al igual que en Instagram, en la app móvil de Facebook el ratio **4:5 (1080×1350)** genera un CTR sensiblemente mayor que el formato 16:9 clásico gracias a la cobertura de pantalla.
