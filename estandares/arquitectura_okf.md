# 🏛️ Arquitectura del Open Knowledge Framework (OKF v1.3) para Edición de Vídeo

El **Open Knowledge Framework (OKF)** en **social-video-specs** es una especificación estructurada, modular y de código abierto concebida para catalogar, estandarizar y operacionalizar todos los parámetros técnicos de la producción y optimización audiovisual para plataformas sociales.

---

## 1. Propósito y Filosofía del Estándar

En el ecosistema de la edición digital, los editores y los creadores de contenido se enfrentan habitualmente a especificaciones dispersas, desactualizadas o contradictorias publicadas en blogs o foros. Además, los sistemas automáticos de edición y los **Agentes de Inteligencia Artificial** carecen de una base de verdad determinista y estructurada que les permita calcular resoluciones, bitrates, safe zones y comandos de transcodificación sin alucinaciones.

El estándar **OKF** resuelve este problema mediante tres pilares fundamentales:

1. **Modularidad Atómica en Markdown + YAML Frontmatter:** Cada plataforma y formato cuenta con un documento autocontenido con metadatos estructurados que los agentes pueden parsear y consultar directamente.
2. **Validación Formal mediante Esquemas JSON (JSON Schema):** Se garantiza que toda especificación cumpla tipos estrictos para resoluciones, tasas de bits, normas de sonoridad LUFS y coordenadas de zonas seguras.
3. **Orientación Práctica y Ejecutable:** Toda especificación se traduce en recetas y presets directamente importables en editores no lineales (DaVinci Resolve, Premiere Pro) y comandos FFmpeg listos para terminales de producción automatizada.

---

## 2. Taxonomía Integral del Repositorio

```text
social-video-specs/
├── README.md                            # Documento rector, prompt maestro y matriz de referencia rápida
├── LICENSE.md                           # Licencia CC BY-SA 4.0 con cláusula de atribución
├── .gitignore                           # Exclusiones de Git
├── manifest.json                        # Manifiesto central OKF v1.3
├── schema/                              # Esquemas JSON Schema formales
│   ├── social_video_spec_schema.json    # Validación de especificaciones técnicas
│   ├── safe_zone_schema.json            # Validación de zonas seguras y áreas de UI
│   └── export_preset_schema.json        # Validación de perfiles de exportación
├── plataformas/                         # Fichas técnicas con metadatos YAML
│   ├── youtube/                         # Long-form 16:9, Shorts 9:16 y Miniaturas
│   ├── instagram/                       # Reels 9:16, Stories 9:16 y Feed 4:5/1:1
│   ├── tiktok/                          # Feed nativo 9:16 y modo horizontal 16:9
│   ├── facebook/                        # Reels, Stories y Vídeo en Feed
│   ├── x_twitter/                       # Vídeo en Feed y límites estándar vs Premium
│   ├── linkedin/                        # Formatos corporativos 1:1, 9:16 y 16:9
│   ├── twitch_kick/                     # Clips verticales y VODs
│   └── pinterest/                       # Video Pins 2:3, 9:16 y 1:1
├── estandares/                          # Fundamentos técnicos de ingeniería audiovisual
│   ├── arquitectura_okf.md              # Esta especificación
│   ├── codificacion_y_codecs.md         # Códecs, contenedores, átomo moov y bitrate
│   ├── audio_lufs_y_masterizacion.md    # Estándar -14 LUFS, True Peak y EQ móvil
│   ├── zonas_seguras_y_composicion.md   # Metodología de safe zones y capas UI
│   ├── subtitulado_y_accesibilidad.md   # Subtítulos kinetic, estilos y safe margins
│   └── checklist_qa_pre_publicacion.md  # Protocolo de control de calidad
├── presets/                             # Perfiles y recetas de render
│   ├── ffmpeg/                          # Comandos y scripts de transcodificación
│   ├── davinci_resolve/                 # Guía de exportación en DaVinci Resolve
│   └── premiere_pro/                    # Guía de exportación en Premiere Pro
├── plantillas/prompts/                  # Biblioteca modular de Prompts para Agentes de IA
│   ├── prompt_maestro_editor_video_rrss.md
│   ├── prompt_01_analisis_formato_plataforma.md
│   ├── prompt_02_ritmo_y_storyboarding.md
│   ├── prompt_03_generacion_subtitulos_safe_zones.md
│   └── prompt_04_control_calidad_qa.md
└── herramientas/                        # Aplicación web local autocontenida
    └── calculadora_video_rrss.html      # Inspector visual, visor de safe zones y conversor
```

---

## 3. Protocolo de Consumo por Agentes de IA

Cuando un Agente de Inteligencia Artificial asiste en un flujo de edición o publicación de vídeo:

1. **Lectura del Manifiesto:** Lee `manifest.json` para indexar las capacidades del estándar.
2. **Identificación de la Plataforma:** Accede a `plataformas/<nombre>/` y recupera los metadatos YAML del formato objetivo.
3. **Cálculo de Parámetros:** Cruza la duración deseada con el bitrate recomendado para verificar que el peso final no exceda el límite de subida (`limites.peso_maximo_mb`).
4. **Verificación de Zonas Seguras:** Aplica los márgenes de `zonas_seguras` para posicionar subtítulos, textos de gancho y logotipos.
5. **Generación de Salida:** Emite el comando FFmpeg o las instrucciones de renderizado para el software de edición indicado por el usuario.
