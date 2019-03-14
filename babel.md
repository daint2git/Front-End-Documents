# Babel

Babel is a JavaScript compiler

## loose mode

http://2ality.com/2015/12/babel6-loose-mode.html

Babel’s loose mode transpiles ES6 code to ES5 code that is less faithful to ES6 semantics.

## 2 chế độ

Nhiều `plugin` trong `Babel` có 2 chế độ:
- Một chế độ bình thường tuân theo ngữ nghĩa của ECMAScript 6 càng sát càng tốt.
- Một chế độ lỏng lẻo (loose) tạo ra mã ES5 đơn giản hơn.

Thông thường, không nên sử dụng `loose` mode. Những ưu và nhược điểm là:
- Ưu: Mã được tạo ra có khả năng nhanh hơn và tương thích hơn với older engines. Nó cũng có xu hướng rõ ràng hơn, nhiều hơn `ES5-style`.
- Nhược: Có nguy cơ gặp các vấn đề sau, khi bạn chuyển đổi từ `transpiled ES6` sang `native ES6`. Điều đó hiếm khi là một rủi ro đáng giá.

## Presets

Tập hợp một số `@babel/plugin-*`

### Preset ordering
Thứ tự preset được đảo ngược (last to first).
```js
// .babelrc
{
  "presets": [
    "a",
    "b",
    "c"
  ]
}
```
Sẽ chạy theo thứ tự sau: c → b → a.
(Điều này chủ yếu là để đảm bảo khả năng tương thích ngược, vì hầu hết chúng ta chỉ định `@babel/preset-env` trước các preset khác).

### Preset options
Để chỉ định một tùy chọn, truyền một đối tượng với các `key` như tên tùy chọn.
```js
// .babelrc
{
  "presets": [
    ["@babel/preset-env", {
      "loose": true,
      "modules": false
    }]
  ]
}
```

## Plugins

Babel is a compiler (source code => output code).
Like many other compilers it runs in 3 stages:
- parsing.
- transforming.
- printing.

Về cơ bản nó hoạt động như `const babel = code => code;` bằng cách phân tích mã và sau đó tạo lại cùng một mã. Bạn sẽ cần thêm `plugins` cho Babel để làm bất cứ điều gì.

### Transform Plugins

Các plugin này áp dụng các phép biến đổi cho mã của bạn.

## Plugin Ordering

Các biến đổi sẽ chạy theo thứ tự `plugin` hoặc `preset`.
- Plugins run before Presets.
- Plugin ordering is first to last.
- Preset ordering is reversed (last to first).

## Plugin Options

Tương tự `preset`
