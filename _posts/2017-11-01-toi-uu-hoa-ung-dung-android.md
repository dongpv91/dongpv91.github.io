---
layout: entry
title: Tối ưu hóa ứng dụng Android.
description: Với khả năng chứa năng lượng thấp mà công việc phải tiêu thụ lại vô cùng lớn do tất cả các ứng dụng đều phải lấy một phần năng lượng để hoạt động. Vì hầu hết các loại điện thoại đều được để ở nhà vào ban đêm và được sử dụng trong ngày, không có cơ hội để sạc pin nhưng các chủ sở hửu lại mong đợi kéo dài ít nhất 12 tiếng.
---



## Giới thiệu

Android là một hệ điều hành dựa trên nền tảng Linux được thiết kế dành cho các thiết bị di động có màn hình cảm ứng như điện thoại thông minh và máy tính bảng. Ban đầu, Android được phát triển bởi Tổng công ty Android, với sự hỗ trợ tài chính từ Google và sau này được chính Google mua lại vào năm 2005.

Android có mã nguồn mở và Google phát hành mã nguồn theo Giấy phép Apache. Chính mã nguồn mở cùng với một giấy phép không có nhiều ràng buộc đã cho phép các nhà phát triển thiết bị, mạng di động và các lập trình viên nhiệt huyết được điều chỉnh và phân phối Android một cách tự do. Ngoài ra, Android còn có một cộng đồng lập trình viên đông đảo chuyên viết các ứng dụng để mở rộng chức năng của thiết bị, bằng một loại ngôn ngữ lập trình Java có sửa đổi. Vào tháng 10 năm 2012, có khoảng 700.000 ứng dụng trên Android, và số lượt tải ứng dụng từ Google Play, cửa hàng ứng dụng chính của Android, ước tính khoảng 25 tỷ lượt.

Android chiếm 75% thị phần điện thoại thông minh trên toàn thế giới vào thời điểm quý 3 năm 2012, với tổng cộng 500 triệu thiết bị đã được kích hoạt và 1,3 triệu lượt kích hoạt mỗi ngày.

Android được xây dựng để cho phép các nhà phát triển để tạo ra các ứng dụng di động hấp dẫn tận dụng tất cả một chiếc điện thoại đã cung cấp. Nó được xây dựng để được thực sự mở.

Ví dụ, một ứng dụng có thể kêu gọi bất kỳ chức năng lõi của điện thoại như thực hiện cuộc gọi, gửi tin nhắn văn bản, hoặc bằng cách sử dụng máy ảnh, cho phép các nhà phát triển để tạo ra phong phú hơn và nhiều hơn nữa những kinh nghiệm cố kết cho người dùng.

Android được xây dựng trên mở Linux Kernel. Hơn nữa, nó sử dụng một máy ảo tuỳ chỉnh được thiết kế để tối ưu hóa bộ nhớ và tài nguyên phần cứng trong một môi trường di động. Android là mã nguồn mở, nó có thể được liberally mở rộng.

Nền tảng này sẽ tiếp tục tiến triển như cộng đồng nhà phát triển công việc cùng nhau để xây dựng các ứng dụng di động sáng tạo.

Với Android, không có sự khác nhau giữa các ứng dụng điện thoại cơ bản với ứng dụng của bên thứ ba. Chúng được xây dựng để truy cập như nhau tới một loạt các ứng dụng và dịch vụ của điện thoại.

Với các thiết bị được xây dựng trên nền tảng Android, người dùng có thể đáp ứng đầy đủ các nhu cầu mà họ thích. Chúng ta có thể đổi màn hình nền, kiểu gọi điện thoại, hay bất kể ứng dụng nào. Chúng ta thậm chí có thể hướng dẫn điện thoại chỉ xem những ảnh mình thích.

Với khả năng chứa năng lượng thấp mà công việc phải tiêu thụ lại vô cùng lớn do tất cả các ứng dụng đều phải lấy một phần năng lượng để hoạt động. Vì hầu hết các loại điện thoại đều được để ở nhà vào ban đêm và được sử dụng trong ngày, không có cơ hội để sạc pin nhưng các chủ sở hửu lại mong đợi kéo dài ít nhất 12 tiếng.

