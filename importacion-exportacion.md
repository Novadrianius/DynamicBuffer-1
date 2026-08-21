# Importación y Exportación
@author: chicharron703 / Novadrianius

Supongamos que queremos enviar nuestro buffer creado con `DynamicBuffer` por la red (desde el cliente hasta el servidor).

---
## :ExportBuffer()
Antes de mandar un buffer de `DynamicBuffer` por la red, necesitaremos usar el método `:ExportBuffer()`, el cual devuelve un buffer.

**LocalScript**
``` luau
local buff: buffer = myBuff:ExportBuffer()
```
`:ExportBuffer()` nos devuelve el buffer con los valores escritos desde el `DynamicBuffer`.

Para mandarlo por la red, primero exportamos el buffer y después lo mandamos desde un `RemoteEvent` o alguna instancia similar.

**LocalScript**
``` luau
local buff = myBuff:ExportBuffer()
RemoteEvent:FireServer(buff)
```

---
## :ImportBuffer()
Importar un buffer nos permitirá manejar un buffer enviado por la red como un `DynamicBuffer` de nuevo, __¡Siempre y cuando este sea compatible!__

En un script de servidor, recibiremos el buffer enviado desde el cliente y lo importaremos a nuestro `DynamicBuffer` con el uso del que creamos en un
`ModuleScript`

**Script**
``` luau
local myBuff = require(path.to.myBuff)

RemoteEvent.OnServerEvent:Connect(function(clientBuffer: buffer)
  -- ...
end)
```

El método `:ImportBuffer()` retorna dos valores: un `boolean` que dice si el buffer y el `DynamicBuffer` son compatibles, y un nuevo `DynamicBuffer`, el cual será
con el que se trabajará ahora.

**Script**
``` luau
local myBuff = require(path.to.myBuff)

RemoteEvent.OnServerEvent:Connect(function(clientBuffer: buffer)
  local success, newBuff: DynamicBuffer = myBuff:ImportBuffer(clientBuffer)
  if success then
    print(newBuff:GetLength())
  else
    warn "¡Buffer no compatible!"
  end
end)
```
>[!CAUTION]
>aunque `:ImportBuffer()` devuelva un `boolean` que confirme la compatibilidad, la seguridad para importar buffers a un `DynamicBuffer` todavía no es buena. Ten
>cuidado a la hora de importar buffers.

Esto quiere decir que aunque `DynamicBuffer` muestre que son compatibles, pueden ser buffers con valores distintos, pero con la misma memoria reservada.
