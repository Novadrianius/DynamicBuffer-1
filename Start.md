# Primeros pasos hacia DynamicBuffer

@Author: chicharron703 / Novadrianius

## Ventajas de DynamicBuffer
* **Facilidad de escritura**: A diferencia de la librería `buffer` de Roblox. En `DynamicBuffer` no tienes que calcular ningún desplazamiento de memoria para escribir valores dentro del buffer. Es casi como manejar `table`.
  
* **Facilidad de lectura**: Con `DynamicBuffer` puedes leer y obtener los valores del buffer sin la necesidad de conocer el tipo de dato que está escrito en el buffer gracias al uso de índices.
  
* **Manejo de capacidad automática**: En la librería `buffer` tienes que definir un tamaño fijo para tu buffer. Con `DynamicBuffer` no tienes que preocuparte por el tamaño de tu buffer, pues este se ajusta de forma automática.

* **Optimización de ancho de banda**: Al manejar buffers, el ancho de banda de la red a la hora de usar `Remotes` es mucho más optimizado que mandar datos sin serializar.
  
* **Características adicionales**: Puedes conocer con facilidad cuál es la capacidad actual del buffer y cuánto espacio (en bytes) está siendo ocupado actualmente.

>[!WARNING]
>Hay información a considerar del por qué `DynamicBuffer` no podría reemplazar a la librería nativa de `buffer` a la hora de desarrollar por completo.

Aunque `DynamicBuffer` te permite manejar buffers de manera sencilla, si quieres aprovechar la máxima velocidad posible en el rendimiento de tus scripts, `buffer` sigue siendo la mejor opción.

---
## Instalación
1. Ve al modelo de [DynamicBuffer](https://create.roblox.com/store/asset/87263522449126/DynamicBuffer) en la página de Roblox.
2. Descarga el modelo y abre Roblox Studio.
3. Inserta el modelo en tu juego de Roblox.
4. Crea una carpeta dentro de ReplicatedStorage y llámala "Packages".
5. Inserta el módulo de DynamicBuffer dentro de Packages.

---
En un script (ya sea de cliente o de servidor), vamos a requerir el módulo de DynamicBuffer para poder utilizarlo.

``` luau
-- Server script
local DynamicBuffer = require(path.to.DynamicBuffer)
```
## Crear buffer dinámico
Para crear nuestro primer buffer dinámico, usaremos el método constructor (`.new()`) de DynamicBuffer y será guardado en una variable:
``` luau
local myBuffer = DynamicBuffer.new()
```
Este método retorna un `DynamicBuffer` y se guarda en la variable de `myBuffer`

---
El método constructor `.new()` de DynamicBuffer lleva como único parámetro un número, el cual representa el tamaño inicial en bytes de nuestro buffer dinámico.

Si quisieras un buffer con un tamaño inicial de 8 bytes, simplemente pasas el número 8 como argumento en el método constructor `.new()`.
``` luau
local myBuff = DynamicBuffer.new(8) -- Tamaño inicial de 8 bytes
```
>[!NOTE]
>No pasar un argumento en el método constructor `.new()`, o pasar un número menor o igual a cero terminará creando un `DynamicBuffer` con una capacidad de 4 bytes por defecto.

---
El siguiente paso para manejar DynamicBuffer es la [Escritura de Datos](escritura.md).
