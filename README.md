# MachineLearningBedu
## Proyecto : Modelos de predicción para Fraudes en Transacciones 
### Introducción
Este proyecto se realizó con un dataset disponible en [Kaggle](https://www.kaggle.com/datasets/jainilcoder/online-payment-fraud-detection?resource=download). Este dataset incluye datos sobre transacciones bancarias de varios tipos:
-Cash In
-Cash Out
-Transfers
-Payment
-Debit

Cada uno de ellos contiene información del monto de la transacción, cantidad que había en la cuenta, lo que sobró en la cuenta, el número de cuenta de dónde salió y los mismos datos para la cuenta a donde llegó el dinero.

## Objetivos
- Cargar el dataset
- Analizar el dataset y las relaciones que hay para determinar si es fraude o no
- Tomando como base la columna isFraud que determina si la transacción fue fraude o no, determinar el mejor modelo de predicción para inputs futuros.

## Hipótesis
Yo creo que el dataset tiene ciertos datos que serán funcionales, sin embargo, creo que hay datos que podríamos dejar de lado ya que son alrededor de 6 millones y puede que no haya tantos "fraudes" en payments o en debit.

Por otro lado, creo que la mejor forma de resolver este problema y poder predecir de mejor forma futuras transacciones, sería con un modelo supervisado ya que estuve leyendo en varias fuentes y mencionan que realizar diferentes modelos de supervisión y de no supervisión, los mejores para resolver problemas de tipo fraude eran esos.

Por lo tanto, seguiré el camino de estas fuentes para resolver el proyecto.

