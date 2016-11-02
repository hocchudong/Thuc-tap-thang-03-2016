#Data model

===========

<ul>
<li> Prometheus lưu trữ data dưới dạng **time series**. 
<li> Stream of timestamped values có cùng metric và kích thước nhãn(lebel). 
<li> Ngoài việc lưu trữ time series, Prometheus có thể tạo ra các time series. 
</ul>

###Metric names and labels

Các **time series** được định danh duy nhất bằng *metric name* và *key-value pairs* còn được gọi là *labels*. 

`<metric name>{<label name>=<label value>, ...}`