# BibleText Mining

## Procesamiento de Lenguaje Natural aplicado al análisis de un corpus bíblico


# Resumen

Este proyecto implementa un sistema de análisis computacional sobre un corpus bíblico utilizando técnicas clásicas de Procesamiento de Lenguaje Natural (Natural Language Processing, NLP). El desarrollo considera la construcción de un pipeline completo que abarca desde el preprocesamiento del texto hasta la representación vectorial de documentos, recuperación de información, clasificación automática, generación probabilística de texto y análisis de sentimiento.

El sistema fue desarrollado siguiendo un enfoque de Programación Orientada a Objetos con el propósito de mantener una arquitectura modular, reutilizable y fácilmente extensible.

La implementación utiliza como corpus la **Biblia Reina-Valera 1960**, permitiendo estudiar el comportamiento lingüístico de un conjunto de datos compuesto por miles de versículos distribuidos en distintos libros, capítulos y contextos narrativos.

---

# Objetivos

El proyecto tiene como finalidad implementar un conjunto de técnicas clásicas de minería de texto y procesamiento de lenguaje natural sobre un corpus bíblico.

Los objetivos específicos son los siguientes:

- Implementar un pipeline completo de preprocesamiento textual.
- Construir manualmente la representación vectorial TF-IDF.
- Implementar el cálculo de similitud mediante el coseno.
- Analizar estadísticamente el corpus mediante distintas visualizaciones.
- Aplicar reducción de dimensionalidad utilizando Principal Component Analysis (PCA).
- Desarrollar un motor de búsqueda semántico basado en similitud textual.
- Entrenar un clasificador capaz de identificar el libro al que pertenece un versículo.
- Implementar modelos probabilísticos de lenguaje basados en N-Gram.
- Analizar el comportamiento del sentimiento presente en el corpus.

---

# Características del sistema

El sistema implementa las siguientes funcionalidades.

## Preprocesamiento

El pipeline de procesamiento realiza automáticamente:

- Conversión a minúsculas.
- Eliminación de signos de puntuación.
- Eliminación de caracteres especiales y números.
- Tokenización.
- Eliminación de palabras vacías (stopwords).
- Construcción del vocabulario.
- Cálculo de frecuencias.

---

## Representación vectorial

La representación de documentos se desarrolla mediante una implementación propia del algoritmo TF-IDF.

Se implementan manualmente los siguientes componentes:

- Term Frequency (TF)
- Inverse Document Frequency (IDF)
- TF-IDF

No se utiliza la implementación disponible en Scikit-Learn, cumpliendo las restricciones establecidas en el laboratorio.

---

## Recuperación de información

El proyecto incorpora un motor de búsqueda semántico que recibe una consulta textual y devuelve los K versículos más similares del corpus.

La similitud entre documentos se calcula mediante una implementación propia de la similitud del coseno.

---

## Clasificación automática

Se implementa un clasificador supervisado utilizando el algoritmo **Multinomial Naive Bayes**.

El modelo predice el libro de origen de un versículo utilizando exclusivamente su contenido textual.

La evaluación considera:

- Accuracy.
- Matriz de confusión.

---

## Modelos probabilísticos de lenguaje

Se desarrollan cuatro modelos de generación automática de texto.

- Unigrama
- Bigrama
- Trigrama
- Cuatrigrama

Cada modelo genera secuencias textuales a partir de una palabra inicial definida por el usuario.

---

## Análisis de sentimiento

El sistema calcula la polaridad emocional de cada versículo mediante TextBlob y posteriormente agrega los resultados por libro para analizar la evolución del sentimiento dentro del corpus.

---

# Tecnologías utilizadas

| Tecnología | Descripción |
|------------|-------------|
| Python | Lenguaje principal |
| Pandas | Manipulación de datos |
| NumPy | Cálculo numérico |
| Matplotlib | Visualización |
| Scikit-Learn | PCA y clasificación |
| NLTK | Procesamiento de texto |
| TextBlob | Análisis de sentimiento |
| NetworkX | Grafos de coocurrencia |

