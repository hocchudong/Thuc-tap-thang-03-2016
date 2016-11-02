Prometheus

Prometheus là hệ thống giám sát mã nguồn mở. 

Tính năng: 

- Mô hình dữ liệu đa chiều (Các time series được định danh bởi metric name và key/value pairs)
- Ngôn ngữ truy vấn linh hoạt để sử dụng tính đa chiều của dữ liệu. 
- Không phụ thuộc vào phân phối lưu trữ, các node máy chủ tự xử lý. 
- Time series thu thập các hành động thông qua HTTP.
- Pushing time series được hỗ trợ qua các cổng trung gian.
- Mục tiêu được phát hiện thông qua dịch vụ hoặc cấu hình tĩnh.
- Nhiều chế độ đồ họa và hỗ trợ dashboarding.

Thành phần: 

- [Prometheus server](https://github.com/prometheus/prometheus) phục vụ cho việc xử lý và lưu trữ dữ liệu time series.
- [Client libraties](https://prometheus.io/docs/instrumenting/clientlibs/) phục cho cho việc tạo các đoạn mã ứng dựng.
- [Push Gateway](https://github.com/prometheus/pushgateway) tạo các giá trị metric cho server. 
- [GUI-based dashboard](https://prometheus.io/docs/visualization/promdash/) dựa trên Rails/SQL.
- [Exporters](https://prometheus.io/docs/instrumenting/exporters/) (HAProxy, StatsD, Ganglia, etc).
- [Alertmanager](https://github.com/prometheus/alertmanager) (Đang thử nghiệm).
- Command-line query tool.
- Các công cụ hỗ trợ khác...

Hầu hết các thành phần được viết trên ngôn ngữ lập trình Go.

Kiến trúc:

<img src=http://i.imgur.com/kx3f54W.png>
