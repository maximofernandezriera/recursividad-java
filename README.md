## **Introducción a la Recursividad en Java**

La recursividad es una técnica de programación fundamental en la que una función se llama a sí misma para resolver un problema. Esta estrategia resulta particularmente útil para abordar problemas que pueden descomponerse en subproblemas más pequeños y de naturaleza similar . En esencia, la recursividad permite resolver un problema complejo mediante la solución de instancias más sencillas del mismo problema .  
Un aspecto central de la recursividad reside en la identificación de sus componentes clave. En primer lugar, se encuentra el **caso base**, que define la condición bajo la cual la recursión debe detenerse. Este caso representa la instancia más simple del problema, cuya solución se conoce directamente y no requiere de más llamadas recursivas . Sin un caso base definido de manera apropiada, una función recursiva podría invocarse a sí misma de forma indefinida, lo que conduciría a un error de desbordamiento de pila . En segundo lugar, se halla el **caso recursivo**, donde la función se llama a sí misma con una entrada modificada, acercándose progresivamente al caso base. La solución para la instancia actual del problema se expresa en términos de la solución obtenida para la instancia más pequeña .  
La aplicación de la recursividad ofrece ciertas ventajas notables. Para algunos tipos de problemas, especialmente aquellos con estructuras inherentemente recursivas como los árboles, la recursividad puede conducir a soluciones elegantes y concisas, facilitando tanto la comprensión como la implementación del código . De hecho, las soluciones recursivas a menudo sirven como base para algoritmos más avanzados como la programación dinámica y los algoritmos de divide y vencerás . Sin embargo, es importante reconocer que la recursividad también presenta ciertos inconvenientes. En algunos casos, las soluciones recursivas pueden ser menos eficientes que sus contrapartes iterativas debido a la sobrecarga asociada con las llamadas a funciones y al riesgo de errores de desbordamiento de pila si la profundidad de la recursión se vuelve excesiva . Cada llamada recursiva requiere espacio adicional en la memoria de la pila . Por lo tanto, si bien la recursividad puede ofrecer soluciones claras para ciertos problemas, es crucial considerar sus posibles implicaciones en el rendimiento, especialmente en lo que respecta al uso de memoria y la posibilidad de desbordamiento de pila en recursiones profundas.

## **Ejercicios de Recursividad Básicos**

### **Factorial**

**Introducción:** El factorial de un entero no negativo n, denotado como n\!, se define como el producto de todos los enteros positivos menores o iguales a n. Por convención, el factorial de 0 se define como 1 (0\! \= 1\) . Esta función tiene diversas aplicaciones en matemáticas y ciencias de la computación, como el cálculo de permutaciones .  
**Código Java:**  
`public class Factorial {`  
    `public static long factorial(int n) {`  
        `// Caso base: el factorial de 0 o 1 es 1`  
        `if (n <= 1) {`  
            `return 1;`  
        `} else {`  
            `// Caso recursivo: n! = n * (n-1)!`  
            `return n * factorial(n - 1);`  
        `}`  
    `}`

    `public static void main(String args) {`  
        `System.out.println("Factorial de 5: " + factorial(5)); // Salida esperada: 120`  
        `System.out.println("Factorial de 0: " + factorial(0)); // Salida esperada: 1`  
    `}`  
`}`

            public class Factorial {
            2	    public static long factorial(int n) {
            3	        // Caso base: el factorial de 0 o 1 es 1
            4	        if (n <= 1) {
            5	            return 1;
            6	        } else {
            7	            // Caso recursivo: n! = n * (n-1)!
            8	            return n * factorial(n - 1);
            9	        }
            10	    }
            11	
            12	    // Added a main method for testing the factorial function
            13	    public static void main(String[] args) {
            14	        System.out.println(factorial(5));  // Output: 120
            15	    }
            16	}  // Added this line to close the class

**Explicación Paso a Paso:**

