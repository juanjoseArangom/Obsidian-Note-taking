#### Características
- El elemento superior se llama **raíz**.
- Todo nodo tiene máximo dos hijos.
- Su descendencia es un menor a la izquierda y uno mayor a la derecha. Estrictamente mayor o menor. Debe cumplir la regla con la raíz.
- No hay elementos repetidos.
- La altura mínima del árbol con N elementos es piso(log2(N)) + 1 y la máxima N.

## Inserción de elementos
Se debe garantizar la regla de mantener el orden.
*Complejidad O(N)*.
La forma final del árbol puede variar y no depende de los elementos que contiene sino del orden de las operaciones de inserción y borrado.

## Indexación y búsqueda
No existe el concepto de índice y solo a la raíz se le puede hacer indexación con O(1).
La búsqueda solamente retorna True o False
*Complejidad O(N)*

## Borrado
Se deben considerar cuatro casos:
###### El elemento no está en el árbol:
La búsqueda retorna False y no se puede borrar. **O(N)**
###### Nodo hoja (no tiene hijos):
Se realiza búsqueda, se libera la memoria y su padre deja de tener hijo, la dirección de memoria a la que apunta su padre pasa a ser = NULL. **O(N)**
###### Nodo con hijo único:
Se realiza la búsqueda, se libera la memoria y el nodo abuelo pasa a apuntar al que era su nieto y lo convierte en su hijo.
###### Nodo con dos hijos:
![[Pasted image 20250115131218.png]]O(N)

## Recorrido
Recorrer un árbol es pasar por cada uno de los elementos del árbol.