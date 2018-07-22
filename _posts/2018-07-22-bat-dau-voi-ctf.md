---
layout: post
title:  Bắt Đầu Với Mảng WEB CTF - CAPTURE THE FLAG
subtitle: Web là một trong những mảng dễ tiếp cận khi chơi CTF. Vậy bắt đầu CTF mảng Web như thế nào?
date:   2018-07-22
categories: security
tags: [news,security]
permalink: bat-dau-voi-ctf/

---
Web là một trong những mảng dễ tiếp cận khi chơi CTF. **Vậy bắt đầu CTF mảng Web như thế nào?**  

[![](https://whitehat.vn/image/xenforo_image/14899399482016-03-18_233536.png)](https://whitehat.vn/image/xenforo_image/14899399482016-03-18_233536.png)

Giờ đặt một website trước mặt mình thì không thể cứ thế mà làm. Làm gì? Tìm flag - một chuỗi bí mật do người ra đề giấu ở đâu đó quanh cái web. Muốn tìm được nó trước hết phải xem đề bài gợi ý cái gì, cho cái gì, trong web có gì, làm sao để khai thác mấy cái đó. Từ đây lại có một vấn đề: **Phải hiểu về web trước đã**.

_Nói thêm một chút là ở bài viết này mình sẽ không đi sâu vào chi tiêt, mình chỉ dừng lại ở việc đặt ra các vấn đề quan trọng mà các bạn cần tìm hiểu_

#### Web hoạt động thế nào?

Chúng ta sẽ cần nắm kiến thức về web qua những vấn đề như thế này:

*   Cách hoạt động của web từ phía client cho đến phía server sẽ có những gì?
*   Client gửi request cho server và nhận lại response như thế nào? Qua đâu? (HTTP, HTTP Header, HTTP Methods)
*   Cách client và server lưu trữ thông tin của nhau (qua cơ sở dữ liệu, cookie, session, …).
*   Các ngôn ngữ cấu thành 1 trang web hoặc thường được dùng khi xây dựng web. (HTML, CSS, JS, PHP, SQL ...)
*   Thông tin whois của 1 trang web (ip, owner,...).

#### 1\. Liên quan đến HTTP

Mỗi khi truy cập một website, từ phía client phải gửi **request** lên server qua **giao thức HTTP**, và những request này được thể hiện dưới dạng **HTTP header**. Giống như việc muốn gửi bức thư thì phải có địa chỉ nhận, tên người viết, thông tin về người viết, nội dung dung thư thì có yêu cầu,... Các headers cũng chứa những thông tin tương tự như vậy.

Những headers này có rất nhiều nên các bạn có thể tự google tìm hiểu. _Đặc biệt là chú ý về **cookie, user-agent**, là 2 trường hay được dùng trong các bài ctf._

Gủi một HTTP request đi cũng có thể gửi được bằng nhiều dạng khác nhau. Các dạng này chính là các **HTTP Methods** hay còn gọi là HTTP Verb. Dạng của nó bao gồm GET, POST, PUT, DELETE, OPTIONS,... Thường dùng nhất là **POST và GET**. Các bạn nên tìm hiểu kỹ điểm giống và khác của 2 methods này.

Một số bài khi dùng POST, GET đều không nhận được gì từ phía server, nhưng khi đổi sang HEAD, PUT, hoặc method khác thì lại ra kết quả. Lý do là ở file .htaccess đã block 2 method đó. Tham khảo:

*   [http://www.tutorialspoint.com/restful/restful_introduction.htm](http://www.tutorialspoint.com/restful/restful_introduction.htm)
*   [.htaccess là gì?](http://www.htmlgoodies.com/beyond/webmaster/article.php/3899416/What-is-the-htaccess-File-and-What-Can-I-Do-With-It.htm)
*   [.htaccess Restrict method POST GET](http://stackoverflow.com/questions/11584101/restrict-post-request-the-server)

Nói tiếp đến **response**. Hẳn các bạn đã không ít lần gặp những thông báo kiểu `404 Not Found` hoặc `302 Forbidden` khi truy cập một url nào đó. Đó là vì sau một request được gửi đến server, ta sẽ nhận được response. Trong response, một cái luôn luôn có là **HTTP Status Code. Mỗi đầu số 1xx 2xx 3xx 4xx 5xx có một ý nghĩa khác nhau.**

*   Tham khảo: [Tìm hiểu cơ bản về HTTP và định dạng của các HTTP message](http://aptech.vn/kien-thuc-tin-hoc/tim-hieu-co-ban-ve-http-va-dinh-dang-cua-cac-http-message.html)

[![](http://sting8k.github.io/content/images/2016/03/Screen-Shot-2016-03-07-at-12-10-19-PM.png)](http://sting8k.github.io/content/images/2016/03/Screen-Shot-2016-03-07-at-12-10-19-PM.png)

Cuối cùng là việc **thao tác với các headers**. Trên Firefox mình hay dùng addon [Live Http Headers](https://addons.mozilla.org/en-US/firefox/addon/live-http-headers-fixed-by-dan) hoặc [Tamper data](https://addons.mozilla.org/en-US/firefox/addon/tamper-data/). Nâng cao hơn các bạn hãy tập dùng [curl](https://curl.haxx.se/), rất tiện và có api cho nhiều ngôn ngữ lập trình.

*   Tham khảo: [http://curl.haxx.se/docs/httpscripting.html](http://curl.haxx.se/docs/httpscripting.html)

#### 2\. Liên quan đến các ngôn ngữ lập trình web

Với nhiều bài CTF chúng ta sẽ phải đọc hiểu code, phân tích hoặc đoán code. Nói chung ta cần trang bị kiến thức về lập trình, hiểu từng ngôn ngữ để làm gì. Ví dụ như html, css thì giới hạn cũng để thể hiện giao diện web, ở html5 "xịn" hơn thì làm được game gì đó; js thì làm được nhiều hơn, hiệu ứng, tính toán …, quan trọng mấy thằng này đều là kiểu ngôn ngữ ở phía client, tức là chạy được luôn ở phía máy mình, và mình xem được code gốc của nó.

Đối với PHP, ASP, JSP,... đây là các ngôn ngữ được biên dịch trên server, và code gốc thì không xem được nhưng có rất nhiều bài CTF chủ động cho người chơi đọc code để phân tích hoặc có lỗi giúp ta có thể đọc code từ đó khai thác.

**Túm lại ta cần học HTML, CSS, JS và một ngôn ngữ server nào đó như PHP hoặc JSP (ít nhất ở mức đọc hiểu).**

#### 3\. Liên quan đến Cookie, Session

*   Nắm được định nghĩa cookie, session
*   Nắm được cách thức lưu trữ của cookie, session.

Lưu ý quan trọng là cookie có thể thay đổi được ở phía client. Session thì chỉ đổi được id (tức là làm mới id, hoặc làm rỗng id). Phía server nếu đọc cookie ko phân biệt ip, đặc điểm trình duyệt người dùng,... thì ta có thể dựa vào đó để khai thác. Ví dụ xác thực admin qua cookie (có một trường id=1234; user=guest, giờ nếu sửa thành id=1;user=admin thì sẽ có thể đăng nhập dưới quyền admin).

*   Một ví dụ rất cơ bản về cookie: [https://www.youtube.com/watch?v=NrC3129Q55c](https://www.youtube.com/watch?v=NrC3129Q55c)

Giải thích một chút về clip phía trên như sau.

*   Phía server có một đoạn code kiểu như thế này:

    <?php  
    if(!isset($_COOKIE[‘restricted_login’])){ //check có trường cookie restricted_login chưa?  
        setcookie(‘restricted_login’,’false’); // nếu chưa thì set với giá trị là False
    } else { // Nếu đã có trường restricted_login
        if($_COOKIE[‘restricted_login’] == ‘true’){ //nếu giá trị là true thì qua bàn
        // Qua bàn, + điểm, blah blah ...
        }
    }
    ?>

  

Đoạn code này sẽ kiểm tra xem ở phía client có trường cookie là `restricted_login`chưa, nếu chưa có thì thêm vào và có giá trị là `false`. Nếu đã có thì kiểm tra giá trị của `restricted_login`, giá trị bằng `true` thì được phép qua bàn.

**Trong CTF đối khi có một bài SQL injection qua cookie. Nói chung cookie cũng là dữ liệu từ phía người dùng, tức là mình có thể thay đổi, và truyền các dữ liệu sai trái lên server**

#### 4\. Liên quan đến SQL Injection

*   SQL injection cơ bản
*   SQL injection - Blind: Không thể trực tiếp get ra đoạn dữ liệu mình muốn và phải get từng ký tự, hoặc dựa và các câu lệnh điều kiện đúng sai,...
*   SQL injection - Error based: Có thể nói là mở rộng của blind, tùy vào dữ liệu đúng hoặc sai mà server trả về kết quả khác nhau.
*   SQL injection - Time based: Dùng một câu lệnh SQL chứa lệnh Sleep(), hoặc một hàm nào đó để nghỉ khi gặp điều kiện đúng. Ví dụ IF(điều kiện, điều kiện nếu đúng-> Sleep(10), đk nếu sai -> null)

SQL Injection cơ bản mình học qua course này, có thể ko cần học hết, chỉ cần nắm rõ cách khai thác qua SQL sau đó có thể tự tìm hiểu thêm tùy bài ctf:

*   [http://newdemy.com/courses/sql-injection-online-course-by-hitesh-choudhary](http://newdemy.com/courses/sql-injection-online-course-by-hitesh-choudhary)

#### 5\. Local & Remote File Inclusion

*   Chi tiết: [http://hakipedia.com/index.php/Local_File_Inclusion](http://hakipedia.com/index.php/Local_File_Inclusion)
*   Một clip ví dụ: [https://www.youtube.com/watch?v=s3XQ1n5kdeQ](https://www.youtube.com/watch?v=s3XQ1n5kdeQ)

#### 6\. XSS

*   Mọi thông tin chi tiết xin truy cập vào link sau: [Kĩ thuật tấn công CROSS-SITE SCRIPTING](https://viblo.asia/Thanh/posts/73KbvZeLGmWB)

#### 7\. Luyện tập

Đọc qua tất cả những thông tin phía trên thì đúng là có phần hơi quá tải. Lúc đầu mới chơi CTF mình cũng không có nhiều kiến thức đến vậy. Bài viết này mình muốn là một nơi tổng hợp tương đối các kiến thức cần thiết để các bạn biết sẽ cần trang bị những gì, tìm vấn đề ở đâu,... Sau cùng dưới đây là những nơi mình đã luyện tập CTF mà thấy rất hiệu quả

*   [http://hackthis.co.uk](http://hackthis.co.uk/) \- Một site phù hợp cho người mới bắt đầu.
*   [http://www.root-me.org/en/Challenges/Web-Server/](http://www.root-me.org/en/Challenges/Web-Server/) \- Một list challenges bao quát rất nhiều vấn đề, gồm cả các bài LFI/ RFI, các loại SQLi, các tài liệu hướng dẫn.
*   [http://overthewire.org/wargames/natas/](http://overthewire.org/wargames/natas/) \- Gồm cả các dạng bài về Command injection và PHP Objection Injection
*   [http://webhacking.kr](http://webhacking.kr/) \- Có khoảng 60 challenges về web từ khó đến dễ. Một số bài hơi mang tính thách đố
*   [http://ringzer0team.com](http://ringzer0team.com/)

Một lưu ý cuối là các bạn hãy kết hợp việc luyện tập ở các site phái trên và việc tham gia các giải ctf mới ra ở [http://ctftime.org](http://ctftime.org/) nữa :D. Chúc các bạn vui vẻ!

 [Nguồn: STING8K](http://sting8k.github.io/ctf-lam-the-nao-de-bat-dau-voi-ctf-mang-web/)
