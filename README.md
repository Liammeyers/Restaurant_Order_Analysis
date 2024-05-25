# Restaurant_Order_Analysis
SQL code for Maven Analytics guided project

--Situation-- You've just been hired as a Data Analyst for the Taste of the World Cafe, a restaurant that has diverse menu offerings and serves generous portions

--Assignment-- The Taste of the World Cafe debuted a new menu at the start of the year. You've been asked to dig into the customer data to see which menu items are doing well/not well and what the top customers seem to like best

--Objectives--
  --Explore teh menu_items table to get an idea of what's on the new menu
  --Explore the order_details table to get an idea of the data that's been collected
  --Use both tables to understand how customers are reacting to the new menu

--Explore the menu table

-- 1. View the menu_items table 

SELECT * FROM restaurant_orders.menu_items

-- 2. Find the number of items on the menu.

SELECT COUNT (*) FROM restaurant_orders.menu_items

-- 3. What are the least and most expensive items on the menu?

SELECT * FROM restaurant_orders.menu_items
ORDER BY price;

SELECT * FROM restaurant_orders.menu_items
ORDER BY price DESC;

-- 4. How many Italian dishes are on the menu?

SELECT COUNT(*) FROM restaurant_orders.menu_items
WHERE category = "Italian";

-- 5. What are the least and most expensive Italian dishes on the menu?

SELECT * FROM restaurant_orders.menu_items
WHERE category = "Italian"
ORDER BY price;

SELECT * FROM restaurant_orders.menu_items
WHERE category = "Italian"
ORDER BY price DESC;

-- 6. How many dishes are in each category?

SELECT category,COUNT (menu_item_id) AS num_dishes
FROM restaurant_orders.menu_items
GROUP BY category

-- 7. What is the average dish price within each category?

SELECT category,AVG(price) AS avg_price
FROM restaurant_orders.menu_items
GROUP BY category;

--Explore the orders table

-- 1. View the order_details table

SELECT * FROM restaurant_orders.order_details

-- 2. What is the date range of the table?

SELECT * FROM restaurant_orders.order_details
ORDER BY order_date;

SELECT MIN(order_date), MAX(order_date) FROM restaurant_orders.order_details;

-- 3. How many orders were made within this date range?

SELECT COUNT(DISTINCT order_id) FROM restaurant_orders.order_details;

-- 4. How many items were ordered withing this date range?

SELECT COUNT(*) FROM restaurant_orders.order_details;

-- 5. Which orders had the most number of items?

SELECT order_id, COUNT(item_id) AS num_items
From restaurant_orders.order_details
GROUP BY order_id
ORDER BY num_items DESC;
