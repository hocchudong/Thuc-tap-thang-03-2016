# Các Project Openstack
###Mục lục
####[1.Kiến trúc của Openstack](#kientruc)
####[2.Các project của Openstack](#project)
#####[2.1.Horizon](#horizon)
#####[2.2.Keystone](#keystone)
#####[2.3.Nova](#nova)
#####[2.4.Glance](#glance)
#####[2.5.Swift](#swift)
#####[2.6.Neutron](#neutron)
#####[2.7.Cinder](#cinder)
#####[2.8.Ceilometer](#ceilometer)
#####[2.9.Heat](#heat)
#####[2.10.Trove](#trove)
####[3.Sự khác nhau giữa Object storage và Block storage](#khacnhau)

<a name="kientruc"></a>
#####1.Kiến trúc của Openstack:
<img src="https://dague.net/wp-content/uploads/2014/08/screenshot_185.png">

<a name="project"></a>
####2.Các project của Openstack:

<a name="horizon"></a>
#####2.1.Horizon-Dashboard:
- Horizon là một module ứng dụng web, cung cấp cho người dùng cuối và người quản trị cloud có một giao diện sử dụng các OpenStack services.
-Horizon API: Cho phép chúng ta phát triển những chức năng tốt hơn so với OpenStack Dashborad cung cấp
<ul>
<li> Tạo cho người dùng khả năng 1 khả năng nhanh chóng để mở rộng bộ dữ liệu trên 1 tập hợp các thông số tùy chỉnh</li>
<li> Cải tiến bổ sung bao gồm việc mở rộng hệ thống RBAC để hỗ trợ các dự án OpenStack Compute, Networking, và Orchestration</li>
</ul>
- Dashboard cung cấp 1 cho quản trị viên và người dùng một giao diện đồ họa để truy cập, cung cấp và tự động hóa các nguồn lực của cloud.
- Khả năng của Dashboard:
<ul>
<li> Cho phép các quản trị viên và người dùng có thể kiểm soát compute, storage, networking.</li>
<li> Cung cấp cho người dùng 1 cái nhìn tổng quát về kích cỡ và trạng thái của cloud. Tạo ra các người dùng và dự án, gán người dùng vào các dự án, thiết lập giới hạn về nguồn lực của các projects.</li>
<li> Dashboard cung cấp 1 cổng thông tin tự phục vụ để cung cấp cho người dùng các tài nguyên trong giới hạn cho phép</li>
</ul>

<a name="keystone"></a>
#####2.2.Keystone-Identity Service:
-Mô hình của Keystone:
<img src="https://allthingsopendotcom.files.wordpress.com/2014/07/keystone.png">
- Keystone cung cấp các dịch vụ nhận dạng cho toàn bộ cơ sở hạ tầng OpenStack, đặt chính sách phân quyền cho các project.
- Các chức năng chính:
<ul>
<li> Xác thực user và vấn đề token để truy cập vào các dịch vụ</li>
<li> Lưu trữ user và người thuê cho vai trò kiểm soát truy cập (role-based access control (RBAC))</li>
<li> Cung cấp catalog của dịch vụ trên cloud</li>
<li> Tạo các chính sách giữa user và dịch vụ</li>
</ul>
- Các thành phần chính của Keystone:
<ul>
<li> Identity: Xác thực về chứng chỉ, dữ liệu của Users, Groups, Projects, Domains và Roles.</li>
<li> Token: Được dùng để xác thực thông tin người dùng khi thông tin người dùng đã được xác minh</li>
<li> Catalog: Cung cấp một đăng ký thiết bị đầu cuối sử dụng để phát hiện điểm cuối.</li>
<li> Policy: Đưa ra các nguyên tắc và giao diện quản lý các nguyên tắc</li>
</ul>

<a name="nova"></a>
#####2.3.Nova-Compute service:
- Là thành phần cơ bản của OpenStack, quản lý vòng đời các máy ảo (RAM, CPU, status)
- Cung cấp cho người dùng khả năng chạy máy ảo, giao diện để quản lý các máy ảo trên nền phần cứng
- Hỗ trợ bởi các hypervisor như: KVM, ESXi, Hyper-V, Xen-server.
- Quản lý mạng nội bộ (LAN): Flat, Flat DHCP, VLAN, IPv6,.
- API với nhiều tính năng và xác thực: Quản lý việc users truy cập vào các tài nguyên và ngăn chặn truy cập trái phép qua lại giữa các users
- Các thành phần của Nova:
<img src="http://docs.openstack.org/developer/nova/_images/Novadiagram.png">
<ul>
<li>Cloud Controller: Là thành phần đại diện và tương tác với các thành phần khác.</li>
<li>API server: Giống như một Web service đầu cuối của Cloud Controller</li>
<li>Compute Controller: Cung cấp các tài nguyên, quản lý các máy ảo</li>
<li>Object Store: Cung cấp dịch vụ lưu trữ</li>
<li>Auth Manager: Cung cấp các dịch vụ xác thực, ủy quyền</li>
<li>Volume Controller: Cung cấp nhanh chóng và lưu trữ kiểu block-storage cho compute services</li>
<li>Network Controller: Cung cấp các mạng ảo cho phép compute service có thể tương tác với nhau và với mạng bên ngoài</li>
<li>Scheduler: Chọn ra compute service phù hợp nhất để lưu máy instances</li>
</ul>

