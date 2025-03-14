# Recursividad en Java: Ejercicios Resueltos Paso a Paso

La recursividad es una técnica de programación en la que una función se llama a sí misma para resolver un problema dividiéndolo en subproblemas más pequeños. A continuación se presentan varios ejercicios clásicos de recursividad en Java, ordenados desde un nivel básico hasta un nivel avanzado. Cada ejercicio incluye una introducción del problema, la solución con código Java comentado, una explicación detallada paso a paso del proceso recursivo y ejemplos de ejecución con sus resultados esperados.

Ejemplo básico: Factorial de un número

Introducción: El factorial de un número entero positivo n (denotado como n!) se define como el producto de todos los enteros positivos desde 1 hasta n. Por ejemplo, 5! = 5 \times 4 \times 3 \times 2 \times 1 = 120. En recursividad, el factorial tiene una definición natural: el caso base es 0! = 1 y para n > 0, n! = n \times (n-1)!. Usaremos recursividad para calcular el factorial, multiplicando el número por el factorial de su predecesor hasta llegar al caso base.

Código en Java:

public static int factorial(int n) {
    // Caso base: el factorial de 0 es 1
    if (n == 0) {
        return 1;
    }
    // Llamada recursiva: n * factorial de (n-1)
    return n * factorial(n - 1);
}

Paso a paso del proceso recursivo:

Supongamos que llamamos a factorial(5). A continuación se detalla cómo se desarrolla la recursividad:
	1.	factorial(5) comprueba el caso base. Como 5 no es 0, procede a calcular 5 * factorial(4).
	2.	Para calcular factorial(4), la función invoca recursivamente factorial(4). Nuevamente 4 no es 0, así que intenta calcular 4 * factorial(3).
	3.	La función llama a factorial(3). Dado que 3 no es 0, continúa con 3 * factorial(2).
	4.	La función llama a factorial(2). Como 2 no es 0, sigue con 2 * factorial(1).
	5.	La función llama a factorial(1). 1 no es 0, así que intenta calcular 1 * factorial(0).
	6.	La función llama a factorial(0). Aquí se cumple el caso base (n == 0), por lo que la función retorna 1 directamente.
	7.	Ahora comienza la fase de retorno de la recursión: factorial(1) recibe el resultado de factorial(0) (que es 1) y calcula 1 * 1 = 1.
	8.	factorial(2) recibe el resultado de factorial(1) (1) y calcula 2 * 1 = 2.
	9.	factorial(3) recibe el resultado de factorial(2) (2) y calcula 3 * 2 = 6.
	10.	factorial(4) recibe el resultado de factorial(3) (6) y calcula 4 * 6 = 24.
	11.	Finalmente, factorial(5) recibe el resultado de factorial(4) (24) y calcula 5 * 24 = 120. Este es el resultado final que devuelve factorial(5).

Ejecución con ejemplos y resultado esperado:

System.out.println("Factorial de 5 = " + factorial(5));  // Factorial de 5 = 120
System.out.println("Factorial de 0 = " + factorial(0));  // Factorial de 0 = 1

Ejemplo intermedio: Cálculo del término n-ésimo de la secuencia de Fibonacci

Introducción: La sucesión de Fibonacci es una serie de números donde cada término (a partir del tercero) es la suma de los dos anteriores. La secuencia comienza típicamente con 0 y 1, por lo que queda: 0, 1, 1, 2, 3, 5, 8, 13, … etc. Para calcular recursivamente el término n-ésimo de Fibonacci, definimos los casos base como los términos iniciales: F(0) = 0 y F(1) = 1. Luego, para n \geq 2, F(n) = F(n-1) + F(n-2). Utilizaremos esta definición recursiva en la implementación.

Código en Java:

public static int fibonacci(int n) {
    // Caso base: Fibonacci de 0 es 0, y de 1 es 1
    if (n == 0 || n == 1) {
        return n;
    }
    // Llamada recursiva: suma de los dos anteriores
    return fibonacci(n - 1) + fibonacci(n - 2);
}

