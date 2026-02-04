
-- 1-Vazifa
SELECT  ship_country
FROM orders
WHERE ship_country LIKE 'U%';


-- 2-vazifa
SELECT order_id, customer_id, freight, ship_country
FROM orders
WHERE ship_country LIKE 'N%'
ORDER BY freight DESC
LIMIT 10;


-- 3-vazifa
SELECT first_name, last_name, home_phone, region
FROM employees
WHERE region IS NULL;


-- 4-vazifa

SELECT COUNT(*)
FROM customers
WHERE region IS NOT NULL;


-- 5-vazifa

SELECT country, COUNT(*)
FROM suppliers
GROUP BY country
ORDER BY COUNT(*) DESC;

-- 6-vazifa
SELECT ship_country, SUM(freight)
FROM orders
WHERE ship_region IS NOT NULL
GROUP BY ship_country
HAVING SUM(freight) > 2750
ORDER BY SUM(freight) DESC;