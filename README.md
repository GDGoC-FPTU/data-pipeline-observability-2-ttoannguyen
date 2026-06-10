# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** toannguyen@example.com
**Name:** Toan Nguyen

---

## Mo ta

Bài Lab này thực hiện xây dựng một ETL Pipeline đơn giản bằng Python và thư viện Pandas để xử lý dữ liệu thô từ `raw_data.json`, bao gồm:
1. **Extract**: Đọc dữ liệu từ file JSON.
2. **Validate**: Loại bỏ các bản ghi không hợp lệ (giá trị price <= 0 hoặc trường category bị trống).
3. **Transform**: Áp dụng mức giảm giá 10% (tính cột `discounted_price`), chuẩn hóa danh mục `category` thành dạng Title Case, và thêm nhãn thời gian `processed_at`.
4. **Load**: Xuất dữ liệu đã xử lý ra file CSV `processed_data.csv`.

Ngoài ra, bài Lab cũng thực hiện thử nghiệm chạy Agent Simulation để đánh giá tầm quan trọng của Data Quality đối với chất lượng đầu ra của AI.

---

## Cach chay (How to Run)

### Prerequisites
```bash
python3 -m venv venv
source venv/bin/activate
pip install pandas pytest
```

### Chay ETL Pipeline
```bash
python3 solution.py
```

### Chay Agent Simulation (Stress Test)
```bash
# Tao du lieu rac
python3 generate_garbage.py

# Chay Agent thu nghiem voi Clean vs Garbage data
python3 agent_simulation.py
```

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script
├── processed_data.csv       # Output cua pipeline
├── experiment_report.md     # Bao cao thi nghiem
└── README.md                # File nay
```

---

## Ket qua

- **Tổng số bản ghi đầu vào**: 5 records
- **Số bản ghi hợp lệ được xử lý**: 3 records (Laptop, Chair, Monitor)
- **Số bản ghi bị loại bỏ**: 2 records (Mystery Box do giá âm, Phone do category trống)
