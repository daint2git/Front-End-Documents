# Redux

## 3 nguyên tắc của Redux
- `Single source of truth`: Chỉ một `store` được đặt trong ứng dụng và trạng thái được lưu trữ trong `store` dưới dạng một `object`.
- `State is read-only`: Trạng thái không thể được thay trực tiếp, trạng thái chỉ có thể được thay đổi bằng cách gửi `action` đến `store`.
- `Mutations are written as pure functions`: Hàm thay đổi trạng thái (Reducer) là một `pure function`.
