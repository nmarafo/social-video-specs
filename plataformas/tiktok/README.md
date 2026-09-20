---
id: "plataforma-tiktok"
plataforma: "tiktok"
nombre: "TikTok"
formatos_disponibles: ["feed_9_16", "horizontal_16_9"]
norma_audio_lufs: -14.0
true_peak_dbtp: -1.0
actualizado: "2026"
---

# 🎵 Plataforma: TikTok (Especificaciones Técnicas OKF)

TikTok es el estándar de referencia en vídeo vertical de formato corto (*short-form content*). Su reproductor cuenta con la mayor densidad de elementos interactivos de pantalla de todas las redes sociales, haciendo del respeto a las zonas seguras un requisito ineludible.

---

## 🎯 Resumen Ejecutivo de Formatos

| Formato | Relación de Aspecto | Resolución Recomendada | Duración Máx. | Particularidad Crítica | Ficha Técnica |
| :--- | :---: | :---: | :---: | :---: | :--- |
| **Feed Vertical Nativo** | `9:16` | 1080×1920 | 10 minutos (hasta 60 min en cuentas selectas) | Gran densidad de UI en margen derecho e inferior | [`feed_9_16.md`](feed_9_16.md) |
| **Modo Horizontal Paisaje** | `16:9` | 1920×1080 | 10 a 60 minutos | Botón flotante 'Pantalla completa' en móvil | [`horizontal_16_9.md`](horizontal_16_9.md) |

---

## 💡 Claves de Optimización Técnica para TikTok

1. **La Interfaz "Pesada" (El Lado Derecho e Inferior):**
   * El botón de perfil con el signo +, el corazón, los comentarios, los favoritos/guardados, el botón de compartir y el disco de vinilo giratorio del audio forman una columna ininterrumpida a lo largo de los **150 px derechos**.
   * La descripción de texto puede expandirse hasta ocupar hasta **400 px** en la zona inferior.
2. **Ajuste de Exportación para Evitar la Compresión Agresiva:**
   * No exportes a 4K para TikTok; la app suele tardar más en procesarlo y su re-escalado automático a 1080p introduce artefactos.
   * Exporta a **1080×1920 nativo a 30 o 60 fps** con un bitrate de entre **10 y 15 Mbps**.
3. **Sincronización con el Hook Auditivo:**
   * El audio en TikTok suele ser el elemento catalizador del algoritmo (*trending sounds*).
   * Siempre masteriza tu voz a **-14 LUFS** y comprime el rango dinámico para que los diálogos se entiendan perfectamente por encima de los altavoces de baja fidelidad de los teléfonos móviles.
