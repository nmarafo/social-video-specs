# ⚙️ Codificación, Códecs y Contenedores para Redes Sociales

La elección correcta del códec, el perfil de compresión y la estructura interna del contenedor de vídeo determina si una pieza audiovisual se visualiza con nitidez cristalina o si el algoritmo de la plataforma la degrada mediante macrobloques y pérdida de detalle.

---

## 1. El Trío de Códecs en Vídeo Web

### A. H.264 / AVC (Advanced Video Coding) — *El Estándar Universal*
* **Compatibilidad:** 100% de dispositivos móviles, navegadores y plataformas.
* **Perfil Obligatorio:** **High Profile (L4.2 o L5.1)**.
* **Uso recomendado:** Formato de entrega primario para Instagram, TikTok, Facebook, LinkedIn y X.
* **Espacio de color:** Rec.709 con submuestreo de croma **YUV 4:2:0** de 8 bits.

### B. H.265 / HEVC (High Efficiency Video Coding)
* **Eficiencia:** Ofrece un ahorro de entre el 30% y el 50% de tasa de bits respecto a H.264 a igualdad de calidad percibida.
* **Uso recomendado:** Vídeos 4K en YouTube, subidas desde dispositivos iPhone recientes y archivo de másteres intermedios ligeros.

### C. VP9 y AV1 — *Los Códecs de Próxima Generación de YouTube*
* **Eficiencia:** AV1 es un códec abierto y libre de regalías desarrollado por la *Alliance for Open Media* (AOMedia) que supera a HEVC en un 20% en compresión.
* **Cómo forzar su activación:** YouTube utiliza AVC1 para 1080p estándar en la mayoría de cuentas, pero conmuta automáticamente a **VP9 o AV1** cuando el vídeo se sube en resolución **1440p (2K)** o superior.

---

## 2. La Anatomía del Contenedor MP4 y el Átomo `moov`

Un archivo `.mp4` es un contenedor basado en el formato de archivo multimedia base ISO (ISO/IEC 14496-12). Se organiza internamente en bloques denominados "átomos" o "boxes":

* **Átomo `mdat` (Media Data):** Contiene los paquetes crudos de audio y vídeo codificados (el grueso de los gigabytes del archivo).
* **Átomo `moov` (Movie Atom):** Contiene el índice de tiempo, la tasa de fotogramas, la resolución y la tabla de compensación de muestras (*sample offset table*) necesaria para decodificar los datos.

```text
[ Estructura por defecto en muchos NLEs (LENTA EN WEB) ]
┌────────────────────────────────────────────────────────┬──────────────┐
│                      Átomo 'mdat'                      │ Átomo 'moov' │
│               (99.9% de los bytes del vídeo)           │ (Metadatos)  │
└────────────────────────────────────────────────────────┴──────────────┘
▲ Para comenzar la reproducción, el servidor debe descargar hasta el último byte.

[ Estructura Optimizada para Streaming (FASTSTART) ]
┌──────────────┬────────────────────────────────────────────────────────┐
│ Átomo 'moov' │                      Átomo 'mdat'                      │
│ (Metadatos)  │               (99.9% de los bytes del vídeo)           │
└──────────────┴────────────────────────────────────────────────────────┘
▲ El reproductor lee los primeros kilobytes y reproduce el vídeo al instante.
```

### Cómo activar FastStart:
* En **FFmpeg:** Incluye siempre el parámetro `-movflags +faststart`.
* En **DaVinci Resolve:** En la pestaña Deliver > Video, marca la casilla **"Network Optimization"**.
* En **Adobe Premiere Pro:** Marca la opción **"Optimizar para web"** o exporta en formato MP4 nativo con perfil moderno.

---

## 3. Estrategias de Control de Tasa de Bits (Rate Control)

1. **VBR 1-Pass (Tasa de Bits Variable en 1 Pase):**
   * El codificador asigna más bits a las escenas complejas (movimiento, explosiones, agua) y menos a las escenas estáticas.
   * Ideal para vídeos verticales rápidos de TikTok, Reels y Shorts donde la velocidad de render es prioritaria.
2. **VBR 2-Pass (Tasa de Bits Variable en 2 Pases):**
   * En el primer pase analiza todo el vídeo; en el segundo distribuye los bits con máxima precisión matemática.
   * Recomendado para vídeos horizontales de YouTube de alta producción (evita picos inesperados).
3. **CRF (Constant Rate Factor) en x264/x265:**
   * Método basado en calidad constante en lugar de tasa de bits fija.
   * **Valores recomendados:**
     * `CRF 18`: Calidad visual prácticamente sin pérdidas (*visually lossless*).
     * `CRF 21`: Calidad excelente para subidas a redes sociales con un tamaño de archivo muy contenido.
     * `CRF 23`: Calidad estándar por defecto.

---

## 4. Solución al "Gamma Shift" de macOS / QuickTime

Uno de los problemas más frecuentes en edición de vídeo es exportar un proyecto con colores y contraste perfectos en DaVinci Resolve o Premiere, y comprobar que al abrirlo en QuickTime o subirlo a la web los colores se ven deslavados o con poco contraste.

* **Causa:** QuickTime y los navegadores basados en WebKit en macOS interpretan los vídeos Rec.709 sin metadatos NCLC como Gamma 1.96 en lugar de Gamma 2.4 / BT.1886.
* **Solución Técnica:**
  * Etiquetar explícitamente el archivo con los metadatos Color Space Tagging: **Rec.709 / Rec.709-A** (en DaVinci Resolve).
  * En FFmpeg: aplicar los flags de color:
    ```bash
    -color_primaries bt709 -color_trc bt709 -colorspace bt709
    ```
