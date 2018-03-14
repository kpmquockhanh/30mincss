### Reset box-sizing

Reset box-model để `width` và `height` không bị ảnh hưởng bởi `border`s hay `padding` của chúng.

#### CSS

```css
html {
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: inherit;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__box-sizing-reset">Demo</div>
</div>

<style>
.snippet-demo__box-sizing-reset {
  box-sizing: border-box;
  width: 200px;
  padding: 1.5em;
  color: #7983ff;
  font-family: sans-serif;
  background-color: white;
  border: 5px solid;
}
</style>

#### Giải thích

1. `box-sizing: border-box` làm cho việc bổ sung `padding` or `border`s không ảnh hưởng tới các `width` hay `height` của các phần tử.
2. `box-sizing: inherit` làm cho một element tôn trọng quy tắc `box-sizing` của cha nó.

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">✅ Không cảnh báo.</span>

* https://caniuse.com/#feat=css3-boxsizing

<!-- tags: layout -->

### Clearfix

Ensures that an element self-clears its children.
Đảm bảo rằng một phần tử tự clear con của nó.

###### Lưu ý: Tiều này chỉ hữu ích nếu bạn vẫn đang sử dụng float để xây dựng layout. Hãy xem xét sử dụng một phương pháp hiện đại với flexbox hoặc grid.

#### HTML

```html
<div class="clearfix">
  <div class="floated">float a</div>
  <div class="floated">float b</div>
  <div class="floated">float c</div>
</div>
```

#### CSS

```css
.clearfix::after {
  content: '';
  display: block;
  clear: both;
}

