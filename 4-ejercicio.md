## Esquema para el ejercicio
![Imagen](esquema-4-ejercicio.PNG)

### Crear la red
```
docker network create net-wp
```

### Crear el contenedor mysql a partir de la imagen mysql:8, configurar las variables de entorno necesarias
```
docker run -d --name contenedor_mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=12345 -e MYSQL_DATABASE=base_wordpress -e MYSQL_USER=admin -e MYSQL_PASSWORD=admin123 --network net-wp mysql:8
```
### Crear el contenedor wordpress a partir de la imagen: wordpress, configurar las variables de entorno necesarias
```
docker run -d --name contenedor_wordpress -p 8080:80 -e WORDPRESS_DB_HOST=contenedor_mysql:3306 -e WORDPRESS_DB_USER=admin -e WORDPRESS_DB_PASSWORD=admin123 -e WORDPRESS_DB_NAME=base_wordpress --network net-wp wordpress
```

De acuerdo con el trabajo realizado, en el esquema del ejercicio el puerto a es 8080

Ingresar desde el navegador al wordpress y finalizar la configuración de instalación.
<img width="1582" height="779" alt="image" src="https://github.com/user-attachments/assets/84e3829e-7d75-4459-8f8b-44244c0977d3" />


Desde el panel de admin: cambiar el tema y crear una nueva publicación.


Ingresar a: http://localhost:8080/ 
recordar que a es el puerto que usó para el mapeo con wordpress
# COLOCAR UNA CAPTURA DEL SITO EN DONDE SEA VISIBLE LA PUBLICACIÓN.
<img width="1599" height="802" alt="image" src="https://github.com/user-attachments/assets/93b1bb97-13de-4f43-9495-8be4bb5303cf" />


### Eliminar el contenedor wordpress
```
docker rm -f contenedor_wordpress
```

### Crear nuevamente el contenedor wordpress
Ingresar a: http://localhost:8080/ 
recordar que a es el puerto que usó para el mapeo con wordpress

### ¿Qué ha sucedido, qué puede observar?
Se puede observar lo que he hecho debido a que se ingreso con las mismos atributos, sin embargo el rol de administrador no se refleja:

<img width="1599" height="614" alt="image" src="https://github.com/user-attachments/assets/9979b624-8695-4700-8f1b-8ca7b7faa701" />

