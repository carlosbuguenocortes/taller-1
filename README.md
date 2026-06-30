# Biblical Text Mining

Proyecto desarrollado para el Laboratorio 2 de la asignatura **Programación Científica** de la **Universidad Católica del Norte**.

## Descripción

Este proyecto implementa un sistema completo de análisis del texto bíblico utilizando técnicas clásicas de Procesamiento de Lenguaje Natural (Natural Language Processing, NLP). Se trabaja sobre el corpus de la **Biblia Reina-Valera 1960** con el objetivo de estudiar patrones lingüísticos, analizar similitud entre textos, construir modelos de clasificación y generar texto de manera probabilística.

El sistema integra distintas etapas del procesamiento de texto, incluyendo preprocesamiento, representación vectorial, análisis exploratorio, recuperación de información, clasificación supervisada, modelos de lenguaje basados en n-gramas y análisis de sentimiento.

El desarrollo se realizó siguiendo un enfoque de **Programación Orientada a Objetos**, privilegiando la modularidad, reutilización de código y facilidad de mantenimiento.

---

# Tabla de Contenidos

- Descripción
- Objetivos
- Funcionalidades
- Tecnologías utilizadas
- Estructura del proyecto
- Instalación
- Ejecución
- Flujo del sistema
- Modelos implementados
- Resultados
- Discusión
- Cumplimiento del laboratorio
- Trabajo futuro
- Integrantes
- Licencia

---

# Objetivos

El proyecto tiene como principales objetivos:

- Implementar un pipeline completo de preprocesamiento de texto.
- Construir una representación vectorial mediante TF-IDF.
- Implementar manualmente la similitud del coseno.
- Analizar relaciones entre libros y versículos mediante técnicas de visualización.
- Construir un motor de búsqueda semántico.
- Clasificar automáticamente versículos según su libro de origen.
- Generar texto utilizando modelos probabilísticos basados en n-gramas.
- Analizar el sentimiento presente en el corpus bíblico.

---

# Funcionalidades

## Preprocesamiento

- Conversión del texto a minúsculas.
- Eliminación de signos de puntuación.
- Eliminación de números y caracteres especiales.
- Tokenización.
- Eliminación de stopwords.
- Construcción del vocabulario.
- Cálculo de frecuencias de palabras.

---

## Representación vectorial

Se implementa manualmente el algoritmo TF-IDF utilizando los conceptos de:

- Term Frequency (TF)
- Inverse Document Frequency (IDF)
- TF-IDF

No se utiliza `TfidfVectorizer` de Scikit-Learn, cumpliendo los requerimientos establecidos en el laboratorio.

---

## Motor de búsqueda semántico

El sistema permite ingresar una consulta libre y recuperar los **K versículos más similares** utilizando:

- Representación TF-IDF.
- Similitud del coseno implementada manualmente.

---

## Clasificación automática

Se implementa un clasificador basado en **Multinomial Naive Bayes** para predecir el libro al que pertenece un versículo.

La evaluación considera:

- Accuracy.
- Matriz de confusión.

---

## Modelos de lenguaje

Se implementan los siguientes modelos probabilísticos:

- Unigrama
- Bigrama
- Trigrama
- Cuatrigrama

Cada modelo permite generar texto sintético a partir de una palabra inicial seleccionada por el usuario.

---

## Análisis de sentimiento

Se calcula la polaridad de cada versículo utilizando TextBlob y posteriormente se agregan los resultados por libro para analizar el comportamiento emocional del corpus.

---

# Visualizaciones

El sistema genera automáticamente diversas visualizaciones para facilitar el análisis del corpus.

- Heatmap de similitud entre libros.
- Distribución de longitud de versículos.
- Frecuencia de palabras.
- Nube de palabras.
- Proyección bidimensional mediante PCA.
- Evolución del sentimiento promedio por libro.

---

# Tecnologías utilizadas

