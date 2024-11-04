# SQL Sorgu Dokümantasyonu

Bu belge, projede kullanılan SQL sorgularının açıklamalarını içermektedir. Bu sorgular, `country` ve `film` tablolarından belirli koşullara göre veri çekmek için tasarlanmıştır.

## Sorgular

### 1. 'A' ile Başlayıp 'a' ile Biten Ülkeleri Seçme
Bu sorgu, `country` tablosundaki ülke isimlerinden büyük/küçük harf duyarlılığı olmadan 'A' ile başlayıp 'a' ile biten tüm kayıtları getirir.

```sql
SELECT * FROM country
WHERE country ILIKE 'A%a';
```

### 2. Belirli Kriterlere Göre Ülkeleri Seçme
Bu sorgu, country tablosundan country ve country_id alanlarını getirir. Bu ülkeler:

country_id 6 veya daha büyük olan,
'n' harfi ile biten,
En az 6 karakter uzunluğunda isimlere sahip olan ülkelerdir.
```sql
SELECT country, country_id FROM country
WHERE country_id >= 6 AND country LIKE '%n' AND LENGTH(country) >= 6;
```
### 3. Başlığında En Az 4 T Harfi Bulunan Filmleri Seçme
Bu sorgu, film tablosundaki başlıklarında en az 4 adet 'T' harfi (büyük/küçük harf duyarsız) bulunan filmleri getirir.

```sql
SELECT title FROM film
WHERE LENGTH(title) - LENGTH(REPLACE(LOWER(title), 't', '')) >= 4;
```

### 4. Belirli Kriterlere Göre Film Seçme
Bu sorgu, film tablosundan şu özelliklere sahip filmleri getirir:

Başlığı 'C' harfi ile başlayan,
Başlık uzunluğu 90 karakterden fazla olan,
rental_rate değeri 2.99 olan.
```sql
SELECT * FROM film
WHERE (title LIKE 'C%' AND LENGTH(title) > 90 AND rental_rate = 2.99);
```
