# Práctica 1: Optimización de algoritmos secuenciales

### Información útil para compilar y ejecutar

- Para compilar en Linux con gcc: gcc –o salidaEjecutable archivoFuente.c
- Para ejecutar:

### Ejercicios

1. El algoritmo fib.c resuelve la serie de Fibonacci, para un número N dado, utilizando dos métodos:
recursivo e iterativo. Analice los tiempos de ejecución de ambos métodos ¿Cuál es más rápido? ¿Porqué?
Nota: ejecute con N = 1..50.

    - Al ejecutarse el programa, se puede observar lo siguiente a su salida:

    ``` 
    Calculando Fibonacci iterativo para n = 50...
    Resultado = 12586269025
    Tiempo en segundos 0.0000002861 
    Calculando Fibonacci recursivo para n = 50...
    Resultado = 12586269025
    Tiempo en segundos 75.5262809992 
    ```

    Se puede ver que el calculo de la serie de Fibonacci para N = 50 tarda mucho menos que al calcularlo de forma recursiva. Esto se debe a que la función para el calculo de la serie de Fibonacci de forma recursiva tiene un tiempo de ejecución de orden exponencial, ya que cada llamada recursiva genera dos nuevas llamadas. Entonces, al crecer N, el número de llamadas crece de forma exponencial. En cambio, la función para el cálculo de la serie de Fiboncci de forma iterativa tiene un tiempo de ejecución de orden lineal, y que la función es solo un bucle for.

2. El algoritmo funcion.c resuelve, para un x dado, la siguiente sumatoria:

    $$\sum_{i=10}^{100000000} \frac{x^3 + 3x² + 3x + 2}{x^2 + 1} \$$

    El algoritmo compara dos alternativas de solución. ¿Cuál de las dos formas es más rápida? ¿Por qué?

    - Al ejecutar el programa obtenemos la siguiente salida:

        ```
            Funcion calculada...
            Tiempo total en segundos 0.2982280254 
            Tiempo promedio en segundos 0.0000000030 
            Funcion calculada cada vez...
            Tiempo total en segundos 0.4533119202 
            Tiempo promedio en segundos 0.0000000045
        ```

        Observandose que la primer forma es más rápida que la segunda. Esto se debe a que la primer forma realiza primero el cálculo más grande y luego los restantes, no es como la segunda opción que realiza el cálculo más grande en cada iteración del bucle for (lo va a realizar cant veces, siendo cant una cte ya seteada de antemano).

3. El algoritmo instrucciones.c compara el tiempo de ejecución de las operaciones básicas: suma (+), resta (-), multiplicación (*) y división (/), para dos operandos dados x e y. ¿Qué análisis se puede hacer de cada operación? ¿Qué ocurre si x e y son potencias de 2?

    - Al ejecutar el programa, se obtiene la siguiente salida:

        ```
            Suma...
                Tiempo total en segundos 2.2939500809 
                Tiempo promedio en segundos 0.0000000023 
            Resta...
                Tiempo total en segundos 2.1503040791 
                Tiempo promedio en segundos 0.0000000022 
            Producto...
                Tiempo total en segundos 2.2949979305 
                Tiempo promedio en segundos 0.0000000023 
            Division...
                Tiempo total en segundos 4.4253740311 
                Tiempo promedio en segundos 0.0000000044
        ```

        Se puede observar que las operaciones de suma, resta y producto tardan casi el mismo tiempo, sin embargo la operación de división tarda más tiempo (casi el doble podría decirse). Esto se debe a que la operación de division suele ser una operación más costosa en términos de tiempo de ejecución debido a la complejidad de su implementación a nivel de hardware y algoritmos en comparación a la suma, resta y producto.

        Si asignamos a x e y valores que sean potencias de 2 y ejecutamos de nuevo el programa, a la salida obtenemos lo siguiente

        ```
            x = 1024, y = 512

            Suma...
                Tiempo total en segundos 2.2862520218 
                Tiempo promedio en segundos 0.0000000023 
            Resta...
                Tiempo total en segundos 2.0121490955 
                Tiempo promedio en segundos 0.0000000020 
            Producto...
                Tiempo total en segundos 2.2906899452 
                Tiempo promedio en segundos 0.0000000023 
            Division...
                Tiempo total en segundos 2.5266251564 
                Tiempo promedio en segundos 0.0000000025
        ```

        Donde se puede observar en este caso que los tiempos de todas las operaciones pasan a ser similares. Esto se debe a que en estos casos la operación de división se vuelve más eficiente y que se reducen las operaciones a realizar. En vez de realizar una operación de división completa, se puede realizar una operación de desplazamiento a la derecha en el nivel de bits, que es una operación mucho más rápida y eficiente.

