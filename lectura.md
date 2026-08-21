# Lectura de Datos
@author: chicharron703 / Novadrianius

## Leer datos de un buffer dinámico
Los buffers dinámicos también proporcionan una forma más sencilla de leer datos que la librería `buffer` de Roblox.

Los `DynamicBuffers` son igual de sencillos de manejar que una `table` de Roblox. Los `DynamicBuffer` te evitan calcular desplazamientos de memoria, y tu único trabajo será saber en qué orden escribiste los valores dentro de tu `DynamicBuffer`.

### `GetValueByIndex`
Si tenemos un `DynamicBuffer` con varios valores escritos y queremos leer (obtener) el primer valor de este, basta con usar el método `:GetValueByIndex()`.

`:GetValueByIndex()` lleva como parámetro un número, el cual es el índice que se desea leer dentro del `DynamicBuffer` (iniciando desde el índice 0).
``` luau
local myBuff = DynamicBuffer.new(8)

myBuff:uint8(100)
myBuff:uint16(200)
myBuff:uint32(5_000_000)

print(myBuff:GetValueByIndex(0)) -- Imprime el primer valor escrito dentro del buffer
```
**Output:**
```text
100
```
>[!TIP]
>Si quieres acceder a los últimos índices del `DynamicBuffer`, puedes usar números negativos (como el -1 para leer el último valor escrito o el -2 para leer el penúltimo).
``` luau
local myBuff = DynamicBuffer.new(8)

myBuff:uint8(100)
myBuff:uint16(200)
myBuff:uint32(5_000_000)

print(myBuff:GetValueByIndex(-1)) -- Imprime el último valor escrito dentro del buffer
```
**Output:**
``` text
5000000
```
---
En `DynamicBuffer`, en lugar de calcular desplazamientos de memoria, basta con acordarse del orden en que escribiste los valores dentro del buffer.
``` luau
myBuff:uin8(100)
myBuff:uint8(50)
myBuff:uint16(1_000)

local value1 = myBuff:GetValueByIndex(0) -- 100
local value2 = myBuff:GetValueByIndex(1) -- 50
local value3 = myBuff:GetValueByIndex(2) -- 1,000
```
Esto permite que manejar buffers sea como manejar tablas. La única diferencia sería que los `DynamicBuffer` empiezan desde el índice 0, a diferencia de una tabla
(la cual inicia desde el índice 1).

>[!NOTE]
>Pasar un índice inválido al método `:GetValueByIndex()` simplemente mostrará un mensaje diciendo que se intentó acceder a un índice fuera de memoria del `DynamicBuffer`.
---
Puedes conocer el comportamiento de un `DynamicBuffer` respecto al manejo de su tamaño en [Incremento de Tamaño](incremento.md).

## [Volver a inicio](README.md)
