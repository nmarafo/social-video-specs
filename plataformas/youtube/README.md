---
id: "plataforma-youtube"
plataforma: "youtube"
nombre: "YouTube"
formatos_disponibles: ["long_form_16_9", "shorts_9_16", "miniaturas_thumbnails"]
norma_audio_lufs: -14.0
true_peak_dbtp: -1.0
actualizado: "2026"
---

# 📺 Plataforma: YouTube (Especificaciones Técnicas OKF)

YouTube es la mayor plataforma global de vídeo en línea y cuenta con el sistema de transcodificación y compresión más avanzado de la industria. Procesa múltiples perfiles y códecs secundarios (AVC1/H.264, VP9 y AV1) en función de la resolución de subida y el volumen de visualizaciones.

---

## 🎯 Resumen Ejecutivo de Formatos

| Formato | Relación de Aspecto | Resolución Recomendada | Duración Máx. | LUFS Target | Ficha Técnica |
| :--- | :---: | :---: | :---: | :---: | :--- |
| **Horizontal Estándar (Long-Form)** | `16:9` | 3840×2160 (4K) / 1920×1080 (FHD) | 12 horas (256 GB) | -14.0 LUFS | [`long_form_16_9.md`](long_form_16_9.md) |
| **YouTube Shorts** | `9:16` | 1080×1920 (FHD Vertical) | 60 segundos | -14.0 LUFS | [`shorts_9_16.md`](shorts_9_16.md) |
| **Miniaturas (Thumbnails)** | `16:9` | 1280×720 (Mín. 640px ancho) | N/A (Máx. 2 MB) | N/A | [`miniaturas_thumbnails.md`](miniaturas_thumbnails.md) |

---

## 💡 Claves de Optimización Técnica para YouTube

1. **El Secreto del Códec VP9 / AV1 (Regla de los 1440p):**
   * Los vídeos subidos a **1080p** en canales pequeños a medianos se codifican casi siempre con **AVC1 (H.264)**, lo que genera artefactos de compresión y pérdida de nitidez en escenas con movimiento o grano.
   * Si exportas y subes en **1440p (2560×1440)** o **4K (3840×2160)**, YouTube asigna automáticamente sus transcodificadores premium **VP9** o **AV1**, preservando una calidad visual drásticamente superior, incluso cuando el espectador selecciona reproducción en 1080p.
2. **Normalización de Audio (Loudness War Finalizada):**
   * YouTube mide la sonoridad integrada del archivo completo mediante el estándar ITU-R BS.1770-4.
   * Su objetivo estricto es **-14.0 LUFS**. Si subes a -10 LUFS, el reproductor aplicará una atenuación automática de volumen (*Volume Normalization / Content Loudness*) de -4.0 dB. Subir más fuerte no hace que suene más fuerte; solo destruye la dinámica de tus diálogos y música.
3. **Optimización Web (Átomo `moov` al inicio):**
   * Todo vídeo exportado en contenedor MP4 debe procesarse con la bandera `faststart` (`-movflags +faststart` en FFmpeg). Esto ubica los metadatos al inicio del contenedor, permitiendo a YouTube procesar el archivo en tiempo real durante la subida sin tener que esperar a recibir el 100% de los bytes.
