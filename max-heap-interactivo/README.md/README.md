 Max-Heap Interactivo

Sitio web educativo e interactivo para aprender el funcionamiento de un Max-Heap (Montículo Binario Máximo) mediante teoría, visualizaciones, simulaciones y un mini-juego.

El proyecto está desarrollado completamente con HTML, CSS y JavaScript, sin dependencias externas, frameworks ni librerías adicionales.

 Descripción

Un Max-Heap es una estructura de datos basada en un árbol binario completo donde cada padre es mayor o igual que sus hijos.

Este proyecto busca explicar el concepto de una manera visual y práctica, permitiendo al usuario experimentar directamente con las operaciones de la estructura.

La aplicación incluye:

 Explicación teórica del Max-Heap.
 Analogía con un torneo para comprender la estructura.
 Visualización gráfica del árbol.
 Inserción de elementos.
⬇ Extracción del elemento máximo.
 Animación del proceso sift-up.
 Animación del proceso sift-down.
 Representación del heap como arreglo.
 Análisis de complejidad Big O.
 Código base de implementación en JavaScript.
 Aplicaciones del Max-Heap en sistemas reales.
 Mini-juego para identificar errores en un Max-Heap.
 Características
 Teoría

La sección de teoría explica:

Qué es un heap.
Diferencia entre Max-Heap y Min-Heap.
Propiedad fundamental del Max-Heap.
Representación mediante arreglos.
Relación entre índices y nodos.
Operaciones principales.
Ventajas y limitaciones.
Analogía

Para facilitar la comprensión se utiliza la analogía de un torneo.

El participante con mayor puntuación asciende hacia la parte superior, de forma similar a como un elemento grande puede subir hacia la raíz durante una operación de inserción.

Esta analogía permite comprender visualmente conceptos como:

Padre.
Hijo.
Raíz.
Sift-up.
Sift-down.
Máximo.
 Laboratorio interactivo

El laboratorio permite experimentar directamente con la estructura.

El usuario puede:

Introducir un número.
Insertarlo en el heap.
Observar cómo sube hasta encontrar su posición correcta.
Extraer el máximo.
Observar cómo el último elemento ocupa la raíz.
Ver cómo el elemento se hunde hasta restaurar la propiedad del Max-Heap.

También existe un botón para generar valores aleatorios.

 Mini-juego

El mini-juego presenta diferentes árboles y el usuario debe identificar el nodo que rompe la propiedad del Max-Heap.

Cuenta con:

3 niveles.
Sistema de puntos.
Sistema de vidas.
Retroalimentación inmediata.
Identificación visual del nodo incorrecto.
 Complejidad algorítmica
Operación	Complejidad	Descripción
Consultar máximo	O(1)	El máximo siempre está en la raíz.
Insertar	O(log n)	El elemento puede subir varios niveles.
Extraer máximo	O(log n)	El elemento puede descender varios niveles.
Buscar un valor	O(n)	El heap no está completamente ordenado.
Construir heap	O(n)	Puede construirse mediante el algoritmo bottom-up.

Un Max-Heap es especialmente útil cuando necesitamos obtener repetidamente el elemento de mayor prioridad.

No es la estructura ideal cuando necesitamos realizar búsquedas arbitrarias rápidamente.

 Representación mediante arreglo

Debido a que el árbol es completo, puede almacenarse en un arreglo sin utilizar punteros.

Para un nodo ubicado en el índice i:

Padre          = Math.floor((i - 1) / 2)
Hijo izquierdo = 2 * i + 1
Hijo derecho   = 2 * i + 2


Por ejemplo:

             90
           /    \
         80      60
        /  \    /  \
      70   50  40  30


Se representa como:

[90, 80, 60, 70, 50, 40, 30]

 Código base

La aplicación incluye una implementación básica de un Max-Heap en JavaScript:

class MaxHeap {
  constructor() {
    this.heap = [];
  }

