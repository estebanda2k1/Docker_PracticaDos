# Variables de Entorno
### ¿Qué son las variables de entorno?

Valores dinámicos que se almacenan en el sistema operativo y que pueden afectar el comportamiento de los programas.

### Para crear un contenedor con variables de entorno

```
docker run -d --name <nombre contenedor> -e <nombre variable1>=<valor1> -e <nombre variable2>=<valor2>
```

### Crear un contenedor a partir de la imagen de nginx:alpine con las siguientes variables de entorno: username y role. Para la variable de entorno rol asignar el valor admin.

```
docker run -d --name contenedor_variables -e username=user -e rol=admin
```

# COMPLETAR

# CAPTURA CON LA COMPROBACIÓN DE LA CREACIÓN DE LAS VARIABLES DE ENTORNO DEL CONTENEDOR ANTERIOR
<img width="953" height="64" alt="image" src="https://github.com/user-attachments/assets/dc5c6616-db4c-49bd-addf-5c4bcf2c4a50" />

### Crear un contenedor con la imagen de mysql, mapear todos los puertos

# COMPLETAR
```
docker run -d --name contenedor_sql -p 5432:5432 mysql
```
### ¿El contenedor se está ejecutando?
No

### Identificar el problema
No funciono por dos razones, los puertos default para mysql son 3306, y segundo porque se necesita crear el contenedor con variables de entorno obligatorias, si se usa este comando, contenedor deberia funcionar de manera correcta:
```
docker run -d --name contenedor_sql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=12345 mysql
```

<img width="1102" height="205" alt="image" src="https://github.com/user-attachments/assets/1a5f2f92-5166-485b-b6ba-4aad30ae1a15" />

### Para crear un contenedor con variables de entorno especificadas
- Portabilidad: Las aplicaciones se vuelven más portátiles y pueden ser desplegadas en diferentes entornos (desarrollo, pruebas, producción) simplemente cambiando el archivo de variables de entorno.
- Centralización: Todas las configuraciones importantes se centralizan en un solo lugar, lo que facilita la gestión y auditoría de las configuraciones.
- Consistencia: Asegura que todos los miembros del equipo de desarrollo o los entornos de despliegue utilicen las mismas configuraciones.
- Evitar Exposición en el Código: Mantener variables sensibles como contraseñas, claves API, y tokens fuera del código fuente reduce el riesgo de exposición accidental a través del control de versiones.
- Control de Acceso: Los archivos de variables de entorno pueden ser gestionados con permisos específicos, limitando quién puede ver o modificar la configuración sensible.

### ¿Qué bases de datos existen en el contenedor creado?
Para observar que base de datos existen se ejecuto estos comandos:

Para entrar al comando del contenedor SQL:
```
docker exec -it contenedor_sql mysql -u root -p
```

Una vez ejecutado el contenedor y haber ingresado la contraseña anterior, se ejecuta este comando:
```
SHOW DATABASES;
```
<img width="360" height="244" alt="image" src="https://github.com/user-attachments/assets/5fd9158a-34df-464d-a092-992fa3910fc8" />
