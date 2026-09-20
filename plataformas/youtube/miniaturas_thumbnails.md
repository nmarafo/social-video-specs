---
id: "spec-yt-thumbnails"
plataforma: "youtube"
formato: "miniaturas_thumbnails"
relacion_aspecto: "16:9"
resolucion:
  ancho: 1280
  alto: 720
  unidad: "px"
  alternativas_aceptadas:
    - { ancho: 1920, alto: 1080, nombre: "Full HD (Máxima nitidez en 4K)" }
formatos_imagen: ["jpg", "png", "webp", "gif"]
peso_maximo_mb: 2.0
zonas_seguras:
  zona_critica_ui:
    - "Esquina inferior derecha (180px ancho × 60px alto): Badge negro de duración del vídeo (Timecode)."
    - "Esquina inferior izquierda (en TV o consolas): Icono de subtítulos o badges de directo."
tags: ["youtube", "miniaturas", "thumbnails", "portadas"]
---

# 🖼️ Portadas y Miniaturas de YouTube (Thumbnails)

La miniatura es el factor determinante del **CTR (Click-Through Rate)** en YouTube. Una miniatura optimizada puede multiplicar por 5 el alcance orgánico de un vídeo.

---

## 📐 Parámetros Técnicos Canónicos

* **Resolución Recomendada:** 1280×720 px (mínimo 640 px de ancho).
* **Resolución Pro para Displays Retina/4K:** 1920×1080 px (siempre que el peso final se mantenga bajo los 2 MB).
* **Relación de Aspecto:** 16:9 obligatoria.
* **Formatos Aceptados:** `.jpg`, `.png`, `.webp`.
* **Peso Máximo Oficial:** **2.0 MB** (los archivos de 2.01 MB son rechazados por la API).

---

## ⚠️ Zona Prohibida: El Badge de Duración (Timecode)

YouTube superpone automáticamente una etiqueta negra semiopaca con la duración del vídeo en la **esquina inferior derecha**:

* **Área de Riesgo:** Aproximadamente **220 px de ancho por 80 px de alto** desde la esquina inferior derecha en un lienzo de 1280×720.
* **Regla de Oro:** **NUNCA** coloques textos, logos, caras ni elementos esenciales en esa esquina. Cualquier información allí quedará completamente tapada en la app móvil.

---

## 🎨 Directrices de Alto Rendimiento Visual

1. **La Regla del Tamaño Celular (Prueba de los 50px):**
   * Reduce tu miniatura al tamaño de una moneda en tu monitor. Si el texto no se puede leer o el rostro no transmite emoción a ese tamaño, descártala.
2. **Máximo 3 a 4 Palabras:** No repitas el título del vídeo. Usa palabras gatillo que despierten curiosidad o refuercen la promesa.
3. **Contraste y Saturación:** Incrementa el contraste un 15-20% respecto a una foto normal. Aplica un ligero trazo exterior o halo de separación (*drop shadow* o *rim light*) en el sujeto recortado.
