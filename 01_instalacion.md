# Instalación

1. Descargar desde https://www.mongodb.com/try/download/community

2. Introducir en path la ruta C:\Program Files\MongoDB\Server\5.0\bin

3. Crear el directorio de ficheros

- Usar la configuración por defecto
    Crear C:\data\db

- Usar cualquier otro directorio
    mongod --dbpath <ruta>

4. Levantar servidor en local (en localhost y puerto 27017)

```
mongod // opciones --dbpath <ruta> | --port <puerto>
```

5. Apagar con CTRL + C o desde la shell use admin + db.shutdownServer()

# Conexiones

## CLI

- mongo
- mongosh https://www.mongodb.com/try/download/shell

## GUI

- Mongo Compass
- Otras alternativas de terceros
