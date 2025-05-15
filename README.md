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


