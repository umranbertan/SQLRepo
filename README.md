# SQLRepo
DBms PostgreSQL SQL homework-1
***
# ÖDEV 1

### 1-Film tablosunda bulunan title ve description sütunlardaki verileri sıralayınız.

```
SELECT title, description FROM film;
```

### 2- Film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu(length) 60 dan büyük  **VE** 75 ten küçük olma koşullarıyla sıralayınız.

```
SELECT * FROM film
where  length >60 AND  length < 75 ;
```

### 3-Film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 **VE** replacement_cost 12.99 **VEYA** 28.99 olma koşullarıyla sıralayınız.

```
ELECT * FROM film
where  rental_rate =0.99 AND replacement_cost = 12.99 OR replacement_cost = 28.99 ;
```

### 4- customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?

```
SELECT * FROM customer
WHERE first_name = 'Mary';
```

### 5- film rablosundaki uzunluğu(length) 50 den büyük olmayıp aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.

```
SELECT * FROM film
WHERE NOT length > 50 AND (NOT (rental_rate = 2.99 OR rental_rate = 4.99 ));

```
***
# ÖDEV 2
### 1-Film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)
```
SELECT replacement_cost FROM film
WHERE (replacement_cost BETWEEN 12.99 AND 16.99) ;
```
### 2-actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)
```
SELECT first_name, last_name FROM actor
WHERE first_name IN ('Penelope', 'Nick' , 'Ed') ;

```
### 3- film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)
```
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

```
SELECT DISTINCT replacement_cost FROM film;

```
### 2- film tablosunda bulunan relacement_cost sütununda birbirinden farklı kaç tane veri vardır?

```
SELECT COUNT(DISTINCT replacement_cost) from film;
```
### 3- film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?
```

SELECT count (*) from film
where title LIKE 'T%' and rating = 'G' ;
```
### 4-country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?
```
SELECT count (country) from country
WHERE length (country) = 5;
```

### 5-city tablosundaki şehir isimlerinin kaçtanesi 'R' veya r karakteri ile biter?

```
SELECT count (city) from city
WHERE city ILIKE '%R';

```