Paso a paso del proceso recursivo:

Veamos qué ocurre al calcular, por ejemplo, fibonacci(5):
	1.	fibonacci(5) no es caso base (5 > 1), debe calcular fibonacci(4) + fibonacci(3).
	2.	Para calcular fibonacci(4), la función llama recursivamente a fibonacci(4):
	•	fibonacci(4) = fibonacci(3) + fibonacci(2) (ya que 4 > 1).
	•	Para obtener fibonacci(3): fibonacci(3) = fibonacci(2) + fibonacci(1).
	•	fibonacci(2) = fibonacci(1) + fibonacci(0); aquí fibonacci(1) devuelve 1 (caso base) y fibonacci(0) devuelve 0 (caso base). Por lo tanto, fibonacci(2) retorna 1 + 0 = 1.
	•	Ahora, con fibonacci(2) calculado como 1, fibonacci(3) puede retornar fibonacci(2) + fibonacci(1) = 1 + 1 = 2 (recordando que fibonacci(1) es 1).
	•	Paralelamente, para completar fibonacci(4), necesitamos también fibonacci(2) (además de fibonacci(3) que acabamos de calcular). Ya calculamos fibonacci(2) anteriormente como 1. Entonces fibonacci(4) = fibonacci(3) + fibonacci(2) = 2 + 1 = 3.
	3.	Ahora volvemos a fibonacci(5). Ya tenemos fibonacci(4) = 3. Necesitamos calcular fibonacci(3) (la segunda parte de la suma original fibonacci(4) + fibonacci(3)):
	•	Podemos notar que fibonacci(3) fue calculado antes como 2. En una implementación real, esa llamada se realizaría de nuevo a menos que usemos memoización, pero para entender el flujo supondremos ese valor conocido: fibonacci(3) resultará en 2.
	4.	Finalmente, fibonacci(5) suma los resultados: fibonacci(4) + fibonacci(3) = 3 + 2 = 5. Este es el valor que devuelve fibonacci(5).

Ejecución con ejemplos y resultado esperado:

System.out.println("Fibonacci de 5 = " + fibonacci(5));  // Fibonacci de 5 = 5
System.out.println("Fibonacci de 6 = " + fibonacci(6));  // Fibonacci de 6 = 8

Ejemplo práctico: Suma de los dígitos de un número

Introducción: Este problema consiste en sumar todos los dígitos de un número entero. Por ejemplo, si el número es 1234, la suma de sus dígitos es 1+2+3+4 = 10. Podemos resolverlo recursivamente aprovechando que un número se puede descomponer en su último dígito y el resto del número. La idea es tomar el último dígito (usando la operación módulo 10) y sumarlo a la suma de los dígitos restantes del número (el número dividido entre 10). El proceso continúa hasta llegar a un número de un solo dígito, que es el caso base.

Código en Java:

public static int sumaDigitos(int n) {
    // Caso base: si n es menor de 10, se devuelve n (el número es de una sola cifra)
    if (n < 10) {
        return n;
    }
    // Llamada recursiva: último dígito (n % 10) + suma de dígitos del resto del número (n / 10)
    return (n % 10) + sumaDigitos(n / 10);
}

Paso a paso del proceso recursivo:

