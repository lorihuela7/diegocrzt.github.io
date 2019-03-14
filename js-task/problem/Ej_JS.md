# Listado de Tareas - Introduciendo JavaScript

El objetivo de éste trabajo práctico es dar dinamismo a la página del listado de tareas vista en el TP anterior.

Para ello, usaremos el API `https://task-backend-fpuna.herokuapp.com/tasks/` publicado en internet, el cuál provee servicios para añadir / listar / editar y borrar tareas con los métodos `POST` / `GET` / `PUT` y `DELETE` respectivamente.

Se pueden obtener los archivos fuentes necesarios para éste trabajo [aquí](./).

Lo que se debe hacer es completar el fichero `todolist.js` añadiendo la lógica necesaria para permitir el funcionamiento de la página en los métodos, indicados en el enunciado más abajo, usando las funciones descriptas en clases.

> El fichero `ajax.js` no necesita ser modificado, ya contiene todas las funciones necesarias para hacer llamadas AJAX con los métodos `GET`, `POST`, `PUT` y `DELETE`. Sin embargo, `DEBE` ser leido para entender su funcionamiento y forma de uso.

## Pre-requisitos

* Leer el soporte dado en clases y/o las referencias(al final de la página) para dar dinamismo a la página listado de tareas usando JavaScript.
* Leer y entender el código proveído [aquí](./), en ambos archivos [`ajax.js`](./ajax.js) y [`todolist.js`](./todolist.js).
* Retomar el código del último trabajo práctico desarrollado(El de moficiación CSS) y agregar los archivos del punto anterior en un directorio `js` y colocar las siguientes etiquetas al final del cuerpo de la página (el orden es importante):

```html
<script type="text/javascript" src="js/ajax.js" async></script>
<script type="text/javascript" src="js/todolist.js" async></script>
```

## Funcionamiento de la API

El servicio publicado provee todo lo que se necesita para listar, agregar, editar y borrar tareas.
En éste [link](https://documenter.getpostman.com/view/2543680/S17kyrCZ), se puede consultar como realizar las llamadas a cada método del API.

También se proveen tres ficheros para usar con postman, insomnia o algún otro cliente REST

[Fichero genérico](tasks_backend.har)

[Fichero para insomnia](tasks_backend_insomnia.json)

[Fichero para postman](tasks_backend_postman.json)

Estos ficheros pueden importarse en postman o insomnia y sirven solo a modo de documentar y probar la API.

## Haciendo una llamada usando la técnica AJAX(JavaScript) hacia la API

Hemos visto en clases, que ésto se hace usando el objeto `XMLHttpRequest`. Sin embargo, para que la llamada al API sea más fácil, podés usar las funciones que se encuentran en el archivo `ajax.js`.

Aquí un ejemplo, para hacer una llamada `POST` al API, donde `f1` y `f2` son funciones dentro del programa y `param` es un objeto que se envía como parámetro.

```javascript 1.8
const API_URL = 'https://task-backend-fpuna.herokuapp.com/';
Ajax.sendPostRequest(API_URL, param, MediaFormat.JSON, (value) => f1(value), (code) => f2(code, 'La tarea no ha podido ser añadida.'), true);
```

_* Para saber como enviar otros métodos no te olvides de consultar el código del archivo._

_** Ante alguna duda sobre las llamadas REST consultar la [documentación](https://documenter.getpostman.com/view/2543680/S17kyrCZ) del API para saber como se debe hacer la invocación a cada método._

## Añadiendo JavaScript

* ITEM 0: Dentro de la función `document.onreadystatechange` que es leída una vez que la página se ha cargado, llama al API con el método `GET` para recuperar la lista de tareas existentes. [más detalles](js/todolist.js#L32-L36)
* ITEM 1: Dentro de la función `addTask` llamar al API con el método `POST` para crear una nueva tarea. [más detalles](js/todolist.js#L82-L88).
* ITEM 2: Dentro de la función `editTask` llamar a la API con el método `PUT` cuando la descripción de la tarea es modificada. [más detalles](js/todolist.js#L186-L193).
* ITEM 3: Dentro de la función `addOnChangeEvent`, en el evento `onchange` del checkbox, recuperar el nuevo valor del estado de la tarea, (si el checkbox está marcado significa que la tarea está terminada, sino, sigue pendiente) y colocar la tarea entre la lista de tareas que corresponda (tareas completadas o tareas pendientes). Una vez hecho ésto, llamar al API con el método `PUT` para guardar el nuevo estado de la tarea. [más detalles](js/todolist.js#L109-L115).
* ITEM 4: Dentro de la función `removeTaskFromList`, eliminar la tarea en cuestión del DOM HTML.
[más detalles](js/todolist.js#L240).
* ITEM 5: Dentro de la función `removeTask`, llamar al API con el método `DELETE` para borrar la tarea del servidor. [más detalles](js/todolist.js#L249-L254).
* _Bonus!_ ITEM 6: Agrega un elemento en la página HTML para mostrar los mensajes de error, y desde la función `showError()` hacer visible o invisible el elemento para mostrar el texto de error. El error debe mostrarse solo por 5 segundos, luego de ésto, debe desaparecer. Pueden utilizarse las clases css `error-bar`, `hide-bar` y `show-bar` en el archivo de estilos. [más detalles](js/todolist.js#L46-L48).
* _Bonus!_ ITEM 7: Agrega un nuevo botón a cada tarea que la permita `CANCELAR`. Para ello, debe escribir el HTML requerido y todas las funciones JavaScript necesarias. Tener en cuenta que, no se puede pasar del estado `CANCELADO` a `TERMINADO` o de `TERMINADO` a `CANCELADO` y recoradr llamar la API para actualizar el estado de la tarea en el servidor.

### Criterios

* Completa las funciones solicitadas para que la página sea funcional usando los [métodos HTTP](../../http_protocol/README.md) vistos en las clases anteriores y la API proveída.
* No comprimas el archivo JS.
* No deben aparecer errores a causa del código en la consola del navegador al cargar la página.
* El repositorio debe contener el archivo HTML, CSS y los archivos JS modificados con las funciones solicitadas, y la applicación debe estar deployada usando github pages.
* La información del estudiante junto con los enlaces al repositorio y la página `DEBEN` ser enviados antes del `miércoles 20 de marzo de 2019` a las `23:59:59` por medio del siguiente [formulario](https://goo.gl/forms/UG92suQTIoucEC542).

## Consideraciones Adicionales

* **NO** se puede utilizar jQuery o ninguna otra librería, sólo JavaScript.
* Dado que el API es compartido entre todos los estudiantes, deben tener en cuenta que tareas pueden ser añadidas, borradas o editadas por otros usuarios.
* Es importante completar éste TP porque los enunciados siguientes se basaran sobre ésta misma aplicación.