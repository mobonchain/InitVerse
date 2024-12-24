
# Hướng Dẫn Chạy Node Mining Pool trên Linux (Testnet InitVerse)

Chào mừng bạn đến với hướng dẫn chạy Node Mining Pool trên hệ điều hành Linux (Ubuntu). Nếu bạn muốn chạy Mining Pool trên **Windows** hoặc Mining Solo, vui lòng truy cập [Mining | InitVerse](https://inichain.gitbook.io/initverseinichain/inichain/mining#mining-pool-setup).

---

## Thông Tin Về Cấu Hình

Để tối ưu hiệu suất khi chạy Node Mining Pool, cấu hình máy tính càng mạnh càng tốt. CPU càng nhiều nhân và có hiệu suất mạnh sẽ giúp quá trình đào nhanh chóng và ổn định hơn.

**Lưu ý:** Máy tính với cấu hình mạnh sẽ giúp tăng hiệu quả đào và giảm thiểu khả năng gián đoạn khi tham gia vào mining pool.

---

## Thiết Lập Chạy Tool

### Bước 1: Cài Đặt `iniminer-linux-x64`

Để bắt đầu, bạn cần tải về tool mining của InitVerse và cấp quyền thực thi cho tệp:

1. Tải `iniminer-linux-x64` bằng lệnh:

   ```bash
   wget https://github.com/Project-InitVerse/ini-miner/releases/download/v1.0.0/iniminer-linux-x64
   ```

   **Giải thích:** Lệnh `wget` sẽ tải tệp thực thi của miner từ GitHub về hệ thống của bạn.

2. Cấp quyền thực thi cho tệp tải về:

   ```bash
   chmod +x iniminer-linux-x64
   ```

   **Giải thích:** Lệnh `chmod +x` sẽ giúp tệp `iniminer-linux-x64` có quyền thực thi, giúp bạn có thể chạy nó.

---

### Bước 2: Chạy Miner Trên `screen`

Để chạy mining trong một phiên `screen`, bạn cần tạo một phiên `screen` và chạy lệnh miner trong đó.

1. Mở một phiên `screen` mới:

   ```bash
   screen -S initverse
   ```

   **Giải thích:** Lệnh này sẽ mở một phiên `screen` mới với tên `initverse`, cho phép bạn tiếp tục chạy chương trình ngay cả khi ngắt kết nối SSH.

2. Chạy miner với lệnh sau:

   ```bash
   ./iniminer-linux-x64 --pool stratum+tcp://Your_Wallet_Address.Worker001@pool-core-testnet.inichain.com:32672
   ```

   **Giải thích:** Lệnh này khởi động miner và khởi chạy tất cả **CPU Cores** để kết nối đến testnet mining pool của InitVerse nếu muốn chỉ định lại CPU thì kéo xuống cùng xem hướng dẫn. Bạn cần thay `Your_Wallet_Address` bằng địa chỉ ví của bạn và **có thể** thay đổi `Worker001` thành tên worker của bạn nếu cần thiết.

---

### Bước 3: Thoát khỏi phiên

Khi bạn chạy lệnh trong `screen`, bạn có thể ngắt kết nối mà không ảnh hưởng đến quá trình mining bằng cách sử dụng:

- **`Ctrl + A`**: Chế độ điều khiển của `screen`.
- **`D`**: Để thoát khỏi phiên `screen` mà không dừng chương trình.

Sau khi nhấn `Ctrl + A` và `D`, bạn có thể ngắt kết nối SSH, nhưng mining vẫn tiếp tục chạy ở phía sau. Để quay lại phiên `screen`:

```bash
screen -r initverse
```

---

### Kiểm Tra Trạng Thái Node

Để kiểm tra tình trạng node của bạn, bạn có thể truy cập vào trang [https://genesis-testnet.yatespool.com](https://genesis-testnet.yatespool.com). Nhập địa chỉ ví của bạn vào ô tìm kiếm để kiểm tra tiến độ đào.

---

### Chạy Với CPU Được Chỉ Định

Nếu bạn muốn chỉ định các CPU cụ thể để đào, bạn có thể sử dụng tùy chọn `--cpu-devices`. Ví dụ, nếu bạn muốn chỉ định các CPU 0 và 1, bạn có thể chạy lệnh sau:

```bash
./iniminer-linux-x64 --pool stratum+tcp://Your_Wallet_Address.Worker001@pool-core-testnet.inichain.com:32672 --cpu-devices 0 --cpu-devices 1
```

---

**Nhóm [TopAME | Chat - Supports](https://t.me/yTopAME)**
