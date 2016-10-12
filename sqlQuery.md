1.
##Provide a query showing Customers (just their full names, customer ID and country) who are not in the US.


SELECT Customer.FirstName , Customer.LastName , Customer.CustomerId , Customer.Country FROM Customer
WHERE Customer.Country <> 'USA'


2.
##Provide a query only showing the Customers from Brazil.


SELECT Customer.FirstName , Customer.LastName , Customer.CustomerId , Customer.Country FROM Customer
WHERE Customer.Country = 'Brazil'


3.
##Provide a query showing the Invoices of customers who are from Brazil. The resultant table should show the customer's full name, Invoice ID, Date of the invoice and billing country.


SELECT Invoice.InvoiceId, Invoice.InvoiceDate, Invoice.BillingCountry , Customer.FirstName , Customer.LastName FROM Invoice
JOIN Customer ON Invoice.CustomerId = Customer.CustomerId
WHERE Customer.Country = "Brazil"


4.
##Provide a query showing only the Employees who are Sales Agents.


SELECT Employee.FirstName, Employee.LastName FROM Employee
WHERE ReportsTo = '2'


5.
##Provide a query showing a unique list of billing countries from the Invoice table.


SELECT DISTINCT Invoice.BillingCountry FROM Invoice


6.
##Provide a query showing the invoices of customers who are from Brazil.


SELECT Invoice.InvoiceId, Customer.FirstName, Customer.LastName FROM Invoice
JOIN Customer ON Invoice.CustomerId = Customer.CustomerId
WHERE Customer.Country = 'Brazil';


7.
##Provide a query that shows the invoices associated with each sales agent. The resultant table should include the Sales Agent's full name.


SELECT *, Employee.Title FROM Invoice.*
JOIN Customer ON Invoice.CustomerId = Customer.CustomerId
JOIN Employee ON Customer.SupportRepId = Employee.EmployeeId
WHERE Employee.Title = 'Sales Support Agent'


8.
##Provide a query that shows the Invoice Total, Customer name, Country and Sale Agent name for all invoices and customers.


SELECT Invoice.Total, Customer.FirstName, Customer.LastName, Customer.Country, Employee.Title, Employee.FirstName, Employee.LastName FROM Invoice
JOIN Customer ON Invoice.CustomerId = Customer.CustomerId
JOIN Employee ON Customer.SupportRepId = Employee.EmployeeId
WHERE Employee.Title = 'Sales Support Agent';


9.
##How many Invoices were there in 2009 and 2011? What are the respective total sales for each of those years?


SELECT COUNT(InvoiceDate) FROM Invoice WHERE Invoice.InvoiceDate LIKE "2009%"       83
SELECT COUNT(InvoiceDate) FROM Invoice WHERE Invoice.InvoiceDate LIKE "2011%"				83
SELECT SUM(Total) FROM Invoice WHERE DATE(InvoiceDate) LIKE "2009%"									449.46
SELECT SUM(Total) FROM Invoice WHERE DATE(InvoiceDate) LIKE "2011%"									469.58


10.
##Looking at the InvoiceLine table, provide a query that COUNTs the number of line items for Invoice ID 37.


SELECT COUNT(InvoiceId) FROM InvoiceLine WHERE InvoiceLine.InvoiceId LIKE "37"


11.
##Looking at the InvoiceLine table, provide a query that COUNTs the number of line items for each Invoice. HINT: GROUP BY

