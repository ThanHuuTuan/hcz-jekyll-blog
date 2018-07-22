---
layout: post
title:  "Một Số Câu Hỏi Phỏng Vấn PHP"
date:   2018-07-20 13:50:39
categories: infomation
tags: [tuts, news]
permalink: /cau-hoi-phong-van-php/
bigimg: /static/img/logo-xana.gif
---
[![](https://3.bp.blogspot.com/-oB077863oQ8/WrYrvTwQLAI/AAAAAAAADgY/D7AumFr7LvMOqAvumQt1_QCmm5e5Z7j2ACLcBGAs/s640/php-interview-696x392.jpg)](https://3.bp.blogspot.com/-oB077863oQ8/WrYrvTwQLAI/AAAAAAAADgY/D7AumFr7LvMOqAvumQt1_QCmm5e5Z7j2ACLcBGAs/s1600/php-interview-696x392.jpg)

1\. Phiên bản PHP cao nhất hiện tại là bao nhiêu ?

*   Phiên bản 7.2.2 – Phát hành chính thức: 1 Feb 2018.

2\. PHP là gì ?

*   PHP là ngôn ngữ lập trình kịch bản phía máy chủ (server), mã nguồn mở. Là một công cụ mạnh mẽ để phát triển các ứng dụng web.

3\. Unset vs Unlink khác nhau như nào ?

*   Unset dùng để xoá biến (variable). Unlink dùng để xoá file.

4\. Session vs Cookie khác nhau như nào ?

*   Session được lưu trữ trên máy chủ – Cookie lữu trữ trên máy người dùng.
*   Nội dung Cookie có thể sửa đổi – Session thì rất khó hoặc không.
*   Cookie có thể được lưu lâu dài hơn, có thể set thời gian chết – Session sẽ mất khi người dùng đóng trình duyệt.
*   Session là tạm thời – Cookie thì có thời gian lâu hơn.

5\. Cách khai báo và sử dụng Cookie như thế nào ?

*   setcookie() – function được sử dụng để thiết lập cookie trong PHP.
*   Cú pháp khai bác Cookie : setcookie(name, value, expire, path, domain).

1.  name : tên của cookie.
2.  value : gía trị của cookie đó.
3.  expire : thời gian sống của cookie đó.
4.  path : đường dẫn để lưu thông tin cookie.
5.  domain : tên miền mà ta muốn lưu cookie.

6\. Var_dump() là gì ?

*   Được sử dụng để hiển thị thông tin, cấu trúc, giá trị của một hoặc nhiều biến.
*   Cú pháp : 
    
{% highlight php %}
var_dump(var1,  var  2,  ...  ,  var n);
}
{% endhighlight %}
    

7\. Điểm khác nhau giữa include() vs require()

Tuy đều dùng để chèn một file php vào nhưng :

*   include() : khi chèn một file nhưng không tìm thấy file đó, mã PHP vẫn chạy và không dừng. Các đoạn mã dưới vẫn chạy.
*   require() : khi chèn một file nhưng không tìm thấy file đó, mã PHP sẽ thông báo lỗi và dừng ngay ở chỗ fail đó, các đoạn code phía dưới sẽ không được chạy.

8\. So sánh echo() vs print_r()

Đều có chức năng hiển thị thông tin ra màn hình, nhưng :

*   echo() : nhanh hơn so vs print\_r, nhưng chỉ hiển thị được một số dữ liệu cơ bản, không đầy đủ thông tin như print\_r.
*   print_r() : hiển thị đầy đủ thông tin của dữ liệu, như Array, Object.

9\. Có bao nhiêu kiểu lỗi trong PHP

*   Lỗi thông báo (Notice error) : báo lỗi khi sử dụng biến mà chưa được khai báo.
*   Lỗi cảnh báo (Warning error) : khi một gói không được định nghĩa và một số chức năng đã được sử dụng, lỗi này không nghiêm trọng, chương trình vẫn tiếp tục.
*   Lỗi nghiêm trọng(Fatal error) : khi đối tượng gọi một class và class không tồn tại hoăc không khả dụng. Lỗi này sẽ khiến chương trình dừng ngay lập tức tại đó.

10\. File .htaccess là gì ?

Là một tệp cấu hình chạy trên máy chủ Apache. Dùng để thay đổi tính năng của máy chủ.

*   Dùng để viết lại url.
*   Sử dụng để làm mật khẩu bảo vệ trang web.
*   Giới hạn địa chỉ IP truy cập web.

11\. Define (hằng số) là gì ?

*   Dùng để khai báo biến với giá trị không thay đổi trong toàn bộ dự án.
*   Cú pháp : 
    
    1.  define(tên biến, giá trị);
    

12\. Làm thế nào để thay đổi múi giờ (time zone)

*   Sử dụng hàm : 
    
    1.  date\_default\_timezone_set('Asia/Ho\_Chi\_Minh');
    

13\. Sự khác nhau giữa Public, Protected, Private ?

*   Public : khai báo công khai, có thể dùng ở mọi nơi trong, bên trong class, bên ngoài class, class kế thừa.
*   Protected : cho phép truy cập từ class của nó và các class kế thừa.
*   Private : chỉ cho phép truy cập trong class của nó.

14\. Làm sao để đếm số phần tử trong mảng ?

*   Sử dụng hàm :
    
    1.  count();
    

15\. Làm thế nào dể huỷ session ?

*   Sử dụng hàm :
    
    1.  session_destroy();
    

16\. Làm thế nào để làm mới trang bằng HTML ?

Có thể sử dụng thẻ <meta> để làm mới trang hoặc chuyển hướng tới trang khác sau một thời gian nhất định.

<head>  <meta  http-equiv="refresh"  content="15">  </head> // Trang sẽ làm mới sau mỗi 15s

<head>  <meta  http-equiv="refresh"  content="15"  URL="target.html">  </head> // Trang sẽ làm mới sau 15s và url mới sẽ là target.html

17\. Chức năng của in_array() là gì ?

*   Dùng để tìm kiếm phần tử có trong mảng hay không. Nếu phần tử cần tìm là chuỗi và tham số truyền vào là TRUE, thì kết quả tìm kiếm sẽ phần biệt chữ hoa, chữ thường.
*   Cú pháp : 
    
    1.  in_array(search, array, type);
    

18\. Kết quả hiển thị dưới đây là gì ?

$arrayData1 =  \['126'=>'a','226'=>'b','336'=>'c'\]; $arrayData2 =  \['446'=>'a','556'=>'b','666'=>'c'\]; $resultant = array_merge($arrayData1, $arrayData2); print_r($resultant);  // Result  Array  (  \[0\]  => a \[1\]  => b \[2\]  => c \[3\]  => a \[4\]  => b \[5\]  => c )
