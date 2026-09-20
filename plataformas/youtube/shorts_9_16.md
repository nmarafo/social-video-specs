---
id: "spec-yt-shorts-9-16"
plataforma: "youtube"
formato: "shorts_9_16"
orientacion: "vertical"
relacion_aspecto: "9:16"
resolucion:
  ancho: 1080
  alto: 1920
  unidad: "px"
  alternativas_aceptadas:
    - { ancho: 1440, alto: 2560, nombre: "2K Vertical (Máxima nitidez)" }
fps:
  recomendados: [30, 60]
  permitidos: [24, 25, 30, 50, 60]
  tipo_escaneo: "progresivo"
video:
  contenedor: ["mp4", "mov"]
  codecs_recomendados: ["h264", "hevc"]
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
  tolerancia_lufs: 0.5
  true_peak_max_dbtp: -1.0
  rango_dinamico_sugerido_lu: { min: 4.0, max: 8.0 }
limites:
  peso_maximo_mb: 2048
  duracion_minima_seg: 1
  duracion_maxima_seg: 60
  duracion_recomendada_seg: { min: 15, max: 45 }
zonas_seguras:
  margen_superior_px: 140
  margen_inferior_px: 360
  margen_izquierdo_px: 60
  margen_derecho_px: 140
  zona_critica_ui:
    - "Margen inferior (360px): Título del Short, botón de suscripción, nombre del canal y sonido oficial."
    - "Margen lateral derecho (140px): Botón 'Me gusta', 'No me gusta', Comentarios, Compartir y Remix."
    - "Margen superior (140px): Botón de búsqueda, cámara y selector de cuenta."
tags: ["youtube", "shorts", "vertical", "9:16", "short_form"]
---

# 📱 YouTube Shorts (9:16 Vertical)

Especificación técnica de referencia para la creación y edición de YouTube Shorts. El formato vertical exige un estricto control de las zonas seguras debido a la densa capa de elementos visuales flotantes del reproductor móvil.

---

## 🗺️ Mapa de Zonas Seguras en YouTube Shorts (1080×1920)

```text
┌──────────────────────────────────────────────┐ 0px
│ [ ← ]                [ 🔍 ]   [ 📷 ]   [ ⋮ ] │ ◄── Margen superior (140px): Navegación y búsqueda
├──────────────────────────────────────────────┤ 140px
│                                              │
│                                              │
│               ZONA SEGURA                    │
│                 CENTRAL                      │
│                                              │
│         (Subtítulos dinámicos,               │    [ 👍 ]
│          rostros principales                 │    [ 👎 ]
│          y elementos clave)                  │    [ 💬 ] ◄── Botonera lateral derecha
│                                              │    [ ↗ ]      (140px de ancho)
│                                              │    [ 🎛️ ]
├──────────────────────────────────────────────┤ 1560px
│ @Canal [Suscribirse]                         │ ◄── Margen inferior (360px):
│ Título del Short con hashtags...             │     Identidad, suscripción,
│ 🎵 Sonido original - Título de la pista      │     título y audio
└──────────────────────────────────────────────┘ 1920px
  0px                    940px              1080px
```

---

## ⚡ Reglas de Edición para Alta Retención

1. **El Gancho (0 a 3 segundos):**
   * El 65% de los usuarios deciden si deslizar (*swipe*) en los primeros 1.5 a 2.5 segundos.
   * Coloca el elemento visual más intrigante o una pregunta de conflicto en el tercio superior de la zona segura.
2. **Subtitulado Dinámico Kinetic:**
   * La posición óptima de los subtítulos se ubica entre **Y: 900px y Y: 1350px**.
   * No bajes de **Y: 1560px** bajo ningún concepto para evitar que el nombre del canal o el botón de suscribirse los tape.
3. **Looping Perfecto (Bucle Invisible):**
   * Enlaza la última frase del vídeo con la primera palabra del gancho para fomentar que el espectador lo vea más de una vez (elevando la métrica *Average Percentage Viewed* por encima del 100%).