<a name="glance"></a>
#####2.4.Glance-Image service:
- Là nơi cung cấp các dịch vụ khai báo, lưu trữ, quản lý các virtual machine images.
- Hỗ trợ các định dạng khác nhau của hypervisor như: vmdk, iso, ami...
- Chuyển phát image tới Nova để bắt đầu instance, snapshot từ các instance đang chạy có thể được lưu trữ vì vậy máy ảo đó có thể được backup.
- Các thành phần chính:
<ul>
<li>glance-database: Nơi lưu trữ siêu dữ liệu image</li>
<li>glance-registry: Lưu lại và nhận dữ liệu về image (size, type, etc)</li>
</ul>
- Glance-API đóng vai trò quan trọng trong quá trình xử lý image. Có 2 phiên bản của Glance-API (version 1 và version 2)

<a name="swift"></a>
#####2.5.Swift-Object Storage Service:
- Swift là dịch vụ lưu trữ đối tượng trong OpenStack.
- Được thiết kế để cung cấp lưu trữ quy mô lớn dữ liệu có thể được truy cập thông qua các API.
- Nó là hoàn toàn phân phối, lưu trữ nhiều bản sao của từng đối tượng để đạt được tính sẵn sàng cao và khả năng mở rộng.
- Cấu trúc đơn giản của Swift:
<img src="http://i.imgur.com/9CrfyLK.png">


<a name="neutron"></a>
#####2.6.Neutron-Network service:
- Cung cấp dịch vụ về mạng cho OpenStack
<img src="http://i.imgur.com/hWTvdd9.png">
- Các thành phần chính trong OpenStack Networking.
<ul>
<li>Neutron server: Chạy trên các node mạng để phục vụ các API Networking, nó cũng triển khai mô hình mạng và địa chỉ IP cho mỗi cổng, neutron-server và plugin yêu cầu quyền truy cập vào một cơ sở dữ liệu cho lưu trữ liên tục và truy cập vào một hàng đợi thông điệp để liên lạc.</li>
<li>Neutron agent: Chạy trên mỗi node compute để quản lý chuyển mạch ảo</li>
<li>DHCP agent: Cung cấp dịch vụ DHCP cho mạng thuê, hành động này là như nhau trên tất cả các plug-in và chịu trách nhiệm duy trì cấu hình DHCP, Các neutron-dhcp-agent yêu cầu truy cập hàng đợi thông điệp.</li>
<li>L3 agent: Cung cấp L3 / NAT chuyển tiếp để truy cập mạng bên ngoài của máy ảo trên mạng cho thuê. Yêu cầu truy cập hàng đợi thông điệp.</li>
<li>SDN server/services: Cung cấp các dịch vụ mạng bổ sung cho mạng lưới thuê, Những dịch vụ SDN có thể tương tác với các neutron-server, neutron-plugin hoặc plugin-agent thông qua các API REST hoặc các kênh truyền thông khác.</li>
</ul>
- Neutron API Extension: Với việc mở rộng API, người dùng có thể xác định chức năng mạng bổ sung thông qua các plugin Neutron, Biểu đồ này cho thấy mối quan hệ của Neutron API, mở rộng Neutron API và Neutron Plugin nơi giao diện plugin với một SDN Controller - OpenDaylight.
<img src="http://i.imgur.com/opdT9Tr.jpg">
- Neutron Plug-ins:Plugin là giao diện giữa neutron và các công nghệ back-end như SDN, Cisco, VMware NSX để người tiêu dùng của Neutron có thể tận dụng lợi thế của các thiết bị mạng bên thứ 3 hoặc phần mềm.

<a name=""></a>
#####2.7.Cinder-Block Storage Service:
- Cinder là một phần của Nova (nova-volume). Cinder có thể được triển khai độc lập mà không cần dịch vụ OpenStack khác.
- Cinder là tương tự như Amazon Web Services S3 (Simple Storage Service)
- Cấu trúc của Cinder:
<img src="https://varchitectthoughts.files.wordpress.com/2013/11/screen-shot-2013-11-18-at-11-00-24-am.png">
<ul>
<li>Cinder-api: Xác nhận và yêu cầu tìm đường cho dịch vụ Block Storge.Gửi yêu cầu đến Cinder-Scheduler.</li>
<li>Cinder-scheduler: Dựa trên các yêu cầu dịch vụ Cinder-Volume thông qua AMPQ (RabbitMQ hoặc Qpid)</li>
<li>Cinder-Volume: Quản lí các lưu trữ back-end khác, tương tác trực tiếp với phần cứng hoặc phần mềm cung cấp các lưu trữ khối, cung cấp cho người dùng 1 cái nhìn chung về volume</li>
<li>Cinder-backup: Cung cấp các dịch vụ sao lưu các tập Cinder tới OpenStack Swift.</li>
</ul>

<a name="ceilometer"></a>
#####2.8.Ceilometer:
- Project Ceilometer được bắt đầu vào năm 2012 với một mục tiêu đơn giản: thống kê tài nguyên mà người dùng sử dụng. Từ đó tính toán được chi phí sử dụng.
- Thu thập, giám sát mọi thông tin trong các project.
- Tích hợp trong Horizon với quyền Admin.

<a name=""></a>
#####2.9.Heat-Orchestration service:
Cung cấp một cách để tạo và quản lý nguồn tài nguyên điện toán đám mây như storage, networking, computer instances, các ứng dụng với một mẫu.

<a name=""></a>
#####2.10.Trove-Database service:











