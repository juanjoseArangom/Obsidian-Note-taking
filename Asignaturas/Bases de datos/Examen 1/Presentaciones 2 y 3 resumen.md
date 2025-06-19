# Resumen de Presentaciones sobre Sistemas de Bases de Datos

## Presentación 1: Introducción a los Sistemas de Bases de Datos (BDs)

Esta presentación introduce los conceptos fundamentales de los sistemas de bases de datos, su historia, componentes y ventajas sobre los sistemas de archivos tradicionales.

### 1. Historia de las Bases de Datos (BDs)
* **Sistemas de archivos:** Surgieron por la necesidad de almacenar datos para su reutilización (persistencia). [cite: 2]
    * **Desventajas:**
        * Redundancia de datos. [cite: 2]
        * Dificultad de integración debido a diferentes formatos y estructuras. [cite: 2]
        * Alto costo para la propagación de cambios y para modificar la estructura de un archivo. [cite: 2]
        * Riesgo de inconsistencias por actualizaciones simultáneas. [cite: 2]
        * Muchas aplicaciones usaban sus propios archivos, complicando la generación de informes que requerían datos de diferentes fuentes. [cite: 2]
    * Un diseño físico de archivos podía beneficiar ciertas aplicaciones pero ser desventajoso para otras. [cite: 7]
    * La dificultad para combinar archivos promovía la redundancia de datos (ejemplo visualizado con archivos de Clientes y Ventas). [cite: 8]
* **Sistemas de BD:** Nacieron para solucionar los problemas de los sistemas de archivos. [cite: 9]
    * **Capacidades Clave:**
        * Manejo de persistencia. [cite: 9]
        * Soporte para al menos un modelo de datos. [cite: 9]
        * Soporte de un lenguaje de alto nivel (como SQL) para manipulación y definición eficiente de datos. [cite: 9]
        * Definición de usuarios, roles, permisos (Control de acceso y Seguridad). [cite: 9]
        * Evitar inconsistencias al compartir datos. [cite: 9]

### 2. Definiciones Fundamentales
* **Base de Datos (BD):** Conjunto de datos (con su esquema) almacenados en un medio (ej. disco) y usados con diversos propósitos por múltiples usuarios. [cite: 13]
* **Esquema de la BD:** Describe la estructura de los datos requeridos por la organización; suele ser estático por largos períodos. [cite: 13, 14]
* **Instancia de la BD:** Los datos que la BD posee en un instante determinado; suelen cambiar constantemente (adiciones, borrados, actualizaciones), excepto en BDs como los Data Warehouse. [cite: 15]

### 3. Tipos de Usuarios de BD
* **Usuario final:** Interactúa con la BD, usualmente a través de aplicaciones e interfaces. [cite: 16]
* **Usuario especialista:** Diseña y programa aplicaciones para los usuarios finales. [cite: 16]
* **DBA (DataBase Administrator):** Administra la BD. [cite: 16]

### 4. Sistema de Gestión de Bases de Datos (SGBD o DBMS)
* **Definición:** Sistema computarizado que permite la gestión de las BDs. Es un conjunto de programas que sirve de interfaz entre usuarios, datos y programas de la BD, interactuando con el sistema operativo. [cite: 18]
* **Ejemplos:** Oracle, SQL Server, DB2, PostgreSQL. [cite: 18]
* **Soporte de Lenguajes:**
    * **DDL (Data Definition Language):** Para la creación del esquema. [cite: 20]
    * **DML (Data Manipulation Language):** Para inserción, actualización, borrado y consulta de datos. [cite: 20]
    * **DCL (Data Control Language):** Para la gestión de usuarios, roles, permisos, etc. [cite: 20]
    * SQL incluye estos tres sub-lenguajes. [cite: 21]
* **Servicios Adicionales:**
    * **Gestión de transacciones:** Una transacción es una unidad de trabajo (consultas, actualizaciones, etc.). [cite: 22]
    * **Recuperación ante fallas y rollback de transacciones:** Usa una bitácora (log de transacciones). [cite: 22]
    * **Manejo de respaldos (backups).** [cite: 22]
    * **Independencia de los datos.** [cite: 22]
* **Propiedades ACID para Transacciones:** Un SGBD debe garantizar:
    * **A**tomicidad (Atomicity). [cite: 23]
    * **C**onsistencia (Consistency). [cite: 23]
    * **I**solamiento (Isolation). [cite: 23]
    * **D**urabilidad (Durability). [cite: 23]
    * Una BD debe estar en estado consistente antes y después de una transacción (commit o rollback), aunque pueda estar inconsistente durante su ejecución. [cite: 24]
* **Manejo de Concurrencia:**
    * **Bloqueos:** Compartido (S) y Exclusivo (X) para controlar el acceso concurrente. Se presenta una matriz de compatibilidad de bloqueos. [cite: 25] Los bloqueos se liberan al finalizar la transacción. [cite: 25]
    * Se plantea un ejemplo para analizar el efecto de transacciones concurrentes con commit y rollback. [cite: 26, 27]

