---
layout: entry
title: Xây dựng ứng dụng AR với ARToolkit.
description: AR là một công nghệ cho phép lồng ghép thông tin ảo vào thế giới thực (và ngược lại), nó giúp người sử dụng tương tác với những nội dung số trong thực tại (như chạm vào, phủ vật thể lên trên - nói dễ hiểu là ghép ảnh theo dạng 3D).
---

### Giới thiệu về AR
Nói đến AR hẳn là ai không biết thì cũng từng nghe qua rồi.
> https://en.wikipedia.org/wiki/Augmented_reality

Hiểu nôm na nó AR là một công nghệ cho phép lồng ghép thông tin ảo vào thế giới thực (và ngược lại), nó giúp người sử dụng tương tác với những nội dung số trong thực tại (như chạm vào, phủ vật thể lên trên - nói dễ hiểu là ghép ảnh theo dạng 3D),...

Và với phần cứng mạnh mẽ như hiện nay VR/AR sẽ "ảo tung chảo" nhờ Snapdragon 835 mới nhất từ Qualcomm hay A10X của Apple.

#### VR/AR cái nào đang phát triển hơn?

Tính đến thời điểm hiện tại, công nghệ AR đang phổ biến hơn so với VR, nhất là sau đợt Pokemon Go. AR có thể xài ngay chiếc điện thoại của bạn để chạy, vì hiện tại hầu hết điện thoại đều đã có camera cũng như các cảm biến đủ mạnh để nhận biết về thế giới bên ngoài của bạn. CEO Facebook cũng tin rằng smartphone sẽ là công cụ đưa AR đến với mọi người ở thời điểm ban đầu chứ không phải những thiết bị phức tạp như HoloLens. Hãy nhìn vào cách mà AR được Pokemon Go sử dụng, chẳng phải đó là một đợt bùng nổ hay sao?

Trong khi đó, VR do đòi hỏi phải có phần cứng chuyên dụng nên chưa thể phát triển mạnh như AR. Ít nhất bạn sẽ cần có một chiếc kính thực tế ảo, dù giá rẻ hay mắc thì vẫn phải đi mua. Để trải nghiệm tốt hơn, bạn sẽ cần thêm một dạng tay cầm nào đó, có thể là tay cầm chơi game hay những thiết bị được phát triển riêng. Ở khoảng giá rẻ, chiếc kính Google Cardboard chỉ có giá 10-15$ mà thôi. Còn lên cao hơn, xịn hơn, hình ảnh rõ hơn, nét hơn thì có Oculus Rift giá 600$ hay HTC Vive Pre giá 800$. Ngoài ra, những chiếc kính Rift hay Vive còn đòi hỏi máy tính phải có cấu hình mạnh, thứ mà không phải ai cũng dễ dàng mua được.

#### Các thư viện (tool) hỗ trợ xây dựng ứng dụng AR hiện nay

<table>
    <thead>
        <tr>
            <th>Tool</th>
            <th>Ưu điểm</th>
            <th>Nhược điểm</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><a href="https://developer.vuforia.com/">Vuforia</a></td>
            <td>
                Mạnh nhất luôn, nhiều người chọn nhất, fps cao, có Cloud riêng của của nó
            </td>
            <td>
                Khi build product thì phải mất tiền ($499 / one-time per app) chưa kể tiền Cloud ($99 / mo.)
            </td>
        </tr>
        <tr>
            <td><a href="https://www.easyar.com/">EasyAR</a></td>
            <td>
                Đúng như cái tên của nó, khá là đơn giản mà lại free
            </td>
            <td>
                Mặc dù free nhưng bản Pro của nó lại mất phí. chất lượng chưa được cao
            </td>
        </tr>
        <tr>
            <td><a href="https://www.wikitude.com/">Wikitude</a></td>
            <td>
                Cũng khá mạnh, hỗ trợ cả Smart Glasses
            </td>
            <td>
                Giá thành siêu đắt(€2490 / yr. per app)
            </td>
        </tr>
        <tr>
            <td><a href="https://artoolkit.org/">ARToolKit</a></td>
            <td>
                Hoàn toàn free, open source, nhẹ và nhanh
            </td>
            <td>
                Chỉ hỗ trợ 2D Recognition, tính năng còn ít
            </td>
        </tr>
        <tr>
            <td><a href="http://nyatla.jp/nyartoolkit/wp/">NyARToolkit</a></td>
            <td colspan="2">
                Base trên ARToolKit
            </td>
        </tr>
        <tr>
            <td><a href="https://developer.apple.com/arkit/">ARKit</a></td>
            <td>
                Được phát triển bới Apple, fps cao, chất lượng tốt
            </td>
            <td>
                Chỉ chạy được trên iOS, mới ra nên cộng đồng vẫn đang kiểm định 
            </td>
        </tr>
    </tbody>
</table>

