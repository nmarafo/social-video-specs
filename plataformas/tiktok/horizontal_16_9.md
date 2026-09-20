---
id: "spec-tiktok-horizontal-16-9"
plataforma: "tiktok"
formato: "horizontal_16_9"
orientacion: "horizontal"
relacion_aspecto: "16:9"
resolucion:
  ancho: 1920
  alto: 1080
  unidad: "px"
fps:
  recomendados: [30, 60]
  permitidos: [24, 25, 30, 50, 60]
  tipo_escaneo: "progresivo"
video:
  contenedor: ["mp4", "mov"]
  codecs_recomendados: ["h264"]
  perfil_h264: "High"
  espacio_color: "Rec.709"
  submuestreo_croma: "4:2:0"
  bitrate_mbps:
    minimo: 8.0
    target: 15.0
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
  peso_maximo_mb: 512
  duracion_minima_seg: 60
  duracion_maxima_seg: 3600
  duracion_recomendada_seg: { min: 180, max: 600 }
zonas_seguras:
  margen_superior_px: 50
  margen_inferior_px: 100
  margen_izquierdo_px: 50
  margen_derecho_px: 50
tags: ["tiktok", "horizontal", "16:9", "long_form"]
---

# 📺 TikTok Modo Horizontal (16:9)

TikTok admite formalmente vídeos horizontales tradicionales en relación 16:9. La app muestra un botón interactivo de *"Pantalla completa"* que invita al usuario a rotar el smartphone para consumir el contenido de forma panorámica.

---

## 🎯 Directrices de Producción

1. **Subida Limpia sin Letterboxing Forzado:**
   * Sube el archivo en formato **1920×1080 nativo**. No agregues barras negras (*letterboxing* o *pillarboxing*) tú mismo; TikTok se encarga de posicionarlo en el reproductor vertical y ofrecer la opción de rotación automática.
2. **Duraciones Extensas:**
   * Formato pensado para documentales cortos, tutoriales técnicos, podcasts y gameplays (duraciones de entre 3 y 10 minutos).
3. **Indicador Visual en los Primeros 3 Segundos:**
   * Es una buena práctica incluir una animación o icono breve en los primeros 3 segundos indicando *"Gira tu teléfono"* para maximizar la tasa de visionado en pantalla completa.
