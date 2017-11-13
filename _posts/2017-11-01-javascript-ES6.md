---
layout: entry
title: JavaScript ES6.
description: ECMAScript 6/ES6 là phiên bản mới nhất của bộ tiêu chuẩn ECMAScript – một bộ đặc tả tiêu chuẩn dành cho Javascript do Hiệp hội các nhà sản xuất máy tính Châu Âu (European Computer Manufacturers Association – ECMA) đề xuất. Phiên bảnECMAScript phổ biến ở thời điểm hiện tại (đầu 2015), và được hầu hết các trình duyệt hỗ trợ là ES5 và ES5.1 (ra mắt vào khoảng năm 2009 và 2011)。
---

### ES6 là gì?

**ECMAScript 6/ES6** là phiên bản mới nhất của bộ tiêu chuẩn **ECMAScript** – một bộ đặc tả tiêu chuẩn dành cho Javascript do Hiệp hội các nhà sản xuất máy tính Châu Âu (*European Computer Manufacturers Association* – *ECMA*) đề xuất. Phiên bản**ECMAScript** phổ biến ở thời điểm hiện tại (đầu 2015), và được hầu hết các trình duyệt hỗ trợ là **ES5** và **ES5.1** (ra mắt vào khoảng năm 2009 và 2011)

**ES6** đã ra mắt vào giữa năm 2015 và được lấy tên chính thức là **ES2015**, với rất nhiều những tính năng mới lạ, và cần thiết đối với sự phát triển chóng mặt của Javascript trong những năm gần đây. Ngoài ra, phiên bản mới nhất của bộ đặc tả tiêu chuẩn này là **ES7** cũng đang được phát triển, tuy chưa định ngày ra mắt chính thức nhưng cũng đã bắt đầu gây được sự chú ý của giới công nghệ với những tính năgn hấp dẫn như *async function*,*observer*,…

Trong phạm vi bài viết này, mình sẽ liệt kê ra một số chức năng nổi bật nhất. Và mình sẽ hạn chế dịch những tên khái niệm này ra tiếng Việt, để đảm bảo tính toàn vẹn của kiến thức (thực ra là vì dịch mấy từ thuật ngữ kiểu này ra tiếng Việt khó vô đối)

### <span id="Cac_chuc_nang_moi_cua_ES6">Các chức năng mới của ES6</span>

#### <span id="Arrow">Arrow</span>

Arrow là một dạng viết tắt của các function sử dụng dấu `=>`, tương tự như trong C#, Java 8,…

```
// Expression bodies 
var odds = evens.map(v => v + 1);
var nums = evens.map((v, i) => v + i);
var pairs = evens.map(v => ({
    even: v,
    odd: v + 1
}));

// Statement bodies
nums.forEach(v => {
    if (v % 5 === 0) fives.push(v);
});

// Lexical this 
var bob = {
    _name: "Bob",
    _friends: [],
    printFriends() {
        this._friends.forEach(f => console.log(this._name + " knows " + f));
    }
}
```

#### <span id="Class">Class</span>

Đối với Javascript truyền thống, để sử khai báo và kế thừa các class, chúng ta phải thiết kế theo hướng sử dụng Prototype (prototype-based OO). Việc khai báo và kế thừa các class trong ES6 dễ hơn rất nhiều với cú pháp gần giống với Java và C++, ngoài ra, class trong ES6 cũng hỗ trợ kế thừa thông qua prototype, các static method, constructor,…

```
class SkinnedMesh extends THREE.Mesh {
    constructor(geometry, materials) {
        super(geometry, materials);
        this.idMatrix = SkinnedMesh.defaultMatrix();
        this.bones = [];
        this.boneMatrices = [];
        //... 
    }

    update(camera) {
        //... 
        super.update();
    }
    get boneCount() {
        return this.bones.length;
    }
    set matrixType(matrixType) {
        this.idMatrix = SkinnedMeshmatrixType;
    }
    static defaultMatrix() {
        return new THREE.Matrix4();
    }
}
```

#### <span id="Xu_ly_chuoi">Xử lý chuỗi</span>

Xử lý chuỗi trong ES6 đã trở nên dễ dàng và tiện dụng hơn rất nhiều, mang hơi hướng của các ngôn ngữ như Python, Perl,… đặc biệt, hỗ trợ chuỗi nhiều dòng, đây có lẽ là một cải tiến khiến rất nhiều người cảm thấy thích thú.

