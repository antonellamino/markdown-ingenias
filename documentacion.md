# Documentacion API de peliculas Trailerflix

Esta documentacion proporciona informacion sobre la API de peliculas TRAILERFLIX la cual tiene 7 endpoints que permiten realizar diferentes acciones asociadas a un
listado de series y peliculas con una serie de datos.

## Endpoints

### 1. Ruta raiz
**Metodo:** `GET`  
**Ruta:** `/localhost:3008/`  
**Descripcion:** Este endpoint retorna un mensaje de bienvenida.  
**Ejemplo de respuesta exitosa:**  
```html
    <h1> Bienvenida a la plataforma de series y peliculas TRAILERFLIX </h1>
```


### 2. Obtener el listado de peliculas y series
**Metodo:** `GET`  
**Ruta:** `/localhost:3008/catalogo`  
**Descripcion:** Este endpoint retorna un array de objetos en formato JSON con las peliculas y series disponibles en el catalogo con sus respectivos datos asociados.  
**Ejemplo de respuesta exitosa:**  
```json 
{
      "id": 3,
      "poster": "./posters/3.jpg",
      "titulo": "The Mandalorian",
      "categoria": "Serie",
      "tags": "Sci-Fi, Fantasía, Acción",
      "genero": "Ciencia Ficción",
      "resumen": "Ambientada tras la caída del Imperio y antes de la aparición de la Primera Orden, la Serie sigue los pasos de un pistolero solitario en las aventuras que protagoniza en los confines de la galaxia, donde no alcanza la autoridad de la Nueva República.",
      "temporadas": 2,
      "reparto": "Pedro Pascal, Carl Weathers, Misty Rosas, Chris Bartlett, Rio Hackford, Giancarlo Esposito",
      "trailer": "https://www.youtube.com/embed/aOC8E8z_ifw"
}
```

### 3. Obtener un elemento por ID
**Metodo:** `GET`  
**Ruta:** `/localhost:3008/trailer/:id`  
**Descripcion:** Este endpoint permite recuperar un elemento especifico a traves de su ID. Si se encuentra un elemento con el ID proporcionado, la API devolvera los datos "id", "titulo" y "trailer" de ese elemento. En caso contrario, la API respondera con un mensaje de error indicando que el elemento no se encontro.  
**Parametros de la URL:**  
- `id` (required): El ID del elemento que se desea obtener.  
- **Ejemplo de solicitud:**  
```
GET /localhost:3008/trailer/3
```
**Ejemplo de respuesta exitosa:**  
``` json
{
      "id": 3,
      "titulo": "The Mandalorian",
      "trailer": "https://www.youtube.com/embed/aOC8E8z_ifw"
}
```

### 4. Busqueda por titulo  
**Metodo:** `GET`  
**Ruta:** `/localhost:3008/titulo/:title`  
**Descripcion:** Este endpoint permite buscar titulos de peliculas o series en la plataforma TRAILERFLIX en funcion del titulo proporcionado como parametro en la URL, el cual puede ser un nombre del titulo parcial o total.
 La busqueda no es case sensitive.
Si se encuentra al menos un titulo coincidente con el parametro, la API respondera con una lista de resultados que incluyen los titulos encontrados. Si no se encuentra ninguna coincidencia, la API respondera con un codigo de error y un mensaje que indica que el titulo buscado no esta disponible en la plataforma.  
**Parametros de la URL:**  
- `title` (required): El titulo parcial o total del elemento que se desea obtener.  
- **Ejemplo de solicitud:**  
```
GET /localhost:3008/titulo/mandalorian  
```
**Ejemplo de respuesta exitosa:**  
``` json
{
      "id": 3,
      "poster": "./posters/3.jpg",
      "titulo": "The Mandalorian",
      "categoria": "Serie",
      "tags": "Sci-Fi, Fantasía, Acción",
      "genero": "Ciencia Ficción",
      "resumen": "Ambientada tras la caída del Imperio y antes de la aparición de la Primera Orden, la Serie sigue los pasos de un pistolero solitario en las aventuras que protagoniza en los confines de la galaxia, donde no alcanza la autoridad de la Nueva República.",
      "temporadas": 2,
      "reparto": "Pedro Pascal, Carl Weathers, Misty Rosas, Chris Bartlett, Rio Hackford, Giancarlo Esposito",
      "trailer": "https://www.youtube.com/embed/aOC8E8z_ifw"
}
```

### 5. Busqueda por categoria  
**Metodo:** `GET`  
**Ruta:** `/localhost:3008/categoria/:cat`  
**Descripcion:** Este endpoint permite recuperar buscar titulos en funcion de la categoria proporcionada como parametro en la URL.
Los valores validos son "serie" y "pelicula".
La API devolvera, segun el parametro, un listado de series o peliculas.
La busqueda no es case sensitive.
Si no se encuentra ningun titulo en la categoria enviada como parametro, la API respondera con un codigo de error, indicando que no existen titulos en esa categoria.
Si el parametro enviado por URL no es valido, la API tambien respondera con un codigo de error y un mensaje indicando que la categoria no es valida.  
**Parametros de la URL:**  
- `cat` (required): El nombre de la categoria de los elementos que se desean obtener.  
- **Ejemplo de solicitud:**  
```
GET /localhost:3008/categoria/serie  
```
**Ejemplo de respuesta exitosa:**  
``` json
{
      "id": 3,
      "poster": "./posters/3.jpg",
      "titulo": "The Mandalorian",
      "categoria": "Serie",
      "tags": "Sci-Fi, Fantasía, Acción",
      "genero": "Ciencia Ficción",
      "resumen": "Ambientada tras la caída del Imperio y antes de la aparición de la Primera Orden, la Serie sigue los pasos de un pistolero solitario en las aventuras que protagoniza en los confines de la galaxia, donde no alcanza la autoridad de la Nueva República.",
      "temporadas": 2,
      "reparto": "Pedro Pascal, Carl Weathers, Misty Rosas, Chris Bartlett, Rio Hackford, Giancarlo Esposito",
      "trailer": "https://www.youtube.com/embed/aOC8E8z_ifw"
}
```

### 6. Busqueda por nombre de reparto  
**Metodo:** `GET`  
**Ruta:** `/localhost:3008/reparto/:act`  
**Descripcion:** Este endpoint permite buscar titulos en funcion del nombre parcial o total de un miembro del reparto enviado como parametro en la URL.
La busqueda no es case sensitive.
Si se encuentra al menos un titulo que incluya al miembro del reparto buscado, la API respondera con un JSON con el titulo y el reparto de la o las coincidencias, en caso contrario, se respondera con un codigo de error y un mensaje de que no se encontraron coincidencias.  
**Parametros de la URL:**  
- `act` (required): Nombre parcial o total del miembro del reparto.  
- **Ejemplo de solicitud:**  
```
GET /localhost:3008/reparto/carl  
```
**Ejemplo de respuesta exitosa:**  
``` json
{
      "titulo": "The Mandalorian",
      "reparto": "Pedro Pascal, Carl Weathers, Misty Rosas, Chris Bartlett, Rio Hackford, Giancarlo Esposito"
}
```


### 7. Manejo de rutas no encontradas  
**Descripcion:** Este endpoint se utiliza para manejar las solicitudes de rutas que no coinciden con ningu endpoint definido en la API. Si se quiere acceder a una ruta no implementada, la API respondera con un error 404 y un mensaje que indica que no se encuentra la ruta solicitada.  
**Ejemplo de respuesta :**  
```json
{
    "error": "404",
    "message": "No se encuentra la ruta solicitada",
}
```
