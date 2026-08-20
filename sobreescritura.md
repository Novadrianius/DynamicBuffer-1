# Sobreescritura de Valores
@author: chicharron703 / Novadrianius

El uso real de los `DynamicBuffer` suele ser desde scripts de módulo, y la sobreescritura de valores es una pieza clave.

---
## OverwriteByIndex
Los objetos `DynamicBuffer` cuenta con el método `:OverwriteByIndex()`, el cual lleva como parámetros el índice donde quieres sobrescribir un nuevo valor y el nuevo valor
que se va a escribir dentro del `DynamicBuffer`.

``` luau
local myBuff = DynamicBuffer.new()
myBuff:int16(500)
print("Indice 0 =", myByff:GetValueByIndex(0))

myBuff:OverwriteByIndex(0, 300)
print("Indice 0 =", myByff:GetValueByIndex(0))
```
**Output**
``` text
Indice 0 = 500
Indice 0 = 300
```

---
En un `ModuleScript` puedes definir la estructura de tu `DynamicBuffer`.

**ModuleScript**
``` luau
local myBuff = DynamicBuffer.new()

myBuff:uint8()
myBuff:uint16()
myBuff:uint32()

return myBuff
```

En un `LocalScript` o en un `Script` puedes sobrescribir los valores del buffer.

**LocalScript**
``` luau
local myBuff = require(path.to.myBuff)

myBuff:OverwriteByIndex(0, player.data.level)
myBuff:OverwriteByIndex(1, player.data.exp)
myBuff:OverwriteByIndex(2, player.data.money)
```

Y el `DynamicBuffer` ya tendría los valores listos para que después sea enviado por la red hacia el servidor mediante un `RemoteEvent`.
