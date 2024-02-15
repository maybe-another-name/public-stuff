* https://www.sqlshack.com/query-optimization-techniques-in-sql-server-tips-and-tricks/
## or in _where_
```
SELECT DISTINCT
PRODUCT.ProductID,
PRODUCT.Name
FROM Production.Product PRODUCT
INNER JOIN Sales.SalesOrderDetail DETAIL
ON PRODUCT.ProductID = DETAIL.ProductID
OR PRODUCT.rowguid = DETAIL.rowguid;
```

### suggestion - separate smaller queries
```
SELECT
PRODUCT.ProductID,
PRODUCT.Name
FROM Production.Product PRODUCT
INNER JOIN Sales.SalesOrderDetail DETAIL
ON PRODUCT.ProductID = DETAIL.ProductID
UNION
SELECT
PRODUCT.ProductID,
PRODUCT.Name
FROM Production.Product PRODUCT
INNER JOIN Sales.SalesOrderDetail DETAIL
ON PRODUCT.rowguid = DETAIL.rowguid
```

* results in complex query plan, and two scans instead of one, but still results in fewer reads
* is this something specific to sql server?  i have difficulty understanding this...
	* how can more scans result in fewer reads?
		* seems to create an intermediate 'work-table'


* https://learn.microsoft.com/en-us/troubleshoot/sql/database-engine/performance/troubleshoot-slow-running-queries

