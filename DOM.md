# DOM

- Mô hình Đối tượng Tài liệu (Document Object Model)
- Được định nghĩa là một giao diện lập trình ứng dụng (API) được dùng để truy xuất các tài liệu dạng `HTML` và `XML`, có dạng một cây cấu trúc dữ liệu
- DOM quy định cấu trúc của văn bản `HTML` và `XML` qua đó giúp lập trình viên có thể dễ quản lý nó

## DOM và JS

- Trong JS để thao tác được với các thẻ HTML ta phải thông qua đối tượng document (DOM)
- Với DOM, JS được tất cả sức mạnh cần thiết để tạo ra HTML động:
  - JS có thể thay đổi tất cả các phần tử HTML trong trang
  - JS có thể thay đổi tất cả các thuộc tính HTML trong trang
  - JS có thể thay đổi tất cả các phong cách CSS trong trang
  - JS có thể loại bỏ các yếu tố HTML và thuộc tính hiện tại
  - JS có thể thêm các yếu tố HTML mới và các thuộc tính
  - JS có thể phản ứng với tất cả các sự kiện HTML hiện trong trang
  - JS có thể tạo ra các sự kiện HTML mới trong trang
  
## HTML DOM là gì ?
  
- Là một chuẩn mô hình object và programming interface cho HTML. nó định nghĩa:
  - HTML elements như là objects
  - properties của tất cả HTML elements
  - methods để truy cập đến tất cả HTML elements
  - events cho tất cả HTML elements
    
- Là một tiêu chuẩn cho phép bạn thực hiện những công việc thao tác với bất kì một trang web: get, change, add, or delete các thành phần của HTML

## Attribute và Property
- `Attribute` là thuộc tính các phần tử DOM
- `Property` là thuộc tính của đối tượng JS

> **Một vài chú ý nhỏ**
> - `Attribute` của DOM element và `Property` của JS object tương ứng thì không có quan hệ 1 - 1. Chẳng hạn như attribute `class` được ánh xạ thành property `className` và attribute `for` được ánh xạ thành `htmlFor`
> - Dùng phương thức `getAttribute(name)` và `setAttribute(name, value)` để thao tác với attribute. Để thao tác với property dùng dot notation (element.property = value)
> - Attribute `value` của phần tử `<input type="text" value="type to search"/>` chính vì vậy thay đổi property không chắc chắn làm thay đổi attribute và ngược lại
