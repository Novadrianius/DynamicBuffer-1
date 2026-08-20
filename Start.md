# Primer paso hacia la pinche documentación de GitHub

Mi primer párrafo en MD

## Instalación
1. Ve a roblox.com/marketplace/models/dynamicbuffer-01
2. Descarga el modelo .rbxl.
3. Inserta el archivo en tu juego de Roblox.
4. Crea una carpeta dentro de ReplicatedStorage y llámala "Packages".
5. Inserta el módulo de DynamicBuffer dentro de Packages.

---

En un script de servidor, vamos a requerir el módulo de DynamicBuffer para poder utilizarlo.

``` luau
-- Server script
local DynamicBuffer = require(path.to.DynamicBuffer)
```

Para crear nuestro primer buffer dinámico, usaremos el método constructor (`.new()`) de DynamicBuffer y será guardado en una variable:
``` luau
local myBuffer = DynamicBuffer.new()
```
---
El método constructor `.new()` de DynamicBuffer lleva como único parámetro un número, el cual representa el tamaño inicial en bytes de nuestro buffer dinámico. Si lo dejas vacío (`nil`), o con un número menor o igual a cero, el buffer dinámico tomará un tamaño inicial de 4 bytes por default.

Si quisieras un buffer con un tamaño inicial de 8 bytes, simplemente pasas el número 8 como argumento en el método constructor `.new()`.
``` luau
local myBuff = DynamicBuffer.new(8) -- Tamaño inicial de 8 bytes
```
