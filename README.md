Metodos de Ordenamiento Simple
================

Los metodos de ordenamiento iterativo son aquellos que se realizan de
forma que el codigo deba de repetirse una y otra vez hasta comprobar que
ha sido ordenado por completo.

### 1 - Metodo de Ordenamiento de la Burbuja (BubbleSort)

El Ordenamiento de burbuja (BubbleSort) es un algoritmo de ordenamiento
simple. El mismo funciona revisando cada elemento de la lista a ordenar
con el que le sigue, cambiándolos de posición si están en un orden
incorrecto (n\>n+1). Es necesario repetir este proceso varias veces
hasta que no se necesiten más cambios, lo que significa que la lista
quedó ordenada. Un ejemplo de ordenamiento con bubblesort sería:

![](./images/bubble-sort.gif)

Su código en Python 3 sería el siguiente:

``` python
from random import sample 
# Importamos un metodo de la biblioteca random para generar listas aleatorias

lista = list(range(100)) # Creamos la lista base con números del 1 al 100

# Creamos una lista aleatoria con sample 
#(8 elementos aleatorios de la lista base)
vectorbs = sample(lista,5) 


def bubblesort(vectorbs):
    """Esta función ordenara el vector que le pases como argumento con el metodo de Bubble Sort"""
    
    # Imprimimos la lista obtenida al principio (Desordenada)
    print("El vector a ordenar es:",vectorbs)
    n = 0 # Establecemos un contador del largo del vector
    
    for _ in vectorbs:
        n += 1 #Contamos la cantidad de caracteres dentro del vector
    
    for i in range(n-1): 
    # Le damos un rango n para que complete el proceso. 
        for j in range(0, n-i-1): 
            # Revisa la matriz de 0 hasta n-i-1
            if vectorbs[j] > vectorbs[j+1] :
                vectorbs[j], vectorbs[j+1] = vectorbs[j+1], vectorbs[j]
            # Se intercambian si el elemento encontrado es mayor 
            # Luego pasa al siguiente
    print ("El vector ordenado es: ",vectorbs)

bubblesort(vectorbs)
```

    ## ('El vector a ordenar es:', [39, 55, 50, 31, 49])
    ## ('El vector ordenado es: ', [31, 39, 49, 50, 55])

### 2 - Metodo de Ordenamiento de Selección (SelectionSort)

El metodo de ordenamiento por selección consiste en buscar el menor
entre todos los elementos no ordenados y colocarlo al principio, luego
se debe repetir lo mismo con los restantes (no se tienen en cuenta los
ya ordenados). Aquí una muestra más visual del metodo:

![](./images/selection-sort-animation.gif)

Y su código en Python 3 sería el siguiente:

``` python

from random import sample 
# Importamos un metodo de la biblioteca random para generar listas aleatorias

lista = list(range(100)) # Creamos la lista base con números del 1 al 100

# Creamos una lista aleatoria con sample 
#(8 elementos aleatorios de la lista base)
vectorselect = sample(lista,10) 


def selectionsort(vectorselect):
    """Esta función ordenara el vector que le pases como argumento con el metodo Selection Sort"""
    # Imprimimos la lista obtenida al principio (Desordenada)
    print ("El vector a ordenar es:",vectorselect)
    
    largo = 0
    
    for _ in vectorselect:
        largo += 1 # Obtenemos el largo del vector
        
    for i in range(largo): 
      
        # Encontrar el minimo elemento de los restantes sin ordenar
        minimo = i 
        for j in range(i+1, largo): 
            if vectorselect[minimo] > vectorselect[j]: 
                minimo = j 
                
        # Cambiamos el elemento minimo encontrado con el primer elemento de la matriz
        vectorselect[i], vectorselect[minimo] = vectorselect[minimo], vectorselect[i]
        # Repetimos el proceso hasta terminar
    print("El vector ordenado es: ",vectorselect)

selectionsort(vectorselect)
```

    ## ('El vector a ordenar es:', [3, 54, 91, 77, 32, 74, 36, 53, 48, 88])
    ## ('El vector ordenado es: ', [3, 32, 36, 48, 53, 54, 74, 77, 88, 91])

