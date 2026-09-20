# 🎯 Módulo 01: Selector y Analizador de Formato por Plataforma

Utiliza este prompt para que el agente determine automáticamente las especificaciones óptimas según el objetivo de distribución del usuario.

---

```markdown
Actúa como un Arquitecto de Formatos Audiovisuales. Analiza la siguiente solicitud de vídeo y extrae la matriz de especificaciones exactas:

DATOS DEL PROYECTO:
- Tipo de contenido: [Tutorial / VSL / Vídeo promocional / Gameplay / Podcast / Resumen / Story]
- Plataformas de destino: [YouTube / Instagram / TikTok / X / LinkedIn / Facebook]
- Metraje original: [Resolución, framerate y relación de aspecto de la grabación original]

GENERA:
1. Tabla de resoluciones y relaciones de aspecto recomendadas para cada red indicada.
2. Identificación del formato "Pivote": el formato maestro sobre el que conviene editar primero para minimizar el esfuerzo de reencuadre en las demás redes.
3. Alertas tempranas de recortes (ej. recorte de feed 4:5 en Instagram o cuadrícula de perfil 1:1).
4. Si el origen es horizontal (16:9) y el destino es vertical (9:16), propone las 4 opciones de reencuadre:
   - Letterbox Blur (Fondo difuminado ambiental).
   - Split-Stack (Pantalla dividida superior e inferior a pantalla completa).
   - Pan & Scan Dinámico (Travelling / Movimiento de cámara continuo).
   - Multi-Cámara Virtual (Cortes dinámicos por protagonista).

```
