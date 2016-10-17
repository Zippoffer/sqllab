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

Select COUNT(*) FROM InvoiceLine GROUP BY InvoiceLineId

12.
##Provide a query that includes the track name with each invoice line item.

SELECT InvoiceLine.InvoiceLineId, Track.Name AS Track FROM InvoiceLine 
JOIN Track ON Track.TrackId = InvoiceLine.TrackId 
JOIN Album ON Album.AlbumId = Track.AlbumId 
ORDER BY InvoiceLineId

13.
##Provide a query that includes the purchased track name AND artist name with each invoice line item.

SELECT InvoiceLine.InvoiceLineId, Track.Name AS Track, Artist.Name AS ArtistName FROM InvoiceLine 
JOIN Track ON Track.TrackId = InvoiceLine.TrackId 
JOIN Album ON Album.AlbumId = Track.AlbumId 
JOIN Artist ON Album.ArtistId = Artist.ArtistId
ORDER BY InvoiceLineId;

14.
##Provide a query that shows the # of invoices per country. HINT: [GROUP BY](http://www.sqlite.org/lang_select.html#resultset)

SELECT Invoice.Total, Invoice.BillingCountry FROM Invoice
GROUP BY Invoice.BillingCountry

15.
##Provide a query that shows the total number of tracks in each playlist. The Playlist name should be include on the resultant table.

SELECT Playlist.Name AS PlaylistName, Playlist.PlaylistId, COUNT(PlaylistTrack.TrackId) AS NumOfTracks FROM Playlist 
INNER JOIN PlaylistTrack ON PlaylistTrack.PlaylistId = Playlist.PlaylistId 
GROUP BY Playlist.PlaylistId


16.
##Provide a query that shows all the Tracks, but displays no IDs. The resultant table should include the Album name, Media type and Genre.

SELECT Track.Name AS Track, Album.Title AS AlbumName, MediaType.Name AS MediaType, Genre.Name AS Genre FROM Track
JOIN Album ON Album.AlbumId = Track.AlbumId
JOIN MediaType ON MediaType.MediaTypeId = Track.MediaTypeId
JOIN Genre ON Genre.GenreId = Track.GenreId


17.
##Provide a query that shows all Invoices but includes the # of invoice line items.

SELECT COUNT(InvoiceLine.InvoiceId), Invoice.InvoiceId AS InvoiceId FROM Invoice
JOIN InvoiceLine ON InvoiceLine.InvoiceId = Invoice.InvoiceId 
Group BY Invoice.InvoiceId;

18.
##Provide a query that shows total sales made by each sales agent.

SELECT Employee.FirstName ||'  '|| Employee.LastName AS SalesAgent, SUM(Invoice.Total) AS TotalSales FROM Employee
JOIN Customer ON Customer.SupportRepId = Employee.EmployeeId
JOIN Invoice ON Invoice.CustomerId = Customer.CustomerId
WHERE ReportsTo = '2'
GROUP BY Employee.LastName

Steve Johnson: $720.16
Margaret Park: $775.40
Jane Peacock: $833.04

19.
##Which sales agent made the most in sales in 2009?

SELECT Employee.FirstName ||'  '|| Employee.LastName AS SalesAgent, SUM(Invoice.Total) AS TotalSales FROM Employee
JOIN Customer ON Customer.SupportRepId = Employee.EmployeeId
JOIN Invoice ON Invoice.CustomerId = Customer.CustomerId
WHERE Invoice.InvoiceDate LIKE '%2009%'
GROUP BY Employee.LastName

"Steve  Johnson"	"164.34"
"Margaret  Park"	"161.37"
"Jane  Peacock"	"123.75"

20.
##Which sales agent made the most in sales in 2010?

SELECT Employee.FirstName ||'  '|| Employee.LastName AS SalesAgent, SUM(Invoice.Total) AS TotalSales FROM Employee
JOIN Customer ON Customer.SupportRepId = Employee.EmployeeId
JOIN Invoice ON Invoice.CustomerId = Customer.CustomerId
WHERE Invoice.InvoiceDate LIKE '%2010%'
GROUP BY Employee.LastName

"Steve  Johnson"	"136.77"
"Margaret  Park"	"122.76"
"Jane  Peacock"	"221.92"

21.
##Which sales agent made the most in sales over all?

SELECT [Sales Agent], MAX([Total Sales]) FROM ( SELECT Employee.FirstName || ' ' || Employee.LastName AS [Sales Agent],
SUM(Invoice.Total) AS [Total Sales] FROM Employee 
INNER JOIN Customer ON Customer.SupportRepId = Employee.EmployeeId 
INNER JOIN Invoice ON Invoice.CustomerId = Customer.CustomerId
GROUP BY Employee.LastName )

"Jane Peacock"	"833.040000000002"

22.
##Provide a query that shows the # of customers assigned to each sales agent.

SELECT SUM(Customer.CustomerId), Employee.FirstName ||''|| Employee.LastName AS SalesAgent FROM Customer
JOIN Employee ON Customer.SupportRepId = Employee.EmployeeId
WHERE ReportsTo = '2'
GROUP BY Employee.LastName

"546"	"SteveJohnson"
"523"	"MargaretPark"
"701"	"JanePeacock"

23.
##Provide a query that shows the total sales per country. Which country's customers spent the most?

SELECT SUM(Invoice.Total), Invoice.BillingCountry FROM Invoice
Group BY Invoice.BillingCountry

"523.06"	"USA"

24.
##Provide a query that shows the most purchased track of 2013.

SELECT Track.*, SUM(InvoiceLine.TrackId) AS "Total Sales", Invoice.InvoiceDate AS "Year" FROM InvoiceLine
JOIN Invoice ON Invoice.InvoiceId = InvoiceLine.InvoiceId
JOIN Track ON InvoiceLine.TrackId = Track.TrackId
WHERE Invoice.InvoiceDate LIKE "2013%"
GROUP BY InvoiceLine.TrackId
ORDER BY "Total Sales" 
DESC LIMIT 1

"3177"	"Hot Girl"	"249"	"3"	"19"		"1325458"	"267836576"	"1.99"	"3177"	"2013-12-22 00:00:00"

25.
##Provide a query that shows the top 5 most purchased tracks over all.

SELECT Track.*, SUM(InvoiceLine.TrackId) AS "Total Sales" FROM InvoiceLine
JOIN Track ON InvoiceLine.TrackId = Track.TrackId
GROUP BY InvoiceLine.TrackId
ORDER BY "Total Sales" DESC LIMIT 5

26.
##Provide a query that shows the top 3 best selling artists.


27.
##Provide a query that shows the most purchased Media Type.

