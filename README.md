# Portfolio
# Hành trình chinh phục an ninh mạng - My Cybersecurity Journey

Xin chào, tôi là Tran Tien Cuong. Đây là nơi tôi ghi lại hành trình học tập và chuẩn bị cho sự nghiệp trong lĩnh vực An ninh mạng, với mục tiêu ứng tuyển vào chương trình StarCamp của NAB.
### **Nhật ký hành trình (Journey Log)**

* **20/06/2025: Security Principles**
    * Phân tích các khái niệm nền tảng về an ninh thông tin như CIA Triad, Zero Trust, và Defence in Depth.
    * **[Đọc bài phân tích chi tiết tại đây](./Writeups/Security-Principles-Writeup.md)**
### Ý tưởng & Suy ngẫm (Ideas & Reflections)
* **Nghiên cứu cách áp dụng các nguyên tắc kiến trúc bảo mật (ISO/IEC 19249) vào việc thiết kế workflow trên N8N/Dify, xem xét từng node như một 'miền' riêng biệt để giảm thiểu rủi ro.**

    * **Cụ thể hóa ý tưởng:** Khi thiết kế một workflow, hãy tự hỏi những câu sau:
    
    1.  **Tách biệt miền (Domain Separation):** Mỗi node trong workflow có phải là một "miền" không? Node xử lý thông tin nhạy cảm (ví dụ: API key, dữ liệu khách hàng) có cần được tách biệt và xử lý riêng biệt với các node chỉ xử lý dữ liệu công khai không?
        
    2.  **Đặc quyền tối thiểu (Least Privilege):** Credential (API key, password) được dùng trong một node N8N có được cấp quá nhiều quyền không? Nó chỉ nên có quyền thực hiện đúng một hành động cần thiết (ví dụ: chỉ đọc dữ liệu, hoặc chỉ ghi vào một bảng cụ thể) thay vì quyền admin đầy đủ.
        
    3.  **Đóng gói (Encapsulation):** Thay vì truyền trực tiếp một object dữ liệu lớn và nhạy cảm qua tất cả các node, có nên tạo một "sub-workflow" (workflow con) để xử lý riêng phần đó, và chỉ trả về kết quả cuối cùng không? Điều này giúp "đóng gói" và che giấu logic xử lý nhạy cảm.
        
    4.  **Giảm thiểu bề mặt tấn công (Attack Surface Minimisation):** Workflow của mình có tiếp xúc với các trigger không cần thiết từ bên ngoài không (ví dụ: Webhook)? Có nên giới hạn webhook trigger chỉ chấp nhận request từ những địa chỉ IP cụ thể không?
