---
id: "spec-linkedin-video-feed"
plataforma: "linkedin"
formato: "video_feed"
orientacion: "vertical"
relacion_aspecto: "1:1"
resolucion:
  ancho: 1080
  alto: 1080
  unidad: "px"
  alternativas_aceptadas:
    - { ancho: 1080, alto: 1920, nombre: "Vertical Móvil 9:16" }
    - { ancho: 1920, alto: 1080, nombre: "Horizontal Paisaje 16:9" }
fps:
  recomendados: [30]
  permitidos: [24, 25, 30, 60]
video:
  contenedor: ["mp4"]
  codecs_recomendados: ["h264"]
  perfil_h264: "High"
  espacio_color: "Rec.709"
  submuestreo_croma: "4:2:0"
  bitrate_mbps:
    minimo: 5.0
    target: 10.0
    maximo: 20.0
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
  peso_maximo_mb: 5120
  duracion_minima_seg: 3
  duracion_maxima_seg: 900
  duracion_recomendada_seg: { min: 30, max: 180 }
zonas_seguras:
  margen_superior_px: 0
  margen_inferior_px: 80
  margen_izquierdo_px: 0
  margen_derecho_px: 0
tags: ["linkedin", "b2b", "feed", "1:1", "16:9", "9:16"]
---

# 💼 LinkedIn Vídeo en Feed (1:1, 9:16 y 16:9)

Especificación técnica de vídeo profesional para LinkedIn.

---

## 💡 Estrategia de Edición para LinkedIn

1. **Subtítulos Incorporados o Archivo `.srt`:**
   * La inmensa mayoría de profesionales visualizan los contenidos durante su jornada laboral con el audio silenciado.
   * LinkedIn admite subir archivos `.srt` independientes, pero la práctica con mayor retención es "quemar" (*burn-in*) subtítulos elegantes con tipografía profesional (sans-serif moderna tipo Montserrat, Roboto o Inter).
2. **El Gancho Textual Superior:**
   * En formato 1:1 o 4:5, añade una barra superior (*header banner*) con el titular del problema profesional que resuelve el vídeo.
3. **Límite de Peso:** Admite hasta 5 GB, pero para vídeos de 1 a 3 minutos mantén el archivo entre **50 y 150 MB** para agilizar la carga en conexiones de empresa o itinerancia.
