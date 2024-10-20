## Esquema para el ejercicio
![Imagen](img/esquema-ejercicio5.PNG)

### Crear la red
# docker network create net-wp -d bridge

### Crear el contenedor mysql a partir de la imagen mysql:8, configurar las variables de entorno necesarias
# docker run -d --name docker-mysql2 -e MYSQL_ROOT_PASSWORD=P@ssw0rd -e MYSQL_DATABASE=database -e MYSQL_USER=user -e MYSQL_PASSWORD=P@ssw0rd mysql:8
# docker network connect net-wp docker-mysql2

### Crear el contenedor wordpress a partir de la imagen: wordpress, configurar las variables de entorno necesarias
# docker run -d --name docker-wordpress -e WORDPRESS_DB_HOST=docker-mysql2 -e WORDPRESS_DB_USER=user -e WORDPRESS_DB_PASSWORD=P@ssw0rd -e WORDPRESS_DB_NAME=database -p 8080:80 wordpress 
# docker network connect net-wp docker-wordpress

De acuerdo con el trabajo realizado, en la el esquema de ejercicio el puerto a es **8080**

Ingresar desde el navegador al wordpress y finalizar la configuración de instalación.
# COLOCAR UNA CAPTURA DE LA CONFIGURACIÓN

Desde el panel de admin: cambiar el tema y crear una nueva publicación.
Ingresar a: http://localhost:9300/ 
recordar que a es el puerto que usó para el mapeo con wordpress
# COLOCAR UNA CAPTURA DEL SITO EN DONDE SEA VISIBLE LA PUBLICACIÓN.

### Eliminar el contenedor wordpress
# docker stop docker-wordpress
# docker rm docker-wordpress

### Crear nuevamente el contenedor wordpress
Ingresar a: http://localhost:9300/ 
recordar que a es el puerto que usó para el mapeo con wordpress

### ¿Qué ha sucedido, qué puede observar?
# No se muestra nada, la pantalla está en blanco. Incluso se puso al nuevo contenedor de wordpress, en la red que estaba antes de ser eliminado, pero no se ve nada.





