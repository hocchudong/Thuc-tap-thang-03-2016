#Giới thiệu về Prometheus

Prometheus là hệ thống giám sát mã nguồn mở. 

**Tính năng:** 

- Data model đa chiều (Các time series được định danh bởi metric name và key/value pairs)
- Ngôn ngữ truy vấn linh hoạt (flexible query language) để thúc đẩy tính đa chiều của dữ liệu. 
- Không phụ thuộc vào phân phối lưu trữ, các node máy chủ tự xử lý. 
- Time series thu thập các hành động thông qua HTTP.
- Pushing time series sử lý các thành phần ko thể tính toán (scraped), được hỗ trợ qua các cổng trung gian.
- Mục tiêu được phát hiện thông qua dịch vụ hoặc cấu hình tĩnh.
- Nhiều chế độ đồ họa và hỗ trợ dashboard.

**Thành phần:** 

- [Prometheus server](https://github.com/prometheus/prometheus) phục vụ cho việc xử lý (scraped) và lưu trữ dữ liệu time series.
- [Client libraties](https://prometheus.io/docs/instrumenting/clientlibs/) phục vụ cho việc tạo các đoạn mã ứng dụng tính toán cho dịch vụ monitor.
- [Push Gateway](https://github.com/prometheus/pushgateway) tạo các metrics từ *short-lived job* cho Prometheus, được coi như là *metric cache*. 
- [GUI-based dashboard](https://prometheus.io/docs/visualization/promdash/) được code bằng Rails và lấy dữ liệu từ SQL.
- [Exporters](https://prometheus.io/docs/instrumenting/exporters/) giúp cho việc tạo ra các metric từ hệ thống bên thứ 3 như Database, Storage, Hardware...
- [Alertmanager](https://github.com/prometheus/alertmanager) đưa ra các cảnh báo như mail...
- Command-line query tool.
- Các công cụ hỗ trợ khác...

Hầu hết các thành phần được viết trên ngôn ngữ lập trình Go.

**Kiến trúc:**

<img src=http://i.imgur.com/kx3f54W.png>

Prometheus thích hợp để giám máy chủ trung tâm, dịch vụ. Cho độ tin cậy cao và chạy độc lập, không phụ thuộc lưu trữ mạng hoặc remote service.

