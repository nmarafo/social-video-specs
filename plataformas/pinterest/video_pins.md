---
id: "spec-pinterest-video-pins"
plataforma: "pinterest"
formato: "video_pins"
orientacion: "vertical"
relacion_aspecto: "2:3"
resolucion:
  ancho: 1000
  alto: 1500
  unidad: "px"
  alternativas_aceptadas:
    - { ancho: 1080, alto: 1920, nombre: "Vertical Inmersivo 9:16" }
    - { ancho: 1080, alto: 1080, nombre: "Cuadrado 1:1" }
fps:
  recomendados: [30]
  permitidos: [24, 25, 30]
video:
  contenedor: ["mp4", "mov"]
  codecs_recomendados: ["h264"]
  perfil_h264: "High"
  espacio_color: "Rec.709"
  submuestreo_croma: "4:2:0"
  bitrate_mbps:
    minimo: 4.0
    target: 8.0
    maximo: 15.0
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
  peso_maximo_mb: 2048
  duracion_minima_seg: 4
  duracion_maxima_seg: 900
  duracion_recomendada_seg: { min: 6, max: 15 }
tags: ["pinterest", "pins", "ecommerce", "2:3", "9:16"]
---

# 📌 Pines de Vídeo en Pinterest (2:3, 9:16 y 1:1)

Especificaciones para optimizar el alcance y la conversión en Pinterest mediante Pines de vídeo.

---

## 💡 Claves de Optimización

1. **La Relación de Aspecto 2:3:**
   * Es el estándar canónico del feed de Pinterest. A diferencia de 9:16 (que puede recortarse ligeramente en ciertos layouts de cuadrícula de escritorio), el formato **1000×1500 (2:3)** se muestra al 100% de escala sin ningún recorte.
2. **Vídeos de Acción Rápida (6 a 15 segundos):**
   * En Pinterest los usuarios buscan inspiración para actuar (DIY, recetas, moda, diseño). Vídeos concisos y dinámicos que muestran el resultado en los primeros 2 segundos tienen una tasa de guardado (*Pin saves*) muy superior.
3. **Portada del Pin Atractiva:**
   * Selecciona manualmente un fotograma clave nítido y luminoso como portada del Pin, ya que muchos usuarios exploran con la reproducción automática desactivada.
