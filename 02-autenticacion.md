# Módulo de autenticación

## Técnica utilizada: Análisis de valores límite

Para este módulo se utiliza la técnica de análisis de valores límite, ya que la contraseña debe cumplir con una longitud mínima y máxima.

La contraseña debe tener entre 8 y 20 caracteres, incluir al menos una letra mayúscula, un número y un carácter especial.

## Casos de prueba

| ID | Condición | Datos de entrada | Resultado esperado | Resultado real |
|---|---|---|---|---|
| AUT-01 | Un carácter por debajo del mínimo | Contraseña de 7 caracteres: Ab1#xyz | El sistema debe rechazar la contraseña por no cumplir la longitud mínima | |
| AUT-02 | Límite mínimo permitido | Contraseña de 8 caracteres: Abc1#xyz | El sistema debe aceptar la contraseña | |
| AUT-03 | Un carácter por encima del mínimo | Contraseña de 9 caracteres: Abcd1#xyz | El sistema debe aceptar la contraseña | |
| AUT-04 | Un carácter por debajo del máximo | Contraseña válida de 19 caracteres | El sistema debe aceptar la contraseña | |
| AUT-05 | Límite máximo permitido | Contraseña válida de 20 caracteres | El sistema debe aceptar la contraseña | |
| AUT-06 | Un carácter por encima del máximo | Contraseña válida de 21 caracteres | El sistema debe rechazar la contraseña por superar la longitud máxima | |
| AUT-07 | Longitud válida pero sin mayúscula | abcdef1# | El sistema debe rechazar la contraseña | |
| AUT-08 | Longitud válida pero sin número | Abcdefg# | El sistema debe rechazar la contraseña | |
| AUT-09 | Longitud válida pero sin carácter especial | Abcdefg1 | El sistema debe rechazar la contraseña | |

## Análisis

Estos casos permiten comprobar los límites mínimos y máximos establecidos para la contraseña.

También se incluyen casos donde la longitud es correcta, pero falta alguno de los requisitos obligatorios, como una letra mayúscula, un número o un carácter especial.

El campo de resultado real se deja vacío para diligenciarlo al momento de ejecutar las pruebas.
