## Búsqueda binaria
Su funcionamiento se basa en dividir el problema en mitades hasta localizar el elemento deseado o determinar que no está en la lista. El arreglo debe estar previamente ordenado ascendentemente. 
**Complejidad O(log2N)**
## Select-sort
Este algoritmo encuentra el elemento más pequeño de la lista. Intercambia con el primer elemento. Repite el proceso con la sublista restante (ignorando el primer elemento ya ordenado) hasta que toda la lista esté ordenada.
**Complejidad O(N^2)**
## Insert-sort
- Toma un elemento de la lista, empezando por el segundo.
- Compara ese elemento con los anteriores y mueve los mayores hacia la derecha.
- Inserta el elemento en su posición correcta.
- Repite hasta que toda la lista esté ordenada.
**Complejidad O(N^2)**
## Bubble-sort
- Recorre la lista comparando elementos adyacentes.
- Intercambia los elementos si el de la izquierda es mayor que el de la derecha.
- Repite este proceso varias veces, ignorando el último elemento ordenado en cada pasada.
- Finaliza cuando no hay más intercambios, lo que significa que la lista está ordenada.
**Complejidad O(N^2)**
## Merge-sort
- Divide la lista en mitades hasta que cada sublista tenga un solo elemento.
- Fusiona esas sublistas de forma ordenada.
**Complejidad O(NlogN)**