| Herramienta | Propósito |
|-------------|-----------|
| Python | Lenguaje principal |
| Pandas | Manipulación de datos |
| NumPy | Cálculo numérico |
| Matplotlib | Visualización |
| Scikit-Learn | PCA y clasificación |
| NLTK | Procesamiento de texto |
| TextBlob | Análisis de sentimiento |
| NetworkX | Grafos de coocurrencia |

---

# Estructura del proyecto

```
biblical-text-mining/
│
├── data/
│   └── bible.csv
│
├── src/
│   ├── dataset.py
│   ├── preprocessor.py
│   ├── tfidf.py
│   ├── visualization.py
│   ├── search_engine.py
│   ├── classifier.py
│   ├── ngram.py
│   ├── sentiment.py
│   └── main.py
│
├── results/
│
├── README.md
├── requirements.txt
└── .gitignore
```

---

# Instalación

Clonar el repositorio:

```bash
git clone https://github.com/usuario/biblical-text-mining.git
```

Ingresar al directorio del proyecto:

```bash
cd biblical-text-mining
```

Instalar las dependencias:

```bash
pip install -r requirements.txt
```

---

# Ejecución

Ejecutar el programa principal:

```bash
python src/main.py
```

---

# Flujo del sistema

```
Carga del corpus
        │
        ▼
Preprocesamiento
        │
        ▼
Construcción del modelo TF-IDF
        │
        ▼
Visualización y análisis exploratorio
        │
        ├── PCA
        ├── Heatmap
        ├── Frecuencia de palabras
        │
        ▼
Motor de búsqueda semántico
        │
        ▼
Clasificación automática
        │
        ▼
Modelos N-Gram
        │
        ▼
Análisis de sentimiento
```

---

# Resultados

| Tamaño del corpus | Accuracy |
|------------------:|---------:|
| 2.000 versículos | 0.84 |
| 10.000 versículos | 0.30 |
| Corpus completo | 0.38 |

Los resultados muestran que el rendimiento del clasificador disminuye conforme aumenta la cantidad de clases y la complejidad del problema. La similitud existente entre distintos libros genera una importante superposición en el espacio de características, dificultando la correcta clasificación de los versículos.

---

# Discusión

Durante el desarrollo se observaron las siguientes características:

- TF-IDF representa correctamente la importancia estadística de las palabras dentro del corpus.
- La similitud del coseno permite recuperar versículos relacionados con una consulta textual.
- Naive Bayes ofrece un buen desempeño en conjuntos de datos pequeños, pero su rendimiento disminuye al aumentar la cantidad de libros.
- Los modelos n-gram generan secuencias con coherencia local, aunque presentan repetición y pérdida de contexto en textos largos.
- El análisis de sentimiento presenta limitaciones debido al lenguaje religioso, el contexto histórico y las características propias de la traducción utilizada.

---

# Cumplimiento del laboratorio

| Requerimiento | Estado |
|---------------|:------:|
| Preprocesamiento | Cumplido |
| Implementación manual de TF-IDF | Cumplido |
| Implementación manual de similitud del coseno | Cumplido |
| Heatmap de similitud entre libros | Cumplido |
| Visualización mediante PCA | Cumplido |
| Motor de búsqueda semántico | Cumplido |
| Clasificación automática | Cumplido |
| Modelos n-gram | Cumplido |
| Análisis de sentimiento | Cumplido |

---

# Trabajo futuro

Como posibles extensiones del proyecto se proponen:

- Incorporar representaciones distribucionales como Word2Vec o FastText.
- Evaluar modelos basados en Transformers (BERT o BETO).
- Implementar modelado de tópicos mediante LDA.
- Desarrollar una interfaz gráfica para facilitar la interacción con el sistema.
- Optimizar el motor de búsqueda mediante índices invertidos.

---

# Integrantes

- Carlos Bugueño
- Constantino Bekios
- Vicente Moyano

---

# Licencia

Este proyecto fue desarrollado exclusivamente con fines académicos para la asignatura **Programación Científica** de la **Universidad Católica del Norte**.
