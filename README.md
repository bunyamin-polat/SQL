# Patika.dev SQL
## Ödev-1
### 1.film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.
 SELECT title,description FROM film 
### 2.film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.
SELECT * FROM film WHERE length > 60 AND length < 75
### 3.film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.
SELECT * FROM film WHERE rental_rate = 0.99 AND replacement_cost = 12.99 OR replacement_cost = 28.99
### 4.customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?
SELECT * FROM customer WHERE first_name='Mary'
### 5.film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.
SELECT * FROM film WHERE length < 50 AND NOT(rental_rate = 2.99 OR rental_rate = 4.99)
## Ödev-2
### 1.film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)
SELECT * FROM film WHERE replacement_cost BETWEEN 12.99 AND 16.99
### 2.actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)
SELECT first_name, last_name FROM actor WHERE first_name IN('Penelope','Nick','Ed')
### 3.film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)
SELECT * FROM film WHERE rental_rate IN(0.99, 2.99, 4.99) AND replacement_cost IN(12.99, 15.99, 28.99)
## Ödev-3
### 1.country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.
SELECT country FROM country WHERE country LIKE 'A%a
### 2.country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.
SELECT country From country WHERE length(country) > 6 AND country LIKE '%n'
### 3.film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.
SELECT title FROM film WHERE title ILIKE '%t%t%t%t%'
### 4.film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.
SELECT * FROM film WHERE title LIKE 'C%' AND length > 90 AND rental_rate=2.99
## Ödev-4
### 1.film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.
SELECT DISTINCT replacement_cost FROM film
### 2.film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?
SELECT COUNT(DISTINCT replacement_cost) FROM film
### 3.film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?
SELECT COUNT(title) FROM film WHERE title LIKE 'T%' AND rating = 'G'
### 4.country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?
SELECT COUNT(title) FROM country WHERE length(country)=5 
### 5.city tablosundaki şehir isimlerinin kaçtanesi 'R' veya r karakteri ile biter?
SELECT COUNT(city) FROM city WHERE city ILIKE '%R'
## Ödev-5
### 1.film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.
SELECT title,length FROM film 
WHERE title LIKE '%n'
ORDER BY length DESC
LIMIT 5
### 2.film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci 5 filmi sıralayınız.
SELECT title,length FROM film 
WHERE title LIKE '%n'
ORDER BY length ASC
OFFSET 5
LIMIT 5
### 3.customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.
SELECT * FROM customer 
WHERE store_id = 1 
ORDER BY last_name DESC 
LIMIT 4

## Ödev-6
### 1.film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?
SELECT AVG(rental_rate) FROM film
### 2.film tablosunda bulunan filmlerden kaçtanesi 'C' karekteri ile başlar?
SELECT COUNT(*) FROM film
WHERE title LIKE 'C%'
### 3.film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?
SELECT MAX(length) FROM film 
WHERE rental_rate = 0.99
### 4.film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?
SELECT COUNT(DISTINCT replacement_cost ) FROM film
WHERE length > 150

## Ödev-7
### 1.film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.
SELECT rating ,COUNT(*) FROM film
GROUP BY rating
### 2.film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.
SELECT replacement_cost ,COUNT(*) FROM film
GROUP BY replacement_cost
HAVING COUNT(*) > 50
### 3. customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir?
SELECT store_id ,COUNT(*) FROM customer
GROUP BY store_id
### 4. city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıra country_id bilgisini ve şehir sayısını paylaşınız.
SELECT country_id ,COUNT(*) FROM city
GROUP BY country_id
ORDER BY COUNT(*) DESC
LIMIT 1

