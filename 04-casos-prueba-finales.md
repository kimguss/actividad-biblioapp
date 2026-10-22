# Registro general de casos de prueba

En esta sección se reúnen los casos de prueba diseñados para los módulos de préstamos, autenticación y búsqueda de BiblioApp.

Los campos "Resultado real" y "Estado" se dejan vacíos para completarlos cuando las pruebas sean ejecutadas.

| ID | Módulo | Técnica | Descripción | Datos de entrada | Resultado esperado | Resultado real | Estado |
|---|---|---|---|---|---|---|---|
| PRE-01 | Préstamos | Partición de equivalencias | Solicitar préstamo sin préstamos activos | 0 préstamos, libro disponible | Préstamo aprobado | | |
| PRE-02 | Préstamos | Partición de equivalencias | Solicitar préstamo con 2 préstamos activos | 2 préstamos, libro disponible | Préstamo aprobado | | |
| PRE-03 | Préstamos | Partición de equivalencias | Solicitar préstamo con el máximo permitido | 3 préstamos, libro disponible | Préstamo aprobado | | |
| PRE-04 | Préstamos | Partición de equivalencias | Superar el máximo de préstamos permitidos | 4 préstamos, libro disponible | Préstamo rechazado | | |
| PRE-05 | Préstamos | Partición de equivalencias | Solicitar un libro no disponible | 1 préstamo, libro no disponible | Préstamo rechazado | | |
| PRE-06 | Préstamos | Partición de equivalencias | Devolver libro dentro del plazo | 0 días de retraso | Devolución aceptada sin multa | | |
| PRE-07 | Préstamos | Partición de equivalencias | Devolver libro con un día de retraso | 1 día de retraso | Multa de $500 | | |
| PRE-08 | Préstamos | Partición de equivalencias | Devolver libro con cinco días de retraso | 5 días de retraso | Multa de $2.500 | | |
| PRE-09 | Préstamos | Partición de equivalencias | Ingresar días de retraso negativos | -1 día | Rechazar el valor ingresado | | |
| AUT-01 | Autenticación | Valores límite | Contraseña menor al mínimo | Ab1#xyz (7 caracteres) | Contraseña rechazada | | |
| AUT-02 | Autenticación | Valores límite | Contraseña en el límite mínimo | Abc1#xyz (8 caracteres) | Contraseña aceptada | | |
| AUT-03 | Autenticación | Valores límite | Contraseña un carácter sobre el mínimo | Abcd1#xyz (9 caracteres) | Contraseña aceptada | | |
| AUT-04 | Autenticación | Valores límite | Contraseña de 19 caracteres | Abcdefghijklmn1#XYZ | Contraseña aceptada | | |
| AUT-05 | Autenticación | Valores límite | Contraseña en el límite máximo | Abcdefghijklmno1#XYZ | Contraseña aceptada | | |
| AUT-06 | Autenticación | Valores límite | Contraseña superior al máximo | Abcdefghijklmnop1#XYZ | Contraseña rechazada | | |
| AUT-07 | Autenticación | Valores límite | Contraseña sin mayúscula | abcdef1# | Contraseña rechazada | | |
| AUT-08 | Autenticación | Valores límite | Contraseña sin número | Abcdefg# | Contraseña rechazada | | |
| AUT-09 | Autenticación | Valores límite | Contraseña sin carácter especial | Abcdefg1 | Contraseña rechazada | | |
| BUS-01 | Búsqueda | Tabla de decisión | Búsqueda válida con resultados | Bases de datos | Mostrar libros relacionados | | |
| BUS-02 | Búsqueda | Tabla de decisión | Búsqueda válida sin resultados | Libro inexistente | Informar que no existen resultados | | |
| BUS-03 | Búsqueda | Tabla de decisión | Búsqueda menor al mínimo | BD | Rechazar la búsqueda | | |
| BUS-04 | Búsqueda | Tabla de decisión | Búsqueda con exactamente 3 caracteres | SQL | Ejecutar la búsqueda | | |
| BUS-05 | Búsqueda | Tabla de decisión | Búsqueda mayor al máximo permitido | Texto de 101 caracteres | Rechazar la búsqueda | | |
| BUS-06 | Búsqueda | Tabla de decisión | Búsqueda con carácter especial | Base<datos | Mostrar "Caracteres no permitidos" | | |
| BUS-07 | Búsqueda | Tabla de decisión | Búsqueda con punto y coma | Oracle; | Mostrar "Caracteres no permitidos" | | |
| BUS-08 | Búsqueda | Tabla de decisión | Búsqueda válida mediante ISBN | ISBN válido | Mostrar el libro si existe | | |

## Conclusión

El desarrollo de estos casos de prueba permite revisar el comportamiento de las funciones principales de BiblioApp sin necesidad de conocer cómo está programada internamente.

Con la partición de equivalencias se revisaron diferentes situaciones relacionadas con los préstamos. El análisis de valores límite permitió comprobar las reglas de la contraseña y la tabla de decisión ayudó a analizar diferentes escenarios del módulo de búsqueda.

Estas técnicas permiten organizar mejor las pruebas y encontrar posibles errores antes de que la aplicación sea utilizada por los usuarios.