  parent(i) {
    return Math.floor((i - 1) / 2);
  }

  left(i) {
    return 2 * i + 1;
  }

  right(i) {
    return 2 * i + 2;
  }

  insert(value) {
    this.heap.push(value);

    let i = this.heap.length - 1;

    while (i > 0) {
      const p = this.parent(i);

      if (this.heap[p] >= this.heap[i]) {
        break;
      }

      [this.heap[p], this.heap[i]] =
        [this.heap[i], this.heap[p]];

      i = p;
    }
  }

  peek() {
    return this.heap.length > 0
      ? this.heap[0]
      : null;
  }

  extractMax() {
    if (this.heap.length === 0) {
      return null;
    }

    if (this.heap.length === 1) {
      return this.heap.pop();
    }

    const max = this.heap[0];

    this.heap[0] = this.heap.pop();

    let i = 0;

    while (true) {
      const left = this.left(i);
      const right = this.right(i);

      let largest = i;

      if (
        left < this.heap.length &&
        this.heap[left] > this.heap[largest]
      ) {
        largest = left;
      }

      if (
        right < this.heap.length &&
        this.heap[right] > this.heap[largest]
      ) {
        largest = right;
      }

      if (largest === i) {
        break;
      }

      [this.heap[i], this.heap[largest]] =
        [this.heap[largest], this.heap[i]];

      i = largest;
    }

    return max;
  }
}

 Aplicaciones

Los Max-Heaps y las estructuras basadas en heaps tienen aplicaciones en diferentes áreas de la informática:

 Colas de prioridad

Permiten administrar tareas según su nivel de prioridad y obtener rápidamente la tarea más importante.

 Videojuegos

Pueden utilizarse para administrar eventos, acciones o entidades según diferentes niveles de prioridad.

 Heap Sort

Heap Sort utiliza un heap como parte fundamental de su algoritmo y tiene una complejidad de O(n log n).

 Algoritmos de grafos

Las estructuras de prioridad basadas en heaps aparecen en algoritmos como Dijkstra y Prim.

 Sistemas operativos

Los conceptos de colas de prioridad pueden utilizarse para organizar procesos y tareas según su prioridad.

 Tecnologías utilizadas
HTML5
CSS3
JavaScript
SVG
DOM API
CSS Animations

No se utilizan:

Frameworks.
Librerías externas.
Bases de datos.
Backend.
Dependencias de npm.
 Estructura del proyecto
max-heap-interactivo/
│
├── index.html
└── README.md


Todo el proyecto está contenido en un único archivo HTML para facilitar su ejecución y distribución.

Cómo ejecutar

No es necesario instalar nada.

Opción 1 — Abrir directamente

Descarga o clona el repositorio y abre:

index.html


con cualquier navegador moderno.

Opción 2 — Clonar el repositorio
git clone https://github.com/TU-USUARIO/max-heap-interactivo.git
cd max-heap-interactivo


Después abre index.html.

 Compatibilidad

El proyecto está diseñado para funcionar en navegadores modernos como:

Google Chrome
Mozilla Firefox
Microsoft Edge
Safari

También cuenta con estilos responsive para adaptarse a pantallas pequeñas.

 Objetivo académico

Este proyecto fue desarrollado con fines educativos para facilitar el aprendizaje de estructuras de datos.

Su objetivo principal es complementar la explicación teórica con una experiencia visual e interactiva que permita comprender qué sucede internamente durante las operaciones de un Max-Heap.

Conceptos demostrados
Max-Heap
├── Árbol binario completo
├── Propiedad padre ≥ hijos
├── Representación mediante arreglo
├── Insertar
│   └── Sift-Up
├── Extraer máximo
│   └── Sift-Down
├── Consultar máximo
├── Complejidad Big O
└── Aplicaciones reales

 Autor: Suyen,Chenoa,Josebeth

Proyecto educativo desarrollado para el estudio y demostración de estructuras de datos.