### 3 - Metodo de Ordenamiento de Inserción (InsertionSort)

El método de ordenamiento de inserción actua recorriendo la lista a
ordenar, tomando el elemento actual e insertándolo donde debería
comparandoló entre los que ya ha recorrido. Esta es una muestra mas
clara del metodo de ordenamiento por Inserción:

![](./images/insertion-sort-example.gif)

Y el código en Python 3 quedaría de la siguiente forma:

``` python
from random import sample 
# Importamos un metodo de la biblioteca random para generar listas aleatorias

lista = list(range(100)) # Creamos la lista base con números del 1 al 100

# Creamos una lista aleatoria con sample 
#(8 elementos aleatorios de la lista base)
vectorins = sample(lista,8)

def insertionsort(vectorins): 
    """Esta función ordenara el vector que le pases como argumento con
    el metodo Insertion Sort"""
    
    # Imprimimos la lista obtenida al principio (Desordenada)
    print("El vector a ordenar es:", vectorins)
    
    largo = 0 # Establecemos un contador del largo
     
    for i in vectorins:
        largo += 1 # Obtenemos el largo del vector
    
    # Recorremos la lista de 1 hasta el largo del vector
    for i in range(1, largo): 
    
        elemento = vectorins[i] 
  
        # Movemos los elementos de vectorins[0...i-1], que son mayores que el elemento
        # a una posición adelante de su posición actual
        j = i-1
        while j >= 0 and elemento < vectorins[j] : 
                vectorins[j+1] = vectorins[j] 
                j -= 1
        vectorins[j+1] = elemento 
    print("El vector ordenado es: ", vectorins)

insertionsort(vectorins)
```

    ## ('El vector a ordenar es:', [54, 74, 53, 92, 11, 8, 56, 16])
    ## ('El vector ordenado es: ', [8, 11, 16, 53, 54, 56, 74, 92])

### 4 - Metodo de Ordenamiento Shell

El metodo de ordenamiento Shell es una mejora del metodo de Ordenamiento
por inserción ya que el metodo de inserción es eficiente si la lista
está **casi ordenada**, para ello el metodo Shell compara elementos
separados por un espacio de varias posiciones, esto permite que un
elemento haga “pasos más grandes” hacia su posición esperada, el mismo
finaliza con un Ordenamiento por inserción simple. Aquí un ejemplo más
grafico del ordenamiento Shell:

![](./images/Sorting_shellsort.gif)

Y su codigo en Python 3 sería el siguiente:

``` python
from random import sample 
# Importamos un metodo de la biblioteca random para generar listas aleatorias

lista = list(range(100)) # Creamos la lista base con números del 1 al 100

# Creamos una lista aleatoria con sample 
#(8 elementos aleatorios de la lista base)
vectorshell = sample(lista,8)

def shellsort(vectorshell):
    
    """Esta función ordenara el vector que le pases como argumento 
    con el metodo Shell Sort"""
    
    print("El vector a ordenar con shell es:", vectorshell)
    
    largo = 0
    
    for i in vectorshell:
        largo += 1
    
    distancia = largo // 2
    
     # Creamos un bucle según las distancias
    while distancia > 0:
        # Utilizamos el Insertionsort
        for i in range(distancia, largo):
            val = vectorshell[i]
            j = i
            while j >= distancia and vectorshell[j - distancia] > val:
                vectorshell[j] = vectorshell[j - distancia]
                j -= distancia
            vectorshell[j] = val
        distancia //= 2 # Acotamos la distancia nuevamente y continua el ciclo
    print("El vector ordenado con shell es: ", vectorshell)
    
shellsort(vectorshell)
    
```

    ## ('El vector a ordenar con shell es:', [50, 94, 29, 91, 3, 59, 69, 60])
    ## ('El vector ordenado con shell es: ', [3, 29, 50, 59, 60, 69, 91, 94])

### 5 - Metodo de Ordenamiento por mezcla (MergeSort)

