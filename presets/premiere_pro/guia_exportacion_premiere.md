# 🎬 Guía de Exportación en Adobe Premiere Pro / Media Encoder

Parámetros canónicos de exportación en Adobe Premiere Pro y Adobe Media Encoder para conseguir renders ultranítidos sin artefactos de compresión para redes sociales.

---

## 1. Ajustes del Panel de Exportación (Ctrl + M / Cmd + M)

* **Formato:** H.264.
* **Ajuste preestablecido:** Personalizado (o basado en *Coincidir con origen - Velocidad de bits alta*).

---

## 2. Pestaña "Vídeo"

```text
┌────────────────────────────────────────────────────────┐
│ PREMIERE PRO: AJUSTES DE VÍDEO BÁSICOS                 │
├────────────────────────────────────────────────────────┤
│ • Tamaño de fotograma: 1080 × 1920 (Vertical)          │
│ • Proporción de píxeles: Píxeles cuadrados (1,0)       │
│ • Velocidad de fotograma: 30 fps (o 60 fps)            │
│ • Orden de campos:     Progresivo                      │
│ • Procesar con la máxima profundidad: [ ✔ MARCAR ]     │
│ • Usar calidad de procesamiento máxima: [ ✔ MARCAR ]   │
│                                                        │
│ AJUSTES DE CODIFICACIÓN:                               │
│ • Rendimiento:         Aceleración por hardware        │
│ • Perfil:              Principal o Alto (High)         │
│ • Nivel:               4.2 o 5.1                       │
│                                                        │
│ AJUSTES DE VELOCIDAD DE BITS (BITRATE):                │
│ • Codificación de velocidad: VBR, 1 pase (o 2 pases)   │
│ • Velocidad de bits de destino [Mbps]: 14.00 Mbps      │
│ • Velocidad de bits máxima [Mbps]:     18.00 Mbps      │
└────────────────────────────────────────────────────────┘
```

---

## 3. Pestaña "Audio" y Normalización de Sonoridad Automática

Premiere Pro incluye una función nativa para clavar los -14 LUFS automáticamente durante el render sin plugins externos:

1. En el panel de exportación, ve a la pestaña **Efectos**.
2. Despliega la sección **Normalización de sonoridad**.
3. Marca la casilla de activación.
4. **Estándar de sonoridad:** Selecciona **ITU BS.1770-4** o **EBU R128**.
5. **Sonoridad de destino:** Introduce **-14.0 LUFS**.
6. **Tolerancia:** `0.5 LUFS`.
7. **Pico máximo real (True Peak):** Introduce **-1.0 dBTP**.

> [!TIP]
> Al activar esta opción, Adobe Media Encoder analiza todo el audio de la línea de tiempo en el renderizado y ajusta la ganancia global matemáticamente para que el archivo final cumpla con el estándar sin ninguna distorsión.
