# Patika.dev-SQL-Repo
## Patika.dev SQL Ödev 1

1. film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.

```sql
SELECT title,description FROM film;
```

2. **film** tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük **VE** 75 ten küçük olma koşullarıyla sıralayınız.

```sql
SELECT * FROM film 
WHERE ( length > 60 AND length < 75 );
```

3. **film** tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 **VE** replacement_cost 12.99 **VEYA** 28.99 olma koşullarıyla sıralayınız.

```SQL
SELECT * FROM film
WHERE (rental_rate = 0.99 AND replacement_cost = 12.99 OR replacement_cost = 28.99);
```

4. **customer** tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?

```sql
SELECT * FROM customer
WHERE first_name = 'Mary' ;
```

5. **film** tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.

```sql
SELECT * FROM film
WHERE NOT length>50 AND NOT rental_rate =2.99 AND NOT rental_rate=4.99;
```





## Patika.dev SQL Ödev 2

1. **film** tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)

```sql
SELECT * FROM film
WHERE replacement_cost BETWEEN 12.99 AND 16.99;
```

2. .**actor** tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)

```sql
SELECT * FROM actor
WHERE first_name IN('Penelope','Nick','Ed');
```

3. **film** tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 **VE** replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)

```sql
SELECT * FROM film
WHERE rental_rate IN(0.99,2.99,4.99) AND replacement_cost IN(12.99, 15.99, 28.99);
```





## Patika.dev SQL Ödev 3

1. **country** tablosunda bulunan **country** sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.

```sql
SELECT * FROM country
WHERE country LIKE('A%a');
```

2. **country** tablosunda bulunan **country** sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.

```sql
SELECT * FROM country
WHERE country LIKE('_____n');
```

3. **film** tablosunda bulunan **title** sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.

```sql
SELECT title FROM film
WHERE title ILIKE('%t%t%t%t%');
```

4. **film** tablosunda bulunan tüm sütunlardaki verilerden **title** 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.

```sql
SELECT * FROM film
WHERE title LIKE('C%') AND length>90 AND rental_rate =2.99;
```







## Patika.dev SQL Ödev 4
1. **film** tablosunda bulunan **replacement_cost** sütununda bulunan birbirinden farklı değerleri sıralayınız.

   ```sql
   SELECT DISTINCT replacement_cost FROM film;
   ```

   

2. **film** tablosunda bulunan **replacement_cost** sütununda birbirinden farklı kaç tane veri vardır?

   ```sql
   SELECT COUNT(DISTINCT replacement_cost) FROM film;
   ```

   

3. **film** tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?

   ```sql
   SELECT COUNT(*) FROM film
   WHERE title LIKE('T%') AND rating='G';
   ```

   

4. **country** tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?

   ```sql
   SELECT COUNT(*) FROM country
   WHERE country LIKE('_____');
   ```

   

5. **city** tablosundaki şehir isimlerinin kaçtanesi 'R' veya r karakteri ile biter?

   ```sql
   SELECT COUNT(*) FROM city
   WHERE city ILIKE('%r');
   ```
## Patika.dev SQL Ödev 5

1. **film** tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.

   ```sql
   1. 1. SELECT * FROM film
         WHERE title LIKE('%n')
         ORDER BY length DESC
         LIMIT 5;
   
   
   ```

2. **film** tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci 5 filmi sıralayınız.

   ```sql
   SELECT * FROM film
   WHERE title LIKE('%n')
   ORDER BY length ASC
   OFFSET 5
   LIMIT 5;
   ```

3. **customer** tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.

   ```sql
   SELECT * FROM customer
   WHERE store_id=1
   ORDER BY last_name DESC
   LIMIT 4;
   ```

  
  
  
  
  
  
  
  
  ## Patika.dev SQL Ödev 6

1. **film** tablosunda bulunan **rental_rate** sütunundaki değerlerin ortalaması nedir?

   ```sql
   SELECT AVG(rental_rate) FROM film;
   ```