1. El método factorial toma un entero n como entrada.  
2. **Caso Base:** Si n es menor o igual a 1, el método retorna inmediatamente 1\. Esto detiene la recursión para n \= 0 y n \= 1\.  
3. **Caso Recursivo:** Si n es mayor que 1, el método retorna el producto de n y el resultado de llamar a factorial con n \- 1\.  
4. Por ejemplo, factorial(5) se ejecutará de la siguiente manera:  
   * factorial(5) retorna 5 \* factorial(4)  
   * factorial(4) retorna 4 \* factorial(3)  
   * factorial(3) retorna 3 \* factorial(2)  
   * factorial(2) retorna 2 \* factorial(1)  
   * factorial(1) retorna 1 (caso base)  
   * Los resultados se multiplican de vuelta: 2 \* 1 \= 2, 3 \* 2 \= 6, 4 \* 6 \= 24, 5 \* 24 \= 120\.

**Ejemplos de Ejecución:**

* Factorial.factorial(5) producirá la salida: Factorial de 5: 120  
* Factorial.factorial(0) producirá la salida: Factorial de 0: 1

**Consideraciones:**  
La definición matemática del factorial, n\! \= n \* (n-1)\!, se traduce directamente a la estructura del código recursivo . Esta correspondencia hace que la implementación recursiva sea una representación natural del concepto. Es fundamental que el caso base (n \<= 1\) detenga la recursión, ya que de lo contrario, la función se llamaría a sí misma con números negativos decrecientes, lo que eventualmente provocaría un error de desbordamiento de pila.

**Tabla 1: Comparación de Factorial Iterativo vs. Recursivo (para n=3)**

| Paso | Factorial Iterativo (n=3) | Factorial Recursivo (n=3) |
| :---- | :---- | :---- |
| 1 | resultado \= 1, i \= 1 | factorial(3) llama a 3 \* factorial(2) |
| 2 | resultado \= 1 \* 1 \= 1, i \= 2 | factorial(2) llama a 2 \* factorial(1) |
| 3 | resultado \= 1 \* 2 \= 2, i \= 3 | factorial(1) retorna 1 (caso base) |
| 4 | resultado \= 2 \* 3 \= 6 | factorial(2) retorna 2 \* 1 \= 2 |
| 5 | Fin del bucle | factorial(3) retorna 3 \* 2 \= 6 |

### **Secuencia de Fibonacci**

**Introducción:** La secuencia de Fibonacci es una serie de números que comienza con 0 y 1, donde cada número subsiguiente es la suma de los dos números precedentes. La secuencia comienza típicamente así: 0, 1, 1, 2, 3, 5, 8, 13, 21, etc.. Esta secuencia aparece en diversos fenómenos naturales y tiene aplicaciones en informática.  
**Código Java:**  
`public class Fibonacci {`  
    `public static int fibonacci(int n) {`  
        `// Casos base: Fibonacci de 0 es 0, y Fibonacci de 1 es 1`  
        `if (n <= 1) {`  
            `return n;`  
        `} else {`  
            `// Caso recursivo: fib(n) = fib(n-1) + fib(n-2)`  
            `return fibonacci(n - 1) + fibonacci(n - 2);`  
        `}`  
    `}`

    `public static void main(String args) {`  
        `System.out.println("Fibonacci de 10: " + fibonacci(10)); // Salida esperada: 55`  
        `System.out.print("Primeros 10 números de Fibonacci: ");`  
        `for (int i = 0; i < 10; i++) {`  
            `System.out.print(fibonacci(i) + " "); // Salida esperada: 0 1 1 2 3 5 8 13 21 34`  
        `}`  
        `System.out.println();`  
    `}`  
`}`

**Explicación Paso a Paso:**

