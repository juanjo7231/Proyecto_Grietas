# Proyecto_Grietas
Detección de Grietas e Inclinación de Elementos Estructurales para la Evaluación de Riesgo en Edificaciones

Hola, este es el repositorio de nuestro grupo para el proyecto de la materia Algoritmos y Programación en la UIS Barrancabermeja.

## 1. Integrantes y Plan de Trabajo

Como somos un equipo de solo dos personas, repartimos el trabajo inicial de forma sencilla para ir aprendiendo ambos sin enredarnos:

* **Juan Jose Vega Navas**
  * Rol: Carga y exploración del dataset en Google Colab, conteo de imágenes por clase y verificación de integridad de los archivos.
* **Andres Camilo Gamarra Jaimes** 
  * Rol: Redacción del contexto y problemática, apoyo en la búsqueda del estado del arte y primeras pruebas con el módulo de inclinación usando OpenCV.

*(Conforme avancemos en las siguientes entregas iremos ajustando o alternando las tareas).*

---

## 2. Descripción del Problema y Contexto

En lugares como Barrancabermeja es muy común encontrar casas o edificaciones que con los años van mostrando grietas o pequeñas desviaciones en muros y columnas. Para alguien que no sabe de ingeniería civil, a veces es difícil notar si una grieta es un simple detalle estético en la pintura o si de verdad representa un peligro de daño estructural.

La idea de este proyecto es construir un prototipo básico que nos ayude a evaluar este tipo de situaciones:
1. **Clasificación de grietas:** Un modelo que nos diga si en una foto hay o no una grieta (`Positive` o `Negative`).
2. **Medición de inclinación:** Un script que use visión por computador o  el propio sensor del celular para medir qué tan desviada está una columna o pared respecto a la vertical.
3. **Evaluación de riesgo:** Juntar estas dos cosas para dar una orientación inicial sobre el nivel de riesgo (bajo, medio o alto).

Para esta **Entrega 1**, la meta principal es dejar lista la base: verificar que las fotos carguen bien, explorar los datos y poner a correr un código directo y sin complicaciones.

---

## 3. El Dataset (Concrete Crack Images)

Para la parte de las grietas estamos usando el dataset de acceso libre **Concrete Crack Images** (creado por Özgenel), el cual obtuvimos directamente desde Mendeley Data:
* **Fuente de los datos:** https://data.mendeley.com/datasets/5y9wdsg2zt/2

**Características del conjunto de datos:**
* **Total de imágenes:** 40.000 fotografías en total.
* **Dimensiones:** Son imágenes cuadradas de 227x227 píxeles en color (RGB).
* **Clases:**
  * `Positive`: 20.000 fotos que muestran concreto con grietas.
  * `Negative`: 20.000 fotos de concreto sano o sin grietas.
* **Balance:** Está totalmente balanceado (50% positivas y 50% negativas). Creo que esto nos evita bastantes dolores de cabeza porque no tenemos que lidiar con clases desbalanceadas al principio.

Con el código que armamos en Python revisamos que todas las imágenes se pudieran abrir con la librería `PIL` y no encontramos archivos dañados o corruptos.

---

## 4. Estado del Arte (Muy breve)

Estuvimos leyendo un poco sobre cómo se suele abordar este problema normalmente:
* **Métodos tradicionales:** Antes se utilizaban técnicas de procesamiento digital de imágenes, como filtros de bordes (por ejemplo Canny) para buscar líneas oscuras en el concreto. El problema de esto es que cualquier sombra, mugre o textura rugosa puede confundir al algoritmo.
* **Redes Neuronales:** Hoy en día se prefieren las redes convolucionale porque aprenden solas los patrones visuales reales de una grieta. Para aplicaciones en computadores o celulares se suelen usar arquitecturas ligeras como *MobileNetV2*.

Como apenas estamos en primer semestre y estamos aprendiendo la lógica, para esta entrega no usamos un modelo complejo todavía, sino una prueba simple para comprobar que la carga de datos funciona bien de principio a fin.

---

## 5. Avance de la Entrega 1

En el cuaderno de Google Colab dejamos montado un prototipo funcional de extremo a extremo[cite: 1, 2]:
- Carga, descompresión y verificación de las 40.000 imágenes del dataset[cite: 1, 2].
- Entrenamiento de una red neuronal convolucional sencilla (línea base) para detectar grietas[cite: 1, 2].
- Cálculo del ángulo de inclinación mediante visión por computador (OpenCV y detección de líneas)[cite: 1, 2].
- Integración de resultados para entregar un diagnóstico inicial de riesgo (Bajo, Medio o Alto)[cite: 2].

---

## 6. ¿Cómo ejecutar el proyecto?

1. Abrir o clonar el cuaderno `.ipynb` en Google Colab[cite: 1, 2].
2. Subir una imagen de prueba llamada `mi_foto.jpg` en la raíz del entorno (`/content/mi_foto.jpg`)[cite: 1].
3. Ejecutar las celdas en orden de arriba a abajo. El script descargará el dataset, entrenará el modelo base, analizará la inclinación y mostrará la predicción con su nivel de riesgo[cite: 1, 2].
