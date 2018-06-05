---
layout: entry
title: Thử dùng Pepper SDK với Android Studio
description: Sử dụng Pepper SDK với Android Studio: Đây là SDK mới được Softbank cung cấp giúp phát triển nhanh, hơn đơn giản hơn rất nhiều, đặc biệt với các lập trình viên Android. Và đây sẽ là cách sẽ được giới thiệu trong bài viết này.
---


### [Pepper là gì?](http://www.softbank.jp/robot/products/)

Pepper là một robot màu trắng, cao 121 cm và nặng 28 kg với đầy đủ hai tay (nhưng không có chân) có khả năng thể hiện cảm xúc giống như người và được thiết kế để trở thành một thành viên thực thụ trong gia đình.

Hiện tại, chú robot này đang được công ty SoftBank Corp (công ty sản xuất ra Pepper) bán ra tại Nhật Bản. Các nhà mạng Nhật đã tiết lộ có khoảng 1000 robot Pepper được bán ra trong vòng 1 phút khi nó chính thức được bán ra. Phòng [GMO 時勢大研究システム](http://recruit.gmo.jp/engineer/jisedai/blog/pepper_was_coming/) hiện nay cũng có một con để nghiên cứu từ năm 2015. Pepper của GMO không thể làm việc nhà nhưng bù lại nó có thể trò chuyện, nhận ra cảm xúc của người đối diện và có khả năng học hỏi để phát triển "cảm xúc" của mình. Ngoài ra, Pepper cũng biết thu thập các thông tin từ internet như tin nhắn hay dữ liệu dự báo thời tiết.

### Phát triển tính năng mở rộng cho Pepper

Sẽ có 2 cách chủ yếu để develop cho Pepper

* Sử dụng [Choregraphe](http://doc.aldebaran.com/2-1/software/choregraphe/tutos/index.html): Đây là cách truyền thống, có thể viết bằng Python, C++, hay Java. Tuy nhiên sẽ khá phức tạp trong lập trình. Mặc dù mình không tập trung vào cách này nhưng nếu ai quan tâm có thể tham khảo một số link ở dưới:
 * http://doc.aldebaran.com/2-1/software/choregraphe/tutos/index.html
 * http://recruit.gmo.jp/engineer/jisedai/blog/pepper_was_coming/
 * http://qiita.com/tdaiku/items/3ffe124cfff5f892f9f7

* Sử dụng Pepper SDK với Android Studio: Đây là SDK mới được Softbank cung cấp giúp phát triển nhanh, hơn đơn giản hơn rất nhiều, đặc biệt với các lập trình viên Android. Và đây sẽ là cách sẽ được giới thiệu trong bài viết này.

### Sử dụng Pepper SDK

#### Cài đặt môi trường

Hãy chắc chắn rằng JDK, Android Studio (1.5 hoặc cao hơn), Android SDK đã được cài đặt.

##### Cài đặt Android SDK và Build-Tools

Để có thể phát triển theo hướng Android Application, cần phải cài đặt Android SDK và Build-Tools chuẩn như sau:

* Bước 1: Từ thanh **Menu Bar** click vào SDK Manager ![sdk manager](https://drive.google.com/uc?id=0B05rqFCwNCjkTE5wNFpfZmEyUVk&export=download)

![](https://drive.google.com/uc?id=0B05rqFCwNCjkOGFFWURaQUE2QUU&export=download)

* Bước 2: Download và cài đặt Android SDK version 5.1.1 (API 22, Lollipop)

![](https://drive.google.com/uc?id=0B05rqFCwNCjkTE9RTzRZdUVsbm8&export=download)

* Bước 3: Download và cài đặt SDK Buil-Tools

SDK Build-Tools như là Emulator/Android Debug Bridge cần được cài đặt tương ứng với Android SDK version.

![](https://drive.google.com/uc?id=0B05rqFCwNCjkM2RkUXdZZEpIYmM&export=download)

##### Cài đặt Pepper SDK Plugin

Từ Setting: Preferences... > Plugins > Browse repositries... sẽ hiện lên dialog tìm kiếm plugin. Hãy nhập `pepper` để tìm kiếm Pugin

![](https://drive.google.com/uc?id=0B05rqFCwNCjkX1lrTVI1aEI2Tzg&export=download)

![](https://drive.google.com/uc?id=0B05rqFCwNCjkaUFQR1loMm9SeGc&export=download)

Sau khi khởi động lại Android Studio. Vào File > New , sẽ thấy biểu tượng robot.

![](https://drive.google.com/uc?id=0B05rqFCwNCjkSGIzelBMNEFMUmc&export=download)

##### Cài đặt Robot SDK

Đây là bước cuối cùng để cài thêm công cụ cũng như Emulator cho Robot

Từ thanh Menu bar click vào biểu tượng **Robot SDK Manager** ![](https://drive.google.com/uc?id=0B05rqFCwNCjkSVZjd2Rtb1FaVDA&export=download) Sau đó check vào API version muốn cài đặt(hiện tại chỉ có 1 version 0.9)

![](https://drive.google.com/uc?id=0B05rqFCwNCjkODZGX0RiRXF2TWs&export=download)

#### Kết quả

Tổng hợp lại sau khi cài đặt chung ta sẽ có được các công cụ phát triển gồm:

* **ADV**: Máy ảo Android dành cho tablet được gắn trên Pepper
* Các công cụ khác dành riêng cho robot: **Robot Viewer, Robots Browser, Trajectory**

### Thử tạo một Robot Application

Với cách làm truyền thống sẽ sử dụng Python sau đó kết nối với IP Address của Robot rồi build vào trong robot. Ứng dụng như này sẽ kết nối với tablet và các bộ phận của robot. Nhưng với các sử dụng Android Studio, ứng dụng sẽ được build vào trong Tablet của robot, Tablet này sẽ gọi các API bên trong của robot

#### Tạo Project mới

Từ Android studio, chọn **File** > **New** > **New Project**. Vì tạo ứng dụng cho tablet nên cần phải chọn **Phone and Tablet**, Android version la 5.1 (Lollipop)

![](https://drive.google.com/uc?id=0B05rqFCwNCjkUFpVSEQzNG82WkU&export=download)

Sau khi tạo Project, cần tao thêm một Robot Application, chọn **File** > **New** > **Robot Application**

![](https://drive.google.com/uc?id=0B05rqFCwNCjkTmlIbnFvMEYzcDg&export=download)

Tạo xong **Robot Application** một số icon và tính năng trong menu sẽ được kích hoạt
![](https://drive.google.com/uc?id=0B05rqFCwNCjkdWVlbzU3SzRtWEE&export=download)

Cấu trúc của Project sẽ như sau:
![](https://drive.google.com/uc?id=0B05rqFCwNCjkREg2RnBJRmN1b0k&export=download)

Thêm các thư viện để có thể tương tác, liên kết với Robot.
![](https://drive.google.com/uc?id=0B05rqFCwNCjkVm5IbFpxeUdyM3M&export=download)

Ngoài các file resource dành cho Robot còn có các file resource dành riêng cho robot:
![](https://drive.google.com/uc?id=0B05rqFCwNCjkLWxZMWhUYmZ4UjQ&export=download)
* File .anim định nghĩa animation cho robot, hay định nghĩa các cử động cho robot rất đơn giản.
* File .pmt định nghĩa sự di chuyển của Ropot
* File .top định nghĩa việc tự động trả lời chat bằng giọng nói của Robot(khá giống với chatbot nhưng nhận diện giọng nói và trả nời bằng tiếng nói). Đươc đặt trong các thư mục như là `raw-en` hay `raw-fr` tương ứng với ngôn ngữ cần định nghĩa.
* File config của Project robotsdk.xml
> Chi tiết cách thực hiện với các file này sẽ được giới thiệu trong bài khác

Cuối cùng là thêm dòng dưới vào AndroidManifest
```
<uses-feature android:name=”com.softbank.hardware.pepper” />
```

Thử một đoạn code để chạy "Hello word!" cho Pepper

```
import android.app.Activity;
import android.os.Bundle;

import com.aldebaran.qi.sdk.object.interaction.Say;

public class MainActivity extends Activity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        Say say = new Say(this);
        say.run("Hello world!");

    }

}
```
Ngoài ví dụ "Hello world!" ở trên hãy thử với một vài ví dụ đơn giản như di chuyển robot, bật nhạc hay cử động chân tay [ở đây](https://android.aldebaran.com/doc/tutorials.html)

#### Robot Emulator

Khi Run, Robot Emulator sẽ tự động được bật lên hoặc kích vào biểu tượng ![](https://drive.google.com/uc?id=0B05rqFCwNCjkNVJBamR6MXpqSm8&export=download) trên thanh menu.

![](https://drive.google.com/uc?id=0B05rqFCwNCjkM1BmaUs1NkllNlU&export=download)

Robot Emulator sẽ gồm 3 thành phần chính:

* ADV: Là Máy ảo Android cho tablet trên robot
* Robot viewer: là mô hình giống như robot thật giúp mô phỏng được dễ dàng
* NAOqi: Robot engine giống như robot thật chính nó sẽ làm cho robot ảo cử động di chuyển như robot thật

### Tổng kết
Tương lai co Pepper sẽ còn rất nhiều hướng đi khác nhau. Nó sẽ được nâng cấp trí tuệ nhân tạo thông minh hơn, sử dụng trong IoT hay thậm chí là VR

* https://iotnews.jp/archives/tag/pepper
* https://robotstart.info/2015/12/21/kozaki_shogeki-no1.html

Và để tạo ứng dụng robot đơn giản hơn, trực quan hơn rõ ràng Softbank đã tạo ra SDK cho Android Studio vô cùng tiện lợi.
Tuy nhiên hiện nay giá thành của Pepper còn khá cao chỉ có một số công ty mạnh như GMO Internet mua làm vị trí lễ tân có nhiệm vụ đón, giúp đỡ đưa ra địa điểm họp, thời gian họp cho khách và gọi tới các CBNV có liên quan khi có lịch họp. Đặc biệt, lễ tân robot này có khả năng nhận diện hình ảnh khách từng đến công ty để gửi lời chào khi gặp lại.


**Tài liệu tham khảo**

* https://android.aldebaran.com/doc/index.html
* https://github.com/ohwada/Pepper_Android_Tutorial
* http://doc.aldebaran.com/2-4/family/pepper_technical/index_dev_pepper.html
* https://developer.softbankrobotics.com/jp-ja/documents/faq
* http://doc.aldebaran.com/2-4/index_dev_guide.html
* http://qiita.com/enta0701/items/a6217bb07d56421a3a03
* https://developer.softbankrobotics.com/jp-ja/downloads/pepper
* http://qiita.com/chibi929/items/4f8aa53e5f9ad2668b1e#_reference-b7db910da10675aa8914
* http://qiita.com/Suna/items/235708f9833a92dd598d#_reference-5673892dc16a3e26be02
* http://doc.aldebaran.com/2-1/software/choregraphe/tutos/index.html
* http://qiita.com/tdaiku/items/3ffe124cfff5f892f9f7
* http://qiita.com/Atelier-Akihabara/items/4162192129f366da1240
* https://www.softbank.jp/corp/set/data/group/sbm/news/conference/pdf/material/20160519_01.pdf
* http://recruit.gmo.jp/engineer/jisedai/blog/pepper_was_coming/
* http://recruit.gmo.jp/engineer/jisedai/blog/pepper_tablet/
* http://recruit.gmo.jp/engineer/jisedai/blog/pepper_event_operation/
* http://recruit.gmo.jp/engineer/jisedai/blog/pepper-alredballdetection/