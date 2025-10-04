# 🔬 NCKH - BPA and Entropy Research
### Mô hình xác định BPA và xử lý xung đột bằng Adaboost & Entropy Niềm Tin

**Tác giả:** Nguyễn Thị Thanh Thảo và đồng sự.
**Ngôn ngữ:** Python (Jupyter Notebook)

---

## 📘 Giới thiệu

Trong kỷ nguyên dữ liệu lớn và trí tuệ nhân tạo, việc **xử lý thông tin không chắc chắn** trở thành một thách thức lớn trong các bài toán phân loại, đặc biệt ở các lĩnh vực yêu cầu độ tin cậy cao như **y tế, tài chính, chẩn đoán lỗi và nhận dạng mẫu**.

Dự án này nghiên cứu và triển khai **một mô hình phân loại dựa trên lý thuyết Dempster–Shafer (DSET)**, trong đó:
- **Adaboost** được sử dụng để xác định **BPA (Basic Probability Assignment)** mà không cần giả định phân phối dữ liệu.  
- **Entropy Niềm Tin (Deng Entropy)** và **Phủ định BPA** được áp dụng để **giảm xung đột thông tin** và **nâng cao độ chính xác phân loại**.

Mục tiêu chính:
- Tối ưu hóa quy trình gán BPA từ dữ liệu nhỏ hoặc phân tán.  
- Đề xuất cơ chế kết hợp BPA đáng tin cậy hơn thông qua phủ định và entropy.  
- Ứng dụng vào các bài toán phân loại thực nghiệm như bộ dữ liệu **Iris (UCI)**.

---

## 🧩 Phương pháp nghiên cứu

### 1️⃣ Xác định BPA bằng Adaboost
- Áp dụng **Adaboost với Decision Stump** làm bộ phân loại yếu.  
- Mỗi cặp thuộc tính được huấn luyện riêng biệt → tính BPA cho từng lớp.  
- Sử dụng **phương pháp tỷ lệ diện tích (Area Ratio Method)** để phân bổ lại BPA cho các vùng giao nhau (tập hợp mệnh đề tổng hợp).  
- Không cần giả định phân phối dữ liệu (như Gaussian), giúp phù hợp với tập huấn luyện nhỏ.

### 2️⃣ Xử lý xung đột bằng Phủ định BPA và Entropy Niềm Tin
- **Phủ định BPA** giúp khôi phục thông tin bị mất trong quá trình kết hợp chứng cứ mâu thuẫn.  
- **Entropy Niềm Tin (Deng Entropy)** dùng để đo lường mức độ không chắc chắn của mỗi nguồn thông tin → điều chỉnh trọng số trước khi hợp nhất.  
- Kết hợp các chứng cứ bằng **quy tắc Dempster** để tạo ra quyết định phân loại cuối cùng.

---

## ⚙️ Quy trình thực hiện

1. Chuẩn bị và chia dữ liệu (80% train / 20% test).  
2. Huấn luyện mô hình Adaboost cho từng cặp thuộc tính.  
3. Tính BPA cho từng lớp và mệnh đề tổng hợp.  
4. Áp dụng phủ định BPA và entropy niềm tin để hiệu chỉnh.  
5. Hợp nhất chứng cứ bằng quy tắc Dempster.  
6. Phân loại mẫu dựa trên BPA lớn nhất.  
7. Đánh giá hiệu suất bằng Accuracy, Precision, Recall, F1-score.

---

## 🧪 Kết quả thực nghiệm

- **Tập dữ liệu:** Iris (UCI Repository)  
- **Số mẫu:** 150 (3 lớp: Setosa, Versicolor, Virginica)  
- **Đặc trưng:** 4 thuộc tính (chiều dài/rộng đài hoa & cánh hoa)

| Chỉ số | Kết quả |
|--------|----------|
| Accuracy | **100.00%** (với ≥ 60% dữ liệu huấn luyện) |
| Accuracy (10% train) | **>93%** |
| Phương pháp so sánh | SVM, KNN, Random Forest |
| Kết quả | Mô hình BPA-Adaboost vượt trội về độ ổn định và độ tin cậy |

> ✅ Mô hình thể hiện khả năng **phân loại chính xác và tin cậy cao**, ngay cả khi dữ liệu huấn luyện hạn chế.

---

## 📊 Đóng góp chính

- **Xây dựng mô hình xác định BPA động** dựa trên trọng số Adaboost.  
- **Đề xuất phương pháp phủ định BPA** để giảm xung đột trong quá trình hợp nhất.  
- **Ứng dụng entropy niềm tin (Deng entropy)** để điều chỉnh trọng số hợp nhất.  
- **Thử nghiệm và chứng minh hiệu quả** trên tập dữ liệu thực tế với độ chính xác cao.

---

## 🧱 Cài đặt và chạy

### 1️⃣ Cài đặt môi trường
```bash
pip install -r requirements.txt
```

### 2️⃣ Mở notebook
```bash
jupyter notebook Main.ipynb
```

### 3️⃣ Chạy tuần tự từng cell để xem quá trình:
- Tiền xử lý dữ liệu  
- Huấn luyện Adaboost  
- Tính BPA  
- Kết hợp Dempster + Entropy  
- Phân tích kết quả

---

## 🧠 Ứng dụng tiềm năng

- Nhận dạng mẫu (Pattern Recognition)  
- Chẩn đoán lỗi kỹ thuật (Fault Diagnosis)  
- Phân tích rủi ro (Risk Analysis)  
- Phân loại dữ liệu phức tạp (Data Classification)

---

## 📚 Tài liệu tham khảo

1. Dempster, A.P. (1967). *Upper and Lower Probabilities Induced by a Multivalued Mapping.*  
2. Shafer, G. (1976). *A Mathematical Theory of Evidence.* Princeton University Press.  
3. Yager, R. (2014). *On the negation of probability distributions.*  
4. Yin et al. (2018). *Negation of Basic Probability Assignment in Dempster–Shafer Theory.*  
5. Wu et al. (2020). *Belief Entropy and Its Application in Evidence Theory.*

---

## 💬 Liên hệ

Nếu bạn muốn đóng góp, cải thiện hoặc sử dụng mô hình trong nghiên cứu khác, vui lòng tạo **issue** hoặc **pull request** tại repository.  

---

> 📈 **Kết luận:**  
> Mô hình kết hợp **Adaboost – BPA – Entropy Niềm Tin** là hướng tiếp cận hiệu quả cho bài toán phân loại trong môi trường dữ liệu không chắc chắn.  
> Nghiên cứu này góp phần mở rộng khả năng ứng dụng lý thuyết Dempster–Shafer trong trí tuệ nhân tạo và học máy hiện đại.
