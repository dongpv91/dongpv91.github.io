---
layout: entry
title: Giới thiệu Recommend Music Model
description: Giới thiệu 3 model dùng để gợi ý bài hát của Spotify: CF Models, NLP Models, Audio Models.
---

Trong những ngày mưa gió, ngắm những đám mây vội vã bay, cây trút lá, người người vội vã về nhà, đó là cơ hội không thể tốt hơn để ngồi nghe những bản nhạc hay về cuộc sống.

![alt](https://drive.google.com/uc?id=0B05rqFCwNCjkWkhVcXhFLUFtX1E&export=download)


Và khi man mác buồn tôi tim đến thằng bạn tỉ tê về một ứng dụng nghe nhạc *Spotify* . Tôi không thể ngờ rằng có thể ngồi nghe nhạc cả ngày với cái ứng dụng này. Tôi không thể ngờ rằng trong đại dương nhạc hơn 30 triệu bài hát lại có thể chọn lọc ra được những bài hát hiểu lòng tôi đến vậy. Discover Weekly, có thể gọi là một “phép màu” của Spotify trong thế giới nghe nhạc trực tuyến. Và từ đây về sau mỗi sáng thứ 2 khi tôi mở Spotify, Discover Weekly mang đến cho tôi một playlist những bài nhạc giúp tôi chiêm nghiệm cuộc sống này. Playlist này phần lớn là nhạc tôi chưa nghe bao giờ làm tôi không bao giờ biết chán.

Trong một ngày mất mạng tôi không thể nghe nhạc online được nữa, tôi buồn bực chán nản quyết định lên mạng xem tại sao Spotify luôn có thể cho tôi nhưng bài nhạc tôi muốn nghe.

Cảm ơn cuộc đời đã đưa đẩy tôi đến với IT, và cuối cùng tôi đã tìm được 3 Model gợi ý của nó.

* **Collaborative Filtering** model: Nó sẽ phân tích hành vi của mình và cả người khác để gợi ý.
* **Natural Language Processing (NLP)** model: đây là mô hình phân tích dữ liệu text để gợi ý.
* **Audio** model: Đây là model dựa vào các bản raw của bài hát để phân tích.


![alt](http://galvanize-wp.s3.amazonaws.com/wp-content/uploads/2016/08/18104334/Screen-Shot-2016-08-17-at-4.48.55-PM.png) 

Phần thực hiện 3 model này lằm ở 3 Batch: Batch CF Models, Batch NLP Models, Batch Audio Models.
Tiếp theo điểm qua từng model sẽ thực hiện ra sao

### Recommendation Model #1: Collaborative Filtering
Khi tìm kiếm **Collaborative Filtering** trên mạng có lẽ thực hiện thành công nhất là Netfix. Họ là công ty đầu tiên sử dụng Collaborative Filtering để gợi ý phim. Họ sử dụng xếp hạng phim dựa trên ngôi sao của người dùng để thông báo cho họ sự hiểu biết về những gì phim để giới thiệu cho người sử dụng khác "tương tự".

Sau khi Netflix sử dụng nó thành công, việc sử dụng nó lan truyền nhanh chóng, và bây giờ nó thường được coi là điểm khởi đầu cho các công ty khác cố gắng tạo ra Recommend model.

Tuy nhiên, không giống như Netflix, Spotify không có những ngôi sao mà người dùng đánh giá âm nhạc của họ. Thay vào đó, dữ liệu Spotify là dữ liệu phản hồi được ẩn đi - cụ thể là số lượng luồng các bài hát được lắng nghe, cũng như dữ liệu phát trực tuyến bổ sung, bao gồm việc người dùng đã lưu bản nhạc vào danh sách nhạc của mình hoặc truy cập trang Nghệ sĩ sau khi nghe.

Nhưng Collaborative Filtering là gì và nó hoạt động như thế nào?

Ví dụ: Minh thích nghe bài *"Mình từng yêu nhau"*, **"Có anh ở đây rồi", "Em luôn ở trong tâm trí anh", "Hãy để anh yêu em thêm lần nữa"** và vợ mình thích nghe bài **"Có anh ở đây rồi", "Em luôn ở trong tâm trí anh", "Hãy để anh yêu em thêm lần nữa"**, *"Định mệnh ta gặp nhau"*. Mình và vợ mình đều thích 3 bài **"Có anh ở đây rồi", "Em luôn ở trong tâm trí anh", "Hãy để anh yêu em thêm lần nữa"**. Đương nhiên trong suy nghĩ của mình sẽ nghĩ vợ mình thích cả bài *"Mình từng yêu nhau"* nữa và mình nói với vợ "Vợ nghe thử bài Mình từng yêu nhau đi". và quả đúng là vợ mình thích và ngược lai mình cũng thích bài "Định mệnh ta gặp nhau". Đơn giản phải không?

Nhưng Spotify thực sự sử dụng như thế nào khái niệm đó trên thực tế để tính toán *hàng triệu* bài hát được đề xuất của người dùng dựa trên hàng triệu sở thích của người dùng khác?

Tập hợp tất cả các (User, bài hát) sẽ đua vào 1 ma trận lớn. Cột tương ứng với user và hàng tương ứng với bài hát

![alt](https://drive.google.com/uc?id=0B05rqFCwNCjkaWJkNXdydzBVSm8&export=download)

Trong thực tế, so với ma trận mà bạn nhìn thấy ở đây là *khổng lồ* hơn rất nhiều. Mỗi hàng đại diện cho một trong 140 triệu người dùng Spotify (nếu bạn sử dụng Spotify, chính bạn là một hàng trong ma trận này) và mỗi cột đại diện cho một trong số 30 triệu bài hát trong cơ sở dữ liệu của Spotify.

Sau đó thư viên python sẽ tính công thức dài bên dưới. Mục đích là vì ma trận trên quá lớn lên nên phải chỉa ra thành 2 vector X(là môt tập vector user) và vector Y(là một tập vector bài hát). Công thức cuối cùng họ sự dùng phức tạp hơn cả công thức ở phía trên và sẽ còn liên quán đến các yếu tố khắc nữa như là nội dung, thời gian nghe,...

Và giờ chúng ta đã có 140 triệu vector người dùng và 30 triệu vector vài hát. Các con số trong vector sẽ dùng để phân tích sau này.

Để tìm ra người dùng nào có khiếu âm nhạc giống với tôi nhất, Collaborative Filtering so sánh vector của tôi với tất cả các vector của người dùng khác, cuối cùng là trả về những người dùng tương tự nhất với tôi. Tương tự với vector Y, các bài hát - bạn có thể so sánh vector của bài hát với tất cả các vectơ bài hát khác và tìm những bài hát nào giống nhất với bài hát bạn đang xem.

Collaborative Filtering thực hiện một công việc khá tốt, nhưng Spotify biết rằng họ có thể làm tốt hơn bằng cách thêm một công cụ khác

### Recommendation Model #2: Natural Language Processing (NLP)

Thư hai loại mô hình khuyến nghị mà Spotify sử dụng là các mô hình xử lý ngôn ngữ tự nhiên (NLP) . Các dữ liệu nguồn của các mô hình này, như tên cho thấy, thường là các siêu dữ liệu theo từ, các bài báo, blog và các văn bản khác trên internet.

![alt](https://drive.google.com/uc?id=0B05rqFCwNCjkMl82ZkVCZWZOX2s&export=download)

Xử lý Ngôn ngữ Tự nhiên - khả năng của một máy tính để hiểu tiếng nói của con người như nó được nói - là một lĩnh vực rộng lớn cho chính nó, thường được khai thác thông qua các API phân tích tình cảm.

Cơ chế chính xác của NLP nằm ngoài phạm vi của bài viết này, tuy nhiên đây là những gì xảy ra ở mức rất cao: Spotify thu thập dữ liệu trên web liên tục tìm các bài đăng trên blog và các văn bản viết về âm nhạc và tìm ra những gì mọi người đang nói về các nghệ sĩ cụ thể và bài hát - những tính từ và ngôn ngữ thường được sử dụng trong những bài hát đó, những nghệ sĩ và bài hát nào cũng được thảo luận cùng với họ.

Mặc dù tôi không biết chi tiết về cách Spotify chọn xử lý dữ liệu đã đã được thu thập của họ, tôi có thể cho bạn biết cách Echo Nest đã làm việc với chúng như thế nào. Họ sẽ đặt chúng vào cái mà họ gọi là "các vector văn hoá vùng miền" hoặc "các thuật ngữ(term) top". Mỗi nghệ sĩ và bài hát có hàng ngàn thuật ngữ hàng ngày thay đổi hàng ngày. Mỗi thuật ngữ có trọng lượng liên quan, cho thấy mức độ quan trọng của mô tả (khoảng, xác suất là ai đó sẽ mô tả âm nhạc như thuật ngữ đó.)

![alt](https://drive.google.com/uc?id=0B05rqFCwNCjkQ01jNHI5eXZnV0E&export=download)

Sau đó, giống như trong Collaborative Filtering, mô hình NLP sử dụng các thuật ngữ và trọng lượng này để tạo ra một biểu diễn vector của bài hát có thể được sử dụng để xác định xem hai mẩu nhạc có giống nhau hay không. Cũng kinh, phải không?

### Recommendation Model #3: Raw Audio Models

Mục đích chính của mô hình thứ ba tiếp tục cải thiện tính chính xác của dịch vụ đề xuất tuyệt vời này. Nhưng thực tế, mô hình này cũng phục vụ cho mục đích thứ yếu: Không giống như hai loại mô hình đầu tiên, các mô hình âm thanh thô sẽ tính đến các bài hát mới.

**Chẳng hạn, bài hát mà bạn ca sĩ-người viết nhạc của mới đưa lên Spotify. Có lẽ nó chỉ có 50 nghe, vì vậy có ít người nghe nenen dùng collaboratively filter có lẽ là không hợp lý. Nó cũng không được đề cập đến bất cứ nơi nào trên internet, vì vậy các mô hình NLP sẽ không nhận được vào nó.** May mắn thay, các mô hình âm thanh sử dụng bản thô(raw) không phân biệt giữa bài hát mới và bài hát phổ biến, vì vậy với sự giúp đỡ của họ, bài hát của bạn bè của bạn có thể lằm ở cuối trong danh sách phát. Discover Weekly sẽ là các bài hát phổ biến nhất!

Vậy làm thế nào chúng ta có thể phân tích các dữ liệu âm thanh thô , có vẻ như trừu tượng?

Với convolutional neural networks là công nghệ tương tự đằng sau sự nhận biết khuôn mặt. Trong trường hợp của Spotify, chúng đã được sửa đổi để sử dụng trên dữ liệu âm thanh thay vì các pixel. Dưới đây là một ví dụ về kiến ​​trúc mạng nơron:

![alt](https://drive.google.com/uc?id=0B05rqFCwNCjkeEJDV1VsMWRhdFE&export=download)

Mạng neural network đặc biệt này có bốn lớp convolutional , được xem như các thanh dày bên trái, và ba lớp dày đặc, được xem như các thanh bên hẹp hơn bên phải. Đầu vào là các đại diện tần số thời gian của các khung âm thanh, sau đó được ghép nối thành hình quang phổ.

Các khung âm thanh đi qua các lớp này, và sau lớp cuối cùng, bạn có thể thấy một lớp "global temporal pooling", lần lượt qua các tầng khác nhau, tại mỗi tần sẽ chó ra các kết quả là các tính chất của bài hát.

Sau khi xử lý, mạng neural thông qua sự hiểu biết về bài hát, bao gồm các đặc điểm như **thời gian ước tính**, **nốt**, **chế độ**, **tốc độ**, và **độ ồn**. 

Ví dụ về output trên tài liệu tham khảo: http://docs.echonest.com.s3-website-us-east-1.amazonaws.com/_static/AnalyzeDocumentation.pdf
```
{
"meta":
{
"analyzer_version":"3.08b", "detailed_status":"OK", "filename":"/Users/Jim/
Desktop/file.mp3", "artist":"Michael Jackson", "album":"Thriller",
"title":"Billie Jean", "genre":"Rock", "bitrate":192, "sample_rate":44100,
"seconds":294, "status_code":0, "timestamp":1279120425, "analysis_time":
3.83081
},
"track":
{
"num_samples":6486072, "duration":294.15293,
"sample_md5":"0a84b8523c00b3c8c42b2a0eaabc9bcd", "decoder":"mpg123",
"offset_seconds":0, "window_seconds":0, "analysis_sample_rate":22050,
"analysis_channels":1, "end_of_fade_in":0.87624, "start_of_fade_out":
282.38948, "loudness":-7.078, "tempo":117.152, "tempo_confidence":0.848,
"time_signature":4, "time_signature_confidence":0.42, "key":6,
"key_confidence":0.019, "mode":1, "mode_confidence":0.416,
"codestring":"eJwdk8U7m4Rz9Pej...tbtSnk8U7m4Rz980uF", "code_version":3.15,
"echoprintstring":"eJzFnQuyrTquZbsENjamOf5A_5t...pDF6eF__7eH_D9MWE8p",
"echoprint_version": 4.12, "synchstring": "eJxlWwmWJCsOu0ocIWz2-1-
ssSRDZP...nUf0aeyz4=", "synch_version": 1.00, "rhythmstring":
"eJxVnAmyHDcM...9v71b_92-5V-fmWuX2n", "rhythm_version": 1.00
},
"bars":
[{"start":1.49356, "duration":2.07688, "confidence":0.037}, ...],
"beats":
[{"start":0.42759, "duration":0.53730, "confidence":0.936}, ...],
"tatums":
[{"start":0.16563, "duration":0.26196, "confidence":0.845}, ...],
"sections":
[{"start":0.00000, "duration":8.11340, "confidence":1.000,
"loudness": -15.761, "tempo": 135.405, "tempo_confidence": 0.938,
 "key": 0, "key_confidence": 0.107, "mode": 1, "mode_confidence": 0.516,
 "time_signature": 4, "time_signature_confidence": 1.000}, ...],
"segments":
[{
"start":0.00000, "duration":0.31887, "confidence":1.000,
"loudness_start":-60.000, "loudness_max_time":0.10242,
"loudness_max":-16.511, "pitches":[0.370, 0.067, 0.055, 0.073, 0.108, 0.082,
0.123, 0.180, 0.327, 1.000, 0.178, 0.234], "timbre":[24.736, 110.034, 57.822,
-171.580, 92.572, 230.158, 48.856, 10.804, 1.371, 41.446, -66.896, 11.207]
 }, ...]
}
```

Cuối cùng, sự hiểu biết về các đặc điểm chính của bài hát cho phép Spotify hiểu được sự tương đồng cơ bản giữa các bài hát và do đó người dùng có thể thưởng thức chúng dựa trên lịch sử nghe của riêng họ.

Kết quả thực nghiệm lấy từ http://benanne.github.io/2014/08/05/spotify-cnns.html
<iframe src="https://embed.spotify.com/?uri=spotify:user:sander_dieleman:playlist:3KcOA1o1Q1E7AKJp6lRKOG" width="300" height="380" frameborder="0" allowtransparency="true"></iframe>
<iframe src="https://embed.spotify.com/?uri=spotify:user:sander_dieleman:playlist:4XSo1qV9vGNwM7uz8LYwDR" width="300" height="380" frameborder="0" allowtransparency="true"></iframe>


<iframe src="https://embed.spotify.com/?uri=spotify:user:sander_dieleman:playlist:2CRSJ4h9cWvDSwNoqh9UJC" width="300" height="380" frameborder="0" allowtransparency="true"></iframe>
<iframe src="https://embed.spotify.com/?uri=spotify:user:sander_dieleman:playlist:121nUXz11tA96ONF4Dk2Eh" width="300" height="380" frameborder="0" allowtransparency="true"></iframe>



![alt](http://galvanize-wp.s3.amazonaws.com/wp-content/uploads/2016/08/18104334/Screen-Shot-2016-08-17-at-4.48.55-PM.png) 
Và kết quả qua 3 mô hình trên. Spotify đưa các bài hát vào Discover Weekly playlist của họ. Tất nhiện với số lượng bài hát và user gần như không giới hạn về số lượng trên internet khổng lồ như vậy họ phải liên kết với các ecosystem.


Cuối cùng mình muốn nói rằng trong cuộc sống chắc hản ai cũng có những lúc gặp buồn chán, thất tình, stress,... thậm chí là cả chán đời, tuyệt vọng rất cần yếu tố giúp bạn thoát khỏi những rắc rối đó để cảm thấy yêu đời hơn. Có rất nhiều cách, nhưng có lẽ âm nhạc là cách được nhiều người lựa chọn nhất vì nó khá phổ biến và chúng tá có thể thưởng thức mọi lúc mọi nơi. Nhưng không phải bài nhạc nào cũng hợp với tậm trạng bạn lúc đó. Mình không có ý quảng cáo cho Spotify nhưng bạn hãy thử nghe Spotify nhé.


*Link tham khảo:*

- https://www.spotify.com/jp/discoverweekly/
- https://qz.com/1108548/costco-cost-says-the-threat-of-tariffs-and-duties-pose-a-risk-to-its-business/
- https://www.slideshare.net/MrChrisJohnson/from-idea-to-execution-spotifys-discover-weekly/31-1_0_0_0_1
http://benanne.github.io/2014/08/05/spotify-cnns.html
- http://docs.echonest.com.s3-website-us-east-1.amazonaws.com/_static/AnalyzeDocumentation.pdf
- https://notes.variogr.am/2012/12/11/how-music-recommendation-works-and-doesnt-work/
- https://hackernoon.com/spotifys-discover-weekly-how-machine-learning-finds-your-new-music-19a41ab76efe
- https://www.slideshare.net/erikbern/collaborative-filtering-at-spotify-16182818/11-Supervised_learning_Matrix_completion