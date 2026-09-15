# Análisis de Experiencia del Cliente de Olist

**Español** | [English](README.md)

Análisis estadístico y probabilístico de aproximadamente **99.441 pedidos de comercio electrónico en Brasil** para estudiar satisfacción del cliente, desempeño logístico, comportamiento de compra y confiabilidad de vendedores.

Desarrollado con **Python, Pandas, NumPy, SciPy, Scikit-learn, Matplotlib y Seaborn**.

> Este proyecto fue desarrollado como un caso académico de Ciencia de Datos en la Universidad de La Sabana utilizando el Brazilian E-Commerce Public Dataset by Olist. Se presenta como proyecto de portafolio para demostrar habilidades en razonamiento estadístico, modelado probabilístico, análisis de datos y machine learning.

## Problema de negocio

Un marketplace necesita entender qué factores están asociados con la satisfacción de sus clientes y el desempeño de sus vendedores para respaldar decisiones operativas con evidencia cuantitativa.

El proyecto estudia la experiencia del cliente desde diferentes perspectivas:

- Desempeño de entrega y reseñas negativas
- Comportamiento de productos y medios de pago
- Distribuciones estadísticas de variables operativas
- Confiabilidad de vendedores con información limitada
- Diversidad de categorías de producto
- Diferencias geográficas en calificaciones
- Predicción de reseñas negativas

## Dataset

El análisis utiliza el **Brazilian E-Commerce Public Dataset by Olist**, con aproximadamente **99.441 pedidos entre 2016 y 2018** distribuidos en 9 archivos CSV relacionales con información de clientes, pedidos, ítems, pagos, reseñas, productos, vendedores y geolocalización.

Los CSV originales no están incluidos en este repositorio. El dataset público de Olist debe descargarse desde Kaggle y ubicarse en las rutas requeridas por el notebook antes de ejecutar el análisis.

## Enfoque analítico

El proyecto combina análisis exploratorio, probabilidad, inferencia estadística, ajuste de distribuciones, teoría de la información, razonamiento Bayesiano y clasificación.

Las principales técnicas utilizadas son:

- Probabilidad condicional
- Teorema de Bayes
- Máxima verosimilitud y comparación mediante AIC
- Ajuste de distribuciones paramétricas
- Esperanza y varianza
- Prueba Chi-cuadrado de independencia
- Análisis de correlación
- Actualización Bayesiana Beta-Binomial
- Entropía de Shannon
- Clasificación logística y entropía cruzada/log-loss
- Divergencia de Kullback-Leibler

## Resultados principales

### Entregas y experiencia del cliente

Los pedidos con tiempos de entrega superiores al umbral promedio definido presentaron una **probabilidad de reseña negativa de 21,0%**, frente a **8,2%** para los pedidos clasificados como entregados a tiempo. Esto representa aproximadamente **2,55 veces mayor probabilidad de reseña negativa**.

Aplicando el teorema de Bayes, la probabilidad de que un pedido hubiera llegado tarde aumentó desde un prior de **8,0%** hasta un posterior de **33,7%** después de observar una reseña negativa.

### Modelado de distribuciones

El tiempo de entrega presentó un mejor ajuste mediante una distribución **Log-Normal** que mediante una Gamma según AIC:

| Distribución | AIC |
|---|---:|
| Log-Normal | 646.576 |
| Gamma | 647.288 |

El peso de los productos también favoreció Log-Normal frente a Gamma utilizando el estadístico Kolmogorov-Smirnov:

| Distribución | Estadístico KS |
|---|---:|
| Log-Normal | 0,066 |
| Gamma | 0,139 |

### Comportamiento de compra

El método de pago y la categoría de producto no resultaron independientes en la muestra analizada (**χ² = 405,2, p < 0,001**).

El tiempo de entrega y la calificación presentaron una correlación negativa de **r = -0,33**, lo que indica que entregas más largas tienden a estar asociadas con calificaciones más bajas.

La categoría `fixed_telephony` presentó la mayor varianza del ticket promedio, indicando una alta heterogeneidad de precios dentro de esa categoría.

### Evaluación Bayesiana de vendedores

Se utilizó un modelo Beta-Binomial para actualizar la confiabilidad estimada de un vendedor nuevo.

El prior poblacional fue de **75,5%** y la estimación posterior aumentó a **83,7% después de 5 ventas con buena calificación**.

Este ejemplo demuestra cómo la actualización Bayesiana permite evaluar vendedores cuando existe poca información nueva disponible.

### Diversidad del catálogo

El catálogo presentó una entropía de Shannon de **4,71 bits**, frente a un máximo teórico de **6,15 bits** para el espacio de categorías analizado.

Esto indica que existe diversidad de categorías, aunque una parte importante de la actividad se concentra en un subconjunto de categorías líderes.

### Clasificación de reseñas negativas

Un clasificador logístico para reseñas negativas obtuvo:

- **Log-loss entrenamiento:** 0,324
- **Log-loss prueba:** 0,325

La similitud entre ambos valores muestra un comportamiento predictivo estable en este experimento. El retraso de entrega aparece como el predictor dominante.

### Comparación geográfica

Las distribuciones de calificaciones de São Paulo y Río de Janeiro fueron relativamente similares, con una **divergencia KL de 0,035 bits**, aunque Río de Janeiro presentó una mayor proporción de reseñas de una estrella.

## Interpretación de negocio

El análisis identifica de manera consistente el **desempeño logístico como una señal importante de la experiencia del cliente**. Los retrasos están asociados con una probabilidad considerablemente mayor de recibir reseñas negativas y aparecen como una variable importante dentro del clasificador.

El proyecto también demuestra cómo herramientas probabilísticas y estadísticas pueden apoyar decisiones de marketplace más allá de un análisis descriptivo, incluyendo evaluación de vendedores, análisis de categorías y comparación del comportamiento de clientes entre regiones.

Los resultados son observacionales y no deben interpretarse como efectos causales sin un diseño causal apropiado.

## Estructura actual del repositorio

```text
.
├── README.md
├── README_ES.md
├── proyecto_olist_completo.ipynb
├── Informe_Gerencial_Olist.docx
├── Guia_Defensa_Oral.md
└── .gitattributes
```

Esta estructura refleja el estado actual del repositorio. El notebook y los documentos complementarios pueden reorganizarse posteriormente como parte de la estandarización del portafolio.

## Reproducir el análisis

Instala las dependencias principales:

```bash
pip install pandas numpy scipy scikit-learn matplotlib seaborn jupyter
```

Descarga el dataset de Olist, configura las rutas de los datos utilizadas por el notebook y ejecuta:

```bash
jupyter notebook proyecto_olist_completo.ipynb
```

## Tecnologías

`Python` · `Pandas` · `NumPy` · `SciPy` · `Scikit-learn` · `Matplotlib` · `Seaborn` · `Jupyter Notebook`

## Habilidades demostradas

`Análisis de Datos` · `Análisis Estadístico` · `Probabilidad` · `Análisis Bayesiano` · `Análisis Exploratorio de Datos` · `Pruebas de Hipótesis` · `Ajuste de Distribuciones` · `Teoría de la Información` · `Machine Learning` · `Interpretación de Negocio`

## Autor

**David Santiago Cifuentes Grimaldo**  
Estudiante de Ciencia de Datos  
Universidad de La Sabana
