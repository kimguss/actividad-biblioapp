01-prestamos.md
# Módulo de préstamos

## Técnica utilizada: Partición de equivalencias

Para este módulo se utiliza la técnica de partición de equivalencias. 
La idea es separar los datos de entrada en grupos válidos e inválidos para 
evitar tener que probar todos los valores posibles.

Para estos casos se supone que el usuario se encuentra registrado y autenticado.

## Clases de equivalencia

| Variable | Clase válida | Clase inválida |
|---|---|---|
| Número de préstamos activos | De 0 a 3 préstamos | 4 o más préstamos |
| Días de retraso | 0 días: devolución a tiempo | Valores negativos |
| Días de retraso | 1 o más días: se genera multa de $500 por cada día | No aplica un retraso negativo |
| Disponibilidad del libro | Libro disponible | Libro no disponible |

## Casos de prueba

| ID | Descripción | Datos de entrada | Resultado esperado |
|---|---|---|---|
| PRE-01 | Solicitar un préstamo sin tener préstamos activos | 0 préstamos activos, libro disponible | El préstamo debe ser aprobado |
| PRE-02 | Solicitar un préstamo teniendo 2 préstamos activos | 2 préstamos activos, libro disponible | El préstamo debe ser aprobado |
| PRE-03 | Solicitar un préstamo teniendo el máximo permitido | 3 préstamos activos, libro disponible | El préstamo debe ser aprobado |
| PRE-04 | Solicitar un préstamo superando el máximo permitido | 4 préstamos activos, libro disponible | El sistema debe rechazar el préstamo |
| PRE-05 | Solicitar un préstamo cuando el libro no está disponible | 1 préstamo activo, libro no disponible | El sistema debe rechazar el préstamo |
| PRE-06 | Devolver un libro dentro del plazo establecido | 0 días de retraso | El libro debe ser recibido sin generar multa |
| PRE-07 | Devolver un libro con 1 día de retraso | 1 día de retraso | El sistema debe generar una multa de $500 |
| PRE-08 | Devolver un libro con 5 días de retraso | 5 días de retraso | El sistema debe generar una multa de $2.500 |
| PRE-09 | Ingresar un número de días de retraso negativo | -1 día de retraso | El sistema debe rechazar el valor por ser inválido |

## Análisis

Los casos anteriores permiten comprobar las principales reglas relacionadas 
con el préstamo de libros. Se revisa que un usuario pueda tener máximo tres 
préstamos activos al mismo tiempo, que el libro se encuentre disponible y que 
las devoluciones realizadas fuera del plazo generen la multa correspondiente.

También se incluye un caso con un valor negativo para comprobar que el sistema 
no acepte información que no tendría sentido dentro del proceso de devolución.
