# Tìm hiểu dịch vụ WEB
================
[Mục lục](#content)

[1.Tổng quát dịch vụ WEB](#tqweb)
  <ul>
  <li>[1.1 Khái niệm](#khainiem)
  <li>[1.2 Công dụng](#congdung)
  </ul>

[2. Cấu trúc dịch vụ WEB](#cautruc)
  <ul>
  <li>[2.1 Thành phần](#thanhphan)
  <li>[2.2 Khái niệm từng thành phần](#khainiemtp)
  </ul>

[3. Cơ chế dịch vụ WEB](#coche)
  <ul>
  <li>[3.1 Dịch vụ WEB hoạt động như thế nào?](#hd)
  <li>[3.2 Cơ chế tương tác giữa các thành phần](#cochett)
  </ul>

[4. Triển khai dịch vụ WEB](#trienkhai)
  <ul>
  <li>[4.1 Ứng dụng thực tế](#ungdung)
  <li>[4.2 Cách cài đặt](#caidat)
  </ul>
[5. Lời cảm ơn](#tks)

<a name="tqweb"></a>
##1.Tổng quát dịch vụ WEB


<a name="khainiem"></a>
###1.1 Khái niệm
<ul>
<li>Web Services (tạm dịch là dịch vụ web) là tập hợp các phương thức của một đối tượng mà các Client có thể gọi thực hiện.</li> 
<li>Là một abstract interface, được thể hiện trong HTML dựa trên sự tương tác của User & Web Server.</li>
<li>Là một software application được truy xuất thông qua Web bởi một ứng dụng khác.</li>
</ul>

<a name="congdung"></a>
###1.2 Công dụng
Công dụng chính của website là cung cấp thông tin cho người dùng. website có thể đáp ứng hầu như toàn bộ nhu cầu của con người như: giải trí, tìm kiếm thông tin, mua hàng ....

<a name="cautruc"></a>
##2. Cấu trúc dịch vụ WEB

<a name="thanhphan"></a>
###2.1 Thành phần
Dịch vụ Web gồm có 3 thành phần chính:
<ul>
<li>XML – eXtensible Markup Language.</li>
<li>WSDL – Web Service Description Language.</li>
<li>Universal Description, Discovery, and Integration (UDDI).</li>
<li>SOAP – Simple Object Access Protocol.</li>
</ul>

<a name="khainiemtp"></a>
###2.2 Khái niệm từng thành phần
a) XML – eXtensible Markup Language

Là một chuẩn mở do W3C đưa ra cho cách thức mô tả dữ liệu, nó được sử dụng để định nghĩa các thành phần dữ liệu trên trang web và cho những tài liệu B2B. Về hình thức, XML hoàn toàn có cấu trúc thẻ giống như ngôn ngữ HTML nhưng HTML định nghĩa thành phần được hiển thị như thế nào thì XML lại định nghĩa những thành phần đó chứa cái gì. Với XML, các thẻ có thể được lập trình viên tự tạo ra trên mỗi trang web và được chọn là định dạng thông điệp chuẩn bởi tính phổ biến và hiệu quả mã nguồn mở.

Do dịch vụ Web là sự kết hợp của nhiều thành phần khác nhau nên nó sử dụng các tính năng và đặc trưng của các thành phần đó để giao tiếp. XML là công cụ chính để giải quyết vấn đề này và là kiến trúc nền tảng cho việc xây dựng một dịch vụ Web, tất cả dữ liệu sẽ được chuyển sang định dạng thẻ XML. Khi đó, các thông tin mã hóa sẽ hoàn toàn phù hợp với các thông tin theo chuẩn của SOAP hoặc XML-RPC và có thể tương tác với nhau trong một thể thống nhất.

b)WSDL – Web Service Description Language

WSDL định nghĩa cách mô tả dịch vụ Web theo cú pháp tổng quát của XML, bao gồm các thông tin:
<ul>
<li>Tên dịch vụ</li>
<li>Giao thức và kiểu mã hóa sẽ được sử dụng khi gọi các hàm của dịch vụ Web</li>
<li>Loại thông tin: thao tác, tham số, những kiểu dữ liệu (có thể là giao diện của dịch vụ Web cộng với tên cho giao diện này)</li>
</ul>

Một WSDL hợp lệ gồm hai phần: phần giao diện (mô tả giao diện và phương thức kết nối) và phần thi hành mô tả thông tin truy xuất CSDL. Cả hai phần này sẽ được lưu trong 2 tập tin XML tương ứng là tập tin giao diện dịch vụ và tập tin thi hành dịch vụ. Giao diện của một dịch vụ Web được miêu tả trong phần này đưa ra cách thức làm thế nào để giao tiếp qua dịch vụ Web. Tên, giao thức liên kết và định dạng thông điệp yêu cầu để tương tác với dịch vụ Web được đưa vào thư mục của WSDL.

WSDL thường được sử dụng kết hợp với XML schema và SOAP để cung cấp dịch vụ Web qua Internet. Một client khi kết nối tới dịch vụ Web có thể đọc WSDL để xác định những chức năng sẵn có trên server. Sau đó, client có thể sử dụng SOAP để lấy ra chức năng chính xác có trong WSDL.

c) Universal Description, Discovery, and Integration (UDDI)

Để có thể sử dụng các dịch vụ, trước tiên client phải tìm dịch vụ, ghi nhận thông tin về cách sử dụng và biết được đối tượng nào cung cấp dịch vụ. UDDI định nghĩa một số thành phần cho biết các thông tin này, cho phép các client truy tìm và nhận những thông tin được yêu cầu khi sử dụng dịch vụ Web.

– Cấu trúc UDDI :
+ Trang trắng – White pages: chứa thông tin liên hệ và các định dạng chính yếu của dịch vụ Web, chẳng hạn tên giao dịch, địa chỉ, thông tin nhận dạng… Những thông tin này cho phép các đối tượng khác xác định được dịch vụ.
+ Trang vàng – Yellow pages: chứa thông tin mô tả dịch vụ Web theo những loại khác nhau. Những thông tin này cho phép các đối tượng thấy được dịch vụ Web theo từng loại với nó.
+ Trang xanh – Green pages: chứa thông tin kỹ thuật mô tả các hành vi và các chức năng của dịch vụ Web.
+ Loại dịch vụ – tModel:  chứa các thông tin về loại dịch vụ được sử dụng.

Những thông tin về dịch vụ Web được sử dụng và công bố lên mạng sử dụng giao thức này. Nó sẽ kích hoạt các ứng dụng để tìm kiếm thông tin của dịch vụ Web khác nhằm xác định xem dịch vụ nào sẽ cần đến nó.

d) SOAP – Simple Object Access Protocol
SOAP là một giao thức giao tiếp có cấu trúc như XML. Nó được xem là cấu trúc xương sống của các ứng dụng phân tán được xây dựng từ nhiều ngôn ngữ và các hệ điều hành khác nhau. SOAP là giao thức thay đổi các thông điệp dựa trên XML qua mạng máy tính, thông thường sử dụng giao thức HTTP.

Một client sẽ gửi thông điệp yêu cầu tới server và ngay lập tức server sẽ gửi những thông điệp trả lời tới client. Cả SMTP và HTTP đều là những giao thức ở lớp ứng dụng của SOAP nhưng HTTP được sử dụng và chấp nhận rộng rãi hơn bởi ngày nay nó có thể làm việc rất tốt với cơ sở hạ tầng Internet.

<a name="coche"></a>
##3. Cơ chế dịch vụ WEB
<ul>
<li>Dịch vụ vận chuyển (Service Transport): có nhiệm vụ truyền thông điệp giữa các ứng dụng mạng, bao gồm những giao thức như HTTP, SMTP, FTP, JSM và gần đây nhất là giao thức thay đổi khổi mở rộng (Blocks Extensible Exchange Protocol- BEEP).</li>
<li>Thông điệp XML: có nhiệm vụ giải mã các thông điệp theo định dạng XML để có thể hiểu được ở mức ứng dụng tương tác với người dùng. Hiện tại, những giao thức thực hiện nhiệm vụ này là XML-RPC, SOAP và REST.</li>
<li>Mô tả dịch vụ: được sử dụng để miêu tả các giao diện chung cho một Web service cụ thể. WSDL thường được sử dụng cho mục đích này, nó là một ngôn ngữ mô tả giao tiếp và thực thi dựa trên XML. Web service sẽ sử dụng ngôn ngữ này để truyền tham số và các loại dữ liệu cho các thao tác và chức năng mà Web service cung cấp.</li>
<li>Khám phá dịch vụ: tập trung dịch vụ vào trong một nơi được đăng ký, từ đó giúp một Web service có thể dễ dàng khám phá ra những dịch vụ nào đã có trên mạng, tốt hơn trong việc tìm kiếm những dịch vụ khác để tương tác. Một Web service cũng phải tiến hành đăng ký để các dịch vụ khác có thể truy cập và giao tiếp. Hiện tại, UDDI API thường được sử dụng để thực hiện công việc này.</li>

<a name="trienkhai"></a>
##4. Triển khai dịch vụ WEB


<a name="ungdung"></a>
###4.1 Ứng dụng thực tế
Google Gears, Facebook API, Zoho Notebook...

<a name="caidat"></a>
###4.2 Cách cài đặt


<a name="tks"></a>
##5. Lời cảm ơn
Bài viết cung cấp thông tin về giao thức HTTP và Dịch vụ web. Cảm ơn đã theo dõi.
