

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








-- 1-amaliy
SELECT products.product_name, categories.category_name
FROM products
INNER JOIN categories
ON products.category_id = categories.category_id;

-- 2-amaliy

SELECT customers.company_name, orders.order_date
FROM customers
LEFT JOIN orders
ON customers.customer_id = orders.customer_id;


-- 3-amaliy

SELECT territories.territory_id, employees.last_name
FROM employees
RIGHT JOIN employee_territories
ON employees.employee_id = employee_territories.employee_id
RIGHT JOIN territories
ON employee_territories.territory_id = territories.territory_id;

-- 4-vazifa

SELECT categories.category_name, products.product_name
FROM categories
FULL OUTER JOIN products
ON categories.category_id = products.category_id;