El metodo de ordenamiento por mezcla tiene un funcionamiento muy
particular, primero debemos saber que si la longitud de la lista es 0 ó
1 ya está ordenada, En otro caso: el algoritmo deberá dividir la lista
desordenada en dos sublistas de aproximadamente la mitad del tamaño,
luego ordenará cada sublista recursivamente aplicando el ordenamiento
por mezcla y por ultimo mezcla las dos sublistas en una sola lista
ordenada. Esta es una demostración gráfica del mismo:

![](./images/Merge-sort.gif)

Y su código en Python 3 sería el siguiente:

``` python
from random import sample 
# Importamos un metodo de la biblioteca random para generar listas aleatorias

lista = list(range(100)) # Creamos la lista base con números del 1 al 100

# Creamos una lista aleatoria con sample 
#(8 elementos aleatorios de la lista base)
vectormerge = sample(lista,8)

def mergesort(vectormerge): 
    """Esta función ordenara el vector que le pases como argumento 
    con el metodo Merge Sort"""
    
    # Imprimimos la lista obtenida al principio (Desordenada)
    print("El vector a ordenar con merge es:", vectormerge)
    
    def merge(vectormerge):
    
        def largo(vec):
                largovec = 0 # Establecemos un contador del largovec
                for _ in vec:
                    largovec += 1 # Obtenemos el largo del vector
                return largovec
        
        
        if largo(vectormerge) >1: 
            medio = largo(vectormerge)//2 # Buscamos el medio del vector
            
            # Lo dividimos en 2 partes 
            izq = vectormerge[:medio]  
            der = vectormerge[medio:]
            
            merge(izq) # Mismo procedimiento a la primer mitad
            merge(der) # Mismo procedimiento a la segunda mitad
            
            i = j = k = 0
            
            # Copiamos los datos a los vectores temporales izq[] y der[] 
            while i < largo(izq) and j < largo(der): 
                if izq[i] < der[j]: 
                    vectormerge[k] = izq[i] 
                    i+= 1
                else: 
                    vectormerge[k] = der[j] 
                    j+= 1
                k += 1
            
            # Nos fijamos si quedaron elementos en la lista
            # tanto derecha como izquierda 
            while i < largo(izq): 
                vectormerge[k] = izq[i] 
                i+= 1
                k+= 1
            
            while j < largo(der): 
                vectormerge[k] = der[j] 
                j+= 1
                k+= 1
    merge(vectormerge)
    print("El vector ordenado con merge es: ", vectormerge)
mergesort(vectormerge)
```

    ## ('El vector a ordenar con merge es:', [14, 53, 1, 36, 23, 43, 77, 81])
    ## ('El vector ordenado con merge es: ', [1, 14, 23, 36, 43, 53, 77, 81])

### 6 - Metodo de ordenamiento rápido (QuickSort)

Al igual que el ordenamiento por mezcla, el ordenamiento rápido es un
algoritmo *divide y ganarás*, el mismo funciona seleccionando un
elemento como pivot y dividiendo la matriz dada alrededor del pivot
elegido. Hay muchas versiones diferentes de ordenamiento rápido que
eligen pivotar de diferentes maneras.

1.  Elegir siempre el primer elemento como pivot.
2.  Elegir siempre el último elemento como pivot.
3.  Elegir un elemento aleatorio como pivot.
4.  Elegir la mitad como pivot.

El proceso llevado a cabo en el ordenamiento rápido es la partición, el
objetivo de las mismas es, dado una matriz A y un elemento x de la
matriz como pivot, poner x en su posición correcta en la matriz ordenada
y poner todos los elementos menores que x antes de x, y poner todos los
elementos mayores que x después de x. Aquí hay una demostración grafica
del proceso llevado a cabo:

![](./images/Sorting_quicksort.gif)

Y su código en Python 3 sería el siguiente:

