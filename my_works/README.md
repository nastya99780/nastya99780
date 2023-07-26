# Задание: протестировать требования

---

Ссылка: https://docs.google.com/spreadsheets/d/1JQNBN9ypW59Sbx1iIU7JnclZ5Yzx_RRBgBHWJFD4od8/edit?usp=sharing

# Задание: определить классы эквивалентности и граничные значения для каждого из них

---

Ссылка: https://docs.google.com/spreadsheets/d/1Zuxr1DeI_GByC3CZzDPcj1O3lVygT9pI4UAevwsnNwI/edit?usp=sharing


# Задание: Создать чек-лист на проверку логина в систему через почту и функциональность "Забыли пароль", создать 10 тест-кейсов на данную функциональность, а также отчеты о деффекте

---

Ссылка: https://docs.google.com/spreadsheets/d/1nLhflX5uApYkHu9SrIRhlonCb-ylSezOIbfXXw9zuOQ/edit?usp=sharing


# Задание: Создать коллекцию в Postman

---

Ссылка: https://documenter.getpostman.com/view/28083726/2s93zB6hEQ


# Несколько примеров моих запросов на SQL
```sql
use hogwarts;
SELECT 
	characters.fname, 
    characters.lname, 
	library.book_name
FROM characters
	join library
	ON characters.book_id = library.book_id and characters.char_id=library.char_id ;

```
```sql
SELECT 
	characters.fname, 
    characters.lname, 
	library.book_name
FROM characters
	LEFT join library
	ON characters.book_id = library.book_id and characters.char_id=library.char_id ;
```
```sql
SELECT 
	characters.fname, 
    characters.lname, 
    characters.age,
	library.book_name
FROM characters
	join library
	ON characters.book_id = library.book_id and characters.char_id=library.char_id 
WHERE age > 15;
```
```sql
SELECT count(*)
FROM library
WHERE end_date > ( 	
		SELECT 
			library.end_date
		FROM  library
        join characters
			ON characters.book_id = library.book_id and characters.char_id=library.char_id
		WHERE fname = "Hermione"
);
```
```sql
SELECT characters.patronus
FROM characters
WHERE age > (
		SELECT characters.age
        FROM characters
        WHERE patronus = 'Unknown'
);
```
```sql
SELECT COUNT(char_id), faculty
FROM characters
group by faculty
HAVING COUNT(char_id) > 1;
```
```sql
SELECT fname, lname,
CASE
    WHEN faculty = 'Gryffindor' THEN 'Godric'
    WHEN faculty = 'Slytherin' THEN 'Salazar'
    WHEN faculty = 'Ravenclaw' THEN 'Rovena'
    WHEN faculty = 'Hufflepuff' THEN 'Helga'
    ELSE 'Muggle'
END AS Founders
FROM characters;
```
```sql
SELECT lname
FROM characters 
WHERE lname NOT rlike 'H%' and lname NOT rlike 'L%'and lname NOT rlike 'S%';
```