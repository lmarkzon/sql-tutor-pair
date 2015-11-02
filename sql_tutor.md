SELECT * FROM invoices
WHERE billing_city LIKE 'Reno%'
AND total > 5.00;

SELECT * FROM tracks
WHERE composer IS null;

SELECT * FROM customers
WHERE company IS null;

SELECT * FROM invoices
WHERE billing_city LIKE 'Redmond%'
ORDER BY total ASC;

SELECT * FROM invoices
WHERE billing_country LIKE 'Germany%'
ORDER BY total DESC LIMIT 10;

SELECT billing_address FROM invoices
WHERE billing_city LIKE 'Cupertino%'
ORDER BY total DESC LIMIT 3;

SELECT * FROM invoices
WHERE billing_city LIKE 'Cupertino%'
OR billing_city LIKE 'Mountain View%';

SELECT COUNT(*) FROM invoices
WHERE billing_city LIKE 'Santiago%';

SELECT country, COUNT(*) FROM customers
GROUP BY country;

SELECT unit_price, COUNT(*) FROM tracks
GROUP BY unit_price;

SELECT name FROM artists
WHERE name LIKE '%smith%';

SELECT city, COUNT(*) FROM employees
GROUP BY city;

SELECT country, COUNT(*) FROM customers
GROUP BY country
ORDER BY COUNT(*) DESC
LIMIT 3;

***********HARD***********
SELECT name, title
FROM artists
INNER JOIN albums
ON artists.id=albums.artist_id;

SELECT name, title
FROM tracks
INNER JOIN albums
ON tracks.album_id=albums.id;

SELECT name, title
FROM artists
INNER JOIN albums
ON artists.id=albums.artist_id
ORDER BY name ASC;
***********HARD***********

SELECT first_name, last_name, total
FROM customers
INNER JOIN invoices
ON customers.id=invoices.customer_id
ORDER BY total DESC;

SELECT *
FROM customers
INNER JOIN invoices
ON customers.id=invoices.customer_id
ORDER BY total DESC
LIMIT 1;

SELECT *
FROM albums
INNER JOIN artists
ON albums.artist_id=artists.id
WHERE name='Aerosmith';

SELECT *
FROM albums
INNER JOIN tracks
ON albums.id=tracks.album_id
WHERE name='Midnight';

SELECT *
FROM artists
INNER JOIN albums
ON artists.id=albums.artist_id
INNER JOIN tracks
ON albums.id=tracks.album_id
WHERE tracks.name='Midnight';

SELECT name, COUNT(*)
FROM albums
INNER JOIN artists
ON artists.id=albums.artist_id
GROUP BY name
ORDER BY name;

SELECT artists.id, artists.name, COUNT(*)
FROM artists
INNER JOIN albums
ON artists.id=albums.artist_id
GROUP BY artists.id, artists.name
ORDER BY COUNT(*) DESC
LIMIT 1;

SELECT albums.id, albums.title, albums.artist_id, COUNT(*)
FROM albums
INNER JOIN tracks
ON albums.id=tracks.album_id
GROUP BY albums.id, albums.title, albums.artist_id
ORDER BY COUNT(*) DESC
LIMIT 1;

SELECT first_name, last_name, SUM(total)
FROM customers
INNER JOIN invoices
ON customers.id=invoices.customer_id
GROUP BY first_name, last_name
ORDER BY SUM(total) DESC, last_name ASC
LIMIT 5;