1. El método fibonacci toma un entero n como entrada, representando el índice del número de Fibonacci que se va a calcular.  
2. **Casos Base:** Si n es 0, el método retorna 0\. Si n es 1, el método retorna 1\. Estos son los puntos de inicio de la secuencia.  
3. **Caso Recursivo:** Si n es mayor que 1, el método retorna la suma del (n-1)-ésimo y el (n-2)-ésimo número de Fibonacci, que se calculan llamando recursivamente a fibonacci con n \- 1 y n \- 2\.  
4. Por ejemplo, fibonacci(4) se ejecutará como fibonacci(3) \+ fibonacci(2), que se descompone aún más en (fibonacci(2) \+ fibonacci(1)) \+ (fibonacci(1) \+ fibonacci(0)), y así sucesivamente, hasta que se alcancen los casos base.

**Ejemplos de Ejecución:**

* Fibonacci.fibonacci(10) producirá la salida: Fibonacci de 10: 55  
* El bucle en main producirá la salida: Primeros 10 números de Fibonacci: 0 1 1 2 3 5 8 13 21 34

**Consideraciones:**  
La solución recursiva refleja directamente la definición matemática F(n) \= F(n-1) \+ F(n-2) . La naturaleza recursiva inherente de la secuencia de Fibonacci hace que una implementación recursiva sea sencilla. Sin embargo, esta implementación ilustra el concepto de subproblemas superpuestos, ya que los mismos números de Fibonacci se calculan varias veces . Por ejemplo, al calcular fibonacci(4), fibonacci(2) se calcula dos veces. Esto conduce a una ineficiencia para valores más grandes de n, como se menciona en con respecto a la complejidad temporal de O(2^N).

**Tabla 2: Traza de Ejecución de Fibonacci Recursivo (para n=4)**  
`fibonacci(4)`  
  `fibonacci(3) + fibonacci(2)`  
    `(fibonacci(2) + fibonacci(1)) + (fibonacci(1) + fibonacci(0))`  
      `((fibonacci(1) + fibonacci(0)) + 1) + (1 + 0)`  
        `((1 + 0) + 1) + (1 + 0)`  
          `(1 + 1) + 1`  
            `2 + 1`  
              `3`

### **Cuenta Regresiva**

**Introducción:** La tarea consiste en implementar una función que imprima una cuenta regresiva desde un entero positivo dado hasta 0\.  
**Código Java:**  
`public class Countdown {`  
    `public static void countDown(int number) {`  
        `System.out.println(number);`  
        `// Caso base: detener cuando el número llega a 0`  
        `if (number > 0) {`  
            `// Caso recursivo: llamar a countDown con el siguiente número más pequeño`  
            `countDown(number - 1);`  
        `}`  
    `}`

    `public static void main(String args) {`  
        `System.out.println("Cuenta regresiva desde 3:");`  
        `countDown(3);`  
        `// Salida esperada:`  
        `// 3`  
        `// 2`  
        `// 1`  
        `// 0`  
    `}`  
`}`

**Explicación Paso a Paso:**

1. El método countDown toma un entero number como entrada.  
2. Primero imprime el valor actual de number.  
3. **Caso Base:** Si number es 0 o menor, la condición if (number \> 0\) se vuelve falsa y la recursión se detiene.  
4. **Caso Recursivo:** Si number es mayor que 0, el método se llama a sí mismo (countDown) con number \- 1, continuando la cuenta regresiva.  
5. Por ejemplo, countDown(3) se ejecutará de la siguiente manera:  
   * Imprime 3, luego llama a countDown(2).  
   * countDown(2) imprimirá 2, luego llamará a countDown(1).  
   * countDown(1) imprimirá 1, luego llamará a countDown(0).  
   * countDown(0) imprimirá 0, y la condición if (0 \> 0\) es falsa, por lo que la recursión se detiene.

**Ejemplos de Ejecución:**

* Countdown.countDown(3) producirá la salida:  
  `3`  
  `2`  
  `1`  
  `0`

**Consideraciones:**  
Este ejemplo ilustra una forma simple de recursión donde la función realiza una acción (imprimir) antes de realizar la llamada recursiva. El orden de las operaciones dentro de la función recursiva determina el comportamiento. Aquí, la instrucción de impresión antes de la llamada recursiva da como resultado una secuencia descendente. El caso base (number \<= 0, implícitamente manejado por number \> 0 en la condición if) asegura que la cuenta regresiva finalmente se detenga en 0\.

