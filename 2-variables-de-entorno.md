# Variables de Entorno
### ¿Qué son las variables de entorno
# Variables dinámicas para un programa en ejecución. No dependen del programa en sí, sino del entorno, entonces se pueden usar en varios sitios y no solo en un lugar local.

### Para crear un contenedor con variables de entorno?

```
docker run -d --name <nombre contenedor> -e <nombre variable1>=<valor1> -e <nombre variable2>=<valor2>
```

### Crear un contenedor a partir de la imagen de nginx:alpine con las siguientes variables de entorno: username y role. Para la variable de entorno rol asignar el valor admin.

# docker run -d --name docker-entorno -e username=andres -e role=admin nginx:alpine

# CAPTURA CON LA COMPROBACIÓN DE LA CREACIÓN DE LAS VARIABLES DE ENTORNO DEL CONTENEDOR ANTERIOR

### Crear un contenedor con mysql:8 , mapear todos los puertos
# docker run -P -d --name docker-mysql mysql:8

### ¿El contenedor se está ejecutando?
# El contenedor no se está ejecutando.

### Identificar el problema
# Dice que se deben establecer una variable de entorno, y que se puede elegir de tres opciones que son: 
    - MYSQL_ROOT_PASSWORD
    - MYSQL_ALLOW_EMPTY_PASSWORD
    - MYSQL_RANDOM_ROOT_PASSWORD

### Eliminar el contenedor creado con mysql:8 
# docker rm docker-mysql

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
# docker run -P -d --name docker-mysql -e MYSQL_ROOT_PASSWORD=P@ssw0rd --env-file=./docker.env mysql:8

# CAPTURA CON LA COMPROBACIÓN DE LA CREACIÓN DE LAS VARIABLES DE ENTORNO DEL CONTENEDOR ANTERIOR


### ¿Qué bases de datos existen en el contenedor creado?
# Las 4 principales y que vienen por defecto: information_schema, performance_schema, sys y mysql.
