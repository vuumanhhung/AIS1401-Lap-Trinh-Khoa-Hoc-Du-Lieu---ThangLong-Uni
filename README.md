# Tổng hợp: Lập trình Khoa học dữ liệu (AIS1401)

> @hungdentutuonglai
> Nguồn: 5 file từ bài giảng của giảng viên Nguyễn Đức Minh
> Các ô **⚠ Ghi chú** là phần mình thêm vào để sửa/cập nhật chỗ slide chưa chuẩn hoặc đã cũ, không phải nội dung gốc.

## Mục lục

1. [Giới thiệu môn học](#1-giới-thiệu-môn-học)
2. [Python cơ bản](#2-python-cơ-bản)
3. [List & Dictionary](#3-list--dictionary)
4. [Numpy](#4-numpy)
5. [Pandas](#5-pandas)
6. [Matplotlib](#6-matplotlib)
7. [Cheat sheet nhanh](#7-cheat-sheet-nhanh)

---

## 1. Giới thiệu môn học

| Mục | Nội dung |
|---|---|
| Tên môn | AIS1401 – Lập trình khoa học dữ liệu (Data Science Programming) |
| Học phần trước | FIT1100 – Tin học đại cương |
| Số tín chỉ | 3 (15 tiết lý thuyết + 25 tiết thực hành + 5 tiết kiểm tra/đánh giá) |
| Điểm tổng kết | 10% chuyên cần + 30% bài kiểm tra quá trình (thực hành) + 60% bài tập lớn |

**Nội dung 4 phần:**

1. **Python cơ bản**: cú pháp, cấu trúc dữ liệu, lập trình hiện đại tích hợp AI
2. **Numpy**: tính toán số học, mảng nhiều chiều, đại số tuyến tính
3. **Pandas**: làm sạch, biến đổi, gom nhóm, truy vấn dữ liệu dạng bảng
4. **Matplotlib**: trực quan hóa dữ liệu

**Giáo trình:**
- Python Data Science Handbook, 2nd Ed. – Jake VanderPlas (O'Reilly, 2023)
- Python for Data Science: A Hands-On Introduction – Yuli Vasiliev (No Starch Press, 2022)
- Tham khảo: Python for Data Analysis, 3rd Ed. – Wes McKinney (O'Reilly, 2022)

**Môi trường làm việc:** Google Colab (có Gemini AI tích hợp), Jupyter…

### Khoa học dữ liệu là gì?

Ngành liên quan đến tìm tòi, khai thác, thu thập, phân tích, xử lý dữ liệu để rút ra **insight** rồi chuyển thành hành động. Là sự kết hợp của toán học, thống kê, khoa học máy tính và kiến thức chuyên ngành.

Ví dụ bài toán:
- **Dự báo**: giá nhà đất, hành vi mua hàng
- **Ra quyết định**: giao dịch cổ phiếu
- **Phân tích thời gian thực**: cảnh báo cháy rừng, phân tích dữ liệu bầu cử Mỹ 2020

---

## 2. Python cơ bản

Python do Guido van Rossum phát triển năm 1991. Cú pháp đơn giản, mã nguồn mở, hệ sinh thái thư viện lớn. Dùng cho AI, Data Science, Web, Automation, Cloud.

### 2.1 Căn lề & chú thích
- Dùng **căn lề** (thường 4 space/Tab) thay cho `{}` để chia khối lệnh.
- `#` chú thích 1 dòng; `"""..."""` cho docstring/nhiều dòng.

### 2.2 Biến & kiểu dữ liệu
- **Dynamic typing**: không cần khai báo kiểu.
- Đặt tên theo `snake_case`, không bắt đầu bằng số.
- Gán nhiều biến cùng lúc, hoán đổi giá trị gọn: `a, b = b, a`.

| Kiểu | Mô tả | Ví dụ |
|---|---|---|
| `int` | Số nguyên (không giới hạn kích thước) | `age = 25` |
| `float` | Số thực dấu phẩy động | `pi = 3.14159` |
| `str` | Chuỗi | `name = "Alice"` |
| `bool` | Đúng/sai | `is_active = True` |
| `NoneType` | Giá trị rỗng | `result = None` |

- Kiểm tra kiểu: `type()`, `isinstance()`
- Ép kiểu: `int()`, `float()`, `str()`…

### 2.3 Toán tử

| Nhóm | Toán tử |
|---|---|
| Số học | `+ - * / % ** //` (`9 // 2 = 4`) |
| So sánh | `== != > < >= <=` |
| Gán | `= += -= *= /= %= **= //= &= \|= ^= >>= <<=` |
| Bitwise | `& \| ^ ~ << >>` |
| Logic | `and`, `or`, `not` |
| Membership | `in`, `not in` |
| Identity | `is`, `is not` (so sánh vị trí bộ nhớ, không phải giá trị) |

> **⚠ Ghi chú:** slide gốc ghi toán tử logic là `& | !`. Đó là kiểu C++. Python dùng `and`, `or`, `not`. `&`, `|` là bitwise (và là toán tử logic **từng phần tử** trong Numpy/Pandas, xem các phần sau).

### 2.4 Nhập / xuất
```python
x = input("Nhập: ")      # luôn trả về str
print("a", "b", sep="-", end="\n")
```

### 2.5 Rẽ nhánh
```python
if dieu_kien_1:
    ...
elif dieu_kien_2:
    ...
else:
    ...
```

### 2.6 Vòng lặp
```python
for bien in tap_hop:        # duyệt list/chuỗi/range
    ...
for i in range(start, stop, step):
    ...
while dieu_kien:
    ...
```
- `break`: thoát hẳn vòng lặp
- `continue`: bỏ qua lượt hiện tại
- `pass`: câu lệnh rỗng, giữ chỗ

### 2.7 Hàm
```python
def ten_ham(tham_so):
    return ket_qua
```
- **Built-in**: `print()`, `len()`, `range()`, `int()`, `max()`, `min()`
- **Tự định nghĩa**: dùng `def`
- **Lambda** (ẩn danh): `lambda x: x * 2`

---

## 3. List & Dictionary

| Tiêu chí | List `[ ]` | Dictionary `{ }` |
|---|---|---|
| Truy cập theo | Vị trí (0, 1, 2…) | Khóa (tên tự đặt) |
| Thứ tự | Có thứ tự | Giữ thứ tự thêm vào (Python 3.7+) |
| Trùng lặp | Cho phép trùng giá trị | Khóa **không** trùng |
| Tra cứu | Chậm khi tìm giá trị | Rất nhanh theo khóa |
| Dùng khi | Dãy phần tử cùng loại | Dữ liệu có nhãn/thuộc tính |

**Quy tắc nhanh:** cần một **dãy** → List; cần tra theo **tên/nhãn** → Dictionary. Hai cái lồng nhau tùy ý.

### 3.1 List

**Tạo:** `[ ]`, `list()`, list comprehension. Mutable, chỉ số từ 0, phần tử có thể khác kiểu.
```python
so = [10, 20, 30, 40]
hon_hop = [1, 'hai', 3.0, True]
tu_chuoi = list('abc')       # ['a','b','c']
so[0] = 99                   # sửa được (mutable)
```
> List khác tuple `( )`: tuple **không** đổi được (immutable).

**Chỉ số & slicing** (`lst[đầu:cuối]` không gồm `cuối`):
```python
lst = ['a','b','c','d','e']
lst[0]      # 'a'
lst[-1]     # 'e'  (chỉ số âm đếm từ phải)
lst[1:4]    # ['b','c','d']
lst[:2]     # ['a','b']
lst[::-1]   # đảo ngược
```

**Thêm / xóa:**

| Hàm | Tác dụng |
|---|---|
| `append(x)` | Thêm x vào cuối |
| `insert(i, x)` | Chèn x vào vị trí i |
| `extend(lst2)` | Nối cả list khác vào |
| `remove(x)` | Xóa lần xuất hiện đầu của x |
| `pop(i)` | Lấy ra và xóa phần tử ở i (mặc định cuối) |
| `del lst[i]` / `clear()` | Xóa theo vị trí / xóa hết |

> `append([5,6])` tạo list lồng, khác `extend([5,6])`.

**Thao tác hay dùng:**
```python
a = [3, 1, 4, 1, 5, 9]
len(a)          # 6
4 in a          # True
a.count(1)      # 2
a.index(4)      # 2
a.sort()        # sắp xếp TẠI CHỖ, trả None
b = sorted(a)   # trả bản sao đã sắp xếp
a.sort(reverse=True)
a.reverse()
sum(a); min(a); max(a)
```

**List comprehension:** `[biểu_thức for x in dãy if đk]`
```python
kq = [x**2 for x in range(6) if x % 2 == 0]   # [0, 4, 16]
```

**List lồng nhau (ma trận):**
```python
m = [[1, 2, 3],
     [4, 5, 6],
     [7, 8, 9]]
m[1][2]   # 6  (hàng 1, cột 2)
```

**Sao chép:**
```python
b = a            # THAM CHIẾU: a và b cùng 1 list, sửa b là đổi a
b = a.copy()     # bản sao nông (shallow copy)
# list lồng nhau cần copy.deepcopy
```

### 3.2 Dictionary

```python
sv = {'ten': 'An', 'tuoi': 20, 'lop': 'K65'}
sv['ten']     # 'An'
```
Khóa phải **duy nhất và bất biến** (str, số, tuple). Giá trị là gì cũng được, kể cả list/dict.

**Thêm / sửa / xóa:**
```python
d = {'a': 1, 'b': 2}
d['c'] = 3            # thêm mới
d['a'] = 10           # sửa
d['x']                # KeyError!
d.get('x')            # None (an toàn)
d.get('x', 0)         # 0 (giá trị mặc định)
del d['b']
d.pop('c')            # lấy ra và xóa
'a' in d              # True
```
> Ưu tiên `d.get(k, mặc_định)` khi không chắc khóa tồn tại.

**Phương thức:**

| Hàm | Tác dụng |
|---|---|
| `keys()` / `values()` / `items()` | Khóa / giá trị / cặp (khóa, giá trị) (là *view* động) |
| `update(d2)` | Trộn/ghi đè bằng dict khác |
| `pop(k)`, `popitem()` | Lấy ra và xóa |
| `setdefault(k, v)` | Lấy k, nếu chưa có thì đặt v |

**Duyệt:**
```python
diem = {'An': 9, 'Binh': 7, 'Cuong': 8}
for ten in diem: ...                   # duyệt khóa (mặc định)
for ten, d in diem.items(): ...        # duyệt cả khóa và giá trị
for d in diem.values(): ...            # chỉ giá trị
```
> Đừng thêm/xóa khóa **trong khi đang duyệt** dict. Duyệt trên `list(d.keys())` nếu cần.

**Dict comprehension:**
```python
{x: x**2 for x in range(5)}                       # {0:0, 1:1, 2:4, 3:9, 4:16}
{k: v*0.9 for k, v in {'ao':100,'quan':200}.items()}
```

**Dict lồng nhau** (giống cấu trúc JSON):
```python
lop = {'An': {'toan': 9, 'ly': 8}, 'Binh': {'toan': 7, 'ly': 6}}
lop['An']['toan']   # 9
```

### 3.3 Lỗi thường gặp

| ✓ NÊN | ✕ TRÁNH |
|---|---|
| `d.get(k, mặc_định)` | `b = a` rồi tưởng b là bản sao |
| List comprehension cho biến đổi ngắn | `d['x']` khi chưa chắc có khóa |
| `a.copy()` khi cần bản sao độc lập | Thêm/xóa phần tử khi đang duyệt |
| Dict khi cần tra nhanh theo khóa | Nhầm `append([..])` với `extend([..])` |

---

## 4. Numpy

**NumPy (Numerical Python)** là thư viện nền tảng cho khoa học dữ liệu, học máy, xử lý tín hiệu và ảnh.
```bash
pip install numpy
```
```python
import numpy as np
np.__version__
```

### 4.1 Vì sao dùng Numpy?
- Đối tượng chính: **`ndarray`**, mảng N chiều **đồng nhất** (mọi phần tử cùng kiểu).
- Các chiều gọi là **axis** (từ 0); số chiều gọi là **rank**.
- Nhanh hơn Python thuần khoảng **10–100 lần** và tốn ít bộ nhớ hơn.
- Lý do: `list` lưu con trỏ rải rác khắp bộ nhớ (chậm, tốn RAM); `ndarray` lưu **một khối bộ nhớ liên tục, cùng kiểu**, CPU đọc tuần tự và vector hóa được.

### 4.2 Kiểu dữ liệu Scalar

| Nhóm | Kiểu | Ghi chú |
|---|---|---|
| Boolean | `bool` | 1 byte/phần tử |
| Integer | `int8, int16, int32, int64, int` | `int` mặc định theo C của nền tảng |
| Unsigned | `uint8, uint16, uint32, uint64, uint` | |
| Float | `float32, float64, float` | `float` luôn là 64-bit |
| Complex | `complex64, complex128` | `complex64` = 2 × float32 |
| String | `str` | Unicode UTF-32 |
| Object | `object` | Lưu như object Python |
| Record | `void` | Mảng bản ghi |

### 4.3 Khởi tạo mảng

```python
np.array([1, 2, 3])                       # từ list
np.array([[1, 2], [3, 4], [5, 6]])        # 2D
np.zeros((2, 3))                          # toàn 0
np.ones((2, 3))                           # toàn 1
np.full((2, 3), 9)                        # toàn 9
np.eye(3)                                 # ma trận đơn vị 3x3
np.random.random((2, 3))                  # ngẫu nhiên [0,1)
np.arange(0, 5, 2)                        # [0 2 4]
```

### 4.4 Thuộc tính

| Thuộc tính | Ý nghĩa |
|---|---|
| `.shape` | Kích thước (tuple) |
| `.ndim` | Số chiều |
| `.size` | Số phần tử |
| `.itemsize` | Số byte 1 phần tử |
| `.nbytes` | Tổng số byte |
| `.dtype` | Kiểu dữ liệu |
| `.T` | Chuyển vị |

Ví dụ: mảng 3×4 kiểu `int32` → shape `(3, 4)`, ndim 2, size 12, itemsize 4, nbytes 48.

### 4.5 Reshape & flatten
```python
data = np.array([1, 2, 3, 4, 5, 6])
data.reshape(2, 3)           # 2 hàng 3 cột
data.reshape(3, 2)
# order='C' (theo hàng, mặc định) hoặc 'F' (theo cột)

m = np.array([[1, 2, 3], [4, 5, 6]])
m.flatten()                  # [1 2 3 4 5 6]
m.reshape(-1)                # cũng làm phẳng
```

### 4.6 Truy cập phần tử

| Cú pháp | Ý nghĩa |
|---|---|
| `arr[i]` | Phần tử i của mảng 1D |
| `arr[i, j]` | Hàng i, cột j |
| `arr[i, j, k]` | Mảng 3D |
| `arr[-1]` | Phần tử cuối |
| `arr[start:stop:step]` | Slicing |

```python
b = np.array([[1,2,3,4],[5,6,7,8],[9,10,11,12]])
b[1:, 2:]        # từ hàng 1, cột 2
b[:, 0]          # cả cột 0
a = np.array([10,20,30,40,50,60])
a[::-1]          # đảo ngược
a[[0, 2, 4]]     # fancy indexing: lấy theo danh sách chỉ số
```

### 4.7 Phép toán

- Số ↔ array: phép toán áp lên **từng phần tử**, trả array cùng kích thước.
- Array ↔ array (cùng shape): tính từng cặp phần tử cùng vị trí.

```python
x = np.array([[1, 2], [3, 4]], dtype=np.float64)
y = np.array([[5, 6], [7, 8]], dtype=np.float64)
x + y        # np.add
x - y        # np.subtract
x * y        # np.multiply (nhân TỪNG PHẦN TỬ, không phải nhân ma trận)
x / y        # np.divide
np.sqrt(x)
2 ** x
```

### 4.8 Broadcasting

Cho phép tính giữa các mảng **khác shape** mà không sao chép dữ liệu thật: tiết kiệm bộ nhớ, nhanh, code ngắn.

```python
data = np.array([1.0, 2.0])
data * 1.6          # array([1.6, 3.2])
```
- Ví dụ: A shape `(2,3)` + B shape `(1,3)` → B được "kéo giãn" thành `(2,3)`.
- **Quy tắc:** so sánh các chiều từ **phải sang trái**; hai chiều tương thích khi **bằng nhau** hoặc **một trong hai bằng 1**.
- Lỗi khi: kích thước khác nhau **và** không có cái nào bằng 1. Ví dụ `(3,4)` với `(2,4)`: 4 = 4 nhưng 3 ≠ 2 và không có chiều nào bằng 1 → không broadcast được.

### 4.9 Phép toán Logic & So sánh

| Phép | Hàm | Toán tử |
|---|---|---|
| AND | `np.logical_and()` | `&` |
| OR | `np.logical_or()` | `\|` |
| NOT | `np.logical_not()` | `~` |
| XOR | `np.logical_xor()` | `^` |

| Hàm | Toán tử | Nghĩa |
|---|---|---|
| `np.equal` | `==` | Bằng |
| `np.not_equal` | `!=` | Khác |
| `np.greater` / `greater_equal` | `>` / `>=` | Lớn hơn / ≥ |
| `np.less` / `less_equal` | `<` / `<=` | Nhỏ hơn / ≤ |

Kết quả là mảng boolean, dùng làm **mask** để lọc:
```python
x = np.array([3, 5, 2, 1, 4])
y = np.array([1, 4, 7, 2, 5])
mask = (x > 3) & (y <= x)     # nhớ bọc ngoặc từng điều kiện
x[mask]
mask2 = (x > 3) | (y < 2)
```

### 4.10 Hàm tiện ích

**Tổng hợp theo trục** (`axis=0`: theo từng **cột**; `axis=1`: theo từng **hàng**):
```python
A = np.array([[1, 2], [3, 4], [5, 6]])
A.sum()          # 21
A.sum(axis=0)    # [ 9 12]
A.sum(axis=1)    # [ 3  7 11]
A.min(axis=0)    # [1 2]
A.max(axis=1)
```

| Nhóm | Hàm |
|---|---|
| Kiểm tra | `all()`, `any()` |
| Vị trí | `argmax()`, `argmin()` |
| Chuyển/giới hạn | `astype()`, `clip(min,max)`, `copy()`, `fill(v)`, `round(n)`, `squeeze()` |
| Thống kê | `mean()`, `std()`, `var()` |
| Tích lũy | `prod()`, `cumsum()`, `cumprod()` |
| Khoảng biến thiên | `ptp()` = max − min |
| Xuất | `tolist()`, `dump('f.pkl')`, `dumps()` |

### 4.11 Sắp xếp & tìm kiếm
```python
a = np.array([12, 5, 20, 8, 3])
np.sort(a)              # mảng mới đã sắp xếp (tăng dần)
np.argsort(a)           # chỉ số sắp xếp
np.argmax(a); np.argmin(a)
np.argwhere(a > 10)     # lấy VỊ TRÍ/tọa độ
np.where(a > 10)        # lấy vị trí, hoặc chọn giá trị theo điều kiện
np.extract(a > 10, a)   # lấy GIÁ TRỊ thỏa điều kiện
```

### 4.12 Numpy trong toán học

**Hằng số:** `np.inf`, `np.nan`, `np.e`, `np.pi`, `np.euler_gamma` (≈ 0.5772), `np.NZERO` (−0.0), `np.newaxis` (thêm chiều).

**Lượng giác** (đơn vị radian): `np.sin`, `np.cos`, `np.tan`. **Hyperbolic:** `np.sinh`, `np.cosh`, `np.tanh`.

**Làm tròn:**

| Hàm | Chức năng | Ví dụ |
|---|---|---|
| `np.round(x, d)` | Làm tròn d chữ số | `np.round(3.14159, 2)` → 3.14 |
| `np.rint(x)` | Số nguyên gần nhất | `[1.2, 2.7]` → `[1., 3.]` |
| `np.fix(x)` | Về phía 0 | `[-3.8, 3.8]` → `[-3., 3.]` |
| `np.floor(x)` | Sàn | `3.9` → 3 |
| `np.ceil(x)` | Trần | `3.1` → 4 |
| `np.trunc(x)` | Bỏ phần thập phân | `-3.8` → -3 |

**Mũ & logarit:** `np.exp`, `np.exp2`, `np.log` (ln), `np.log10`, `np.log2`.

**Hàm tích lũy / vi tích phân cơ bản:** `np.sum`, `np.cumsum`, `np.diff` (sai phân), `np.trapz` (tích phân hình thang)…

### 4.13 Đại số tuyến tính

| Hàm | Chức năng |
|---|---|
| `np.dot(a, b)` | Tích vô hướng 2 vector (nhân từng cặp rồi cộng) |
| `np.matmul(A, B)` hoặc `A @ B` | Nhân ma trận. A (m×n) · B (n×p) → (m×p) |
| `np.inner(a, b)` | Tích trong (2 vector) |
| `np.outer(a, b)` | Tích ngoài: a có m phần tử, b có n → ma trận m×n |
| `np.linalg.eig(A)` | Trả `(eigvals, eigvecs)`: giá trị riêng và vector riêng (mỗi **cột** là 1 vector riêng) |
| `np.linalg.eigvals(A)` | Chỉ giá trị riêng |
| `np.linalg.norm(x, ord=None, axis=None, keepdims=False)` | Chuẩn (L1, L2, `np.inf`, `'fro'`, `'nuc'`…) |
| `np.linalg.det(A)` | Định thức (ma trận vuông) |
| `np.linalg.matrix_rank(A)` | Hạng ma trận |
| `np.linalg.inv(A)` | Nghịch đảo (cần `det(A) ≠ 0`) |
| `np.linalg.solve(A, b)` | Giải hệ `Ax = b` (A vuông, khả nghịch) |

Ví dụ nhanh:
```python
A = np.array([[4, 1], [2, 3]])
vals, vecs = np.linalg.eig(A)     # vals = [5., 2.]

a = np.array([1, 2, 3]); b = np.array([4, 5, 6])
np.inner(a, b)                    # 32
np.outer(a, np.array([4, 5]))     # [[4 5],[8 10],[12 15]]

x = np.array([3, 4])
np.linalg.norm(x)                 # 5.0  (L2)
np.linalg.norm(x, 1)              # 7.0  (L1)
np.linalg.norm(x, np.inf)         # 4.0
```

Tính chất định thức: `det(A) ≠ 0` ⇔ A khả nghịch; `det(AB) = det(A)·det(B)`; `det(Aᵀ) = det(A)`.

### 4.14 Xác suất thống kê (`np.random`)

| Hàm | Mô tả | Tham số chính |
|---|---|---|
| `binomial(n, p, size)` | Phân phối nhị thức | n phép thử, xác suất p |
| `chisquare(df, size)` | Chi bình phương | bậc tự do df |
| `choice(a, size, replace, p)` | Chọn ngẫu nhiên từ mảng | |
| `dirichlet(alpha, size)` | Vector xác suất có tổng = 1 | |
| `f(dfnum, dfden, size)` | Phân phối Fisher (ANOVA) | |
| `gamma(shape, scale, size)` | Phân phối Gamma | |
| `multinomial(n, pvals, size)` | Đa thức | |
| `normal(loc, scale, size)` | Chuẩn (Gaussian) | μ, σ |
| `uniform(low, high, size)` | Đều trong [low, high) | |
| `poisson(lam, size)` | Poisson | λ |
| `rand(d0, d1, …)` | Đều [0,1) | |
| `randint(low, high, size)` | Nguyên ngẫu nhiên trong [low, high) | |
| `randn(d0, d1, …)` | Chuẩn tắc (μ=0, σ=1) | |
| `permutation(x)` | Trả **bản sao** hoán vị | không đổi gốc |
| `shuffle(x)` | Tráo **tại chỗ** | đổi mảng gốc |
| `seed(n)` | Cố định hạt giống để tái lập kết quả | |

**Thống kê mô tả:** `np.ptp`, `np.percentile`, `np.quantile`, `np.median`, `np.average` (có trọng số), `np.mean`, `np.std`, `np.var`, `np.corrcoef` (Pearson), `np.correlate`, `np.cov`, `np.histogram`, `np.bincount`.

> **⚠ Ghi chú:** API `np.random.*` ở trên là kiểu cũ (legacy), vẫn dùng được. Code mới nên dùng `rng = np.random.default_rng(42)` rồi `rng.normal(...)`, `rng.integers(...)`. `np.trapz` đã được thay bằng `np.trapezoid` ở Numpy 2.x.

### 4.15 Ứng dụng: xử lý ảnh
Máy tính nhìn ảnh như **ma trận số nguyên** (pixel; ảnh màu là 3 kênh RGB). Dùng Numpy để biến đổi, lọc pixel, tích chập (ví dụ bộ lọc Sobel để dò biên).

---

## 5. Pandas

**Pandas** (từ "Panel Data") là thư viện xử lý và phân tích dữ liệu **dạng bảng** (giống Excel/SQL). Tài liệu: <https://pandas.pydata.org/docs/>
```bash
pip install pandas
```
```python
import numpy as np
import pandas as pd
print(pd.__version__)
```
Hệ sinh thái: NumPy (nền tảng) → Pandas (làm sạch/biến đổi) → Matplotlib/Seaborn (vẽ), scikit-learn (học máy), Jupyter (notebook).

### 5.1 Cấu trúc dữ liệu
- **Series**: 1 chiều, đồng nhất.
- **DataFrame**: 2 chiều, mỗi cột đồng nhất; = tập hợp các Series chung một **index** dòng. `axis=0` là DÒNG (index), `axis=1` là CỘT (columns).
- ~~Panel~~: 3 chiều (đã bị loại khỏi pandas, xem ghi chú cuối phần).

### 5.2 Khởi tạo

```python
# Series
s = pd.Series([1, 2, 3, 4, 5])
s[0] = 2
s.sum(); s.cumsum(); s.mean(); s.argmax()

# DataFrame từ list
df1 = pd.DataFrame([['An', 9], ['Binh', 8]], columns=['Ten', 'Diem'])
# từ dict, có đặt index
df2 = pd.DataFrame({'Ten': ['An', 'Binh'], 'Diem': [9, 8]}, index=['sv1', 'sv2'])
# từ file
df3 = pd.read_csv('Salary_Data.csv')
```
Chữ ký: `pd.DataFrame(data, index, columns, dtype, copy)`.

### 5.3 Thuộc tính & xem thông tin

| Thuộc tính | Mô tả | Kiểu |
|---|---|---|
| `df.shape` | (số dòng, số cột) | tuple |
| `df.columns` | Nhãn cột | Index |
| `df.index` | Nhãn dòng | Index |
| `df.values` | Mảng 2D không gồm nhãn | ndarray |
| `df.dtypes` | Kiểu từng cột | Series |
| `df.size` | Số ô = dòng × cột | int |
| `df.ndim` | Luôn = 2 | int |
| `df.empty` | Rỗng hay không | bool |
| `df.T` | Chuyển vị | DataFrame |

> Đây là **thuộc tính**, không có `()`: `df.shape` đúng, `df.shape()` sai.

```python
df.head(n)      # n dòng đầu (mặc định 5)
df.tail(n)      # n dòng cuối
df.sample(n)    # n dòng ngẫu nhiên
df.info()       # cột, kiểu, số ô non-null, bộ nhớ
df.describe()   # count, mean, std, min, quartiles, max
```

### 5.4 Nhập / xuất (I/O)
Mẫu thống nhất: `pd.read_<định dạng>()` để đọc, `df.to_<định dạng>()` để ghi.

| Định dạng | Đọc | Ghi |
|---|---|---|
| CSV | `pd.read_csv()` | `df.to_csv()` |
| Excel | `pd.read_excel()` | `df.to_excel()` |
| JSON | `pd.read_json()` | `df.to_json()` |
| SQL | `pd.read_sql()` | `df.to_sql()` |
| HTML | `pd.read_html()` | `df.to_html()` |
| Pickle | `pd.read_pickle()` | `df.to_pickle()` |
| Dict | `pd.DataFrame(d)` | `df.to_dict()` |
| Khác | clipboard | `to_latex()`, `to_markdown()` |

```python
df.to_csv('out.csv', index=False, encoding='utf-8-sig')   # utf-8-sig để Excel mở đúng tiếng Việt
```
Tham số hay dùng: `sep`, `encoding`, `index=False`.

### 5.5 Chuyển kiểu
```python
df['Diem'] = df['Diem'].astype(float)
df = df.convert_dtypes()                 # tự suy luận kiểu tối ưu
df.select_dtypes(include='number')       # lọc cột theo kiểu
df.to_dict()
df2 = df.copy()                          # bản sao độc lập
```

### 5.6 Đổi tên dòng/cột
```python
df.rename(columns={'W': 'Tuan'}, index={0: 'sv1'})   # đổi có chọn lọc
df.rename_axis(index='Mon')                          # đặt tên cho TRỤC, không đổi nhãn
df.set_axis(['a', 'b', 'c'], axis=1)                 # thay TOÀN BỘ nhãn
df.add_suffix('_1')
df.add_prefix('col_')
```

### 5.7 Thao tác với cột
```python
df['A']  # hoặc df.A       → Series
df[['A', 'B']]             → DataFrame
df['C'] = [...]            # thêm/sửa (số phần tử = số dòng)
df.insert(1, 'Ten', values)   # chèn đúng vị trí
df.pop('C'); df.drop(columns='C')
```

### 5.8 Chọn dòng/cột

| Cách | Dùng |
|---|---|
| `df.loc[nhãn_dòng, nhãn_cột]` | Theo **nhãn** |
| `df.iloc[i, j]` | Theo **vị trí** (0-based) |
| `df.at['Binh', 'Ly']` | 1 ô theo nhãn (nhanh) |
| `df.iat[1, 2]` | 1 ô theo vị trí (nhanh) |
| `df.get('Hoa')` | Lấy cột an toàn, thiếu → `None` |

> `at`/`iat` chỉ dùng cho **đơn ô**; cần nhiều ô thì dùng `loc`/`iloc`.

### 5.9 Truy vấn theo điều kiện
```python
df[df['Toan'] >= 8]                                  # 1 điều kiện
df[(df['Toan'] >= 8) & (df['Ly'] >= 6)]              # nhiều điều kiện: & | ~ và NGOẶC ĐƠN
df[df['Ten'].isin(['An', 'Binh'])]                   # thuộc tập giá trị

df.query('Toan >= 8 and Ly > 5')                     # biểu thức kiểu SQL
nguong = 8
df.query('Toan >= @nguong')                          # @biến tham chiếu biến Python

df.filter(items=['Toan', 'Ly'])                      # chọn cột theo tên
df.filter(like='_id')                                # chứa '_id'
df.filter(regex='^T')                                # bắt đầu bằng T
```

**Theo thời gian** (cần `DatetimeIndex`; so sánh chuỗi sẽ sai):
```python
ts.at_time('09:00')                       # đúng 9h
ts.between_time('09:00', '17:00')         # giờ hành chính
df.truncate(before='2023-01-05', after='2023-01-20')
```

### 5.10 Cập nhật giá trị
```python
df.where(df >= 5, 0)            # GIỮ giá trị nếu đúng, còn lại thay bằng 0
df.mask(df > 8, 0)              # NGƯỢC where: thay khi điều kiện đúng
df.replace(0, np.nan)
df.replace({'yes': 1, 'no': 0})
```

### 5.11 Duyệt DataFrame
```python
for idx, row in df.iterrows(): ...      # (index, Series-dòng), dễ đọc nhưng chậm
for row in df.itertuples(): ...         # namedtuple, nhanh hơn: row.A, row.B
df.items()                              # (tên_cột, Series-cột)
df.keys()                               # = df.columns
```

**Ví dụ tạo cột điểm TB** (nhiều cách, khác nhau về tốc độ):
```python
# Cách 1: vòng lặp (chậm)
tb = []
for idx, row in df.iterrows():
    tb.append((row['Toan'] + row['Ly']) / 2)
df['TB'] = tb
# Cách 2: vector hóa (nhanh, gọn) ← nên dùng
df['TB'] = (df['Toan'] + df['Ly']) / 2
```

### 5.12 Áp hàm
```python
df.apply(sum, axis=1)                          # theo dòng (axis=1) hoặc cột (axis=0)
df.apply(lambda x: x.max() - x.min())
df.applymap(lambda v: v * 2)                   # từng ô
df['Toan'].map(lambda x: x / 10)               # từng phần tử Series
df['XL'] = df['Toan'].map(lambda x: 'Gioi' if x >= 8 else 'Kha')
s.map({'A': 1, 'B': 0})                        # map bằng dict: mã hóa nhãn thành số
df.pipe(chuan_hoa).pipe(loc_bo)                # nối chuỗi xử lý
```
Mẹo nhớ: `axis=0` "đi dọc xuống" → ra 1 giá trị cho mỗi **cột**; `axis=1` "đi ngang" → 1 giá trị cho mỗi **dòng**.
`apply` linh hoạt nhưng chậm hơn phép vector hóa; chỉ dùng khi không có hàm sẵn.

### 5.13 Gom nhóm (`groupby`)
```python
df.groupby('Lop')['Diem'].mean()                                  # TB điểm theo lớp
df.groupby('Lop').agg({'Diem': ['mean', 'max'], 'Tuoi': 'min'})   # nhiều hàm cùng lúc
df.groupby('Lop')['Diem'].transform(lambda x: (x - x.mean()) / x.std())   # chuẩn hóa trong nhóm
```
`transform` trả kết quả **cùng kích thước** dữ liệu gốc (broadcast ngược lại).

### 5.14 Thống kê & tổng hợp
```python
df.mean(); df.std(); df.count()
df.quantile(0.75)               # phân vị 75%
df['Nuoc'].value_counts()       # đếm tần suất
df['Nuoc'].unique()
df['Diem'].idxmax()             # NHÃN dòng có giá trị max (khác .max())
(df > 5).any(); (df > 0).all()
```

### 5.15 Dữ liệu rỗng (NaN)
```python
df.isna().sum()                 # đếm NaN theo cột — bước đầu khi làm sạch
df.dropna()                     # xóa mọi dòng có ≥1 NaN
df.dropna(subset=['sale'])      # chỉ xét cột 'sale'
df.dropna(how='all')            # chỉ xóa dòng toàn NaN
df.dropna(thresh=k)             # giữ dòng có ≥ k giá trị hợp lệ
df.fillna(0)
df.ffill()                      # điền tiến: [10, NaN, NaN, 20] → [10, 10, 10, 20]
df.bfill()                      # điền lùi
df.interpolate()                # nội suy: [10, NaN, 30] → [10, 20, 30]
```
Chọn xóa hay bổ sung tùy bài toán.

### 5.16 Dữ liệu trùng lặp
Mức độ: **Exact** (trùng hoàn toàn) · **Near/Fuzzy** (trùng mờ) · **Key-based** (trùng theo khóa).
```python
df.duplicated()                         # đánh dấu True/False
df.duplicated().sum()                   # đếm dòng trùng
df.drop_duplicates()                    # giữ lần xuất hiện ĐẦU TIÊN
df.drop_duplicates(subset=['Ten'])      # xét trùng chỉ theo cột Ten
df.drop_duplicates(keep='last')         # giữ lần cuối ('first' | 'last' | False)
```

### 5.17 Sắp xếp & Top-N
```python
df.sort_values('Diem', ascending=False)
df.sort_values(['Lop', 'Diem'])
df.sort_index()
df.nlargest(3, 'GDP'); df.nsmallest(3, 'GDP')
df.sort_values('Diem').reset_index(drop=True)   # đánh số lại index
```
Tham số: `ascending`, `na_position`.

### 5.18 Bảng tổng hợp
```python
df.pivot(index='Ten', columns='Mon', values='Diem')      # xoay dài → rộng, KHÔNG tổng hợp
df.pivot_table(index='Lop', values='Diem', aggfunc='mean')   # có hàm tổng hợp
pd.crosstab(df['Lop'], df['Mon'])                        # bảng tần suất chéo 2 biến
```

### 5.19 Vẽ nhanh với `.plot()`
Pandas tích hợp Matplotlib:

| Loại | Gọi | Dùng cho |
|---|---|---|
| line / area | `df.plot()`, `df.plot.area()` | Xu hướng theo thời gian |
| bar | `df.plot.bar()` | So sánh giữa các nhóm |
| hist | `df.hist()`, `df.plot.hist()` | Phân bố tần suất |
| box | `df.plot.box()` | Tứ phân vị & outlier |
| kde | `df.plot.kde()` | Ước lượng mật độ |
| scatter | `df.plot.scatter(x, y)` | Quan hệ 2 biến số |

### 5.20 Nối & kết hợp DataFrame
```python
pd.concat([df1, df2])                 # axis=0: xếp chồng theo DÒNG
pd.concat([df1, df2], axis=1)         # axis=1: ghép theo CỘT (dựa trên index)
pd.merge(df_A, df_B, on='Ma_SV')                    # mặc định how='inner'
pd.merge(df_A, df_B, on='Ma_SV', how='left')        # giữ hết df_A; thiếu bên B → NaN
```

| `how` | Giữ khóa |
|---|---|
| `inner` | Giao (khóa có ở cả 2 bảng) |
| `left` | Toàn bộ bảng trái |
| `right` | Toàn bộ bảng phải |
| `outer` | Hợp (tất cả); bên thiếu → NaN |

### 5.21 Dữ liệu thời gian
```python
pd.to_datetime(['1/2/23'], format='%d/%m/%y')     # chuỗi → datetime; %d ngày, %m tháng, %y năm 2 số
pd.date_range(start='2023-01-01', periods=9)      # mặc định freq='D'
pd.infer_freq(idx)                                # suy ra chu kỳ
df['ngay'] = pd.to_datetime(df['ngay'])
df['thang'] = df['ngay'].dt.month
df['thu'] = df['ngay'].dt.day_name()
```
`.dt` có: `.year`, `.month`, `.day`, `.hour`, `.dayofweek`, `.quarter`, `.is_month_end`… (chỉ dùng trên cột kiểu datetime). Cũng có `tz_localize()`.

`freq`: `'D'` ngày · `'W'` tuần · `'B'` ngày làm việc · `'H'` giờ · `'M'` cuối tháng.

> **⚠ Ghi chú (pandas 2.x trở lên):**
> - **Panel** đã bị xóa khỏi pandas; dữ liệu 3 chiều dùng MultiIndex hoặc `xarray`.
> - `DataFrame.applymap` đã đổi tên thành `DataFrame.map` (từ 2.1), `applymap` bị cảnh báo deprecated.
> - `fillna(method='ffill')` đã deprecated, dùng `df.ffill()` / `df.bfill()`.
> - `freq='H'` → `'h'`, `'M'` → `'ME'` (month end) ở bản mới.

---

## 6. Matplotlib

**Trực quan hóa dữ liệu** là biểu diễn thông tin dưới dạng đồ họa để phân tích lượng lớn dữ liệu và ra quyết định dựa trên dữ liệu (data-driven).

**Matplotlib**: thư viện vẽ biểu đồ mở rộng từ Numpy, mục tiêu "chỉ cần vài dòng lệnh". Hỗ trợ plot, histogram, power spectra, bar, error chart, scatter…
```bash
pip install matplotlib
```
```python
import matplotlib.pyplot as plt
```

### 6.1 Thành phần của một hình
- **Figure**: toàn bộ khung hình, chứa các Axes và các Artist đặc biệt (tiêu đề, legend, colorbar…).
- **Axes**: vùng chứa dữ liệu bên trong Figure, có trục x/y (Axis), nhãn, tiêu đề, vùng vẽ.
- Mô hình tư duy: **Figure → Axes → Artists** (line, text, marker, patch…).

### 6.2 Biểu đồ đầu tiên
```python
plt.plot([1, 2, 3, 4])        # 1 list → hiểu là y; x tự sinh = [0,1,2,3]
plt.ylabel('some numbers')
plt.show()
```

**Mẫu cơ bản:** tạo Figure/Axes → vẽ → hiển thị.
```python
x = np.linspace(0, 2, 100)
fig, ax = plt.subplots()      # Figure + Axes
ax.plot(x, x, label='linear')
ax.plot(x, x**2, label='quadratic')
ax.plot(x, x**3, label='cubic')
ax.set_xlabel('x'); ax.set_ylabel('y'); ax.set_title('Simple Plot')
ax.legend()
plt.show()
```

### 6.3 Hai phong cách viết

| OO style (khuyến nghị) | pyplot style (nhanh, tiện) |
|---|---|
| `fig, ax = plt.subplots()` | `plt.figure()` |
| `ax.plot(x, x, label='linear')` | `plt.plot(x, x, label='linear')` |
| `ax.set_xlabel('x')` | `plt.xlabel('x')` |
| `ax.set_title('Simple Plot')` | `plt.title('Simple Plot')` |
| `ax.legend()` | `plt.legend()` |

### 6.4 Dữ liệu đầu vào
- NumPy: `np.array`, `np.ma.masked_array`, hoặc đối tượng chuyển được qua `np.asarray()`.
- Pandas/dict: truyền `data=` và dùng tên cột/khóa: `ax.scatter('a', 'b', c='c', s='d', data=data)`.

### 6.5 Tùy chỉnh
```python
ax.set_xlabel('Length [cm]')
ax.set_ylabel('Probability')
ax.set_title('Distribution')
ax.text(75, .025, r'$\mu=115,\ \sigma=15$')      # thêm text (hỗ trợ LaTeX)
ax.grid(True)
ax.annotate('local max', xy=(2, 1), xytext=(3, 1.5))
ax.legend()
```
- **Scale:** tuyến tính, log (`ax.set_yscale('log')`), tùy chỉnh vị trí/nhãn ticks. Dữ liệu trải qua nhiều bậc độ lớn → dùng log scale.
- **Categorical & dates:** chuỗi được hiểu là category. Cẩn thận: truyền hàng nghìn chuỗi số sẽ bị coi là hàng nghìn category.
- **Color-mapped data:** màu biểu diễn thêm 1 chiều dữ liệu; `colorbar` để giải mã. Hàm tiêu biểu: `pcolormesh()`, `contourf()`, `imshow()`, `scatter()`.
- **Nhiều Axes:**
  ```python
  fig, axs = plt.subplots(2, 2)                       # lưới 2×2
  fig, axd = plt.subplot_mosaic([["upleft", "right"],
                                 ["lowleft", "right"]])   # layout đặt tên
  ax.twinx()               # thêm trục y thứ hai (khác đơn vị)
  ax.secondary_xaxis(...)  # trục phụ có phép biến đổi (vd radian ↔ độ)
  ```

### 6.6 Quy trình vẽ (4 bước)
1. **Chọn loại biểu đồ** (theo loại dữ liệu và mục đích)
2. **Thiết lập tham số**: trục, nhãn, tỉ lệ, điểm nhấn, màu, chú thích
3. **Vẽ biểu đồ**: `plot()` / `scatter()` / `bar()` / `hist()`
4. **Hiển thị / lưu**: `plt.show()` / `fig.savefig('ten.png')`

### 6.7 Các loại biểu đồ

**Line plot**: `plot([x], y, [fmt], data=None, **kwargs)`. Trả về list các `Line2D`. Vẽ nhiều lần trên 1 hình được.

`fmt = '[color][marker][line]'`:

| Màu | Marker | Nét |
|---|---|---|
| `b` blue, `g` green, `r` red, `c` cyan, `m` magenta, `y` yellow, `k` black, `w` white, `#rrggbb` | `o` tròn, `v ^ < >` tam giác, `*` sao, `.` chấm, `p` ngũ giác | `-` liền, `--` đứt, `-.` gạch chấm |

> **⚠ Ghi chú:** slide ghi black là `'b'`, nhưng `'b'` là blue; **black là `'k'`**.

**Bar plot:**
```python
names = ["A", "B", "C", "D", "E"]; values = [5, 6, 3, 7, 2]
plt.bar(names, values, color="green")
plt.barh(names, values, color="yellowgreen")   # thêm "h" → nằm ngang
```
Có thể truyền `width=0.8`, danh sách màu, rồi `plt.xlabel / ylabel / title`.

**Histogram:**
```python
ages = [2, 5, 70, 40, 30, 45, 50, 45, 43, 40, 44, 60, 7, 13, 57, 18, 90, 77, 32, 21, 20, 40]
plt.hist(ages, bins=10, range=(0, 100), color='green', histtype='bar', rwidth=0.8)
plt.xlabel('age'); plt.ylabel('No. of people'); plt.title('My histogram')
```

**Scatter:**
```python
plt.scatter(x_values, y_values, s=30, color="blue")
plt.scatter(x, y, label="stars", color="green", marker="*", s=30)
plt.legend()
```

**Pie chart:**
```python
activities = ['eat', 'sleep', 'work', 'play']
slices = [3, 7, 8, 6]
colors = ['r', 'y', 'g', 'b']
plt.pie(slices, labels=activities, colors=colors, startangle=90,
        shadow=True, explode=(0, 0, 0.1, 0), radius=1.2, autopct='%1.1f%%')
plt.legend()
plt.show()
```

---

## 7. Cheat sheet nhanh

### Chọn công cụ theo mục đích

| Cần làm gì | Dùng |
|---|---|
| Dãy phần tử, thứ tự | `list` |
| Tra theo tên/nhãn | `dict` |
| Tính toán số học nhanh, ma trận | `numpy.ndarray` |
| Dữ liệu bảng, làm sạch, gom nhóm | `pandas.DataFrame` |
| Vẽ biểu đồ | `matplotlib` (hoặc `df.plot()`) |

### Dễ nhầm

| Cặp | Khác nhau |
|---|---|
| `list.sort()` vs `sorted()` | `sort()` đổi tại chỗ, trả `None`; `sorted()` trả bản sao |
| `append` vs `extend` | `append` thêm 1 phần tử (có thể là list lồng); `extend` nối nhiều phần tử |
| `b = a` vs `a.copy()` | Tham chiếu vs bản sao độc lập |
| `shuffle` vs `permutation` | Đổi tại chỗ vs trả bản sao |
| `x * y` (Numpy) vs `np.matmul` / `@` | Nhân từng phần tử vs nhân ma trận |
| `argwhere` / `where` / `extract` | Lấy vị trí / vị trí hoặc chọn giá trị / lấy giá trị |
| `loc` vs `iloc` | Theo nhãn vs theo vị trí |
| `where` vs `mask` | Giữ khi đúng vs thay khi đúng |
| `pivot` vs `pivot_table` | Không tổng hợp vs có `aggfunc` |
| `max()` vs `idxmax()` | Giá trị lớn nhất vs nhãn dòng chứa giá trị đó |
| `axis=0` vs `axis=1` | Theo cột (đi dọc xuống) vs theo hàng (đi ngang) |
| `iterrows` vs `itertuples` | Series-dòng (chậm) vs namedtuple (nhanh hơn) |
| `permutation` / `shuffle` + `seed` | Cố định `seed` để kết quả tái lập được |
| Merge `inner` / `left` / `right` / `outer` | Giao / giữ trái / giữ phải / hợp |

### Quy trình phân tích dữ liệu thường gặp

```
Đọc dữ liệu (read_csv)
  → Khảo sát (head, info, describe)
  → Làm sạch (isna, dropna/fillna, drop_duplicates, astype)
  → Biến đổi (cột mới, apply/map, groupby, pivot_table, merge)
  → Trực quan hóa (df.plot / matplotlib)
  → Lưu kết quả (to_csv, savefig)
```