``` python
from random import sample 
# Importamos un metodo de la biblioteca random para generar listas aleatorias

lista = list(range(100)) # Creamos la lista base con números del 1 al 100

# Creamos una lista aleatoria con sample 
#(8 elementos aleatorios de la lista base)
vectorquick = sample(lista,8)
def quicksort(vectorquick, start = 0, end = len(vectorquick) - 1 ):
    """Esta función ordenara el vector que le pases como argumento 
    con el metodo Quick Sort"""
    
    # Imprimimos la lista obtenida al principio (Desordenada)
    print("El vector a ordenar con quick es:", vectorquick)
    
    def quick(vectorquick, start = 0, end = len(vectorquick) - 1):
        
        
        if start >= end:
            return

        def particion(vectorquick, start = 0, end = len(vectorquick) - 1):
            pivot = vectorquick[start]
            menor = start + 1
            mayor = end

            while True:
                # Si el valor actual es mayor que el pivot
                # está en el lugar correcto (lado derecho del pivot) y podemos 
                # movernos hacia la izquierda, al siguiente elemento.
                # También debemos asegurarnos de no haber superado el puntero bajo, ya que indica 
                # que ya hemos movido todos los elementos a su lado correcto del pivot
                while menor <= mayor and vectorquick[mayor] >= pivot:
                    mayor = mayor - 1

                # Proceso opuesto al anterior            
                while menor <= mayor and vectorquick[menor] <= pivot:
                    menor = menor + 1

                # Encontramos un valor sea mayor o menor y que este fuera del arreglo
                # ó menor es más grande que mayor, en cuyo caso salimos del ciclo
                if menor <= mayor:
                    vectorquick[menor], vectorquick[mayor] = vectorquick[mayor], vectorquick[menor]
                    # Continua el bucle
                else:
                    # Salimos del bucle
                    break

            vectorquick[start], vectorquick[mayor] = vectorquick[mayor], vectorquick[start]
            
            return mayor
        
        p = particion(vectorquick, start, end)
        quick(vectorquick, start, p-1)
        quick(vectorquick, p+1, end)
        
    quick(vectorquick)
    print("El vector ordenado con quick es:", vectorquick)

quicksort(vectorquick)
```

    ## ('El vector a ordenar con quick es:', [48, 21, 35, 85, 91, 46, 68, 62])
    ## ('El vector ordenado con quick es:', [21, 35, 46, 48, 62, 68, 85, 91])

### 7 - Metodo de ordenamiento del montón (HeapSort)

El metodo de Ordenamiento del montón es similar a la clasificación por
selección donde primero encontramos el elemento máximo y lo colocamos al
final. Repetimos el mismo proceso para el resto de elementos. Pero en el
metodo del montón debemos realizar previamente montones que son los que
irán acomodandose con el algoritmo según cual es más grande de un lado o
del otro del montón y al mismo tiempo, se irán eliminando y acomodando
los elementos mayores en la lista. Aquí hay un ejemplo gráfico del
proceso:

![](./images/heapsort.gif)

Y su código en Python 3 sería el siguiente:

``` python
from random import sample 
# Importamos un metodo de la biblioteca random para generar listas aleatorias

lista = list(range(100)) # Creamos la lista base con números del 1 al 100

# Creamos una lista aleatoria con sample 
#(8 elementos aleatorios de la lista base)
vectorheap = sample(lista,8)

def heapsort(vectorheap):
    """Esta función ordenara el vector que le pases como argumento 
    con el metodo Heap Sort"""
    
    # Imprimimos la lista obtenida al principio (Desordenada)
    print("El vector a ordenar con heap es:", vectorheap)

    largo = 0 # Establecemos un contador del largo
        
    for _ in vectorheap:
        largo += 1 # Obtenemos el largo del vector

    # Para amontonar la subparte a partir de i. 
    # n es el tamaño del montón.
    def amontonar(vectorheap, n, i): 
        mas_largo = i # Tomamos i como el más grande 
        izq = 2 * i + 1      
        der = 2 * i + 2    
    
        
        if izq < n and vectorheap[i] < vectorheap[izq]: 
            mas_largo = izq 
    
        # Ver si existe la subparte de i correctamente y 
        # si es mayor que i
        if der < n and vectorheap[mas_largo] < vectorheap[der]: 
            mas_largo = der 
            
    
        if mas_largo != i: 
            vectorheap[i],vectorheap[mas_largo] = vectorheap[mas_largo],vectorheap[i] # swap 
            # Cambiar el origen, si es necesario
            # amontonar el origen. 
            amontonar(vectorheap, n, mas_largo)
            
    def heap(vectorheap):
        
        n = largo
        # Crear un montón maximo 
        for i in range(n//2 - 1, -1, -1): 
            amontonar(vectorheap, n, i) 
    
        # Extraer elementos uno a uno
        for i in range(n-1, 0, -1): 
            vectorheap[i], vectorheap[0] = vectorheap[0], vectorheap[i] 
            # Intercambio 
            amontonar(vectorheap, i, 0)
        
    heap(vectorheap)
    print("El vector ordenado con heap es:", vectorheap)

heapsort(vectorheap)
```

    ## ('El vector a ordenar con heap es:', [29, 14, 9, 58, 22, 59, 69, 43])
    ## ('El vector ordenado con heap es:', [9, 14, 22, 29, 43, 58, 59, 69])

