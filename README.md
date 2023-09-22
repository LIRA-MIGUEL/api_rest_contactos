#Design Document: API REST CONTACTOS



##1. Descripcion 
Ejemplo de una API REST para gestionar contactos en una BD utilizando FastAPI. 

##.Objetivo 
Realizar un ejemplo de diseño de una API REST de tipo CRUD y su posterior codificacion utilizando el framework [FastAPI].(https://fastapi.tiangolo.com/)

##3.Diseño de la BD 
Para este ejemplo se utilizara gestor de base de datos. [SQLite3].(https://www.sqlite.org/index.html) con las siguientes tablas: 

|NO.|Campo|Tipo|Restriccion|Descripcion|
|--|--|--|--|--|
|1|id_contactos|int|Primary KEY|Llave primaria de la tabla|

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
