# 📖 Biblical Text Mining

Proyecto desarrollado en el marco del Laboratorio 2 de Procesamiento de Lenguaje Natural.

---

## 🚀 Descripción

Este proyecto implementa un sistema completo de análisis del texto bíblico utilizando técnicas clásicas de Procesamiento de Lenguaje Natural (NLP). Se trabaja sobre el corpus de la Biblia Reina-Valera 1960 en español con el objetivo de estudiar patrones lingüísticos, analizar similitud entre textos y evaluar el rendimiento de distintos modelos.

El sistema desarrollado permite abordar distintas tareas fundamentales de NLP, incluyendo representación vectorial de documentos, clasificación automática, recuperación de información, generación de texto y análisis de sentimiento.

Además, se evalúa el impacto del tamaño del dataset en el desempeño de los modelos, permitiendo comprender sus limitaciones en escenarios reales.

---

## 📊 Funcionalidades principales

- 🔍 Representación de texto mediante TF-IDF  
- 🔎 Búsqueda semántica utilizando similitud del coseno  
- 🤖 Clasificación de versículos con Naive Bayes  
- 🧠 Generación de texto usando modelos n-gram:
  - Bigrama  
  - Trigrama  
  - Cuatrigrama  
- 📉 Reducción de dimensionalidad mediante PCA  
- 📊 Visualización de datos:
  - Heatmap de similitud entre libros  
  - Distribución de longitud de versículos  
  - Proyección PCA  
- 💬 Análisis de sentimiento por libro  

---

## 📁 Estructura del proyecto
bible-text-mining/
├── data/
│   └── bible.csv
├── src/
│   ├── preprocesamiento.py
│   ├── tfidf.py
│   ├── buscador.py
│   ├── ngram.py
│   ├── experimentos.py
│   └── utils.py
├── main.py
└── README.md

---

## ⚙️ Requisitos

Para ejecutar el proyecto se requiere:

- Python 3.8 o superior  
- pip (gestor de paquetes)

### Instalación de dependencias

```bash
pip install pandas numpy matplotlib scikit-learn textblob


📥 Clonar el repositorio
Para obtener el proyecto desde GitHub:
Shellgit clone https://github.com/carlosbuguenocortes/bible-text-mining.gitcd bible-text-mining``Show more lines

▶️ Ejecución
Para ejecutar el sistema:
Shellpython main.pyShow more lines

🔄 Flujo del programa
El sistema realiza automáticamente las siguientes etapas:

Carga del dataset bíblico
Limpieza del texto
Preprocesamiento (tokenización y eliminación de stopwords)
Generación de visualizaciones del corpus
Construcción del modelo TF-IDF
Reducción de dimensionalidad mediante PCA
Búsqueda semántica
Clasificación de versículos con Naive Bayes
Generación de texto con modelos n-gram
Análisis de sentimiento


📈 Resultados obtenidos
El sistema fue evaluado con distintos tamaños de dataset:


DatasetAccuracy2000 versículos~0.8410000 versículos~0.3031102 versículos~0.38
Interpretación de resultados
Se observa que el rendimiento del clasificador disminuye a medida que aumenta la complejidad del problema.
Esto se debe principalmente a:

Incremento en el número de clases
Mayor similitud entre textos
Alta superposición en el espacio de características

Esto dificulta la correcta separación entre clases utilizando modelos simples.

🔎 Ejemplo de búsqueda semántica
Consulta utilizada:
Dios creó la tierra

Resultados esperados

Recuperación de versículos relacionados temáticamente
Coincidencia en términos clave como Dios y tierra
Aparición de textos coherentes como pasajes del libro de Génesis

Interpretación
El modelo TF-IDF permite identificar similitud entre textos basándose en la relevancia de términos. Sin embargo, presenta limitaciones al no comprender el significado semántico profundo del lenguaje.

🧠 Modelos implementados
TF-IDF
Representa los textos como vectores numéricos, permitiendo calcular similitud entre documentos mediante similitud del coseno.

Clasificador Naive Bayes
Se utiliza para clasificar versículos según su libro de origen. Su desempeño es adecuado en datasets simples, pero disminuye en escenarios más complejos.

Modelos N-Gram
Permiten generar texto en base a probabilidades de secuencias de palabras:

Bigrama → secuencias de 2 palabras
Trigrama → secuencias de 3 palabras
Cuatrigrama → secuencias de 4 palabras

A mayor contexto, se obtiene una mejor coherencia local del texto generado.

Análisis de Sentimiento
El análisis se realiza utilizando TextBlob, calculando la polaridad del texto.
Se observa que el corpus presenta valores cercanos a cero, lo que indica una predominancia de lenguaje neutral.

📊 Visualizaciones
El sistema genera automáticamente:

Heatmap de similitud entre libros
Histograma de longitud de versículos
Proyección PCA de los datos
Gráfico de sentimiento promedio por libro

Estas visualizaciones permiten:

Analizar la estructura del corpus
Identificar similitudes entre distintos libros
Evidenciar la dificultad de separación entre clases
Comprender características globales del lenguaje


📘 Conclusiones
El proyecto demuestra que las técnicas clásicas de Procesamiento de Lenguaje Natural permiten analizar de manera efectiva un corpus textual complejo como la Biblia.
Sin embargo, se evidencian importantes limitaciones:

El rendimiento del clasificador disminuye al aumentar la complejidad del dataset
Existe una alta superposición entre clases
TF-IDF no captura relaciones semánticas profundas
El análisis de sentimiento presenta baja capacidad discriminativa

Estos resultados sugieren que problemas más complejos requieren métodos más avanzados, como modelos basados en aprendizaje profundo o representaciones semánticas más sofisticadas.
Finalmente, el trabajo permite comprender tanto el potencial como las limitaciones de las técnicas clásicas de NLP en escenarios reales.

👥 Integrantes

Carlos Bugueño
Constantino Bekios
Vicente Moyano