2. **film** tablosunda bulunan filmlerden kaçtanesi 'C' karekteri ile başlar?

   ```sql
   SELECT COUNT(*) FROM film
   WHERE title LIKE('C%') ;
   ```

3. **film** tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır? 

   ```sql
   SELECT MAX(length) FROM film
   WHERE rental_rate=0.99;
   ```

4. **film** tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?

   ```sql
   SELECT DISTINCT(replacement_cost) FROM film
   WHERE length >150;
   ```

   
  
  
  
  
  
  
  
  
  ## Patika.dev SQL Ödev 7

1. **film** tablosunda bulunan filmleri **rating** değerlerine göre gruplayınız.

   ```sql
   SELECT rating, COUNT(*) FROM film
   GROUP BY rating;
   ```

2. **film** tablosunda bulunan filmleri **replacement_cost** sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.

   ```sql
   SELECT replacement_cost, COUNT(*) FROM film
   GROUP BY replacement_cost
   HAVING COUNT(*)>50;
   ```

3. **customer** tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir?

   ```sql
   SELECT store_id, COUNT(*) FROM customer 
   GROUP BY store_id;
   ```

4. **city** tablosunda bulunan şehir verilerini **country_id** sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıran country_id bilgisini ve şehir sayısını paylaşınız.

   ```sql
   SELECT country_id, COUNT(*) FROM city
   GROUP BY country_id
   ORDER BY COUNT(*) DESC;
   ```

   
   
  
  
  
  
  
  ## Patika.dev SQL Ödev 8

1. **test** veritabanınızda **employee** isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.

   ```sql
   CREATE TABLE employee(
   id SERIAL PRIMARY KEY,
   name VARCHAR(50) NOT NULL,		
   birthday DATE,
   email VARCHAR(100)	
   );
   ```

