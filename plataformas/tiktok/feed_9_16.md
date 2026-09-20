---
id: "spec-tiktok-feed-9-16"
plataforma: "tiktok"
formato: "feed_9_16"
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
  tolerancia_lufs: 1.0
  true_peak_max_dbtp: -1.0
  rango_dinamico_sugerido_lu: { min: 4.0, max: 7.0 }
limites:
  peso_maximo_mb: 287
  duracion_minima_seg: 3
  duracion_maxima_seg: 600
  duracion_recomendada_seg: { min: 15, max: 45 }
zonas_seguras:
  margen_superior_px: 160
  margen_inferior_px: 380
  margen_izquierdo_px: 60
  margen_derecho_px: 160
  zona_critica_ui:
    - "Margen derecho (160px): Avatar de creador con botón [+], Like, Comentarios, Guardar en Favoritos, Compartir y disco giratorio."
    - "Margen inferior (380px): Nombre de usuario @cuenta, descripción de varias líneas, hashtags, enlaces a productos/tienda y ticker de sonido con nota musical."
    - "Margen superior (160px): Pestañas 'Siguiendo / Para ti', lupa de búsqueda [🔍] y LIVE."
tags: ["tiktok", "feed", "vertical", "9:16", "short_form"]
---

# 🎵 TikTok Feed Nativo (9:16 Vertical)

Especificación técnica de referencia y áreas seguras para vídeos en el feed de TikTok. Debido a la gran cantidad de iconos flotantes a la derecha y los textos inferiores, el espacio útil libre de interferencias es el más estrecho de todas las plataformas.

---

## 🗺️ Mapa de Zonas Seguras en TikTok (1080×1920)

```text
┌──────────────────────────────────────────────┐ 0px
│ [ LIVE ]       Siguiendo | Para ti     [ 🔍 ]│ ◄── Margen superior (160px): Navegación y búsqueda
├──────────────────────────────────────────────┤ 160px
│                                              │
│                                              │
│               ZONA SEGURA                    │    [ 👤+ ] Avatar y seguir
│                 CENTRAL                      │    [  ❤️  ] Likes
│                                              │    [  💬  ] Comentarios
│         (Subtítulos dinámicos,               │    [  🔖  ] Guardados
│          puntos de interés visual,           │    [  ↗  ] Compartir
│          rostros y gráficos)                 │    [  💿  ] Disco de audio
│                                              │    (160px margen derecho)
├──────────────────────────────────────────────┤ 1540px
│ @usuario                                     │ ◄── Margen inferior (380px):
│ Descripción del vídeo con hashtags #fyp...   │     Identidad, texto largo,
│ ♫ Sonido original - Artista oficial          │     música y barra de progreso
└──────────────────────────────────────────────┘ 1920px
  0px                    920px              1080px
```

---

## 📐 Zona Segura Recomendada para Subtítulos

* **Coordenadas Verticales:** Sitúa tus subtítulos entre **Y: 950 px y Y: 1350 px**.
* **Coordenadas Horizontales:** Centrados entre **X: 80 px y X: 900 px** (dejando 180 px libres a la derecha).
* **Tamaño de Fuente:** Entre **50 y 75 pt** (en resolución 1080×1920) con reborde negro grueso (*stroke* de 4 a 6 px) o fondo semitransparente para asegurar legibilidad sobre cualquier fondo de vídeo.
