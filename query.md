
1) 👉 SELECT * FROM students WHERE YEAR(date_of_birth) = 1990;
2) 👉 SELECT * FROM courses WHERE cfu > 10;
3) 👉 SELECT * FROM students WHERE YEAR(date_of_birth) < 1993;
4) 👉 SELECT * FROM courses WHERE period='I semestre' AND year = 1;
5) 👉 SELECT * FROM exams WHERE date = '2020-06-20' AND hour > '14:00:00';
6) 👉 SELECT * FROM degrees WHERE level ='magistrale';
7) 👉 SELECT COUNT(0) AS 'Numero Dipartimenti' FROM departments;
8) 👉 SELECT COUNT(*) AS 'Quante Insegnanti non hanno inserito il numero di telefono' FROM teachers WHERE phone is not null;


## GROUP BY 👇:

1) 👉 Contare quanti iscritti ci sono stati ogni anno:
SELECT COUNT(*) AS student_count, YEAR(enrolment_date) FROM students GROUP BY YEAR(enrolment_date);

2) 👉 Contare gli insegnanti che hanno l'ufficio nello stesso edificio
SELECT COUNT(*) AS teachers_count, office_address FROM teachers GROUP BY office_address;

3) 👉 Calcolare la media dei voti di ogni appello d'esame
SELECT COUNT(exam_id) AS exams_count, AVG(vote) AS average_vote FROM exam_student GROUP BY exam_id;

4) 👉 Contare quanti corsi di laurea ci sono per ogni dipartimento
SELECT COUNT(*) AS degrees_count, department_id, departments.name AS department_name FROM degrees JOIN departments ON department_id = departments.id GROUP BY department_id;


## JOINS 👇:

1) 👉 Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

2) 👉 Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

3) 👉 Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

4) 👉 Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

5) 👉 Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

6) 👉 Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