<table width="631"><tbody><tr><td width="210">**Thiết bị**</td><td width="210">**Hẳng sản xuất**</td><td width="210">**Dung lượng pin**</td></tr><tr><td width="210">Blade</td><td width="210">ZTE</td><td width="210">1,250 mAh</td></tr><tr><td width="210">LePhone</td><td width="210">Lenovo</td><td width="210">1,500 mAh</td></tr><tr><td width="210">Nexus S</td><td width="210">Samsung</td><td width="210">1,500 mAh</td></tr><tr><td width="210">Xoom</td><td width="210">Motorola</td><td width="210">6,500 mAh</td></tr><tr><td width="210">Galaxy Tab (7’’)</td><td width="210">Samsung</td><td width="210">4,000 mAh</td></tr><tr><td width="210">Galaxy Tab 10.1</td><td width="210">Samsung</td><td width="210">4,000 mAh</td></tr></tbody></table>
## [![untitled](https://i0.wp.com/vietnamlab.vn/wp-content/uploads/2016/09/Untitled-2-300x184.png?fit=300%2C184)](https://i0.wp.com/vietnamlab.vn/wp-content/uploads/2016/09/Untitled-2.png)

Như vậy:

- Với một ứng dụng bình thường trương bình có công suất khoảng 300-400mA dùng trong các thiết bị có dung lượng pin khoảng 1500-2000mAh thì chỉ đc 5 đến 7 tiếng.
- Các yếu tố tiêu thụ năng lượng chủ yếu gồm có: CPU, network, hiển thị. Và đây cũng là các thành phần có thể can thiệp được trong mã nguồn


## []() []()1     Tối ưu hóa xử lý

Ứng dụng Android được viết bằng java vì vậy cần phải tối ưu hóa các tính toán và thuật toán các mã java trong mã nguồn.

### []() []()1.1     Sử dụng các phép dịch bit

- Đây là phương pháp đơn giản nhất để giảm thiểu xử lý
- Sử dụng dịch bit cho các phép nhân chia lũy thừa của 2

### []() []()1.2     Sử dụng các biến trung gian

- Trong quá trình tính toán có nhiều đoạn tính lập lại một biểu thức để không mất công tính lại cần phải lưu giá trị của đoạn tính toán đó vào một biến trung gian
- VD:

double x = d * (lim / max) * sx; double y = d * (lim / max) * sy; có thể thay bằng double temp = d * (lim / max); double x = temp * sx; double y = temp * sy;

 

### []() []()1.3     Bỏ các câu lệnh, tính toán thừa

Có những phần do làm theo lý thuyết hoặc theo suy nghĩ của lập trình viên để dễ hiểu và đễ đọc nhưng lại gây thêm công sức cho việc tính toán

VD:

- if(false) i = 1
- i = 10 * (4 + 6);
- thay bằng i = 100;

### []() []()1.4     Vòng lặp

- Vòng lặp là vấn đề được chú ý nhất vì nó thực hiện chủ yếu các tính toán và trong vòng lặp dù chỉ là một tính toán nhỏ nhưng só lương lần lặp lớn làm cho nó rất lãng phí.

 

- Dưới đây là một số các cách sử dụng vòng lặp với hiệu quả tăng dần:

for (int i = 0; i < x.length(); i++)      x[i] *= Math.PI * Math.cos(y); thay vì mỗi lần lặp lại tính Math.PI * Math.cos(y); nên tính ở ngoài vòng lặp double picosy = Math.PI * Math.cos(y); for (int i = 0; i < x.length(); i++)       x[i] *= picosy; Mặc dù không còn tính toán trong vòng lặp nhưng mỗi lần lặp lại phải so sánh i với x.length() double picosy = Math.PI * Math.cos(y); for (int i = x.length(); --i >= 0;) {       x[i] *= picosy; }

 

Java có thể tự bắt lỗi lên chó vào khối try catch bát lỗi

ArrayIndexOutOfBoundsException

Thì không cần so sánh mỗi lần lặp mà khi quá chỉ số mảng sẽ tự kêt thúc thực hiện trong khối try catch

double picosy = Math.PI * Math.cos(y); try {      for (int i = 0; ; i++)                          x[i] *= picosy; } catch (ArrayIndexOutOfBoundsException e) {}

 

Và có thể sử dụng foreach để thực hiện đối với mẳng ArayList cũng là hiệu quả nhất để duyệt mảng

