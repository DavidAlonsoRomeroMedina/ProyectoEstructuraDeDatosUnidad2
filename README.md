# PROYECTO 3: Grafo por Nodos y Enlaces + Coloración (Método Greedy)

**Estudiante:** David Alonso Romero Medina  
**Institución:** Tecnológico de Software
**Fecha de entrega:** 27 de febrero de 2026

## Descripción del Proyecto
Este proyecto implementa una estructura de datos de **Grafo No Dirigido** utilizando listas de adyacencia. El objetivo principal es aplicar el algoritmo **Greedy Coloring** para asignar colores a los vértices de manera que no existan dos nodos adyacentes con el mismo color, buscando la eficiencia en el uso de recursos.

## Funcionalidades Principales
* **Estructura Dinámica:** Implementación de clase `Graph` con diccionarios.
* **Algoritmo Greedy:** Asignación de colores enteros (0, 1, 2...).
* **Optimización de Órdenes:** * Orden Natural (por ID).
    * Orden por Grado Descendente (Heurística de Welsh-Powell).
* **Validación Automática:** Función incorporada para verificar la legalidad de la coloración.

## Estructura del Repositorio
* `Proyecto3_EstructuraDeDatos_Unidad2.ipynb`: Libreta con el código documentado y pruebas de rendimiento.
* `README.md`: Documentación del proyecto.

## Cómo ejecutarlo
1. Clonar el repositorio.
2. Abrir el archivo `.ipynb` en **Google Colab** o Jupyter Notebook.
3. Ejecutar las celdas secuencialmente para observar las pruebas en grafos K4, C5 y el reto de 1000 nodos.


### 1. Estructura de Datos
Se utilizó un diccionario (`{vertice: [vecinos]}`) para representar la lista de adyacencia. Esto permite una búsqueda y asignación de conexiones en tiempo constante (O(1) en el mejor de los casos), lo cual es ideal para escalar el proyecto.

### 2. Métodos Principales Construidos
* `add_vertex(v)`: Registra un nuevo vértice en el diccionario si no existe.
* `add_edge(u, v)`: Crea un enlace bidireccional entre dos vértices, cumpliendo con la naturaleza de un grafo no dirigido.
* `neighbors(v)`: Retorna la lista de vértices conectados directamente a un nodo específico.
* `get_vertices()`: Retorna todos los nodos existentes en el grafo.

### 3. El Algoritmo de Coloración (`greedy_coloring`)
Este método recorre los vértices y asigna el primer color disponible. Se implementaron dos formas de ordenar los vértices antes de colorearlos, ya que el orden de entrada afecta drásticamente el resultado final:
* **Orden Natural:** Los vértices se procesan en orden alfabético o numérico ascendente.
* **Orden por Grado Descendente:** Se procesan primero los vértices con más conexiones (mayor número de vecinos). Matemáticamente, esto optimiza el uso de colores.

### 4. Validación (`validate_coloring`)
Un método automatizado que recorre todo el grafo una vez finalizada la coloración para verificar estrictamente que ninguna arista conecte dos vértices del mismo color. Retorna `True` si es válida y `False` si hay algún conflicto.

---

## Pruebas Ejecutadas en Colab

Para comprobar la solidez del código, se ejecutaron las siguientes pruebas solicitadas, mostrando en cada una la asignación de colores, el total utilizado y la validación:

1. **Grafo Completo K4:** Un grafo de 4 nodos donde todos están interconectados. El algoritmo asignó correctamente 4 colores distintos, ya que ninguna repetición es posible.
2. **Grafo Ciclo C5:** Un grafo de 5 nodos en forma de anillo. El algoritmo resolvió el problema utilizando 3 colores.
3. **Comparación de Órdenes:** Se creó un grafo irregular personalizado para demostrar cómo el método de **Grado Descendente** logra un uso más eficiente de los colores en comparación con el **Orden Natural**.

---

## Reto de Rendimiento: Grafo Masivo (1000 Nodos)
Como valor agregado a las pruebas base, se programó un script que genera un grafo de **1000 nodos y 5000 aristas aleatorias**. 
* **Propósito:** Medir el tiempo de ejecución (en milisegundos) y comprobar la eficiencia de la estructura de diccionarios en Python.
* **Resultado:** Demostró que ordenar los nodos por **Grado Descendente** en redes complejas no solo es rápido, sino que ahorra una cantidad significativa de colores frente al procesamiento lineal.

---

## Entorno de Desarrollo
* **Lenguaje:** Python 3
* **Entorno:** Google Colab (Jupyter Notebook)
* **Librerías usadas:** Solo librerías nativas (`random`, `time` para el reto masivo).
