# Evaluación con **block bootstrap**

- En ocasiones anteriores, una crítica del trabajo ha sido que el proceso de muestreo del experimento puede violar la autocorrelación en las series de tiempo de variaciones intermensuales de los índices de precios de los gastos básicos.

- Esto debido a que se *desarma* la serie de tiempo y se combina una nueva serie de tiempo de variaciones intermensuales utilizando un criterio de estacionalidad, es decir, conservando las variaciones intermensuales observadas en los mismos meses de ocurrencia, aunque puedan repetirse en diferentes años.
  - Este procedimiento ayuda eficazmente a reducir la varianza del experimento, ya que solo se permiten ciertas variaciones intermensuales en cada mes. 

- Una forma de controlar este efecto es el de utilizar una variante de *bootstrap* denominada *block bootstrap*, que se utiliza, bajos ciertos supuestos, para realizar remuestreos cuando la muestra no es iid (independiente e idénticamente distribuida), como en el caso de datos series de tiempo.  

- En particular, si la serie de tiempo es estacionaria y se asume una **dependencia débil en covarianza**, entonces, las observaciones pierden dependencia de sus rezagos eventualmente (el proceso es dependiente solamentede sus primeros rezagos). 
  - Este hecho se aprovecha para generar el procedimiento de *block bootsrap*.
 
## *Block bootstrap*

- Existen diferentes variantes: NBB (*Nonoverlapping block bootstrap*), MBB (*Moving block bootstrap*), CBB (*Circular block bootstrap*), SB (*Stationary block bootstrap*). 

- La idea de todos estos procedimientos es mantener la relación muestra-distribución que se tiene en el *bootstrap clásico* (iid), ante dependencia en los datos.

- Existe toda una literatura al respecto, sobre la adecuación y aplicación de cada método en la práctica.

## *Nonoverlapping Block Bootstrap (NBB)*

- Se asume estacionariedad y dependencia débil en covarianza de la secuencia de variables aleatorias.
- Se puede dividir la muestra de $T$ observaciones en la unión de $B$ bloques consecutivos o series más pequeñas de largo $l$. 
  - El muestreo de bootstrap se obtiene al muestrear aleatoriamente $B$ bloques aleatoriamente y concatenar las observaciones. 

- El principio de *bootstrap* se mantiene, aunque ligeramente diferente:
  - Debido a la estacionariedad y dependencia débil, cada bloque de largo $l$ se distribuye idénticamente con los otros bloques. 
  - Esto genera (aproximadamente) la muestra iid al concatenar todos los bloques y recrea el principio de bootstrap.

## Propuesta para un análisis de sensibilidad

- Generar un conjunto de resultados que tome en cuenta un procedimiento de *block bootstrap*.

- Se plantea esta propuesta para darle **robustez al procedimiento estadístico de simulación**, ya el procedimiento de evaluación depende críticamente del tipo de muestreo realizado en las variaciones intermensuales de los gastos básicos.