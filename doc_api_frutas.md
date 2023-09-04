# Documentacion de la API RESTful de frutas

Documentacion de la API RESTful de frutas. Esta API proporciona el acceso a una coleccion de datos de frutas, permitiendo realizar operaciones CRUD.

## Sumario

- [Documentacion de la API RESTful de frutas](#documentacion-de-la-api-restful-de-frutas)
  - [Sumario](#sumario)
    - [1. OBtener coleccion de frutas](#1-obtener-coleccion-de-frutas)
    - [2. Agregar fruta](#2-agregar-fruta)
    - [3. Modificar fruta](#3-modificar-fruta)
    - [4. ELiminar una fruta](#4-eliminar-una-fruta)
  - [Tabla representativa de endpoints con sus respectivas rutas](#tabla-representativa-de-endpoints-con-sus-respectivas-rutas)
  - [Diagrama de flujo representativo de la interaccion de un cliente con la API](#diagrama-de-flujo-representativo-de-la-interaccion-de-un-cliente-con-la-api)

**URL base:** `http://localhost:3008/api/v1/`  

Para utilizar la API, se puedem realizar solicitudes a la URL base mencionada anteriormente utilizando los siguientes metodos HTTP:

- **GET**: Para recuperar informacion de las frutas.  
- **POST**: Para agregar una nueva fruta a la coleccion.  
- **PUT**: Para actualizar la informacion de una fruta existente en la coleccion.
- **DELETE**: Para eliminar una fruta de la coleccion.


### 1. OBtener coleccion de frutas
**Metodo:** `GET`  
**Ruta:** `/localhost:3008/api/v1/frutas`  
**Descripcion:** Este endpoint retorna la coleccion de frutas.  
- Ejemplo de solicitud:
    ```
    GET http://localhost:3008/api/v1/frutas
    ```


### 2. Agregar fruta
**Metodo:** `POST`  
**Ruta:** `/localhost:3008/api/v1/frutas`  
**Descripcion:** Este endpoint agrega una fruta a la coleccion.  
**Ejemplo del cuerpo del mensaje:**   
```json
{
    "id": 100,
    "imagen": "🍌",
    "nombre": "Bananas brasileras",
    "importe": 350,
    "stock": 55
}
```
  - Ejemplo de solicitud:
    ```
    POST http://localhost:3008/api/v1/frutas
    ```


### 3. Modificar fruta
**Metodo:** `PUT`  
**Ruta:** `/localhost:3008/api/v1/frutas/:id`  
**Descripcion:** Este endpoint modifica la fruta con el ID enviado como parametro en caso de que exista. Caso contrario, se devuelve un mensaje de error al actualizar.  
**Ejemplo del cuerpo del mensaje:**     
```json
{
    "id": 110,
    "imagen": "🍌",
    "nombre": "Bananas argentinas",
    "importe": 350,
    "stock": 100
}
```
 - Ejemplo de solicitud:
    ```
    PUT http://localhost:3008/api/v1/frutas/:id
    ```

### 4. ELiminar una fruta  
**Metodo:** `DELETE`  
**Ruta:** `/localhost:3008/api/v1/frutas/:id`  
**Descripcion:** Este endpoint elimina una fruta con el id enviado por parametro en la URL en caso de que exista y se muestra un mensaje de exito, caso contrario se retorna un mensaje de error.  
 - Ejemplo de solicitud:
    ```
    DELETE http://localhost:3008/api/v1/frutas/:id
    ```

## Tabla representativa de endpoints con sus respectivas rutas
| METODO | RUTA                                     |
| ------ | -----------------------------------------|
| GET    | `/localhost:3008/api/v1/frutas`          |
| POST   | `/localhost:3008/api/v1/frutas`          |
| PUT    | `/localhost:3008/api/v1/frutas/:id`      |
| DELETE | `/localhost:3008/api/v1/frutas/:id`      |

## Diagrama de flujo representativo de la interaccion de un cliente con la API
::: mermaid
graph TD;
  subgraph "Cliente";
    A[Cliente] -->|Realiza solicitudes HTTP| B[API de Frutas];
  end
  subgraph "API de Frutas";
    B -->|Accede a datos de frutas| D[Base de Datos de Frutas];
  end
  :::