4. En función del ejercicio anterior analice el algoritmo instrucciones2.c que resuelve una operación binaria (dos operandos) con dos operaciones distintas.

    - Generalmente se puede observar al ejecutar el programa que la división tarda más que el producto, y que estos en general no varían de gran manera en sus tiempos de ejecución.


        **Nota:** Preguntar este ejercicio

5. Investigue en la documentación del compilador o a través de Internet qué opciones de optimización ofrece el compilador gcc (flag O). Compile y ejecute el algoritmo matrices.c, el cual resuelve una multiplicación de matrices de NxN. Explore los diferentes niveles de optimización para distintos tamaños de matrices. ¿Qué optimizaciones aplica el compilador? ¿Cuál es la ganancia respecto a la versión sin optimización del compilador? ¿Cuál es la ganancia entre los distintos niveles?

    - -O aplica habilita flags de optimización al compilador. Sin ningúna opción de optimización activada, el compilador tendrá como objetivo reducir el costo de compilación y las tareas de debugging. Activando los flags de optimización, el compilador intentará mejorar el rendimiento y/o el tamaño del programa a expensas del tiempo de compilación y posiblemente de la capacidad de debuggear el programa. se tienen varios niveles de optimizaciones (O, O2, O3) y los mismos habilitan diferentes flags de optimización.

        Ahora ejecutamos el programa matrices.c con las diferentes opciones de optimización activadas para comparar como cambian sus tiempos de ejecución.

        ```
            # Con Opción O no activada
                Multiplicacion de matrices de 100x100. Tiempo en segundos 0.021741
                Multiplicacion de matrices resultado correcto
            # Con opción -O activada
                Multiplicacion de matrices de 100x100. Tiempo en segundos 0.001662
                Multiplicacion de matrices resultado correcto
            # Con opción -O2 activada
                Multiplicacion de matrices de 100x100. Tiempo en segundos 0.001719
                Multiplicacion de matrices resultado correcto
            # Con opción -O3 activada
                Multiplicacion de matrices de 100x100. Tiempo en segundos 0.001578
                Multiplicacion de matrices resultado correcto    
        ```

        Podemos observar que la mayor diferencia en tiempo de ejecución puede observarse cuando no se activa la opción -O y luego se activa dicha opción. luego entre las opciones -O, -O2 y -O3 no se observan grandes diferencias en cuanto al tiempo de ejecución, por lo que no veo grandes ganancias en que el tiempo de compilación aumente y solo mejorar en décimas de segundos el tiempo de ejecución. En general hay que tener un conocimiento del dominio del problema y asi tener en cuenta que conviene más, si sacrificar tiempo de ejecución o tiempo de compilación.

6. Dada la ecuación cuadrática: $$ x = 2 − 4.0000000 x + 3.9999999 = 0$$ sus raíces son r1 = 2.000316228 y r2 = 1.999683772 (empleando 10 dígitos para la parte decimal).

    a. El algoritmo quadratic1.c computa las raíces de esta ecuación empleando los tipos de datos
    float y double. Compile y ejecute el código. ¿Qué diferencia nota en el resultado?

    - Al ejecutar el programa quadratic1.c obtenemos:

        ```
            Soluciones Float: 2.00000	2.00000
            Soluciones Double: 2.00032	1.99968
        ```

        Se puede observar que las soluciones con tipo de dato double nos dan una mayor precisión que las soluciones con tipo de dato float. Esto se debe a la cantidad de bits asociada a cada variable, 32 para las del tipo float, 64 para las del tipo double.

    b. El algoritmo quadratic2.c computa las raíces de esta ecuación, pero en forma repetida. Compile y ejecute el código variando la constante TIMES. ¿Qué diferencia nota en la ejecución? 

    - Al ejecutar el programa obtenemos:
    
        ```
            # TIMES = 100
            Tiempo requerido solucion Double: 1.969867
            Tiempo requerido solucion Float: 2.937815

            #TIMES = 500
            Tiempo requerido solucion Double: 9.664860
            Tiempo requerido solucion Float: 14.651240

            # TIMES = 1000
            Tiempo requerido solucion Double: 19.405977
            Tiempo requerido solucion Float: 29.276145
        ```

        Puede observarse que en general las soluciones con tipo de dato double tardan menos en todos los casos que cuando se usan tipo de datos float. Además, al aumentar **TIMES** noto que para obtener las soluciones utilizando tipo de datos double aumentan el tiempo de ejecución de 10 en 10 aprox. Mientras que para obtener las soluciones utilizando tipo de datos float, el tiempo de ejecución aumenta pero cada vez de mayor manera.

        **Nota:** preguntar esto 
    
    c. El algoritmo quadratic3.c computa las raíces de esta ecuación, pero en forma repetida. Compile y ejecute el código variando la constante TIMES. ¿Qué diferencia nota en la ejecución? ¿Qué diferencias puede observar en el código con respecto a quadratic2.c?

    - Al ejecutar el programa quadatric3.c obtenemos que:

        ```
            # TIMES = 100
            Tiempo requerido solucion Double: 1.969256
            Tiempo requerido solucion Float: 1.515367

            # TIMES = 500
            Tiempo requerido solucion Double: 9.743275
            Tiempo requerido solucion Float: 7.525010

            # TIMES = 1000
            Tiempo requerido solucion Double: 19.455622
            Tiempo requerido solucion Float: 15.071261
        ```

        Ahora puede observarse que el tiempo de ejecución de la función utilizando tipo de datos float es menor en comparación que la que utiliza tipo de datos double. Observando el código, se ve que en quadatric3.c se definen las constantes FA, FB y FC y se le asignan valores float, y luego estos se asignan a fa, fb y fc cuando se inicializan. Intuyo que esto en comparación a quadatric2.c puede ahorrar el paso de tener que hacer un upcasting para convertir los valores de double a float.

7. Analice los algoritmos iterstruc1.c e iterstruc2.c que resuelven una multiplicación de matrices utilizando dos estructuras de control distintas. ¿Cuál de las dos estructuras de control tiende a acelerar el cómputo? Compile con y sin opciones de optimización del compilador.

    - ```
        # Todas las veces N = 1024

        # iterstruc1 sin optimizar
        Incializando matrices...
        Calculando For...
        Tiempo For en segundos 4.942071

        # itesrtruc1 optimizado
        Incializando matrices...
        Calculando For...
        Tiempo For en segundos 1.153361

        # iterstruc2 sin optimizar
        Incializando matrices...
        Calculando While...
        Tiempo While en segundos 5.081174

        # iterstruc optimizado
        Incializando matrices...
        Calculando While...
        Tiempo While en segundos 1.208659

      ```

      Comparando los códigos en iterstruc1.c e iterstruc2.c, la diferencia está en como realizan las iteraciones. En iterstruc1.c las iteraciones se hacen mediante un for, mientras que en iterstruc2.c se hacen con un while. A pesar de esta diferencia entre los códigos, no se observa que una u otra estructura de control tienda a acelerar el cómputo. Solo se acelera el cómputo cuando se activan las opciones de optimización para ambos casos.


8. Analice el algoritmo matrices.c. ¿Dónde cree que se producen demoras? ¿Cómo podría optimizarse el código? Al menos, considere los siguientes aspectos:

    - Explotación de localidad de datos a través de reorganización interna de matrices A, B o C (según corresponda).
    - El uso de Setters y getters es una buena práctica en la programación orientada a objetos. ¿Tiene sentido usarlos en este caso? ¿cuál es su impacto en el rendimiento?
    - ¿Hay expresiones en el cómputo que pueden refactorizarse para no ser computadas en forma repetida?
    - En lugar de ir acumulando directamente sobre la posición C[i,j] de la matriz resultado (línea 72), pruebe usar una variable local individual y al finalizar el bucle más interno, asigne su valor a C[i,j]. ¿Esta modificación impacta en el rendimiento? ¿Por qué?

    Combine las mejoras que haya encontrado para obtener una solución optimizada y compare los tiempos con la solución original para diferentes tamaños de matrices.

    - Se puede aprovechar la localidad de datos reorganizando las matrices de tal manera que se almacenen como arreglos unidimensionales y el acceso a los valores de la misma sea de forma consecutiva en memoria, ya que estos de esta forma se almacenarán de forma contigua.

    - En este caso, no tiene sentido usar getters y setters, ya que agrega un acceso adicional a memoria que podría evitarse. En lugar de esto, se puede acceder directamente a los valores almacenados en memoria dependiendo de como esten organizados estos (si por filas o columnas).

    - No observo expresiones en el cómputo que esten repetidas.

    - Al colocar una variable temporal, hace que el tiempo de ejecución del programa sea menor, pero solo por unas milesimas de segundos, no es mucha diferencia en este caso.

    - Con la forma optimizada, los tiempos de ejecución son los siguientes:

        ```
            # N = 1024 código sin optimizar
            Multiplicacion de matrices de 1024x1024. Tiempo en segundos 8.321785
            Multiplicacion de matrices resultado correcto

            # N = 1024 código optimizado
            Multiplicacion de matrices de 1024x1024. Tiempo en segundos 1.186097
            Multiplicacion de matrices resultado correcto

            # N = 2048 código sin optimizar
            Multiplicacion de matrices de 2048x2048. Tiempo en segundos 83.707171
            Multiplicacion de matrices resultado correcto

            # N = 2048 código optimizado
            Multiplicacion de matrices de 2048x2048. Tiempo en segundos 9.668741
            Multiplicacion de matrices resultado correcto
        ``` 

        Se puede notar que optimizando el código según lo planteado, se reduce el tiempo de ejecución.

9. Analice y describa brevemente cómo funciona el algoritmo mmblk.c que resuelve la multiplicación de matrices cuadradas de NxN utilizando una técnica de multiplicación por bloques. Luego, ejecute el algoritmo utilizando distintos tamaños de matrices y distintos tamaños de bloque (pruebe con valores que sean potencia de 2; p.e. N={512,1024,2048} y TB={16,32,64,128}). Finalmente, compare los tiempos con respecto a la multiplicación de matrices optimizada del ejercicio anterior. Según el tamaño
de las matrices y de bloque elegido, responda: ¿Cuál es más rápido? ¿Por qué? ¿Cuál sería el tamaño de bloque óptimo para un determinado tamaño de matriz? ¿De qué depende el tamaño de bloque óptimo para un sistema?

    -    

10. Analice el algoritmo triangular.c que resuelve la multiplicación de una matriz cuadrada por una matriz triangular inferior, ambas de NxN. ¿Cómo se podría optimizar el código? ¿Se pueden evitar operaciones? ¿Se puede reducir la memoria reservada? Implemente una solución optimizada y compare los tiempos probando con diferentes tamaños de matrices.

    -