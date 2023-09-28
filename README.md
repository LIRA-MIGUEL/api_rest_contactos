#Design Document: API REST CONTACTOS



##1. Descripcion 
Ejemplo de una API REST para gestionar contactos en una BD utilizando FastAPI. 

##.Objetivo 
Realizar un ejemplo de diseño de una API REST de tipo CRUD y su posterior codificacion utilizando el framework [FastAPI].(https://fastapi.tiangolo.com/)

##3.Diseño de la BD 
Para este ejemplo se utilizara gestor de base de datos. [SQLite3].(https://www.sqlite.org/index.html) con las siguientes tablas: 

|NO.|Campo            |Tipo    |Restriccion  |Descripcion                   |
|-- |-----------------|------- |------------ |----------------------------- |
|1  |id_contactos     |int     |Primary KEY  |Llave primaria de la tabla    |
|2  |nombre           |varchar |NOT NULL     |Nombre del usuario           |
|3  |primer_apellido  |varchar |NOT NULL     |Primer apellido del usuario   |
|4  |segundo_apellido |varchar |NOT NULL     |Segundo apellido del usuario  |
|5  |telefono          |varchar |NOT NULL     |Teléfono del usuario         |
|6  |correo_electronico|varchar|NOT NULL     |Correo electrónico del usuario (gmail)|

##3.2.Script 
```sql 
CREATE TABLE IF NOT EXISTS contactos (
    id_contacto        INT PRIMARY KEY NOT NULL,
    nombre             VARCHAR(100) NOT NULL,
    primer_apellido    VARCHAR(50) NOT NULL,
    segundo_apellido   VARCHAR(50) NOT NULL,
    telefono           VARCHAR(20) NOT NULL,
    correo_electronico VARCHAR(50) NOT NULL
);

```
##3.3.(temporal) JSON
[{
		"id_contacto": 1,
		"nombre": "dejah",
		"primer_apellido": "Thoris",
		"segundo_apellido": "carter",
		"email": "dejah@barsoon",
		"telefono": "12345"
	},

	{
		"id_contacto": 2,
		"nombre": "juan",
		"primer_apellido": "perez",
		"segundo_apellido": "lopez"
	}
]
## 5. Diseño de los métodos
### 5.1 GET - http://localhost:8000/

| No | Propiedad          | Detalle                                          |
|--- |------------------- |------------------------------------------------- |
| 1  | Description        | Endpoint raíz de la API                         |
| 2  | Summary            | Endpoint raíz                                    |
| 3  | Method             | GET                                             |
| 4  | Endpoint           | http://localhost:8000/                          |
| 5  | QueryParam         | NA                                              |
| 6  | PathParam          | NA                                              |
| 7  | DATA               | NA                                              |
| 8  | Versiones          | V1                                              |
| 9  | Status code        | 200 OK                                          |
| 10 | Response-Type      | application/json                                |
| 11 | Response           | {"version":"v1","message":"endpoint raiz","datatime":"21/9/23 10:16"} |
| 12 | Curl               | curl -X 'GET' 'http://localhost:8000/' -H 'accept: application/json' |
| 13 | Status code(error) | NA                                              |
| 14 | Response Type(error)| NA                                             |
| 15 | Response(error)    | NA                                              |
### 5.2 GET - Listar Contactos

| No | Propiedad          | Detalle                                       |
|--- |------------------- |---------------------------------------------- |
| 1  | Description        | Endpoint para istar contactos en la API       |
| 2  | Summary            | Endpoint para listar Contactos                |
| 3  | Method             | GET                                          |
| 4  | Endpoint           | http://localhost:8000/contactos              |
| 5  | QueryParam         | NA                                           |
| 6  | PathParam          | NA                                           |
| 7  | DATA               | NA                                           |
| 8  | Versiones          | V1                                           |
| 9  | Status code        | 200 OK                                       |
| 10 | Response-Type      | application/json                             |
| 11 | Response           | {"version":"v1","message":"listados con exito","datetime":"27/09/2023 10:16"} |
| 12 | Curl               | curl -X 'GET' 'http://localhost:8000/contactos' -H 'accept: application/json' |
| 13 | Status code(error) | NA                                           |
| 14 | Response Type(error)| NA                                           |
| 15 | Response(error)    | NA                                           |
### 5.3 GET - http://localhost:8000/contactos

| No | Propiedad          | Detalle                                             |
|--- |------------------- |---------------------------------------------------- |
| 1  | Description        | Endpoint para obtener datos                        |
| 2  | Summary            | Endpoint para listar                                |
| 3  | Method             | GET                                                |
| 4  | Endpoint           | http://localhost:8000/contactos                    |
| 5  | QueryParam         | NA|
| 6  | PathParam          | NA                                                 |
| 7  | DATA               | NA                                                 |
| 8  | Versiones          | V1                                                 |
| 9  | Status code        | 200 OK                                             |
| 10 | Response-Type      | application/json                                   |
| 11 | Response           | {"version":"v1","message":"datos odtenidos","datatime":"27/09/23 10:36"} |
| 12 | Curl               | curl -X 'GET' 'http://localhost:8000/?limit=10&offset=0&nombre=Juan' -H 'accept: application/json' |
| 13 | Status code(error) | 400                                                |
| 14 | Response Type(error)| application/json                                   |
| 15 | Response(error)    | {"version":"v1","message-error":"datos no listados","datatime":"21/9/27 10:16"} |
### 5.4 DELETE - http://localhost:8000/contactos/?id_contacto=
| No | Propiedad          | Detalle                                             |
|--- |------------------- |---------------------------------------------------- |
| 1  | Description        | Endpoint para eliminar un recurso de la API        |
| 2  | Summary            | Endpoint para eliminar un recurso                  |
| 3  | Method             | DELETE                                             |
| 4  | Endpoint           | http://localhost:8000/contactos/?id=1      |
| 5  | QueryParam         | id_contacto                                        |
| 6  | PathParam          | NA                                                 |
| 7  | DATA               | NA                                                 |
| 8  | Versiones          | V1                                                 |
| 9  | Status code        | 204 No Content                                     |
| 10 | Response-Type      | application/json                                   |
| 11 | Response           | {"version":"v1","message":"contacto eliminado","datatime":"27/09/23 9:36"} |
| 12 | Curl               | curl -X 'DELETE' 'http://localhost:8000/?id=1' -H 'accept: application/json' |
| 13 | Status code(error) | 400 Bad Request                                    |
| 14 | Response Type(error)| application/json                                   |
| 15 | Response(error)    | {"version":"v1","message-error":"no se encontro el dato que desea eliminar","datatime":"21/9/27 10:16"} |

### 5.5 PUT - http://localhost:8000/contactos/?id_contactos=

| No | Propiedad          | Detalle                                             |
|--- |------------------- |---------------------------------------------------- |
| 1  | Description        | Endpoint para actualizar recursos de la API        |
| 2  | Summary            | Endpoint para actualizar datos                     |
| 3  | Method             | PUT                                                |
| 4  | Endpoint           | http://localhost:8000/contactos/?id=1     |
| 5  | QueryParam         | id_contacto                                        |
| 6  | PathParam          | NA                                                 |
| 7  | DATA               | NA                                                 |
| 8  | Versiones          | V1                                                 |
| 9  | Status code        | 200 OK                                             |
| 10 | Response-Type      | application/json                                   |
| 11 | Response           | {"version":"v1","message":"Contacto Actualizado","datatime":"27/09/23 9:36"} |
| 12 | Curl               | curl -X 'DELETE' 'http://localhost:8000/?id=1' -H 'accept: application/json' |
| 13 | Status code(error) | 400 Bad Request                                    |
| 14 | Response Type(error)| application/json                                   |
| 15 | Response(error)    | {"version":"v1","message-error":"error al actualizar su contacto","datatime":"27/09/23 10:16"} |
### 5.3 POST - http://localhost:8000/contactos

| No | Propiedad          | Detalle                                             |
|--- |------------------- |---------------------------------------------------- |
| 1  | Description        | Endpoint para enviar datos a la API                |
| 2  | Summary            | Endpoint para enviar datos                         |
| 3  | Method             | POST                                               |
| 4  | Endpoint           | http://localhost:8000/contactos                    |
| 5  | QueryParam         | NA                                                 |
| 6  | PathParam          | NA                                                 |
| 7  | DATA               | {"id_contacto": int, "nombre": varchar, "apellido_paterno": varchar, "apellido_materno": varchar, "email": varchar, "telefono": varchar} |
| 8  | Versiones          | V1                                                 |
| 9  | Status code        | 201 Created                                        |
| 10 | Response-Type      | application/json                                   |
| 11 | Response           | {"version": "v1", "message": "Enviado con exito", "datatime": "27/09/23 9:36"} |
| 12 | Curl               | curl -X 'POST' 'http://localhost:8000/contactos' -H 'accept: application/json' -d '{"id_contacto": int, "nombre": string, "apellido_paterno": string, "apellido_materno": string, "email": string, "telefono": string}' |
| 13 | Status code(error) | 400 Bad Request                                    |
| 14 | Response Type(error)| application/json                                   |
| 15 | Response(error)    | {"version": "v1", "message-error": "error al enviar", "datatime": "21/9/27 10:16"} |
