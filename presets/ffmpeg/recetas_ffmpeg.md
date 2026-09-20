# 🛠️ Recetas Maestras de FFmpeg para Redes Sociales

Colección de comandos y scripts de terminal FFmpeg optimizados para transcodificación con máxima calidad, recorte vertical, normalización EBU R128 y preparación web inmediata.

---

## 1. Exportación Universal de Alta Calidad (H.264 + FastStart)

El comando canónico para convertir cualquier máster de vídeo a un MP4 perfectamente compatible con todas las redes sociales (TikTok, Reels, Shorts, X, LinkedIn):

```bash
ffmpeg -i input.mov \
  -c:v libx264 -profile:v high -level 4.2 \
  -preset slow -crf 20 \
  -pix_fmt yuv420p \
  -color_primaries bt709 -color_trc bt709 -colorspace bt709 \
  -movflags +faststart \
  -c:a aac -b:a 256k -ar 48000 \
  output_social_ready.mp4
```

* `-preset slow`: Mayor eficiencia de compresión sin aumentar el tamaño de archivo.
* `-crf 20`: Calidad visual prácticamente transparente.
* `-pix_fmt yuv420p`: Garantiza reproducción en el 100% de dispositivos móviles y navegadores.
* `-color_primaries bt709...`: Corrige el desfase de gamma (*gamma shift*) en dispositivos Apple / QuickTime.
* `-movflags +faststart`: Mueve el átomo `moov` al inicio del archivo.

---

## 2. Normalización de Sonoridad Automática (-14 LUFS / -1.0 dBTP)

Aplica el filtro `loudnorm` en modo 2-pass o en modo lineal rápido para cumplir el estándar estricto de audio:

```bash
ffmpeg -i input.mp4 \
  -c:v copy \
  -af "loudnorm=I=-14.0:TP=-1.0:LRA=7.0" \
  -c:a aac -b:a 256k -ar 48000 \
  output_normalized_lufs.mp4
```

> [!NOTE]
> Al usar `-c:v copy`, el flujo de vídeo no se recodifica, lo que permite procesar un archivo completo en cuestión de 2 a 5 segundos sin alterar la imagen.

---

## 3. Conversión de Horizontal (16:9) a Vertical (9:16) con Fondo Difuminado

Técnica estándar para reutilizar contenido panorámico en Shorts, TikTok o Reels sin añadir barras negras vacías:

```bash
ffmpeg -i input_16_9.mp4 -filter_complex \
"[0:v]scale=1080:1920:force_original_aspect_ratio=increase,crop=1080:1920,boxblur=luma_radius=30:luma_power=3[bg]; \
 [0:v]scale=1080:1920:force_original_aspect_ratio=decrease[fg]; \
 [bg][fg]overlay=(W-w)/2:(H-h)/2" \
-c:v libx264 -preset fast -crf 21 -pix_fmt yuv420p -movflags +faststart \
-c:a aac -b:a 256k \
output_blurred_9_16.mp4
```

---

## 4. Quema de Subtítulos con Zona Segura Respetada

Incrusta un archivo `.srt` o `.ass` directamente sobre el vídeo forzando un estilo sans-serif bold y un margen inferior seguro:

```bash
ffmpeg -i input_vertical.mp4 -vf \
"subtitles=subtitulos.srt:force_style='FontName=Montserrat,FontSize=16,PrimaryColour=&H00FFFFFF,OutlineColour=&H00000000,BorderStyle=1,Outline=2,Shadow=2,MarginV=140,Alignment=2'" \
-c:v libx264 -crf 20 -preset medium -pix_fmt yuv420p -movflags +faststart \
-c:a copy \
output_with_subtitles.mp4
```

* `MarginV=140`: Eleva los subtítulos para situarlos holgadamente por encima de la zona de descripción y nombre de usuario.
* `Alignment=2`: Alineación centrada en la parte inferior de la pantalla.

---

## 5. Extracción Rápida del Mejor Fotograma para Miniatura

Extrae un fotograma exacto en alta calidad sin pérdidas en el segundo 2.5:

```bash
ffmpeg -ss 00:00:02.500 -i input.mp4 -vframes 1 -q:v 2 miniatura_fotograma.jpg
```

---

## 6. Split-Stack Vertical 9:16 (Pantalla Dividida 100% Pantalla Completa)

Convierte un plano horizontal 16:9 con dos protagonistas (ej. cantante a la derecha y pianista a la izquierda) en un Reel vertical 9:16 dividiendo la pantalla en dos bloques de 1080×960 con línea divisoria estética:

```bash
ffmpeg -i input_16_9.mp4 -filter_complex \
"[0:v]scale=3414:1920:flags=lanczos,crop=1080:960:1750:50[top]; \
 [0:v]scale=3414:1920:flags=lanczos,crop=1080:960:500:500[bot]; \
 [top][bot]vstack,drawbox=y=959:color=white@0.6:width=1080:height=2:t=fill[v]; \
 [0:a]loudnorm=I=-14.0:TP=-1.0:LRA=7.0[a]" \
-map "[v]" -map "[a]" \
-c:v libx264 -profile:v high -level 4.2 -preset fast -crf 20 -pix_fmt yuv420p \
-c:a aac -b:a 256k -ar 48000 -movflags +faststart \
output_split_stack_9_16.mp4
```

---

## 7. Pan & Scan Dinámico / Travelling Virtual (Zoom a Pantalla Completa 9:16)

Ocupa el 100% de la pantalla vertical 9:16 desplazando la cámara horizontalmente entre el sujeto izquierdo (X=500) y el sujeto derecho (X=1750) de forma cinematográfica suave mediante interpolación temporal matemática:

```bash
ffmpeg -i input_16_9.mp4 -filter_complex \
"[0:v]scale=3414:1920:flags=lanczos,crop=w=1080:h=1920:x='if(lt(t,2.5),500,if(lt(t,5.5),500+1250*(t-2.5)/3.0,if(lt(t,20.5),1750,if(lt(t,23.0),1750-1250*(t-20.5)/2.5,if(lt(t,27.5),500,if(lt(t,30.5),500+1250*(t-27.5)/3.0,1750))))))':y=0,unsharp=5:5:0.6:5:5:0.0[v]; \
 [0:a]loudnorm=I=-14.0:TP=-1.0:LRA=7.0[a]" \
-map "[v]" -map "[a]" \
-c:v libx264 -profile:v high -level 4.2 -preset fast -crf 20 -pix_fmt yuv420p \
-c:a aac -b:a 256k -ar 48000 -movflags +faststart \
output_pan_dinamico_9_16.mp4
```