2. Oluşturduğumuz **employee** tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.

   ```sql
   insert into employee (name, email, birthday) values ('Ardenia', 'ablaszczyk0@admin.ch', '1987-04-27');
   insert into employee (name, email, birthday) values ('Belinda', 'bblue1@eventbrite.com', '1906-08-22');
   insert into employee (name, email, birthday) values ('Stanleigh', 'spottell2@elpais.com', '1953-10-13');
   insert into employee (name, email, birthday) values ('Mason', 'mravenhill3@nifty.com', '1933-08-01');
   insert into employee (name, email, birthday) values ('Joshuah', 'juzielli4@symantec.com', '1997-08-24');
   insert into employee (name, email, birthday) values ('Jaimie', 'jkonzelmann5@illinois.edu', '1996-09-11');
   insert into employee (name, email, birthday) values ('Lowell', 'lswanson6@huffingtonpost.com', '1996-12-15');
   insert into employee (name, email, birthday) values ('Wainwright', 'wstellino7@eepurl.com', '1981-06-28');
   insert into employee (name, email, birthday) values ('Theodosia', 'tdifilippo8@pen.io', '1903-08-03');
   insert into employee (name, email, birthday) values ('Dell', 'dlooby9@etsy.com', '1975-04-24');
   insert into employee (name, email, birthday) values ('Cordi', 'ckanwella@usatoday.com', '1954-12-14');
   insert into employee (name, email, birthday) values ('Baryram', 'bhatterslayb@flavors.me', '1903-08-04');
   insert into employee (name, email, birthday) values ('Grazia', 'gyoungsc@addtoany.com', '1941-08-18');
   insert into employee (name, email, birthday) values ('Andie', 'akinnend@google.nl', '1941-08-22');
   insert into employee (name, email, birthday) values ('Michal', 'mgroobye@stumbleupon.com', '1982-03-14');
   insert into employee (name, email, birthday) values ('Ethyl', 'eburfordf@flavors.me', '1913-12-13');
   insert into employee (name, email, birthday) values ('Jermayne', 'jpickering@shinystat.com', '1945-09-12');
   insert into employee (name, email, birthday) values ('Biddie', 'blorinczh@samsung.com', '1987-08-10');
   insert into employee (name, email, birthday) values ('Gabi', 'gmayeri@cloudflare.com', '1955-11-15');
   insert into employee (name, email, birthday) values ('Arthur', 'ahaigj@nhs.uk', '1923-05-13');
   insert into employee (name, email, birthday) values ('Damara', 'drhoddiek@tumblr.com', '1946-05-10');
   insert into employee (name, email, birthday) values ('El', 'ebatterl@cisco.com', '1956-11-09');
   insert into employee (name, email, birthday) values ('Jessey', 'jmalbonm@java.com', '1952-08-28');
   insert into employee (name, email, birthday) values ('Laetitia', 'lmacgruern@blogtalkradio.com', '1922-06-26');
   insert into employee (name, email, birthday) values ('Elsbeth', 'ehaseldineo@sun.com', '1994-10-21');
   insert into employee (name, email, birthday) values ('Reynolds', 'rhabbalp@mayoclinic.com', '1999-01-16');
   insert into employee (name, email, birthday) values ('Erika', 'evonbrookq@opensource.org', '1967-09-15');
   insert into employee (name, email, birthday) values ('Vanna', 'vmontgomeryr@narod.ru', '1906-06-16');
   insert into employee (name, email, birthday) values ('Kaleena', 'kgoodhews@cisco.com', '1922-07-17');
   insert into employee (name, email, birthday) values ('Clementia', 'cransomt@51.la', '1955-07-26');
   insert into employee (name, email, birthday) values ('Muire', 'mmanieu@netlog.com', '1962-03-20');
   insert into employee (name, email, birthday) values ('Janaye', 'jviveashv@phoca.cz', '1919-12-19');
   insert into employee (name, email, birthday) values ('Consalve', 'casplinw@indiegogo.com', '1982-11-30');
   insert into employee (name, email, birthday) values ('Ursula', 'udunseathx@cbc.ca', '1977-12-04');
   insert into employee (name, email, birthday) values ('Bambie', 'bwhylery@weebly.com', '1965-06-14');
   insert into employee (name, email, birthday) values ('Bastian', 'bdamrellz@ftc.gov', '1998-08-06');
   insert into employee (name, email, birthday) values ('Cammy', 'cprophet10@gov.uk', '1924-10-25');
   insert into employee (name, email, birthday) values ('Othella', 'opagnin11@angelfire.com', '1990-05-17');
   insert into employee (name, email, birthday) values ('Chrissy', 'cedgcombe12@issuu.com', '1903-06-14');
   insert into employee (name, email, birthday) values ('Aland', 'adeller13@i2i.jp', '1930-10-12');
   insert into employee (name, email, birthday) values ('Arabele', 'acollyear14@census.gov', '1940-01-21');
   insert into employee (name, email, birthday) values ('Hank', 'hkeers15@sciencedirect.com', '1979-03-30');
   insert into employee (name, email, birthday) values ('Bernette', 'brobertz16@china.com.cn', '1958-11-19');
   insert into employee (name, email, birthday) values ('Mellie', 'mrosas17@ask.com', '1944-08-24');
   insert into employee (name, email, birthday) values ('Rawley', 'rdrover18@umn.edu', '1949-09-27');
   insert into employee (name, email, birthday) values ('Fredrick', 'fvondra19@nytimes.com', '1956-08-08');
   insert into employee (name, email, birthday) values ('Oby', 'ostallen1a@mit.edu', '1970-11-15');
   insert into employee (name, email, birthday) values ('Mireielle', 'minchley1b@jalbum.net', '1971-07-24');
   insert into employee (name, email, birthday) values ('Malena', 'mflanagan1c@webs.com', '1996-02-23');
   insert into employee (name, email, birthday) values ('Kit', 'kfetherstonhaugh1d@timesonline.co.uk', '1905-03-23');
   ```

3. Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.

   ```sql
   UPDATE employee SET name='OGEDAY' WHERE id=1;
   UPDATE employee SET email='ogedayonline@gmail.com' WHERE name='Ogeday';
   UPDATE employee SET birthday='1998-12-29' WHERE id=1;
   UPDATE employee SET name='Enes' WHERE id=2;
   UPDATE employee SET birthday='1997-11-23',name='Rabia' WHERE id=2;
   ```

