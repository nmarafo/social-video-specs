---
id: "spec-twitch-kick-clips"
plataforma: "twitch_kick"
formato: "clips_vods"
orientacion: "vertical"
relacion_aspecto: "9:16"
resolucion:
  ancho: 1080
  alto: 1920
  unidad: "px"
  alternativas_aceptadas:
    - { ancho: 1920, alto: 1080, nombre: "Horizontal 16:9 Clip Original" }
fps:
  recomendados: [60]
  permitidos: [30, 60]
video:
  contenedor: ["mp4"]
  codecs_recomendados: ["h264"]
  perfil_h264: "High"
  espacio_color: "Rec.709"
  submuestreo_croma: "4:2:0"
  bitrate_mbps:
    minimo: 8.0
    target: 14.0
    maximo: 22.0
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
  duracion_minima_seg: 5
  duracion_maxima_seg: 60
tags: ["twitch", "kick", "streaming", "clips", "gaming", "9:16"]
---

# 🎮 Clips y VODs de Streaming (Reencuadre 9:16)

Especificación para transformar directos y jugadas en clips verticales de alto impacto.

---

## ✂️ Patrón de Diseño para Reencuadre Vertical (Streamer Stack)

Para convertir un stream 16:9 en un formato 9:16 optimizado para viralización:

1. **Capa Superior (Webcam / Reacción):**
   * Recorta la cámara del creador en formato 16:9 o 4:3 y sitúala en la parte superior (**Y: 200 px a Y: 700 px**).
2. **Capa Central / Inferior (Gameplay o Contenido Principal):**
   * Recorta la acción central del juego o pantalla y amplíala para llenar el área media e inferior (**Y: 700 px a Y: 1550 px**).
3. **Fondo Desenfoque (*Gaussian Blur*):**
   * Duplica el clip de fondo, estíralo para cubrir todo el lienzo 9:16 y aplica un desenfoque gaussiano de 50px con opacidad al 50%.
4. **Subtítulos Dinámicos Centrados:**
   * Coloca subtítulos con palabras clave resaltadas en color entre la webcam y el juego para máxima claridad.
