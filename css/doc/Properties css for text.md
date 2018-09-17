# Properties css for text

## color
- Thuộc tính quy định màu sắc cho văn bản
```css
p { color: red; }

p { color: #f00; }

p { color: rgb(255,0,0); }
```

## font-size
- Thuộc tính quy định cỡ chữ cho văn bản
```css
p { font-size: 14px; }

p { font-size: large; }

p { font-size: 150%; }
```

## text-align
- Thuộc tính quy định căn chỉnh văn bản theo chiều ngang
```css
p{ text-algin: left; } 

p{ text-algin: center; } 

p{ text-algin: right; }

p{ text-algin: justify; }
```

## text-decoration
- Thuộc tính quy định trang trí được thêm vào cho văn bản
```css
p { text-decoration: overline; }

p { text-decoration: line-through; }

p { text-decoration: underline; }

p { text-decoration: underline overline; }
```
- Thuộc tính viết tắt cho:
  - text-decoration-line
  - text-decoration-color
  - text-decoration-style
  
## text-transformation
- Thuộc tính điều khiển chữ hoa và chữ thường trong văn bản
```css
p { text-transform: uppercase; }

p { text-transform: lowercase; }

p { text-transform: capitalize; }
```

## text-indent
- Thuộc tính quy định thụt dòng đầu tiên trong văn bản
```css
p { text-indent: 50px; }

p { text-indent: -2em; }

p { text-indent: 30%; }
```

## letter-spacing
- Thuộc tính quy định khoảng cách giữa các `kí tự` trong văn bản
```css
p { letter-spacing: 3px; }

p { letter-spacing: -3px; }
```
## line-height
- Thuộc tính quy định chiều cao của một dòng
```css
p { line-height: normal;}

p { line-height: 1.6; }

p { line-height: 80%; }

p { line-height: 200%; }
```

## direction
- Thuộc tính quy định hướng văn bản viết của một phần từ
```css
p { direction: rtl; }
```

## word-spacing
- Thuộc tính quy định khoảng cách giữa các `từ` trong văn bản
```css
p { word-spacing: 10px; }

p { word-spacing: -5px; }
```

## text-shadow
- Thuộc tính thêm bóng vào văn bản
```css
p { text-shadow: 2px 2px #f00; }
```

## white-space
- Thuộc tính quy định cách khoảng trắng bên trong phần tử xử lý như thế nào
```css
p { white-space: nowrap; }

p { white-space: pre; }

p { white-space: pre-line; }
```

## word-break
- Thuộc tính quy định cách các từ sẽ bị ngắt khi đến cuối dòng
```css
p { word-break: break-all; }

p { word-break: keep-all; }

p { word-break: break-word; }
```
- Các giá trị thường được sử dụng của thuộc tính
  - `word-break: break-all`: ngắt dòng theo `kí tự` khi văn bản bản vượt quá độ dài thẻ bao bọc nó
  - `word-break: keep-all`: ngắt dòng theo `từ` khi văn bản bản vượt quá độ dài thẻ bao bọc nó
  - `word-break: break-word`: ngắt dòng theo `từ` khi văn bản vượt quá độ dài thẻ bao bọc nó (nếu từ có độ dài vượt quá độ dài thẻ bao bọc nó thì sẽ tự động ngắt dòng)
- Note: `word-break` không nên sử dụng cho các ngôn ngữ Trung Quốc, Nhật Bản, Hàn Quốc
## word-wrap
- Thuộc tính quy định xuống dòng văn bản khi chuỗi kí tự có quá nhiều kí tự liền nhau (giống `word-break: break-word`)
```css
p { word-wrap: break-word; }
```