4. #### Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.

```sql
DELETE FROM employee WHERE id=3;
DELETE FROM employee WHERE name='Mason';
DELETE FROM employee WHERE email='mravenhill3@nifty.com';
DELETE FROM employee WHERE birthday='1996-12-15';
DELETE FROM employee WHERE name='Michal';
```







## Patika.dev SQL Ödev 9

1. **city** tablosu ile **country** tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

```sql
SELECT city,country FROM city
INNER JOIN country ON country.country_id=city.country_id;
```

2. **customer** tablosu ile **payment** tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

   ```sql
   SELECT payment_id,first_name,last_name FROM customer
   INNER JOIN payment ON payment.customer_id=customer.customer_id;
   ```

3. **customer** tablosu ile **rental** tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

   ```sql
   SELECT rental_id,first_name,last_name FROM rental
   INNER JOIN customer ON rental.customer_id=customer.customer_id;
   ```

   
   
   
   
   
   
   
   ## Patika.dev SQL Ödev 10

1. **city** tablosu ile **country** tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.

```sql
SELECT city,country FROM city
LEFT JOIN country ON city.country_id=country.country_id;
```

2. **customer** tablosu ile **payment** tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.

   ```sql
   SELECT payment_id,first_name,last_name FROM payment
   RIGHT JOIN customer ON customer.customer_id=payment.customer_id;
   ```

3. **customer** tablosu ile **rental** tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.

   

```sql
SELECT rental_id,first_name,last_name FROM rental
FULL JOIN customer ON customer.customer_id=rental.customer_id;
```








## Patika.dev SQL Ödev 11

1. **actor** ve **customer** tablolarında bulunan **first_name** sütunları için tüm verileri sıralayalım.

```sql
(SELECT first_name FROM actor)
UNION
(SELECT first_name FROM customer);
```

2. **actor** ve **customer** tablolarında bulunan **first_name** sütunları için kesişen verileri sıralayalım.

```sql
(SELECT first_name FROM actor)
INTERSECT 
(SELECT first_name FROM customer);
```

3. **actor** ve **customer** tablolarında bulunan **first_name** sütunları için ilk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralayalım.

```sql
(SELECT first_name FROM actor)
EXCEPT 
(SELECT first_name FROM customer);
```

4. İlk 3 sorguyu tekrar eden veriler için de yapalım.

```sql
(SELECT first_name FROM actor)
UNION ALL
(SELECT first_name FROM customer);
```

```sql
(SELECT first_name FROM actor)
INTERSECT ALL
(SELECT first_name FROM customer);
```

```sql
(SELECT first_name FROM actor)
EXCEPT ALL
(SELECT first_name FROM customer);
```

















## Patika.dev SQL Ödev 12

1. **film** tablosunda film uzunluğu **length** sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan büyük fazla kaç tane film vardır?

   ```sql
   SELECT COUNT(*) FROM film
   WHERE length>
   (
   SELECT AVG(length) FROM film
   );
   ```

2. **film** tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?

   ```sql
   1. SELECT COUNT(*) FROM film
      WHERE rental_rate =
      (
      SELECT MAX(rental_rate) FROM film
      );
   ```

3. **film** tablosunda en düşük rental_rate ve en düşük replacement_cost değerlerine sahip filmleri sıralayınız.

   ```sql
   1. SELECT title FROM film
      WHERE film_id=any
      (
      SELECT film_id FROM film
      	WHERE rental_rate=
      	(
      	SELECT MIN(rental_rate) FROM film
      	)
      	AND 
      	replacement_cost=
      	(
      	SELECT MIN(replacement_cost) FROM film
      	)
      	);
   
   
   ```

4. **payment** tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.

   ```sql
   SELECT first_name,last_name
   FROM customer 
   JOIN payment 
   ON ( payment.customer_id = customer.customer_id )
   WHERE amount = ( SELECT MAX(amount) from payment );
   ```

   



