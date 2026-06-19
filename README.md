# Calories Burn Dataset

## Contexto

El ejercicio es definido como cualquier actividad fisica que esté estructurada que requiera un gasto energético. El hecho de mantenerse activo representa un pilar fundamental en el estilo de vida de las personas, conllevando numerosos benefifcios comprobados tanto para la salud mental como para el bienestar fisico. Como un amante del deporte, me interesa aprovechar esta oportunidad para entender a fondo el impacto real de nuestras decisiones en lo que decidimos realizar como deporte/entrenamiento. Con el propósito de que los resultados sean de utilidad práctica tanto para mi como para cualquier persona que desee mejorar su salud.

## Definición del Problema

A pesar de que existe una gran variedad de disciplinas disponibles, existe una falta de claridad sobre como varía el gasto energético real entre los ditintos tipos de esfuerzo. Por lo tanto, el problema central de este análisis consiste es poder determinar que actividades fisicas o ejercicios queman la mayor y menor cantidad de calorías por hora, y ver como esto influye en el peso corporal de cada individuo en el dicho deporte.

## Relevancia del Problema

Este problema posee un alto grado de relevancia debido a que permite a las personas optimizar su tiempo y esfuerzo, especialmente si tienen el objetivo concreto de perder peso. Cabe destacar que este análisis no se restringe al gusto personal por un deporte en específico, sino que evalúa de forma objetiva y cuantitativa el gasto calórico por hora. De este modo, los resultados actúan como una herramienta de decisión: el usuario puede identificar primero el grupo de actividades con mayor quema energética y, entre ellas, seleccionar la que mejor se adapte a sus preferencias personales.

#  Plan de Acción
## Descripción del Dataset
El siguiente dataset contiene una amplia variedad de actividades físicas, definido de la siguiente manera:

- Contiene un total de 248 registros y 6 columnas. Cada fila representa una actividad, ejerciico o deporte específico.
- La naturaleza de los datos nos presenta una combinación de datos cualitativos y cuantitativos.

### Variables Dataset

| Columna | Tipo de Dato | Descripción |
|-----------|-----------|-----------|
| Actividad, Ejercicio o Deporte  | Catégorico  | El nombre o descripción detallada de la actividad física |
| 130 lbs  | Numérico  | Calorías aproximadas quemadas por hora por una persona que pesa 130 libras (~59kg)  |
| 155 lbs  | Numérico | Calorías aproximadas quemadas por hora por una persona que pesa 155 libras (~70kg)  |
| 180 lbs  | Numérico  | Calorías aproximadas quemadas por hora por una persona que pesa 180 libras (~81kg)  |
| 205 lbs  | Numérico  | Calorías aproximadas quemadas por hora por una persona que pesa 205 libras (~93kg)  |
| Calorias por Kilo  | Numérico  | indica las calorías quemadas por hora por cada kilogramo de peso corporal. |

>  Para efectos de este análisis y con el fin de estandarizar los resultados a la forma que se mide en Chile el peso, se utilizará la variable kilogramos (kg).

## Modelo Seleccionado
Se seleccionará un modelo de Regresión Lineal. El algoritmo tomará como variables de entrada (features) el peso del usuario (calculado en kilogramos) y el factor de gasto de la actividad (Calories per kg), prediciendo el gasto calórico teórico para una hora. Luego, mediante una función matemática simple, escalará ese valor al tiempo específico disponible declarado por el usuario (ej. si el usuario tiene 30 minutos, el valor predicho se multiplicará por 0.5).

Una vez calculadas las calorías personalizadas para ese tiempo en todas las actividades, un algoritmo de ordenamiento filtrará aquellas que alcancen el objetivo del usuario y las listará de mayor a menor eficiencia calórica.

Al ser un problema de regresión, los datos se dividirán de forma aleatoria en un 80% para el entrenamiento de la recta y un 20% para la prueba final.

Evaluaremos la precisión de la predicción numérica utilizando dos métricas clave:

- R-Cuadrado ($R^2$)
- Error Cuadrático Medio (MSE)
- Error Absoluto Medio (MAE)

## Justificación del Modelo

El gasto energético ($E$) es directamente proporcional a la masa corporal ($m$) y al tiempo de trabajo ($t$). Dado que la relación entre el peso de una persona y las calorías que quema realizando una misma actividad es estrictamente lineal, por ello una Regresión Lineal al ser un modelo de baja varianza es lo que mejor funciona para este caso, sin necesidad de manejar modelos más complejos, evitando el overfitting.

## Limitaciones del modelo en este contexto

El modelo asume que el gasto calórico se mantiene constante a lo largo del tiempo. Cosa que no es así, ya que en realidad factores como la fatiga humana alteran completamente la constancia de los resultados que están planteados. Además como segundo punto, el dataset no incorpora variables demográficas como el género, edad o condición de salud, las cuales influyen directamente en el gasto calórico. Por consecuencia, el modelo ofrece una aproximación simplificada de lo razonable a realizar, pero no captura la variabilidad de cada usuario.

# Activación Ambiente Conda

### 1. Crear el enviroment de Conda

conda env create -f ambiente.yaml

### 2. Activar el Enviroment
conda activate Ejercicios