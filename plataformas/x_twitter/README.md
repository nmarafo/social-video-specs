---
id: "plataforma-x-twitter"
plataforma: "x_twitter"
nombre: "X (anteriormente Twitter)"
formatos_disponibles: ["video_feed"]
norma_audio_lufs: -14.0
true_peak_dbtp: -1.0
actualizado: "2026"
---

# ✖️ Plataforma: X (Twitter) (Especificaciones Técnicas OKF)

X (Twitter) se ha transformado progresivamente en una plataforma centrada en el vídeo (*video-first*), introduciendo un reproductor vertical inmersivo de pantalla completa similar a TikTok y capacidades de transmisión y podcasting de larga duración para usuarios con suscripción X Premium / Verified Organizations.

---

## 🎯 Resumen Ejecutivo de Formatos

| Nivel de Usuario | Relación de Aspecto | Resolución Máxima | Duración Máxima | Peso Máximo | Ficha Técnica |
| :--- | :---: | :---: | :---: | :---: | :--- |
| **Cuenta Estándar (Gratuita)** | `16:9`, `1:1`, `9:16` | 1920×1080 (o 1080×1920) | 140 segundos (2 min 20 s) | 512 MB | [`video_feed.md`](video_feed.md) |
| **X Premium (Suscripción)** | `16:9`, `1:1`, `9:16` | 1920×1080 (1080p nativo) | Hasta 3 horas (en web) | Hasta 16 GB | [`video_feed.md`](video_feed.md) |

---

## 💡 Claves de Optimización Técnica para X

1. **Codificación de Audio Estricta:**
   * X solo acepta audio en formato **AAC-LC**. Si subes un vídeo con audio PCM sin comprimir o Dolby AC3 en contenedor MP4, el procesamiento fallará con un error genérico de transcodificación.
2. **Limitación de Bitrate Máximo de Entrada:**
   * X recomienda un bitrate máximo de **25 Mbps**. Subir a tasas superiores provoca un re-escalado muy lento y puede dar timeout en la API de subida de medios.