### **Inversión de Cadena**

**Introducción:** El objetivo es escribir una función recursiva que tome una cadena como entrada y devuelva su versión invertida.  
**Código Java:**  
`public class StringReversal {`  
    `public static String reverseString(String str) {`  
        `// Caso base: una cadena vacía o de un solo carácter es su propia inversa`  
        `if (str.length() <= 1) {`  
            `return str;`  
        `} else {`  
            `// Caso recursivo: invertir la subcadena excluyendo el primer carácter`  
            `// y agregar el primer carácter al final`  
            `return reverseString(str.substring(1)) + str.charAt(0);`  
        `}`  
    `}`

    `public static void main(String args) {`  
        `System.out.println("Inversa de 'hello': " + reverseString("hello")); // Salida esperada: olleh`  
        `System.out.println("Inversa de 'a': " + reverseString("a"));     // Salida esperada: a`  
        `System.out.println("Inversa de '': " + reverseString(""));      // Salida esperada:`  
    `}`  
`}`

**Explicación Paso a Paso:**

1. El método reverseString toma una cadena str como entrada.  
2. **Caso Base:** Si la longitud de str es 0 o 1, el método retorna str directamente, ya que una cadena con cero o un carácter es su propia inversa.  
3. **Caso Recursivo:** Si la longitud de str es mayor que 1, el método hace lo siguiente:  
   * Toma la subcadena de str comenzando desde el segundo carácter (str.substring(1)).  
   * Llama recursivamente a reverseString en esta subcadena.  
   * Luego toma el primer carácter de la cadena original (str.charAt(0)) y lo agrega al final de la subcadena invertida.  
4. Por ejemplo, reverseString("hello") se ejecutará de la siguiente manera:  
   * reverseString("hello") retorna reverseString("ello") \+ 'h'  
   * reverseString("ello") retorna reverseString("llo") \+ 'e'  
   * reverseString("llo") retorna reverseString("lo") \+ 'l'  
   * reverseString("lo") retorna reverseString("o") \+ 'l'  
   * reverseString("o") retorna "o" (caso base)  
   * Los resultados se concatenan de vuelta: "o" \+ 'l' \= "ol", "ol" \+ 'l' \= "oll", "oll" \+ 'e' \= "olle", "olle" \+ 'h' \= "olleh".

**Ejemplos de Ejecución:**

* StringReversal.reverseString("hello") producirá la salida: Inversa de 'hello': olleh  
* StringReversal.reverseString("a") producirá la salida: Inversa de 'a': a  
* StringReversal.reverseString("") producirá la salida: Inversa de '':

**Consideraciones:**  
La recursividad permite una forma concisa e intuitiva de invertir una cadena procesándola carácter por carácter . El problema de invertir una cadena se puede descomponer naturalmente en invertir una cadena más pequeña y luego colocar el carácter restante en el extremo correcto. El caso base maneja los escenarios más simples, asegurando que la recursión termine. El paso recursivo reduce el tamaño del problema en un carácter en cada llamada.

### **Suma de Dígitos**

**Introducción:** El problema consiste en calcular la suma de los dígitos individuales de un entero no negativo dado utilizando la recursividad. Por ejemplo, la suma de los dígitos de 123 es 1 \+ 2 \+ 3 \= 6\.  
**Código Java:**  
`public class SumOfDigits {`  
    `public static int sumOfDigits(int n) {`  
        `// Caso base: si el número es 0, la suma de los dígitos es 0`  
        `if (n == 0) {`  
            `return 0;`  
        `} else {`  
            `// Caso recursivo: la suma de los dígitos es el último dígito más la suma de los dígitos restantes`  
            `return (n % 10) + sumOfDigits(n / 10);`  
        `}`  
    `}`

    `public static void main(String args) {`  
        `System.out.println("Suma de los dígitos de 123: " + sumOfDigits(123)); // Salida esperada: 6`  
        `System.out.println("Suma de los dígitos de 9: " + sumOfDigits(9));   // Salida esperada: 9`  
        `System.out.println("Suma de los dígitos de 0: " + sumOfDigits(0));   // Salida esperada: 0`  
    `}`  
