# Temario

https://university.mongodb.com/exam/guide

## Referencia de documentación de MongoDB Server

https://docs.mongodb.com/manual

## Architecture guide

https://webassets.mongodb.com/_com_assets/collateral/MongoDB_Architecture_Guide.pdf

Suele entrar una consulta sobre

- Alta disponibilidad => Replica set
- Escalado horizontal => Sharding

## JSON y BSON

Los registros en MongoDB son denominados documentos (pares clave-valor) se almacenan en
formato BSON (serialización binario de JSON).

Nos puede entrar una consulta de por qué MongoDB usa BSON como almacenamiento interno

- Extiende los tipos de datos de JSON (para dar compatibilidad a los diferentes driver de MongoDB).

Nos pueden preguntar acerca de los tipos de datos

https://docs.mongodb.com/manual/reference/bson-types/

Los driver de MongoDB (y las shell) parsean los documentos BSON a los tipos de datos soportados
por los lenguajes de esos driver (JSON-JavaScript).

BSON <-> Java
BSON <-> Ruby
BSON <-> Node y las Shell, en este caso podemos escribir tanto en JSON como en JS

## ObjectId

MongoDB dispone de un campo único y obligatorio en todos sus documentos que es _id. Aunque se le
puede proporcionar valor, si no se especifica, Mongo le asigna un valor automaticamente de tipo ObjectId()

ObjectIds are small, likely unique, fast to generate, and ordered. ObjectId values are 12 bytes in length, consisting of:

a 4-byte timestamp value, representing the ObjectId's creation, measured in seconds since the Unix epoch
a 5-byte random value generated once per process. This random value is unique to the machine and process.
a 3-byte incrementing counter, initialized to a random value (este contador se inicia para las operaciones
                                                              en el mismo segundo)

- Garantiza que en entornos de escritura masiva no existan dos valores de _id idénticos (para evitar error
  or duplicidad).

## The Mongo Shell

```
mongosh --port <puerto> // opciones adicionales
```

### Caractéristicas fundamentales

- Acepta comandos de shell y métodos del lenguaje de consultas de MongoDB
- Ejecuta JS
- Ayudas habituales de shell (textos predictivos en el caso de mongosh)

### Comandos básicos de la shell

```
show dbs // devuelve las bases de dato
```

```
use <nombre-base-datos> // Para crear o conectarnos a una base de datos
```

Por ejemplo

use clinica // si no existe la base de datos 'reserva' su nombre

```
db // devuelve la base de datos en la que estamos
```

```
show collections // Devuelve las colecciones de esa base de datos (idem show tables)
```

### Operaciones básicas de administración

Para crear colecciones de manera explícita

```
db.createColletcion(<nombre-colección>) // Buena práctica cumplir identificadores JS
```
db.createCollection('pacientes')

```
db.<nombre-colección>.drop() // Eliminar una colección
```

```
db.dropDatabase() // Elimina la base de datos
```

### Métodos de colección

```
db.<nombre-colección>.metodo(args).metodo(args)
```

db.pacientes.insert({nombre: 'Lucía', apellidos: 'Pérez Gómez'})
db.pacientes.find()

## Esquema flexible en MongoDB (esquema dinámico o schemmaless)

- Los documentos no tienen campos obligatorios ni se definen su campos previamente (salvo _id)
- Documentos diferentes en la misma colección pueden tener campos diferentes o no tenerlos.
- Solamente el campo _id es obligatorio y debe ser único
- Diferentes documentos en la misma colección pueden tener distinto tipo de dato en los mismos campos.