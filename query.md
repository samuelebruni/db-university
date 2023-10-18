
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
SELECT students.id, students.name, students.surname, students.degree_id, degrees.name AS course_name FROM students JOIN degrees ON degrees.id = students.degree_id WHERE degrees.name = 'Corso di Laurea in Economia';

2) 👉 Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
SELECT degrees.name, degrees.level, departments.name AS department_name FROM degrees JOIN departments ON department_id = departments.id WHERE departments.name = 'Dipartimento di Neuroscienze' AND degrees.level = 'magistrale';


3) 👉 Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
SELECT courses.id,courses.name, teachers.name,teachers.surname FROM courses JOIN course_teacher ON course_teacher.course_id = courses.id JOIN teachers ON teachers.id = course_teacher.teacher_id WHERE teachers.id = 44;

4) 👉 Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
SELECT students.name, students.surname, degrees.name AS degree_name, departments.name AS department_name FROM students JOIN degrees ON degree_id = degrees.id JOIN departments ON department_id = departments.id ORDER BY students.surname, students.name;

5) 👉 Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
SELECT degrees.name AS degree_name, courses.name AS course_name, teachers.name AS teacher_name, teachers.surname AS teacher_surname FROM course_teacher JOIN courses ON course_id = courses.id JOIN degrees ON degree_id = degrees.id JOIN teachers ON teacher_id = teachers.id;

6) 👉 Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
SELECT DISTINCT teachers.name AS teacher_name, teachers.surname AS teacher_surname, departments.name AS department_name FROM course_teacher JOIN courses ON course_id = courses.id JOIN degrees ON degree_id = degrees.id JOIN departments ON department_id = departments.id JOIN teachers ON teacher_id = teachers.id WHERE departments.name = 'Dipartimento di Matematica';