.floated {
  float: left;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__clearfix">
    <div class="snippet-demo__floated">float a</div>
    <div class="snippet-demo__floated">float b</div>
    <div class="snippet-demo__floated">float c</div>
  </div>
</div>

<style>
.snippet-demo__clearfix::after {
  content: '';
  display: block;
  clear: both;
}

.snippet-demo__floated {
  float: left;
}
</style>

#### Giải thích

1. `.clearfix::after` định nghĩa một element giả.
2. `content: ''` cho phép các element giả để ảnh hưởng đến layout.
3. `clear: both` chỉ ra rằng phía trái, phải hoặc cả 2 phía của phần tử không thẻ được lền kề phần tử đã float  mà không cùng một bối cảnh format block._(nghe hơi chuối :|)_

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">⚠️ Để đoạn mã này hoạt động đúng bạn cần đảm bảo rằng không có phần tử con nào trong container và không có float trước khi có container rõ ràng trong cùng bối cảnh định dạng (ví dụ floated columns).</span>

<!-- tags: layout -->

### Hằng tỉ lệ width/height

Cho một phàn tử có width biến đổi, nó sẽ đảm bảo chiều cao của nó vẫn tương xứng theo một kiểu phù hợp
(i.e., tỉ lệ chiều rộng chiều cao không đổi).

#### HTML

```html
<div class="constant-width-to-height-ratio"></div>
```

#### CSS

```css
.constant-width-to-height-ratio {
  background: #333;
  width: 50%;
}
.constant-width-to-height-ratio::before {
  content: '';
  display: block;
  padding-top: 100%;
  float: left;
}
.constant-width-to-height-ratio::after {
  content: '';
  display: block;
  clear: both;
}
```

#### Demo

Thay đổi kích thước cửa sổ trình duyệt của bạn để xem tỷ lệ phần tử vẫn giữ nguyên.

<div class="snippet-demo">
  <div class="snippet-demo__constant-width-to-height-ratio"></div>
</div>

<style>
.snippet-demo__constant-width-to-height-ratio {
  background: #333;
  width: 50%;
}
.snippet-demo__constant-width-to-height-ratio::before {
  content: '';
  display: block;
  padding-top: 100%;
  float: left;
}
.snippet-demo__constant-width-to-height-ratio::after {
  content: '';
  display: block;
  clear: both;
}
</style>

#### Giải thích

`padding-top` trên `::before` của phần tử giả là nguyên nhân height of phần tử để bằng một phần trăm chiều rộng của nó. Do đó `100%` có nghĩa là chiều cao của phần tử sẽ luôn là  `100%`  chiều rộng, tạo ra một hình vuông responsive.

Phương pháp này cũng cho phép nội dung được đặt bên trong phần tử bình thường.

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">✅ Không có gì.</span>

<!-- tags: layout -->

### Phân phối đền phần tử con

Phân phối đều các phần tử con trong phần tử cha.

#### HTML

```html
<div class="evenly-distributed-children">
  <p>Item1</p>
  <p>Item2</p>
  <p>Item3</p>
</div>
```

#### CSS

```css
.evenly-distributed-children {
  display: flex;
  justify-content: space-between;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__evenly-distributed-children">
    <p>Item1</p>
    <p>Item2</p>
    <p>Item3</p>
  </div>
</div>

<style>
.snippet-demo__evenly-distributed-children {
  display: flex;
  width: 100%;  
  justify-content: space-between;
}
</style>

#### Giải thích

1. `display: flex` cho phép flexbox.
2. `justify-content: space-between` phân bố đều các phần tử con theo chiều ngang. Mục đầu tiên của anh ta được đặt ở cạnh trái, trong khi mục cuối cùng được đặt ở cạnh bên phải.
EXTENSION OPTIONS

Ngoài ra, hãy sử dụng `justify-content: space-around`  để phân phối phần tử con có không gian xung quanh chúng, chứ không phải giữa chúng.

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">⚠️ Cần tiền tố để được hỗ trợ đầy đủ.</span>

* https://caniuse.com/#feat=flexbox

<!-- tags: layout -->

### Flexbox centering

Căn giữa theo chiều ngang và dọc phần tử con bên trong phần tử cha sử dụng `flexbox`.

#### HTML

```html
<div class="flexbox-centering">
  <div class="child">Centered content.</div>
</div>
```

#### CSS

```css
.flexbox-centering {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__flexbox-centering">
    <p class="snippet-demo__flexbox-centering__child">Nội dung chính giữa.</p>
  </div>
</div>

<style>
.snippet-demo__flexbox-centering {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 200px;
}
</style>

#### Giải thích

1. `display: flex` cho phép flexbox.
2. `justify-content: center` căn giữa phần tử con theo chiều dọc.
3. `align-items: center` căn giữa phần tử con theo chiều ngang.

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">⚠️ Cần tiền tố đề được hỗ trợ đầy đủ.</span>

* https://caniuse.com/#feat=flexbox

<!-- tags: layout -->

### Căn giữa grid

Căn giữa theo chiều ngang và dọc phần tử con bên trong phần tử cha sử dụng `grid`.

#### HTML

```html
<div class="grid-centering">
  <div class="child">Centered content.</div>
</div>
```

#### CSS

```css
.grid-centering {
  display: grid;
  justify-content: center;
  align-items: center;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__grid-centering">
    <p class="snippet-demo__grid-centering__child">Centered content.</p>
  </div>
</div>

<style>
.snippet-demo__grid-centering {
  display: grid;
  justify-content: center;
  align-items: center;
  height: 200px;
}
</style>

#### Explanation

1. `display: grid` cho phép flexbox.
2. `justify-content: center` căn giữa phần tử con theo chiều dọc.
3. `align-items: center` căn giữa phần tử con theo chiều ngang.

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">✅ Không có gì.</span>

* https://caniuse.com/#feat=css-grid

<!-- tags: layout -->

### Layout grid

Website cơ bản sử dụng `grid`.

#### HTML

```html
<div class="grid-layout">
  <div class="header">Header</div>
  <div class="sidebar">Sidebar</div>
  <div class="content">
    Content
    <br>
    Lorem ipsum dolor sit amet, consectetur adipisicing elit.
  </div>
  <div class="footer">Footer</div>
</div>
```

#### CSS

```css
.grid-layout {
  display: grid;
  grid-gap: 10px;
  grid-template-columns: repeat(3, 1fr);
  grid-template-areas:
    'sidebar header header'
    'sidebar content content'
    'sidebar footer  footer';
  color: white;
}
.grid-layout > div {
  background: #333;
  padding: 10px;
}
.sidebar {
  grid-area: sidebar;
}
.content {
  grid-area: content;
}
.header {
  grid-area: header;
}
.footer {
  grid-area: footer;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__grid-layout">
    <div class="box snippet-demo__grid-layout__header">Header</div>
    <div class="box snippet-demo__grid-layout__sidebar">Sidebar</div>
    <div class="box snippet-demo__grid-layout__content">Content
      <br> Lorem ipsum dolor sit amet, consectetur adipisicing elit.
    </div>
    <div class="box snippet-demo__grid-layout__footer">Footer</div>
  </div>
</div>

<style>
.snippet-demo__grid-layout {
  margin: 1em;
  display: grid;
  grid-gap: 10px;
  grid-template-columns: repeat(3, 1fr);
  grid-template-areas:
    "sidebar header header"
    "sidebar content content"
    "sidebar  footer  footer";
  background-color: #fff;
  color: white;
}
.snippet-demo__grid-layout > div {
  background: #333;
  padding: 10px;
}
.snippet-demo__grid-layout__sidebar {
    grid-area: sidebar;
}
.snippet-demo__grid-layout__content {
    grid-area: content;
}
.snippet-demo__grid-layout__header {
    grid-area: header;
}
.snippet-demo__grid-layout__footer {
    grid-area: footer;
}
</style>

#### Giải thích

1. `display: grid` cho phép grid.
2. `grid-gap: 10px` đinh nghĩa khoảng cách giữa các phần tử.
3. `grid-template-columns: repeat(3, 1fr)` định nghĩa 3 cột cùng kích thước.
4. `grid-template-areas` định nghĩa tên các khu vực grid.
5. `grid-area: sidebar` làm cho phần tử sử dụng vùng có tên `sidebar`.

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">✅ Không có gì.</span>

* https://caniuse.com/#feat=css-grid

<!-- tags: layout -->

### Cắt bớt văn bản

Nếu văn bản dài hơn một dòng, nó sẽ được cắt ngắn và kết thúc bằng một dấu chấm phẩy `…`.

#### HTML

```html
<p class="truncate-text">Nếu tôi vượt quá chiều rộng của một dòng, tôi sẽ bị cắt ngắn.</p>
```

#### CSS

```css
.truncate-text {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
  width: 200px;
}
```

#### Demo

<div class="snippet-demo">
  <p class="snippet-demo__truncate-text">
    Văn bản này sẽ bị cắt ngắn nếu chiều rộng vượt quá 200px.
  </p>
</div>

<style>
.snippet-demo__truncate-text {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
  width: 200px;
  margin: 0;
}
</style>

#### Giải thích

1. `overflow: hidden` ngăn văn bản tràn lên kích thước của nó (đối với block, 100% width và auto height).
2. `white-space: nowrap` ngăn văn bản vượt quá một chiều cao.
3. `text-overflow: ellipsis` makes it so that if the text exceeds its dimensions, it
   will end with an ellipsis.
4. `width: 200px;` đảm bảo rằng phần tử có một kích thước, để biết khi nào cần dấu chấm phẩy.

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">⚠️ Chỉ hoạt động cho các phần tử trên một dòng.</span>

* https://caniuse.com/#feat=text-overflow

<!-- tags: layout -->

### Vòng tròn

Tạo hình tròn với thuần CSS.

#### HTML

```html
<div class="circle"></div>
```

#### CSS

```css
.circle {
  border-radius: 50%;
  width: 2rem;
  height: 2rem;
  background: #333;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__circle"></div>
</div>

<style>
.snippet-demo__circle {
  border-radius: 50%;
  width: 2rem;
  height: 2rem;
  background: #333;
}
</style>

#### Giải thích

`border-radius: 50%` bẻ cong viền của một phần tử để tạo ra một vòng tròn.

Vì một vòng tròn có cùng bán kính tại bất kỳ điểm cho trước, `width` và `height` phải gioongsn hau. Các giá trị khác nhau sẽ tạo ra một hình elip.

#### Browser support

<span class="snippet__support-note">✅ Không có gì.</span>

* https://caniuse.com/#feat=border-radius

<!-- tags: visual -->

### Thanh cuộn tùy chỉnh

Tùy chỉnh scrollbar cho tài liệu và các phần tử với scrollable overflow (tràn có thể cuộn), trên nền tảng WebKit.

#### HTML

```html
<div class="custom-scrollbar">
  <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Iure id exercitationem nulla qui repellat laborum vitae, molestias tempora velit natus. Quas, assumenda nisi. Quisquam enim qui iure, consequatur velit sit?</p>
</div>
```

#### CSS

```css
/* Document scrollbar */
::-webkit-scrollbar {
  width: 8px;
}

::-webkit-scrollbar-track {
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.3);
  border-radius: 10px;
}

::-webkit-scrollbar-thumb {
  border-radius: 10px;
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.5);
}

/* Scrollable element */
.some-element::webkit-scrollbar {
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__custom-scrollbar">
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Iure id exercitationem nulla qui repellat laborum vitae, molestias tempora velit natus. Quas, assumenda nisi. Quisquam enim qui iure, consequatur velit sit?
    </p>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Iure id exercitationem nulla qui repellat laborum vitae, molestias tempora velit natus. Quas, assumenda nisi. Quisquam enim qui iure, consequatur velit sit?
    </p>
  </div>
</div>

<style>
.snippet-demo__custom-scrollbar {
  height: 100px;
  overflow: auto;
}

.snippet-demo__custom-scrollbar::-webkit-scrollbar {
  width: 8px;
}

.snippet-demo__custom-scrollbar::-webkit-scrollbar-track {
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.3);
  border-radius: 10px;
}

.snippet-demo__custom-scrollbar::-webkit-scrollbar-thumb {
  border-radius: 10px;
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.5);
}
</style>

#### Giải thích

1. `::-webkit-scrollbar` nhắm tới toàn bộ thanh scrollbar.
2. `::-webkit-scrollbar-track` chỉ nhắm tới scrollbar track.
3. `::-webkit-scrollbar-thumb` nhắm tới scrollbar thumb.

