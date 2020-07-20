# Determinación del proceso de caminata aleatoria
- A continuación, se expone el proceso actual de caminata aleatoria. 

- Posteriormente, se hace una propuesta alternativa para la calibración de la tendencia aleatoria.


## Proceso de caminata aleatoria

Actualmente, el proceso de caminata aleatoria se genera con un modelo de caminata aleatoria 
$$ a_t = a_{t-1} + \epsilon_t \quad \text{ en donde } \quad a_0 = 1, t = 1,\ldots, 120$$
- Se asume que la señal de perturbación $\epsilon_t$ es independiente a los datos del IPC. En particular, $\epsilon_t \sim  N(0, 0.05^2)$.  
- Se genera una señal $\epsilon_t$ diferente para cada una de los períodos del IPC Base 2000 y 2010. 
- La señal empieza en $1$ al inicio de cada base.


 
## Desviación estándar promedio en base 2000 y 2010
- Se muestra la desviación estándar promedio entre gastos básicos (porcentajes)

| Base      | Mínimo |  Media | Media Ponderada | Mediana |  Máximo |
|:-|-:|-:|-:|--:|--:|
| Base 2000 | 0.3604 | 1.6037 |          1.5731 |  0.7310 | 21.6526 |
| Base 2010 |      0 | 1.0690 |          1.0666 |  0.3865 | 13.3409 |

- Desviación estándar utilizada = 0.05
- Rango propuesto: 1% al 5%.

## Propuesta para el proceso de caminata aleatoria
- Se propone darle continuidad al proceso de caminata aleatoria, es decir, que el proceso no regrese a $1$ al inicio de la base 2010.
  - Se calibrará, tantas veces como sea necesario, hasta obtener una trayectoria que muestre movimientos aleatorios altos y bajos. 

- Se propone **fijar** la varianza del proceso de ruido: 
  - Que sea la misma magnitud entre bases del IPC. Esto para no generar más fuentes de variabilidad entre bases del IPC, más que las exhibidas por los datos.
  - Que este valor sea fijo, en un nivel de entre 0.01 y 0.05, de tal forma que el factor variable en el tiempo $a_t$ se encuentre siempre alrededor de $1$, para evitar mayores distorsiones en las distribuciones de variaciones intermensuales.