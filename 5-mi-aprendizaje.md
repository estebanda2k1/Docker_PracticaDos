# Mi aprehendizaje
Par mi aprehendizaje profesional lo que más me sirvió fue saber como se conectan los contenedores en función de las reds y que tipos de redes existen en Docker, a la vez experimentar como funciona Wordpress y su respectiva conexión a una base de datos, que es algo que nunca había manejado. Como se sabe el aprehendizaje autónomo es crucial pero tener este tipo de talleres como guía acelera bastante este proceso. Los comandos mas importantes que me guardo son las variabales y como estas cambian en funcion de la imagen que vayamos a usar como fue el caso de Wordpress que teniamos que enviar las variables de usuario de la imagen de mysql.

Considero que la práctica estuvo bien planteada, sin embargo el punto 3 debería estar antes del punto 2, debido que se necesita conocimientos referentes a la conexion de contenedores para poder elaborar los ejercicios planteados en el punto 2; como fue el uso de una red para conectar el mysql con el postgres, porque al momento de hacerlo sin redes no se podia crear la base de datos

## Gestión de Datos Confidenciales con Docker Secrets

Docker permite manejar información sensible (contraseñas, tokens, claves API) de manera segura usando **Docker Secrets**. Esta guía explica cómo funcionan y cómo implementarlos.

### 1. ¿Qué son los secretos en Docker?

- Un **Docker Secret** es un objeto seguro que almacena información sensible.
- Se mantiene **encriptado** en Docker Swarm (modo clúster).
- Solo los servicios que lo necesitan pueden acceder a él.
- No queda expuesto en la línea de comandos ni en contenedores normales si se usa correctamente.

### 2. Crear un secreto

Guardar una contraseña de base de datos:

```
echo "mi_contraseña_secreta" | docker secret create db_password -
```
