# [TryHackMe Write-up] Phân tích Room: Security Principles

* **Tác giả:** Trần Tiến Cường
* **Ngày hoàn thành:** 20/06/2025
* **Link Room:** [Security Principles on TryHackMe](https://tryhackme.com/room/securityprinciples)
![image](https://github.com/user-attachments/assets/e88a0792-3f0b-4534-940c-895adf52be88)


---

### **1. Tổng quan (Overview)**

Bài viết này là bản phân tích chi tiết các kiến thức thu được từ room "Security Principles" trên nền tảng TryHackMe. Nội dung bao quát từ các khái niệm rủi ro cơ bản, bộ ba CIA, các triết lý phòng thủ hiện đại cho đến các mô hình kiểm soát truy cập và kiến trúc bảo mật.

---

### **2. Các khái niệm và mô hình chính**

Dưới đây là tổng hợp các nguyên tắc và mô hình mà tôi cho là quan trọng nhất sau khi hoàn thành room:

#### **2.1. Nền tảng Rủi ro: Lỗ hổng, Mối đe dọa, Rủi ro**
* **Lỗ hổng (Vulnerability):** Một điểm yếu trong hệ thống.
* **Mối đe dọa (Threat):** Một nguy hiểm tiềm tàng có thể khai thác lỗ hổng.
* **Rủi ro (Risk):** Khả năng mối đe dọa khai thác lỗ hổng và gây ra tác động.

#### **2.2. Trụ cột An ninh: Bộ ba CIA (Confidentiality, Integrity, Availability)**
* **Confidentiality (Tính bảo mật):** Bảo vệ dữ liệu khỏi truy cập trái phép.
* **Integrity (Tính toàn vẹn):** Bảo vệ dữ liệu khỏi sự thay đổi trái phép.
* **Availability (Tính sẵn sàng):** Đảm bảo hệ thống và dữ liệu luôn có thể truy cập khi cần.

#### **2.3. Phản đề của CIA: Tam giác DAD (Disclosure, Alteration, Destruction/Denial)**
* **Disclosure (Tiết lộ):** Đối lập với Confidentiality.
* **Alteration (Thay đổi):** Đối lập với Integrity.
* **Destruction/Denial (Phá hủy/Từ chối):** Đối lập với Availability.

#### **2.4. Mở rộng ngoài CIA: Xác thực & Không chối bỏ**
* **Authenticity (Tính xác thực):** Đảm bảo dữ liệu đến từ nguồn đã được xác nhận.
* **Non-repudiation (Không thể chối bỏ):** Đảm bảo nguồn gốc không thể phủ nhận hành động đã thực hiện.

#### **2.5. Khung Parkerian Hexad**
Mô hình này mở rộng CIA bằng cách thêm 3 yếu tố: **Utility (Tính hữu ích)**, **Possession (Quyền sở hữu)**, và **Authenticity (Tính xác thực)**. Nó cung cấp một cái nhìn toàn diện hơn về các thuộc tính cần được bảo vệ.

#### **2.6. Triết lý phòng thủ: Zero Trust vs. Trust but Verify**
* **Trust but Verify:** Tin tưởng ban đầu, nhưng vẫn xác minh.
* **Zero Trust:** Một triết lý hiện đại và mạnh mẽ hơn, hoạt động theo nguyên tắc "không bao giờ tin, luôn luôn xác minh". Mọi truy cập đều phải được xác thực và cấp quyền chặt chẽ.

#### **2.7. Chiến lược thực thi: Phòng thủ đa tầng (Defence in Depth)**
Xây dựng nhiều lớp bảo vệ chồng chéo để nếu một lớp bị vượt qua, các lớp khác vẫn có thể ngăn chặn hoặc làm chậm cuộc tấn công.

#### **2.8. Nguyên tắc kiến trúc bảo mật (ISO/IEC 19249:2017)**
Các nguyên tắc thiết kế như **Tách biệt miền (Domain Separation)**, **Phân lớp (Layering)**, **Đóng gói (Encapsulation)**, **Dự phòng (Redundancy)**, và **Ảo hóa (Virtualization)** giúp xây dựng một hệ thống vững chắc từ nền tảng.

#### **2.9. Các mô hình kiểm soát truy cập**
* **Bell-LaPadula:** Tập trung vào Tính bảo mật (Confidentiality) với quy tắc "no read up, no write down".
* **Biba:** Tập trung vào Tính toàn vẹn (Integrity) với quy tắc "no read down, no write up".
* **Clark-Wilson:** Cũng tập trung vào Tính toàn vẹn bằng cách kiểm soát chặt chẽ các quy trình sửa đổi dữ liệu.

---

### **3. Phân tích & Vận dụng cá nhân**

Kiến thức lý thuyết trên có thể được áp dụng trực tiếp để phân tích các hệ thống thực tế. Trong đồ án tốt nghiệp của tôi, việc xây dựng một hệ thống mạng ảo với nhiều thành phần chính là một ví dụ về nguyên tắc **Phòng thủ đa tầng**:

* **Lớp 1 (Firewall):** Tôi đã cấu hình pfSense để tạo một vành đai bảo vệ bên ngoài, lọc các truy cập không mong muốn. Đây là việc thực thi nguyên tắc **Tách biệt miền (Domain Separation)**.
* **Lớp 2 (IDS):** Bên trong mạng, tôi triển khai Snort/Suricata để giám sát và phát hiện các hành vi bất thường đã lọt qua được lớp firewall. Đây là một lớp bảo vệ bổ sung, giúp đảm bảo **Tính toàn vẹn (Integrity)** cho các máy chủ bên trong.

Việc này cho thấy, một hệ thống an toàn không phải là một sản phẩm, mà là một quá trình kết hợp nhiều nguyên tắc và công nghệ khác nhau.

### **4. Kết luận**

Hoàn thành room này đã cho tôi một bộ khung tư duy vững chắc để tiếp cận các vấn đề an ninh mạng. Thay vì chỉ nhìn vào các công cụ riêng lẻ, giờ đây tôi có thể đánh giá chúng dựa trên các nguyên tắc và triết lý bảo mật mà chúng phục vụ.
