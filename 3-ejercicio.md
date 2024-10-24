### Crear contenedor de Postgres sin que exponga los puertos. Usar la imagen: postgres:11.21-alpine3.17

```
docker run -d --name postgres -e POSTGRES_PASSWORD=123 postgres:11.21-alpine3.17
```

### Crear un cliente de postgres. Usar la imagen: dpage/pgadmin4

```
docker run -d --name pgadmin -e PGADMIN_DEFAULT_EMAIL=admin@local.com -e PGADMIN_DEFAULT_PASSWORD=123 -p 80:80 dpage/pgadmin4
```

La figura presenta el esquema creado en donde los puertos son:

- 80
- 5432
- 80

![Imagen](img/esquema-ejercicio3.PNG)

## Desde el cliente

### Acceder desde el cliente al servidor postgres creado

![LOGIN](img/login.png)

### Crear la base de datos info, y dentro de esa base la tabla personas, con id (serial) y nombre (varchar), agregar un par de registros en la tabla, obligatorio incluir su nombre

## Desde el servidor postgresl

### Acceder al servidor

```
docker exec -it postgres psql -U postgres
```

### Conectarse a la base de datos info

```
\c info
```

### Realizar un select *from personas

![consulta](img/consulta.png)