`}`

**Explicación Paso a Paso:**

1. El método sumOfDigits toma un entero no negativo n como entrada.  
2. **Caso Base:** Si n es 0, el método retorna 0, ya que no hay dígitos para sumar.  
3. **Caso Recursivo:** Si n no es 0, el método calcula el último dígito de n utilizando el operador módulo (n % 10). Luego llama recursivamente a sumOfDigits con los dígitos restantes (n / 10\) y suma el último dígito al resultado de la llamada recursiva.  
4. Por ejemplo, sumOfDigits(123) se ejecutará de la siguiente manera:  
   * sumOfDigits(123) retorna (123 % 10\) \+ sumOfDigits(123 / 10\) que es 3 \+ sumOfDigits(12)  
   * sumOfDigits(12) retorna (12 % 10\) \+ sumOfDigits(12 / 10\) que es 2 \+ sumOfDigits(1)  
   * sumOfDigits(1) retorna (1 % 10\) \+ sumOfDigits(1 / 10\) que es 1 \+ sumOfDigits(0)  
   * sumOfDigits(0) retorna 0 (caso base)  
   * Los resultados se suman de vuelta: 1 \+ 0 \= 1, 2 \+ 1 \= 3, 3 \+ 3 \= 6\.

**Ejemplos de Ejecución:**

* SumOfDigits.sumOfDigits(123) producirá la salida: Suma de los dígitos de 123: 6  
* SumOfDigits.sumOfDigits(9) producirá la salida: Suma de los dígitos de 9: 9  
* SumOfDigits.sumOfDigits(0) producirá la salida: Suma de los dígitos de 0: 0

**Consideraciones:**  
La recursividad proporciona una forma clara de procesar los dígitos de un número extrayendo repetidamente el último dígito y procesando la parte restante. El uso de los operadores módulo y división entera conduce naturalmente a una descomposición recursiva del número. El caso base n \== 0 asegura que la recursión se detenga cuando todos los dígitos han sido procesados.

## **Ejercicios de Recursividad Intermedios**

### **Búsqueda Binaria**

**Introducción:** La búsqueda binaria es un algoritmo eficiente para encontrar un valor objetivo específico dentro de una matriz ordenada. Funciona dividiendo repetidamente el intervalo de búsqueda por la mitad .  
**Código Java:**  
`public class BinarySearchRecursive {`  
    `public static int binarySearch(int arr, int target, int low, int high) {`  
        `// Caso base: si el índice bajo excede el índice alto, el objetivo no se encuentra`  
        `if (low > high) {`  
            `return -1;`  
        `}`

        `int mid = low + (high - low) / 2; // Calcular el índice medio`

        `// Si el objetivo está en el medio`  
        `if (arr[mid] == target) {`  
            `return mid;`  
        `}`  
        `// Si el objetivo es menor que el elemento medio, buscar en la mitad izquierda`  
        `else if (arr[mid] > target) {`  
            `return binarySearch(arr, target, low, mid - 1);`  
        `}`  
        `// Si el objetivo es mayor que el elemento medio, buscar en la mitad derecha`  
        `else {`  
            `return binarySearch(arr, target, mid + 1, high);`  
        `}`  
    `}`

    `public static void main(String args) {`  
        `int sortedArray = {2, 5, 7, 8, 11, 12};`  
        `int target = 7;`  
        `int index = binarySearch(sortedArray, target, 0, sortedArray.length - 1);`  
        `if (index != -1) {`  
            `System.out.println("Objetivo " + target + " encontrado en el índice " + index); // Salida esperada: Objetivo 7 encontrado en el índice 2`  
        `} else {`  
            `System.out.println("Objetivo " + target + " no encontrado en la matriz");`  
        `}`

        `target = 1;`  
        `index = binarySearch(sortedArray, target, 0, sortedArray.length - 1);`  
        `if (index != -1) {`  
            `System.out.println("Objetivo " + target + " encontrado en el índice " + index);`  
        `} else {`  
            `System.out.println("Objetivo " + target + " no encontrado en la matriz"); // Salida esperada: Objetivo 1 no encontrado en la matriz`  
        `}`  
    `}`  
