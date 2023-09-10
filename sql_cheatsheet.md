```sql
show databases;
SELECT datname FROM pg_database;
SELECT fname FROM students ORDER BY fname ASC LIMIT 3;
SELECT fname FROM students where fname LIKE 'A%';
SELECT surname FROM students WHERE age BETWEEN 18 AND 24;
