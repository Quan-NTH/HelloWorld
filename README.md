# HelloWorld
Dự án mới
Học SQL cấp tốc trong 2 tuần
---
 **Chọn tất cả các hàng trong bảng customer.**
- select *
from [customers];
---
**Hợp tên khách hàng và ngày bán ra.**

- select c.[first_name] + ' ' +c.[last_name] as "Fullname",
		s.[order_date]
from [sales].[customers] as c
INNER JOIN [sales].[orders] as s on c.[customer_id]=s.customer_id
---
**Lọc đơn đặt hàng đã được giao vào tháng 5, và sắp xếp tăng dần theo năm.**

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

