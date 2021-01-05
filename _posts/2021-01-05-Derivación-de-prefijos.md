---
layout: post
title: "Derivación de prefijos para lógica de negocio"
date: 2021-01-05
---
A veces, al crear la lógica de negocios, se da alguna identificación por el prefijo de un número, pero tenemos que extraer ese prefijo con SQL.

Aunque aquí nos referimos a los prefijos de forma computacional, la definición gramatical tiene sentido: un prefijo es un afijo colocado antes de una palabra, base u otro prefijo para modificar el significado de un término.

Hay dos (y posiblemente muchas más formas) de extraer el prefijo que queremos.

Por ejemplo, si queremos recuperar todos los números de teléfono internacionales que son argentinos, necesitamos recuperar aquellos números que comienzan con "54".

1. Operador SQL LIKE

Por ejemplo:

SELECT numero_telefono
, nombre
FROM xyz_numeros
WHERE numero_telefono LIKE '54%'

Hay dos comodines que se utilizan a menudo junto con el operador LIKE:
%: El signo de porcentaje representa cero, uno o varios caracteres
_ - El guión bajo representa un solo carácter

En este caso, usamos el % porque vienen varios digitos en un número, no uno solo.

2. Función SUBSTRING ()

Por ejemplo:

SELECT numero_telefono
, nombre
FROM xyz_numeros
WHERE substring(numero_telefono,1,2) = '54'

Personalmente, me gusta la función SUBSTRING () , ya que me recuerda que lo que estoy buscando es un prefijo, ya que los prefijos son substring en sí.

¡Eso es todo!