### Tôi chọn ARToolkit
Thư viện thực tại ảo ARToolKit cho phép các lập trình viên phát triển ứng dụng thực tại ảo. Với các phiên bản khác nhau ra đời từ năm 2001, ARToolKit đã được triển khai trong hàng ngàn dự án thương mại và mã nguồn mở và được hưởng ứng bởi một cộng đồng chuyên gia lớn của các nhà phát triển và sáng tạo.

ARToolKit là thư viện C/C++ giúp dễ dàng phát triển các ứng dụng thực tại ảo (AR). AR là các hình ảnh máy tính được xây dựng overlay trên thế giới thực. Một trong những ưu điểm của ARToolkit là Open Source nên có thể tim hiểu qua source code bên trong của nó được viết như thế nào nên sẽ hứa hẹn rất nhiều tiềm năng trong nghiên cứu khoa học cũng như ứng dụng thực tế.

Một trong những vấn đề khó nhất khi phát triển các ứng dụng AR là phải tính toán chính xác góc nhìn (user's viewpoint) theo thời gian thực để hình ảnh ảo được gắn (aligned) chính xác vào các vật thể của thế giới thực. ARToolKit sử dụng kĩ thuật computer vision để tính toán vị trí tương đối của camera và card đánh dấu vị trí. Từ thông tin này, programmer có thể gắn các vật thể ảo lên card. Kĩ thuật tracking nhanh, chính xác của ARToolKit hỗ trợ rất nhiều trong việc phát triển các ứng dụng AR vô cùng thú vị.

#### Tính năng nổi trội của ARToolkit

* Robust Tracking, including Natural Feature Tracking
* Strong Camera Calibration Support
* Simultaneous tracking and Stereo Camera Support
* Multiple Languages Supported
* Optimized for Mobile Devices
* Full Unity3D and OpenSceneGraph Support

#### Một vài ví dụ đã sử dụng ARToolkit
* iNVENtor 2014 AR Showcase
<iframe width="560" height="315" src="https://www.youtube.com/embed/pVyFxdJ5lcI" frameborder="0" allowfullscreen></iframe>
* ARToolKit + iPhone Video
<iframe width="560" height="315" src="https://www.youtube.com/embed/5M-oAmBDcZk" frameborder="0" allowfullscreen></iframe>
* ARToolKit + Solar System
<iframe width="560" height="315" src="https://www.youtube.com/embed/OKcWp7NLVz4" frameborder="0" allowfullscreen></iframe>

### ARToolkit căn bản
#### Cơ chế hoạt động của ARToolkit
![alt](https://drive.google.com/uc?id=0B05rqFCwNCjkckhlZzloMllVdmc&export=download)
1. Camera sẽ quay video lại và gửi đến máy tính hoặc điện thoại
2. Phần mềm trên máy tính tìm kiếm thông qua mỗi khung hình trong video bất kỳ hình dạng vuông (dấu vuông).
3. Nếu một ô vuông được tìm thấy sẽ xác định các nội dung hình ảnh hay mô hình nhúng trong ô vuông đó phù hợp. Phần mềm sử dụng toán học để tính toán vị trí của các hình mẫu bên trong ô vuông màu đen và kiểm tra xem nó có phù hợp với pattern đang cần tìm không.
4. Khi các vị trí và hướng của máy ảnh được xác định, một mô hình đồ họa máy tính được vẽ vào vị trí đó và nó định hướng luôn mô hinh này quay đi đâu.
5. Mô hình này được vẽ ở mặt trước của video và theo dõi sự di chuyển của marker để mô hình đồ họa có thể luôn được gắn theo marker.
6. Kết quả cuối cùng mô hình được hiển thị trở lại trên màn hình, Và như vậy người dùng sẽ thấy mô hình đồ họa được đưa lồng vào video thế giới thực; cảm giác giống như nó đồng nhất với marker qua máy ảnh

#### Thuật toán Computer Vision
Để thực hiện phát hiện marker cần phải có một thuật toán ước lượng nhanh. Đó là Computer Vision
![alt](https://drive.google.com/uc?id=0B05rqFCwNCjkTjMxUHA4WUN4VTg&export=download)
Computer Vision là một lĩnh vực bao gồm các phương pháp thu nhận, xử lý ảnh kỹ thuật số, phân tích và nhận dạng các hình ảnh và, nói chung là dữ liệu đa chiều từ thế giới thực để cho ra các thông tin số hoặc biểu tượng, ví dụ trong các dạng quyết định. Việc phát triển lĩnh vực này có bối cảnh từ việc sao chép các khả năng thị giác con người bởi sự nhận diện và hiểu biết một hình ảnh mang tính điện tử. Sự nhận diện hình ảnh có thể xem là việc giải quyết vấn đề của các biểu tượng thông tin từ dữ liệu hình ảnh qua cách dùng các mô hình được xây dựng với sự giúp đỡ của các ngành lý thuyết học, thống kê, vật lý và hình học. Thị giác máy tính cũng được mô tả là sự tổng thể của một dải rộng các quá trình tự động và tích hợp và các thể hiện cho các nhận thức thị giác.

Thị giác máy tính là một môn học khoa học liên quan đến lý thuyết đằng sau các hệ thống nhân tạo có trích xuất các thông tin từ các hình ảnh. Dữ liệu hình ảnh có thể nhiều dạng, chẳng hạn như chuỗi video, các cảnh từ đa camera, hay dữ liệu đa chiều từ máy quét y học. Thị giác máy tính còn là một môn học kỹ thuật, trong đó tìm kiếm việc áp dụng các mô hình và các lý thuyết cho việc xây dựng các hệ thống thị giác máy tính.

Các lĩnh vực con của thị giác máy tính bao gồm tái cấu trúc cảnh, dò tìm sự kiện, theo dõi video, nhận diện bố cục đối tượng, học, chỉ mục, đánh giá chuyển động và phục hồi ảnh.


#### Một vài bài viết về thuật toán
* http://szeliski.org/Book/drafts/SzeliskiBook_20100903_draft.pdf
* https://en.wikipedia.org/wiki/Computer_vision
* http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.14.7673

#### Hệ trục tọa độ

ARToolkit định nghĩa 2 hệ trục tọa độ khác nhau để sử dụng cho 2 mục đích: *Computer vision algorithm* và *Rendering*
![alt](https://drive.google.com/uc?id=0B05rqFCwNCjkVW94TFlQX3B3Q2c&export=download)

Như trong hình phía trên, tạo độ trên marker sẽ được chuyển về tọa độ của camere (qua một ma trận được tính từ thuật toán Computer Vision). Trên camera sẽ chuyển về 2 chiều trên màn hình (xd, yd). Khi chúng ta render thì đương nhiên chỉ hiện thị được trên hệ trục tọa đô 2 chiều và giờ chỉ việc render nên điểm (xd, yd).
![alt](https://drive.google.com/uc?id=0B05rqFCwNCjkSUdTOTZ3WGdaeFU&export=download)

> Tọa độ mô hình trên hệ trục gắn với camera = Tọa độ mô hình trên hệ trục gắn với marker x Ma trận chuyển tọa độ

### Sử dụng ARToolkit với Unity

#### Chuẩn bị
* Unity bản mới nhất
* Các tool hỗ trợ build như là Android SDK, XCode
* Kiến thức về Unity(Cách tạo Model, C#, đưa model vào scene, Animation, ..)
* Import thư ARToolkit cho Unity
  * https://github.com/artoolkit/arunity5

![alt](https://drive.google.com/uc?id=0B05rqFCwNCjkNWtJUXBiZGpFMTA&export=download)
![alt](https://drive.google.com/uc?id=0B05rqFCwNCjkeDdVZVBLVWNra00&export=download)

#### Tạo một AR Scene
![alt](https://drive.google.com/uc?id=0B05rqFCwNCjkNkFaYzNBZEpuMzQ&export=download)
![alt](https://drive.google.com/uc?id=0B05rqFCwNCjkbV85OWpHYW1yY28&export=download)
* Tạo 1 GameObject và thêm vào script ARController và ARMarker. Trong Component ARMarker có thể chọn loại marker(Type): Square, Square Barcode, Multimarker, NTF(dành cho marker là hình ảnh cụ thể)
* Đổi tên GameObject thành ARToolkit và chuyển Layer thành AR background. Tạo GameObject Scene root như hình dưới.
![alt](https://drive.google.com/uc?id=0B05rqFCwNCjkM1p0NU1YWlcyTVk&export=download)
* Thêm script ARCamera vào Camera và chuyển Layer thành AR foreground.
![alt](https://drive.google.com/uc?id=0B05rqFCwNCjkWEd4YzJDSXYxMHc&export=download)
* Khối cầu là một model để hiển thị bên trên marker, chúng ta có thể thây thế bằng các mô hình khác(người chơi, nhân vật game). Mô hình này cần được chỉnh Layer là AR foreground.
![alt](https://drive.google.com/uc?id=0B05rqFCwNCjkQ2NXTklBNnBneWc&export=download)
![alt](https://drive.google.com/uc?id=0B05rqFCwNCjkdUI1d0cxY3ROV2c&export=download)

#### Chi tiết các lớp được sử dụng
![alt](https://drive.google.com/uc?id=0B05rqFCwNCjkLXVKdzM5eFpKTEk&export=download)
* ARController: Điều chỉnh các thông số cài đặt cho từng thiết bị và các cài đặt điều khiển các hoạt động của việc Tracking marker
![alt](https://drive.google.com/uc?id=0B05rqFCwNCjkd2I3MV9VQnp4Sms&export=download)
* ARMarker là lớp để nhận biết marker và chứa các Object của Model để đưa đến ARCamera. Các thông số cần thiết:
  * Tag: Là một tên định nghĩa marker
  * ID: Một id tự tăng
  * Marker: Chọn marker để sử dụng danh sách các marker tương ứng với các file trong thư mục `Assets/Resources/ardata/markers`
  * Width: Độ rộng marker tính bằng mét

* ARCamera có chức năng kết nối đến camera và hiển thị các model trên camera

### Tài liệu tham khảo

* https://archive.artoolkit.org/documentation
* https://github.com/artoolkit/arunity5
