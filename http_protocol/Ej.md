# Buscando el método HTTP

A partir de los métodos HTTP vistos en la clase, analizar el siguiente URL [http://obscure-meadow-82990.herokuapp.com](http://obscure-meadow-82990.herokuapp.com) y encontrar la manera de enviar sus datos

- `nombre`
- `apellido`
- `email`

Se advierte que el sitio **NO** soporta el método `GET`, por lo que un intento de abrir dicho URL en el navegador devolverá un error del tipo (405) `Method Not Allowed` 

Para completar el ejercicio, se puede utilizar cualquier herramienta con el que se sienta más familiarizado, como ser:

- Utilizar una herramienta de línea de comandos como `curl`.
- Utilizar un cliente REST gráfico como `insomnia` o `postman`. (Recomendado)
- Programar las peticiones necesarias en cualquier lenguaje de su preferencia.

Sirvase de volver a leer el [enlace de apoyo](https://github.com/diegocrzt/diegocrzt.github.io/tree/master/http_protocol).

Recuerde que descubrir el **método** y el **formato** en el que se esperan los datos (nombre,apellido,email) es parte del ejercicio. Observe cuidadosamente las respuestas y las cabeceras (*headers*) HTTP retornadas por el servidor, así como las cabeceras que usted esté enviando.

Una vez que envíe sus datos correctamente, el servidor guardará dichos datos para luego retornar una respuesta HTTP con código 200 `OK` y un mensaje similar al siguiente pero con los datos que usted haya enviado.

```json
{
  "data": "Nombre Apellido - direccion@email.com",
  "status": "received"
}
```

Se consideraran las peticiones hasta las **23:59** del día **domingo, 24 de febrero de 2019**. 

**Importante**: En ocaciones el servidor suele apagarse para ahorrar recursos, pero se despierta segundos después de recibir una petición. Si aparecen errores del tipo `Timeout`, simplemente reintente la petición.
