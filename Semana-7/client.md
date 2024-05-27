# Tarea en clase semana 8
## Creación de la tabla
```
CREATE TABLE client(
id SERIAL,
nui VARCHAR (100) NOT NULL,
fullname VARCHAR (100) NOT NULL,
phone VARCHAR (10),
type_of_client VARCHAR (100) DEFAULT 'Basic',
city VARCHAR (100),
credit_limit DECIMAL (7,2),
UNIQUE (nui),
PRIMARY KEY (id)
);

```
<img src="C"/>
###Inserción de datos

```
INSERT INTO client (nui, fullname, phone, type_of_client, city, credit_limit)
VALUES 
    ('1712345678', 'Juan Perez', '0987654321', 'Basic', 'Quito', 1000.00),
    ('0912345670', 'Maria Garcia', '0998765432', 'Premium', 'Guayaquil', 1500.50),
    ('0301234562', 'Carlos Rodriguez', '0976543210', 'Basic', 'Cuenca', 2000.75),
    ('1319876541', 'Ana Martinez', '0965432109', 'Premium', 'Manta', 1800.25),
    ('0123456781', 'Pedro Sanchez', '0954321098', 'Basic', 'Quito', 1200.00),
    ('2409876543', 'Laura Hernandez', '0943210987', 'Premium', 'Guayaquil', 1700.00),
    ('0512345678', 'Luis Gomez', '0932109876', 'Basic', 'Cuenca', 2200.00),
    ('1209876542', 'Diana Castro', '0921098765', 'Premium', 'Manta', 1900.50),
    ('0901234567', 'Gabriel Velez', '0910987654', 'Basic', 'Quito', 1300.25),
    ('0712345678', 'Paola Alvarez', '0909876543', 'Premium', 'Guayaquil', 1600.75);
```
###Inserción de nuevos datos con el campo "phone" en nulo

```
INSERT INTO client (nui, fullname, phone, type_of_client, city, credit_limit)
VALUES 
    ('2012345678', 'Andrés Mendoza', NULL, 'Basic', 'Quito', 1100.00),
    ('2112345670', 'Elena Ramirez', NULL, 'Premium', 'Guayaquil', 1400.50),
    ('2212345672', 'Ricardo Torres', NULL, 'Basic', 'Cuenca', 1800.75),
    ('2312345674', 'Sofía Fernández', NULL, 'Premium', 'Manta', 1700.25),
    ('2412345676', 'Diego Herrera', NULL, 'Basic', 'Quito', 1600.00);
```

###Mostrar el total de nombres
####Para mostrar todos los nombres, usamos la función **COUNT()**, pasándole como parámetro el campo, en este caso "fullname"

```
SELECT COUNT (fullname)
FROM CLIENT

```
