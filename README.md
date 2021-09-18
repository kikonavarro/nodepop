# Nodepop
Práctica de NodeJS, Express y mongoDB del Bootcamp de Keepcoding

## Objetivo

- Desarrollar una API que se ejecutará en el servidor de un servicio de venta de artículos llamado Nodepop en el que hay tanto anuncios de compra como de venta y permite buscar por distintos criterios.
- La API debe hacer lo siguiente:
  - Listar los anuncios con sus filtros
  - Listar los tags existentes
  - Posibilidad de crear anuncios
- Los sistemas donde se desplegará la API utilizan bases de datos de MongoDB
## Inicializar

Descargamos el repositorio, por ejemplo con SSH o HTTPS:

```sh
git clone git@github.com:kikonavarro/nodepop.git
git clone https://github.com/kikonavarro/nodepop.git
```

Una vez lo tengamos abierto, instalamos las dependencias con:
```sh
npm install
```
## Inicializar la base de datos MongoDB

Para arrancar el servidor de `MongoDB` en MAC y LINUX nos situamos dentro de la carpeta donde tengamos instalado MongoDB y escribimos en la terminal:
 
```sh
./bin/mongod --dbpath ./data/db
```

Para inicializar la base de datos ejecutamos el siguiente script que nos borrará nuestra base de datos nodepopAnuncios y creará 2 anuncios.

```sh
npm run install_db
```
## Arrancar la aplicación
Ejecutamos con:
```sh
npm start
```
La URL donde se ejecuta el producto es:

http://localhost:3000/api/productos

## Filtrado de anuncios
Puedes filtrar los anuncios añadiendo parámetros especiales a la URL con el formato `?<query>=<valor>`

Ejemplos de parámetros de búsqueda son los siguientes:

- `nombre`: filtra por el nombre del artículo que busquemos.

  - Ejemplo: http://localhost:3000/api/anuncios/?nombre=bicicleta

- `precio`: tiene 4 filtros distintos que funcionan tanto en la vista http://localhost:3000/ como en http://localhost:3000/api/anuncios

  - `?precio=<valor->` muestra los anuncios que tegnan ese precio o más. (ejemplo http://localhost:3000/api/anuncios/?precio=50-)
  - `?precio=<-valor>` muestra los anuncios que tengan ese precio o menos. http://localhost:3000/api/anuncios/?precio=-50
  - `?precio=<valormin-valormax>` muestra los anuncios que estén en ese rango de precios. http://localhost:3000/api/anuncios/?precio=10-1000
  - `?precio=<valor>` muestra los anuncios con el precio igual al valor. http://localhost:3000/api/anuncios/?precio=50
  
- `tags`: permite filtrar los anuncios que tengan el tag indicado. Dentro de los posibles.
- `venta`: permite filtrar por anuncios de venta (=true), o anuncios de compra (=false)

## Listado de tags
Para obtener un listado de los `Tags` existentes basta con entrar en http://localhost:3000/api/productos/tags

## Crear un anuncio
Si queremos crear un anuncio habrá que usar un método **POST**, para ello podemos usar herramientas como **Postman**


## Vistas
Hemos usado el motor `EJS` para obtener una vista de los productos de nuestro servicio e incluso si filtramos en la URL con los mismos filtros detallados anteriormente debe funcionar.
