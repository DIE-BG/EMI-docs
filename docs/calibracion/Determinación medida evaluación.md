# Determinación de la medida de evaluación

- A continuación, se exponen diferentes propuestas para la métrica básica del proceso de evaluación de las medidas de inflación. 

 
## Índice de error muestral en la medida de evaluación
- Se considera el siguiente índice final de evaluación: 
$$ \text{IEM}_j = \overline{\text{RMSE}}_j + |\overline{\text{ME}}_j| + (1- \bar{\rho}_j)$$
- En donde: 
  - $\text{IEM}_j$ es el índice de error muestral de la medida de inflación $j$.
  - $\overline{\text{RMSE}}_j$ es el promedio en el muestreo del RMSE de evaluación de la medida de inflación $j$ (respecto al parámetro poblacional).
  - $|\overline{\text{ME}}_j|$ es el valor absoluto del promedio en el muestreo del error medio de evaluación de la medida de inflación $j$ (respecto al parámetro poblacional).
  - $\bar{\rho}_j$ es el promedio en el muestreo del coeficiente de correlación lineal de la medida de inflación $j$ con el parámetro poblacional.

 
### Ventajas y desventajas
- Es un punteo aditivo simple, mientras más pequeño su valor, mejor.
- Sin embargo, aunque el $\overline{\text{RMSE}}_j$ y el $|\overline{\text{ME}}_j|$ están en una escala similar (puntos porcentuales), el término de correlación no tiene unidades y podría no variar en la misma proporción que los otros.
- Una opción, podría ser generar un punteo dependiente y multiplicativo, por ejemplo $\text{IEM}_j = \overline{\text{RMSE}}_j * |\overline{\text{ME}}_j| * (1 - \bar{\rho}_j)$
- Podrían agregarse coeficientes de ponderación, pero nuevamente, serían subjetivos. 


## Error cuadrático medio
- El error cuadrático medio (MSE) de un estimador se puede descomponer en una medida de varianza y sesgo: 
$$ \text{MSE}(\hat{\theta}) = \text{E}\left[ (\hat{\theta}-\theta)^2 \right] = \text{Var}(\hat{\theta}) + \text{Sesgo}^2(\hat{\theta}, \theta) $$
- Véase Casella y Berger (2002, pág. 330) para una derivación de este resultado.
- Casella y Berger indican (ibíd.) que es una medida razonable para el desempeño de un estimador puntual y tiene la ventaja de interpretarse como la combinación de varianza y sesgo descrita arriba.


#### Descomposición aditiva del MSE
- Adicionalmente, esto se puede expresar como 
<!-- - (ver documento anexo FMI):  -->
$$ \text{MSE}(\hat{\theta}) = \text{Sesgo}^2(\hat{\theta}, \theta) + (s_\theta - s_{\hat{\theta}})^2 + 2(1-r) s_\theta s_{\hat{\theta}} $$ 
- en donde: 
    - $s_\theta$ es el error estándar del parámetro (a través del tiempo). 
    - $s_{\hat{\theta}}$ es el error estándar del estimador (a través del tiempo).
    - $r$ representa el coeficiente de correlación muestral entre parámetro y estimador.  

- Esto significa que el MSE representa una medida completa de eficiencia de un estimador, que relaciona la variabilidad, el sesgo y la correlación entre parámetro y estimador. 

### Consideraciones de sesgo
- En la literatura se menciona que estimadores sesgados pueden presentar valores bajos de MSE.

- Casella y Berger, 2002, pág. 331
> *Although many unbiased estimators are also reasonable from the standpoint of MSE, be aware that controlling bias does not guarantee that MSE is controlled. In particular, it is sometimes the case that a trade-off occurs between variance and bias in such a way that a small increase in bias can be traded for a larger decrease in variance, resulting in an improvement in MSE*.

- Posteriormente, se presenta un ejemplo en donde el estimador de varianza insesgado (el que divide por $n-1$) posee mayor MSE que el estimador sesgado de máxima verosimilitud (el que divide por $n$).

### Efecto de valores atípicos

- En la literatura también se menciona que el MSE puede verse afectado por *outliers*.
- Véase Walther y Moore (2005):  
  
> *Since both MSE and RMSE are calculated using squared differences, they tend to be dominated by outlying estimates far away from the true value*.

- En este mismo documento se menciona que para evitar el problema de *outliers*, se puede utilizar el valor absoluto de las diferencias (MAE) como una medida de precisión.

### Implicaciones para el proceso de simulación

- En Casella y Berger (2002)[^1]: 
[^1]: Casella y Berger (2002), página 332.

> In general, since MSE is a function of the parameter, there will be not one "best" estimator". Often, the MSEs of two estimators will cross each other, showing that each estimator is better (with respect to the other) in only a portion of the parameter space. However, even this partial information can sometimes provide guidelines for choosing between estimators.

- Al utilizar el MSE para comparar el desempeño de las medidas de inflación, en general, se tienen que realizar más simulaciones que con un estadístico como el error absoluto medio, ya que la distribución de esta medida de error es la más **volátil** (por el castigo cuadrático que pone a las desviaciones respecto al parámetro poblacional).

## Propuesta para la métrica de evaluación básica

- Se propone utilizar el MSE como métrica de evaluación básica debido a que representa una medida integral de eficiencia que pueede descomponerse en términos del sesgo, varianza y covarianza entre parámetros de inflación y sus diferentes estimadores muestrales. 
