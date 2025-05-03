# 🧠 GenAIOps RAG Pipeline con LangChain, FAISS y MLflow en Databricks

Este proyecto demuestra cómo construir un pipeline completo de Retrieval-Augmented Generation (RAG) en un entorno Databricks usando herramientas modernas de GenAIOps. Se trabaja con modelos de lenguaje de Databricks, bases vectoriales en memoria (FAISS), y el tracking de experimentos y despliegue con MLflow.

---

## 📌 ¿Qué contiene el notebook?

El notebook incluye:

1. **Instalación de dependencias** necesarias para trabajar con LangChain, embeddings, FAISS y MLflow.
2. **Descarga y carga de documentos** desde un repositorio GitHub.
3. **Chunking**: partición del contenido de los documentos en fragmentos más pequeños para procesamiento semántico.
4. **Generación de embeddings** usando `DatabricksEmbeddings` y creación de un índice local con FAISS.
5. **Construcción de una RAG Chain** usando LangChain `Runnable` y ChatDatabricks como modelo generador.
6. **Registro del modelo en MLflow** usando `log_model_from_chain`, con inclusión del endpoint LLM como recurso.

---

## 🧰 Tecnologías y librerías utilizadas

| Herramienta | Propósito |
|-------------|-----------|
| **LangChain** | Orquestación de LLMs, retrieval y prompts |
| **FAISS** | Base vectorial en memoria para búsqueda semántica |
| **DatabricksEmbeddings** | API de modelos de embeddings servidos desde Databricks |
| **ChatDatabricks** | LLM servidos vía Model Serving |
| **MLflow** | Tracking, versionado y registro del modelo RAG completo |
| **PyPDF + RecursiveTextSplitter** | Extracción de texto y segmentación de documentos |

---

## ⚠️ Consideraciones

- **No se usa Vector Search gestionado** de Databricks: en su lugar se implementa FAISS local.
- El índice FAISS se guarda en `/tmp`, lo cual **no es persistente entre sesiones**. Por eso, el índice debe regenerarse dentro de `create_chain(model_config)`.
- El registro con MLflow se realiza usando `log_model_from_chain` para evitar escribir archivos en disco.

---

## ✅ Ideal para:

- Demostraciones de GenAIOps en entornos controlados.
- Construcción de copilotos privados usando documentos PDF.
- Integración de LangChain con servicios Databricks reales.

---

## 🚀 Autor / Créditos

Demo creada como parte de la charla **"Del Laboratorio a Producción: Cómo Azure Databricks Impulsa Agentes Autónomos"**, para PyCon 2025.

