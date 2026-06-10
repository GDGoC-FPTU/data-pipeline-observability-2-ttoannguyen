# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** AI20K-1234
**Name:** Toan Nguyen
**Date:** 2026-06-10

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Agent: Based on my data, the best choice is Laptop at $1200. | 9/10 | The response is accurate and the data is properly cleaned and formatted. |
| Garbage Data (`garbage_data.csv`) | Agent: Based on my data, the best choice is Nuclear Reactor at $999999. | 2/10 | The agent recommended an outlier (Nuclear Reactor) with a highly unrealistic price. |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Khi sử dụng dữ liệu rác (Garbage Data), Agent đưa ra các câu trả lời không chính xác và thiếu độ tin cậy do gặp phải các vấn đề nghiêm trọng về chất lượng dữ liệu:
1. **Outliers (Giá trị ngoại lai cực đoan):** Sản phẩm 'Nuclear Reactor' có mức giá cực kỳ lớn (999,999) trong danh mục đồ điện tử. Do thuật toán chọn sản phẩm có giá trị lớn nhất trong danh mục mà không qua bộ lọc, Agent đã đưa ra khuyến nghị không phù hợp cho người dùng thông thường.
2. **Duplicate IDs (Trùng lặp mã định danh):** Việc trùng lặp ID (ví dụ: Laptop và Banana cùng có ID là 1) gây khó khăn trong việc truy vấn chính xác thông tin thực tế, dẫn tới sai sót khi tham chiếu chéo dữ liệu.
3. **Wrong Data Types (Sai kiểu dữ liệu):** Bản ghi 'Broken Chair' có giá là chuỗi chữ 'ten dollars' thay vì số, điều này làm hư hại các phép tính toán số học trên Pandas hoặc gây lỗi khi sắp xếp/so sánh giá cả.
4. **Null/Missing Values (Dữ liệu trống/thiếu):** 'Ghost Item' có các trường ID và Category bằng rỗng (Null/None), làm giảm độ chính xác và tính toàn vẹn của tập dữ liệu.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** Đồng ý. Dữ liệu chất lượng (Quality Data) đóng vai trò quyết định và quan trọng hơn cả một Prompt chất lượng. Cho dù prompt được tối ưu hóa tốt đến đâu, nếu dữ liệu đầu vào bị nhiễm độc, chứa các giá trị ngoại lai cực đoan hoặc sai lệch lớn, Agent vẫn sẽ đưa ra những câu trả lời sai hoặc không thể tính toán được. Việc chuẩn hóa và làm sạch dữ liệu qua ETL pipeline là bước bắt buộc để đảm bảo độ tin cậy của AI Agent.
