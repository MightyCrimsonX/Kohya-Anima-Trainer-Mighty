# Kohya-Anima-Trainer-Mighty
# 🎨 Kohya Anima Trainer — MightyCrimson Edition

Colección de notebooks de Google Colab diseñados para entrenar **LoRAs** de forma sencilla usando **Kohya_ss** y la interfaz gráfica de **Lora Easy Training Scripts**, con soporte especial para el modelo **Anima**.

&gt; ⚡ Entrena LoRAs de anime, personajes, estilos y más directamente desde Colab con una UI moderna y fácil de usar.

---

## 📦 Contenido del Repositorio

| Archivo | Descripción |
|---------|-------------|
| [📘 Guía de Uso](Guia_EasyTrainerScript.md) | Guía paso a paso en español para configurar y usar los notebooks |
| [🚀 Easy Trainer Script](MightyCrimson_EasyTrainerScript.ipynb) | Notebook principal para entrenar LoRAs (SDXL / Illustrious) |
| [🌸 Lora Anima Trainer](MightyCrimson_LoraAnimaTrainer.ipynb) | Notebook especializado para entrenar LoRAs del modelo **Anima** |

---

## 🚀 Notebooks

### 1. MightyCrimson — Easy Trainer Script
Notebook general para entrenar LoRAs usando la UI de **Lora Easy Training Scripts** como frontend.

- Soporta modelos base **SDXL** e **Illustrious**
- Compatible con múltiples tipos de red: **LoRA, LoCon, LoHa, LoKr, DyLoRA**
- Configuración avanzada de optimizadores, schedulers y sample previews
- Backend en Colab + UI local vía Gradio / Cloudflare tunnel

📎 [Abrir en Colab](https://colab.research.google.com/github/MightyCrimsonX/Kohya-Anima-Trainer-Mighty/blob/main/MightyCrimson_EasyTrainerScript.ipynb)

---

### 2. MightyCrimson — Lora Anima Trainer
Notebook especializado para entrenar LoRAs del modelo **Anima V1**, un modelo de generación de imágenes anime.

- Incluye descarga automática de modelos Anima, VAE y Text Encoder
- Parámetros preconfigurados para el ecosistema Anima
- Compatible con el mismo sistema de UI local que el notebook anterior

📎 [Abrir en Colab](https://colab.research.google.com/github/MightyCrimsonX/Kohya-Anima-Trainer-Mighty/blob/main/MightyCrimson_LoraAnimaTrainer.ipynb)

---

## 📖 Guía de Uso

Para aprender a usar cualquiera de los notebooks, consulta la guía completa que explica:

- ✅ Instalación de la UI de Lora Easy Training Scripts
- ✅ Configuración de **General Args** (modelo base, VAE, resolución)
- ✅ Configuración de **Network Args** (tipo de LoRA, dim, alpha)
- ✅ Configuración de **Optimizer Args** (optimizador, learning rate, scheduler)
- ✅ Configuración de **Saving Args** (carpeta de salida, nombre, formato)
- ✅ Configuración de **Sample Args** (previews durante el entrenamiento)
- ✅ Configuración de **Anima Args** (modelos específicos de Anima)
- ✅ Configuración de **Subset Args** (dataset, repeats, tags, captions)
- ✅ Rutas de modelos predefinidas en Colab
- ✅ Cómo conectar la UI local con el backend de Colab

📎 [Leer la Guía Completa](Guia_EasyTrainerScript.md)

---

## 🧰 Requisitos

- **Google Colab** (se recomienda GPU T4 o superior)
- **Python 3.10+** (para la UI local)
- **Git** (para clonar Lora Easy Training Scripts)

---

## 📁 Modelos Soportados (Rutas en Colab)

| Modelo | Ruta en Colab |
|--------|---------------|
| Illustrious XL v0.1 | `/content/models/Illustrious-XL-v0.1.safetensors` |
| Illustrious XL v2.0 | `/content/models/Illustrious-XL-v2.0.safetensors` |
| SDXL VAE | `/content/models/sdxl_vae.safetensors` |
| **Anima Base** | `/content/models/anima-base-v1.0.safetensors` |
| **Anima VAE** | `/content/models/qwen_image_vae.safetensors` |
| **Anima Text Encoder** | `/content/models/qwen_3_06b_base.safetensors` |

---

## 🖼️ Vista Previa de la UI

La interfaz de Lora Easy Training Scripts incluye paneles organizados para cada aspecto del entrenamiento:

- **General Args** — Modelo base, resolución, semilla, batch size
- **Network Args** — Tipo de LoRA, dimensiones, dropout
- **Optimizer Args** — Optimizador, learning rate, scheduler, SNR
- **Saving Args** — Carpeta de salida, nombre, frecuencia de guardado
- **Sample Args** — Generación de previews durante el entrenamiento
- **Anima Args** — Configuración exclusiva para el modelo Anima
- **Subset Args** — Gestión de datasets, repeats, captions y tags

---

## ⚠️ Notas Importantes

- La UI descargada localmente actúa como **frontend**; el entrenamiento real ocurre en el backend de **Colab**.
- Si usas el almacenamiento interno de Colab (no Google Drive), **descarga tus LoRAs antes de cerrar la sesión** o se perderán.
- Verifica que las rutas de los modelos y datasets estén correctamente escritas si el entrenamiento no inicia.
- Puedes usar el enlace de **Gradio** o **Cloudflare** para conectar la UI con Colab.

---

## 🙏 Créditos

- [Kohya_ss](https://github.com/kohya-ss/sd-scripts) — Scripts de entrenamiento base
- [Lora Easy Training Scripts](https://github.com/derrian-distro/LoRA_Easy_Training_Scripts) — Interfaz gráfica para Kohya_ss
- [MightyCrimsonX](https://github.com/MightyCrimsonX) — Adaptación y notebooks para Colab

---

## 📜 Licencia

Este proyecto se distribuye bajo la misma licencia que los proyectos base (GPL-3.0). Consulta los repositorios originales para más detalles.
