# sqllab



SELECT FirstName || " " || LastName AS Name FROM Customer
WHERE Name LIKE "%m%";
SELECT * FROM Customer
Join Employee ON Customer.SupportRepId = Employee.EmployeeId;
SELECT Genre.Name FROM Genre
JOIN Track ON Genre.GenreId = Track.GenreId
JOIN InvoiceLine ON Track.TrackId = InvoiceLine.TrackId
JOIN Invoice ON InvoiceLine.InvoiceId = Invoice.InvoiceId
JOIN Customer ON Invoice.CustomerId = Customer.CustomerId;
SELECT * FROM Genre
JOIN Track ON Genre.GenreId = Track.GenreId
JOIN InvoiceLine ON Track.TrackId = InvoiceLine.TrackId
JOIN Invoice ON InvoiceLine.InvoiceId = Invoice.InvoiceId
JOIN Customer ON Invoice.CustomerId = Customer.CustomerId
WHERE Customer.Country = "Canada"
GROUP BY Customer.FirstName;
SELECT Employee.FirstName || " " || Employee.LastName AS "Name" FROM Employee
JOIN Customer ON Employee.EmployeeId = Customer.SupportRepId
JOIN Invoice ON Customer.CustomerId = Invoice.CustomerId
JOIN InvoiceLine ON Invoice.InvoiceId = InvoiceLine.InvoiceId;

SELECT Customer.FirstName || " " || Customer.LastName || " " || Customer.CustomerId || " " || Customer.Country FROM Customer
WHERE Customer.Country <> 'USA';
SELECT Customer.FirstName || " " || Customer.LastName || " " || Customer.CustomerId || " " || Customer.Country FROM Customer
WHERE Customer.Country = 'Brazil';
