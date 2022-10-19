# MYSQL
MYSQL CODE
导入数据
CREATE TABLE ecommerce123(
invoiceNo VARCHAR(255),
StockCode VARCHAR(255),
Description VARCHAR(255),
Quantity VARCHAR(255),
InvoiceDate VARCHAR(255),
Unitprice VARCHAR(255),
CustomerID VARCHAR(255),
Country VARCHAR(255)
);
load data infile "C:/ProgramData/MySQL/MySQL Server 8.0/uploads/econommerdata.CSV"
into table ecommerce123
FIELDS TERMINATED by ',' enclosed by '"'
lines terminated by '\n' ignore 1 lines;
