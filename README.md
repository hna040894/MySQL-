# MySQL-
Database ua_dillards;
HELP TABLE trnsact

SELECT saledate, SUM(amt)
FROM trnsact
GROUP BY saledate
ORDER BY SUM(amt) DESC;

HELP TABLE deptinfo
HELP TABLE skuinfo

SELECT d.deptdesc, COUNT(DISTINCT s.sku)
FROM skuinfo s LEFT JOIN deptinfo d
ON s.dept = d.dept
GROUP BY d.deptdesc
ORDER BY COUNT(DISTINCT s.sku) DESC;
SELECT TOP 1 orgprice
FROM trnsact
WHERE SKU = 3631365
ORDER BY orgprice DESC;

HELP TABLE strinfo;

SELECT TOP 1 color
from skuinfo
where brand='LIZ CLAI'
ORDER BY sku DESC

SELECT TOP 1 sku
FROM trnsact
ORDER BY orgprice DESC;

SELECT COUNT (DISTINCT state)
FROM strinfo;

SELECT COUNT(DISTINCT deptdesc)
FROM deptinfo
WHERE deptdesc LIKE 'e%';

SELECT TOP 10 orgprice, sprice, orgprice-sprice AS margin, saledate
FROM trnsact
WHERE orgprice <> sprice
ORDER BY saledate ASC, margin DESC

SELECT TOP 1 register, saledate, orgprice, sprice
FROM trnsact
WHERE extract(year from saledate)=2004 AND extract(MONTH from saledate)=8 AND extract(DAY from saledate)< 10
ORDER BY orgprice DESC, sprice DESC; 

SELECT DISTINCT brand
FROM skuinfo
WHERE brand LIKE '%liz%';

SELECT store
FROM store_msa
WHERE city IN ('LITTLE ROCK','MEMPHIS','TULSA')
ORDER BY store ASC;
