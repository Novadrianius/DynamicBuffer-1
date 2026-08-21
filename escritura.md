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

>[!WARNING]
>Los `int` quieren decir que son enteros, por lo que no deben llevar punto decimal.

Estos métodos de escritura llevan como parámetro el valor que se desea escribir dentro del `DynamicBuffer`. Sin embargo, estos pueden ir sin argumento por si solo se
desea reservar memoria dentro del `DynamicBuffer` sin escribir un valor aún.
``` luau
local myBuff = DynamicBuffer.new(8)

myBuff:int16() -- Memoria reservada (2 bytes)
myBuff:int8(100)
```
>[!NOTE]
>No pasar un argumento en los métodos de escritura sigue reservando memoria dentro del buffer, y escribe un valor de 0 **por** defecto.

---
### Métodos de escritura de números con signo
|   Método   | Tamaño en bytes | Rango de valores |
| :---: | :---: | :---: |
| `:int8()` | 1 | -128 a 127 |
| `:int16()` | 2 | -32,768 a 32,767 |
| `:int32()` | 4 | -2,147,483,648 a 2,147,483,647 |

---
## Números sin signo
La forma en que se escriben valores numéricos sin signo (`unsigned`) dentro de un `DynamicBuffer` es la misma que con los números con signo: con el uso de métodos.

Los métodos para los números sin signo llevan el mismo nombre que los métodos vistos anteriormente, pero con una __u__ al inicio del nombre del método. Esta __u__ significa `unsigned`

``` luau
myBuff:uint8(255) -- Entero de 8 bits sin signo
myBuff:uint16()
myBuff:uint32(-100) -- Tiene un signo (negativo). No se puede
```
>[!NOTE]
> Cuando pasas como argumento un número con signo negativo a estos métodos, automáticamente los convierte a 0.

### Métodos de escritura de números sin signo
|   Método   | Tamaño en bytes | Rango de valores |
|    :---:   |      :---:      |      :---:       |
| `:uint8()` | 1 | 0 a 255 |
| `:uint16()` | 2 | 0 a 65,535 |
| `:uint32()` | 4 | 0 a 4,294,967,295 |

---
## Números flotantes
Los números flotantes son aquellos que poseen punto decimal. Ideales si dentro de tu juego manejas valores con decimales como dinero.

Para escribir valores flotantes dentro de un `DynamicBuffer`, usas los métodos `:float32()` y `:float64()`.
``` luau
local myBuff = DynamicBuffer.new(12)
myBuff:float32(3.1416)
myBuff:float64(9.987654321)
```
Aunque ambos métodos manejen valores flotantes, `:float64()` es el que mayor precisión tiene a la hora de trabajar con decimales.
>[!TIP]
>Tanto `:float32()` como `:float64()` pueden manejar valores negativos.

### Tamaño en bytes
* `:float32()`: 4 bytes y 7 dígitos decimales de precisión.
* `:float64()`: 8 bytes y 15-17 dígitos decimales de precisión.

---
El siguiente paso para aprender `DynamicBuffer` es la [Lectura de Datos](lectura.md).
