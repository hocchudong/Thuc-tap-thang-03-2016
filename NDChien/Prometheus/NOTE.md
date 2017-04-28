#NOTE: Các khái niệm

[1. EXPORTER](#1)

[2. SCRAPING](#2)

[3. CONSOLES DASHBOARDS](#3)

[4. INSTRUMETATION](#4)

[5. PUSHGATE](#5)

[6. DATA MODEL](#6)

[7. FLEXIBLE QUERY LANGUAGE](#7)

[8. ALERTING](#8)

[9. JOBS AND INSTANCES](#9)

==================

<a name="1"></a>
1. EXPORTER

Các thành phần thu thập data và chuyển  tới một URL mà Prometheus server có thể truy cập được gọi là **Exporters**

List các thành phần phục vụ cho việc thu thập: https://github.com/prometheus/node_exporter#collectors

Xem metric từ node_exporter: http://<your-device-ip>:9100/metrics

<a name="2"></a>
2. SCRAPING

**prometheus.yml** Chứa các cấu hình miêu tả `how and which exporters to scrape` 

<a name="3"></a>
3. CONSOLES DASHBOARDS

- Ko quá 5 Graph trên 1 console
- Ko quá 5 ô(dòng) trên mỗi graph 
- Các trình duyệt sẵn có trong /graph của Prometheus server cho phép xem kết quả trên đồ thì hoặc bảng. Ví dụ PromDash hoặc Console templates.
- Grafana dùng Prometheus như là data source.

<a name="4"></a>
4. INSTRUMETATION

- Các giá trị metric từ Library, subsystem và service cho ra ý tưởng để code các ứng dụng.
- Services được chia làm 3 loại với monitor là Online-serving, offline-processing, batch jobs. 

<a name="5"></a>
5. PUSHGATE

- Được khuyến cáo sử dụng trong một số trường hợp đặc biệt.
- Khi giám sát nhiều trường hợp thông qua Pushgateway thì Pushgateway trở thành điểm thất bại.
- Các Pushgateway expose time series liên tới Prometheus trừ khi đc xóa bằng tay thông qua Pushgateway API.
- Thường đc dùng cho batch job. 

<a name="6"></a>
6. DATA MODEL

- Prometheus lưu trữ data dưới dạng **time series**. 
- Stream of timestamped values có cùng metric và kích thước nhãn(label). 
- Ngoài việc lưu trữ time series, Prometheus có thể tạo ra các time series. 

Các **time series** được định danh duy nhất bằng *metric name* và *key-value pairs* còn được gọi là *labels*. 

`<metric name>{<label name>=<label value>, ...}`

<a name="7"></a>
7. FLEXIBLE QUERY LANGUAGE

* Prometheus cung cấp ngôn ngữ thể hiện (Expression language) để lựu chọn và tổng hợp time series data với thời gian thực. 
* Kết quả trả về có thể view như một biểu đồ, bảng hoặc sử dụng bởi các hệ thống khác thông qua HTTP API.
* Có 4 loại:

	- Instant vector: `http_requests_total{job="prometheus",group="canary"}`
	- Range vector: `http_requests_total{job="prometheus"}[5m]`
	- Scalar
	- String: `'these are not unescaped: \n ' " \t'`

https://prometheus.io/docs/querying/basics/

<a name="8"></a>
8. ALERTING

* Alerting được chia làm 2 phần. Alerting ruler từ Prometheus server gửi cảnh báo tới AlertManager. 
* AlertManager quản lý các cảnh báo như im lặng (Silencing), ức chế (Inhibition), tập hợp (Grouping) và gửi thông báo qua email...
	- Grouping: Tập hợp các thông báo giống nhau vào một cảnh báo.
	- Inhibition: Giữ lại các cảnh báo nếu một số cảnh báo khác đã được đưa ra.
	- Silencing: Tắt cảnh báo trong khoảng thời gian nhất định.
* Kết hợp cảnh báo với Plugin Nagios

<a name="9"></a>
9. JOBS AND INSTANCES

Việc Scrap các target được gọi là `instance`. Việc thu thập các instance cùng loại được gọi là 1 `job`

```sh
job: api-server
	instance 1: 1.2.3.4:5670
	instance 2: 1.2.3.4:5671
	instance 3: 5.6.7.8:5670
	instance 4: 5.6.7.8:5671
```

10. RULES

Có 2 loại rule `recording rules` và `alerting rules`.

- Recording rule set of time series được tạo và load thông qua `rule_files`
```sh
<new time series name>[{<label overrides>}] = <expression to record>
job:http_inprogress_requests:sum = sum(http_inprogress_requests) by (job)
```
		
- Alerting rule xác định các điều kiện đưa ra cảnh báo

```sh
ALERT <alert name>
  IF <expression>
  [ FOR <duration> ]
  [ LABELS <label set> ]
  [ ANNOTATIONS <label set> ]
```