### 5. Componentes y Arquitectura de un SGBD
* **Diagrama de Arquitectura:** Muestra cómo las consultas y programas de usuario interactúan con compiladores DDL, DML y DCL, el optimizador, manejador de transacciones y de almacenamiento, utilizando un Diccionario de Datos para acceder a la BD física. [cite: 28]
* **Diccionario de Datos (DD):**
    * Contiene metadatos: datos sobre el esquema de la BD, usuarios, permisos, etc. [cite: 29]
    * Permite la traducción entre los tres niveles de la arquitectura ANSI-SPARC. [cite: 29]
    * Es un catálogo autodescriptivo (datos sobre los datos). [cite: 30]
* **Optimizador de Consultas:** Define el plan de ejecución eficiente para las operaciones solicitadas. [cite: 31]
* **Manejador de Transacciones:** Controla el acceso y la concurrencia de operaciones. [cite: 32]
* **Manejador de Almacenamiento:**
    * **Manejador de Archivos:** Recupera bloques de datos desde el disco. [cite: 33]
    * **Manejador de Buffer:** Mantiene datos usados frecuentemente en memoria principal y decide cuándo escribir bloques a disco. [cite: 34]

### 6. Ventajas de un SGBD
* Reúso de datos y programas. [cite: 36]
* Control de redundancia. [cite: 36]
* Estandarización (ej. en el acceso a datos). [cite: 36]
* Concurrencia. [cite: 37]
* Posibilidad de equilibrar cargas y establecer prioridades. [cite: 37]
* Integridad (cumplimiento de reglas establecidas). [cite: 38]
* Seguridad. [cite: 38]
* Rapidez de desarrollo. [cite: 38]
* Mantenimiento y reingeniería: cambios en el esquema sin cambiar (idealmente) los programas. [cite: 38]

### 7. Desventajas de un SGBD
* Tamaño. [cite: 39]
* Susceptibilidad a fallas (discutible). [cite: 39]
* Complejidad en la recuperación a fallas (discutible). [cite: 39]
* Lentitud debido a la cantidad de verificaciones que debe hacer (ej. permisos, tipos de datos). [cite: 39, 40]

### 8. Bases de Datos Especializadas
* BDs de documentos (JSON, XML), BDs de grafos. [cite: 41]
* BDs para la toma de decisiones (Data Warehouse). [cite: 41]
* BDs distribuidas, paralelas, blockchain. [cite: 42]
* BDs deductivas, temporales, multimediales (imágenes, audio, videos). [cite: 42]
* BDs geográficas (Sistemas de Información Geográficos - SIG, trayectorias). [cite: 43]
* BDs vectoriales. [cite: 43]
* Un ejemplo práctico es una aplicación de taxis que detecta la posición del usuario y asigna el taxi más cercano. [cite: 12]

---

## Presentación 2: Introducción a los Sistemas de Bases de Datos (2) - Niveles de Abstracción y Modelos de Datos

Esta presentación profundiza en la arquitectura de los sistemas de bases de datos, los niveles de abstracción y los diferentes tipos de modelos de datos.

### 1. Niveles de Abstracción de una BD
* La percepción de una BD varía según el tipo de usuario (final, especialista o administrador). [cite: 45]
* **Arquitectura ANSI/SPARC:** Es la base para la independencia de datos. [cite: 45] Propone tres niveles:
    * **Nivel de Visión o Externo:** Vistas parciales de la BD para usuarios finales (ej. Inventario, Ventas, Contabilidad). [cite: 46, 47]
        * Es el más cercano a los usuarios finales. [cite: 47]
        * Cada visión puede ser un subesquema y ofrecer una representación particular de los datos (ej. formatos de fecha diferentes para Secretaria y Contador). [cite: 47, 48]
        * Puede incluir datos agregados (ej. totales por Dpto), derivados (ej. sueldo total = básico + comisión) o calculados (ej. edad a partir de fecha de nacimiento), que usualmente no están almacenados explícitamente. [cite: 49, 51, 52]
    * **Nivel Conceptual/Lógico:** Vista global de la BD, describe la estructura semántica de todos los datos y sus relaciones, así como las restricciones, de forma independiente del almacenamiento físico. [cite: 46, 53, 54]
        * Interesante para el usuario especialista. [cite: 53]
        * Soporta cada visión externa. [cite: 53]
        * El nivel lógico es un refinamiento con más detalles que el modelo conceptual. [cite: 54]
    * **Nivel Físico o Interno:** Describe cómo se almacenan los datos en la máquina (estructuras de datos, tipos de datos, índices, compresión, encriptación). [cite: 46, 55, 56]
        * Interesa al administrador y al especialista. [cite: 55]
