#Alerting

==============

<ul>
<li> Alerting được chia làm 2 phần. Alerting ruler từ Prometheus server gửi cảnh báo tới AlertManager. 
<li> AlertManager quản lý các cảnh báo như im lặng (Silencing), ức chế (Inhibition), tập hợp (Grouping) và gửi thông báo qua email...
	- Grouping: Tập hợp các thông báo giống nhau vào một cảnh báo.
	- Inhibition: Giữ lại các cảnh báo nếu một số cảnh báo khác đã được đưa ra.
	- Silencing: Tắt cảnh báo trong khoảng thời gian nhất định.
	
