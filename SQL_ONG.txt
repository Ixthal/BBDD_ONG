CREATE DATABASE ong;
USE ong;
CREATE TABLE trabajador(
	DNItrabajador CHAR NOT NULL UNSIGNED AUTO_INCREMENTAL PRIMARY KEY, 
	codigo_ong INT,
	nombre VARCHAR,
	apellidos VARCHAR, 
	fecha VARCHAR
	);


CREATE TABLE telefonos(
	IDtelefono VARCHAR NOT NULL UNSIGNED AUTO_INCREMENTAL PRIMARY KEY, 
	DNIsocio CHAR,
	DNItrabajador CHAR,
	telefono INT
	);


CREATE TABLE ong(
	codigo_ong INT NOT NULL UNSIGNED AUTO_INCREMENTAL PRIMARY KEY, 
	nombre VARCHAR,
	calle VARCHAR, 
	fecha VARCHAR
	);

CREATE TABLE organizacion(
	IDorg_evento INT NOT NULL UNSIGNED AUTO_INCREMENTAL PRIMARY KEY, 
	codigo_ong INT, 
	DNIsocio CHAR,
	IDtelefono INT
	);


CREATE TABLE telefonos(
	IDtelefono VARCHAR NOT NULL UNSIGNED AUTO_INCREMENTAL PRIMARY KEY, 
	DNI CHAR,
	telefono INT
	);

CREATE TABLE socio(
	DNIsocio VARCHAR NOT NULL UNSIGNED AUTO_INCREMENTAL PRIMARY KEY, 
	nombre VARCHAR,
	apellido VARCHAR,
	fecha VARCHAR
	);

ALTER TABLE organizacion
ADD FOREIGN KEY (codigo_ong) REFERENCES ong(codigo_ong);
ADD FOREIGN KEY (DNIsocio) REFERENCES socio(DNIsocio);
ADD FOREIGN KEY (IDtelefono) REFERENCES telefono(IDtelefono);

ALTER TABLE telefonos
ADD FOREIGN KEY (DNIsocio) REFERENCES socio(DNIsocio);

ALTER TABLE trabajador
ADD FOREIGN KEY (codigo_ong) REFERENCES ong(codigo_ong);