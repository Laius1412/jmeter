# Kiểm thử JMeter
# Tên dự án: Kiểm định hiệu suất web vexere.com
# Người kiểm thử: Cao Mậu Thành Đạt
# Ngày kiểm thử: 26/06/2025

# 1. Mục tiêu kiểm thử

- Sử dụng JMeter để kiểm thử hiệu suất cho trang chủ trang web vexere.com

# 2. Các bước kiểm thử

-	Bước 1: Cài đặt JMeter và giải nén tập tin vừa tải.
-	Bước 2: Chạy Jmeter bằng file jmeter.bat trong thư mục bin.
-	Bước 3: Tạo kế hoạch kiểm thử.
-	Bước 4: Thực hiện kiểm thử.
-	Bước 5: Phân tích kết quả.

# 3. Kịch bản kiểm thử

## Thiết lập Thread Group

![image](https://github.com/user-attachments/assets/08b6ad20-8344-49f8-9304-3bebd4b231c8)

Cấu hình của thread group:
-	Number of Threads: Số lượng người dùng ảo được gửi vào trang web.
-	Ranp-up period: Thời gian gửi lượng users vào trang web.
-	Loop Count: Số lần lặp.

## Thiết lập homepage test

![image](https://github.com/user-attachments/assets/173a2a2f-b33a-48fc-abe3-93d756d810b2)

-	Protocol: https.
-	Server Name or IP: vexere.com.
-	HTTP Request: GET.
-	Path: /


## Thêm các listener để xem kết quả:

### View Results Tree:

![image](https://github.com/user-attachments/assets/a2f1e8ec-57a7-4fb0-8d46-a58998102d20)

Qua việc phân tích kết quả View Results Tree, nhận thấy trang web vexere.com không gặp lỗi hoặc ít lỗi khi số lượng truy cập dưới 300 người dùng, khi số lượng người dùng vượt mức 300 số lỗi sẽ xảy ra nhiều hơn.

### Summary Report:

![image](https://github.com/user-attachments/assets/04976f97-4696-4625-89a8-f959389b00d3)

| Cột | Ý nghĩa | Dữ liệu bạn nhận được |
|---|---|---|
| **Samples** | Tổng số request gửi đi | 1800 |
| **Average** | Thời gian phản hồi trung bình (ms) | 2552 ms (~2.5 giây) |
| **Min** | Thời gian phản hồi nhanh nhất | 220 ms |
| **Max** | Thời gian phản hồi chậm nhất | 21059 ms (~21 giây) |
| **Std. Dev.** | Độ lệch chuẩn (biến động thời gian phản hồi) | 2723 ms – khá cao |
| **Error %** | Tỷ lệ lỗi request | 14.33% (≈ 258 request bị lỗi) |
| **Throughput** | Số lượng request xử lý mỗi giây | 6.0/sec |
| **Received KB/sec** | Băng thông nhận từ server | 2201.24 KB/giây |
| **Sent KB/sec** | Băng thông gửi lên server | 0.65 KB/giây |
| **Avg. Bytes** | Dung lượng trung bình mỗi phản hồi | ~376 KB |

