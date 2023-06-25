![foto](Rdm.png)

# Script de base de datos para MySQL 🗂️

El objetivo de este proyecto es aprender a trabajar en una base de datos y hacer consultas SQL.

**CREAR UNA BASE DE DATOS** 📂

Crea una base de datos que se llame **my_company_database**.
La base de datos deberá contener la siguiente tabla: employees.
A su vez tendrá los siguientes campos:

-   id
-   birth_date
-   first_name
-   last_name
-   gender

**AÑADIR NUEVAS COLUMNAS A LA TABLA:** 📊

-   Columna "salary"
-   Columna "title"
-   Columna "title_date"(fecha)

**INSERTAR DATOS** 📇

-   Inserte al menos 15 nuevos empleados:
-   Al menos 3 empleados deben tener el mismo nombre.
-   Los salarios de los empleados deben oscilar en un rango de 5000 y 50.000 y deben variar entre diferentes géneros.
-   Todos los empleados tienen un título.
-   Al menos 5 títulos son de 2020.

**ACTUALIZAR DATOS** 📝

⦁ Cambiar el nombre de un empleado. Para ello, genere una consulta que afecte solo a un determinado empleado en función de su nombre, apellido y fecha de nacimiento.

**OBTENER DATOS** 📥

⦁ Seleccione todos los empleados con un salario superior a 20.000
⦁ Seleccione todos los empleados con un salario inferior a 10.000
⦁ Seleccione todos los empleados que tengan un salario entre 14.000 y 50.000
⦁ Seleccione el número total de empleados
⦁ Selecciona los títulos del año 2019
⦁ Seleccione solo el nombre de los empleados y que se vean en mayúsculas
⦁ Seleccionar el nombre de los empleados sin que se repita ninguno

**BORRAR DATOS** 🗑️

⦁ Elimina el empleado con id = 5
⦁ Eliminar a todos los empleados con un salario superior a 20.000

```SQL
CREATE DATABASE my_company_database;

USE my_company_database;

CREATE TABLE employees (
  id INT PRIMARY KEY AUTO_INCREMENT,
  birth_date DATE,
  first_name VARCHAR(50),
  last_name VARCHAR(50),
  gender ENUM('Male', 'Female', 'Other')
);

ALTER TABLE employees ADD COLUMN (
  salary DOUBLE,
  title VARCHAR(50),
  title_date DATE
);

SELECT * FROM employees;

INSERT INTO employees (birth_date, first_name, last_name, gender, salary, title, title_date) VALUES ('1983-06-21', 'Juan', 'Perez', 'Male', '300909.24', 'Developer', '2020-09-22'),('1978-04-20', 'Juan', 'Lopez', 'Male', '41300.99', 'Economista', '2023-06-21'),('1989-09-04', 'Juan', 'Gomez', 'Other', '2950', 'Enfermero', '1998-11-09'),('1998-10-02', 'Daniel', 'Torres', 'Male', '50000', 'Ingeniero', '2020-01-10'),('1976-11-01', 'Marta', 'Fuentes', 'Female', '1970.50', 'Chef', '1999-12-01'),('1989-12-02', 'Ramón', 'Del Valle', 'Male', '48990.20', 'Profesor', '2000-07-12'),('1982-01-03', 'Lorenzo', 'Ortiz', 'Male', '1305', 'Pintor', '2009-05-23'),('1991-02-10', 'Ivana', 'Da Silva', 'Female', '11300.40', 'Diseñadora', '2012-08-06'),('1999-03-12', 'Andrea', 'Soto', 'Female', '30500', 'Arquitecta', '2020-10-15'),('1970-04-13', 'Maria', 'Castro', 'Female', '7100','Periodista', '1996-11-22'),('2001-05-14', 'Roberto', 'Reyes', 'Other', '1300.10', 'Peluquero', '2020-03-16'),('1971-06-20', 'Alberto', 'Vargas', 'Male', '39080', 'Medico', '1985-07-30'),('1988-07-29', 'Facundo', 'Cruz', 'Male', '48308.70', 'Inversor', '2020-12-25'),('2000-08-30', 'Lorena', 'Pierri', 'Male', '29650.24', 'Psicóloga', '2020-02-02'),('1973-09-15', 'Santiago', 'Urquiza', 'Male', '19768.24', 'Abogado', '1991-04-29');

SELECT * FROM employees;

UPDATE employees SET first_name = 'Rodrigo', last_name = 'Rossi', birth_date = '1980-01-17' WHERE id = 15;

SELECT * FROM employees WHERE salary > 20000;
SELECT * FROM employees WHERE salary < 10000;
SELECT * FROM employees WHERE salary BETWEEN 14000 AND 50000;

SELECT COUNT(*) AS total_empleados FROM employees;

SELECT title FROM employees WHERE YEAR(title_date) = 2020;

SELECT UPPER(first_name) AS nombre FROM employees;

SELECT DISTINCT first_name FROM employees;

DELETE FROM employees WHERE id = 5;

DELETE FROM employees WHERE salary > 20000;

--TRUNCATE TABLE employees;
```
