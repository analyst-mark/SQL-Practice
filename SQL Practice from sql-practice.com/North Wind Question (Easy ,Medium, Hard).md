



## Easy

1. Show the category_name and description from the categories table sorted by category_name.

![](src-img/Pasted%20image%2020230525125929.png)

![](src-img/Pasted%20image%2020230525125940.png)

2. Show all the contact_name, address, city of all customers which are not from 'Germany', 'Mexico', 'Spain'

![](src-img/Pasted%20image%2020230525130118.png)

![](src-img/Pasted%20image%2020230525130132.png)

3. Show order_date, shipped_date, customer_id, Freight of all orders placed on 2018 Feb 26

![](src-img/Pasted%20image%2020230525130416.png)

![](src-img/Pasted%20image%2020230525130422.png)

4.  Show the employee_id, order_id, customer_id, required_date, shipped_date from all orders shipped later than the required date

![](src-img/Pasted%20image%2020230525130605.png)

![](src-img/Pasted%20image%2020230525130611.png)

5. Show all the even numbered Order_id from the orders table

![](src-img/Pasted%20image%2020230525130913.png)

![](src-img/Pasted%20image%2020230525130921.png)

6. Show the city, company_name, contact_name of all customers from cities which contains the letter 'L' in the city name, sorted by contact_name

![](src-img/Pasted%20image%2020230525131107.png)

![](src-img/Pasted%20image%2020230525131114.png)

7. Show the company_name, contact_name, fax number of all customers that has a fax number. (not null)

![](src-img/Pasted%20image%2020230525131217.png)

![](src-img/Pasted%20image%2020230525131223.png)

8. Show the first_name, last_name of the most recently hired employee.

![](src-img/Pasted%20image%2020230525131418.png)

or  using max

![](src-img/Pasted%20image%2020230525131439.png)

![](src-img/Pasted%20image%2020230525131500.png)

9. Show the average unit price rounded to 2 decimal places, the total units in stock, total discontinued products from the products table.

![](src-img/Pasted%20image%2020230525132154.png)

![](src-img/Pasted%20image%2020230525132159.png)


## Medium

1. Show the ProductName, CompanyName, CategoryName from the products, suppliers, and categories table

![](src-img/Pasted%20image%2020230525153334.png)

![](src-img/Pasted%20image%2020230525153340.png)

2. Show the category_name and the average product unit price for each category rounded to 2 decimal places.

![](src-img/Pasted%20image%2020230525153515.png)

![](src-img/Pasted%20image%2020230525153521.png)

3.   Show the city, company_name, contact_name from the customers and suppliers table merged together.  
	Create a column which contains 'customers' or 'suppliers' depending on the table it came from.

![](src-img/Pasted%20image%2020230525153847.png)

![](src-img/Pasted%20image%2020230525153852.png)

## Hard

1. Show the employee's first_name and last_name, a "num_orders" column with a count of the orders taken, and a column called "Shipped" that displays "On Time" if the order shipped on time and "Late" if the order shipped late.  
  
	Order by employee last_name, then by first_name, and then descending by number of orders.

![](src-img/Pasted%20image%2020230525180000.png)

![](src-img/Pasted%20image%2020230525180006.png)