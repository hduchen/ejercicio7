# Pasos 

* Creamos el yml

* Ejecutamos comando para levantar

```
$   docker-compose -f docker-compose-jobvacancy.yml up

```

* Ejecutamos comando para ver contenedores
```
$   docker ps
```
* Corren dos contenedores 
    * ej7_web_1
    * ej7_db_1

* las imagenes corresponde con los contenedores
    *  nicopaez/jobvacancy-ruby:1.3.0  --> ej7_web_1
    *  postgres:14.4-alpine --> ej7_db_1

* Descripcion del yml

services: Indica arbols de servicio
  web: Servicio Web
    image: nicopaez/jobvacancy-ruby:1.3.0 --> es de donde se toma la imagen para crearla
    links: hace referenci
      - db 
    ports: --> setea puertos de de puerto y host del contenedor
      - "3000:3000"
    environment: -->indica variables de enterno , en este caso la BD que esta linqueada
      PORT: "3000"
      RACK_ENV: "production"
      DATABASE_URL: "postgres://postgres:Passw0rd!@db:5432/postgres"
    depends_on:
      - db
  db: Define un servio de BD
    image: postgres:14.4-alpine ,--> es de donde se toma la imagen para crearla
    environment: indica variables de enterno 
      POSTGRES_PASSWORD: Passw0rd!