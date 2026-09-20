# 📝 Subtitulado, Tipografía Dinámica y Accesibilidad

El subtitulado en redes sociales ha dejado de ser un mero recurso de accesibilidad para convertirse en el **motor principal de retención y comprensión auditiva**. Más del 70% de los usuarios consumen vídeos en espacios públicos o laborales con el volumen bajo o silenciado.

---

## 1. Tipologías de Subtítulos: ¿Burn-in o Sidecar?

| Modalidad | Formato | Ventajas | Desventajas | Uso Recomendado |
| :--- | :---: | :--- | :--- | :--- |
| **Quemados (Burn-in / Hardcoded)** | Integrados en el píxel de vídeo | Animaciones cinéticas (estilo Hormozi), control total de tipografía, colores y posición. | No se pueden desactivar ni traducir automáticamente. | **TikTok, Reels, Shorts y formatos de alta retención.** |
| **Sidecar (Soft Subtitles)** | Archivo externo `.srt` o `.vtt` | Indexación SEO por Google/YouTube, accesibilidad para lectores de pantalla, multilingüe. | No admite estilos visuales llamativos; la plataforma decide la tipografía. | **YouTube Long-Form y LinkedIn.** |

---

## 2. Anatomía del Subtítulo de Alta Retención (Estilo Micro-Chunking)

Los subtítulos extensos de 3 o 4 líneas aburren la mirada y ralentizan la percepción. El estándar de alta retención aplica el principio de **micro-fragmentación**:

* **Palabras por Pantalla:** Máximo de **1 a 3 palabras simultáneas**.
* **Duración por Fragmento:** Entre **0.2 y 0.6 segundos** por grupo de palabras, sincronizado al milisegundo con la sílaba hablada.
* **Palabra Destacada (Karaoke Highlighting):** Resaltar la palabra de énfasis en un color contrastante (amarillo neón `#FFE500`, verde lima `#00FF66` o cian `#00F0FF`).
* **Tipografía Recomendada:** Tipografías sans-serif pesadas (*Bold* o *Black*), de formas geométricas claras y legibles a escala reducida:
  * **The Bold Font**
  * **Montserrat Black**
  * **Futura Bold / Extra Bold**
  * **Komika Axis**
  * **Inter Extra Bold**

---

## 3. Especificaciones de Estilo y Contraste

Para garantizar legibilidad sobre cualquier fondo (escenas oscuras, cielos brillantes, ropa blanca o fondos abigarrados):

1. **Tamaño de Fuente en 1080×1920:** Entre **60 pt y 80 pt**.
2. **Trazo Exterior (Stroke):** Trazo negro continuo de **4 a 6 px** de grosor alrededor de las letras.
3. **Sombra Paralela (Drop Shadow):**
   * Color: Negro con opacidad del 80% al 100%.
   * Distancia: 4 a 6 px.
   * Desenfoque: 8 a 12 px en ángulo de 135° hacia abajo.
4. **Caja de Fondo (Bounding Box):** Si el fondo es extremadamente caótico, utiliza una caja de fondo rectangular semitransparente (negro al 60% de opacidad) con esquinas redondeadas (*border-radius*).