Consideremos el cálculo de sumaDigitos(1234):
	1.	sumaDigitos(1234) no es caso base (1234 tiene más de un dígito). Se separa el último dígito: 1234 % 10 = 4, y el resto: 1234 / 10 = 123. La función necesita calcular 4 + sumaDigitos(123).
	2.	sumaDigitos(123) tampoco es caso base (123 tiene varios dígitos). 123 % 10 = 3, resto 123 / 10 = 12. Se plantea calcular 3 + sumaDigitos(12) (este resultado se sumará luego con el 4 que quedó pendiente en el paso anterior).
	3.	sumaDigitos(12) tampoco es caso base (12 tiene dos dígitos). 12 % 10 = 2, resto 12 / 10 = 1. Calcula 2 + sumaDigitos(1).
	4.	sumaDigitos(1) sí es caso base (1 es menor que 10). La función retorna 1.
	5.	Ahora, sumaDigitos(12) recibe el resultado de sumaDigitos(1) (que es 1) y calcula 2 + 1 = 3.
	6.	sumaDigitos(123) recibe el resultado de sumaDigitos(12) (que es 3) y lo suma con su último dígito (3), obteniendo 6.
	7.	sumaDigitos(1234) recibe el resultado de sumaDigitos(123) (6) y lo suma con su último dígito (4), obteniendo 10.
	8.	Finalmente, sumaDigitos(1234) retorna 10, que es la suma de todos sus dígitos.

Ejecución con ejemplos y resultado esperado:

System.out.println("Suma de dígitos de 1234 = " + sumaDigitos(1234));  // Suma de dígitos de 1234 = 10
System.out.println("Suma de dígitos de 7 = " + sumaDigitos(7));        // Suma de dígitos de 7 = 7

Ejemplo avanzado: Inversión de una cadena de texto de forma recursiva

Introducción: Invertir una cadena de texto (es decir, obtener la cadena al revés) es un problema clásico. Por ejemplo, la cadena "hola" invertida es "aloh". Usando recursividad, podemos invertir una cadena tomando un carácter de la cadena y resolviendo recursivamente el problema para el resto. El enfoque típico es considerar el primer carácter y colocarlo al final de la cadena invertida del resto de los caracteres. El caso base ocurre cuando la cadena está vacía o tiene un solo carácter, en cuyo caso se retorna tal cual (ya está “invertida”).

Código en Java:

public static String invertirCadena(String str) {
    // Caso base: cadena vacía o con un solo carácter, se retorna la misma cadena
    if (str.length() <= 1) {
        return str;
    }
    // Llamada recursiva: invierte la subcadena a partir del segundo carácter y luego añade el primer carácter al final
    return invertirCadena(str.substring(1)) + str.charAt(0);
}

Paso a paso del proceso recursivo:

Supongamos que queremos invertir la cadena "hola" llamando a invertirCadena("hola"):
	1.	"hola" tiene más de un carácter, por lo que se toma el primer carácter 'h' aparte y se llama recursivamente a invertirCadena("ola"). (Queda pendiente agregar 'h' al final del resultado de esa llamada recursiva).
	2.	En la llamada invertirCadena("ola"), la cadena "ola" también tiene más de un carácter. Se separa 'o' y se llama a invertirCadena("la"), dejando 'o' pendiente para añadir al final.
	3.	En la llamada invertirCadena("la"), la cadena "la" tiene más de un carácter. Se separa 'l' y se llama a invertirCadena("a"), dejando 'l' pendiente.
	4.	En la llamada invertirCadena("a"), la longitud de la cadena es 1 (caso base). La función retorna "a" sin realizar más llamadas recursivas.
	5.	Comienza la fase de retorno: la llamada invertirCadena("la") recibe la salida de invertirCadena("a") (que es "a") y le agrega el carácter que tenía pendiente ('l') al final, formando "al".
	6.	Esa salida "al" es devuelta a invertirCadena("ola"), que le agrega su carácter pendiente 'o', formando "alo".
	7.	Esa salida "alo" es devuelta a invertirCadena("hola"), que le agrega el carácter pendiente 'h', formando "aloh".
	8.	Finalmente, invertirCadena("hola") retorna "aloh", que es la cadena invertida.

Ejecución con ejemplos y resultado esperado:

System.out.println(invertirCadena("hola"));       // aloh
System.out.println(invertirCadena("recursivo"));  // ovisrucer  (cadena invertida)
System.out.println(invertirCadena(""));           //  (cadena vacía permanece vacía)

