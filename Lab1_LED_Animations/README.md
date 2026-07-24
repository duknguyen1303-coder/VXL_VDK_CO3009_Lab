# Lab 1: LED Animations

Nguồn: HCMUT - Computer Engineering, môn Microcontroller
Chip sử dụng: STM32F103C8T6 (đề gốc dùng C6, board thật dùng C8 - tương thích chân-đối-chân)

## Exercise 1
LED-YELLOW nối PA6 (cực âm), thêm vào bên cạnh LED-RED (PA5) đã có sẵn.
Yêu cầu: 2 LED đổi trạng thái luân phiên mỗi 2 giây (RED ON/YELLOW OFF <-> RED OFF/YELLOW ON).

- Report 1: Vẽ sơ đồ mạch Proteus, caption là link tải file .pdsprj (VD: link GitHub).
- Report 2: Code trong vòng lặp while(1).

## Exercise 2
Mở rộng Exercise 1 thành đèn giao thông. Thêm LED-GREEN nối PA7 (cực âm).
Chu kỳ: RED 5s -> YELLOW 2s -> GREEN 3s -> lặp lại.

- Report 1: Sơ đồ mạch.
- Report 2: Code trong while.

## Exercise 3
Mở rộng thành đèn giao thông 4 hướng (4-way traffic light).
Sắp xếp 12 LED (4 đỏ, 4 vàng, 4 xanh) theo hình dạng hợp lý, tham khảo mẫu trong đề.

- Report 1: Sơ đồ mạch.

## Exercise 4
Thêm 1 LED 7 đoạn vào mạch Exercise 3.
Linh kiện: 7SEG-COM-ANODE (tìm trong Proteus theo từ khóa này).
Chân chung (common) nối nguồn (+3.3V), các chân còn lại nối PB0 - PB6.
Lưu ý: vì là COM-ANODE nên để sáng 1 đoạn, chân STM32 tương ứng phải ở mức logic 0 (0V).

Yêu cầu: viết hàm display7SEG(int num) - input 0-9, hiển thị đúng số trên 7 đoạn.
Test bằng đoạn code đếm từ 0-9 lặp lại, mỗi số delay 1 giây:

    int counter = 0;
    while (1) {
        if (counter >= 10) counter = 0;
        display7SEG(counter++);
        HAL_Delay(1000);
    }

- Report 1: Sơ đồ mạch.
- Report 2: Code hàm display7SEG.

## Exercise 5
Tích hợp 7SEG-LED vào mạch đèn giao thông 4 hướng (Exercise 3).
7SEG dùng để hiển thị giá trị đếm ngược (countdown) thời gian còn lại của đèn.
Có thể tái sử dụng hàm display7SEG từ Exercise 4.

- Chỉ cần nộp source code, không cần vẽ lại sơ đồ mạch mới.

## Exercise 6
Thiết kế mạch Proteus mới: đồng hồ analog, 12 số (12 LED).
Các LED nối từ PA4 đến PA15 của STM32.
Sắp xếp 12 LED theo đúng vị trí số trên mặt đồng hồ (tham khảo hình trong đề).

- Report 1: Sơ đồ mạch.
- Report 2: Viết chương trình test kết nối - lần lượt bật từng LED theo thứ tự để kiểm tra dây nối đúng chưa.

## Exercise 7
Viết hàm clearAllClock() - tắt toàn bộ 12 LED của đồng hồ (Exercise 6).

    void clearAllClock() {
        // TODO
    }

- Chỉ cần nộp source code hàm này.

## Exercise 8
Viết hàm setNumberOnClock(int num) - input từ 0 đến 11, bật đúng LED tương ứng vị trí số đó trên mặt đồng hồ.

- Chỉ cần nộp source code hàm này.

## Exercise 9
Viết hàm clearNumberOnClock(int num) - input từ 0 đến 11, tắt đúng LED tương ứng vị trí số đó.

- Chỉ cần nộp source code hàm này.

## Exercise 10
Tích hợp toàn bộ hệ thống: dùng 12 LED để hiển thị đồng hồ thời gian thực.
Tại 1 thời điểm, chỉ có đúng 3 LED sáng, tương ứng với giờ - phút - giây hiện tại.
Sử dụng lại các hàm: clearAllClock, setNumberOnClock, clearNumberOnClock từ Exercise 7-9.

- Nộp toàn bộ source code hệ thống hoàn chỉnh.
