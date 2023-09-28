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