Ejemplo aplicado: Búsqueda binaria recursiva en un array ordenado

Introducción: La búsqueda binaria es un algoritmo eficiente para encontrar un elemento en un array ordenado. Consiste en comparar el elemento buscado con el elemento central del rango considerado y, en función de esa comparación, descartar la mitad del rango. En la versión recursiva, la función se llamará a sí misma reduciendo el rango de búsqueda a la mitad en cada paso. El caso base ocurre cuando el rango está vacío (no quedan elementos por buscar) o cuando encontramos el elemento. En esta implementación, la función retornará la posición (índice) donde se encuentra el elemento buscado, o -1 si no se encuentra.

Código en Java:

public static int busquedaBinaria(int[] arr, int objetivo, int inicio, int fin) {
    // Caso base: rango inválido (el elemento no está en el array)
    if (inicio > fin) {
        return -1;
    }
    int medio = (inicio + fin) / 2;
    // Si el elemento central es el objetivo, lo encontramos: retornar índice medio
    if (arr[medio] == objetivo) {
        return medio;
    } 
    // Si el objetivo es menor que el elemento central, buscar en la mitad izquierda
    else if (objetivo < arr[medio]) {
        return busquedaBinaria(arr, objetivo, inicio, medio - 1);
    } 
    // Si el objetivo es mayor que el elemento central, buscar en la mitad derecha
    else {
        return busquedaBinaria(arr, objetivo, medio + 1, fin);
    }
}

(Nota: La primera llamada a esta función típicamente sería busquedaBinaria(miArray, valorBuscado, 0, miArray.length - 1) para iniciar la búsqueda en todo el array.)

Paso a paso del proceso recursivo:

Supongamos un array ordenado datos = [1, 3, 5, 7, 9] y queremos buscar el valor 7 llamando a busquedaBinaria(datos, 7, 0, 4):
	1.	Primera llamada: inicio = 0, fin = 4. Calculamos medio = (0 + 4) / 2 = 2. El elemento central es datos[2] = 5. Como 7 (objetivo) es mayor que 5, descartamos la mitad izquierda (todos los elementos en índices 0,1,2). Ahora nos enfocamos en la mitad derecha del array.
	2.	Llamada recursiva: ahora inicio = 3, fin = 4. Calculamos medio = (3 + 4) / 2 = 3 (división entera). El elemento central ahora es datos[3] = 7, que coincide con el valor buscado. ¡Encontramos el elemento! La función retornará el índice 3.
	3.	La llamada original recibe el valor retornado (3) y a su vez lo retorna como resultado final de la búsqueda.

Si en algún punto el subrango se vuelve inválido (por ejemplo, inicio supera a fin sin haber encontrado el elemento), la función retornará -1 indicando que el elemento no está en el array.

Ejecución con ejemplos y resultado esperado:

int[] datos = {1, 3, 5, 7, 9};
System.out.println(busquedaBinaria(datos, 7, 0, datos.length - 1));  // 3
System.out.println(busquedaBinaria(datos, 4, 0, datos.length - 1));  // -1 (no encontrado)

Ejercicio desafío: Resolver el problema de las Torres de Hanói con explicación

Introducción: Las Torres de Hanói es un famoso problema matemático y de recursividad. Se tienen tres postes (torres) y n discos apilados en uno de ellos (torre de origen), ordenados por tamaño de mayor (abajo) a menor (arriba). El objetivo es trasladar toda la pila de n discos desde la torre de origen hasta otra torre de destino, usando la tercera torre como auxiliar, y cumpliendo dos reglas: 1) solo se puede mover un disco a la vez, y 2) nunca se puede colocar un disco más grande sobre otro más pequeño. La solución recursiva aplica el siguiente plan:
	1.	Mover recursivamente los primeros n-1 discos de la torre origen a la torre auxiliar.
	2.	Mover el disco n (el más grande) de la torre origen a la torre destino.
	3.	Mover recursivamente los n-1 discos que estaban en la torre auxiliar a la torre destino.

