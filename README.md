# CountingSortPractice
 
### Ahora toca practicar!!
![Practice](https://user-images.githubusercontent.com/97609743/223197070-5b2a0730-85b3-4c22-a231-2a80ae5da015.png)

### Primero crear nuestra función que ordenará el arreglo dado como entrada

``` java
   public static void sort(int[] arr) {
```

### Luego necesitamos encontrar el valor máximo posible de nuestro arreglo

``` 
    int maxVal = getMaxValue(arr);
```

### Para ello crearemos una función que nos ayude a hacerlo

``` 
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

``` 
    int[] counts = new int[maxVal + 1];
    int[] sortedArr = new int[arr.length];

```

### Ahora crearemos un ciclo for donde llenamos nuestro arreglo que cuenta

```         
        for (int i = 0; i < arr.length; i++) {
            counts[arr[i]]++;
        }
```

### Luego creamos otro ciclo for que modifica el arreglo de conteo haciendo que cada elemento de cada índice almacene la suma de los recuentos anteriores. El array de conteo modificaado indica la posición de cada objeto en la secuencia de salida.

``` 
        for (int i = 1; i < counts.length; i++) {
            counts[i] += counts[i - 1];
        }
```
### Después creamos otro ciclo for con el cual vamos a hacer el ordenamiento.

``` 
        for (int i = arr.length - 1; i >= 0; i--) {
            sortedArr[counts[arr[i]] - 1] = arr[i];
            counts[arr[i]]--;
        }
```

### Acto seguidi copiamos el arreglo ordenado con el arreglo dado como entrada.

``` 
    System.arraycopy(sortedArr, 0, arr, 0, arr.length);
```

### Finalmente creamos el main donde se pondrá el arreglo de entrada, se llame a la función de arreglo y se imprima

``` 
    public static void main(String[] args) {
        int[] arr = {3, 2, 4, 1, 5};
        CountingSort.sort(arr);
        System.out.println(Arrays.toString(arr));
    }
```

## Este debería ser le resultado:

``` import java.util.Arrays;

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
