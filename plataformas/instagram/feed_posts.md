---
id: "spec-ig-feed-posts"
plataforma: "instagram"
formato: "feed_posts"
orientacion: "vertical"
relacion_aspecto: "4:5"
resolucion:
  ancho: 1080
  alto: 1350
  unidad: "px"
  alternativas_aceptadas:
    - { ancho: 1080, alto: 1080, nombre: "Cuadrado 1:1" }
    - { ancho: 1080, alto: 608, nombre: "Horizontal 1.91:1" }
fps:
  recomendados: [30]
  permitidos: [24, 25, 30, 60]
  tipo_escaneo: "progresivo"
video:
  contenedor: ["mp4", "mov"]
  codecs_recomendados: ["h264"]
  perfil_h264: "High"
  espacio_color: "Rec.709"
  submuestreo_croma: "4:2:0"
  bitrate_mbps:
    minimo: 5.0
    target: 10.0
    maximo: 16.0
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
  peso_maximo_mb: 4096
  duracion_minima_seg: 3
  duracion_maxima_seg: 3600
  duracion_recomendada_seg: { min: 30, max: 120 }
zonas_seguras:
  margen_superior_px: 0
  margen_inferior_px: 0
  margen_izquierdo_px: 0
  margen_derecho_px: 0
  zona_critica_ui:
    - "Sin superposiciones internas directas; los controles de Instagram se sitúan fuera del contenedor de vídeo en el muro."
tags: ["instagram", "feed", "vertical", "4:5", "cuadrado", "1:1"]
---

# 🖼️ Instagram Feed Posts (4:5 y 1:1)

El vídeo tradicional para el muro de Instagram sigue siendo un formato potente para tutoriales, carruseles de vídeo y contenido corporativo donde no se desea la interferencia de la interfaz inmersiva de Reels.

---

## 🏆 ¿Por qué el formato 4:5 (1080×1350) domina el Feed?

* **Ocupación del Viewport:** El formato 4:5 ocupa un **78% más de espacio vertical en pantalla** que el formato panorámico 16:9 tradicional. Al hacer scroll, el usuario no ve ninguna otra publicación compitiendo por su atención visual.
* **Sin Recortes Sorpresa:** A diferencia de Reels, el vídeo 4:5 se reproduce íntegro dentro del contenedor sin elementos de interfaz flotantes que tapen los bordes.
* **Ideal para Subtítulos Informativos:** Permite ubicar bandas de subtítulos o rótulos en la parte inferior con tipografía nítida y legible sin riesgo de colisión con botones.
