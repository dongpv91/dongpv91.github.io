---
layout: entry
title: Các thành phần để xây dựng plugin cho eclipse.
description: PMD là công cụ phân tích mã nguồn. Nó tìm thấy những lỗ hổng chương trình phổ biến về variables, khối catch rỗng, tạo ra đối tượng không cần thiết,… . Nó hỗ trợ chủ yếu **Java** và một số ngôn ngữ như JavaScript, XML, XSL..
---


### []()1. PMD

PMD là công cụ phân tích mã nguồn. Nó tìm thấy những lỗ hổng chương trình phổ biến về variables, khối catch rỗng, tạo ra đối tượng không cần thiết,… . Nó hỗ trợ chủ yếu **Java** và một số ngôn ngữ như JavaScript, XML, XSL.

Tải các phiên bản và công cụ của PMD tại đây:

[http://sourceforge.net/projects/pmd/files/](http://sourceforge.net/projects/pmd/files/)

Link cài plugin cho eclipse:

[http://sourceforge.net/projects/pmd/files/pmd-eclipse/update-site/](http://sourceforge.net/projects/pmd/files/pmd-eclipse/update-site/)

[]() []() []() []()Hình 3‑8: PMD Plugin cho eclipse

PMD xây dụng một tập luật và dựa vào tập luật này để đưa ra các kết quả tối ưu. Tập luật này có thể được thay đổi(thêm sửa xóa) tùy thuộc vào mục đích và kinh nghiệm của lập trình viên. Các luật được sử dụng ở đây:

[http://pmd.sourceforge.net/snapshot/rules/index.html](http://pmd.sourceforge.net/snapshot/rules/index.html)

PMD quét mã nguồn Java và tìm kiếm các vấn đề tiềm năng như:

- Possible bugs: rỗng các khối try/catch/finally/switch statements
- Chết mã: các biến dịa phương, parameters và các phương thức private không được sử dụng
- Mã chưa được tối ưu: Sử dụng lãng phí String/StringBuffer
- Biểu thức quá phức tạp: các statements không cần thiết, vòng lập for có thể thay bằng vong lặp while
- Sao chép mã: copy/paste code tức là copy/paste bug

PMD không sử dụng mã nguồn trực tiếp, nó sử dụng một phân tích cú pháp JavaCC tạo ra để phân tích mã nguồn và tạo ra một AST.

class Example {  void bar() {   while (baz)    buz.doSomething();  } }

 

AST cho đoạn mã trên như sau:

CompilationUnit TypeDeclaration ClassDeclaration:(package private) UnmodifiedClassDeclaration(Example) ClassBody ClassBodyDeclaration MethodDeclaration:(package private) ResultType MethodDeclarator(bar) FormalParameters Block BlockStatement Statement WhileStatement Expression PrimaryExpression PrimaryPrefix Name:baz Statement StatementExpression:null PrimaryExpression PrimaryPrefix Name:buz.doSomething PrimarySuffix Arguments

Luật được viết dưới dạng Xpath. Ví dụ như:

TypeDeclaration[count(//VariableDeclarator[../Type/ReferenceType/ClassOrInterfaceType[@Image='Logger']])>1]

tức là chỉ tạo ra một đối tượng của lớp Logger áp dụng cho lớp sau khi có nhiều logger trong một lớp

public class a { Logger log = null; Logger log = null; int b; void myMethod() { Logger log = null; int a; } class c { Logger a; Logger a; } }

 

 

PMD tích hợp với rất nhiều các IDE khác nhau: JDeveloper, Eclipse, JEdit, JBuilder, BlueJ, CodeGuide, NetBeans/Sun Java Studio Enterprise/Creator, IntelliJ IDEA, TextPad, Maven, Ant, Gel, JCreator, và Emacs.

### []() []()2. Android Lint

Android Lint là một công cụ mới được giới thiệu trong ADT 16. Nó có thể quét các nguồn dự án Android cho các lỗi tiềm năng. Nó có các loại là công cụ dòng lệnh và plugin cho Eclipse (mô tả dưới đây) , và IntelliJ. Kiến trúc không dành cho một IDE độc lập do đó, nó sẽ được tích hợp với IDE khác, với các công cụ xây dựng khác và với các hệ thống tích hợp khác.

Mỗi vấn đề được phát hiện bởi công cụ này được báo cáo với một thông điệp mô tả và một mức độ nghiêm trọng, do đó có thể nhanh chóng ưu tiên những cải tiến quan trọng mà cần phải được thực hiện. Cũng có thể cấu hình mức độ nghiêm trọng của vấn đề để bỏ qua các vấn đề không liên quan cho dự án của bạn, hoặc tăng mức độ nghiêm trọng. Công cụ này có một giao diện dòng lệnh, vì vậy có thể dễ dàng tích hợp nó vào quá trình kiểm tra tự động.

Đây là một số ví dụ về các loại lỗi mà nó tìm kiếm:

- Thiếu bản dịch ( và bản dịch không sử dụng)
- Vấn đề Layout (tất cả các vấn đề công cụ layoutopt cũ được sử dụng để tìm kiếm,…)
- Tài nguyên không sử dụng
- Kích thước mảng không phù hợp (khi mảng được định nghĩa đa chiều)
- Khả năng tiếp cận và quốc tế các vấn đề ( chuỗi hardcoded , thiếu contentDescription , vv)
- Vấn đề biểu tượng ( như thiếu mật độ , biểu tượng trùng lặp , kích thước sai , vv)
- Vấn đề khả năng sử dụng ( như không quy định cụ thể một loại đầu vào một trường văn bản )
- Lỗi Manifest
- …

![](https://i0.wp.com/developer.android.com/studio/images/write/lint.png?resize=604%2C287&ssl=1)

 

- **Chạy lint từ Eclipse**

Nếu ADT Plugin được cài đặt trong môi trường Eclipse rồi, lint chạy tự động khi thực hiện một trong những hành động này:

- Xuất khẩu một apk
- Chỉnh sửa và lưu một tập tin nguồn XML trong dự án Android của bạn (chẳng hạn như một tập tin biểu hiện hoặc bố trí)
- Thay đổi Layout của ứng dụng Android

Có thể tắt tự động kiểm tra này từ trang **Error Checking Lint** trong Preferences Eclipse.

![](https://i2.wp.com/tools.android.com/_/rsrc/1472841747211/recent/lint/lint-window2.png)

- **Chạy lint từ Android studio**

Trên thanh menu **Analyze > Inspect Code  
![Specify Inspection Scope](https://i2.wp.com/developer.android.com/studio/images/write/specify_inspection_scope_2x.png?ssl=1)  
**

![](https://i1.wp.com/developer.android.com/studio/images/write/inspectandfix_2x.png?ssl=1)

 

- **Chạy bằng dòng lệnh**

Để kiểm tra toàn bộ project: lint [flags] <project directory>

Để hiển thị các flag: lint –help

 

*Tài liệu tham khảo*

[https://developer.android.com/studio/write/lint.html](https://developer.android.com/studio/write/lint.html)

[http://qiita.com/operandoOS/items/1318ca9fca5c238e2e02](http://qiita.com/operandoOS/items/1318ca9fca5c238e2e02)

[https://android.googlesource.com/platform/tools/base/+/master/lint/libs/lint-checks/src/main/java/com/android/tools/lint/checks](https://android.googlesource.com/platform/tools/base/+/master/lint/libs/lint-checks/src/main/java/com/android/tools/lint/checks)

[http://sourceforge.net/projects/pmd/files](http://sourceforge.net/projects/pmd/files/)/

[http://sourceforge.net/projects/pmd/files/pmd-eclipse/update-site/](http://sourceforge.net/projects/pmd/files/pmd-eclipse/update-site/)


