
1) 👉 SELECT * FROM students WHERE YEAR(date_of_birth) = 1990;
2) 👉 SELECT * FROM courses WHERE cfu > 10;
3) 👉 SELECT * FROM students WHERE YEAR(date_of_birth) < 1993;
4) 👉 SELECT * FROM courses WHERE period='I semestre' AND year = 1;
5) 👉 SELECT * FROM exams WHERE date = '2020-06-20' AND hour > '14:00:00';
6) 👉 SELECT * FROM `degrees` WHERE level ='magistrale';
7) 👉 SELECT COUNT(0) AS 'Numero Dipartimenti' FROM departments;
8) 👉 SELECT COUNT(*) AS 'Quante Insegnanti non hanno inserito il numero di telefono' FROM teachers WHERE phone is not null;
