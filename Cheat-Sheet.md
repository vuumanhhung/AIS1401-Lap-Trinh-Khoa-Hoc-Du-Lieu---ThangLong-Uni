# 📘 CẨM NANG ÔN TẬP PANDAS & TITANIC TRỰC QUAN KHÔNG THỂ BỎ QUA

Bộ tài liệu ôn tập tóm tắt ngắn gọn, đi kèm ý nghĩa cốt lõi và ví dụ thực tế giúp bạn nhớ lâu nhất.

---

## 1. Truy vấn Dữ liệu Cơ bản (Selecting & Filtering)

### 🔹 1.1 Chọn Cột (`[]`, `loc`, `iloc`)
* **Ý nghĩa:** Trích xuất các đặc trưng (cột) hoặc mẫu tin (dòng) cần thiết để tối ưu hóa bộ nhớ.
* **Ví dụ:**
  ```python
  # Chỉ lấy cột Name và Fare
  df[['Name', 'Fare']]

  # Lấy dòng thứ 10 đến 20 của cột Name và Fare bằng iloc (theo chỉ số số nguyên)
  df.iloc[10:21][['Name', 'Fare']]
  ```

### 🔹 1.2 Lọc Theo Điều Kiện (Boolean Indexing)
* **Ý nghĩa:** Giữ lại các dòng thỏa mãn một hoặc nhiều tiêu chí (nam/nữ, độ tuổi, giá vé...).
* **Ví dụ:**
  ```python
  # Lọc phụ nữ ở hạng ghế 1
  df[(df['Sex'] == 'female') & (df['Pclass'] == 1)]

  # Lọc hành khách đi một mình
  df[(df['SibSp'] == 0) & (df['Parch'] == 0)]
  ```

### 🔹 1.3 Lọc Trong Khoảng / Danh sách (`between`, `isin`)
* **Ý nghĩa:** Rút gọn cú pháp lọc khoảng số hoặc lọc danh sách giá trị thuộc nhóm cụ thể.
* **Ví dụ:**
  ```python
  # Lọc giá vé từ 50 đến 100
  df[df['Fare'].between(50, 100)]

  # Lọc hành khách xuất phát từ cảng Cherbourg (C) hoặc Queenstown (Q)
  df[df['Embarked'].isin(['C', 'Q'])]
  ```

---

## 2. Thao Tác Chuỗi (String Methods `.str`)

### 🔹 2.1 Kiểm tra tiền tố & chứa ký tự (`startswith`, `contains`)
* **Ý nghĩa:** Tìm kiếm các mẫu ký tự trong dữ liệu dạng chữ (văn bản).
* **Ví dụ:**
  ```python
  # Vé bắt đầu bằng ký tự 'PC'
  df[df['Ticket'].str.startswith('PC', na=False)]

  # Cabin chứa khoảng trắng (nhiều cabin đặt cùng lúc)
  df[df['Cabin'].str.contains(' ', na=False)]
  ```

### 🔹 2.2 Tách chuỗi (`split`)
* **Ý nghĩa:** Phân tách một chuỗi dài thành các phần nhỏ dựa trên ký tự ngăn cách (phân tích Họ tên, Địa chỉ...).
* **Ví dụ:**
  ```python
  # Tách họ của hành khách (phần trước dấu phẩy trong Name)
  df['Name'].str.split(',').str[0]
  ```

---

## 3. Gom Nhóm & Thống Kê (Grouping & Aggregation)

### 🔹 3.1 Nhóm nâng cao (`groupby`, `agg`)
* **Ý nghĩa:** Gom nhóm dữ liệu dựa trên một hay nhiều đặc trưng để tính toán các chỉ số thống kê tổng hợp.
* **Ví dụ:**
  ```python
  # Tính giá vé nhỏ nhất, lớn nhất và trung bình cho từng Hạng ghế
  df.groupby('Pclass')['Fare'].agg(['min', 'max', 'mean'])
  ```

### 🔹 3.2 Bảng Chéo (`pd.crosstab`)
* **Ý nghĩa:** Thống kê tần suất hoặc tỷ lệ phân bổ chéo giữa 2 nhóm biến phân loại.
* **Ví dụ:**
  ```python
  # Tỷ lệ phần trăm hành khách của từng cảng trong mỗi hạng vé
  pd.crosstab(df['Pclass'], df['Embarked'], normalize='index') * 100
  ```

---

## 4. Ghép Bảng & Phân Tích (Joins & Window Functions)

### 🔹 4.1 Khớp nối dữ liệu (`pd.merge`)
* **Ý nghĩa:** Kết nối các bảng dữ liệu có chung khóa liên kết tương tự SQL JOIN.
* **Ví dụ:**
  ```python
  # Ghép thông tin cảng chi tiết vào bảng titanic dựa trên mã cảng
  pd.merge(df, ports_df, on='Embarked', how='left')
  ```

### 🔹 4.2 Lũy kế & Biến đổi nhóm (`transform`, `cumsum`)
* **Ý nghĩa:** Thực hiện tính toán giữ nguyên kích thước bảng gốc (không làm gộp dòng).
* **Ví dụ:**
  ```python
  # So sánh giá vé của hành khách với giá trung bình của chính hạng vé họ đi
  df['Fare_Avg_Class'] = df.groupby('Pclass')['Fare'].transform('mean')

  # Tính lũy kế số người sống sót theo ID
  df['Survived_CumSum'] = df['Survived'].cumsum()
  ```
