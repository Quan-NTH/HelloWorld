# HelloWorld
Dự án mới

Học SQL cấp tốc trong 2 tuần

**NGÀY 1: SELECT FROM**
 
-Chọn tất cả các hàng trong bảng customer.

	select *
	from [customers];

-Chọn những khách hàng không trùng tên 


	select distinct *
 	from [customers];

**NGÀY 2: JOIN.**

-Hợp tên khách hàng và ngày bán ra

	select 	c.[first_name] + ' ' +c.[last_name] as "Fullname",
		s.[order_date]
	from [sales].[customers] as c
	INNER JOIN [sales].[orders] as s on c.[customer_id]=s.customer_id

**NGÀY 3: GROUP BY, WHERE, ORDER BY**

-Lọc đơn đặt hàng đã được giao vào tháng 5, và sắp xếp tăng dần theo năm.

-WHERE lọc trước group by
 
 	select [OrderID],
 		count(*) as "TotalOrders",
 		year([ShippedDate]) as "năm", 
  		MONTH([ShippedDate]) as "tháng"
	from [dbo].[Orders]
	where month([ShippedDate])=5
	group by [OrderID], 
	 	YEAR([ShippedDate]), 
  		 MONTH([ShippedDate])
	order by YEAR([ShippedDate]) asc

 **NGÀY 4: HAVING**

-HAVING đứng sau group by
 
-Lọc ra nhà cung cấp sản phẩm có tổng số lượng hàng trong kho lớn hơn 30 và có trung bình đơn giá có giá trị dưới 50 

	select 	[SupplierID], 
 		sum([UnitsInStock]) as "SumUnitStock", 
   		avg([UnitPrice]) as "AvgPrice"
	from [dbo].[Products]
	group by [SupplierID]
	having sum([UnitsInStock])>30 and avg([UnitPrice])<50

-Hãy cho biết tổng số tiền vận chuyển của từng tháng, trong nửa năm sau của năm 1996

-Sắp xếp theo tháng tăng dần

-Tổng số tiền vận chuyển >1000

	select 	sum([Freight]) as "SumFreight", 
 		MONTH([ShippedDate]) as "Tháng"
	from [dbo].[Orders]
	where [ShippedDate] between '1996-07-01' and '1996-12-31'
	group by MONTH([ShippedDate])
	having sum([Freight])>1000
	order by MONTH([ShippedDate]) asc 

-Những thành phố có số đơn hàng lớn hơn 16, sắp xếp theo tổng số lượng giảm dần

	select 	[ShipCity], 
 		count([OrderID]) as "Tổng đơn hàng"
	from [dbo].[Orders]
	group by [ShipCity]
	having count([OrderID]) >16
	order by count([OrderID]) desc

**NGÀY 5: AVG, SUM, COUNT**

1.TÍNH TB UnitPrice và tính tổng Quantity tử bảng OrderDetails
	

	SELECT 	AVG([UnitPrice]) AS [avg_UnitPrice],
		SUM([Quantity]) AS [Tong_soluong]
	FROM [Order Details];  

2.Đếm các Region khác nhau từ bảng Customers

	SELECT COUNT(DISTINCT [Region]) AS [Number of Region]	
	FROM [dbo].[Customers];	

3.tính tổng các CategoryID và tổng các CategoryID khác nhau từ bảng Products
	
 	
  	SELECT 
		SUM([CategoryID]) AS [ALL],
		SUM(DISTINCT[CategoryID]) AS [DISTINCT]
	FROM  [Northwind].[dbo].[Products];

**Ngày 6: ÔN TẬP**

1.Hãy cho biết khách hàng nào đặt nhiều hơn 20 đơn hàng, sắp xếp theo thứ tự tổng số đơn hàng giảm dần

	select [CustomerID], count([OrderID]) as "Số đơn"
	from [dbo].[Orders]
	group by [CustomerID]
	having count([OrderID])>20
	order by count([OrderID]) desc

2.Hãy lọc ra các nhân viên có tổng số đơn hàng lớn hơn hoặc bằng 100, sắp xếp theo tổng số đơn hàng giảm dần

	select [EmployeeID], count([OrderID]) as "Tổng đơn"
	from [dbo].[Orders]
	group by[EmployeeID]
	having count([OrderID])>=100
	order by count([OrderID]) desc

3.Hãy cho biết những thể loại nào có số sản phẩm khác nhau lớn hơn 11

	select [CategoryID], count([ProductID]) as "Số sản phẩm"
	from[dbo].[Products]
	group by [CategoryID]
	having count([ProductID])>11

4.Hãy cho biết những thể loại nào có số tổng số lượng sản phẩm trong kho lớn hơn 350

	select [CategoryID], sum([UnitsInStock]) as "Tổng số lượng sp"
	from [dbo].[Products]
	group by[CategoryID]
	having sum([UnitsInStock])>350

5.Hãy cho biết những quốc gia nào có nhiều hơn 7 đơn hàng

	select [ShipCountry], count([OrderID]) as "Số đơn"
	from [dbo].[Orders]
	group by [ShipCountry]
	having count([OrderID])>7

6.Hãy cho biết những ngày nào có nhiều hơn 5 đơn hàng được giao, sắp xếp tăng dần theo ngày giao hàng

	select [ShippedDate], count([OrderID]) as " số đơn"
	from [dbo].[Orders]
	group by[ShippedDate]
	having count([OrderID])>5
	order by  [ShippedDate] asc

7.Hãy cho biết các quốc gia bắt đầu bằng chữ a hoặc g và có số lượng đơn hàng lớn hơn 29

	
 	select [ShipCountry], count([OrderID]) as "Số đơn"
	from [dbo].[Orders]
	where [ShipCountry] like '[A,G]%'
	group by[ShipCountry]
	having count([OrderID])>29
	order by count([OrderID]) desc

8.Hãy cho biết những thành phố nào có số lượng đơn hàng được giao là khác 1 và 2, ngày đặt hàng từ '1977-04-01' đến '1977-08-31'

	SELECT ShipCity,COUNT(*) AS Tongdonhang
	FROM Orders
	WHERE OrderDate BETWEEN '1997-04-01' AND '1997-08-31'
	GROUP BY ShipCity
	HAVING COUNT(*)  <> 1 AND COUNT(*) <> 2

 **NGÀY 7:TRUY VẤN NHIỀU BẢNG"**

Từ 3 bảng customers, orders, shippers in ra mã đơn hàng, tên khách hàng, tên công ty vận chuyển, chỉ ra các đơn hàng giao đến uk năm 1997

Cách 1
	
 	select o.OrderID, c.ContactName, s.CompanyName
	from [dbo].[Customers] as c, [dbo].[Orders] as o, [dbo].[Shippers] as s
	where o.CustomerID=c.CustomerID and o.ShipVia=s.ShipperID
	group by o.OrderID, c.ContactName, o.ShipCountry, year(o.OrderDate), s.CompanyName
	having o.ShipCountry like'UK' and year(o.OrderDate) = '1997'

Cách 2: Tối ưu hơn

	Select o.ShipCountry, o.OrderID, c.ContactName
	from [dbo].[Customers] as c, [dbo].[Orders] as o, [dbo].[Shippers] as s
	where 	c.CustomerID = o.CustomerID  and 
	  	s.ShipperID = o.ShipVia and 
	  	Year(o.OrderDate) = 1997 and 
	 	o.ShipCountry IN ('UK')
