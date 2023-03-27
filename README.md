# Nest comands

- dentro de src/ solo dejar los archivo app.modulo y main.ts

* para crear un nuevo proyecto
```
nest new pokedex

```
* servir contendio estatico
```
npm add @nestjs/serve-static
```
* crear un nuevo recurso 
```
 nest g res pokemon --no-spec
```
* agregar un prefijo global a nuestro backend.

agregamos en el main
```
 app.setGlobalPrefix('api')

```

## configurar mongo con docker compones

```js
version: '3'

services:
  db:
    image: mongo:5
    restart: allways
    ports:
      - 27017:27017
    environment:
      - ./mongo:/data/db

```

```
docker-compose up -d
```
### Conexion mongo con nest 

1. Comands
```
npm install --save @nestjs/mongoose mongoose
```
2. configuracion  
en app.module

```js

MongooseModule.forRoot('mongodb://localhost:27017/nest-pokemon'),   

```


### Creacion de nuestros Modelos  de Mongo

1. una ves creadas configuramos en el module del componente

```js

  imports: [
    MongooseModule.forFeature([
      {
        name: Pokemon.name,
        schema: PokemonSchema,
      },
    ]),
  ],
```
