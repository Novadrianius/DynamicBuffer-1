# DynamicBuffer - API

>[!WARNING]
>Actualmente `DynamicBuffer` no cuenta con soporte para `string`.
---

#### Tipo de dato `DynamicBuffer`:
``` luau
local DynamicBuffer = require(path.to.DynamicBuffer)
local myBuff: DynamicBuffer.DynamicBuffer = DynamicBuffer.new()
```
**Otra opción:**
``` luau
local DynmicBuffer = require(path.to.DynamicBuffer)

type DynamicBuffer = typeof(DynamicBuffer.new())

local myBuff: DynamicBuffer = DynamicBuffer.new()
```

---
### - Constructor `.new()`
Crea un objeto `DynamicBuffer` y lo retorna.

* **Parámetros** -> InitialSize: `number?`
* **Valores de retorno** -> `DynamicBuffer`
``` luau
DynamicBuffer.new(InitialSize: number?)
```

**Ejemplo:**
``` luau
local myBuff = DynamicBuffer.new()
local myBuff2 = DynamicBuffer.new(8)
```

---
### - Capacidad `:GetLength()`
Retorna un número que representa la capacidad de un `DynamicBuffer` en bytes.

* **Valores de retorno** -> `number`
```luau
myBuff:GetLength()
```

**Ejemplo:**
``` luau
local myBuff = DynamicBuffer.new(10)

local length = myBuff:GetLength()
print("Length:", length)
```

**Output**
``` text
Length: 10
```

---
### - Espacio en uso `:GetUsedSpace()`
Retorna un número que representa el espacio en uso dentro de un `DynamicBuffer` en bytes.

* **Valores de retorno** -> `number`
``` luau
myBuff:GetUsedSpace()
```

**Ejemplo:**
``` luau
local myBuff = DynamicBuffer.new()
myBuff:int16(1_000)

local usedSpace = myBuff:GetUsedSpace()
print("Used space:", usedSpace)
```

**Output**
``` text
Used space: 2
```

---
### - Escritura con signo `:int8()`
Escribe un valor numérico con signo dentro de un `DynamicBuffer`.

* **Parámetros** -> value: number?

``` luau
myBuff:int8(value: number?)
```

**Ejemplo:**
``` luau
local myBuff = DynamicBuffer.new()
myBuff:int8(-128)
```

---
### - Escritura con signo `:int16()`
Escribe un valor numérico con signo dentro de un `DynamicBuffer`.

* **Parámetros** -> value: number?

``` luau
myBuff:int16(value: number?)
```

**Ejemplo:**
``` luau
local myBuff = DynamicBuffer.new()
myBuff:int8(1_000)
```

---
### - Escritura con signo `:int32()`
Escribe un valor numérico con signo dentro de un `DynamicBuffer`.

* **Parámetros** -> value: number?

``` luau
myBuff:int32(value: number?)
```

**Ejemplo:**
``` luau
local myBuff = DynamicBuffer.new()
myBuff:int32(1_000_000)
```

---
### - Escritura sin signo `:uint8()`
Escribe un valor numérico sin signo dentro de un `DynamicBuffer`.

* **Parámetros** -> value: `number?`

``` luau
myBuff:uint8(value: number?)
```

**Ejemplo:**
``` luau
local myBuff = DynamicBuffer.new()
myBuff:uint8(255)
```

---
### - Escritura sin signo `:uint16()`
Escribe un valor numérico sin signo dentro de un `DynamicBuffer`.

* **Parámetros** -> value: `number?`

``` luau
myBuff:uint16(value: number?)
```

**Ejemplo:**
``` luau
local myBuff = DynamicBuffer.new()
myBuff:uint16(1_000)
```

---
### - Escritura sin signo `:uint32()`
Escribe un valor numérico sin signo dentro de un `DynamicBuffer`.

* **Parámetros** -> value: `number?`

``` luau
myBuff:uint32(value: number?)
```

**Ejemplo:**
``` luau
local myBuff = DynamicBuffer.new()
myBuff:uint32(1_000_000)
```

---
### - Escritura de flotantes `:float32()`
Escribe un valor numérico flotante con una precisión de 7 decimales dentro de un `DynamicBuffer`.

* **Parámetros** -> value: `number?`

``` luau
myBuff:float32(value: number?)
```

**Ejemplo:**
``` luau
local myBuff = DynamicBuffer.new()
myBuff:float32()
```

---
### - Escritura de flotantes `:float64()`
Escribe un valor numérico flotante con una precisión de 15-17 decimales dentro de un `DynamicBuffer`.

* **Parámetros** -> value: `number?`

``` luau
myBuff:float64(value: number?)
```

**Ejemplo:**
``` luau
local myBuff = DynamicBuffer.new(8)
myBuff:float64()
```

---
### - Lectura de valores `:GetValueByIndex()`
Retorna un valor escrito dentro de un `DynamicBuffer` de acuerdo con un índice (empezando desde el 0).

* **Parámetros** -> index: `number`
* **Valores de retorno** -> `number` | `string`

``` luau
myBuff:GetValueByIndex(index: number)
```

**Ejemplo:**
``` luau
local myBuff = DynamicBuffer.new()
myBuff:uint8(100)
myBuff:uint8(200)

local value = myBuff:GetValueByIndex(0)
print("Value =", value)
```

**Output**
``` text
Value = 100
```

---
### - Sobreescritura `:OverwriteByIndex()`
Sobrescribe un nuevo valor dentro de un `DynamicBuffer` en el índice especificado en un valor ya existente.

* **Parámetros** -> index: `number`, newValue: `number` | `string`
``` luau
myBuff:OverwriteByIndex(index: number, newValue: number | string)
```

**Ejemplo:**
``` luau
local myBuff = DynamicBuffer.new()
myBuff:uint16(1_000)

myBuff:OverwriteByIndex(0, 500)
print(myBuff:GetValueByIndex(0))
```

**Output**
``` text
500
```

---
### - Obtener buffer `:ExportBuffer()`
Retorna un buffer con los valores de un `DynamicBuffer` escritos en él.

* **Valores de retorno** -> `buffer`
``` luau
myBuff:ExportBuffer()
```

**Ejemplo:**
``` luau
local myBuff = DynamicBuffer.new()
myBuff:uint8(10)
myBuff:uint8(20)
myBuff:uint8(30)

local exportedBuffer = myBuff:ExportBuffer()
print(buffer.readu8(exportedBuffer, 0))
```

**Output**
``` text
10
```

### - Obtener buffer dinámico `:ImportBuffer()`
Convierte un `buffer` a un `DynamicBuffer` siempre y cuando sean compatibles.

* **Valores de retorno** -> `boolean`, `DynamicBuffer`
```
myBuff:ImportBuffer()
```

**Ejemplo:**
``` luau
local myBuff = DynamicBuffer.new()
local createdBuffer = myBuff:ExportBuffer()

local success, newBuff = myBuff:ImportBuffer(createdBuffer)
if success then
  print(newBuff:GetLength())
else
  warn "¡Buffer no compatible!"
end
```

---
Puede consultar la documentación de `DynamicBuffer` haciendo [click aquí](Start.md).

## [Volver a inicio](README.md)
