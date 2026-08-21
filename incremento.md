# Incremento de Tamaño
@author: chicharron703 / Novadrianius

Un buffer dinámico no podría considerarse dinámico si no manejara el tamaño de su capacidad en bytes de forma automática.

---
Como se vio antes en la [creación de un buffer dinámico](Start.md), al usar el método constructor `.new()` podemos definir un tamaño inicial en bytes para nuestro
buffer dinámico. Sin embargo, ¿Qué ocurre cuando escribimos valores dentro de nuestro buffer que terminan superando la capacidad que le dimos a nuestro `DynamicBuffer`
al crearlo?

---
## Duplicación de tamaño
Si nosotros creamos un `DynamicBuffer` (4 bytes de capacidad como ejemplo) y escribimos valores en él que superan esta capacidad inicial:
``` luau
local myBuff = DynamicBuffer.new()
myBuff:uint32(1_000)
myBuff:int8(127) -- Supera la capacidad inicial del DynamicBuffer por 1 byte
```
Lo que terminará haciendo nuestro buffer es duplicar su capacidad hasta tener la suficiente para poder guardar estos valores.

Nuestro buffer tenía una capacidad de 4 bytes, pero al ser sobrepasado por sus métodos de escritura por un 1 byte más, lo que hará nuestro `DynamicBuffer` es
duplicar su capacidad, alcanzando los 8 bytes de capacidad. Con esta capacidad ahora es suficiente para guardar los valores escritos en el buffer sin problema alguno.

---
Para conocer la capacidad de nuestro `DynamicBuffer` podemos usar el método `:GetLength()`, el cual devuelve un número que representa la capacidad en bytes que tiene
el buffer actualmente.
``` luau
local myBuff = DynamicBuffer.new()
print("Capacidad inicial:", myBuff:GetLength())

myBuff:uint8(100)
myBuff:uint32(5_000_000) -- La capacidad del buffer es superada por 1 byte
-- El buffer dinámico duplica su capacidad actual hasta tener la suficiente para guardar los valores a escribir

print("Capacidad nueva:", myBuff:GetLength())
```
**Output:**
``` text
Capacidad inicial: 4
Capacidad nueva: 8
```

---
## Capacidad y espacio ocupado
Ya vimos que `:GetLength()` devuelve un número que representa la capacidad en bytes del `DynamicBuffer`, pero si se desea conocer cuántos bytes se han ocupado en el
buffer se usa el método `:GetUsedSpace()`.

El método `:GetUsedSpace()` devuelve un número que representa la cantidad de bytes en uso dentro del `DynamicBuffer`.
``` luau
local myBuff = DynamicBuffer.new()

myBuff:uint8(100)
myBuff:uint16(200)

print("Capacidad:", myBuff:GetLength())
print("Espacio en uso:", myBuff:GetUsedSpace())
```
**Output**
``` text
Capacidad: 4
Espacio en uso: 3
```

Para conocer cómo modificar los valores ya escritos en un `DynamicBuffer`, puedes leer más en [Sobreescritura de Valores](sobreescritura.md).