- Trong quá trình thực hiện thuật toán việc bố trí chia việc cũng làm nẵng phí công sức tính toán. Ban đầu hàm thực hiện công việc gì đó cần tới 2 biến đầu vào t và i như vậy sẽ thực hiện công việc giống nhau với biến t ở trong hàm func():

      for(i=0 ; i<100 ; i++)     {         func(t,i);     }    public void func(int w,d)     {         //lots of stuff.     }

 

Nhưng nếu tối ưu để thuật toán tốt cần chuyển vòng lặp vào trong hàm để giảm thiểu các tính toán giống nhau

 

func(t);    public void func(w)     {         for(i=0 ; i<100 ; i++)         {             //lots of stuff.         }     }

 

### []() []()1.5     Chánh khởi tạo biến

Thường các phương thức khởi tạo phải thực hiện nhiều công việc do vậy hạn chế khởi tạo nhiều thây vào đó nên sử dụng biến trung gian

for (int i = 0; i < limit; i++) {      StringBuffer sb = new StringBuffer();       // do something with sb... }

 

Rõ ràng nếu cứ khởi tạo biến như vậy mất công xử lý làm máy ảo phải thu dọn bộ nhớ nhiều hơn. Và trong ví dụ này cũng chúng ta lên sử dụng String Buffer thay cho String vì sẽ làm giẳm tính toán thao tác với chuối rất đắng kể

 

StringBuffer sb = new StringBuffer(); for (int i = 0; i < limit; i++) {     sb.setLength(0);     // do something with sb... }

 

### []() []()1.6     Sử dụng lại đối tượng

Tái chế sử dụng lại các đối tượng cần tốn công sức khởi tạo như: XmlPullParserFactory, BitmapFactory, StringBuilder, Matcher,…

Ví dụ :

     Matcher.reset(newString)      StringBuilder.setLength(0)

 

### []() []()1.7     Một số các tối ưu khác

- Sử dụng final đối với hằng số và bất cứ biến nào không có khả năng thay đổi
- Không nên sử dụng Thread khi không cần thiết
- Hạn chế tính toán thập phân (float, double) mà thay vào đó là tính toán số nguyên
- Mảng nhiều chiều luôn phải xử lý nhiều hơn so với mẳng một chiều
- Hai mẳng rời rạc tốt hơn so với một đối tượng có hai mẳng song song
- Sử dụng static để thực hiện lời gọi hay kết hợp với final sẽ hiệu quả hơn 15-20% so với phương thức thông thường và không phải khởi tạo đối tượng. Tuy nhiên việc sử dụng static sẽ tốn kếm hơn rất nhiều
- Trong ngôn ngữ hướng đối tượng các thuộc tính được thể hiên và thây đổi các các phương thức get và set. Tuy nhiên đây là một ý tưởng tồi trong Android, các lời gọi các phương thước này là tốn kém hơn nhiều so với truy cập trực tiếp vào biến của lớp, có thể hiệu quả hơn 3- 7 lần khi biên dịch


## []() []()2     Tối ưu hóa sử dụng mạng

Sử dụng mạng không dây để truyền tải dữ liệu là một trong những hành động tốn pin nhiều nhất. Đối với một số ưng dụng việc sử dụng mạng liên tục sẽ làm tiêu hao năng lượng rất nhanh chóng và khi pin yếu sẽ càng làm tốc đọ mạng trở lên chậm chạp

[![untitled](https://i2.wp.com/vietnamlab.vn/wp-content/uploads/2016/09/Untitled-1-300x108.png?fit=300%2C108)](https://i1.wp.com/vietnamlab.vn/wp-content/uploads/2016/09/Untitled-1.png)

Trạng thái thiết bị cho loại mạng 3g gồm 3 trạng thái:

1. **Full Power**: Được sử dụng khi kết nối đang hoạt động, cho phép các thiết bị để truyền dữ liệu với tốc độ cao nhất có thể của nó.
2. **Low Power**: Một trạng thái trung gian sử dụng khoảng 50% năng lượng pin ở trạng thái đầy đủ.
3. **Standby**: Trạng thái năng lượng tối thiểu trong thời gian đó không có kết nối mạng đang hoạt động hay yêu cầu.

### []() []()2.1     Tải trước dữ liệu gây lãng phí

Tìm nạp trước dữ liệu là một cách hiệu quả để giảm số lượng các phiên truyền dữ liệu độc lập. Việc tìm kiếm và cho phép bạn tải về tất cả các dữ liệu bạn có thể cần trong một khoảng thời gian nhất định trong một số lần sử dụng mạng.

Vì tải trước sẽ giảm số lượng kích hoạt cần thiết để tải về dữ liệu. Kết quả là bạn không chỉ tiết kiệm pin, mà còn cải thiện độ trễ, giảm yêu cầu băng thông, và giảm thời gian download.

Tuy nhiên, sử dụng quá mạnh, việc tải trước nguy cơ gia tăng pin và băng thông sử dụng, khi mà tải dữ liệu mà không sử dụng. Nó cũng quan trọng để đảm bảo việc tìm kiếm và không trì hoãn khởi động ứng dụng trong khi các ứng dụng chờ đợi tải dữ liệu để hoàn thành. Trong thực tế có thể xử lý dữ liệu dần dần, hoặc tiến hành tải dữ liệu ưu tiên như vậy mà các dữ liệu cần thiết để khởi động ứng dụng được tải về và xử lý đầu tiên.

Ví dụ như nghe nhạc hay xem video là nhưng dữ liệu lớn nếu cứ tải toàn bộ album nhạc mà trong khi chỉ nghe một bài đầu tiền rồi tắt đi sẽ rất lãng phí năng lương và tuổi thọ pin

### []() []()2.2     Lưu vào bộ nhớ khi tải về

Khi xem ảnh hoặc sử dụng các ứng dụng mạng xã hội sẽ có rất nhiều dữ liệu ta sẽ phải sử dụng lại nhưng khi xem lại đoi khi lại phải tải lại tất cả những dữ liệu đó.

Vậy cần thiết phải lưu lại những gì đã tải được, khi gặp lại chỉ cần lấy từ bộ nhớ ra. Phương pháp này đặc biệt hiệu quả đối với các ứng dụng mạng xã hội, ví dụ như ứng dụng facebook chỉ load thêm các thông báo mới còn các các thông báo cũ vân còn lại trong máy kễ cả khi không kêt nối mạng. Và sẽ rất tiết kiệm nếu đó là các album ảnh.

### []() []()2.3     Hạn chế số lần chuyển giao dữ liệu

Một ứng dụng mà ping các máy chủ mỗi 20 giây, chỉ để thừa nhận rằng các ứng dụng đang chạy và hiển thị cho người sử dụng. Nhữ vẫn phải tiếp tục cung cấp tri phí để thực hiện, kết quả là chi phí pin đáng kể cho hầu như không có chuyển dữ liệu thực tế.

Quan trọng là gói truyền dữ liệu của bạn và tạo ra một hàng đợi chờ chuyển giao. Sẽ không phải ping nhiều lần mà thay vao đó sẽ gom đến một số lượng dữ liệu hay yêu cầu đủ lớn se chuyên giao một thể tức là chuyển dữ liệu càng nhiều càng tốt trong mỗi lần chuyển giao.

### []() []()2.4     Giảm kết nối

Sẽ hiệu quả hơn nếu tái sử dụng các kêt nối mạng hiện có hơn là khởi tạo lại các đối tượng kết nối mới. Tái sử dụng cũng cho phép kết nối mạng để thông minh hơn phản ứng với tình trạng tắc nghẽn và các vấn đề liên quan đến dữ liệu mạng.

Thay vì tạo ra nhiều kết nối đồng thời để tải dữ liệu, hoặc chuỗi nhiều yêu cầu GET liên tiếp, nếu có thể bạn nên bó những yêu cầu trên vào một GET. Như vậy một lần gửi yêu cầu sẽ có nhiều thôn tin hơn.

### []() []()2.5     Lựa chọn loại mạng băng thông lớn để sử dụng

Khi cần tải cung một dữ liệu thì băng thông càng lớn thì càng tốn ít năng lượng, ví dụ với một dữ liệu lơn là một bài hát 6M:

EDGE (90kbps): 300mA * 9.1 min = 45 mAh

3G (300kbps): 210mA * 2.7 min = 9.5 mAh

WiFi (1Mbps): 330mA * 48 sec = 4.4 mAh

- Khi sử dụng WiFi thì l năng lương tiêu hao chỉ bằng 1/10 so vói EDGE

Như vậy cần xác định loại mạng để có thể sử dụng hoặc lựa chọn loại mạng có băng thông cao để tải các dữ liệu lơn.

 

Để kiểm tra kết nối :

 

// Only update if WiFi or 3G is connected and not roaming ConnectivityManager mConnectivity; TelephonyManager mTelephony; // Skip if no connection, or background data disabled NetworkInfo info = mConnectivity.getActiveNetworkInfo(); int netType = info.getType(); int netSubtype = info.getSubtype(); if (netType == ConnectivityManager.TYPE_WIFI) {      return info.isConnected(); } else if (netType == ConnectivityManager.TYPE_MOBILE      && netSubtype == TelephonyManager.NETWORK_TYPE_UMTS      && !mTelephony.isNetworkRoaming()) {      return info.isConnected(); } else {      return false; }

 

### []() []()2.6     Lựa chọn dữ liệu xử lý nếu có thể

Khi thực hiên gọi API nếu trên Server có thể chả về thông tin dưới nhiều dạng khác nhau thì nên chọn loại dữ liễu dễ xử lý

[![untitled](https://i2.wp.com/vietnamlab.vn/wp-content/uploads/2016/09/Untitled-300x231.png?fit=300%2C231)](https://i0.wp.com/vietnamlab.vn/wp-content/uploads/2016/09/Untitled.png)

Như vậy nên gửi lời gọi để chọn JSON làm dữ liệu trả về.

- Trong thư mục <project_name>/res/layout chứa các file giáo điện, ở đó có các thuộc tính đươc set Backgroud cụ thể và có thế lấy mầu sắc của đối tượng đó

 

*Tham khảo: tự viết và chú ý không muốn cho ai copy*


