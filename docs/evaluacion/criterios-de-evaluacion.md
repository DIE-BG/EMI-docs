# Selección final de criterios de evaluación 

A continuación, se describen brevemente los criterios de evaluación utilizados en este apartado para la evaluación de los diferentes tipos de estimadores muestrales de inflación. Dichos criterios fueron definidos con base en el proceso de calibración y discusión de las diferentes alternativas presentadas en el apartado anterior de esta documentación. 

## Criterios de evaluación base

Estos criterios de evaluación corresponden a la evaluación de un escenario "base" y se utilizarán en para evaluar, en una primera instancia, el desempeño de los diferentes estimadores muestrales de inflación y determinar el mejor estimador de cada uno de los tipos de estimadores propuestos. 

- **Período del estadístico de evaluación**: se determinó que es conveniente evaluar las medidas de inflación hasta el período de **diciembre de 2019**, utilizando el desempeño del estadístico de evaluación sobre el período completo del IPC base 2000 y 2010, es decir, desde diciembre de 2001 hasta diciembre de 2019. 

- **Estadístico de evaluación**: se determinó que el estadístico de error cuadrático medio (MSE) y la media muestral de su distribución de simulación son los adecuados para evaluar el desempeño de las medidas de inflación, ya que permiten resumir el sesgo y la precisión en un único valor, comparable entre diferentes medidas de inflación. 

- **Número de simulaciones**: se escoge de acuerdo con la propuesta de utilizar $\epsilon=0.05\bar{Z}$ y la aproximación normal para el cómputo del número de simulaciones. Inicialmente, se corre una simulación de $50,000$ realizaciones de inflación total (variación interanual del IPC) y se determinó que su MSE promedio fue de $\bar{Z} = 28.86$. Con esto, se requieren un total de $102,952.6$ simulaciones para una probabilidad del $95\%$ de que nuestra estimación no se aleje en más de $\epsilon = (0.05)(28.66) = 1.44$ de la verdadera media de la distribución del MSE. Por lo que el número de simulaciones se fijará en $110,000$ para todas las simulaciones en el escenario base.

- **Función de tendencia**: se escoge utilizar una componente aditiva de tendencia generalizada de inflación utilizando un modelo de caminata aleatoria, tanto para las trayectorias paramétricas, como para las realizaciones de las trayectorias muestrales de inflación, que represente lo mejor posible la estocasticidad que, en cierta forma, puede observarse en el comportamiento generalizado de la inflación (períodos de expansión y contracción en el comportamiento de los precios). La calibración de los parámetros de esta componente se detalla en el apartado de [calibración del proceso de caminata aleatoria](../calibracion/Calibración%20varianza%20RW.md). 

- **Trayectoria de inflación paramétrica**: se utiliza como trayectoria paramétrica de inflación la obtenida a través de la variación interanual del IPC que se obtiene al considerar promedios aritméticos de las variaciones intermensuales de los distintos gastos básicos en los mismos meses, de los dos diferentes períodos del IPC base 2000 y 2010. Además, se considera la variante en la que se realizan cambios de base sintéticos, en el mes de diciembre, de los años 2003, 2006, 2013 y 2016. Con esto se pretende controlar el sesgo por fórmula que introduce la utilización de la fórmula del IPC.


Finalmente, se presenta un resumen de los criterios de evaluación del escenario en la tabla siguiente: 

| Parámetro de evaluación              | Criterio definido                                |
|:-------------------------------------|:-------------------------------------------------|
| Período de evaluación                | completo                                         |
| Período final de evaluación          | diciembre de 2019                                |
| Estadístico de evaluación            | MSE                                              |
| Número de simulaciones               | 110,000                                          |
| Función de tendencia                 | Caminata aleatoria calibrada                     |
| Trayectoria de inflación paramétrica | Variación interanual del IPC con cambios de base |

## Pruebas de sensibilidad de los resultados

Para evaluar la robustez de los resultados obtenidos con los criterios de evaluación base, se realizarán pruebas de sensibilidad respecto de estos. En particular, se consideran las variantes descritas a continuación. 

- **Cambio en el período final de evaluación**: se considera variar el período final de evaluación en meses de diciembre de 2018, junio de 2019 y junio de 2020.  

- **Cambio en el estadístico de evaluación**: además de utilizar el MSE, se considera utilizar los siguientes estadísticos para evaluar el desempeño de los estimadores muestrales de inflación:
    - Promedio en el muestreo de la raíz del error cuadrático medio ($\overline{\text{RMSE}}$) de las trayectorias muestrales como estimador de la precisión de la medida de inflación.  
    - Promedio en el muestreo del valor absoluto del error medio ($\overline{\text{ME}}$) como estimador del sesgo (de cualquier signo) de la medida de inflación.
    - Promedio en el muestreo del coeficiente de correlación lineal ($\overline{\rho}$) entre la medida de inflación y la trayectoria de inflación paramétrica.
    - Índice de error muestral de la medida de inflación (combinación lineal de los anteriores).

- **Cambio en el período de evaluación del estadístico**: se considera el desempeño de las medidas de inflacióin en los siguientes subperíodos: 
    - Período de la base 2000 del IPC.
    - Período de transición de la base 2000 a la base 2010 del IPC.
    - Período de la base 2010 del IPC.

- **Cambio en el número de simulaciones**: se considera un cambio en el parámetro $\epsilon$ de tal forma que $\epsilon=0.025\bar{Z}$, es decir, que la estimación del promedio del estadístico de evaluación no esté más allá de un $2.5\%$ del valor verdadero. Este cambio conlleva realizar $411,810.3$ simulaciones, por lo que se realizará un análisis de sensibilidad de los resultados de simulación que utilice $420,000$ realizaciones para asegurar que el número de simulaciones sea suficiente para tener la mínima variabilidad en las estimaciones.

- **Cambio en la componente de tendencia**: se consideran dos escenarios adicionales de la componente aditiva de tendencia.  
    - Sin tendencia.
    - Crecimiento exponencial.

- **Cambio en el parámetro poblacional de inflación**: se consideran dos trayectorias paramétricas de inflación adicionales con las que se comparan los resultados.  
    - Variación interanual del IPC (sin cambios de base). 
    - Media ponderada interanual.

- **Cambio en la forma de remuestreo utilizando *block bootstrap***: se comparan resultados del escenario base con los resultados obtenidos al utilizar la técnica de muestreo de *bootstrap* de bloque en las variaciones intermensuales de cada gasto básico en las bases del IPC, utilizando un largo de bloque de 12 meses. Este procedimiento permite seguir obteniendo variaciones intermensuales aleatorias en los mismos meses de ocurrencia, pero manteniendo la estructura de autocorrelación individual en la mayoría de las series de tiempo al utilizar la variante de *nonoverlapping block bootstrap*. 

- **Análisis de las distribuciones de simulación del estadístico de evaluación**: se analiza el comportamiento general del estadístico de simulación a través de la distribución de simulación obtenida del proceso de evaluación para comentar sobre las causas técnicas o coyunturales que hacen que exhiba determinada forma o valores de los siguientes estadísticos.
    - Promedio.
    - Desviación estándar.
    - Asimetría. 
    - Curtosis.

- **Análisis de trayectorias utilizando los datos históricamente observados**: se analizan cualitativamente las trayectorias observadas históricamente de las medidas de inflación para determinar su consistencia con dinámica de inflación en el país durante el período de evaluación.  
