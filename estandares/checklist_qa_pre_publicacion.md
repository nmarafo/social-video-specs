# ✅ Checklist de Control de Calidad (QA) Pre-Publicación

Protocolo de verificación técnica de 10 puntos que todo editor o agente de IA debe comprobar antes de autorizar la publicación de un vídeo en redes sociales.

---

## 📋 Lista de Comprobación Técnica (Pre-Flight Check)

### 1. Resolución y Relación de Aspecto
- [ ] ¿Coincide la relación de aspecto con la plataforma objetivo (`9:16`, `16:9`, `4:5`, `1:1`)?
- [ ] ¿La resolución es nativa (1080×1920 para vertical, 1920×1080 o 2560×1440 para horizontal) sin franjas negras involuntarias (*pillarbox* o *letterbox*)?

### 2. Zonas Seguras y Elementos de Interfaz
- [ ] ¿Los subtítulos dinámicos están ubicados entre **Y: 1050 px y Y: 1350 px**?
- [ ] ¿El margen derecho (últimos 160 px) está libre de gráficos esenciales (TikTok / Reels)?
- [ ] En Reels: ¿el titular y el encuadre principal se entienden dentro del recorte de perfil **1:1 (420 a 1500 px)**?

### 3. Audio y Sonoridad (Loudness)
- [ ] ¿La sonoridad integrada mide **-14.0 LUFS (±1.0 LUFS)** en el medidor ITU-R BS.1770?
- [ ] ¿El True Peak se mantiene por debajo de **-1.0 dBTP** para prevenir saturación digital inter-muestra?
- [ ] ¿La música de fondo está atenuada (*ducking*) entre -18 y -24 dB respecto a la voz durante los diálogos?
- [ ] ¿El audio es estéreo a **48.000 Hz**?

### 4. Codificación y Rendimiento Web
- [ ] ¿El códec de vídeo es **H.264 High Profile** (o HEVC si la plataforma lo admite)?
- [ ] ¿El submuestreo de color es **YUV 4:2:0 a 8 bits**?
- [ ] ¿Está activado el parámetro de streaming inmediato **FastStart (átomo `moov` al inicio)**?
- [ ] ¿La tasa de bits (*bitrate*) está en el rango óptimo (ej. 12-15 Mbps para 1080p vertical) sin exceder los límites?

### 5. Edición, Ritmo y Retención
- [ ] ¿El gancho visual y auditivo comienza en el segundo **0.0** (sin fundidos a negro ni intros vacías)?
- [ ] ¿Se han eliminado silencios muertos, respiraciones excesivas o muletillas (*jump cuts* limpios)?
- [ ] ¿Hay variación visual o cambio de plano cada **2.5 a 4 segundos** (zoom in, b-roll, texto, sound effect)?
