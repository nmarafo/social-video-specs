---
id: "spec-ig-reels-9-16"
plataforma: "instagram"
formato: "reels_9_16"
orientacion: "vertical"
relacion_aspecto: "9:16"
resolucion:
  ancho: 1080
  alto: 1920
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
    minimo: 6.0
    target: 14.0
    maximo: 22.0
    modo_control: "VBR_1Pass"
  moov_atom_faststart: true
audio:
  codec: "AAC-LC"
  canales: "estéreo (2.0)"
  frecuencia_muestreo_hz: 48000
  bitrate_kbps: 256
  lufs_integrado_target: -14.0
  tolerancia_lufs: 1.0
  true_peak_max_dbtp: -1.0
limites:
  peso_maximo_mb: 4096
  duracion_minima_seg: 3
  duracion_maxima_seg: 900
  duracion_recomendada_seg: { min: 12, max: 60 }
zonas_seguras:
  margen_superior_px: 220
  margen_inferior_px: 420
  margen_izquierdo_px: 60
  margen_derecho_px: 130
  recortes_cuadricula:
    feed_4_5: { y_inicio_px: 285, y_fin_px: 1635, alto_px: 1350 }
    perfil_1_1: { y_inicio_px: 420, y_fin_px: 1500, alto_px: 1080 }
  zona_critica_ui:
    - "Margen inferior (420px): Nombre @usuario, botón 'Seguir', texto de caption, etiqueta de audio y carrusel de comentarios."
    - "Margen derecho (130px): Botones flotantes (Me gusta, Comentarios, Compartir en DM, Guardar y Menú de tres puntos)."
    - "Margen superior (220px): Cabecera con selector 'Reels', cámara y botón de sonido."
tags: ["instagram", "reels", "vertical", "9:16", "short_form"]
---

# 🌀 Instagram Reels (9:16 Vertical)

Especificación técnica oficial y análisis de zonas seguras para Instagram Reels. Requiere una composición milimétrica para responder simultáneamente a la pantalla completa inmersiva y a los recortes en el feed y perfil.

---

## 📐 El Doble Recorte: Feed (4:5) y Perfil (1:1)

```text
┌──────────────────────────────────────────────┐ 0px
│ [ ← Reels ]                         [ 📷 ]   │ ◄── Margen superior (220px): Cabecera
├ - - - - - - - - - - - - - - - - - - - - - - -┤ 285px ── Límite superior Feed 4:5
│                                              │
├──────────────────────────────────────────────┤ 420px ── Límite superior Cuadrícula Perfil 1:1
│                                              │
│               ZONA SEGURA                    │    [ ❤️ ]
│             PERFIL Y FEED                    │    [ 💬 ]
│                                              │    [ ↗ ] ◄── Botonera lateral derecha
│           (1080 × 1080 px)                   │    [ 🔖 ]    (130px de ancho)
│                                              │    [ ⋮ ]
├──────────────────────────────────────────────┤ 1500px ── Límite inferior Cuadrícula Perfil 1:1
│                                              │
├ - - - - - - - - - - - - - - - - - - - - - - -┤ 1635px ── Límite inferior Feed 4:5
│ @usuario • [Seguir]                          │ ◄── Margen inferior (420px):
│ Texto del pie de foto con hashtags... [más]  │     Pie de foto y audio
│ 🎵 Audio original - Nombre del artista       │
└──────────────────────────────────────────────┘ 1920px
  0px                    950px              1080px
```

---

## 🎯 Consejos de Composición para Reels

1. **El Cuadrado Central Sagrado (420px a 1500px):**
   * Todo título de portada, titular de apertura, texto animado o elemento que desees que se entienda en la cuadrícula de tu perfil de Instagram **DEBE** caber entre **Y: 420 px** y **Y: 1500 px**.
2. **Subtítulos Quemados (*Burn-in*):**
   * Ubica los subtítulos automáticos o animados en el rango **Y: 1050 px a Y: 1350 px**.
   * Esto asegura que sean 100% visibles tanto en el reproductor de Reels como en el feed 4:5, sin colisionar con la descripción ni los botones.
3. **Control de Ruido y Nitidez en Meta:**
   * Evita el exceso de grano cinematográfico (*film grain*). Los algoritmos de compresión de Instagram interpretan el grano fino como movimiento rápido de alta frecuencia y comprimen el fotograma en bloques toscos de macrobloques (*blocking artifacts*).
