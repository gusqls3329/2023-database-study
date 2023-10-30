# 2023-database-study
CREATE TABLE corporation (
	  corp_id SMALLINT
	, NAME VARCHAR(30)
	, PRIMARY KEY (corp_id)
);
/* 
멀티라인 주석
*/

-- 싱글라인 주석
CREATE TABLE corporation2 (
	  corp_id SMALLINT PRIMARY KEY 
	, NAME VARCHAR(30) 
); 

DROP TABLE corporation3;
DROP TABLE corporation2;
DROP TABLE corporation;



INSERT INTO corporation 
(corp_id, NAME)
VALUES
(1, '곽경록'); 

INSERT INTO corporation 
(corp_id, NAME)
VALUES
(2, '김경현'); 


INSERT INTO corporation 
(corp_id, NAME)
VALUES
(3, '김동하'); 


INSERT INTO corporation 
(corp_id, NAME)
VALUES
(4, '김태형'); 


INSERT INTO corporation 
(corp_id, NAME)
VALUES
(5, '김현빈'),
(6, '김현수');

SELECT corp_id, name 
FROM corporation
WHERE corp_id % 2 = 0;

/*
Oracle, SQL Server, MySql/MariaDB
3, '김동하'
4, '김태형'
5, '김현빈'
6, '김현수'
*/
UPDATE corporation
SET NAME = 'Rachel'
WHERE corp_id = 5;

DELETE FROM corporation
WHERE corp_id = 5;

-- 사라진 from 절
SELECT NOW() > '2023-10-28' FROM dual;


/*
date
time
datetime
timestamp (정수로 저장, 19
year

*/
CREATE TABLE person(
     person_id SMALLINT UNSIGNED  
	, fname VARCHAR(20)
	, lname VARCHAR(20)
	, eye_color CHAR(2) CHECK (eye_color IN ('BR', 'BL', 'GR'))
	, birth_date date
	, street VARCHAR(30)
	, city VARCHAR(20)
	, state VARCHAR(20)
	, country VARCHAR(20)
	, postal_code VARCHAR(20)
	, PRIMARY KEY (person_id)	
);

CREATE TABLE favorite_food (
	  person_id SMALLINT UNSIGNED
	, food VARCHAR(20)
	, PRIMARY KEY (person_id, food)
	, FOREIGN KEY (person_id) REFERENCES person(person_id)
);


INSERT INTO person
(person_id, fname, lname, eye_color, birth_date)
VALUES
(1, 'William', 'Turner', 'BL', '1972-05-27');

INSERT INTO person
(
	  person_id, fname, lname, eye_color, birth_date
	, street, city, state, country, postal_code
)
VALUES
(	  
	  2, 'Susan', 'Smith', 'BR', '1975-11-02'
	, '23 Maple St.', 'Arlington', 'VA', 'USA', '20220'
);

INSERT INTO favorite_food
(person_id, food)
VALUES
(1, '햄버거');

INSERT INTO favorite_food
(person_id, food)
VALUES
(1, '닭발');



CREATE TABLE person2(
	person_id INT UNSIGNED PRIMARY KEY
	, num INT UNSIGNED UNIQUE
);

CREATE TABLE food_favorite(
	  my_num INT UNSIGNED PRIMARY KEY
	, food VARCHAR(20)
	, FOREIGN KEY (my_num) REFERENCES person2(num)
);


UPDATE person
SET street = '1225 Tremont St.'
, city = 'Boston'
, state = 'MA'
, country = 'USA'
, postal_code = '02138'
WHERE person_id = 1;


SELECT * FROM person;