`}`

**Explicación Paso a Paso:**

1. El método binarySearch toma una matriz de enteros ordenada arr, el valor target a buscar y los índices low y high del intervalo de búsqueda actual.  
2. **Caso Base:** Si low se vuelve mayor que high, significa que el intervalo de búsqueda está vacío y el objetivo no está presente en la matriz. El método retorna \-1.  
3. Calcula el índice mid del intervalo actual.  
4. Si el elemento en arr\[mid\] es igual al target, el método ha encontrado el objetivo y retorna mid.  
5. Si el elemento en arr\[mid\] es mayor que el target, significa que el objetivo (si está presente) debe estar en la mitad izquierda del intervalo. El método llama recursivamente a binarySearch con la misma matriz y objetivo, pero con el índice high actualizado a mid \- 1\.  
6. Si el elemento en arr\[mid\] es menor que el target, significa que el objetivo (si está presente) debe estar en la mitad derecha del intervalo. El método llama recursivamente a binarySearch con la misma matriz y objetivo, pero con el índice low actualizado a mid \+ 1\.

**Ejemplos de Ejecución:** (Como se proporciona en los comentarios del código)

**Consideraciones:**  
La recursividad implementa de forma elegante la estrategia de divide y vencerás de la búsqueda binaria dividiendo repetidamente el espacio de búsqueda por la mitad. El problema se descompone en buscar en una submatriz más pequeña. Pasar los índices low y high como parámetros es esencial para definir el subproblema actual que se está considerando en las llamadas recursivas.

### **Función de Ackermann**

**Introducción:** La función de Ackermann es un ejemplo clásico de una función recursiva que destaca por no ser una función recursiva primitiva. Crece extremadamente rápido en valor a medida que aumentan sus argumentos . La función se define de la siguiente manera: A(m, n) \=

* n \+ 1, si m \= 0  
* A(m \- 1, 1), si m \> 0 y n \= 0  
* A(m \- 1, A(m, n \- 1)), si m \> 0 y n \> 0

**Código Java:**  
`public class AckermannFunction {`  
    `public static int ackermann(int m, int n) {`  
        `if (m == 0) {`  
            `return n + 1;`  
        `} else if (m > 0 && n == 0) {`  
            `return ackermann(m - 1, 1);`  
        `} else if (m > 0 && n > 0) {`  
            `return ackermann(m - 1, ackermann(m, n - 1));`  
        `} else {`  
            `// Manejar entrada inválida (no debería ocurrir para m y n no negativos)`  
            `return -1;`  
        `}`  
    `}`

    `public static void main(String args) {`  
        `System.out.println("A(0, 0) = " + ackermann(0, 0)); // Salida esperada: 1`  
        `System.out.println("A(1, 2) = " + ackermann(1, 2)); // Salida esperada: 4`  
        `System.out.println("A(2, 1) = " + ackermann(2, 1)); // Salida esperada: 5`  
        `System.out.println("A(3, 3) = " + ackermann(3, 3)); // Salida esperada: 61 (computacionalmente intensivo)`  
        `// System.out.println("A(4, 0) = " + ackermann(4, 0)); // Tomará mucho tiempo y podría causar desbordamiento de pila`  
    `}`  
`}`

**Explicación Paso a Paso:**

1. El método ackermann toma dos enteros no negativos m y n como entrada.  
2. Implementa la definición de la función de Ackermann utilizando una serie de instrucciones if-else if para verificar las condiciones de cada caso.  
3. **Caso Base 1:** Si m es 0, retorna n \+ 1\.  
4. **Caso Base 2:** Si m es mayor que 0 y n es 0, retorna el resultado de llamar a ackermann con m \- 1 y 1\.  
5. **Caso Recursivo:** Si m es mayor que 0 y n es mayor que 0, retorna el resultado de llamar a ackermann con m \- 1 y el resultado de otra llamada recursiva ackermann(m, n \- 1). Esta recursión anidada es lo que hace que la función crezca tan rápidamente.

