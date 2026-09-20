---
id: "spec-fb-reels-stories"
plataforma: "facebook"
formato: "reels_stories"
orientacion: "vertical"
relacion_aspecto: "9:16"
resolucion:
  ancho: 1080
  alto: 1920
  unidad: "px"
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
    maximo: 20.0
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
  peso_maximo_mb: 4096
  duracion_minima_seg: 3
  duracion_maxima_seg: 90
zonas_seguras:
  margen_superior_px: 200
  margen_inferior_px: 380
  margen_izquierdo_px: 60
  margen_derecho_px: 130
tags: ["facebook", "reels", "stories", "vertical", "9:16"]
---

# 🌀 Facebook Reels y Stories (9:16)

Especificaciones para Reels y Stories dentro de la red de Facebook. Si utilizas la sincronización automática cruzada (*Cross-posting*) desde Instagram, las zonas seguras de Instagram Reels cubren perfectamente la interfaz de Facebook.

---

## 🎯 Elementos de Interfaz en Facebook Reels

* **Margen Superior (200px):** Logo de Facebook Reels, botón de búsqueda y botón de creación de reel.
* **Margen Inferior (380px):** Nombre de la página o perfil, botón "Seguir", descripción y etiqueta de audio.
* **Margen Lateral Derecho (130px):** Iconos de reacción (Me gusta, Me encanta...), botón de comentarios, compartir y remix.