---

# Arquitectura del proyecto

```
bible-text-mining/
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
│
├── Informe_Taller2.pdf
├── main.py
├── README.md
├── diagrama_de_clases.png
├── heatmap_libros.png
├── histograma_versiculos.png
├── pca_versiculos.png
└── sentimiento_libros.png
```

---

# Diagrama de clases

La siguiente figura resume la arquitectura orientada a objetos implementada durante el desarrollo.

<p align="center">
<img src="diagrama_de_clases.png" width="900">
</p>

---

# Instalación

Clonar el repositorio

```bash
git clone https://github.com/carlosbuguenocortes/bible-text-mining.git
```

Ingresar al directorio del proyecto

```bash
cd bible-text-mining
```

Instalar las dependencias

```bash
pip install pandas numpy matplotlib scikit-learn textblob
```

---

# Ejecución

Ejecutar el programa principal

```bash
python main.py
```

---

# Flujo general del sistema

```
Corpus bíblico
      │
      ▼
Preprocesamiento
      │
      ▼
Representación TF-IDF
      │
      ▼
Análisis exploratorio
      │
      ├── Frecuencia de palabras
      ├── Heatmap
      ├── PCA
      │
      ▼
Motor de búsqueda
      │
      ▼
Clasificación
      │
      ▼
Modelos N-Gram
      │
      ▼
Análisis de sentimiento
```

---

# Resultados experimentales

El clasificador fue evaluado utilizando distintos tamaños de corpus con el propósito de estudiar el comportamiento del modelo frente al incremento del número de clases.

| Corpus | Accuracy |
|---------|----------|
| 2.000 versículos | 0.84 |
| 10.000 versículos | 0.30 |
| Corpus completo | 0.38 |

Los resultados muestran una disminución progresiva del rendimiento conforme aumenta el tamaño del corpus. Este comportamiento se explica por el incremento del número de clases, la elevada similitud léxica existente entre distintos libros y la superposición del espacio vectorial generado mediante TF-IDF.

---

# Resultados gráficos

## Heatmap de similitud entre libros

<p align="center">
<img src="heatmap_libros.png" width="850">
</p>

---

## Distribución de longitud de versículos

<p align="center">
<img src="histograma_versiculos.png" width="850">
</p>

---

## Proyección bidimensional mediante PCA

<p align="center">
<img src="pca_versiculos.png" width="850">
</p>

---

## Sentimiento promedio por libro

<p align="center">
<img src="sentimiento_libros.png" width="850">
</p>

---

# Discusión

Los resultados obtenidos evidencian que las técnicas clásicas de Procesamiento de Lenguaje Natural permiten representar adecuadamente las características estadísticas del corpus y recuperar documentos relacionados mediante similitud textual.

No obstante, también se observaron limitaciones importantes. La representación TF-IDF no incorpora información semántica del lenguaje, por lo que documentos con significados similares pueden presentar baja similitud cuando utilizan vocabulario diferente.

Asimismo, el rendimiento del clasificador disminuye considerablemente al aumentar la cantidad de libros presentes en el corpus, debido a la superposición existente entre las representaciones vectoriales.

Finalmente, los modelos N-Gram generan secuencias con una adecuada coherencia local, aunque presentan repetición de palabras y pérdida de contexto en textos de mayor longitud.

---

# Limitaciones

Las principales limitaciones identificadas durante el desarrollo corresponden a:

- TF-IDF representa únicamente información estadística del texto.
- Naive Bayes presenta una disminución de rendimiento al aumentar el número de clases.
- Los modelos N-Gram dependen fuertemente del corpus de entrenamiento.
- El análisis de sentimiento presenta limitaciones al trabajar con textos religiosos y traducciones antiguas.

---

# Integrantes

- Carlos Bugueño
- Constantino Bekios
- Vicente Moyano
