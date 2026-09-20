---
id: "plataforma-instagram"
plataforma: "instagram"
nombre: "Instagram"
formatos_disponibles: ["reels_9_16", "stories_9_16", "feed_posts"]
norma_audio_lufs: -14.0
true_peak_dbtp: -1.0
actualizado: "2026"
---

# 📸 Plataforma: Instagram (Especificaciones Técnicas OKF)

Instagram es un entorno visual con una arquitectura de visualización híbrida donde conviven el reproductor inmersivo a pantalla completa (Reels y Stories) con el muro vertical del feed y la cuadrícula estética del perfil.

---

## 🎯 Resumen Ejecutivo de Formatos

| Formato | Relación de Aspecto | Resolución Recomendada | Duración Máx. | Particularidad Crítica | Ficha Técnica |
| :--- | :---: | :---: | :---: | :---: | :--- |
| **Reels** | `9:16` | 1080×1920 | 90 seg (hasta 15 min en subida) | Triple recorte (Feed 4:5 y Cuadrícula 1:1) | [`reels_9_16.md`](reels_9_16.md) |
| **Stories** | `9:16` | 1080×1920 | 60 seg por segmento | Zonas seguras para stickers y mensajes | [`stories_9_16.md`](stories_9_16.md) |
| **Feed Post (Clásico)** | `4:5` / `1:1` | 1080×1350 (4:5) / 1080×1080 (1:1) | 60 minutos | El formato 4:5 ocupa el 100% del viewport vertical | [`feed_posts.md`](feed_posts.md) |

---

## 💡 Claves de Optimización Técnica para Instagram

1. **La Activación Obligatoria de "Subidas en alta calidad":**
   * Por defecto, la app de Instagram ahorra datos reduciendo la calidad del vídeo si detecta una conexión móvil lenta.
   * En la app de Instagram: *Ajustes y privacidad > Uso de datos y calidad del contenido multimedia > Activar 'Subir con la calidad más alta'*.
2. **El "Sweet Spot" de Bitrate (La Trampa de los 50 Mbps):**
   * Si subes un vídeo con un bitrate excesivamente alto (por ejemplo, 60 o 80 Mbps en ProRes o H.264 no optimizado), los servidores de Meta aplican una compresión agresiva y destructiva que genera pixelación, banding y pérdida de fluidez.
   * El rango óptimo (*sweet spot*) para Reels es **12 a 15 Mbps en H.264 High Profile**.
3. **El Doble Recorte del Feed y del Perfil:**
   * En el feed general, tu Reel vertical 9:16 se muestra recortado a **4:5 (1080×1350)**.
   * En la cuadrícula de tu perfil, se muestra recortado en un cuadrado perfecto **1:1 (1080×1080)** centrado.
   * Si colocas títulos o el punto focal fuera de esa zona central de 1080×1080, tu portada y miniatura quedarán mutiladas.
