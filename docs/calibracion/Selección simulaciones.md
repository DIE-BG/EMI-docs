# Determinación del número de simulaciones

- A continuación, se presentan algunas referencias para definir el número de simulaciones a realizar.

- Posteriormente, se presenta la propuesta final para el esquema de evaluación de medidas de inflación.

 
## Búsqueda en foros en línea
Consulta en foros de estadística: [StackExchange: Rule of thumb for number of bootstrap samples](https://stats.stackexchange.com/questions/86040/rule-of-thumb-for-number-of-bootstrap-samples). Algunos comentarios mencionan algunas alternativas:

- Utilizar tantas como sean posibles, con límite en 1 millón.
- Correr varias veces la simulación con un número inicial considerado como suficiente y ver la variación en los estimadores de *bootstrap*. Si las estimaciones repetidas no varían mucho, el número de simulaciones es adecuado. 
- Utilizar 10,000 simulaciones para experimentos propios y hasta 100,000 simulaciones cuando se comparten resultados con otros (con conjuntos de datos pequeños).




## Revisión de papers de inflación
- Haciendo una revisión de los papers principales con metodología similar a la adoptada por el EMI tenemos: 

  - Bryan, Cecchetti y Wiggings (1997) *Efficient Inflation Estimation*: procedimiento de *bootstrap* similar. Se considera un número de simulaciones igual a 10,000 sin mecionar alguna justificación cuantitativa. Sin embargo, en su ejercicio de simulación utilizan menos categorías del IPC y del IPP.

  - Roger (1997) *A robust measure of core inflation in New Zealand, 1949-96*: se evalúa un percentil óptimo para Nueva Zelanda, pero sin técnicas de simulación. La evaluación se hace obteniendo el percentil de la media y tomando un promedio para diferentes períodos. 



<!-- 
_footer: ''
-->

## Literatura académica

- En Chernick, 2da. ed. (2011) *Bootstrap methods : a guide for practitioners and researchers* se discute: 

> Let $B$ be the number of bootstrap replications in a uniform resampling. Let $\sigma_{B}^2$ be the variance of a single bootstrap resample estimate of the parameter. Since the Monte Carlo approximation to the bootstrap estimate is an average of $B$ such estimates independently drawn, the variance of the Monte Carlo approximation is just $\sigma_{B}^2/B$. 
Of course, this basic result is well known and has been applied for many years to judge how many replications to take in a simulation. There is nothing new here with the bootstrap. For the bootstrap, the particular distribution being sampled is the empirical distribution, but otherwise nothing is different.

- Esta aseveración se formaliza aún más en DeGroot y Schervish, 4ta. ed. (2012) *Probability and Statistics*.

 
### Chernick, (2da. ed.)
- Más adelante se tiene: 
>  The practitioner chooses $B$ to make the variance sufficiently small, ensuring that the bootstrap approximation is close to the actual bootstrap estimate. Note that the accuracy of this approximation depends on $B$ and not $n$ (sample size). It only expresses how close the approximation is to the bootstrap estimate and does not express how close the bootstrap estimate is to the true parameter value!

- Esto da indicios de un criterio práctico (*ad hoc*) dependiendo de la aplicación y la confianza en la simulación.

- Más adelante en el libro se discuten, principalmente, algunos **métodos de reducción de varianza**, que permiten diseñar el experimento de tal forma que se limite la aleatoriedad inherente al mismo, lo cual puede reducir en sí mismo el número de simulaciones.

 
### DeGroot y Schervish, versión con estimador normal
- Se supone un estimador de Monte Carlo $Z$ de un parámetro $\theta$, basado en $v$ simulaciones, siendo $Z$ un promedio (estimador de la media poblacional), entonces $Z$ tiene aproximadamente distribución normal con media $\theta$ y varianza $\sigma^2/v$, en donde $\sigma^2$ no depende del tamaño de la simulación. Entonces, para cada $\epsilon > 0$: 
$$ Pr(|Z-\theta| \leq \epsilon) \approx 2\Phi(\epsilon v^{1/2} / \sigma) -1 $$

- A partir de esto, podemos fijar esta probabilidad como $\gamma$ y escoger $v$ a partir de dicha ecuación: 
$$ v = \left[ \Phi^{-1}\left( \frac{1+\gamma}{2} \right) \frac{\hat{\sigma}}{\epsilon} \right]^2 $$

 
### DeGroot y Schervish, versión con el teorema de Chebyshev
- Si la aproximación normal de $Z$ resulta poco confiable, se puede utilizar una aproximación de Chebyshev, tal que si: 
$$ v = \frac{\sigma^2}{\epsilon^2 (1-\gamma)} $$
- La desigualdad de Chebyshev garantiza que $Pr(|Z-\theta| \leq \epsilon) \geq \gamma$
- Este es un criterio más riguroso, pero eleva significativamente el número de simulaciones a realizar. 


<!-- ## Número de simulaciones con diferentes estadísticos 

### Número de simulaciones RMSE
- Utilizando el RMSE, $Z=\overline{\text{RMSE}} = 1.62$ de la variación interanual del IPC.

| $\gamma$ | $\hat{\sigma}$ | $\epsilon$ | $v$ (normal) | $v$ (Chebyshev) |
|:--------:|:--------------:|-----------:|-------------:|----------------:|
|   0.9    |     1.582      |       0.05 |     2,708.49 |       10,010.90 |
|   0.9    |     1.582      |       0.01 |    67,712.29 |      250,272.40 |
|   0.95   |     1.582      |       0.05 |     3,845.64 |       20,021.79 |
|   0.95   |     1.582      |       0.01 |    96,141.11 |      500,544.80 |
|   0.99   |     1.582      |       0.05 |     6,642.13 |      100,108.96 |
|   0.99   |     1.582      |       0.01 |   166,053.15 |    2,502,724.00 |

 

### Número de simulaciones MAE
- Utilizando el MAE, $Z=\overline{\text{MAE}} = 1.17$ de la variación interanual del IPC.

| $\gamma$ | $\hat{\sigma}$ | $\epsilon$ | $v$ (normal) | $v$ (Chebyshev) |
|:--------:|:--------------:|-----------:|-------------:|----------------:|
|   0.9    |     0.973      |       0.05 |     1,024.57 |        3,786.92 |
|   0.9    |     0.973      |       0.01 |    25,614.16 |       94,672.90 |
|   0.95   |     0.973      |       0.05 |     1,454.73 |        7,573.83 |
|   0.95   |     0.973      |       0.01 |    36,368.20 |      189,345.80 |
|   0.99   |     0.973      |       0.05 |     2,512.58 |       37,869.16 |
|   0.99   |     0.973      |       0.01 |    62,814.49 |      946,729.00 |

 

### Número de simulaciones MSE
- Utilizando el MSE, $Z=\overline{\text{MSE}} = 5.14$ de la variación interanual del IPC.

| $\gamma$ | $\hat{\sigma}$ | $\epsilon$ |  $v$ (normal) | $v$ (Chebyshev) |
|:--------:|:--------------:|-----------:|--------------:|----------------:|
|   0.9    |     27.92      |       0.05 |    843,617.02 |    3,118,105.60 |
|   0.9    |     27.92      |       0.01 | 21,090,425.49 |   77,952,640.00 |
|   0.95   |     27.92      |       0.05 |  1,197,807.43 |    6,236,211.20 |
|   0.95   |     27.92      |       0.01 | 29,945,185.65 |  155,905,280.00 |
|   0.99   |     27.92      |       0.05 |  2,068,830.82 |   31,181,056.00 |
|   0.99   |     27.92      |       0.01 | 51,720,770.62 |  779,526,400.00 | -->



 
## Propuesta para definir el número de simulaciones
- Utilizar la aproximación normal $Z$ de la media del estadístico de precisión y computar $\epsilon = 0.05|Z|$. Es decir, se permite una distancia del 5% del valor del estadístico $Z$ y el parámetro estimado.
- Utilizar $\gamma = 0.95$, es decir, que la probabilidad del intervalo de confianza sea del 95%.
- Fijar el número de simulaciones al número requerido por la medida de evaluación para la medida de inflación denominada **"Variación interanual del IPC"**, ya que es la que mayor varianza presenta en sus distribuciones.  
- En este caso, el número de simulaciones estaría dado por:
$$ v = (10,000)\frac{\sigma^2}{Z^2}\left[ \Phi^{-1}\left( \frac{1+\gamma}{2} \right) \right]^2 $$
- Ventajas: 
  - Criterio cuantitativo bien definido, factible y no tan estricto (pero que permite alcanzar una alta probabilidad para el intervalo de confianza). 
  - El número de simulaciones está en función del coeficiente de variación de la medida de evaluación (mayor dispersión relativa, más simulaciones). 


 
<!--  Estos números corresponden a los obtenidos con los estadísticos de la variación interanual del IPC utilizando la caminata aleatoria con factor multiplicativo

### Número de simulaciones MAE
- Utilizando el MAE, $Z=1.77$ y $\epsilon=cZ$, $c \in \lbrace0.05, 0.025, 0.01\rbrace$

| $\gamma$ | $\hat{\sigma}$ | $\epsilon$ |  $v$ (normal) | $v$ (Chebyshev) |
|:|:|--:|--:|-:|
|     0.95 |          0.973 |       0.01 | **26,567.47** |      138,319.67 |
|     0.95 |          0.973 |       0.03 |  **4,250.79** |       22,131.15 |
|     0.95 |          0.973 |       0.06 |  **1,062.70** |        5,532.79 |


 

### Número de simulaciones RMSE
- Utilizando el RMSE, $Z=1.62$ y $\epsilon=cZ$, $c \in \lbrace0.05, 0.025, 0.01\rbrace$

| $\gamma$ | $\hat{\sigma}$ | $\epsilon$ |  $v$ (normal) | $v$ (Chebyshev) |
|:|:|--:|--:|-:|
|     0.95 |          1.582 |       0.08 |  **1,465.34** |        7,629.09 |
|     0.95 |          1.582 |       0.04 |  **5,861.37** |       30,516.37 |
|     0.95 |          1.582 |       0.02 | **36,633.56** |      190,727.33 |



### Número de simulaciones MSE
- Utilizando el MSE, $Z=5.14$ y $\epsilon=cZ$, $c \in \lbrace0.05, 0.025, 0.01\rbrace$

| $\gamma$ | $\hat{\sigma}$ | $\epsilon$ |     $v$ (normal) | $v$ (Chebyshev) |
|:|:|--:|--:|-:|
|     0.95 |          27.92 |       0.26 |    **45,337.83** |      236,044.88 |
|     0.95 |          27.92 |       0.13 |   **181,351.33** |      944,179.50 |
|     0.95 |          27.92 |       0.05 | **1,133,445.84** |    5,901,121.89 |

-->

### Número de simulaciones MSE
- Utilizando el MSE de la variación interanual del IPC con la calibración de tendencia de caminata aleatoria, $Z=\overline{\text{MSE}} = 28.858$ y $\epsilon=cZ$, $c \in \lbrace0.05, 0.025, 0.01\rbrace$. 
- La desviación estándar en la distribución de simulación del MSE es $\hat{\sigma} =236.219 $. 
- Por lo tanto, para los diferentes niveles de confianza $\gamma$ y desviación absoluta $\epsilon$ admisible tenemos: 

| $\gamma$ | $\hat{\sigma}$ | $\epsilon$ | $v$ (normal) | $v$ (Chebyshev) |
|:--------:|:--------------:|-----------:|-------------:|----------------:|
|   0.90   |    236.2194    |   1.442929 |    72,509.62 |       268,003.9 |
|   0.90   |    236.2194    |  0.7214647 |    290,038.5 |       1,072,016 |
|   0.90   |    236.2194    |  0.2885859 |    1,812,740 |       6,700,097 |
|   0.95   |    236.2194    |   1.442929 |    102,952.6 |       536,007.8 |
|   0.95   |    236.2194    |  0.7214647 |    411,810.3 |       2,144,031 |
|   0.95   |    236.2194    |  0.2885859 |    2,573,815 |   13,400,194.00 |
|   0.99   |    236.2194    |   1.442929 |    177,817.8 |       2,680,039 |
|   0.99   |    236.2194    |  0.7214647 |    711,271.2 |   10,720,155.00 |
|   0.99   |    236.2194    |  0.2885859 |    4,445,445 |   67,000,968.00 |

# Referencias

- Bryan, Michael F., Stephen G. Cecchetti y Rodney L. Wiggins (1997). *Efficient inflation estimation*.
- Casella, G., & Berger, R. L. (2002). *Statistical Inference*. 2a. ed. Duxbury. Pacific Grove, CA.
- Chernick, M. R. (2011). Bootstrap methods: *A guide for practitioners and researchers* (Vol. 619). John Wiley & Sons.
- DeGroot, Morris H. y Mark J. Schervish (2012). *Probability and statistics*. 4.a ed. Pearson Education.
- Lahiri, S. N. (2003). *Resampling methods for dependent data*. Springer Science & Business Media.
- Roger, Scott (1997). *A robust measure of core inflation in New Zealand*, 1949-96.
- Walther, B. A., & Moore, J. L. (2005). The concepts of bias, precision and accuracy, and their use in testing the performance of species richness estimators, with a literature review of estimator performance. Ecography, 28(6), 815-829.
- En línea. [StackExchange: Rule of thumb for number of bootstrap samples](https://stats.stackexchange.com/questions/86040/rule-of-thumb-for-number-of-bootstrap-samples). Consultado el 18/06/2020.