# Evaluación de medidas de inflación basadas en percentiles

En esta sección se documentan los resultados del proceso de evaluación de las medidas de inflación interanual basadas en percentiles de la distribución transversal de variaciones intermensuales de índices de precios.

## Resultados con criterios base
Aplicando el procedimiento de evaluación con los criterios de evaluación definidos con el período de evaluación hasta **diciembre de 2019**, se lleva a cabo la simulación de 110,000 realizaciones para cada una de las medidas de inflación interanual que utilizan como base los percentiles 50 a 80 de la distribución de variaciones intermensuales en cada mes. En cada caso, se consideran las versiones equiponderadas y ponderadas de las medidas de inflación. Los resultados son los siguientes:  

![Evaluacion percentiles agosto 2020](images/evaluacion-percentiles_2020-08-08_000753.png)  

Esta gráfica relaciona el MSE de evaluación con el número de percentil utilizado para la construcción de la medida de inflación, al utilizar la distribución equiponderada, así como la distribución ponderada, de las variaciones intermensuales de cada mes. Como se observa, el mínimo valor de MSE para los percentiles equiponderados se presenta en el **Percentil equiponderado 72**, mientras que el valor mínimo de MSE en los percentiles ponderados se presenta en el **Percentil ponderado 69**.

A continuación, se presentan algunos análisis de sensibilidad respecto a este escenario.****

## Análisis de sensibilidad ante cambios en el período final de evaluación

Debido a que se considera el período completo de evaluación hasta diciembre de 2019, se realiza un análisis de sensibilidad que considera los resultados ante un cambio en el período final de evaluación. Se consideran los siguientes períodos finales de evaluación: 

- Diciembre de 2018
- Junio de 2019
- Junio de 2020

Los resultados se muestran en la gráfica que se muestra a continuación.  

![Evaluacion percentiles análisis sensibilidad períodos](images/evaluacion-percentiles_2020-08-08_001736.png)  

Como se puede observar, en los 4 períodos finales, el percentil equiponderado que resulta óptimo sigue siendo invariantemente el **percentil equiponderado 72**. Respecto a los percentiles ponderados, se observa que para los períodos de diciembre de 2018, diciembre de 2019 y junio de 2020, el percentil óptimo es el **percentil ponderado 69**, mientras que en junio de 2019 se registra una ligera variación, siendo el percentil óptimo el **percentil ponderado 70**. 

Estos resultados muestran que el percentil óptimo no es tan sensible a cambios en los períodos finales de evaluación que están separados entre 6 meses y un año.  

## Análisis de sensibilidad ante cambios en el número de simulaciones

En este caso, se realiza una prueba de sensibilidad cambiando el número de simulaciones. Al mantener $\gamma=0.95$, $\sigma=236.22$ y cambiar $\epsilon$ de un valor de $0.05\bar{Z}$ a un $0.025\bar{Z}$ en el MSE de la medida de inflación total, se obtiene un número de simulaciones de 411,810. Este número de simulaciones es superior al que se obtendría dejando $\epsilon$ constante y cambiando de $\gamma=0.95$ a $\gamma=0.99$, el cual resulta en 177,817. 

Por lo tanto, se corre una evaluación con 420,000 realizaciones y se compara con el escenario base de 110,000 realizaciones. Como se muestra en la gráfica siguiente, los resultados coinciden sin mayor variabilidad. Esto se debe a que el número inicial de simulaciones es en realidad más que suficiente para la distribución del MSE de los estimadores muestrales basados en percentiles (en realidad, con alrededor de 10,000 simulaciones se tenía errores estándar de simulación muy pequeños).  

![Evaluacion percentiles análisis sensibilidad simulaciones](images/evaluacion-percentiles_2020-08-08_002802.png)  

## Análisis de sensibilidad ante cambios en el muestreo

Se realiza una prueba de sensibilidad utilizando como técnica de remuestreo *block bootstrap* con bloques de 12 meses. El muestreo se realiza de forma independiente para cada unos de los gastos básicos en cada una de las bases del IPC. A continuación, se muestran los resultados en la gráfica siguiente.  

![Evaluacion percentiles análisis sensibilidad simulaciones](images/evaluacion-percentiles_2020-08-08_022130.png)  

Como se puede observar, utilizando una variante de muestreo de *bootstrap*, el **percentil equiponderado 72** y el **percentil ponderado 69** resultan ser nuevamente los estimadores muestrales que minimizan el MSE de evaluación en el período completo, con resultados hasta el período de diciembre de 2019.  