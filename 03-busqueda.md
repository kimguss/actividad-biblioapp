# Módulo de búsqueda

## Técnica utilizada: Tabla de decisión

Para este módulo se utiliza una tabla de decisión, porque la respuesta del sistema depende de varias condiciones al mismo tiempo.

La búsqueda permite consultar libros por título, autor o ISBN.

El campo debe tener mínimo 3 caracteres y máximo 100. Además, si contiene los caracteres especiales <, >, ", ', ; el sistema debe rechazar la búsqueda mostrando el mensaje "Caracteres no permitidos".

## Tabla de decisión

| Regla | Longitud válida | Caracteres especiales | Existen resultados | Resultado esperado |
|---|---|---|---|---|
| R1 | Sí | No | Sí | Mostrar los libros encontrados |
| R2 | Sí | No | No | Informar que no se encontraron resultados |
| R3 | Sí | Sí | Sí | Mostrar "Caracteres no permitidos" |
| R4 | Sí | Sí | No | Mostrar "Caracteres no permitidos" |
| R5 | No | No | Sí | Rechazar la búsqueda por longitud inválida |
| R6 | No | No | No | Rechazar la búsqueda por longitud inválida |
| R7 | No | Sí | Sí | Rechazar la búsqueda |
| R8 | No | Sí | No | Rechazar la búsqueda |

## Casos de prueba derivados

| ID | Descripción | Datos de entrada | Resultado esperado |
|---|---|---|---|
| BUS-01 | Búsqueda válida con resultados | "Bases de datos" | Mostrar libros relacionados |
| BUS-02 | Búsqueda válida sin resultados | "Libro inexistente" | Informar que no se encontraron resultados |
| BUS-03 | Búsqueda con menos de 3 caracteres | "BD" | Rechazar la búsqueda |
| BUS-04 | Búsqueda con exactamente 3 caracteres | "SQL" | Ejecutar la búsqueda |
| BUS-05 | Búsqueda con más de 100 caracteres | Texto de 101 caracteres | Rechazar la búsqueda |
| BUS-06 | Búsqueda con carácter especial < | "Base<datos" | Mostrar "Caracteres no permitidos" |
| BUS-07 | Búsqueda con carácter especial ; | "Oracle;" | Mostrar "Caracteres no permitidos" |
| BUS-08 | Búsqueda válida por ISBN | ISBN válido | Mostrar el libro si existe |

## Análisis

La tabla de decisión permite revisar diferentes combinaciones posibles entre la longitud del texto, la presencia de caracteres especiales y la existencia de resultados.

De esta manera se puede comprobar que la aplicación responda correctamente tanto en búsquedas válidas como en situaciones en las que el usuario introduce información incorrecta.
