### Crear contenedor de Postgres sin que exponga los puertos. Usar la imagen: postgres:15-alpine3.21
```
docker run -d --name contenedor_postgres -e POSTGRES_USER=admin -e POSTGRES_PASSWORD=12345 -e POSTGRES_DB=BaseUno postgres:15-alpine3.21
```

### Crear un cliente de postgres. Usar la imagen: dpage/pgadmin4

```
docker run -d --name contenedor_pgadmin4 -e PGADMIN_DEFAULT_EMAIL=admin@admin.com -e PGADMIN_DEFAULT_PASSWORD=12345 -p 8080:80 dpage/pgadmin4
```

La figura presenta el esquema creado en donde los puertos son:
- a: 8080
- b: 80
- c: 5432

![Imagen](esquema-2-ejercicio.PNG)

## Desde el cliente
### Acceder desde el cliente al servidor postgres creado.
<img width="1599" height="525" alt="image" src="https://github.com/user-attachments/assets/20c55544-2714-4b4c-89ac-7b3ec5830f18" />

### Crear la base de datos info, y dentro de esa base la tabla personas, con id (serial) y nombre (varchar), agregar un par de registros en la tabla, obligatorio incluir su nombre.
<img width="303" height="427" alt="image" src="https://github.com/user-attachments/assets/a9f14dba-e302-48ac-8ec0-08790ef7d907" />

Se uso el siguiente comando en sql:
```
CREATE TABLE personas (
    id SERIAL PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL
);
INSERT INTO personas (nombre) VALUES 
('Esteban Gómez'),
('Juan Pérez');
```

## Desde el servidor postgresl
### Acceder al servidor
Para acceder al servidor se creó una red para ambos contenedores:
```
docker network create red_postgres
```
### Conectarse a la base de datos info
Se ingresa las credenciales del contenedor postgres creados anteriormente:

<img width="728" height="453" alt="image" src="https://github.com/user-attachments/assets/153499b8-d895-475c-9111-85aa64600ce4" />

### Realizar un select *from personas
# AGREGAR UNA CAPTURA DE PANTALLA DEL RESULTADO

<img width="1251" height="412" alt="image" src="https://github.com/user-attachments/assets/b89f866a-6825-4339-82da-be5fb17373ec" />
