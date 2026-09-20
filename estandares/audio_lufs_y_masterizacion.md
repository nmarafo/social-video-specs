# 🔊 Estándares de Audio, Sonoridad LUFS y Masterización Móvil

El audio representa el 50% de la experiencia audiovisual y, en redes sociales, es frecuentemente el detonante del abandono (*drop-off*) temprano si el volumen es inconsistente, estridente o inaudible en los altavoces de los teléfonos móviles.

---

## 1. Fundamentos de Medición: LUFS y True Peak

A diferencia de los vúmetros analógicos tradicionales (VU) o los medidores de picos digitales de muestra (dBFS Sample Peak), la industria moderna se rige por el estándar **ITU-R BS.1770-4** y la norma europea **EBU R128**:

* **LUFS (Loudness Units relative to Full Scale):** Unidad psicocústica de medida que evalúa cómo el oído humano percibe el volumen medio ponderado a lo largo del tiempo, aplicando una curva de filtrado K (*K-weighting*) que enfatiza las frecuencias medias y altas.
* **Integrated Loudness (Sonoridad Integrada):** El valor medio continuo de sonoridad desde el segundo cero hasta el último segundo del vídeo.
* **True Peak (Pico Real en dBTP):** Medición de los picos inter-muestra (*inter-sample peaks*). Cuando el audio digital se convierte a analógico en los auriculares o altavoces del móvil, las muestras interpoladas pueden superar los 0 dBFS reales y generar distorsión armónica áspera (*clipping* digital).

---

## 2. El Estándar Unificado para Redes Sociales

```text
┌─────────────────────────────────────────────────────────────────────────────┐
│ 🎯 OBJETIVO CANÓNICO PARA REDES SOCIALES (YouTube, Reels, TikTok, X, etc.)   │
│                                                                             │
│ • Sonoridad Integrada:   -14.0 LUFS (Tolerancia ±1.0 LUFS)                  │
│ • True Peak Máximo:      -1.0 dBTP (Ceiling estricto de seguridad)          │
│ • Rango de Sonoridad:    LRA entre 4.0 y 8.0 LU (control dinámico móvil)    │
│ • Frecuencia de Muestreo: 48.000 Hz (48 kHz, estándar broadcast/vídeo)      │
│ • Códec y Bitrate:       AAC-LC a 256 - 320 kbps (estéreo 2.0)              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### ¿Qué ocurre si no respetas los -14.0 LUFS?
1. **Si tu vídeo es demasiado fuerte (ejemplo: -9 LUFS):**
   * Plataformas como YouTube aplicarán una atenuación lineal obligatoria (ej. `-5.0 dB`), mostrada en la opción *"Estadísticas para nerds"* como `Volume / Normalized`.
   * Habrás sacrificado la dinámica de tu mezcla y aplastado los transitorios para sonar al mismo nivel final que un vídeo mezclado limpiamente a -14 LUFS.
2. **Si tu vídeo es demasiado bajo (ejemplo: -22 LUFS):**
   * Muchas plataformas móviles no amplifican el audio para evitar saturar el altavoz.
   * El usuario en el metro o en la calle con ruido ambiente no escuchará tu voz, considerará que el vídeo está mal editado y deslizará al siguiente contenido.

---

## 3. Cadena de Procesamiento Vocal para Dispositivos Móviles

Los altavoces de los teléfonos móviles tienen serias limitaciones físicas: no reproducen frecuencias subgraves por debajo de 80-100 Hz y tienden a saturar en agudos punzantes. Sigue esta cadena de procesamiento en tu pista de diálogo:

```text
Entrada Micrófono
      │
      ▼
┌──────────────┐  Corte de frecuencias graves que restan energía sin aportar claridad
│ High-Pass EQ │  Filtro pasa-altos a 80 Hz - 90 Hz (pendiente de 18 o 24 dB/octava).
└──────┬───────┘
      ▼
┌──────────────┐  Atenuación quirúrgica de frecuencias "acartonadas" o resonancias
│ EQ Correctiva│  Dip estrecho (Q alta) entre 300 Hz y 600 Hz.
└──────┬───────┘
      ▼
┌──────────────┐  Compresión de 2 etapas:
│ Compresores  │  1. Compresor rápido (Opto o FET) para contener picos (2-3 dB de reducción).
│  en Cascada  │  2. Compresor VCA suave (ratio 2:1 a 3:1) para unificar la voz general.
└──────┬───────┘
      ▼
┌──────────────┐  Atenuación de sibilancias molestas ("s", "ch", "t")
│   De-Esser   │  Rango de detección entre 5.5 kHz y 8 kHz.
└──────┬───────┘
      ▼
┌──────────────┐  Potenciación sutil de inteligibilidad y presencia
│ EQ Creativa  │  Realce suave tipo campana en 3.5 kHz y tipo shelf en 10 kHz.
└──────┬───────┘
      ▼
┌──────────────┐  Limitación transparente que asegura sonoridad final sin distorsión
│ True Peak    │  Ceiling en -1.0 dBTP.
│   Limiter    │  Ajuste del umbral para situar la salida integrada en -14 LUFS.
└──────────────┘
```

---

## 4. Normalización Automática con FFmpeg (`loudnorm`)

Para verificar y normalizar el audio de cualquier vídeo al estándar sin abrir un software de audio:

### Pase de Normalización en 1 Línea:
```bash
ffmpeg -i video_entrada.mp4 -c:v copy -af loudnorm=I=-14:TP=-1.0:LRA=7 -c:a aac -b:a 256k video_normalizado.mp4
```

* `-c:v copy`: Mantiene el vídeo intacto sin pérdidas de tiempo ni de calidad de imagen.
* `loudnorm=I=-14:TP=-1.0:LRA=7`: Aplica el algoritmo oficial EBU R128 ajustando la sonoridad a -14 LUFS y el True Peak a -1.0 dBTP.
