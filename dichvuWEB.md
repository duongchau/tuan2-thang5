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
Dịch vụ Web gồm có 3 thành phần chính:XML – eXtensible Markup Language, WSDL – Web Service Description Language, Universal Description, Discovery, and Integration (UDDI), SOAP – Simple Object Access Protocol.

<a name="khainiemtp"></a>
###2.2 Khái niệm từng thành phần
a) XML – eXtensible Markup Language
Là một chuẩn mở do W3C đưa ra cho cách thức mô tả dữ liệu, nó được sử dụng để định nghĩa các thành phần dữ liệu trên trang web và cho những tài liệu B2B. Về hình thức, XML hoàn toàn có cấu trúc thẻ giống như ngôn ngữ HTML nhưng HTML định nghĩa thành phần được hiển thị như thế nào thì XML lại định nghĩa những thành phần đó chứa cái gì. Với XML, các thẻ có thể được lập trình viên tự tạo ra trên mỗi trang web và được chọn là định dạng thông điệp chuẩn bởi tính phổ biến và hiệu quả mã nguồn mở.

Do dịch vụ Web là sự kết hợp của nhiều thành phần khác nhau nên nó sử dụng các tính năng và đặc trưng của các thành phần đó để giao tiếp. XML là công cụ chính để giải quyết vấn đề này và là kiến trúc nền tảng cho việc xây dựng một dịch vụ Web, tất cả dữ liệu sẽ được chuyển sang định dạng thẻ XML. Khi đó, các thông tin mã hóa sẽ hoàn toàn phù hợp với các thông tin theo chuẩn của SOAP hoặc XML-RPC và có thể tương tác với nhau trong một thể thống nhất.

<a name="coche"></a>
##3. Cơ chế dịch vụ WEB


<a name="hd"></a>
###3.1 Dịch vụ WEB hoạt động như thế nào?


<a name="cochett"></a>
###3.2 Cơ chế tương tác giữa các thành phần


<a name="trienkhai"></a>
##4. Triển khai dịch vụ WEB


<a name="ungdung"></a>
###4.1 Ứng dụng thực tế


<a name="caidat"></a>
###4.2 Cách cài đặt

<a name="tks"></a>
##5. Lời cảm ơn

