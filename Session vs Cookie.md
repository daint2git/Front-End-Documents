# Session vs Cookie

## Giống nhau

Session hay cookie đơn giản là những cách để chúng ta (các lập trình viên) lưu lại dữ liệu của người dùng sử dụng website.

## Khác nhau

### Session
- Là phiên làm việc để lưu trữ 1 biến và biến đó có thể tồn tại từ trang này đến trang khác(cùng tên miền)
- Session được lưu trữ trên server
- Thời gian sống của nó sẽ kết thúc khi ta xoá nó hoặc hết tuổi thọ (tắt trình duyệt)

### Cookies

- Cookies là 1 phần dữ liệu được lưu trên máy khách, mỗi khi máy khách yêu cầu đến máy chủ nào đó, thì nó sẽ gửi phần dữ liệu được lưu trong cookies tương ứng tới máy chủ đó
- Một cookies có độ lớn giới hạn bởi trình duyệt là 4kb
- Browsers giới hạn số cookies lưu trữ trên 1 server là khoảng 50 cookies

### Tóm tắt

| Thông tin | Session | Cookies |
|--------|--------|------|
| Vị trí lưu | lưu trên server | lưu trên trình duyệt của client |
| Bảo mật | lưu trên server nên bảo mật hơn | lưu dưới client nên kém bảo mật hơn |
| Giới hạn | lưu không giới hạn | lưu có giới hạn |
