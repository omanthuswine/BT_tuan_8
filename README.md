#Unsupervised Machine Learning: Advanced Clustering & EM Optimization

[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Machine Learning](https://img.shields.io/badge/Focus-Unsupervised%20Learning-orange.svg)]()
[![Scikit-Learn](https://img.shields.io/badge/Library-Scikit--Learn-green.svg)]()

## 1. Giới thiệu Bài toán (Problem Statement)
Dự án này tập trung vào việc giải quyết bài toán phân nhóm dữ liệu tự động mà không cần nhãn (Unsupervised Learning). Mục tiêu là xác định các cấu trúc tiềm ẩn, quy luật phân bổ và mối quan hệ giữa các thực thể dữ liệu.

**Trường hợp nghiên cứu cụ thể:**
* **Customer Segmentation:** Phân tích dữ liệu khách hàng dựa trên Thu nhập (Annual Income) và Điểm chi tiêu (Spending Score).
* **Data Structure Discovery:** Tự động tìm ra số lượng nhóm tối ưu trong các tập dữ liệu nhiễu.

---

## 2. Phân tích các Phương pháp (Methodology)

### 🔹 2.1. K-Means Clustering (Centroid-based)
Thuật toán phân cụm dựa trên việc tối thiểu hóa khoảng cách giữa các điểm dữ liệu và tâm cụm (Centroid).
* **Cơ chế:** Gán điểm dữ liệu vào cụm gần nhất $\rightarrow$ Cập nhật tâm cụm bằng trung bình cộng $\rightarrow$ Lặp lại cho đến khi hội tụ.
* **Tối ưu hóa $K$:** Sử dụng **Elbow Method**. Chúng ta quan sát sự thay đổi của **WCSS** (Within-Cluster Sum of Squares):
    $$WCSS = \sum_{C_i} \sum_{x \in C_i} ||x - \mu_i||^2$$



### 🔹 2.2. Hierarchical Clustering (Connectivity-based)
Xây dựng cấu trúc cây (Hierarchy) để phân loại dữ liệu.
* **Agglomerative (Bottom-up):** Bắt đầu bằng cách coi mỗi điểm là 1 cụm, sau đó gộp dần dựa trên tiêu chí **Linkage** (Ward, Complete, Average).
* **Dendrogram:** Biểu đồ hình cây cho phép ta hình dung toàn bộ quá trình gộp cụm và quyết định số lượng cụm bằng cách đặt một "ngưỡng cắt" (threshold).



### 🔹 2.3. Expectation-Maximization (EM) Algorithm
Một thuật toán lặp dùng để tìm ước lượng hợp lệ tối đa (Maximum Likelihood) của các tham số trong mô hình xác suất (như Gaussian Mixture Models - GMM).
* **E-Step (Expectation):** Tính toán xác suất (trách nhiệm) mà mỗi điểm dữ liệu thuộc về một cụm dựa trên các tham số hiện tại.
* **M-Step (Maximization):** Cập nhật các tham số (trung bình $\mu$, phương sai $\sigma^2$) để tối đa hóa hàm Likelihood.
* **Điểm mạnh:** Xử lý tốt dữ liệu bị thiếu và cho phép "Soft Clustering" (một điểm có xác suất thuộc về nhiều cụm).



---

## 3. Quy trình Triển khai (Pipeline)

### Bước 1: Tiền xử lý dữ liệu
* Xử lý giá trị Null và định dạng lại kiểu dữ liệu.
* **Feature Scaling:** Sử dụng `StandardScaler` để đưa dữ liệu về cùng một thang đo, tránh việc các tính năng có giá trị lớn (như Thu nhập) lấn át các tính năng nhỏ (như số lượng mua hàng).

### Bước 2: Tìm số cụm tối ưu
* Vẽ biểu đồ Elbow để tìm "điểm gãy".
* Phân tích **Silhouette Score** để đánh giá độ dày và khoảng cách giữa các cụm.

### Bước 3: Huấn luyện & Trực quan hóa
* Áp dụng đồng thời K-Means, Agglomerative Clustering và GMM.
* Sử dụng đồ thị Scatter Plot (2D/3D) để quan sát sự phân tách giữa các nhóm khách hàng.

---

## 4. So sánh Kỹ thuật (Comparison)

| Thuật toán | Loại phân cụm | Hình dạng cụm | Độ phức tạp |
| :--- | :--- | :--- | :--- |
| **K-Means** | Hard Clustering | Hình cầu (Spherical) | $O(n \cdot k \cdot i)$ |
| **Hierarchical**| Cấu trúc cây | Đa dạng tùy Linkage | $O(n^2 \log n)$ |
| **EM (GMM)** | Soft Clustering | Hình Ellipsoid | Cao |

---

## 5. Kết quả đạt được
* Phân tách thành công tập dữ liệu khách hàng thành các nhóm chiến lược:
    1.  **Cẩn trọng:** Thu nhập cao - Chi tiêu thấp.
    2.  **Mục tiêu:** Thu nhập thấp - Chi tiêu cao.
    3.  **Tiềm năng:** Thu nhập cao - Chi tiêu cao.
* Xác định được $K=5$ là con số tối ưu cho bài toán Segmentation thực tế.

---


---
*Phát triển và tổng hợp bởi [Nguyễn Minh Hiếu] - 2026*
