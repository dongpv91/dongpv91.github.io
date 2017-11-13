---
layout: entry
title: Các thành phần để xây dựng plugin cho eclipse.
description: Eclipse là IDE được sử dụng rất phổ biến hiện nay. Eclipse hỗ trợ rất nhiều ngôn ngữ lập trình khác nhau, trong đó có Java. Hầu hết các lập trình viên phát triển ứng dụng Java đều dùng eclipse nên việc xây dựng plugin cho eclipse sẽ thuận tiện trong quá trình xây dựng ứng dụng Java.
---

Eclipse là IDE được sử dụng rất phổ biến hiện nay. Eclipse hỗ trợ rất nhiều ngôn ngữ lập trình khác nhau, trong đó có Java. Hầu hết các lập trình viên phát triển ứng dụng Java đều dùng eclipse nên việc xây dựng plugin cho eclipse sẽ thuận tiện trong quá trình xây dựng ứng dụng Java.

Một trong những điểm mạnh của Eclipse đó là cho phép lập trình viên viết các ứng dụng tích hợp dưới dạng plug-in để phục vụ cho nhu cầu công việc bất kỳ một cách dễ dàng. Lập trình viên có thể thực hiện điều đó thông qua môi trường phát triển plugin PDE *(Plug-in Development Environment)* do chính Eclipse cung cấp.

### Các thành phần PDE

PDE được sử dụng trong quá trình phát triển plug-in chủ yếu trong việc tạo giao diện tương tác (User Interface – UI) giữa người sử dụng và plug-in.

#### View

Trong Eclipse UI, "view" (khung nhìn) là một trong những thành phần trực quan quan trọng nhất. Thông thường, view được sử dụng để điều hướng một hệ thống phân cấp của thông tin, mở một trình soạn thảo hoặc hiển thị các thông tin bổ sung cho các thành phần đang được mở bởi trình soạn thảo đang ở trạng thái "active". Ở hình bên dưới, **Package Explorer, Task List, Outline** là các view của Eclipse.

Mỗi view có một thanh công cụ *(toolbar)* và trình đơn *(menu)* của riêng mình. Lập trình viên cũng có thể gắn thêm vào thanh công cụ cũng như trình đơn của các view sẵn có các nút bấm *(button)* mới để làm phong phú thêm chức năng của view đó.  

