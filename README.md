# SQLRepo
DBms PostgreSQL SQL homework-1
***
# ÖDEV 1

### 1-Film tablosunda bulunan title ve description sütunlardaki verileri sıralayınız.

```sql
SELECT title, description FROM film;
```

### 2- Film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu(length) 60 dan büyük  **VE** 75 ten küçük olma koşullarıyla sıralayınız.

```sql
SELECT * FROM film
where  length >60 AND  length < 75 ;
```

### 3-Film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 **VE** replacement_cost 12.99 **VEYA** 28.99 olma koşullarıyla sıralayınız.

```sql
ELECT * FROM film
where  rental_rate =0.99 AND replacement_cost = 12.99 OR replacement_cost = 28.99 ;
```

### 4- customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?

```sql
SELECT * FROM customer
WHERE first_name = 'Mary';
```

### 5- film rablosundaki uzunluğu(length) 50 den büyük olmayıp aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.

```sql
SELECT * FROM film
WHERE NOT length > 50 AND (NOT (rental_rate = 2.99 OR rental_rate = 4.99 ));

```
***
# ÖDEV 2
### 1-Film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)
```sql
SELECT replacement_cost FROM film
WHERE (replacement_cost BETWEEN 12.99 AND 16.99) ;
```
### 2-actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)
```sql
SELECT first_name, last_name FROM actor
WHERE first_name IN ('Penelope', 'Nick' , 'Ed') ;

```
### 3- film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)
```sql
SELECT rental_rate, replacement_cost FROM film
WHERE rental_rate IN (0.99, 2.99, 4.99) and replacement_cost IN (12.99, 15.99, 28.99);
```
***
# ÖDEV3  
### 1- **country** tablosunda bulunan country sütunundaki ülke isimlerinden 'A ' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.

```sql
SELECT country FROM country 
WHERE country LIKE 'A%a';
```

### 2- country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.

```sql
SELECT country FROM country 
WHERE  length (country ) >=  6 AND country LIKE '%n' ;
```

 ### 3- film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.

```sql
SELECT title FROM film
WHERE title ILIKE '%T%T%T%T%';
```

### 4- film tablosunda bulunan tüm sütunlardaki  verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan  büyük olan ve rental_rate 2.99 olan verileri isıralayınız.

```sql
SELECT * FROM film
WHERE title LIKE 'C%' AND length > 90 AND rental_rate =2.99  ;
```
***
# ÖDEV4
### 1- film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.

```sql
SELECT DISTINCT replacement_cost FROM film;

```
### 2- film tablosunda bulunan relacement_cost sütununda birbirinden farklı kaç tane veri vardır?

```sql
SELECT COUNT(DISTINCT replacement_cost) from film;
```
### 3- film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?
```sql

SELECT count (*) from film
where title LIKE 'T%' and rating = 'G' ;
```
### 4-country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?
```sql
SELECT count (country) from country
WHERE length (country) = 5;
```

### 5-city tablosundaki şehir isimlerinin kaçtanesi 'R' veya r karakteri ile biter?

```sql
SELECT count (city) from city
WHERE city ILIKE '%R';

```
***
# ÖDEV5
### 1-film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length ) 5 filmi sıralayınız.
```sql
SELECT * FROM film
where title LIKE '%n'
Order BY (length) desc
limit 5;

```

### 2- film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length )ikinci 5 filmi sıralayınız.
```sql
SELECT * FROM film
where title LIKE '%n'
Order BY (length) asc
offset 5
limit 5;

```

### 3- customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.
```sql
SELECT * FROM customer
where store_id =1 
Order BY (last_name) desc
limit 4
```
***
# ÖDEV6
### 1- film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?

```sql
SELECT avg(rental_rate) from film 

```
### 2- film tablosunda bulunan filmlerden kaçtanesi 'C' karakteri ile başlar?

```sql
SELECT count(rental_rate) from film 
WHERE title LIKE 'C%';
```
### 3- film tablosunda bulunan filmlerden rental_rate 0.99 a eşit olan en uzun(length) film kaç dakikadır?

```sql
SELECT max(length) from film 
WHERE rental_rate= 0.99 ; 
```
### 4- film tablosunda bulunan filmlerin uzunluğu  150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?
```sql
 
SELECT COUNT(DISTINCT replacement_cost) FROM film
WHERE length > 150; 
```
***
# Ödev7
### 1-film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.

```sql
SELECT rating, count(title) from film
GROUP BY rating ;

```

### 2- film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan relacement_cost değerini ve karşılık gelen film sayısını sıralayınız.
```sql
SELECT replacement_cost, count(title)  from film
 group by replacement_cost 
 having count(title) > 50;

```

### 3-customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir?

```sql
 SELECT store_id, count(*) from customer
 group by store_id;
```
### 4- city tablosunda bulunan şehir verilerini country_id sütununa göre grupladıktan sonra en fazla şehir sayısı barındıra country_id bilgisini ve şehir sayısını paylşaınız. 

```sql
SELECT country_id, count(*) from city
 Group by country_id
 order by count(*) desc
 LIMIT	 1;

```
***
#ÖDEV8
### 1- test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.

```sql
CREATE TABLE employee(
id INTEGER Primary key,
	name VARCHAR(50) ,
	birthday DATE,
	email VARCHAR(100)

);
```
### 2- Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.






















```