```
// Basic literal string creation `In JavaScript 'n' is a line-feed.` 
// Multiline strings `In JavaScript this is  not legal.`
// String interpolation
var name = "Bob",
    time = "today";
`Hello ${name}, how are you ${time}?` 
// Construct an HTTP request prefix is used to interpret the replacements and construction 
GET `http://foo.org/bar?a=${a}&b=${b} Content-Type: application/json X-Credentials: ${credentials} { "foo": ${foo}, "bar": ${bar}}` (myOnReadyStateChangeHandler);
```

#### <span id="Gia_tri_default_cho_tham_so">Giá trị default cho tham số</span>

Ở phiên bản này, Javascript đã có thể sử dụng các giá trị mặc định cho tham số truyền vào các hàm như những ngôn ngữ lập trình khác như C++, C#.

```
function f(x, y = 12) {   
    // y = 12 nếu không truyền giá trị cho nó (hoặc truyền undefined)    
    return x + y;
}
f(3) == 15
```

#### <span id="Truyen_tham_so_khong_xac_dinh_so_luong">Truyền tham số không xác định số lượng</span>

Việc này trước đây có thể thực hiện thông qua biến `arguments` có trong từng hàm, nhưng giờ đây chúng ta có thể sử dụng nó một cách linh hoạt hơn rất nhiều.

```
function f(x, ...y) {  
    // y là một mảng  
    return x * y.length;
}
f(3, "hello", true) == 6
```

#### <span id="Truyen_tham_so_thong_qua_tung_phan_tu_cua_mang">Truyền tham số thông qua từng phần tử của mảng</span>

Với kĩ thuật này, bạn có thể truyền một mảng hoặc một đối tượng vào một hàm, các phần tử của mảng/đối tượng này sẽ được tự động truyền vào thành các tham số của hàm đó.

```
function f(x, y, z) {  
        return x + y + z;
    }
    // Pass each elem of array as argument 
f(...[1, 2, 3]) == 6
```

#### <span id="Tu_khoa_let_va_const">Từ khoá let và const</span>

`const`, đúng như tên gọi của nó, là cách khai báo hằng số, một hằng số thì không thể thay đổi giá trị được.

```
const x = 10; x = 5; // Lỗi
```

`let` cũng là một dạng khai báo biến giống như `var`, tuy nhiên, biến được định nghĩa bằng từ khoá `let` có phạm vi truy cập khép kín trong khối lệnh chứa nó.

```
function testLet() {    
    // a *không* truy cập được tại đây     
    for (let a = 0; a < 5; a++) {        
        // a chỉ truy cập được trong này     
    };    
    // a *không* truy cập được tại đây 
}; 

function testVar() {  
    // b truy cập *được* tại đây     
    for (var b = 0; b < 5; b++) { 
        // b truy cập được ở tất cả mọi nơi trong hàm testVar()    
    };   
    // b truy cập *được* tại đây
};
```

#### <span id="Modules">Modules</span>

Ở phiên bản này, Javascript đã chính thức hỗ trợ module.

```
// lib/math.js 
export function sum(x, y) {  
    return x + y;
}
export var pi = 3.141593;

// app.js 
import * as math from "lib/math";
alert("2π = " + math.sum(math.pi, math.pi));

// otherApp.js
import {
    sum, pi
}
from "lib/math";
alert("2π = " + sum(pi, pi));
```

#### <span id="Module_Loaders">Module Loaders</span>

Module loaders hỗ trợ các kiểu load: – Dynamic loading – State isolation – Global namespace isolation – Compilation hooks – Nested virtualization

Chúng ta có thể sử dụng loader mặc định (`System.import`) hoặc tự định nghĩa ra một loader mới.

```
// Dynamic loading – ‘System’ is default loader
System.import('lib/math').then(function(m) {  
    alert("2π = " + m.sum(m.pi, m.pi));
}); 
// Create execution sandboxes – new Loaders
var loader = new Loader({  
    global: fixup(window)
        // replace ‘console.log’ 
});
loader.eval("console.log('hello world!');"); 
// Directly manipulate module cache 
System.get('jquery');
System.set('jquery', Module({
    $: $
})); // WARNING: not yet finalized
```

#### <span id="Map_Set_WeakMap_WeakSet">Map, Set, WeakMap, WeakSet</span>

ES6 còn giới thiệu thêm một số kiểu dữ liệu mới để hỗ trợ chúng ta thực hiện các thuật toán phức tạp hơn.

```
// Sets 
var s = new Set();
s.add("hello").add("goodbye").add("hello");
s.size === 2;
s.has("hello") === true; 
// Maps
var m = new Map();
m.set("hello", 42);
m.set(s, 34);
m.get(s) == 34; 
// Weak Maps 
var wm = new WeakMap();
wm.set(s, {
    extra: 42
});
wm.size === undefined 
    // Weak Sets
var ws = new WeakSet();
ws.add({
    data: 42
});
// Because the added object has no other references, it will not be held in the set
```

#### <span id="Class_ke_thua">Class kế thừa</span>

Trong ES6, các kiểu dữ liệu sẵn có như Array, Date, các DOM Elements có thể được kế thừa bởi các class mới.

```
class MyArray extends Array {    
    constructor(...args) {
        super(...args);
    }
} 
var arr = new MyArray();
arr[1] = 12;
arr.length == 2
```

#### <span id="Promises">Promises</span>

Promises là một thư viện dùng cho lập trình bất đồng bộ (asynchronous programming), hiện nay, Promises đã được ứng dụng rộng rãi trên nhiều thư viện Javascript (ví dụ: AngularJS)

```
function timeout(duration = 0) {    
    return new Promise((resolve, reject) => {        
        setTimeout(resolve, duration);    
    })
} 
var p = timeout(1000).then(() => {    
    return timeout(2000);
}).then(() => {    
    throw new Error("hmm");
}).catch(err => {    
    return Promise.all([timeout(100), timeout(200)]);
})
```
