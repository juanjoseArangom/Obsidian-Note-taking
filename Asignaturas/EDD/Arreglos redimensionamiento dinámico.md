### Características
- Reducen o aumentan su memoria en función de las operaciones de inserción y borrado que se realicen.
- La capacidad del arreglo es >= tamaño del arreglo.

### Operaciones
#### Inserción
Al momento de hacer una inserción, la capacidad del arreglo crece si no hay suficiente espacio para el nuevo elemento. El arreglo crece *x* veces siendo x un factor de crecimiento.
Insertar un elemento al final tiene complejidad O(1) (por análisis amortizado), pero implica O(N) operaciones.
#### Borrado
Si el borrado es al final del arreglo y el tamaño es inferior a 1/x entonces se disminuye su capacidad liberando memoria. Complejidad O(1).
#### Indexación y búsqueda
Misma eficiencia que arreglos normales.
#### Modificación
En arreglos homogéneos es O(1). Para arreglos heterogéneos es O(1) en extremos u O(N) en otro caso.