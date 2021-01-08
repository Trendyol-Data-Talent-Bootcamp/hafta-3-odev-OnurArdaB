# Ödev 3 - Onur Arda Bodur

# Tabloyu inceleyelim

> ```SELECT * FROM `dsmbootcamp.sample.semi_structured_hw`;```

 - `name`
 - `car.id`
 - `car.model`
 - `manufacture.id`
 - `manufacture.year`
 - `manufacture.country`
 - `purchase.id`
 - `purchase.date`

# Tabloyu kendi alanımıza geçiriyoruz

 

>  **Copy Table** yazısına basarak tablonun bir kopyasını oluşturuyoruz.
>  Sorgu kullanarak oluşturmak için aşağıdaki sorguyuda kullanabiliriz.
 ```
 CREATE TABLE `dsmbootcamp.arda_bodur.semi_structured_hw`AS  
 SELECT * FROM `dsmbootcamp.sample.semi_structured_hw`;
 ```


# Ödev Sorgusu
 ```
SELECT name, car,manufacture.year AS manufacture_year,
	ARRAY(SELECT AS STRUCT purch.id, 
	DATETIME_ADD(DATETIME (purch.date), INTERVAL 3 HOUR)AS date 
		  FROM UNNEST(purchase) AS purch) purchase
FROM `dsmbootcamp.arda_bodur.semi_structured_hw`
LEFT JOIN UNNEST(car) car LEFT JOIN UNNEST(manufacture) manufacture
ON car.id=manufacture.id
ORDER BY name;
 ```
