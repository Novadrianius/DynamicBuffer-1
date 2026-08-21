# DynamicBuffer - API

---
### Constructor `.new()`
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
### Capacidad `:GetLength()`
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
### Espacio en uso `:GetUsedSpace()`
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
### Escritura con signo `:int8()`
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
### Escritura con signo `:int16()`
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
### Escritura con signo `:int32()`
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
### Escritura sin signo `:uint8()`
Escribe un valor numérico sin signo dentro de un `DynamicBuffer`

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
### Escritura sin signo `:uint16()`
Escribe un valor numérico sin signo dentro de un `DynamicBuffer`

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
### Escritura sin signo `:uint32()`
Escribe un valor numérico sin signo dentro de un `DynamicBuffer`

* **Parámetros** -> value: `number?`

``` luau
myBuff:uint32(value: number?)
```

**Ejemplo:**
``` luau
local myBuff = DynamicBuffer.new()
myBuff:uint32(1_000_000)
```