Có rất nhiều yếu tố giả khác mà bạn có thể sử dụng để tạo kiểu thanh cuộn. Để biết thêm thông tin, vào [WebKit Blog](https://webkit.org/blog/363/styling-scrollbars/)

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">⚠️ Kiểu dáng thanh cuộn dường như không xuất hiện trên bất kỳ bài hát tiêu chuẩn nào.</span>

* https://caniuse.com/#feat=css-scrollbar

<!-- tags: visual -->

### Lựa chọn văn bản tùy chọn

Thay đổi kiểu dáng của văn bản chọn lựa. ?????

#### HTML

```html
<p class="custom-text-selection">Chọn một vài văn bản này.</p>
```

#### CSS

```css
::selection {
  background: aquamarine;
  color: black;
}
.custom-text-selection::selection {
  background: deeppink;
  color: white;
}
```

#### Demo

<div class="snippet-demo">
  <p class="snippet-demo__custom-text-selection">Chọn một vài văn bản này.</p>
</div>

<style>
.snippet-demo__custom-text-selection::selection {
  background: deeppink;
  color: white;
}
.snippet-demo__custom-text-selection::-moz-selection {
  background: deeppink;
  color: white;
}
</style>

#### Giải thích

`::selection` đhịnh nghĩa một selector giả trên một phần tử định kiểu văn bản bên trong nó khi được chọn. Lưu ý rằng nếu bạn không kết hợp bất kỳ selector khác, style của bạn sẽ được áp dụng ở cấp gốc, cho bất kỳ phần tử có thể lựa chọn nào.

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">⚠️ Yêu cầu tiền tố để được hỗ trợ đầy đủ và không thực sự đúng trong tất cả trường hợp đặc biệt.</span>

* https://caniuse.com/#feat=css-selection

<!-- tags: visual -->

### Đổ bóng động

Tạo một bóng tối tương tự như `box-shadow` nhưng dựa trên màu sắc của chính phần tử đó.

#### HTML

```html
<div class="dynamic-shadow-parent">
  <div class="dynamic-shadow"></div>
</div>
```

#### CSS

```css
.dynamic-shadow-parent {
  position: relative;
  z-index: 1;
}
.dynamic-shadow {
  position: relative;
  width: 10rem;
  height: 10rem;
  background: linear-gradient(75deg, #6d78ff, #00ffb8);
}
.dynamic-shadow::after {
  content: '';
  width: 100%;
  height: 100%;
  position: absolute;
  background: inherit;
  top: 0.5rem;
  filter: blur(0.4rem);
  opacity: 0.7;
  z-index: -1;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__dynamic-shadow-parent">
    <div class="snippet-demo__dynamic-shadow"></div>
  </div>
</div>

<style>
.snippet-demo__dynamic-shadow-parent {
  position: relative;
  z-index: 1;
}
.snippet-demo__dynamic-shadow {
  position: relative;
  width: 10rem;
  height: 10rem;
  background: linear-gradient(75deg, #6d78ff, #00ffb8);
}
.snippet-demo__dynamic-shadow::after {
  content: '';
  position: absolute;
  width: 100%;
  height: 100%;
  background: inherit;
  top: 0.5rem;
  filter: blur(0.4rem);
  opacity: 0.7;
  z-index: -1;
}
</style>

#### Giải thích

Đoạn mã đòi hỏi một trường hợp phức tạp của ngữ cảnh xếp chồng lên để có được đúng, như vậy phần tử giả sẽ được đặt bên dưới chính nó trong khi vẫn hiển thị.

1. `position: relative` thiết lập một bối cảnh định vị trên phần tử cha cho phần tử con.
2. `z-index: 1` thiết lập một ngữ cảnh xếp chồng mới.
3. `position: relative` trên phần tử con thiết lập một bối cảnh định vị cho các phần tử giả.
4. `::after` đinh nghĩa một phần tử giả.
5. `position: absolute` lấy phần tử giả ra khỏi flow của tài liệu và định vị nó trong quan hệ với phần tử cha.
6. `width: 100%` và `height: 100%` kích thước các phần tử giả để lấp đầy kích thước phần tử cha, làm cho nó có kích thước bằng nhau.
7. `background: inherit` làm cho các phần tử giả kế thừa các quy định linear gradient trên phần tử.
8. `top: 0.5rem` độ lệch xuống của phần tử giả từ phần tử cha.
9. `filter: blur(0.4rem)` sẽ làm mờ phần tử giả tạo ra sự xuất hiện của một cái bóng bên dưới.
10. `opacity: 0.7` làm cho phần tử giả mang một phần trong suốt.
11. `z-index: -1` định vị phần tử giả phía sau phần tử cha.

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">⚠️ Yêu cầu tiền tố để được hỗ trợ đầy đủ.</span>

* https://caniuse.com/#feat=css-filters

<!-- tags: visual -->

### Văn bản nổi

Tạo ra một hiệu ứng mà văn bản xuất hiện được "khắc" hoặc khắc vào nền.

#### HTML

```html
<p class="etched-text">I appear etched into the background.</p>
```

#### CSS

```css
.etched-text {
  text-shadow: 0 2px white;
  font-size: 1.5rem;
  font-weight: bold;
  color: #b8bec5;
}
```

#### Demo

<div class="snippet-demo">
  <p class="snippet-demo__etched-text">I appear etched into the background.</p>
</div>

<style>
.snippet-demo__etched-text {
  font-size: 1.5rem;
  font-weight: bold;
  color: #b8bec5;
  text-shadow: 0 2px 0 white;
}
</style>

#### Giải thích

`text-shadow: 0 2px white` tạo một bóng trắng lệch `0px` theo phương dọc và `2px` theo phương ngang.

Nền phải tối hơn bóng để hiệu ứng có kết quả.

Màu văn bản nên hơi nhạt dần để làm cho nó trông giống như nó được khắc / khắc ra nền.

#### Hỗ trợ trình duyệt
<span class="snippet__support-note">✅ Không có gì.</span>

* https://caniuse.com/#feat=css-textshadow

<!-- tags: visual -->

### Văn bản gradient

Cho một văn bản gradient.

#### HTML

```html
<p class="gradient-text">Gradient text</p>
```

#### CSS

```css
.gradient-text {
  background: -webkit-linear-gradient(pink, red);
  -webkit-text-fill-color: transparent;
  -webkit-background-clip: text;
}
```

#### Demo

<div class="snippet-demo">
  <p class="snippet-demo__gradient-text">
    Gradient text
  </p>
</div>

<style>
.snippet-demo__gradient-text {
  background: -webkit-linear-gradient(pink, red);
  -webkit-text-fill-color: transparent;
  -webkit-background-clip: text;
  font-size: 2rem;
  font-weight: bold;
  margin: 0;
}
</style>

#### Giải thích

1. `background: -webkit-linear-gradient(...)` cung cấp cho các phần tử văn bản một nền gradient.
2. `webkit-text-fill-color: transparent` lấp đầy văn bản với màu trong suốt.
3. `webkit-background-clip: text` clips the background with the text, filling the text with
   the gradient background as the color.

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">⚠️ Sử dụng thuộc tính không chuẩn</span>

* https://caniuse.com/#feat=text-stroke

<!-- tags: visual -->

### ĐƯờng vằn

Cung cấp cho một phần tử một đường viền bằng 1 pixel, có thể trông rất sắc nét.

#### HTML

```html
<div class="hairline-border">text</div>
```

#### CSS

```css
.hairline-border {
  box-shadow: 0 0 0 1px;
}

@media (min-resolution: 2dppx) {
  .hairline-border {
    box-shadow: 0 0 0 0.5px;
  }
}

@media (min-resolution: 3dppx) {
  .hairline-border {
    box-shadow: 0 0 0 0.33333333px;
  }
}

@media (min-resolution: 4dppx) {
  .hairline-border {
    box-shadow: 0 0 0 0.25px;
  }
}
```

#### Demo

<div class="snippet-demo">
  <p class="snippet-demo__hairline-border">Text with a hairline border around it.</p>
</div>

<style>
.snippet-demo__hairline-border {
  box-shadow: 0 0 0 1px;
}

@media (min-resolution: 2dppx) {
  .snippet-demo__hairline-border {
    box-shadow: 0 0 0 0.5px;
  }
}

@media (min-resolution: 3dppx) {
  .snippet-demo__hairline-border {
    box-shadow: 0 0 0 0.33333333px;
  }
}

@media (min-resolution: 4dppx) {
  .snippet-demo__hairline-border {
    box-shadow: 0 0 0 0.25px;
  }
}
</style>

#### Giải thích

1. `box-shadow`, khi chỉ sử dụng spread, athêm một biên giả có thể sử sụng pixels âm\*.
2. Sử dụng `@media (min-resolution: ...)` để kiểm tra tỉ lệ thiết bị (`1dppx` bằng 96 DPI),
   cài đặt spread của `box-shadow` bằng `1 / dppx`.

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">⚠️ Needs alternate syntax and JavaScript user agent checking for full support.</span>

* https://caniuse.com/#feat=css-boxshadow
* https://caniuse.com/#feat=css-media-resolution

<hr>

\*Chrome không hỗ trợ các giá trị pixel âm trên `border`. Safari không hỗ trợ các giá trị pixel âm trên `box-shadow`. Firefox không hỗ trợ các giá trị pixel âm trên cả hai.

<!-- tags: visual -->

### cuộn tràn gradient

Thêm một gradient mờ dần cho một phần tử tràn để biểu thị tốt hơn có nhiều nội dung cần được cuộn lại.

#### HTML

```html
<div class="overflow-scroll-gradient">
  <div class="overflow-scroll-gradient__scroller">
    Content to be scrolled
  </div>
</div>
```

#### CSS

```css
.overflow-scroll-gradient {
  position: relative;
}
.overflow-scroll-gradient::after {
  content: '';
  position: absolute;
  bottom: 0;
  width: 240px;
  height: 25px;
  background: linear-gradient(
    rgba(255, 255, 255, 0.001),
    white
  ); /* transparent keyword is broken in Safari */
  pointer-events: none;
}
.overflow-scroll-gradient__scroller {
  overflow-y: scroll;
  background: white;
  width: 240px;
  height: 200px;
  padding: 15px 0;
  line-height: 1.2;
  text-align: center;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__overflow-scroll-gradient">
    <div class="snippet-demo__overflow-scroll-gradient__scroller">
      Content to be scrolled
    </div>
  </div>
</div>

<style>
.snippet-demo__overflow-scroll-gradient {
  position: relative;
}
.snippet-demo__overflow-scroll-gradient::after {
  content: '';
  background: linear-gradient(rgba(255, 255, 255, 0.001), white);
  position: absolute;
  width: 240px;
  height: 25px;
  bottom: 0;
  pointer-events: none;
}
.snippet-demo__overflow-scroll-gradient__scroller {
  overflow-y: scroll;
  background: white;
  width: 240px;
  height: 200px;
  padding: 15px 0;
  line-height: 1.2;
  text-align: center;
}
</style>

<script>
document.querySelector('.snippet-demo__overflow-scroll-gradient__scroller').innerHTML = 'content '.repeat(100)
</script>

#### Giải thích

1. `position: relative` trên phần tử con thiết lập một bối cảnh định vị cho các phần tử giả.
2. `::after` định nghĩa một phần tử giả.
3. `background-image: linear-gradient(...)` thêm một linear gradient mờ dần từ trong suốt đến trắng
   (từ trên xuống dưới).
4. `position: absolute` lấy phần tử giả ra khỏi flow của doc và định vị nó trong quan hệ với phần tử cha.
5. `width: 240px` trùng với kích thước của phần tử cuộn (là một phaatf tử con của phần tử cha có phần tử giả).??:D??
6. `height: 25px` là height của phần tử giả có gradient mờ dần, which should be kept relatively small.
7. `bottom: 0` định vị phần tử giả ở dưới cùng của phần tử cha.
8. `pointer-events: none` xác định rằng phần tử giả không thể là một đích của mouse event, cho phép văn bản đằng sau nó vẫn có thể được lựa chọn / tương tác

#### hỗ trợ trình duyệt

<span class="snippet__support-note">✅ Không có gì.</span>

* https://caniuse.com/#feat=css-gradients

<!-- tags: visual -->

### Gạch chân văn bản

Một sự thay thế đẹp hơn cho `text-decoration: underline` nơi mà các dấu chấm chấm không gạch dưới.
Được thực hiện như là `text-decoration-skip-ink: auto` nhưng khó kiểm soát hơn.

#### HTML

```html
<p class="pretty-text-underline">Pretty text underline without clipping descending letters.</p>
```

#### CSS

```css
.pretty-text-underline {
  font-family: Arial, sans-serif;
  display: inline;
  font-size: 18px;
  text-shadow: 1px 1px 0 #f5f6f9, -1px 1px 0 #f5f6f9, -1px -1px 0 #f5f6f9, 1px -1px 0 #f5f6f9;
  background-image: linear-gradient(90deg, currentColor 100%, transparent 100%);
  background-position: 0 0.98em;
  background-repeat: repeat-x;
  background-size: 1px 1px;
}
.pretty-text-underline::-moz-selection {
  background-color: rgba(0, 150, 255, 0.3);
  text-shadow: none;
}
.pretty-text-underline::selection {
  background-color: rgba(0, 150, 255, 0.3);
  text-shadow: none;
}
```

#### Demo

<div class="snippet-demo">
  <p class="snippet-demo__pretty-text-underline">Pretty text underline without clipping descending letters.</p>
</div>

<style>
.snippet-demo__pretty-text-underline {
  font-family: Arial, sans-serif;
  display: inline;
  font-size: 18px !important;
  text-shadow: 1px 1px 0 #f5f6f9,
    -1px 1px 0 #f5f6f9,
    -1px -1px 0 #f5f6f9,
    1px -1px 0 #f5f6f9;
  background-image: linear-gradient(90deg, currentColor 100%, transparent 100%);
  background-position: 0 0.98em;
  background-repeat: repeat-x;
  background-size: 1px 1px;
}

.snippet-demo__pretty-text-underline::-moz-selection {
  background-color: rgba(0, 150, 255, 0.3);
  text-shadow: none;
}

.snippet-demo__pretty-text-underline::selection {
  background-color: rgba(0, 150, 255, 0.3);
  text-shadow: none;
}
</style>

#### Giải thích

1. `text-shadow: ...` có 4 giá trị bù lại nó bao phủ một khu vực 4x4 để đảm bảo có một 'thick' shadow bao phủ dòng nơi mà kết thúc. Sử dụng một màu trùng với màu nền. Cho font chữ lớn, sử sụng `px` lớn.
2. `background-image: linear-gradient(...)` tạo một  gradient 90 độ so với màu chữ hiện tại(`currentColor`).
3. `background-*` các thuộc tính có kích thước gradient  1x1px ở phía dưới và lặp lại nó dọc theo trục x.
4. The `::selection` selector giả đảm bảo bóng văn bản không ảnh hưởng đến việc lựa chọn văn bản.

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">⚠️ The distance of the underline from the text depends on the internal metrics of a font, so you must ensure everyone sees the same font (i.e. no system fonts which will change based on the OS).</span>

* https://caniuse.com/#feat=css-textshadow
* https://caniuse.com/#feat=css-gradients

<!-- tags: visual -->

### Reset tất cả style

Đặt lại tất cả các style thành các giá trị mặc định với một thuộc tính.Cái này sẽ không ảnh hưởng đến thuộc tính `direction` và `unicode-bidi` .

#### HTML

```html
<div class="reset-all-styles">
  <h4>Title</h4>
  <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Iure id exercitationem nulla qui repellat laborum vitae, molestias tempora velit natus. Quas, assumenda nisi. Quisquam enim qui iure, consequatur velit sit?</p>
</div>
```

#### CSS

```css
.reset-all-styles {
  all: initial;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__reset-all-styles">
    <h3>Title</h3>
    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Iure id exercitationem nulla qui repellat laborum vitae, molestias tempora velit natus. Quas, assumenda nisi. Quisquam enim qui iure, consequatur velit sit?</p>
  </div>
</div>

<style>
.snippet-demo__reset-all-styles {
  all: initial;
}
</style>

#### Giải thích

Thuộc tính `all` cho phép bạn cài đặt lại tất cả các style (kế thừa hay không) thành giá trị mặc định.

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">⚠️ MS Edge status is under consideration.</span>

* https://caniuse.com/#feat=css-all

<!-- tags: visual -->

### Tách hình khối

Sử dụng một hình dạng SVG để tách hai khối khác nhau để tạo ra một hình ảnh thú vị hơn so với sự phân chia ngang bình thường.

#### HTML

```html
<div class="shape-separator"></div>
```

#### CSS

```css
.shape-separator {
  position: relative;
  height: 48px;
  background: #333;
}
.shape-separator::after {
  content: '';
  background-image: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgZmlsbC1ydWxlPSJldmVub2RkIiBjbGlwLXJ1bGU9ImV2ZW5vZGQiIHN0cm9rZS1saW5lam9pbj0icm91bmQiIHN0cm9rZS1taXRlcmxpbWl0PSIxLjQxNCI+PHBhdGggZD0iTTEyIDEybDEyIDEySDBsMTItMTJ6IiBmaWxsPSIjZmZmIi8+PC9zdmc+);
  position: absolute;
  width: 100%;
  height: 24px;
  bottom: 0;
}
```

#### Demo

<div class="snippet-demo is-distinct">
  <div class="snippet-demo__shape-separator"></div>
</div>

<style>
.snippet-demo__shape-separator {
  position: relative;
  height: 48px;
  margin: -0.75rem -1.25rem;
}
.snippet-demo__shape-separator::after {
  content: '';
  background-image: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgZmlsbC1ydWxlPSJldmVub2RkIiBjbGlwLXJ1bGU9ImV2ZW5vZGQiIHN0cm9rZS1saW5lam9pbj0icm91bmQiIHN0cm9rZS1taXRlcmxpbWl0PSIxLjQxNCI+PHBhdGggZD0iTTEyIDEybDEyIDEySDBsMTItMTJ6IiBmaWxsPSIjZmZmIi8+PC9zdmc+);
  position: absolute;
  width: 100%;
  height: 24px;
  bottom: 0;
}
</style>

#### Giải thích

1. `position: relative` trên phần tử con thiết lập một bối cảnh định vị cho các phần tử giả.
2. `::after` định nghĩa một phần tử giả.
3. `background-image: url(...)` thêm SVG shape (một tam giác 24x24 theo định dạng base64) như là ảnh nền của phần tử giả, cái mà mặc định là lặp lại. Nó phải cùng màu với khối được chia.
4. `position: absolute` lấy phần tử giả ra khỏi flow của doc và định vị nó trong quan hệ với phần tử cha.
5. `width: 100%` đảm bảo phần tử trải dài toàn bộ chiều rộng của phần tử cha.
6. `height: 24px` cùng chiều cao với shape.
7. `bottom: 0` định vị phần tử giả ở dưới cùng của phần tử cha.

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=svg

<!-- tags: visual -->

### Stack font hệ thống

ử dụng phông chữ bản địa của hệ điều hành để có được cảm nhận gần giống với ứng dụng gốc.

#### HTML

```html
<p class="system-font-stack">This text uses the system font.</p>
```

#### CSS

```css
.system-font-stack {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen-Sans, Ubuntu,
    Cantarell, 'Helvetica Neue', Helvetica, Arial, sans-serif;
}
```

#### Demo

<div class="snippet-demo">
  <p class="snippet-demo__system-font-stack">This text uses the system font.</p>
</div>

<style>
.snippet-demo__system-font-stack {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen-Sans, Ubuntu, Cantarell, "Helvetica Neue", Helvetica, Arial, sans-serif;
}
</style>

#### Giải thích

Trình duyệt tìm kiếm từng phông chữ, ưu tiên cái đầu tiên nếu khả thi, và quay trở lại font tiếp theo nếu nó không thể tìm thấy phông chữ (trên hệ thống hoặc được định nghĩa trong CSS).

1. `-apple-system` là San Francisco, được sử dụng trên iOS và macOS (  tuy nhiên không có trên Chrome)
2. `BlinkMacSystemFont` là San Francisco, được sử dụng trên macOS Chrome
3. `Segoe UI` được sử dụng trên Windows 10
4. `Roboto` được sử dụng trên Android
5. `Oxygen-Sans` được sử dụng trên GNU+Linux
6. `Ubuntu` được sử dụng trên Linux
7. `"Helvetica Neue"` và`Helvetica` được sử dụng trên macOS 10.10 và thấp hơn (được bao bọc bởi dấu ngoặc kép bởi vì nó có một khoảng trắng)
8. `Arial` là một phông chữ được hỗ trợ rộng rãi bởi tất cả các hệ điều hành
9. `sans-serif` là phông chữ dự phòng nếu không có phông chữ nào được hỗ trợ

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">✅ No caveats.</span>

<!-- tags: visual -->

### Tam giác

Tạo một tam giác với thuần CSS.

#### HTML

```html
<div class="triangle"></div>
```

#### CSS

```css
.triangle {
  width: 0;
  height: 0;
  border-top: 20px solid #333;
  border-left: 20px solid transparent;
  border-right: 20px solid transparent;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__triangles">
    <div class="snippet-demo__triangle snippet-demo__triangle-1"></div>
    <div class="snippet-demo__triangle snippet-demo__triangle-2"></div>
    <div class="snippet-demo__triangle snippet-demo__triangle-3"></div>
    <div class="snippet-demo__triangle snippet-demo__triangle-4"></div>
    <div class="snippet-demo__triangle snippet-demo__triangle-5"></div>
  </div>
</div>

<style>
.snippet-demo__triangles {
  display: flex;
  align-items: center;
}

.snippet-demo__triangle {
  display: inline-block;
  width: 0;
  height: 0;
  margin-right: 0.25rem;
}

.snippet-demo__triangle-1 {
  border-top: 20px solid #333;
  border-left: 20px solid transparent;
  border-right: 20px solid transparent;
}

.snippet-demo__triangle-2 {
  border-bottom: 20px solid #333;
  border-left: 20px solid transparent;
  border-right: 20px solid transparent;
}

.snippet-demo__triangle-3 {
  border-left: 20px solid #333;
  border-top: 20px solid transparent;
  border-bottom: 20px solid transparent;
}

.snippet-demo__triangle-4 {
  border-right: 20px solid #333;
  border-top: 20px solid transparent;
  border-bottom: 20px solid transparent;
}

.snippet-demo__triangle-5 {
  border-top: 40px solid #333;
  border-left: 15px solid transparent;
  border-right: 15px solid transparent;
}
</style>

#### Giải thích

[Xem link giải thích chi tiết.](https://stackoverflow.com/q/7073484)

Màu của đường viền là màu của tam giác. Đỉnh tam giác tương ứng với thuộc tính `border-*`. Ví dụ: màu trên đường biên giới hạn mũi tên xuống.

Thử với các giá trị px để thay đổi tỷ lệ tam giác.

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">✅ No caveats.</span>

<!-- tags: visual -->

### Bouncing loader

Tạo một chuyển động bouncing loader.

#### HTML

```html
<div class="bouncing-loader">
  <div></div>
  <div></div>
  <div></div>
</div>
```

#### CSS

```css
@keyframes bouncing-loader {
  from {
    opacity: 1;
    transform: translateY(0);
  }
  to {
    opacity: 0.1;
    transform: translateY(-1rem);
  }
}
.bouncing-loader {
  display: flex;
  justify-content: center;
}
.bouncing-loader > div {
  width: 1rem;
  height: 1rem;
  margin: 3rem 0.2rem;
  background: #8385aa;
  border-radius: 50%;
  animation: bouncing-loader 0.6s infinite alternate;
}
.bouncing-loader > div:nth-child(2) {
  animation-delay: 0.2s;
}
.bouncing-loader > div:nth-child(3) {
  animation-delay: 0.4s;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__bouncing-loader">
  	<div></div>
    <div></div>
    <div></div>
  </div>
</div>

<style>
@keyframes bouncing-loader {
  from {
    opacity: 1;
    transform: translateY(0);
  }
  to {
    opacity: 0.1;
    transform: translateY(-1rem);
  }
}
.snippet-demo__bouncing-loader {
  display: flex;
  justify-content: center;
}
.snippet-demo__bouncing-loader > div {
  width: 1rem;
  height: 1rem;
  margin: 3rem 0.2rem;
  background: #8385aa;
  border-radius: 50%;
  animation: bouncing-loader 0.6s infinite alternate;
}
.snippet-demo__bouncing-loader > div:nth-child(2) {
  animation-delay: 0.2s;
}
.snippet-demo__bouncing-loader > div:nth-child(3) {
  animation-delay: 0.4s;
}
</style>

#### Giải thích

Note: `1rem` thường là `16px`.

1. `@keyframes` định nghĩa một chuyển động có hai trạng thái, nơi phần tử thay đổi `opacity` và được dịch lên trên mặt phẳng 2D sử dụng `transform: translateY()`.

2. `.bouncing-loader` là container cha của bóng tròn và sử dụng  `display: flex`
   và  `justify-content: center` để đặt chúng ở giữa.

3. `.bouncing-loader > div`, nhắm tới 3 thẻ `div` con của phần tử cha được định kiểu. `div` được cho một chiều rộng và chiều cao là `1rem`, sử dụng  `border-radius: 50%` để bo tròn cạnh.

4. `margin: 3rem 0.2rem` xác định mỗi vòng tròn có margin top/bottom là  `3rem` và margin left/right 
   là  `0.2rem` để chúng không chạm vào nhau, cho chúng một khoảng trống.

5. `animation` là một thuộc tính viết tắt cho các thuộc tính animation khác nhau: `animation-name`, `animation-duration`, `animation-iteration-count`, `animation-direction` được sử dụng.

6. `nth-child(n)` nhắm mục tiêu đến phần tử thứ n của phần tử cha của nó.

7. `animation-delay` được sử dụng trên thẻ thứ 2 và 3 tương ứng  `div`, để mỗi phần tử không bắt đầu chuyển động cùng một lúc.

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=css-animation

<!-- tags: animation -->

### Donut spinner

Tạo một Donut spinner có thể được sử dụng để chỉ việc tải nội dung.

#### HTML

```html
<div class="donut"></div>
```

#### CSS

```css
@keyframes donut-spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
.donut {
  display: inline-block;
  border: 4px solid rgba(0, 0, 0, 0.1);
  border-left-color: #7983ff;
  border-radius: 50%;
  width: 30px;
  height: 30px;
  animation: donut-spin 1.2s linear infinite;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__donut-spinner"></div>
</div>

<style>
@keyframes snippet-demo__donut-spin {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg);}
}
.snippet-demo__donut-spinner {
  display: inline-block;
  border: 4px solid rgba(0, 0, 0, 0.1);
  border-left-color: #7983ff;
  border-radius: 50%;
  width: 30px;
  height: 30px;
  animation: snippet-demo__donut-spin 1.2s linear infinite;
}
</style>

#### Giải thích

Use a semi-transparent `border` cho toàn bộ phần tử, ngoại trừ một bên sẽ đóng vai trò như là chỉ số tải cho donut. Sử dụng `animation` để xuay phần tử.

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">⚠️ Yêu cầu tiền tố để được hỗ trợ đầy đủ.</span>

* https://caniuse.com/#feat=css-animation
* https://caniuse.com/#feat=transforms2d

<!-- tags: animation -->

### Biến giảm dần

Biến này được sử dụng cho thuộc tính `transition-timing-function`, mạnh hơn tích các hợp sẵn `ease`, `ease-in`, `ease-out` and `ease-in-out`.

#### HTML

```html
<div class="easing-variables"></div>
```

#### CSS

```css
:root {
  --ease-in-quad: cubic-bezier(0.55, 0.085, 0.68, 0.53);
  --ease-in-cubic: cubic-bezier(0.55, 0.055, 0.675, 0.19);
  --ease-in-quart: cubic-bezier(0.895, 0.03, 0.685, 0.22);
  --ease-in-quint: cubic-bezier(0.755, 0.05, 0.855, 0.06);
  --ease-in-expo: cubic-bezier(0.95, 0.05, 0.795, 0.035);
  --ease-in-circ: cubic-bezier(0.6, 0.04, 0.98, 0.335);

  --ease-out-quad: cubic-bezier(0.25, 0.46, 0.45, 0.94);
  --ease-out-cubic: cubic-bezier(0.215, 0.61, 0.355, 1);
  --ease-out-quart: cubic-bezier(0.165, 0.84, 0.44, 1);
  --ease-out-quint: cubic-bezier(0.23, 1, 0.32, 1);
  --ease-out-expo: cubic-bezier(0.19, 1, 0.22, 1);
  --ease-out-circ: cubic-bezier(0.075, 0.82, 0.165, 1);

  --ease-in-out-quad: cubic-bezier(0.455, 0.03, 0.515, 0.955);
  --ease-in-out-cubic: cubic-bezier(0.645, 0.045, 0.355, 1);
  --ease-in-out-quart: cubic-bezier(0.77, 0, 0.175, 1);
  --ease-in-out-quint: cubic-bezier(0.86, 0, 0.07, 1);
  --ease-in-out-expo: cubic-bezier(1, 0, 0, 1);
  --ease-in-out-circ: cubic-bezier(0.785, 0.135, 0.15, 0.86);
}

.easing-variables {
  width: 50px;
  height: 50px;
  background: #333;
  transition: transform 1s var(--ease-out-quart);
}

.easing-variables:hover {
  transform: rotate(45deg);
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__easing-variables">Hover</div>
</div>

<style>
:root {
  --ease-in-quad: cubic-bezier(0.55, 0.085, 0.68, 0.53);
  --ease-in-cubic: cubic-bezier(0.55, 0.055, 0.675, 0.19);
  --ease-in-quart: cubic-bezier(0.895, 0.03, 0.685, 0.22);
  --ease-in-quint: cubic-bezier(0.755, 0.05, 0.855, 0.06);
  --ease-in-expo: cubic-bezier(0.95, 0.05, 0.795, 0.035);
  --ease-in-circ: cubic-bezier(0.6, 0.04, 0.98, 0.335);

  --ease-out-quad: cubic-bezier(0.25, 0.46, 0.45, 0.94);
  --ease-out-cubic: cubic-bezier(0.215, 0.61, 0.355, 1);
  --ease-out-quart: cubic-bezier(0.165, 0.84, 0.44, 1);
  --ease-out-quint: cubic-bezier(0.23, 1, 0.32, 1);
  --ease-out-expo: cubic-bezier(0.19, 1, 0.22, 1);
  --ease-out-circ: cubic-bezier(0.075, 0.82, 0.165, 1);

  --ease-in-out-quad: cubic-bezier(0.455, 0.03, 0.515, 0.955);
  --ease-in-out-cubic: cubic-bezier(0.645, 0.045, 0.355, 1);
  --ease-in-out-quart: cubic-bezier(0.77, 0, 0.175, 1);
  --ease-in-out-quint: cubic-bezier(0.86, 0, 0.07, 1);
  --ease-in-out-expo: cubic-bezier(1, 0, 0, 1);
  --ease-in-out-circ: cubic-bezier(0.785, 0.135, 0.15, 0.86);
}

.snippet-demo__easing-variables {
  width: 75px;
  height: 75px;
  background: #333;
  color: white;
  font-size: 0.8rem;
  font-weight: bold;
  display: flex;
  justify-content: center;
  align-items: center;
  transition: transform 1s var(--ease-out-quart);
}

.snippet-demo__easing-variables:hover {
  transform: rotate(45deg);
}
</style>

#### Giải thích

The variables are defined globally within the `:root` CSS pseudo-class which matches the root element of a tree representing the document. In HTML, `:root` represents the `<html>` element and is identical to the selector `html`, except that its specificity is higher.

#### Browser support

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=css-variables

<!-- tags: animation -->

### Hover underline animation

Creates an animated underline effect when the text is hovered over.

<small>**Credit:** https://flatuicolors.com/</small>

#### HTML

```html
<p class="hover-underline-animation">Hover this text to see the effect!</p>
```

#### CSS

```css
.hover-underline-animation {
  display: inline-block;
  position: relative;
  color: #0087ca;
}
.hover-underline-animation::after {
  content: '';
  position: absolute;
  width: 100%;
  transform: scaleX(0);
  height: 2px;
  bottom: 0;
  left: 0;
  background-color: #0087ca;
  transform-origin: bottom right;
  transition: transform 0.25s ease-out;
}
.hover-underline-animation:hover::after {
  transform: scaleX(1);
  transform-origin: bottom left;
}
```

#### Demo

<div class="snippet-demo">
  <p class="snippet-demo__hover-underline-animation">Hover this text to see the effect!</p>
</div>

<style>
.snippet-demo__hover-underline-animation {
  display: inline-block;
  position: relative;
  color: #0087ca;
}
.snippet-demo__hover-underline-animation::after {
  content: '';
  position: absolute;
  width: 100%;
  transform: scaleX(0);
  height: 2px;
  bottom: 0;
  left: 0;
  background-color: #0087ca;
  transform-origin: bottom right;
  transition: transform 0.25s ease-out;
}
.snippet-demo__hover-underline-animation:hover::after {
  transform: scaleX(1);
  transform-origin: bottom left;
}
</style>

#### Explanation

1. `display: inline-block` makes the block `p` an `inline-block` to prevent the underline from
   spanning the entire parent width rather than just the content (text).
2. `position: relative` on the element establishes a Cartesian positioning context for pseudo-elements.
3. `::after` defines a pseudo-element.
4. `position: absolute` takes the pseudo element out of the flow of the document and positions it in relation to the parent.
5. `width: 100%` ensures the pseudo-element spans the entire width of the text block.
6. `transform: scaleX(0)` initially scales the pseudo element to 0 so it has no width and is not visible.
7. `bottom: 0` and `left: 0` position it to the bottom left of the block.
8. `transition: transform 0.25s ease-out` means changes to `transform` will be transitioned over 0.25 seconds
   with an `ease-out` timing function.
9. `transform-origin: bottom right` means the transform anchor point is positioned at the bottom right of the block.
10. `:hover::after` then uses `scaleX(1)` to transition the width to 100%, then changes the `transform-origin`
    to `bottom left` so that the anchor point is reversed, allowing it transition out in the other direction when
    hovered off.

#### Browser support

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=transforms2d
* https://caniuse.com/#feat=css-transitions

<!-- tags: animation -->

### Disable selection

Makes the content unselectable.

#### HTML

```html
<p>You can select me.</p>
<p class="unselectable">You can't select me!</p>
```

#### CSS

```css
.unselectable {
  user-select: none;
}
```

#### Demo

<div class="snippet-demo">
  <p>You can select me.</p>
  <p class="snippet-demo__disable-selection">You can't select me!</p>
</div>

<style>
.snippet-demo__disable-selection {
  user-select: none;
}
</style>

#### Explanation

`user-select: none` specifies that the text cannot be selected.

#### Browser support

<span class="snippet__support-note">⚠️ Requires prefixes for full support.</span>
<span class="snippet__support-note">⚠️ This is not a secure method to prevent users from copying content.</span>

* https://caniuse.com/#feat=user-select-none

<!-- tags: interactivity -->

### Mouse cursor gradient tracking

A hover effect where the gradient follows the mouse cursor.

<small class="snippet__credit">**Credit:** [Tobias Reich](https://codepen.io/electerious/pen/MQrRxX)</small>

#### HTML

```html
<button class="mouse-cursor-gradient-tracking">
  <span>Hover me</span>
</button>
```

#### CSS

```css
.mouse-cursor-gradient-tracking {
  position: relative;
  background: #7983ff;
  padding: 0.5rem 1rem;
  font-size: 1.2rem;
  border: none;
  color: white;
  cursor: pointer;
  outline: none;
  overflow: hidden;
}

.mouse-cursor-gradient-tracking span {
  position: relative;
}

.mouse-cursor-gradient-tracking::before {
  --size: 0;
  content: '';
  position: absolute;
  left: var(--x);
  top: var(--y);
  width: var(--size);
  height: var(--size);
  background: radial-gradient(circle closest-side, pink, transparent);
  transform: translate(-50%, -50%);
  transition: width 0.2s ease, height 0.2s ease;
}

.mouse-cursor-gradient-tracking:hover::before {
  --size: 200px;
}
```

#### JavaScript

```js
var btn = document.querySelector('.mouse-cursor-gradient-tracking')
btn.onmousemove = function(e) {
  var x = e.pageX - btn.offsetLeft
  var y = e.pageY - btn.offsetTop
  btn.style.setProperty('--x', x + 'px')
  btn.style.setProperty('--y', y + 'px')
}
```

#### Demo

<div class="snippet-demo">
  <button class="snippet-demo__mouse-cursor-gradient-tracking">
    <span>Hover me</span>
  </button>
</div>

<style>
.snippet-demo__mouse-cursor-gradient-tracking {
  position: relative;
  background: #7983ff;
  padding: 0.5rem 1rem;
  font-size: 1.2rem;
  border: none;
  color: white;
  cursor: pointer;
  outline: none;
  overflow: hidden;
}

.snippet-demo__mouse-cursor-gradient-tracking span {
  position: relative;
}

.snippet-demo__mouse-cursor-gradient-tracking::before {
  --size: 0;
  content: '';
  position: absolute;
  left: var(--x);
  top: var(--y);
  width: var(--size);
  height: var(--size);
  background: radial-gradient(circle closest-side, aqua, rgba(0,255,255,0.0001));
  transform: translate(-50%, -50%);
  transition: width .2s ease, height .2s ease;
}

.snippet-demo__mouse-cursor-gradient-tracking:hover::before {
  --size: 200px;
}
</style>

<script>
(function () {
  var btn = document.querySelector('.snippet-demo__mouse-cursor-gradient-tracking')
  btn.onmousemove = function (e) {
    var x = e.pageX - btn.offsetLeft - btn.offsetParent.offsetLeft
    var y = e.pageY - btn.offsetTop - btn.offsetParent.offsetTop
    btn.style.setProperty('--x', x + 'px')
    btn.style.setProperty('--y', y + 'px')
  }
})()
</script>

#### Explanation

_TODO_

**Note!**

If the element's parent has a positioning context (`position: relative`), you will need to subtract
its offsets as well.

```js
var x = e.pageX - btn.offsetLeft - btn.offsetParent.offsetLeft
var y = e.pageY - btn.offsetTop - btn.offsetParent.offsetTop
```

#### Browser support

<div class="snippet__requires-javascript">Requires JavaScript</div>
<span class="snippet__support-note">⚠️ Requires JavaScript.</span>

* https://caniuse.com/#feat=css-variables

<!-- tags: visual, interactivity -->

### Popout menu

Reveals an interactive popout menu on hover.

#### HTML

```html
<div class="reference">
  <div class="popout-menu">
    Popout menu
  </div>
</div>
```

#### CSS

```css
.reference {
  position: relative;
}
.popout-menu {
  position: absolute;
  visibility: hidden;
  left: 100%;
}
.reference:hover > .popout-menu {
  visibility: visible;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__reference">
    <div class="snippet-demo__popout-menu">
      Popout menu
    </div>
  </div>
</div>

<style>
.snippet-demo__reference {
  background: linear-gradient(135deg, #ff4c9f, #ff7b74);
  height: 75px;
  width: 75px;
  position: relative;
  will-change: transform;
}
.snippet-demo__popout-menu {
  position: absolute;
  visibility: hidden;
  left: 100%;
  background: #333;
  color: white;
  font-size: 0.9rem;
  padding: 0.4rem 0.8rem;
  width: 100px;
  text-align: center;
}
.snippet-demo__reference:hover > .snippet-demo__popout-menu {
  visibility: visible;
}
</style>

#### Explanation

1. `position: relative` on the reference parent establishes a Cartesian positioning context for its child.
2. `position: absolute` takes the popout menu out of the flow of the document and positions it
   in relation to the parent.
3. `left: 100%` moves the the popout menu 100% of its parent's width from the left.
4. `visibility: hidden` hides the popout menu initially and allows for transitions (unlike `display: none`).
5. `.reference:hover > .popout-menu` means that when `.reference` is hovered over, select immediate
   children with a class of `.popout-menu` and change their `visibility` to `visible`, which shows the popout.

#### Browser support

<span class="snippet__support-note">✅ No caveats.</span>

<!-- tags: interactivity -->

### Sibling fade

Fades out the siblings of a hovered item.

#### HTML

```html
<div class="sibling-fade">
  <span>Item 1</span>
  <span>Item 2</span>
  <span>Item 3</span>
  <span>Item 4</span>
  <span>Item 5</span>
  <span>Item 6</span>
</div>
```

#### CSS

```css
span {
  padding: 0 1rem;
  transition: opacity 0.2s;
}

.sibling-fade:hover span:not(:hover) {
  opacity: 0.5;
}
```

#### Demo

<div class="snippet-demo">
  <nav class="snippet-demo__sibling-fade">
    <span>Item 1</span>
    <span>Item 2</span>
    <span>Item 3</span>
    <span>Item 4</span>
    <span>Item 5</span>
    <span>Item 6</span>
  </nav>
</div>

<style>
.snippet-demo__sibling-fade {
  cursor: default;
  line-height: 2;
  vertical-align: middle;
}

.snippet-demo__sibling-fade span {
  padding: 1rem;
  transition: opacity 0.2s;
}

.snippet-demo__sibling-fade:hover span:not(:hover) {
  opacity: 0.5;
}
</style>

#### Explanation

1. `transition: opacity 0.2s` specifies that changes to opacity will be transitioned over 0.2 seconds.
2. `.sibling-fade:hover span:not(:hover)` specifies that when the parent is hovered, select any `span` children
   that are not currently being hovered and change their opacity to `0.5`.

#### Browser support

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=css-sel3
* https://caniuse.com/#feat=css-transitions

<!-- tags: interactivity -->

### Custom variables

CSS variables that contain specific values to be reused throughout a document.

#### HTML

```html
<p class="custom-variables">CSS is awesome!</p>
```

#### CSS

```css
:root {
  --some-color: #da7800;
  --some-keyword: italic;
  --some-size: 1.25em;
  --some-complex-value: 1px 1px 2px whitesmoke, 0 0 1em slategray, 0 0 0.2em slategray;
}

.custom-variables {
  color: var(--some-color);
  font-size: var(--some-size);
  font-style: var(--some-keyword);
  text-shadow: var(--some-complex-value);
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__custom-variables">
    <p>CSS is awesome!</p>
  </div>
</div>

<style>
.snippet-demo__custom-variables {
  --some-color: #686868;
  --some-keyword: italic;
  --some-size: 1.25em;
  --some-complex-value: 1px 1px 2px whitesmoke, 0 0 1em slategray , 0 0 0.2em slategray;
}

.snippet-demo__custom-variables p {
  color: var(--some-color);
  font-size: var(--some-size);
  font-style: var(--some-keyword);
  text-shadow: var(--some-complex-value);
}
</style>

#### Explanation

The variables are defined globally within the `:root` CSS pseudo-class which matches the root element of a tree representing the document. Variables can also be scoped to a selector if defined within the block.

Declare a variable with `--variable-name:`.

Reuse variables throughout the document using the `var(--variable-name)` function.

#### Browser support

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=css-variables

<!-- tags: other -->
