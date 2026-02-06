

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


















06.02.2026
1-vazifa
SELECT
    c.company_name AS customer_company,
    e.first_name || ' ' || e.last_name AS employee_full_name
FROM orders o
JOIN customers c ON o.customer_id = c.customer_id
JOIN employees e ON o.employee_id = e.employee_id
JOIN shippers s ON o.ship_via = s.shipper_id
WHERE c.city = 'London'
  AND e.city = 'London'
  AND s.company_name = 'Speedy Express';

2-vazifa
SELECT
    p.product_name,
    p.units_in_stock,
    s.contact_name,
    s.phone
FROM products p
JOIN categories c ON p.category_id = c.category_id
JOIN suppliers s ON p.supplier_id = s.supplier_id
WHERE p.units_in_stock < 20
  AND p.discontinued = 0
  AND c.category_name IN ('Beverages', 'Seafood');


3-vazifa

 SELECT
    c.company_name,
    o.order_id
FROM customers c
LEFT JOIN orders o ON c.customer_id = o.customer_id
WHERE o.order_id IS NULL;


4-vazifa 
SELECT
    c.company_name,
    o.order_id
FROM orders o
RIGHT JOIN customers c ON c.customer_id = o.customer_id
WHERE o.order_id IS NULL;
