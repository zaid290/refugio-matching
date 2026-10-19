# Refugio Matching

Sistema de recomendación y *matching* para la adopción de mascotas en un refugio.
Proyecto de **Programación III – Estructuras de Datos y Algoritmos en Java** (UDLA).

## Problema

Los refugios tienen muchos animales y muchos adoptantes, y el emparejamiento manual es lento. Además provoca devoluciones por incompatibilidad, y los animales adultos y seniors envejecen sin ser adoptados. Proponemos un sistema que recomiende a cada adoptante los animales con los que tiene mayor afinidad, que dé visibilidad a los que llevan más tiempo en el refugio y que organice las visitas al hogar que exige cada adopción.

## Integrantes

| Integrante | GitHub | Responsabilidad |
|---|---|---|
| Zaid Chamorro | [@zaid290](https://github.com/zaid290) | Módulos 3 y 4, interfaz de consola |
| Esteban Chapaca | [@Esteban201020](https://github.com/Esteban201020) | Módulos 1 y 2, persistencia CSV |
| Mahe Paredes | [@MaheP-06](https://github.com/MaheP-06) | Módulos 5 y 6 |

## Módulos

1. Registro de animales (especie, edad, salud, temperamento)
2. Registro de adoptantes y preferencias (con precalificación)
3. Motor de recomendación (matching por afinidad)
4. Priorización de animales por tiempo en refugio
5. Historial de adopciones y reportes
6. Visitas domiciliarias y seguimiento posadopción

**Alternativa seleccionada para el motor:** lista de animales + filtrado + scoring ponderado + selección top-N con `PriorityQueue`. La justificación está en el informe del Progreso 1.

## Estructuras y algoritmos (temas de la asignatura)

| Tema | Uso en el proyecto |
|---|---|
| Arreglos | Pesos de los criterios; matriz de tiempos de la ruta del día |
| Listas | Animales ordenados por id; historial de solicitudes |
| Pilas | Deshacer la última edición de una ficha |
| Colas | Solicitudes pendientes (FIFO); recorrido en anchura del mapa |
| Colas con prioridad | Top-N de recomendaciones, priorización, agenda de visitas, Dijkstra |
| Búsqueda | Secuencial (filtros) y binaria (por id y por fechas) |
| Recursividad | Mergesort, árbol binario de búsqueda, árbol de decisión, preorden |
| Ordenamiento | Mergesort para reportes |
| Árboles binarios de búsqueda | Adoptantes por cédula, listado en inorden |
| Árboles de decisión | Precalificación del adoptante |
| Grafos y ruta más corta | Mapa de sectores, Dijkstra, verificación de conectividad (BFS) |
| Árboles de expansión | Orden de las visitas del día (Prim + recorrido en preorden) |

## Tecnologías

- Java (JDK 24), solo con la biblioteca estándar
- IntelliJ IDEA
- Git y GitHub

## Estructura

```
refugio-matching/
├── README.md
├── refugio-matching.iml       # proyecto de IntelliJ IDEA
├── .idea/                     # configuración compartida del proyecto
├── .gitignore
├── docs/
│   └── uml/                   # diagramas de clases (PlantUML y PNG)
├── data/
│   ├── animales.csv           # datos de prueba
│   ├── adoptantes.csv
│   └── sectores.csv           # mapa de sectores (grafo)
├── src/ec/udla/refugio/
│   ├── App.java
│   ├── modelo/                # clases de dominio y enums
│   ├── registro/              # Módulos 1 y 2 (lista, pila, ABB, árbol de decisión)
│   ├── recomendacion/         # Módulo 3
│   ├── prioridad/             # Módulo 4
│   ├── historial/             # Módulo 5
│   ├── visitas/               # Módulo 6 (grafo)
│   └── persistencia/          # lectura/escritura CSV
└── test/ec/udla/refugio/      # casos de prueba por módulo
```

## Cómo abrir el proyecto

1. En IntelliJ IDEA, ve a **File → Open…**, selecciona la carpeta `refugio-matching` y, si lo pregunta, elige **Trust Project**.
2. Ve a **File → Project Structure → Project → SDK** y selecciona **24**.
3. Ejecuta `App.java`.

## Ramas

- `main`: versión estable
- `develop`: integración
- `feature/<modulo>`: una rama por integrante; los cambios entran por *pull request*

## Estado

- **Progreso 1:** análisis, diseño y selección de la solución (estructura inicial del repositorio).
- **Progreso 2:** módulos que usan pilas, colas, colas con prioridad, listas, búsqueda y ordenamiento.
- **Progreso 3:** árbol binario de búsqueda, árbol de decisión y módulo de visitas con grafos.
