##Evaluate code and expression using .NET in T-SQL stored procedure, function and trigger##

Extend SQL syntax with the full C# syntax and have the best of both language.

- Access to .NET objects
	- Math
	- Regex
	- String.Format
- Evaluate expression at runtime
	- Use column as code
	- Use column as parameter
- Perform IO Operation
	- DirectoryInfo
	- FileInfo
	- Impersonate

## Download
**[SQLNET.zip](https://zzzprojects.uservoice.com/forums/327759-eval-expression-net) <sub>(~525 KB)</sub>** 

*FREE Version - up to 50 characters

## Eval
**Evaluate and execute the code or expression.**

**Support:**

_Runtime Evaluation_
```sql
CREATE PROCEDURE [dbo].[select_formula]
AS
BEGIN
	SELECT  SQLNET::New('x + y')
		.Val('x', ColumnValueX)
		.Val('y', ColumnValueY)
		.Eval()
	FROM TableFormula
END
```

_Regex_
```sql
CREATE PROCEDURE [dbo].[select_formula]
AS
BEGIN
	SELECT  SQLNET::New('x + y')
		.Val('x', ColumnValueX)
		.Val('y', ColumnValueY)
		.Eval()
	FROM TableFormula
END
```
**[Learn more](http://eval-sql.net/documentations/#more)**

## EXEC SQLNET_EvalResultSet
**Execute a stored procedure to evaluate the code or expression and return a result set.**

**Support:**

_Output result set_
```sql
CREATE PROCEDURE [dbo].[select_desktop_files]
AS
BEGIN
	DECLARE @sqlnet SQLNET = SQLNET::New('
	var dir = new DirectoryInfo(Environment.GetFolderPath(Environment.SpecialFolder.Desktop));
	return dir.GetFiles("*.*").Select(x => x.FullName).OrderBy(x => x).ToList();')
	
	/* SELECT * FROM [desktop_files] ORDER BY path */
	EXEC SQLNET_EvalResultSet @sqlnet
END
```

_Insert result set_
```sql
CREATE PROCEDURE [dbo].[select_desktop_files]
AS
BEGIN
	DECLARE @sqlnet SQLNET = SQLNET::New('
	var dir = new DirectoryInfo(Environment.GetFolderPath(Environment.SpecialFolder.Desktop));
	return dir.GetFiles("*.*").Select(x => x.FullName).OrderBy(x => x).ToList();')
	
	/* SELECT * FROM [desktop_files] ORDER BY path */
	EXEC SQLNET_EvalResultSet @sqlnet
END
```

**[Learn more](http://eval-sql.net/documentations/#more)**

## FREE vs PRO
Features | FREE Version | [PRO Version](http://eval-sql.net/#pro)
------------ | :-------------: | :-------------:
Maximum Characters | 50 | Unlimited
Commercial License | No | Yes
Royalty-Free | No | Yes
Support & Upgrades (1 year) | No | Yes
Learn more about the **[PRO Version](http://eval-sql.net/#pro)**

## Support
Contact our outstanding customer support for any request. We usually answer within the next business day, hour, or minutes!

- [Website](http://eval-sql.net/)
- [Documentation](https://github.com/zzzprojects/Eval-SQL.NET/wiki)
- [Forum](http://zzzprojects.uservoice.com/forums/328452-eval-sql-net)
- sales@zzzprojects.com

## More Projects
  - [NET Entity Framework Extensions](http://www.zzzprojects.com/products/dotnet-development/entity-framework-extensions/)
  - [NET Bulk Operations](http://www.zzzprojects.com/products/dotnet-development/bulk-operations/)
  - [Eval Expression.NET](http://eval-expression.net/)
  - [Eval SQL.NET](http://eval-sql.net/)


