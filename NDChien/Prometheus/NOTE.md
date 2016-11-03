#NOTE:

==================

###CONSOLES DASHBOARDS:

- Ko quá 5 Graph trên 1 console
- Ko quá 5 ô(dòng) trên mỗi graph 
-Các trình duyệt sẵn có trong /graph của Prometheus server cho phép xem kết quả trên đồ thì hoặc bảng. Ví dụ PromDash hoặc Console templates.
- Grafana dùng Prometheus như là data source.

###INSTRUMETATION:

- Các giá trị metric từ Library, subsystem và service cho ra ý tưởng để code các ứng dụng.
- Services được chia làm 3 loại với monitor là Online-serving, offline-processing, batch jobs. 

###PUSHGATE:

- Được khuyến các sử dụng trong một số trường hợp đặc biệt
- Khi giám sát nhiều trường hợp thông qua Pushgateway thì Pushgateway trở thành điểm thất bại.
- Các Pushgateway expose time series liên tới Prometheus trừ khi đc xóa bằng tay thông qua Pushgateway API.
- Thường đc dùng cho batch job. 

###Data model

<ul>
<li> Prometheus lưu trữ data dưới dạng **time series**. 
<li> Stream of timestamped values có cùng metric và kích thước nhãn(lebel). 
<li> Ngoài việc lưu trữ time series, Prometheus có thể tạo ra các time series. 
</ul>

###Metric names and labels

Các **time series** được định danh duy nhất bằng *metric name* và *key-value pairs* còn được gọi là *labels*. 

`<metric name>{<label name>=<label value>, ...}`

###flexible query language

<ul>
<li>Prometheus cung cấp ngôn ngữ thể hiện (Expression language) để lựu chọn và tổng hợp time series data với thời gian thực. 
<li>Kết quả trả về có thể view như một biểu đồ, bảng hoặc sử dụng bởi các hệ thống khác thông qua HTTP API.
<li>Có 4 loại:

	- Instant vector 
	
	- Range vector 
	
	- Scalar
	
	- String
	
</ul>

https://prometheus.io/docs/querying/basics/

#Alerting

<ul>
<li> Alerting được chia làm 2 phần. Alerting ruler từ Prometheus server gửi cảnh báo tới AlertManager. 
<li> AlertManager quản lý các cảnh báo như im lặng (Silencing), ức chế (Inhibition), tập hợp (Grouping) và gửi thông báo qua email...
	- Grouping: Tập hợp các thông báo giống nhau vào một cảnh báo.
	- Inhibition: Giữ lại các cảnh báo nếu một số cảnh báo khác đã được đưa ra.
	- Silencing: Tắt cảnh báo trong khoảng thời gian nhất định.
	


