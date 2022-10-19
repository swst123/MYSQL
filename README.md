1.导入数据
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


2.导出数据
SELECT * FROM ecommerce123
INTO OUTFILE "C:/ProgramData/MySQL/MySQL Server 8.0/uploads/output.CSV"
FIELDS TERMINATED by ',' enclosed by '"'
lines terminated by '\r\n';

3.查询
1.select 列名称 FROM 表名称
SELECT CustomerID,UnitPrice,Quantity FROM ecommerce123
2.选区所有列的数据查询
select * from ecommerce123
3.select distinct 列名称 from 表名称 筛选出不重复的值
select distinct CustomerID,Country from ecommerce
4.select 列名称 from 表名称 where 列 运算符 值(对于文字类型要加'')
select * FROM ecommerce WHERE InvoiceNo=536368
select * FROM ecommerce WHERE Quantity>=1000
select * FROM ecommerce WHERE Country='Japan'
5.order by子句是根据指定列的结果集进行排序，并默认升序排序，在句末加上desc则按降序排序
select * FROM ecommerce WHERE Country='France' ORDER BY UnitPrice DESC
6.合计函数sum max min avg平均值 count计数:COUNT(*)指统计行数
select MAX(UnitPrice) FROM ecommerce
select SUM(Quantity*UnitPrice) FROM ecommerce
select COUNT(*) FROM ecommerce
7.GROUP BY对一列或多列数据进行分组，as将sum计算值重命名为合计，运算数字通过format或convert保留后两位
decimal(38,2)表示最大38位小数点后2位
select Country,FORMAT(SUM(UnitPrice*Quantity),2) as 合计 
FROM ecommerce
GROUP BY Country
ORDER BY 合计 desc
select Country,convert(sum(UnitPrice*Quantity),decimal(38,2)) as 合计
from ecommerce
GROUP BY Country
order BY 合计 DESC
