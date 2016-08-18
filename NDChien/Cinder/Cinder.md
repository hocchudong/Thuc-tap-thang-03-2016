#Cinder-Block Storage service

###1. Giới thiệu

	Block Storage service cung cấp các khối lưu trữ cho các instances. Có thể thêm các images vào 1 Block Storage device để boot lên instance.

Cinder System Architecture

<img src=http://i.imgur.com/fBL078D.png>

Dịch vụ:
<ul> 
<li>cinder-api: Một ứng dụng WSGI xác nhận và định tuyến các yêu cầu tới service.</li>
<li>cinder-scheduler: Tính toán và định tuyến yêu cầu tới volume service phù hợp. Nó phụ thuộc vào việc cấu hình, có thể scheduling xoay vòng hoặc thông qua Filter Scheduler(default and enables).</li>
<li>cinder-volume: Quản lý các Block Storage devices.</li>
<li>cinder-backup: Backup volume.</li>
</ul>

Thành phần:

- Back-end Storage Devices
- Users and Tenants (Projects): Block Storage service được sử dụng bởi nhiều cloud computing hoặc khách hàng. Để quản lý, ta áp dụng RBAC. Các role có thể được cấu hình tại **policy.json**
	
	For tenants, quota controls are available to limit:

	
	The number of volumes that can be created.
	
	The number of snapshots that can be created.
	
	The total number of GBs allowed per tenant (shared between snapshots and volumes).

- Volumes, Snapshots, and Backups: basic resources offered by the Block Storage service.

WorkFlow

https://netapp.github.io/openstack-deploy-ops-guide/kilo/content/section_cinder-processes.html

Cập nhật tính năng mới

https://specs.openstack.org/openstack/cinder-specs/

###2.Manager volume

Boot from volume 

* Backup incremental

Kích thước volume tăng lên nhanh chóng và sự thay đổi giữa các bản backup ko lớn. Nếu như backup lại tất cả sẽ là dư thừa.
Backup incremental sẽ giải quyết vấn đề trên bằng cách chỉ tạo ra các bản backup những thay đổi so với bản backup trước.

Backup incremental Workflow

<img src=http://i.imgur.com/wU64Y89.png>

<img src=http://i.imgur.com/gGsiqoZ.png>

<img src=http://i.imgur.com/WlxucW8.png>

<img src=http://i.imgur.com/WR61hX2.png>
Tham khảo:

[1]- http://searchstorage.techtarget.com/definition/Cinder-OpenStack-Block-Storage
[2]- http://docs.openstack.org/developer/cinder/devref/architecture.html































-