# Proyecto Final: Agente Tutor de IA (Modelos y Simulación)

Este proyecto es un agente conversacional de IA, desarrollado para el curso "IA Generativa y Agentes Inteligentes". El agente actúa como un "Tutor Virtual", capaz de responder preguntas y generar resúmenes basándose en los apuntes de una materia, y guardar dichos resúmenes en Notion.

El sistema está construido con **LangGraph** (para la arquitectura de agentes), un **RAG** local (para la base de conocimiento) y se integra con **LangSmith** (para observabilidad) y **Notion** (para persistencia).

## 🚀 Instalación

El proyecto está diseñado para ejecutarse en un entorno como Google Colab.

1.  **Clonar el Repositorio:**
    ```bash
    git clone [https://www.youtube.com/watch?v=3GymExBkKjE](https://www.youtube.com/watch?v=3GymExBkKjE)
    ```
2.  **Abrir el Notebook:**
    Sube el archivo `.ipynb` a Google Colab.
3.  **Instalar Dependencias:**
    La primera celda del notebook (o el archivo `requirements.txt`) contiene todas las librerías necesarias. Ejecútala para instalar:
    ```bash
    !pip install -qU langchain langgraph langsmith langchain-groq ... (etc.)
    ```

## ⚙️ Configuración (Variables de Entorno)

Para que el agente funcione, debes configurar las siguientes 5 variables de entorno (API keys). En Google Colab, esto se hace en el panel de **Secretos (🔑)**.

1.  **`GROQ_API_KEY`**:
    * **Propósito:** La API key para el modelo de lenguaje (LLM).
    * **Cómo obtenerla:** [https://console.groq.com/keys](https://console.groq.com/keys)

2.  **`LANGCHAIN_API_KEY`**:
    * **Propósito:** La API key para LangSmith (observabilidad).
    * **Cómo obtenerla:** [https://smith.langchain.com/](https://smith.langchain.com/)

3.  **`NOTION_API_KEY`**:
    * **Propósito:** La llave de la "Integración" de Notion.
    * **Cómo obtenerla:** [https://www.notion.so/my-integrations](https://www.notion.so/my-integrations). (Debe empezar con `ntn_...`).

4.  **`NOTION_DATABASE_ID`**:
    * **Propósito:** El ID de 32 caracteres de la base de datos de Notion donde el agente escribirá.
    * **Cómo obtenerla:** De la URL de tu base de datos (ej. `...notion.so/`**`[ID_DE_32_CARACTERES]`**`?v=...`).

5.  **`GOOGLE_API_KEY`**:
    * **Propósito:** (Opcional, si se usa para embeddings) Necesaria para los modelos de Google. En este proyecto la usamos solo como placeholder, ya que los embeddings son locales.
    * **Cómo obtenerla:** [https://ai.google.dev/](https://ai.google.dev/)

## ▶️ Ejecución

Para ejecutar el agente, sigue el orden de las celdas del notebook:

1.  **Celda 1 (Instalaciones):** Instala todas las librerías.
2.  **Celda 2 (Secretos):** Carga las 5 API keys en el entorno.
3.  **Celda 3 (RAG):**
    * **¡Importante!** Sube tus documentos (`.txt`, `.pdf`) a la carpeta `/content/documentos_rag/` en Colab.
    * Ejecuta la celda para crear la base de conocimiento (el `retriever`).
4.  **Celda 4 (Tools):** Define las herramientas (RAG, Notion, Off-topic).
5.  **Celda 5 (LangGraph):** Construye y compila el agente.
6.  **Celda 6 (Chat):** Ejecuta el bucle interactivo para empezar a chatear con tu "Agente Tutor".

### Pruebas sugeridas:

* **Prueba de RAG:** `¿Qué es un informe ejecutivo?`
* **Prueba de Notion:** `Hazme un resumen sobre [TEMA] y guárdalo en Notion.`
* **Prueba Off-topic:** `¿Cómo está el clima?`
