# Redux

## Redux được thiết kế dựa trên ba nguyên tắc
- `Single source of truth`: Chỉ một `store` được đặt trong ứng dụng và trạng thái được lưu trữ trong `store` dưới dạng một `object`.
- `State is read-only`: Không thể thay đổi trạng thái trực tiếp, trạng thái chỉ có thể được thay đổi bằng cách `dispatch` `action` đến `store`.
- `Mutations are written as pure functions`: Hàm thay đổi trạng thái (Reducer) là một `pure function`.

## Các yếu tố của Redux
- Action
- ActionCreator
- Store
- State
- Reducer
