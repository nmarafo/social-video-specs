# 🎨 Guía de Exportación y Render en DaVinci Resolve

Parámetros exactos para configurar la página **Deliver** en DaVinci Resolve (versiones 18, 19 y superiores) para producir vídeos con la máxima fidelidad de color, compresión optimizada y audio normalizado para redes sociales.

---

## 1. Configuración de la Línea de Tiempo (Project Settings)

* **Resolución de Línea de Tiempo:**
  * Para Reels / Shorts / TikTok: **1080 × 1920** (marcar casilla *"Use vertical resolution"*).
  * Para YouTube Horizontal: **2560 × 1440** (Upscale QHD) o **3840 × 2160** (4K).
* **Frame Rate:** Mantener constante a **30 fps** (o 60 fps si el metraje es deportivo/gaming).
* **Color Science:** DaVinci YRGB Color Managed o DaVinci YRGB estándar con Color Space Transform (CST) a Rec.709.

---

## 2. Parámetros en la Pestaña "Deliver" (Video)

```text
┌────────────────────────────────────────────────────────┐
│ PESTAÑA DELIVER: AJUSTES DE VÍDEO                      │
├────────────────────────────────────────────────────────┤
│ • Format:              MP4                             │
│ • Video Codec:         H.264                           │
│ • Encoder:             NVIDIA / AMD / Apple / Native   │
│ • Network Optimization: [ ✔ ACTIVADA ] (FastStart)     │
│                                                        │
│ QUALITY (Control de Tasa de Bits):                     │
│ • Seleccionar:         Restrict to                     │
│ • Valor:               14000 Kb/s (14 Mbps para 1080p) │
│                                                        │
│ ENCODING PROFILE:                                      │
│ • Profile:             High                            │
│                                                        │
│ ADVANCED SETTINGS (Gestión de Color Mac/PC):           │
│ • Pixel aspect ratio:  Square                          │
│ • Color Space Tag:     Rec.709                         │
│ • Gamma Tag:           Rec.709-A (Vital para macOS)    │
└────────────────────────────────────────────────────────┘
```

> [!TIP]
> **El Secreto del "Rec.709-A" en DaVinci Resolve:**  
> Al seleccionar `Color Space Tag: Rec.709` y `Gamma Tag: Rec.709-A`, DaVinci inyecta los metadatos exactos de color (*nclc 1-1-1*) que impiden que el reproductor QuickTime y las apps de iOS aclaren los negros y desaturen los colores del vídeo exportado.

---

## 3. Parámetros en la Pestaña "Deliver" (Audio)

* **Audio Format:** Linear PCM o AAC.
* **Codec:** AAC.
* **Data Rate:** 320 Kb/s.
* **Sample Rate:** 48.000 Hz (48 kHz).
* **Bit Depth:** 16 o 24 bits.

---

## 4. Normalización en Fairlight (Audio EBU R128)

En lugar de ajustar los faders manualmente:
1. Ve a la pestaña **Fairlight**.
2. Selecciona la pista de salida maestra (*Bus 1*).
3. Abre el plugin nativo **Fairlight FX > Limiter**.
4. Ajusta el **Ceiling** a `-1.0 dBTP`.
5. Abre la ventana **Loudness Meter** y haz clic en *Analyze*. Si tu lectura integrada difiere de `-14.0 LUFS`, ajusta la ganancia del bus maestro hasta igualar el valor objetivo.
