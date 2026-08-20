# Escritura de Datos
@author: chicharron703 / Novadrianius

---
Para escribir datos dentro de un buffer dinámico, usaremos al objeto `DynamicBuffer` que retorna el método constructor.

## Números con signo
Para escribir números con signos dentro de nuestro `DynamicBuffer`, usaremos métodos como `:int16()` (Dependiendo de qué valores y qué tamaño de bytes se desea escribir dentro del `DynamicBuffer`)

Si quisiéramos escribir valores como un `int8` o un `int32` se haría de la siguiente manera:
``` luau
local myBuff = DynamicBuffer.new(8)

myBuff:int8(100)
myBuff:int32(1_000_000)
```
Estos métodos nos permiten escribir valores dentro de los buffers sin la necesidad de calcular `offsets`.

Estos métodos de escritura llevan como parámetro el valor que se desea escribir dentro del `DynamicBuffer`. Sin embargo, estos pueden ir sin argumento por si solo se
desea reservar memoria dentro del `DynamicBuffer` sin escribir un valor aún.
``` luau
local myBuff = DynamicBuffer.new(8)

myBuff:int16() -- Memoria reservada (2 bytes)
myBuff:int8(100)
```
