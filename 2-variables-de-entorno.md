# Variables de Entorno

### ¿Qué son las variables de entorno

Las variables de entorno son valores dinámicos que pueden afectar el comportamiento de los procesos en un sistema operativo. Se utilizan para configurar el entorno en el que se ejecutan los programas y scripts.

### Para crear un contenedor con variables de entorno?

```
docker run -d --name <nombre contenedor> -e <nombre variable1>=<valor1> -e <nombre variable2>=<valor2>
```

### Crear un contenedor a partir de la imagen de nginx:alpine con las siguientes variables de entorno: username y role. Para la variable de entorno rol asignar el valor admin

```
docker run -d --name ejemplo1 -e username=usuario -e rol=admin nginx:alpine
```

```
docker exec ejemplo1 env
```

![variables](img/variables.png)

### Crear un contenedor con mysql:8 , mapear todos los puertos

```
docker run -d --name mysql -e MYSQL_ROOT_PASSWORD=mi_contraseña -p 3306:3306 mysql:8
```

### ¿El contenedor se está ejecutando?

Si se esta ejecutando

```
docker ps -a | Select-String mysql
```

### Identificar el problema

```
docker logs mysql
```

### Eliminar el contenedor creado con mysql:8

```
docker rm -f mysql
```

### Para crear un contenedor con variables de entorno especificadas

- Portabilidad: Las aplicaciones se vuelven más portátiles y pueden ser desplegadas en diferentes entornos (desarrollo, pruebas, producción) simplemente cambiando el archivo de variables de entorno.
- Centralización: Todas las configuraciones importantes se centralizan en un solo lugar, lo que facilita la gestión y auditoría de las configuraciones.
- Consistencia: Asegura que todos los miembros del equipo de desarrollo o los entornos de despliegue utilicen las mismas configuraciones.
- Evitar Exposición en el Código: Mantener variables sensibles como contraseñas, claves API, y tokens fuera del código fuente reduce el riesgo de exposición accidental a través del control de versiones.
- Control de Acceso: Los archivos de variables de entorno pueden ser gestionados con permisos específicos, limitando quién puede ver o modificar la configuración sensible.

Previo a esto es necesario crear el archivo y colocar las variables en un archivo, **.env** se ha convertido en una convención estándar, pero también es posible usar cualquier extensión como **.txt**.

```
docker run -d --name <nombre contenedor> --env-file=<nombreArchivo>.<extensión> <nombre imagen>
```

**Considerar**
Es necesario especificar la ruta absoluta del archivo si este se encuentra en una ubicación diferente a la que estás ejecutando el comando docker run.

### Crear un contenedor con mysql:8 , mapear todos los puertos y configurar las variables de entorno mediante un archivo

```
docker run -d --name mi_contenedor_mysql --env-file variables.env -p 3306:3306 mysql:8
```

![variables](img/variables2.png)

### ¿Qué bases de datos existen en el contenedor creado?

Cuenta con las siguientes base de datos:

- gatos
- information_schema
- mysql
- performance_schema
- sys

```
docker exec -it mysql mysql -u root -p -e "SHOW DATABASES;"
```