## Ödev-8
### 1.test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.
CREATE TABLE employee(
	id SERIAL PRIMARY KEY,
	name VARCHAR(50) NOT NULL,
	email VARCHAR(100),
	birthday DATE
)
### 2.Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.
insert into employee (name, email, birthday) values ('Cosette', 'csouza0@myspace.com', '1919/10/26');
insert into employee (name, email, birthday) values ('Riccardo', 'rsimoneau1@examiner.com', null);
insert into employee (name, email, birthday) values ('Wallie', 'wmatfield2@facebook.com', '1915/09/02');
insert into employee (name, email, birthday) values ('Beniamino', 'bmilkin3@reference.com', '1933/05/08');
insert into employee (name, email, birthday) values ('Kaylee', null, '1957/04/23');
insert into employee (name, email, birthday) values ('Anthea', 'aopenshaw5@epa.gov', null);
insert into employee (name, email, birthday) values ('Lexis', null, null);
insert into employee (name, email, birthday) values ('Loree', 'lsaintsbury7@over-blog.com', '1994/08/11');
insert into employee (name, email, birthday) values ('Kathy', 'kcardenas8@technorati.com', null);
insert into employee (name, email, birthday) values ('Mauricio', 'mlarder9@dyndns.org', '1970/11/24');
insert into employee (name, email, birthday) values ('Gertrudis', 'gkarchewskia@bloomberg.com', '1927/08/24');
insert into employee (name, email, birthday) values ('Cynthie', 'cholburyb@wordpress.com', '1990/07/25');
insert into employee (name, email, birthday) values ('Pen', 'pingerc@ted.com', '1972/05/23');
insert into employee (name, email, birthday) values ('Frankie', null, '1958/07/23');
insert into employee (name, email, birthday) values ('Barty', 'bwyree@bizjournals.com', '1947/06/20');
insert into employee (name, email, birthday) values ('Bernarr', 'bcroxallf@icq.com', '1959/01/19');
insert into employee (name, email, birthday) values ('Darcy', 'dlowingsg@yelp.com', '1978/10/25');
insert into employee (name, email, birthday) values ('Rora', 'rcardish@umn.edu', '1972/10/18');
insert into employee (name, email, birthday) values ('Crysta', null, '1916/08/23');
insert into employee (name, email, birthday) values ('Krystyna', 'kflatmanj@vk.com', '1978/04/06');
insert into employee (name, email, birthday) values ('Hebert', 'hdunphiek@google.pl', '1966/08/06');
insert into employee (name, email, birthday) values ('Daniela', 'dgammiel@nsw.gov.au', '1988/05/19');
insert into employee (name, email, birthday) values ('Zachariah', 'zcharrissonm@dmoz.org', null);
insert into employee (name, email, birthday) values ('Gale', 'gparvinn@sitemeter.com', '1980/09/05');
insert into employee (name, email, birthday) values ('Violet', 'vlebosseo@furl.net', '1901/01/13');
insert into employee (name, email, birthday) values ('Madge', 'mmillwaterp@pen.io', '2006/10/19');
insert into employee (name, email, birthday) values ('Erma', null, null);
insert into employee (name, email, birthday) values ('Bevin', 'bkrugr@mozilla.com', '1947/08/14');
insert into employee (name, email, birthday) values ('June', 'jbonins@comsenz.com', '1996/05/17');
insert into employee (name, email, birthday) values ('Skyler', null, null);
insert into employee (name, email, birthday) values ('Wilden', 'wsigwardu@stumbleupon.com', '1971/01/27');
insert into employee (name, email, birthday) values ('Cammie', 'cpflegerv@fc2.com', null);
insert into employee (name, email, birthday) values ('Phylis', 'pkleintw@google.es', '2000/10/28');
insert into employee (name, email, birthday) values ('Bettye', 'bwhitemarshx@cafepress.com', '2011/11/11');
insert into employee (name, email, birthday) values ('Yorke', null, '2017/06/20');
insert into employee (name, email, birthday) values ('Skipper', 'schittiez@stanford.edu', '1924/05/28');
insert into employee (name, email, birthday) values ('Claribel', null, '2019/04/27');
insert into employee (name, email, birthday) values ('Georgie', 'gbedin11@linkedin.com', '1915/09/29');
insert into employee (name, email, birthday) values ('Wendell', 'wvandecastele12@narod.ru', null);
insert into employee (name, email, birthday) values ('Mack', 'mmccrory13@ucla.edu', null);
insert into employee (name, email, birthday) values ('Kile', null, null);
insert into employee (name, email, birthday) values ('Jakob', 'jbellon15@usa.gov', '1938/09/21');
insert into employee (name, email, birthday) values ('Giorgia', null, '2014/07/01');
insert into employee (name, email, birthday) values ('Barnaby', 'bnormanvill17@house.gov', '2007/11/27');
insert into employee (name, email, birthday) values ('Ange', 'atemperley18@nba.com', '1916/10/10');
insert into employee (name, email, birthday) values ('Anita', 'amichael19@nasa.gov', null);
insert into employee (name, email, birthday) values ('Amandy', 'awalkden1a@ebay.co.uk', null);
insert into employee (name, email, birthday) values ('Amalita', 'aterbrugge1b@sakura.ne.jp', '1906/09/11');
insert into employee (name, email, birthday) values ('Breena', 'bstockow1c@admin.ch', '1901/04/09');
insert into employee (name, email, birthday) values ('Letta', 'ldefreitas1d@plala.or.jp', '1922/09/28');
### 3.Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.
UPDATE employee SET name = 'Coset' WHERE id = 1;
UPDATE employee SET email = 'ricardo@gmail.com' WHERE name = 'Riccardo';
UPDATE employee SET birthday = '"1964-02-01"' WHERE email = 'wmatfield2@facebook.com';
UPDATE employee SET birthday = '2020-05-29',name = 'Benjamin' WHERE email = 'bmilkin3@reference.com';
UPDATE employee SET name = 'Barbaros',birthday = '2021-05-29' WHERE id = 10;
### 4.Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.
DELETE FROM employee WHERE name = 'Coset';
DELETE FROM employee WHERE email = 'ricardo@gmail.com';
DELETE FROM employee WHERE birthday = '1915-09-02';
DELETE FROM employee WHERE name = 'Beniamino';
DELETE FROM employee WHERE id = '10';

