# Desafio-Manipulaci-n-de-Datos-y-Transaccionalidad-en-las-Operaciones
-- Creación de la Base de Datos desafio2_jorge_leiva_128
CREATE DATABASE desafio2_jorge_leiva_128;

-- Creamos la tabla INSCRITOS
CREATE TABLE IF NOT EXISTS INSCRITOS(
	cantidad INT, 
	fecha DATE, 
	fuente VARCHAR
);

-- Ingresamos los resgistros de la tabla INSCRITOS
INSERT INTO INSCRITOS(cantidad, fecha, fuente)
VALUES ( 44, '01/01/2021', 'Blog' );
INSERT INTO INSCRITOS(cantidad, fecha, fuente)
VALUES ( 56, '01/01/2021', 'Página' );
INSERT INTO INSCRITOS(cantidad, fecha, fuente)
VALUES ( 39, '01/02/2021', 'Blog' );
INSERT INTO INSCRITOS(cantidad, fecha, fuente)
VALUES ( 81, '01/02/2021', 'Página' );
INSERT INTO INSCRITOS(cantidad, fecha, fuente)
VALUES ( 12, '01/03/2021', 'Blog' );
INSERT INTO INSCRITOS(cantidad, fecha, fuente)
VALUES ( 91, '01/03/2021', 'Página' );
INSERT INTO INSCRITOS(cantidad, fecha, fuente)
VALUES ( 48, '01/04/2021', 'Blog' );
INSERT INTO INSCRITOS(cantidad, fecha, fuente)
VALUES ( 45, '01/04/2021', 'Página' );
INSERT INTO INSCRITOS(cantidad, fecha, fuente)
VALUES ( 55, '01/05/2021', 'Blog' );
INSERT INTO INSCRITOS(cantidad, fecha, fuente)
VALUES ( 33, '01/05/2021', 'Página' );
INSERT INTO INSCRITOS(cantidad, fecha, fuente)
VALUES ( 18, '01/06/2021', 'Blog' );         
INSERT INTO INSCRITOS(cantidad, fecha, fuente)
VALUES ( 12, '01/06/2021', 'Página' );
INSERT INTO INSCRITOS(cantidad, fecha, fuente)
VALUES ( 34, '01/07/2021', 'Blog' );
INSERT INTO INSCRITOS(cantidad, fecha, fuente)
VALUES ( 24, '01/07/2021', 'Página' );
INSERT INTO INSCRITOS(cantidad, fecha, fuente)
VALUES ( 83, '01/08/2021', 'Blog' );
INSERT INTO INSCRITOS(cantidad, fecha, fuente)
VALUES ( 99, '01/08/2021', 'Página' );

-- Verificamos la tabla si están los campos y los registros de la misma
SELECT * FROM INSCRITOS;

-- RESPUESTAS:
-- 1.- ¿Cuántos registros hay?
SELECT COUNT(*) AS registros_totales FROM INSCRITOS;
-- La cantidad de registros da un total de 16.

-- 2.- ¿Cuántos inscritos hay en total?
SELECT SUM(cantidad) AS inscritos_totales FROM INSCRITOS;
-- El total de inscritos totales es de 774 personas.

-- 3.- ¿Cuál o cuáles son los registros de mayor antigüedad?
SELECT * FROM INSCRITOS
WHERE fecha = (SELECT MIN(fecha) FROM INSCRITOS);
-- Los más antiguos inscritos corresponden a las fuentes "Blog" y "Página" corresponiente a la fecha del "01 de enero de 2021".

-- 4.- ¿Cuántos inscritos hay por día? (entendiendo un día como una fecha distinta de ahora en adelante)
SELECT  fecha, SUM(cantidad) AS total_inscritos_por_dia
FROM INSCRITOS
GROUP BY fecha
ORDER BY fecha;
/*     Fecha     Total inscritos por día
	"2021-01-01"	100
	"2021-01-02"	120
	"2021-01-03"	103
	"2021-01-04"	93
	"2021-01-05"	88
	"2021-01-06"	30
	"2021-01-07"	58
	"2021-01-08"	182
*/

-- 5.- ¿Qué día se inscribieron la mayor cantidad de personas y cuántas personas se inscribieron en ese día?
SELECT fecha, SUM(cantidad) AS total_inscritos_dia
FROM INSCRITOS
GROUP BY fecha
ORDER BY total_inscritos_dia DESC
LIMIT 1;
-- El día que más hay inscritos fue con fecha "El día 01 de Agosto de 2021" y el total fue de 182 personas.