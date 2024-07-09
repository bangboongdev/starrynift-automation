Dưới đây là bản dịch tiếng Việt của mô tả và hướng dẫn cho dự án Starrynift Automation của bạn:

## Starrynift Automation

### Mô tả
### Mã này có các chức năng sau:

- **Đăng nhập** - Đăng nhập vào Starrynift bằng HTTP proxy và private key. Nhận access_token và lưu thông tin tài khoản (private_key, proxy, access_token, user_agent) vào ./data/accounts.txt.
- **Citizen Card mint** - Tạo **Citizen Card NFT** nếu địa chỉ chưa từng tạo NFT này trước đó. Cần thực hiện **Đăng nhập** trước để tạo tài khoản.
- **Daily Check in** - Check in hàng ngày. Gửi giao dịch và xác minh hash.
- **Online Ping** - Hoàn thành nhiệm vụ "Ở trực tuyến 10 phút". Gửi yêu cầu mỗi ~30 giây trên mỗi tài khoản cho đến khi đủ 10 phút. **Completed: True nếu nhiệm vụ hoàn thành thành công**.
- **Follow profile** - Theo dõi **ID** của tài khoản được chỉ định trong **./config.py**.
- **Check profile info** - Hiển thị **Level & Points** cho mỗi tài khoản.

### Cấu trúc

- `./data/keys.txt`: Nơi để tải lên private key với số dư BNB cần thiết để thanh toán phí giao dịch.
- `./data/proxies.txt`: Nơi để tải lên HTTP proxy trong định dạng http://login:pass@ip:port
- `./data/accounts.txt`: Sau khi chạy chức năng **Đăng nhập**, thông tin tài khoản được ghi vào đây với định dạng {private_key, valid_until, proxies, access_token, user_agent}
- `./data/fail_logs.txt`: Ghi nhật ký các hành động thất bại trong kịch bản.
- `./utils/requests_utils.py`: Các hàm liên quan đến **requests**.
- `./utils/starrynift_utils.py`: Các hàm liên quan đến giao dịch & yêu cầu trên **Starrynift**.
- `./utils/web3_utils.py`: Các hàm liên quan đến **web3.py**.
- `./utils/utils.py`: Các hàm hỗ trợ khác.
- `./config.py`: Tập tin cấu hình để tinh chỉnh các giá trị làm việc cá nhân.
- `./main.py`: Tệp chính để chạy.

### Cài đặt và Chạy

1. Clone repository:

    ```bash
    git clone https://github.com/Nomzegh/starrynift-automation.git
    ```

2. Cài đặt các thư viện cần thiết:

    ```bash
    pip install requests
    pip install web3
    ```

3. Thay đổi hoặc giữ nguyên các giá trị trong `config.py`.

4. Tải lên `keys.txt` với private key có số dư BNB để thanh toán phí gas.

5. Chạy lệnh sau:

    ```bash
    python main.py
    ```

6. Để các chức năng khác hoạt động đúng cách, cần chạy chức năng `Đăng nhập` trước, sẽ tạo và lưu thông tin tài khoản (token và các thông tin khác) vào `./data/accounts.txt`.

### Ghi chú
- Không cần phải đăng nhập lại mỗi lần - tệp `./data/accounts.txt` chỉ ra thời gian hiệu lực của token (`valid_until`).
- Đảm bảo rằng có số dư BNB cần thiết trên các ví của bạn.
- Chắc chắn điều chỉnh các giá trị trong `config.py` để phù hợp với nhu cầu làm việc cá nhân.

