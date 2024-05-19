**Crear tabla member:** 

CREATE TABLE member(
id SERIAL,
fullname VARCHAR (100) NOT NULL,
email VARCHAR (200) NOT NULL,
age INT NOT NULL,
UNIQUE (email),
PRIMARY KEY (id)
);

**Crear tabla event:**

CREATE TABLE event(
id SERIAL,
start_date DATE NOT NULL,
end_date DATE NOT NULL,
total_attendees INT NOT NULL,
city VARCHAR (50) NOT NULL,
PRIMARY KEY (id)
);

**Crear tabla conference:**

CREATE TABLE conference(
id SERIAL,
title VARCHAR (100) NOT NULL,
speaker VARCHAR (100) NOT NULL,
hour TIME NOT NULL,
day DATE NOT NULL,
total_attendees INT NOT NULL,
event_id INT NOT NULL,
PRIMARY KEY (id),
FOREIGN KEY (event_id) REFERENCES event (id)
);

**Crear tabla register:**

CREATE TABLE register(
id SERIAL,
member_id INT NOT NULL,
conference_id INT NOT NULL,
code VARCHAR (20) NOT NULL,
registered_at DATE NOT NULL,
assisted BOOLEAN NOT NULL,
UNIQUE (code),
PRIMARY KEY (id),
FOREIGN KEY (member_id) REFERENCES member (id),
FOREIGN KEY (conference_id) REFERENCES conference (id)
);

**Insertar valores a la tabla member:**

INSERT INTO member (fullname, email, age) VALUES
('Carlos Pérez', 'carlos.perez@example.com', 29),
('Ana Gómez', 'ana.gomez@example.com', 35),
('María López', 'maria.lopez@example.com', 42),
('Juan Martínez', 'juan.martinez@example.com', 24),
('Laura Sánchez', 'laura.sanchez@example.com', 31);

**Insertar valores a la tabla event:**

INSERT INTO event (start_date, end_date, total_attendees, city) VALUES
('2024-06-10', '2024-06-12', 150, 'Madrid'),
('2024-07-01', '2024-07-03', 200, 'Barcelona'),
('2024-08-15', '2024-08-17', 100, 'Valencia'),
('2024-09-05', '2024-09-06', 75, 'Sevilla'),
('2024-10-20', '2024-10-22', 300, 'Bilbao');

**Insertar valores a la tabla conference:**

INSERT INTO conference (title, speaker, hour, day, total_attendees, event_id) VALUES
('Innovación Tecnológica', 'Dr. José Hernández', '10:00:00', '2024-06-10', 50, 1),
('Marketing Digital', 'Laura Prieto', '14:00:00', '2024-06-11', 60, 1),
('Desarrollo de Software', 'Ana Gómez', '09:00:00', '2024-07-01', 80, 2),
('Ciberseguridad', 'Carlos Pérez', '11:00:00', '2024-07-02', 90, 2),
('Inteligencia Artificial', 'María López', '15:00:00', '2024-08-15', 40, 3);

**Insertar valores a la tabla register:**

INSERT INTO register (member_id, conference_id, code, registered_at, assisted) VALUES
(1, 1, 'REG20240610-1', '2024-06-01', true),
(2, 2, 'REG20240611-1', '2024-06-02', true),
(3, 3, 'REG20240701-1', '2024-06-20', false),
(4, 4, 'REG20240702-1', '2024-06-25', true),
(5, 5, 'REG20240815-1', '2024-08-01', false);

**CONSULTAS**
1. Filtrar a los miembros que tengan más de 30 años de edad:
SELECT * FROM member
WHERE age>30
ORDER BY age DESC

2. Filtrar las conferencias que se realizaron dentro de un es completo:
SELECT * FROM conference
WHERE day BETWEEN '2024-06-01' AND '2024-07-01'
ORDER BY day DESC

3. Filtrar los eventos en los cuales han asistido menos de 200 personas:
SELECT * FROM event
WHERE total_attendees<200
ORDER BY total_attendees DESC

4. Filtrar si un miembro asisió o no a la conferencia, filtrando el id del registro, id del miembro y si asistió o no:
SELECT id, member_id, assisted FROM register
WHERE assisted=true
ORDER BY id ASC

5. Filtrar un registro que se ha registrado el día 2024-06-01
SELECT * FROM register
WHERE registered_at='2024-06-01'
ORDER BY registered_at DESC