**Ejemplos de Ejecución:** (Como se proporciona en los comentarios del código) Tenga en cuenta que para entradas incluso moderadamente grandes (como A(4, 0)), el cálculo puede llevar mucho tiempo y podría provocar un error de desbordamiento de pila debido a la recursión profunda.  
**Consideraciones:**  
La función de Ackermann es un excelente ejemplo de una función que se define fácilmente de forma recursiva pero que crece más rápido que cualquier función recursiva primitiva. La llamada recursiva anidada en el tercer caso conduce a este crecimiento explosivo. Esta función destaca el potencial de las funciones recursivas para tener una complejidad computacional y un uso de pila extremadamente altos, incluso para entradas pequeñas.

### **Ordenamiento de Burbuja (Recursivo)**

**Introducción:** Implemente el algoritmo de ordenamiento de burbuja utilizando la recursividad para ordenar una matriz de enteros en orden ascendente . El ordenamiento de burbuja recorre repetidamente la lista, compara elementos adyacentes y los intercambia si están en el orden incorrecto. El paso a través de la lista se repite hasta que la lista está ordenada.  
**Código Java:**  
`public class RecursiveBubbleSort {`  
    `public static void bubbleSortRecursive(int arr, int n) {`  
        `// Caso base: si solo hay un elemento, ya está ordenado`  
        `if (n == 1) {`  
            `return;`  
        `}`

        `// Una pasada del ordenamiento de burbuja. Después de esta pasada, el elemento más grande`  
        `// se mueve (o burbujea) al final.`  
        `for (int i = 0; i < n - 1; i++) {`  
            `if (arr[i] > arr[i + 1]) {`  
                `// intercambiar arr[i] y arr[i+1]`  
                `int temp = arr[i];`  
                `arr[i] = arr[i + 1];`  
                `arr[i + 1] = temp;`  
            `}`  
        `}`

        `// El elemento más grande está fijo, recurrir para la matriz restante`  
        `bubbleSortRecursive(arr, n - 1);`  
    `}`

    `public static void main(String args) {`  
        `int arr = {64, 34, 25, 12, 22, 11, 90};`  
        `bubbleSortRecursive(arr, arr.length);`  
        `System.out.println("Matriz ordenada:");`  
        `for (int value : arr) {`  
            `System.out.print(value + " "); // Salida esperada: 11 12 22 25 34 64 90`  
        `}`  
        `System.out.println();`  
    `}`  
`}`

**Explicación Paso a Paso:**

1. El método bubbleSortRecursive toma una matriz de enteros arr y el tamaño actual n de la matriz a ordenar como entrada.  
2. **Caso Base:** Si n es 1, significa que solo hay un elemento, por lo que la matriz ya está ordenada y la recursión se detiene.  
3. **Paso Recursivo:**  
   * Realiza una pasada del algoritmo de ordenamiento de burbuja estándar en los primeros n-1 elementos de la matriz. Esta pasada moverá el elemento más grande en esta porción de la matriz a su posición ordenada correcta al final de esta porción.  
   * Después de esta pasada, el elemento más grande se considera ordenado, por lo que el método se llama recursivamente con la matriz y un tamaño reducido de n \- 1 para ordenar los elementos restantes.

**Ejemplos de Ejecución:** (Como se proporciona en los comentarios del código)  
**Consideraciones:**  
Si bien el ordenamiento de burbuja es inherentemente un algoritmo iterativo, se puede implementar de forma recursiva realizando una pasada y luego ordenando recursivamente la parte restante de la matriz. El problema se puede ver como la búsqueda repetida del elemento más grande y su colocación al final. La llamada recursiva reduce el tamaño de la porción no ordenada de la matriz en uno en cada paso.
