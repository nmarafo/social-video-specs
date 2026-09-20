# 📐 Zonas Seguras, Superposiciones de UI y Composición Vertical

En el formato vertical de pantalla completa (9:16), entre el **25% y el 40% del área total del fotograma** está ocupada o potencialmente obstruida por elementos de la interfaz de usuario (UI) de las aplicaciones móviles: botones de interacción, nombres de usuario, leyendas de texto, buscadores y barras de navegación del sistema operativo.

---

## 1. El Concepto de Zona Segura Cuádruple

A diferencia de la televisión tradicional (que distinguía únicamente entre *Action Safe* al 90% y *Title Safe* al 80%), el vídeo para redes sociales debe satisfacer simultáneamente cuatro entornos de visualización:

```text
┌─────────────────────────────────────────────────────────────┐
│ 1. PANTALLA COMPLETA INMERSIVA (Reels, TikTok, Shorts)      │
│    Espacio 9:16 total donde la UI flota sobre el vídeo.     │
├─────────────────────────────────────────────────────────────┤
│ 2. FEED VERTICAL (Instagram y Facebook 4:5)                 │
│    El reproductor recorta el vídeo superior e inferiormente.│
├─────────────────────────────────────────────────────────────┤
│ 3. CUADRÍCULA DE PERFIL (Instagram Grid 1:1)                │
│    El centro del vídeo se muestra como un cuadrado exacto.  │
├─────────────────────────────────────────────────────────────┤
│ 4. RECORTES DE FABRICANTES (Safe Area del Hardware)         │
│    La 'Dynamic Island', el 'Notch' y la barra inferior de   │
│    gestos de iOS y Android.                                 │
└─────────────────────────────────────────────────────────────┘
```

---

## 2. Coordenadas Maestras de Zonas Seguras (Lienzo 1080×1920)

| Parámetro | TikTok | Instagram Reels | YouTube Shorts | Margen Seguro Universal |
| :--- | :---: | :---: | :---: | :---: |
| **Margen Superior (Top)** | 160 px | 220 px | 140 px | **220 px** |
| **Margen Inferior (Bottom)** | 380 px | 420 px | 360 px | **420 px** |
| **Margen Izquierdo (Left)** | 60 px | 60 px | 60 px | **60 px** |
| **Margen Derecho (Right)** | 160 px | 130 px | 140 px | **160 px** |
| **Ventana Central Libre** | Y: 160 a 1540 px | Y: 220 a 1500 px | Y: 140 a 1560 px | **Y: 220 a 1500 px** |
| **Ancho Central Útil** | X: 60 a 920 px | X: 60 a 950 px | X: 60 a 940 px | **X: 60 a 920 px** |

> [!IMPORTANT]
> **La Regla Universal 220 / 420:**  
> Si vas a distribuir el mismo vídeo en **TikTok, Instagram Reels y YouTube Shorts simultáneamente**, mantén todo texto, rostro y gráfico esencial dentro del rectángulo delimitado por:
> * **Superior:** Y ≥ 220 px
> * **Inferior:** Y ≤ 1500 px (1920 - 420)
> * **Izquierda:** X ≥ 60 px
> * **Derecha:** X ≤ 920 px (1080 - 160)

---

## 3. Composición Visual y Enfoque de la Mirada (Eye-Tracking)

En el formato vertical, el patrón de lectura visual no es el patrón en "F" o en "Z" de las pantallas de ordenador, sino un **escaneo vertical centralizado**:

1. **La Línea de Ojos Sagrada (Tercio Superior Seguro):**
   * Sitúa los ojos del presentador o el punto de interés visual entre **Y: 550 px y Y: 750 px**.
   * Esto sitúa la mirada en el punto de máxima atención ergonómica sin colisionar con la cabecera superior.
2. **La Zona de Subtítulos y Gráficos (Tercio Medio-Inferior):**
   * Sitúa los subtítulos dinámicos y palabras clave entre **Y: 1050 px y Y: 1350 px**.
   * Permite que el espectador lea el texto y mire el rostro del presentador sin realizar movimientos sacádicos oculares amplios.
