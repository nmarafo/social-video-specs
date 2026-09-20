---
id: "spec-ig-stories-9-16"
plataforma: "instagram"
formato: "stories_9_16"
orientacion: "vertical"
relacion_aspecto: "9:16"
resolucion:
  ancho: 1080
  alto: 1920
  unidad: "px"
fps:
  recomendados: [30]
  permitidos: [24, 25, 30]
  tipo_escaneo: "progresivo"
video:
  contenedor: ["mp4", "mov"]
  codecs_recomendados: ["h264"]
  perfil_h264: "High"
  espacio_color: "Rec.709"
  submuestreo_croma: "4:2:0"
  bitrate_mbps:
    minimo: 4.0
    target: 8.0
    maximo: 12.0
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
  peso_maximo_mb: 250
  duracion_minima_seg: 1
  duracion_maxima_seg: 60
  duracion_recomendada_seg: { min: 7, max: 15 }
zonas_seguras:
  margen_superior_px: 250
  margen_inferior_px: 250
  margen_izquierdo_px: 50
  margen_derecho_px: 50
  zona_critica_ui:
    - "Margen superior (250px): Barra de segmentos de stories, foto de perfil, nombre de usuario y botón de cierre [X]."
    - "Margen inferior (250px): Caja de respuesta de mensaje directo 'Enviar mensaje', botón de me gusta y compartir."
tags: ["instagram", "stories", "vertical", "9:16", "efimero"]
---

# 📖 Instagram Stories (9:16 Vertical)

Especificaciones y zonas de interacción para Historias de Instagram. A diferencia de Reels, la interacción en Stories se concentra en la caja de respuesta directa inferior y los stickers interactivos (encuestas, enlaces, preguntas).

---

## 🎯 Zonas de Interacción y Márgenes de Seguridad

* **Margen Superior (Top Safe Zone):** 250 px.
  * Ocupado por las barras de progreso temporales de cada historia y el avatar de la cuenta.
* **Margen Inferior (Bottom Safe Zone):** 250 px.
  * Ocupado por la barra flotante de texto *"Enviar mensaje"* y el botón de corazón.
* **Zona de Stickers Interactivos:**
  * Sitúa siempre los stickers de enlace web (*Link sticker*), encuestas o cajitas de preguntas en el tercio central de la pantalla (**entre Y: 500 px y Y: 1300 px**).
  * Si colocas un sticker demasiado cerca de los bordes laterales, el usuario puede saltar involuntariamente a la siguiente historia al intentar pulsar el sticker.
