
# API_Rest que gestiona una base de datos de incidencias - Realizada en framework Laravel

Guía de Consultas HTTP APIRest Incidencias - Apache2 - Base de datos en servidor XAMP - MySQLWorbench 8.0 - DWES05
En este archivo encontrarás las consultas HTTP básicas necesarias para completar la Tarea Evaluativa 1 de la Unidad Didáctica 5 de DWES. Esta API Rest esta basada en una aplicación de Incidencias, en la que podrás realizar operaciones CRUD sobre las incidencias de una empresa.

🔍 ¿Qué puedes hacer con esta coleccion?
Con esta colección, podrás ejecutar las operaciones básicas de un sistema REST para gestionar Incidencias de una empresa. Entre las operaciones disponibles, encontrarás:

Recuperar la información de todas las incidencias: Verás la lista completa de incidencias que se han genrado en la empresa.

Consultar una incidencia específica por su ID: Obtendrás los detalles de una incidencia concreta.

Insertar una nueva incidencia: Podrás añadir una nueva incidencia a la base de datos de Incidencias.

Modificar una incidencia existente: Actualiza el contenido de una incidencia.

Eliminar un post: Elimina una incidencia de la Base de Datos de forma definitiva.

🌟 Estructura del Ejemplo
Cada operación de esta plantilla cuenta con instrucciones detalladas y ejemplos de cómo enviar y recibir los datos en formato JSON. Solo necesitas hacer clic en Send en cada solicitud para ejecutarla y ver los resultados en tiempo real.

💡 Consejo: Usa el archivo para familiarizarte con las consultas que deberás implementar y personalizar en tu propio servicio en la tarea evaluativa. Cada solicitud incluye una descripción paso a paso para ayudarte a entender cómo funcionan las operaciones CRUD en una API RESTful.

﻿

GET
1: Recibir todas las incidencias - getAll
http://localhost:8000/api/public/post/get
Esta solicitud GET obtiene una lista de todos las incidencias disponibles en el sistema.

Caso de uso: Al pulsar enviar debería devolver la información de todas las incidencias disponibles. En caso de error devolvera codigos 404 o 500

﻿

GET
2: Recibir una incidencia por su id - getById
http://localhost:8000/api/public/post/get/04
Esta solicitud GET obtendría una incidencia específica basado en su ID.

Caso de uso: Si se cambia el valor de {{id}} en la URL al ID de la incidencia que quieres consultar y debería devolver los detalles de esta incidencia en concreto. Si no lo encuentra dara error 406.

﻿

POST
3: Crear incidencia nueva - createIncidencia
http://localhost:8000/api/public/post/create
Esta solicitud POST crearía una nueva incidencia en el sistema.

Caso de uso: En este caso, en el cuerpo de la solicitud se recibiría un JSON con los campos 'idTrabajador', 'hora', 'idInstalacion', 'descripcion' que contendrían los datos necesarios para crear una nueva incidencia que se quiera crear. Se recibira la incidencia introducida junto que el numero de incidencia creado. Si no se consigue crear generaria el error 500.

﻿

Body
raw (json)
json
{
    "idTrabajador":102,
    "idInstalacion":203, 
    "hora":"13:00"
    
}
PUT
4: Actualizar incidencia por su id - updateIncidencia
http://localhost:8000/api/public/post/update/8
Esta solicitud PUT actualiza una incidencia existente en el sistema basándose en su ID.

Caso de uso: Si se cambia el valor de {{id}} al ID de la incidencia que quieres actualizar, editando 'idTrabajador', 'idInstalacion', 'hora' y 'descripcion' en el cuerpo de la solicitud con los valores nuevos que se han de modificar en el contenido de esta incidencia en concreto. En caso de que no encuentre la incidencia generaria un error 406.

﻿

Body
raw (json)
json
{
    "idTrabajador":101,
    "idInstalacion":201, 
    "hora":"00:00",
    "descripcion":"CILINDRO ROTO"
}
DELETE
5: Borrar incidencia por su id - deleteIncidencia
http://localhost:8000/api/public/post/delete/8
Esta solicitud DELETE borra una incidencia existente en el sistema basándose en su ID.

Caso de uso: Si se cambia el valor de {{id}} al ID de la incidencia que quieres borrar, se borrará la incidencia en concreto y se recibirá el id de la incidencia borrada. En caso de que no encuentre la incidencia generaria un error 406.

﻿

GET
1: Recibir todos los Trabajadores - getAll
http://localhost:8000/api/public/post/trabajador/get
Esta solicitud GET obtiene una lista de todos los trabajadores disponibles en el sistema.

Caso de uso: Al pulsar enviar debería devolver la información de todos los trabajadores disponibles. En caso de error devolvera codigos 404 o 500

﻿

GET
2: Recibir un trabajador por su id - getById
http://localhost:8000/api/public/post/trabajador/get/101
Esta solicitud GET obtendría un trabajador específico basado en su ID.

Caso de uso: Si se cambia el valor de {{id}} en la URL al ID del trabajador que quieres consultar (100-199) y debería devolver los detalles del trabajador en concreto. Si no lo encuentra dara error 406.

﻿

POST
3: Crear trabajador nuevo - createTrabajador
http://localhost:8000/api/public/post/trabajador/create
Esta solicitud POST crearía un nuevo trabajador en el sistema.

Caso de uso: En este caso, en el cuerpo de la solicitud se insertaria un JSON con los campos, "idTrabajador", "nombreTrabajador", "apellido1", "apellido2", "dni", "direccion", "telefono", "email", que contendrían los datos necesarios para crear un nuevo trabajador que se quiera crear. Se recibira los datos del trabajador creado. Si no se consigue crear generaria el error 500.

﻿

Body
raw (json)
json
{
    "idTrabajador":104,
    "nombreTrabajador":"Pedro",
    "apellido1":"Fernandez",
    "apellido2":"Murillo",
    "dni":"44444444R",
    "direccion":"Calle cubo 3 4-A",
    "email":"CILINDRO@ROTO.COM",
    "telefono":"666777788"
}
PUT
4: Actualizar trabajador por su id - updateTrabajador
http://localhost:8000/api/public/post/trabajador/update/104
Esta solicitud PUT actualiza un trabajador existente en el sistema basándose en su ID.

Caso de uso: Si se cambia el valor de {{id}} al ID del trabajador que quieres actualizar, editando los datos del body abajo mostrado con los valores nuevos que se han de modificar en el contenido del trabajador en concreto. En caso de que no encuentre el trabajador generaria un error 406.

﻿

Body
raw (json)
json
{
    "nombreTrabajador":"PEDRO",
    "apellido1":"Fernandez",
    "apellido2":"Murillo",
    "dni":"44444444R",
    "direccion":"Calle cubo 3 4-A",
    "email":"CILINDRO@ROTO.COM",
    "telefono":"000000000"
}
DELETE
5: Borrar trabajador por su id - deleteTrabajador
http://localhost:8000/api/public/post/trabajador/delete/104
Esta solicitud DELETE borra un trabajador existente en el sistema basándose en su ID.
Caso de uso: Si se cambia el valor de {{id}} al ID del trabajador que quieres borrar, se borrará el trabajador en concreto y se recibirá el id del trabajador borrado. En caso de que no encuentre el trabajador generaria un error 406.