![Eclipse 1](https://drive.google.com/uc?id=0B05rqFCwNCjkT1JYd1o2d211Sm8&export=download)

#### Context menu

Context menu (hay *"Popup menu"*) là trình đơn ngữ cảnh, được hiển thị khi người sử dụng mở trình đơn trên các đối tượng cụ thể (các đối tượng trên view hoặc trình soạn thảo).

![Eclipse 2](https://drive.google.com/uc?id=0B05rqFCwNCjkOTRYWTFrVXhjbVU&export=download)

#### Action – Command Framework

Đây là hai framework mà Eclipse cung cấp để tạo và gắn thêm các menu item *(mục trình đơn)* vào một menu nào đó.

Action framework là framework cũ hơn và hiện đang được khuyến nghị không nên sử dụng nữa. Command framework mới hơn, linh động, uyển chuyển hơn nhưng cũng phức tạp hơn. Nó cao cấp hơn và nên được sử dụng cho những chức năng mới.

Command framework tương thích với hầu hết, song không phải là tất cả menu. Một số menu của Eclipse vẫn chưa được viết lại để tương thích với framework mới này. Do đó, trong một vài trường hợp cá biệt, lập trình viên phải sử dụng action framework thay thế.

#### Các thành phần khác

Ngoài một số thành phần chính PDE còn một số thành phần không thể thiếu: Menu, Dialog, Editor, TreeView, Toolbar,...

### Những thành phần trong JDT

#### Truy cập mã nguồn Java

Eclipse JDT cung cấp API để lập trình viên có thể truy cập và thao tác với mã nguồn Java. Nó cho phép truy cập đến các Java project, tạo project hay chỉnh sửa những project đó.

Eclise JDT cho phép truy cập mã nguồn Java theo hai cách bằng việc sử dụng các hệ thống phân cấp khác nhau: Java Model và Abstract Syntax Tree (AST). Những hệ thống phân cấp này không phụ thuộc lẫn nhau và phù hợp với những mục đích khác nhau.

##### Java model

Java Model là một tập các *"interface"* biểu diễn các phương thức *(method)*, lớp *(class)*, giao diện *(interface)* và các thành phần khác của Java. Nó là một hệ thống phân cấp gọn nhẹ, có khả năng kháng lỗi. Nó cung cấp những thông tin cơ bản về cấu trúc mã nguồn Java nên để sửa đổi hay tạo các thành phần mới rất nhanh chóng.

Tuy nhiên nhược điểm lớn nhất của nó là không chứa đầy đủ các thông tin về mã nguồn. Vì vậy, mà khả năng của nó có phần hạn chế.

Java Model được định nghĩa trong plug-in `org.eclipse.jdt.core`. Gốc của hệ thống phân cấp Java Model này là `IJavaElement`.

![Eclipse 3](https://drive.google.com/uc?id=0B05rqFCwNCjkUjNEWUlJQnpFUmc&export=download)

##### Abstract Syntax Tree

Abstract Syntax Tree (cây cú pháp trừu tượng) là một tập hợp các lớp (class) biểu diễn các phương thức *(method)*, lớp *(class)*, giao diện *(interface)* và các thành phần khác của Java. Nó cung cấp đầy đủ thông tin về cấu trúc mã nguồn Java giúp cho lập trình viên có thể thực hiện bất kỳ thao tác nào (sửa đổi, tạo mới, đọc hay xóa phần tử) một cách dễ dàng.

Nhược điểm lớn nhất của hệ thống phân cấp này là các thao tác của nó thông thường chậm hơn rất nhiều so với hệ thống phân cấp Java Model. Hơn nữa, khả năng chịu lỗi của nó cũng kém hơn so với hệ thống phân cấp Java Model.

Gói (package) chính đối với AST là `org.eclipse.jdt.core.dom` trong plug-in `org.eclipse.jdt.core`. Gốc của hệ thống phân cấp AST này là lớp `ASTNode`.

Ví dụ với đoạn mã nguồn Java sau:

```java
public void start(BundleContext context) throws Exception
{
    super.start(context);
}
```

Hệ thống phân cấp AST sẽ phân tích đoạn mã trên dưới dạng cây cú pháp với các thuộc tính kèm theo rất đầy đủ như hình dưới đây.

![Eclipse 4](https://drive.google.com/uc?id=0B05rqFCwNCjkdk94SDl3RGlCTGc&export=download)

##### Duyệt mã nguồn với ASTVistor

ASTVisitor là một lớp trừu tượng (abstract class) rất hữu dụng trong việc thu thập thông tin về AST của các phần tử (ASTNode) bất kỳ. Thông tin mà nó thu thập được có thể được sử dụng để phục vụ cho các thao tác tiếp theo trên mã nguồn.

ASTVisitor được xây dựng theo mẫu thiết kế Visitor. Khi một phần tử (ASTNode) nào đó *"accept"* một đối tượng ASTVisitor thì đối tượng này sẽ duyệt trên những ASTNode được chỉ định. Cần nói thêm là hệ thống phân cấp AST có gốc là ASTNode, nhưng được chia thành rất nhiều loại khác nhau, ứng với các phần tử cụ thể của Java (trên dưới 100 loại dẫn xuất của ASTNode).

#### Thao tác trên mã nguồn Java

Thao tác chủ yếu trên mã nguồn ngoài việc đọc nội dung thông tin cấu trúc của nó, việc thay đổi chúng la việc làm thường xuyên hơn cả. Tiến trình công việc chủ yếu khi thao tác trên mã nguồn Java sử dụng hệ thống phân cấp AST được mô tả cụ thể bên hình dưới.

![Eclipse 5](https://drive.google.com/uc?id=0B05rqFCwNCjkSXdVM1MzWUl5bk0&export=download)

Các bước tiến hành như sau:

- Mã nguồn Java trong project, được chuẩn bị để đem phân tích.
- Phân tích mã nguồn được chỉ định. Bộ phân tích cú pháp `eclipse.jdt.core.dom.ASTParser` sẽ đảm nhận vai trò này.
- Kết quả của quá trình phân tích là cây cú pháp AST.
- Thao tác trên cây cú pháp AST có thể được thực hiện theo hai cách: 1. Thao tác trực tiếp trên AST.

Lưu lại những thay đổi trên một bản ghi nhớ riêng biệt. Bản ghi nhớ này được xử lý bởi một đối tượng của ASTRewrite.

- Nếu có những thay đổi xảy ra thì cây cú pháp mới sẽ được lưu lại trên mã nguồn.
- `IDocument` là lớp bao của mã nguồn ở bước 1 và cần thiết ở bước 5 trong quá trình lưu lại mã nguồn mới.

### Những thành phần trong ERAPI được sử dụng

ERAPI được sử dụng cho phục vụ cho mục đích *"Refactoring"*. Refactoring, một cách tổng quát, là quá trình thay đổi hệ thống phần mềm, ứng dụng trong khi vẫn giữ nguyên những hoạt động cố hữu của nó. ERAPI ở đây chỉ phục vụ cho việc refactoring mã nguồn chương trình.

ERAPI là một thành phần của Language Toolkit (LTK) của Eclipse. ERAPI được cài đặt trong các plug-in `org.eclipse.ltk.core.refactoring` và `org.eclipse.ltk.ui.refactoring`.

#### Refactoring

Refactoring (`org.eclipse.ltk.core.refactoring.Refactoring`) là một lớp trừu tượng nhận nhiệm vụ thực hiện quá trình refactoring.

![Eclipse 6](https://drive.google.com/uc?id=0B05rqFCwNCjkck9TOUNnUExaQ3M&export=download)

![Eclipse 7](https://drive.google.com/uc?id=0B05rqFCwNCjkcTdFaXlDVFFjcGM&export=download)

Quá trình refactoring được thực hiện thông qua lớp Refactoring sẽ có thể phải thu thập thêm thông tin cần thiết. Chính vì vậy, những thông tin này cần phải được kiểm tra như là điều kiện đầu vào của quá trình refactoring. Khi những thông tin này được kiểm tra, nếu có bất cứ thông tin nào không hợp lệ, quá trình refactoring sẽ dừng ngay lập tức.

Sau khi các thông tin đầu vào là hợp hệ, lớp Refactoring kiểm tra lại một lần nữa xem các sự thay đổi có vi phạm điều kiện gì hay không. Nếu tất cả sự thay đổi đều hợp lệ, quá trình refactoring được coi là có thể xảy ra. Một đối tượng của lớp Change (trình bày ở phần dưới) sẽ được tạo ra. Khi đó người sử dụng sẽ quyết định có chấp nhận sự thay đổi này không thông qua một giao diện mà Eclipse cung cấp.

#### Change

Change (`org.eclipse.ltk.core.refactoring.Change`) là một lớp trừu tượng đại diện cho sự thay đổi của mã nguồn Java trong quá trình refactoring.

#### RefactoringWizard

RefactoringWizard (`org.eclipse.ltk.ui.refactoring.RefactoringWizard`) là một lớp trừu tượng nhận nhiệm vụ tạo ra một wizard hướng dẫn người sử dụng cách thức thực hiện một quá trình refactoring như thế nào, như thu thập thêm thông tin cần thiết cho quá trình refactoring hay hiển thị sự thay đổi nếu áp dụng refactoring...

### Kết luận

Eclipse hiện nay là một trong những IDE phổ biến nhất trên thế giới. Môi trường phát triển plug-in của Eclipse (PDE) rất mạnh nhưng cũng khá lớn. Do đó để có thể hiểu và sử dụng được những thành phần cơ bản của PDE cũng đòi hỏi rất nhiều thời gian.

Ngoài ra, một số công cụ khác của Eclipse như công cụ phát triển Java (JDT) cũng cần thiết được sử dụng kết hợp để có thể hoàn thành ứng dụng. Việc học cách sử dụng những công cụ này cũng đòi hỏi thời gian và kinh nghiệm bởi chúng khá phức tạp.

### Tham khảo

- http://www.eclipse.org/articles/Article-JavaCodeManipulation_AST/index.html
- http://appperfect.com/support/java-coding-rules/optimization.html
- Michael Petito, “*Eclipse Refactoring*”, EE564, 2007.
- [Leif Frenzel: The Language Toolkit: An API for Automated Refactorings in Eclipsebased IDEs.](http://www.eclipse.org/articles/Article-LTK/ltk.html)
- [Tobias Widmer: *Unleashing the Power of Refactoring,*](http://www.eclipse.org/articles/article.php?file=Article-Unleashing-the-Power-of-Refactoring/index.html)
- [*Platform Plug-in Developer Guide*](http://help.eclipse.org/indigo/index.jsp?topic=%2Forg.eclipse.platform.doc.isv%2Fguide%2Ffirstplugin.htm)
- [*Extending the Eclipse IDE – Plug-in Development Tutorial*](http://www.vogella.com/articles/EclipsePlugIn/article.html), Lars Vogel Dr Alex Blewitt, *“Eclipse 4 Plug-in Development by Example Beginner’s Guide”*, 2013
- Martin Aeschlimann, *“JDT fundamentals – Become a JDT tool smith”*, 2008.