3. **El Área de los Pulgares:**
   * Los primeros 400 px inferiores son la zona natural donde reposan los pulgares del usuario al sostener el teléfono. Nunca sitúes allí información que requiera lectura activa.

---

## 4. Las 4 Técnicas Canónicas de Reencuadre: De Horizontal 16:9 a Vertical 9:16

Cuando se dispone de un metraje original grabado en horizontal (16:9) y se desea optimizar para Reels, TikTok o Shorts, el estándar OKF establece **cuatro estrategias canónicas de reencuadre**:

```text
┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐
│ [  FONDO BLUR ] │ │ [  SUJETO A   ] │ │ [ PAN DINÁMICO] │ │ [ MULTI-CÁMARA] │
│                 │ │  (Cantante / A) │ │                 │ │                 │
│ ┌─────────────┐ │ ├─────────────────┤ │   Travelling    │ │  Corte a Plano  │
│ │ VÍDEO 16:9  │ │ [  SUJETO B   ] │ │   Horizontal      │ │  Vertical 9:16  │
│ └─────────────┘ │ │  (Pianista / B) │ │   de A hacia B  │ │  según la acción│
│ [  FONDO BLUR ] │ │                 │ │                 │ │                 │
└─────────────────┘ └─────────────────┘ └─────────────────┘ └─────────────────┘
  1. Letterbox Blur   2. Split-Stack      3. Pan & Scan       4. Multi-Cámara
```

### Opción 1: Letterbox Blur (Fondo Difuminado Ambiental)
* **Cómo funciona:** El vídeo 16:9 se escala al ancho total (1080 px) y se centra verticalmente. La parte superior e inferior se cubre con un fondo generado a partir del propio vídeo con desenfoque gaussiano y leve atenuación de brillo.
* **Ventajas:** Preserva el 100% del encuadre original sin cortar a ningún protagonista. Los elementos quedan exactamente dentro de la zona segura de perfil 1:1 y feed 4:5.
* **Uso ideal:** Actuaciones grupales, paisajes y planos generales complejos.

### Opción 2: Split-Stack Vertical (Pantalla Dividida 100% Pantalla Completa)
* **Cómo funciona:** El lienzo 9:16 se divide en dos bloques verticales de 1080×960 px. El protagonista A (ej. cantante o entrevistado) se encuadra en la mitad superior y el protagonista B (ej. pianista o entrevistador) en la mitad inferior con una fina línea divisoria.
* **Ventajas:** **Ocupa el 100% de la pantalla del smartphone** sin barras negras ni desenfoques. Ambos artistas permanecen visibles simultáneamente en primer plano.
* **Uso ideal:** Dúos musicales (voz + instrumento), podcasts con dos interlocutores, reacciones en directo o tutoriales con pantalla y webcam.

### Opción 3: Pan & Scan Dinámico / Travelling Virtual (Zoom a Pantalla Completa)
* **Cómo funciona:** Se amplía el metraje para que la altura ocupe los 1920 px completos y una "cámara virtual" se desplaza suavemente de izquierda a derecha (o viceversa) siguiendo al protagonista activo en cada compás o frase.
* **Ventajas:** Sensación cinematográfica de cámara en movimiento continuo (*steadicam* / *slider*) llenando toda la pantalla vertical.
* **Uso ideal:** Vídeos con ritmo fluido donde el foco cambia gradualmente entre dos puntos de interés.

### Opción 4: Multi-Cámara Virtual Inteligente
* **Cómo funciona:** Se extraen planos verticales independientes de cada sujeto y se monta una secuencia con cortes directos en función de los compases musicales o la voz.
* **Ventajas:** Da la apariencia de una producción rodada con múltiples cámaras de televisión verticales de alta gama.
* **Uso ideal:** Vídeos musicales de alta energía, debates rápidos o videoclips.