### 8 - Metodo de Ordenamiento del peine (CombSort)

El metodo de ordenamiento del peine es una mejora del metodo de
ordenamiento de la burbuja, ya que en el metodo de la burbuja siempre se
comparan valores consecutivos, entonces todos los cambios se realizan
uno por uno. El metodo del peine (CombSort) mejora al BubbleSort usando
un espacio de tamaño superior a 1. El espacio comienza con un valor
grande y se reduce en un factor x en cada iteración hasta que alcanza el
valor 1. Por lo tanto este elimina más de una inversión con un
intercambio y funciona mejor que el metodo de la burbuja. Aquí hay una
demostración gráfica del proceso de ordenamiento:

![](./images/Comb_sort.gif)

Y su código en Python 3 sería el siguiente:

### Metodo de Ordenamiento de la burbuja Bidireccional (CocktailSort)

El metodo de ordenamiento CocktailSort es una reforma del metodo de
ordenamiento de la burbuja, con la diferencia que en este el
ordenamiento se realiza en ambas direcciones, comprobando que el primero
sin ordenar sea el menor y el ultimo sin ordenar sea el mayor y
acomodando así en su respectivo lugar cada uno de los elementos. Aquí
hay un ejemplo gráfico del metodo de ordenamiento:

![](./images/cocktailsort.gif)

Y su código en Python 3 sería el siguiente:

## Comparación de distintos metodos de ordenamiento

### Comparación según la cantidad de tiempo de demora

La grafica demuestra cuanto tardan (en segundos) distintos tipos de
ordenamiento al variar la cantidad de elementos que contiene la lista a
ordenar. Siendo las maquinas a comparar:

M1 = Máquina 1 (1 nucleo, 1GB de RAM) M2 = Máquina 2 (2 nucleos, 2GB de
RAM)

Tenemos el siguiente grafico:

![](./images/allAlgorithms_M1_M2.png)

### Comparación según la cantidad de iteraciones e intercambios del algoritmo

Otra forma de comparar los algoritmos de ordenamiento es analizandolos
según la cantidad de comparaciones e intercambios que deben realizar
para cumplir su cometido, hemos analizado algunos de ellos con la
[calculadora](http://lwh.free.fr/pages/algo/tri/tri_es.htm)
correspondiente y encontrado de esta forma, los datos para realizar la
siguiente tabla y gráfico:

![](./images/MetodosdeOrdenamiento.png)

#### Autor

Geremias Baudino

[Linkedin](https://www.linkedin.com/in/geremiasbaudino/)

[Kaggle](https://www.kaggle.com/geremiasbaudino)

[Github](https://github.com/GBaudino)

#### Fuentes

[Analisis de Algoritmos de
Ordenamiento](https://pereiratechtalks.com/analisis-de-algoritmos-de-ordenamiento/)

[Algoritmos de Ordenamiento
GeeksforGeeks](https://www.geeksforgeeks.org/sorting-algorithms/)
