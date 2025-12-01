# Bienvenidos al repositorio de Capstone Proyect. 
Dentro de este repositorio se desarrollara el proyecto de final de cursado, nuestro grupo fue titulado **_"Los tres tristes tigres"_**, y no, no comemos trigo en un trigal. Nuestro objetivo es construir un Asistente Conversacional Inteligente (ACI) diseñado para la marca Samsung, capaz de ofrecer una experiencia de soporte y consulta multimodal y empática.

**Integrantes:**

_Fortes Nuñez, Juana Paola._

_Vico, Naim Natanael._

_Rodriguez, Emir Natanael._

# Funciones esperadas del asistente

**Función 1.**
Analisis de Sentimiento. Asegura que el asistente no solo sea resolutivo sino también empático. Permite al System Prompt reconocer la frustración o el agrado del cliente para modular el inicio de la respuesta con un tono humano y adecuado, mejorando la experiencia del usuario.


**Función 2.**
Recepción y procesamiento de mensajes de texto. Convierte el lenguaje humano natural en comandos estructurados que el sistema puede procesar, permitiendo que el chatbot responda automáticamente a las consultas basadas en las reglas y datos definidos.


**Función 3.**
Recepción y procesamiento de notas de voz. Habilita la interacción a través de canales de voz (como asistentes de voz o llamadas telefónicas), ofreciendo una experiencia de comunicación más natural e inclusiva, manteniendo la misma lógica de negocio que el chat escrito.


**Función 4.**
Recepción e interpretación de imagenes. El modelo identifica el producto y genera una descripción breve y relevante, adhiriéndose a las restricciones del System Prompt (enfoque en Samsung y sugerencia de enlace).

# Capstone Project - Asistente Conversacional Inteligente (ACI)

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Telegram Bot API](https://img.shields.io/badge/Telegram-Bot%20API-blue.svg)](https://core.telegram.org/bots/api)
[![Groq](https://img.shields.io/badge/Groq-AI-FF6600?style=flat&logo=groq&logoColor=white)](https://groq.com/)
[![Hugging Face](https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-Transformers-FFD21E?style=flat)](https://huggingface.co/)
[![NLP](https://img.shields.io/badge/NLP-Sentiment%20Analysis-4B8BBE?style=flat)](https://github.com)

Python 3.8+ | Telegram Bot API | Groq AI | 🤗 Hugging Face | NLP Sentiment Analysis

## 📋 Descripción del proyecto 

Asistente Conversacional Inteligente (ACI) diseñado para Samsung, capaz de ofrecer una experiencia de soporte y consulta **multimodal y empática**. El bot procesa mensajes de texto, notas de voz e imágenes, proporcionando respuestas contextualizadas basadas en un dataset empresarial y análisis de sentimiento en tiempo real.

## 🛠️ Tecnologías Utilizadas

- **Python 3.8+**
- **pyTelegramBotAPI** - Interfaz de bot de Telegram
- **Groq API** - LLM (Llama 3.3 70B) y transcripción (Whisper Large v3)
- **Transformers (HuggingFace)** - Análisis de sentimiento con RoBERTuito
- **python-dotenv** - Gestión de variables de entorno

## 📦 Instalación

### Prerrequisitos

- Python 3.8 o superior
- Cuenta de Telegram y Bot Token ([Crear bot con @BotFather](https://t.me/botfather))
- API Key de Groq ([Obtener en groq.com](https://console.groq.com/))
- Seleccionar solo una versión entre la **Modularizada** o la **integral**
  
### Pasos de Instalación

1. **Clonar el repositorio**
```bash
git clone https://github.com/tu-usuario/samsung-project.git
cd samsung-multimodal-assistant
```

2. **Crear entorno virtual**
```bash
python -m venv venv
source venv/bin/activate  # En Windows: venv\Scripts\activate
```

3. **Instalar dependencias**
```bash
pip install -r requirements.txt
```

4. **Configurar variables de entorno**

Crear archivo `.env` en la raíz del proyecto:
```env
TELEGRAM_TOKEN=tu_token_de_telegram
GROQ_API_KEY=tu_api_key_de_groq
```

5. **Preparar dataset**

Asegurarse de tener el archivo `dataset.json` con la estructura de información empresarial de Samsung.

## 🚀 Uso

### Ejecutar el bot

```bash
python main.py
```

El bot cargará automáticamente:
- Modelo de análisis de sentimiento (RoBERTuito)
- Dataset empresarial
- Conexiones a APIs de Telegram y Groq

### Comandos Disponibles

- `/start` o `/help` - Mensaje de bienvenida y descripción de servicios
- **Texto** - Consultas generales sobre productos y servicios Samsung
- **Nota de voz** - Transcripción automática + respuesta contextualizada
- **Imagen** - Análisis visual de productos + recomendaciones

## 🎯 System Prompt - Lineamientos de Respuesta para el asistente

El asistente está configurado con reglas estrictas:

1. Solo responde información del dataset
2. No inventa ni añade información externa
3. Sugiere contacto oficial si la información no está disponible
4. Respuestas empáticas que reconocen el estado emocional del cliente
5. Utiliza un lenguaje profesional y resolutivo
6. No comparte datos sensibles del personal
7. Puede utilizar hasta 3 emojis por mensaje

## 📈 Modelo de Análisis de Sentimiento

**Modelo:** `pysentimiento/robertuito-sentiment-analysis`

Clasifica mensajes en 5 categorías con emojis representativos:
- ⭐⭐⭐⭐⭐ (5 stars) - 😊
- ⭐⭐⭐⭐ (4 stars) - 🙂
- ⭐⭐⭐ (3 stars) - 😐
- ⭐⭐ (2 stars) - 😟
- ⭐ (1 star) - 😠

## 🔧 Configuración Avanzada para el modelo

### Ajustar temperatura del modelo

En `get_groq_response()`:
```python
temperature=0.3  # Mayor = más creativo, Menor = más determinista
```

### Modificar tokens máximos

```python
max_tokens=500  # Ajustar según longitud de respuestas deseada
```

## 📝 Estructura del Dataset

```json
{
  "company_info": {
    "name": "Samsung",
    "description": "...",
    "contact": "..."
  },
  "products": [...],
  "faq": [...],
  "links": [...]
}
```

## 🐛 Solución de Problemas

### El bot no responde
- Verificar que el token de Telegram sea correcto
- Revisar conexión a internet
- Comprobar logs en consola

### Error al cargar modelo de sentimiento
```bash
pip install --upgrade transformers torch
```

### Transcripción de voz falla
- Verificar API Key de Groq
- Comprobar formato del audio (el bot convierte automáticamente a .ogg)
- Hablar claro

## 🤝 Contribuciones

Este es un proyecto académico de fin de cursado. Las contribuciones, sugerencias y reportes de bugs son bienvenidos a través de issues o pull requests. 

## 📧 Contacto

Para consultas sobre el proyecto, contactar a cualquiera de los integrantes del equipo.

---

⭐ **Proyecto Final de Cursado** - Los Tres Tristes Tigres 🐯🐯🐯
