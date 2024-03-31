```sql
show databases;
SELECT datname FROM pg_database;
SELECT fname FROM students ORDER BY fname ASC LIMIT 3;
SELECT fname FROM students where fname LIKE 'A%';
SELECT surname FROM students WHERE age BETWEEN 18 AND 24;

CREATE TABLE students (
  id SERIAL PRIMARY KEY,
  fname VARCHAR(50),
  surname VARCHAR(50),
  age INTEGER
);

DROP TABLE students;
INSERT INTO students (fname, surname, age) VALUES ('John', 'Doe', 22);
UPDATE students SET fname = 'Johnny' WHERE id = 1;
DELETE FROM students WHERE id = 1;


SELECT students.fname, courses.course_name
FROM students
INNER JOIN enrollments ON students.id = enrollments.student_id
INNER JOIN courses ON enrollments.course_id = courses.id;

SELECT COUNT(*) FROM students; -- Counts all rows
SELECT MAX(age) FROM students; -- Finds the maximum age
SELECT AVG(age) FROM students; -- Finds the average age
SELECT SUM(age) FROM students; -- Finds the sum of all ages

SELECT age, COUNT(*) FROM students GROUP BY age; -- Groups students by age

SELECT * FROM students WHERE age IN (SELECT age FROM students WHERE fname LIKE 'A%'); -- Finds all students with the same age as students whose name starts with 'A'


BEGIN TRANSACTION;
COMMIT;
ROLLBACK;


CREATE VIEW student_info AS
SELECT students.fname, students.surname, courses.course_name
FROM students
INNER JOIN enrollments ON students.id = enrollments.student_id
INNER JOIN courses ON enrollments.course_id = courses.id;


CREATE TRIGGER log_update
AFTER UPDATE ON students
FOR EACH ROW
EXECUTE PROCEDURE log_update_func();

CREATE INDEX idx_students_fname ON students (fname);


CREATE OR REPLACE FUNCTION add_student(fname VARCHAR, surname VARCHAR, age INT)
RETURNS VOID AS
$$
BEGIN
INSERT INTO students (fname, surname, age)
  VALUES (fname, surname, age);
END;
$$ LANGUAGE plpgsql;
