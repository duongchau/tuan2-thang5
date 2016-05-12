#Tìm hiểu dịch vụ DNS
============

-[Mục lục ] (#content)
     <ul>
     <ul>
    <li>[1.Tổng quát chung? ] (#tqc)
	<ul>
	<li>[1.1 Khái niệm](#kn)
	<li>[1.2 Công dụng](#cd)
      </ul>
    <li>[2.Cấu trúc dịch vụ DNS? ](#ctdns)
	<ul>
	<li>[2.1 Có những thành phần nào?](#tp)
	<li>[2.2 Khái niệm các thành phần](#kntp)
	</ul>
    <li>[3. Cơ chế của dịch vụ DNS](#ccdns)
	<ul>
	<li>[3.1 DNS hoạt động như thế nào](#hddns)
	<li>[3.2 Cơ chế tương tác giữa các thành phần](#ccttdns)
	</ul>
    <li>[4.Triển khai dịch vụ DNS](#tkdns)
          <ul>
        <li>[4.1. Áp dụng thực tế ](#adtt)
        <li>[4.2. Cách cài đặt dịch vụ DNS ](#csd)
        </ul>
    <li>[5. Lời cảm ơn](#tks)
    </ul>
	
<a name="tqc"></a>
##1.Tổng quát chung:

<a name="kn"></a>
### 1.1. Khái niệm:
DNS là từ viết tắt trong tiếng Anh của Domain Name System, là hệ thống phân giải tên miền được phát minh vào năm 1984 cho Internet, chỉ một hệ thống cho phép thiết lập tương ứng giữa địa chỉ IP và tên miền.
Hiện nay hệ thống tên miền được phân thành nhiêu cấp : 

<img src=http://img.prntscr.com/img?url=http://i.imgur.com/kDYK0K4.png>

- Gốc (Domain root) : Nó là đỉnh của nhánh cây của tên miền. Nó có thể biểu diễn đơn giản chỉ là dấu chấm “.” 

- Tên miền cấp một (Top-level-domain) : gồm vài kí tự xác định một nước, khu vưc hoặc tổ chức. Nó đươc thể hiện là “.com” , “.edu” …. 

- Tên miền cấp hai (Second-level-domain): Nó rất đa dạng có thể là tên một công ty, một tổ chức hay một cá nhân. 

- Tên miền cấp nhỏ hơn (Subdomain) : Chia thêm ra của tên miền cấp hai trở xuống thường được sử dụng như chi nhánh, phòng ban của một cơ quan hay chủ đề nào đó. 
VD phân loại tên miền:
- Com : Tên miền này được dùng cho các tổ chức thương mại. 

- Edu : Tên miền này được dùng cho các cơ quan giáo dục, trường học. 

- Net : Tên miền này được dùng cho các tổ chức mạng lớn. 

- Gov : Tên miền này được dùng cho các tổ chức chính phủ. 

- Org : Tên miền này được dùng cho các tổ chức khác. 

<a name="cd"></a>
### 1.2 Công dụng:
Dễ dàng sử dụng và đơn giản: cho phép người dùng truy cập máy tính và tài nguyên mạng với những cái tên dể nhớ.
Khả năng mở rộng: cho phép khối lượng công việc phân giải tên có thể được phân phối trên nhiều server và cơ sở sử liệu.
Tình thống nhất: cho phép địa chỉ IP có thể thay đổi trong khi vẫn giữ nguyên tên máy, làm cho việc xác định vị trì tàu nguyên mạng dể dàng.

<a name="ctdns"></a>
##2.Cấu trúc dịch vụ DNS?:

<a name="tp"></a>
### 2.1 Có những thành phần nào?:
-Để hoạt động được thì DNS phải có 2 thành phần: DNS Server và DNS Client.
=> DNS Server dùng để phân giải tên miền ra IP và ngược lại là IP sang tên miền. Thông qua tìm kiếm trên cơ sở dữ liệu của nó, nếu không có nó sẽ đi hỏi DNS khác.
=> DNS Client dùng để phân giải cho máy người dùng. Khi người dùng truy cập tên miền DNS Client sẽ nhờ sang DNS Server phân giải. 

<a name="kntp"></a>
### 2.2 Khái niệm các thành phần?:
- DNS Server có thể cung cấp các thông tin do Client yêu cầu, và chuyển đến một DNS Server khác để nhờ phân giải hộ trong trường hợp nó không thể trả lời được các truy vấn về những tên miền không thuộc quyền quản lý và cũng luôn sẵn sàng trả lời các máy chủ khác về các tên miền mà nó quản lý. DNS Server lưu thông tin của Zone, truy vấn và trả kết quả cho DNS Client. 
- Phân loại DNS server:
+Primary Server : 
<ul>
<li>Được tạo khi ta add một Primary Zone mới thông qua New Zone Wizard. 
<li>Thông tin về tên miền do nó quản lý được lưu trữ tại đây và sau đó có thể được chuyển sang cho các Secondary Server. 
<li>Các tên miền do Primary Server quản lý thì được tạo và sửa đổi tai Primary Server và được cập nhật đến các Secondary Server.
</ul>

+Secondary Server : 
<ul>
<li>DNS được khuyến nghị nên sử dụng ít nhất là hai DNS Server để lưu cho mỗi một Zone. Primary DNS Server quản lý các Zone và Secondary Server sử dụng để lưu trữ dự phòng cho Primary Server. Secondary DNS Server được khuyến nghị dùng nhưng không nhất thiết phải có.</li>
<li>Secondary Server được phép quản lý domain nhưng dữ liệu về tên miền (domain), nhưng Secondary Server không tạo ra các bản ghi về tên miền (domain) mà nó lấy về từ Primary Server.</li>
<li>Khi lượng truy vấn Zone tăng cao tại Primary Server thì nó sẽ chuyển bớt tải sang cho Secondary Server .Hoặc khi Primary Server gặp sự cố không hoạt động được thì Secondary Server sẽ hoạt động thay thế cho đến khi Primary Server hoạt động trở lại.</li> 
</ul>
+Caching-only Server : 
<ul>
<li>Tất cả các DNS Server đều có khả năng lưu trữ dữ liệu trên bộ nhớ cache của máy để trả lời truy vấn một cách nhanh chóng. Nhưng hê thống DNS còn có một loại Caching-only Server.</li> 
<li>Loại này chỉ sử dụng cho việc truy vấn, lưu giữ câu trả lời dựa trên thông tin có trên cache của máy và cho kết quả truy vấn. Chúng không hề quản lý một domain nào và thông tin mà nó chỉ giới hạn những gì được lưu trên cache của Server.</li> 
<li>Lúc ban đầu khi Server bắt đầu chạy thì nó không lưu thông tin nào trong cache. Thông tin sẽ được cập nhật theo thời gian khi các Client Server truy vấn dịch vụ DNS. Nếu sử dụng kết nối mạng WAN tốc độ thấp thì việc sử dụng caching-only DNS Server là giải pháp hữu hiệu cho phép giảm lưu lượng thông tin truy vấn trên đường truyền.</li> 
<li>Caching-only có khả năng trả lời các câu truy vấn đến Client. Nhưng không chứa Zone nào và cũng không có quyền quản lý bất kì domain nào. Nó sử dụng bộ cache của mình để lưu các truy vấn của DNS của Client. Thông tin sẽ được lưu trong cache để trả lời các truy vấn đến Client.</li>
</ul>
+Stub Server : 
<ul>
<li>Là DNS Server chỉ chứa danh sách các DNS Server đã được authoritative từ Primary DNS.</li>
<li>Sử dụng stub có thể tăng tốc độ phân giải tên và dễ quản lý.</li>
</ul>
-Trong DNS Server có 2 thành phần chính là:
=> Forward lookup zone sẽ phân giải các bản ghi từ Tên sang địa chỉ IP
=> Reverse lookup zone sẽ phân giải các bản ghi từ IP sang Tên
- Là bản ghi cơ sở dữ liệu của DNS, được sử dụng để phục vụ cho quá trình trả lời các truy vấn từ DNS Client.
<ul>
<li>Record Type: Mục đích 
<li>A: Host – Phân giải tên máy thành địa chỉ IP (IPv4) 
<li>MX: Mail exchange – Chỉ đến mail Server trong domain. 
<li>CNAME (Alias): Canonical name – Cho phép một host có thể có nhiều tên. 
<li>NS: Name Server – Chứa địa chỉ IP của DNS Server cùng với các thông tin về domain đó. 
<li>SOA: Start of Authority – Bao gồm các thông tin về domain trên DNS Server. 
<li>SRV: Service – Được sử dụng bởi Active Directory để lưu thông tin về vị trí của Domain Controllers 
<li>AAAA: Host – Phân giải tên máy thành địa chỉ IP (IPv6) 
<li>PTR: Pointer – Phân giải địa chỉ IP thành tên máy. 
</ul>
-DNS Server sử dụng 2 giao thức để hoạt động là TCP và UDP:
=> TCP dùng để đóng gói khi 2 Server DNS trao đổi dữ liệu với nhau. Đảm bảo an toàn cho dữ liệu.
=> UDP dùng để đóng gói khi Client yêu cầu phân giải tên miền.

<a name="ccdns"></a>
##3. Cơ chế của dịch vụ DNS:
<a name="hddns"></a>
###3.1 DNS hoạt động như thế nào?
Với client, DNS là một “hộp đen”. Client gửi thông điệp truy vấn DNS vào hộp đen đó, trong thông điệp chứa tên máy cần xác định địa chỉ IP. Với hệ điều hành Unix, gethostname() là một hàm mà ứng dụng có thể gọi để gửi thông điệp truy vấn. Sau một khoảng thời gian nào đó – từ vài phần nghìn giây đến vài chục giây, client nhận được thông điệp trả lời của DNS chứa địa chỉ IP cần xác định. Vì vậy, với client thì DNS là một dịch vụ xác định IP đơn giản và dễ hiểu. Nhưng “hộp đen” triển khai dịch vụ đó thực sự phức tạp, bao gồm nhiều máy chủ tên (nameserver) đặt khắp nơi trên thế giới và một giao thức ở tầng ứng dụng xác định cách thức trao đổi thông tin giữa các nameserver và giữa nameserver và máy tính.

<img src=http://img.prntscr.com/img?url=http://i.imgur.com/hCwNtMb.png>

<a name="ccttdns"></a>
###3.2 Cơ chế tương tác giữa các thành phần:
<ul>
<li>Bước 1: Trên máy người dùng truy cập Website: htttp://google.com.vn bằng IE. Lập tức IE sẽ nhờ DNS Client phân giải tên miền google.com.vn sang địa chỉ IP.</li>
<li>Bước 2: Gói tin của DNS client sẽ được chuyển xuống tầng Transport và đóng gói giao thức UDP. Sau đó chuyển xuống Network.</li>
<li>Bước 3: Network sẽ đóng IP nguồn là IP máy tính, IP đich sẽ là IP DNS Server. Ta hay nhập ở dòng Preferred DNS.</li>
<li>Bước 4: Đã có IP nguồn và IP đích, dữ liệu sẽ chuyển xuống tầng bên dưới và truyền tới đúng DNS Server.</li> 
<li>Bước 5: Khi yêu cầu gửi tới DNS Server nó sẽ tìm trong cơ sở dữ liệu của mình xem tền miền đó ứng địa chỉ IP của Server Website nào.</li>
<li>Bước 6: Sau khi tìm được nó sẽ gửi lại cho máy có DNS Client yêu cầu.</li>
<li>Bước 7: IP của Server Website đã sẵn sàng cho tầng Network đóng vào gói dữ liệu của gói tin truy cập Website.</li>
</ul>
<a name="tkdns"></a>
##4.Triển khai dịch vụ DNS:
<a name="adtt"></a>
###4.1. Áp dụng thực tế:
Các DNS tốt nhanh nhất: Google, VNPT, FPT, Viettel Singapo
<img src=http://img.prntscr.com/img?url=http://i.imgur.com/8QR9zAL.png>

Hiện tại DNS google được rất nhiều người tin tưởng và sử dụng với tốc độ và sự ổn định khá cao, tuy nhiên cũng còn rất nhiều dịch vụ DNS khác các bạn có thể sử dụng vì có thể vào mỗi thời điểm tốc độ DNS sẽ nhanh chậm khác nhau. Ở Việt Nam thì bạn có thể tham khảo các DNS của các nhà mạng FPT, VNPT, Viettel.
-DNS Google
<ul>
<li>8.8.8.8</li>
<li>8.8.4.4</li>
</ul>
-DNS VNPT: 
<ul>
<li>203.162.4.191</li>
<li>203.162.4.190</li>

-DNS Viettel: 
<ul>
<li>203.113.131.1</li>
<li>203.113.131.2</li?
</ul>

-DNS FPT:
<ul>
<li>210.245.24.20</li>
<li>210.245.24.22</li>
</ul>


<a name="csd"></a>
###4.2. Cách cài đặt dịch vụ DNS:
**Cài đặt trên linux**
-Bước 1: Cài đặt phần mềm DNS server

 `yum install bind`
 
 <img src=http://img.prntscr.com/img?url=http://i.imgur.com/9oFw4xx.png>
 
-Bước 2: Cài đặt phần mềm bind-utils để nslookup

`yum install bind-utils`

<img src=http://img.prntscr.com/img?url=http://i.imgur.com/uyME7qE.png>

-Bước 3: Vào card mạng đặt lại DNS trỏ về DNS Server

`vi /etc/sysconfig/network-scripts/ifcfg-eth16777736`

<img src=http://img.prntscr.com/img?url=http://i.imgur.com/TnyAJkg.png>

-Bước 4:Khởi động lại Card mạng

`service network restart`

-Bước 5: Sửa trong file named.conf 

`vi /etc/named.conf`

<img src=http://img.prntscr.com/img?url=http://i.imgur.com/K73V5M2.png>

<img src=http://img.prntscr.com/img?url=http://i.imgur.com/xshzVJ1.png>	

<img src=http://img.prntscr.com/img?url=http://i.imgur.com/KLFBn7O.png>

-Bước 6: Sửa file phân giải thuận

`vi /var/named/hanu.thuan`

<img src=http://img.prntscr.com/img?url=http://i.imgur.com/Z539daW.png>

-Bước 7: Sửa file phân giải nghịch

`vi /var/named/hanu.nguoc`

<img src=http://img.prntscr.com/img?url=http://i.imgur.com/8hMyayb.png>

-Bước 8: Cấu hình khởi động dịch vụ khi khởi động lại server

`chkconfig named on`
-Bước 9: Khởi động lại dịch vụ DNS

`service named start`
-Bước 10: Khởi động lại máy

`reboot`
-Bước 11: : Kiểm tra sau khi thiết lập:
=> Dùng lệnh nslookup
=> set type=MX
=> mail.hanu.vn
**note:** nhớ tắt firewall `service iptables stop`

<a name="tks"></a>
##5. Lời cảm ơn
Mình đã giới thiệu đôi nét về dịch vụ DNS mong giúp ích cho các bạn trong quá trình sử dụng.
 
Cảm ơn các bạn đã đọc hết bài viết này. Tôi hoan nghênh mọi ý kiến đóng, góp xin hãy post lên blog của tôi hoặc có thể commit lên github này.