Este algoritmo divide el problema en subproblemas más pequeños (mover pilas más pequeñas de discos) y permite resolverlo en el mínimo número de movimientos necesarios.

Código en Java:

public static void resolverHanoi(int n, char origen, char auxiliar, char destino) {
    if (n == 1) {
        // Caso base: mover un único disco directamente de origen a destino
        System.out.println("Mover disco 1 de " + origen + " a " + destino);
    } else {
        // Mover n-1 discos de origen a auxiliar (usando destino como apoyo)
        resolverHanoi(n - 1, origen, destino, auxiliar);
        // Mover el disco n (más grande) de origen a destino
        System.out.println("Mover disco " + n + " de " + origen + " a " + destino);
        // Mover los n-1 discos desde auxiliar a destino (usando origen como apoyo)
        resolverHanoi(n - 1, auxiliar, origen, destino);
    }
}

Paso a paso del proceso recursivo:

Veamos cómo funciona resolverHanoi(3, 'A', 'B', 'C'), donde queremos mover 3 discos desde la torre A (origen) a la torre C (destino) usando B como auxiliar:
	1.	Llamada inicial: resolverHanoi(3, A, B, C). Como n > 1, se ejecuta primero resolverHanoi(2, A, C, B) para mover 2 discos de A a B (dejando libre el disco mayor).
	2.	En resolverHanoi(2, A, C, B): Como n > 1, se ejecuta resolverHanoi(1, A, B, C) para mover 1 disco de A a C (usando B como auxiliar).
	3.	resolverHanoi(1, A, B, C): Caso base, imprime “Mover disco 1 de A a C”.
	4.	Regresando a resolverHanoi(2, A, C, B) tras la llamada anterior, ahora imprime “Mover disco 2 de A a B” (mover el disco de tamaño 2 de A a B).
	5.	Luego llama a resolverHanoi(1, C, A, B) para mover 1 disco de C a B (usando A como auxiliar).
	6.	resolverHanoi(1, C, A, B): Caso base, imprime “Mover disco 1 de C a B”.
	7.	Regresamos a resolverHanoi(3, A, B, C) después de haber movido 2 discos de A a B. Ahora imprime “Mover disco 3 de A a C” (mover el disco más grande al destino).
	8.	Finalmente, llama a resolverHanoi(2, B, A, C) para mover los 2 discos restantes desde B hasta C (usando A como auxiliar).
	9.	En resolverHanoi(2, B, A, C): llama a resolverHanoi(1, B, C, A) para mover 1 disco de B a A.
	10.	resolverHanoi(1, B, C, A): Caso base, imprime “Mover disco 1 de B a A”.
	11.	Regresa a resolverHanoi(2, B, A, C) e imprime “Mover disco 2 de B a C”.
	12.	Llama a resolverHanoi(1, A, B, C) para mover 1 disco de A a C.
	13.	resolverHanoi(1, A, B, C): Caso base, imprime “Mover disco 1 de A a C”.
	14.	Con esto finaliza la secuencia de movimientos. En total se han realizado 7 movimientos, que son los necesarios para trasladar 3 discos de A a C.

Ejecución con ejemplo y resultado esperado:

System.out.println("Movimientos para 3 discos:");
resolverHanoi(3, 'A', 'B', 'C');  
// Mover disco 1 de A a C
// Mover disco 2 de A a B
// Mover disco 1 de C a B
// Mover disco 3 de A a C
// Mover disco 1 de B a A
// Mover disco 2 de B a C
// Mover disco 1 de A a C

Nota: Como se observa, para 3 discos se requieren 7 movimientos (2^3 - 1 = 7). En general, para n discos, el número mínimo de movimientos necesarios es 2^n - 1.
