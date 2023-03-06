# CountingSortPractice
 
### Ahora toca practicar!!
![Practice](https://user-images.githubusercontent.com/97609743/223197070-5b2a0730-85b3-4c22-a231-2a80ae5da015.png)

### Primero crear nuestra función que ordenará el arreglo dado como entrada

``` java
   public static void sort(int[] arr) {
```

### Luego necesitamos encontrar el valor máximo posible de nuestro arreglo

``` java
    int maxVal = getMaxValue(arr);
```

### Para ello crearemos una función que nos ayude a hacerlo

``` java
    private static int getMaxValue(int[] arr) {
        int maxVal = arr[0];
        for (int i = 1; i < arr.length; i++) {
            if (arr[i] > maxVal) {
                maxVal = arr[i];
            }
        }
        return maxVal;
    }
    
```

### Ahora crearemos dos arreglos de números, uno sera el que cuenta y otro será el que se ordene. Como pueden ver el arreglo que cuenta, su tamaño será uno más que el valoe máximo que se encuentra en el arreglo dado a ordenar.

```java 
    int[] counts = new int[maxVal + 1];
    int[] sortedArr = new int[arr.length];

```

### Ahora crearemos un ciclo for donde llenamos nuestro arreglo que cuenta

``` java
        for (int i = 0; i < arr.length; i++) {
            counts[arr[i]]++;
        }
```

### Luego creamos otro ciclo for que modifica el arreglo de conteo haciendo que cada elemento de cada índice almacene la suma de los recuentos anteriores. El array de conteo modificaado indica la posición de cada objeto en la secuencia de salida.

``` java 
        for (int i = 1; i < counts.length; i++) {
            counts[i] += counts[i - 1];
        }
```
### Después creamos otro ciclo for con el cual vamos a hacer el ordenamiento.

``` java
        for (int i = arr.length - 1; i >= 0; i--) {
            sortedArr[counts[arr[i]] - 1] = arr[i];
            counts[arr[i]]--;
        }
```

### Acto seguidi copiamos el arreglo ordenado con el arreglo dado como entrada.

``` java 
    System.arraycopy(sortedArr, 0, arr, 0, arr.length);
```

### Finalmente creamos el main donde se pondrá el arreglo de entrada, se llame a la función de arreglo y se imprima

```  java
    public static void main(String[] args) {
        int[] arr = {3, 2, 4, 1, 5};
        CountingSort.sort(arr);
        System.out.println(Arrays.toString(arr));
    }
```

## Este debería ser le resultado:

```  java
import java.util.Arrays;

public class CountingSort {
    
    public static void sort(int[] arr) {
        //
        int maxVal = getMaxValue(arr);
        int[] counts = new int[maxVal + 1];
        int[] sortedArr = new int[arr.length];

        for (int i = 0; i < arr.length; i++) {
            counts[arr[i]]++;
        }

        for (int i = 1; i < counts.length; i++) {
            counts[i] += counts[i - 1];
        }

        for (int i = arr.length - 1; i >= 0; i--) {
            sortedArr[counts[arr[i]] - 1] = arr[i];
            counts[arr[i]]--;
        }

        System.arraycopy(sortedArr, 0, arr, 0, arr.length);
    }

    private static int getMaxValue(int[] arr) {
        int maxVal = arr[0];
        for (int i = 1; i < arr.length; i++) {
            if (arr[i] > maxVal) {
                maxVal = arr[i];
            }
        }
        return maxVal;
    }
    public static void main(String[] args) {
        int[] arr = {3, 2, 4, 1, 5};
        CountingSort.sort(arr);
        System.out.println(Arrays.toString(arr));
    }
}
```
## Para hacer un código que en vez de ordenar números ordene caracteres, le dejo el código a continuación:
```java
// Java implementation of Counting Sort

import java.io.*;

class CountingSort {
	void sort(char arr[])
	{
		int n = arr.length;

		// The output character array that will have sorted
		// arr
		char output[] = new char[n];

		// Create a count array to store count of individual
		// characters and initialize count array as 0
		int count[] = new int[256];
		for (int i = 0; i < 256; ++i)
			count[i] = 0;

		// store count of each character
		for (int i = 0; i < n; ++i)
			++count[arr[i]];

		// Change count[i] so that count[i] now contains
		// actual position of this character in output array
		for (int i = 1; i <= 255; ++i)
			count[i] += count[i - 1];

		// Build the output character array
		// To make it stable we are operating in reverse
		// order.
		for (int i = n - 1; i >= 0; i--) {
			output[count[arr[i]] - 1] = arr[i];
			--count[arr[i]];
		}

		// Copy the output array to arr, so that arr now
		// contains sorted characters
		for (int i = 0; i < n; ++i)
			arr[i] = output[i];
	}

	// Driver code
	public static void main(String args[])
	{
		CountingSort ob = new CountingSort();
		char arr[] = { 'g', 'e', 'e', 'k', 's', 'f', 'o',
					'r', 'g', 'e', 'e', 'k', 's' };

		// Function call
		ob.sort(arr);

		System.out.print("Sorted character array is ");
		for (int i = 0; i < arr.length; ++i)
			System.out.print(arr[i]);
	}
}
/*This code is contributed by Rajat Mishra */

```
## Si quieres saber más sobre todo esto te dejo está página web
```link
 https://www.geeksforgeeks.org/counting-sort/
```
##  y este video
```link
 [https://www.geeksforgeeks.org/counting-sort/](https://www.youtube.com/watch?v=7zuGmKfUt7s&ab_channel=GeeksforGeeks)
```
