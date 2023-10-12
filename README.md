# MachineLearningBedu
## Proyecto : Modelos de predicción para Fraudes en Transacciones 
### Introducción
Este proyecto se realizó con un dataset disponible en [Kaggle](https://www.kaggle.com/datasets/jainilcoder/online-payment-fraud-detection?resource=download). Este dataset incluye datos sobre transacciones bancarias de varios tipos:
+ Cash In
+ Cash Out
+ Transfers
+ Payment
+ Debit

Cada uno de ellos contiene información del monto de la transacción, cantidad que había en la cuenta, lo que sobró en la cuenta, el número de cuenta de dónde salió y los mismos datos para la cuenta a donde llegó el dinero.

## Objetivos
+ Cargar el dataset
+ Analizar el dataset y las relaciones que hay para determinar si es fraude o no
+ Tomando como base la columna isFraud que determina si la transacción fue fraude o no, determinar el mejor modelo de predicción para inputs futuros.

## Hipótesis
Yo pienso que el dataset tiene ciertos datos que serán funcionales, sin embargo, creo que hay datos que podríamos dejar de lado ya que son alrededor de 6 millones y puede que no haya tantos "fraudes" en payments o en debit.

Debido a una investigación previa pude recabar información de distintos autores que mencionan el mejor modelo a utilizar para la resolución de distintos problemas como los fraudes. Debido a esto, opino que la mejor forma de resolver este problema para predecir de mejor forma futuras transacciones, sería utilizando un modelo supervisado.

Por lo tanto, seguiré el camino de estas fuentes para resolver el proyecto.

## Análisis Exploratorio y Final
La mayor parte del [análisis](https://www.kaggle.com/datasets/jainilcoder/online-payment-fraud-detection?resource=download) lo hice por medio del Jupyter Notebook, hasta la última sesión que tuvimos fue que se mencionó que pudimos haber utilizado MYSQL Workbench para realizar búsquedas más rápidas y más cómodas. Hubiera sido de mucha ayuda pero realmente con el poco análisis que realicé, funcionó a la perfección.

Al final, me dí cuenta que debí haber eliminado al menos un 50% de los datos porque utilicé un CrossTab para verificar el número de casos con fraudes que había en cada tipo de movimiento y resultó que los únicos que contaban con fraudes eran Transfers y Cash Out. Por lo que realizando eso, pude haber disminuido el tamaño del archivo y hacer funcionar mis modelos más rápido y quitarle algunos casos que no importaban. Al final esto no podría afectarlo ya que insertando valores de una transacción de posible fraude, al darle un valor de los otros tipos de transacciones, lo tomaba como no fraude.

## Clasificación
Como anteriormente mencionaba, resolveríamos el problema como mencionaban algunos autores en línea, por lo que realizamos dos modelos supervisados de clasificación, uno fue utilizando Regresión Lineal y el otro fue por árboles de decisión.

Para realizar el entrenamiento con todos los modelos se siguieron los siguientes pasos:
+ Como datos de entrada se eligieron los campos de step, type, amount, oldBalanceOrig, newBalanceOrig, isFraud.
+ Como dato de salida se eligió únicamente la columna booleana que retornaba 1 o 0 dependiendo si era fraude o no.
+ Separar el conjunto de datos en entrenamiento y prueba (70%/30%).
+ Realizar el entrenamiento.

Para analizar los resultados se usó una matriz de confusión, un accuracy_score y el classification_report para comparar ambos modelos. Posteriormente, utilicé KFold para la validación cruzada. Los primeros resultados se encuentran en sus [notebooks](https://github.com/aramsdev/MachineLearningBedu/tree/main/notebooks) respectivos. La de KFold se encuentra en el notebook de [TreeClassifier](https://github.com/aramsdev/MachineLearningBedu/blob/main/notebooks/DecisionTreeClassifier.ipynb) al final.

### Regresión Lineal

Se inició este proyecto con la idea de encontrar alguna correlación entre las distintas variables, por esto hice uso de la [Regresión Lineal](https://github.com/aramsdev/MachineLearningBedu/blob/main/notebooks/LinearRegression.ipynb).

### Árboles de Decisión

A través de los árboles de decisión podemos realizar predicciones que determinen futuras transacciones, aquí se encuentra el [notebook](https://github.com/aramsdev/MachineLearningBedu/blob/main/notebooks/DecisionTreeClassifier.ipynb). 

## Conclusiones
Con base en los distintos trabajos de análisis y definición de modelos se dan las siguientes conclusiones:

Los conjuntos de datos de CASH IN, PAYMENT, y DEBIT no contienen datos que puedan ser relevantes para el análisis de transacciones de fraude ya que ninguna de las transacciones en el dataset de esos tipos, están catalogados como fraude.

Hay algunos casos raros, en específico 16, que están catalogados como FlaggedFraud. El significado de esta característica es desconocida por lo que es algo que investigaré a futuro. Aunque el modelo funciona, creo que esta característica podría servir para enviar esas transacciones a un humano para que identifique y siga entrenando al modelo poco a poco. Además, creo que podría agregar una característica en la que si la transacción no deja la cuenta vacía pero representa un porcentaje importante, ponerlo como posible Fraude y a partir de un humano, entrenar al modelo.


Los mejores modelos de predicción fueron la regresión lineal y los árboles de decisión con diferencias mínimas, aunque con las matrices de confusión y demás, salieron resultados donde la precisión de la regresión lineal era de 71 y la del árbol de decisión era de 99. Sin embargo, con KFold logré identificar que no había diferencia alguna entre ambos modelos, era mínima.

## ☑️ Trabajo a futuro
+ Recabar información sobre las categorías incluidas en los conjuntos de datos pues algunos datos son desconocidos tales como el FlaggedFraud.
+ Replicar el proceso para los datos sin incluir los tipos de transacción que no cuentan con ningún fraude para verificar que realmente no afectan al modelo.
+ Recabar más datos sobre otras transacciones con la misma estructura para mejorar el modelo o para predecir transacciones para otros tipos fuera de Cash Out y de Payment.