## Ödev-9
### 1.city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
SELECT city, country FROM city
INNER JOIN country ON city.country_id = country.country_id
### 2.customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
SELECT payment_id, first_name, last_name FROM customer
INNER JOIN payment ON customer.customer_id = payment.customer_id
### 3.customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
SELECT rental_id, first_name, last_name FROM customer
INNER JOIN rental ON customer.customer_id = rental.customer_id

## Ödev-10
### 1.city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.
SELECT city, country FROM city
LEFT JOIN country ON city.country_id = country.country_id
### 2.customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.
SELECT payment_id ,first_name, last_name  FROM customer
RIGHT JOIN payment ON payment.customer_id = customer.customer_id
### 3.customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.
SELECT rental_id ,first_name, last_name  FROM customer
FULL JOIN rental ON customer.customer_id = rental.customer_id

## Ödev-11
### 1.actor ve customer tablolarında bulunan first_name sütunları için tüm verileri sıralayalım.
(SELECT first_name FROM actor)
UNION
(SELECT first_name FROM actor)
### 2.actor ve customer tablolarında bulunan first_name sütunları için kesişen verileri sıralayalım.
(SELECT first_name FROM actor)
INTERSECT
(SELECT first_name FROM actor)
### 3.actor ve customer tablolarında bulunan first_name sütunları için ilk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralayalım.
(SELECT first_name FROM actor)
EXCEPT
(SELECT first_name FROM actor)
### 4.İlk 3 sorguyu tekrar eden veriler için de yapalım.
(SELECT first_name FROM actor)
UNION ALL
(SELECT first_name FROM actor)

(SELECT first_name FROM actor)
INTERSECT ALL
(SELECT first_name FROM actor)

(SELECT first_name FROM actor)
EXCEPT ALL
(SELECT first_name FROM actor)

## Ödev-12
### 1.film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?
SELECT COUNT(*) FROM film
WHERE length > (SELECT AVG(length) FROM film)
### 2.film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?
SELECT COUNT(*) FROM film
WHERE rental_rate =(SELECT MAX(rental_rate) FROM film)
### 3.film tablosunda en düşük rental_rate ve en düşün replacement_cost değerlerine sahip filmleri sıralayınız.
SELECT title, rental_rate,replacement_cost FROM film
WHERE (rental_rate =(SELECT MIN(rental_rate) FROM film)) AND 
      (replacement_cost=(SELECT MIN(replacement_cost) FROM film))
### 4.payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.
SELECT first_name,last_name,amount FROM customer
JOIN payment ON payment.customer_id=customer.customer_id
WHERE amount = (SELECT MAX(amount) FROM payment)