* Existen correspondencias (mappings) entre los niveles (externo/conceptual y conceptual/interno) para que el SGBD pueda relacionar los elementos entre ellos. [cite: 69, 70]

### 2. Independencia de los Datos
* Uno de los principales objetivos de la arquitectura ANSI/SPARC. [cite: 57]
* Permite modificar la definición de un nivel sin afectar (en lo posible) el nivel inmediatamente superior, reduciendo el esfuerzo de adaptar aplicaciones a cambios en el esquema. [cite: 57]
* **Tipos de Independencia:**
    * **Independencia Física:**
        * Se da entre el nivel conceptual y el físico. [cite: 59]
        * Cambios en el esquema físico (ej. cambiar tipo de índice de B+ a hash para mejorar rendimiento) no deben afectar el esquema conceptual. [cite: 59, 60, 61]
        * Proporciona inmunidad del esquema conceptual a cambios en el físico. [cite: 61]
    * **Independencia Lógica:**
        * Se da entre el nivel de visión y el conceptual. [cite: 63]
        * Cambios en el nivel conceptual no deberían implicar cambios en el nivel de visión. [cite: 63]
        * Es más difícil de lograr, ya que las vistas dependen del esquema conceptual. [cite: 63, 64]
        * Ejemplos de cambios conceptuales: Adición de atributos (si es obligatorio, puede afectar subesquemas externos) o eliminación de elementos. [cite: 65, 66]

### 3. Concepto de Modelo de Datos
* La realidad es compleja; un modelo capta los aspectos de interés para una organización. [cite: 72]
* Es una herramienta para comunicar y plasmar la representación de un fenómeno del mundo real, ayudando a su comprensión. [cite: 72]
* Diferentes observadores pueden tener percepciones distintas. [cite: 72]

### 4. Modelo Conceptual
* **Definición:** Descripción de alto nivel de la estructura de la BD, independiente del SGBD a usar. [cite: 73]
* Se diseña a partir de la especificación de requisitos. [cite: 73]
* Su propósito es describir la estructura de los datos y sus relaciones, no las estructuras de almacenamiento. [cite: 74]
* **Características Deseables:**
    * Expresividad: Representar variedad de restricciones. [cite: 75]
    * Simplicidad: Fácil de comprender por usuarios. [cite: 75]
    * Minimalidad: Un concepto no se expresa con otros. [cite: 75]
    * Formalidad: Conceptos con interpretación única y precisa. [cite: 75]
* **Modelos Conceptuales Comunes:**
    * Entidad-Relación (E-R): El más usado y base del curso. [cite: 76]
    * Semántico. [cite: 76]
    * Diagrama de clases de UML. [cite: 76]

### 5. Modelo Lógico
* **Definición:** Descripción de la estructura de la BD que puede ser procesada por un SGBD. [cite: 77]
* Se diseña a partir de un modelo conceptual, siendo más detallado. [cite: 77]
* **Modelos Lógicos Comunes:**
    * Relacional: El más usado y base del curso. [cite: 78]
    * Objeto-Relacional. [cite: 78]
    * Objetual puro. [cite: 78]
    * Anteriores (primitivos): Red, Jerárquico (con similitudes a la organización de documentos XML). [cite: 78]
* La elección depende de la clase de modelo soportado por el *tipo* de SGBD, no de un SGBD específico. [cite: 79]
* Se sitúa entre el modelo conceptual y el físico, aunque en algunos SGBD la especificación del modelo lógico puede fusionarse con elementos del físico. [cite: 79, 80]

### 6. Modelo Físico
* **Definición:** Descripción de la implantación de una BD en disco. [cite: 81]
* Describe las estructuras de almacenamiento y las técnicas para acceder a los datos. [cite: 81]
* Su diseño depende de un SGBD específico (ej. Oracle, MySQL). [cite: 81]

### 7. Relación entre Modelos
* El proceso de diseño generalmente sigue esta secuencia:
    1.  **Requisitos** ->
    2.  **Modelo Conceptual** (E-R, Clases, Semántico) - Independiente del SGBD. [cite: 82] ->
    3.  **Modelo Lógico** (Relacional, Objetual, etc.) - Dependiente del *tipo* de SGBD. [cite: 82] ->
    4.  **Modelo Físico** - Dependiente del SGBD específico (Oracle, MySQL, SQL Server, DB2, ...). [cite: 82]
* En el curso se presentará el modelo E-R como conceptual y el Relacional como lógico. [cite: 83]

### 8. Consideraciones Adicionales
* En teoría, debería existir un lenguaje de descripción para cada esquema (nivel), pero en la práctica, muchos SGBD fusionan la especificación del esquema lógico con la del interno. [cite: 71]
* La descripción completa de una BD se denomina esquema. Cada vista de usuario tiene su subesquema. [cite: 70]