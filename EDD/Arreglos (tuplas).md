## Arreglos homogéneos
### Características
- Los elementos almacenados son del mismo tipo.
- Se guardan en posiciones consecutivas de memoria.
- Sus elementos se pueden acceder mediante un índice.

### Operaciones
#### Indexación
Acceder a un elemento del cuál se conoce su índice. Tiene complejidad O(1).
#### Modificación
Actualizar un elemento almacenado en cierto índice. Tiene complejidad O(1).
#### Búsqueda
Determinar si un elemento se encuentra dentro del arreglo. Tiene complejidad O(N).


## Arreglos heterogéneos
### Operaciones
#### Indexación
O(1) obteniendo la dirección del elemento y luego O(1) obteniendo el elemento como tal.
#### Modificación y búsqueda
La modificación no es posible en python y la búsqueda es O(N) como en los arreglos homogéneos.

## Inserción
Para esta operación pueden ocurrir dos cosas: que la memoria esté desocupada o que esté ocupada.
El primer caso es el favorable ya que solo requiere reservar ese espacio de memoria y guardar el elemento con una eficiencia de O(1).
El segundo caso requiere buscar un nuevo espacio de memoria suficiente, reservarlo y "mudar" los elementos que ya estaban y agregar el nuevo. Tiene complejidad O(N).

Si el elemento no se quiere agregar al final sino en un índice i sería necesario mudar N/2 a la izquierda o derecha, es decir, complejidad O(N).

## Borrado
#### Si se borra el primer o último elemento
Si se borra el último elemento cambia el tamaño del arreglo, liberando memoria. Complejidad O(1).
Si se borra el primer elemento cambia el tamaño y la dirección del arreglo. Complejidad O(1).
#### Si se borra un elemento distinto al primero o al último
Además de modificar el tamaño, hay que mover los elementos a la izquierda o derecha dependiendo de la eficiencia. Complejidad O(N).
#### Si se borra un elemento del que no se conoce su índice
Debemos encontrar primero el índice (O(N)).
