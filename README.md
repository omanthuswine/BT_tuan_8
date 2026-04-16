# Unsupervised Learning: Clustering & Optimization Analysis

[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Machine Learning](https://img.shields.io/badge/Focus-Machine%20Learning-orange.svg)]()
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

##  1. Giới thiệu Bài toán (Problem Definition)
Dự án tập trung vào việc nghiên cứu và triển khai các thuật toán **Học máy không giám sát (Unsupervised Learning)** để khám phá cấu trúc tiềm ẩn trong dữ liệu. 

> **Mục tiêu:** Phân nhóm các điểm dữ liệu $X = \{x_1, x_2, ..., x_n\}$ thành $K$ cụm sao cho độ tương đồng nội cụm là lớn nhất và độ tương đồng ngoại cụm là nhỏ nhất.

**Ứng dụng thực tế:** * Phân khúc khách hàng (Customer Segmentation).
* Nén dữ liệu và giảm nhiễu hình ảnh.
* Phân tích tổ chức sinh học/di truyền.

---

## 🛠 2. Phương pháp thực hiện (Methodology)

### 🔹 K-Means Clustering
Thuật toán phân cụm dựa trên khoảng cách. Mục tiêu là tối thiểu hóa tổng bình phương khoảng cách trong cụm (WCSS):
$$J = \sum_{i=1}^{k} \sum_{x \in C_i} \|x - \mu_i\|^2$$
*Trong đó $\mu_i$ là tâm của cụm $C_i$.*

### 🔹 Hierarchical Clustering
Xây dựng cấu trúc phân cấp dựa trên phương pháp **Agglomerative** (từ dưới lên).
* **Tiêu chí liên kết:** Ward Linkage (tối thiểu hóa phương sai), Complete, hoặc Average Linkage.
* **Công cụ:** Trực quan hóa qua **Dendrogram** để xác định số lượng cụm tối ưu mà không cần thử sai nhiều lần.

### 🔹 Expectation-Maximization (EM) Algorithm
Sử dụng cho các mô hình xác suất (như GMM). Thuật toán tối ưu hóa hàm **Log-Likelihood**:
$$\ln p(X|\theta) = \sum_{i=1}^{N} \ln \sum_{z} p(x_i, z|\theta)$$
* **E-Step:** Ước tính xác suất các biến ẩn (latent variables).
* **M-Step:** Cập nhật tham số $\theta$ (mean, covariance) để tối đa hóa hàm hợp lý.

---

## 3. Quy trình Triển khai (Pipeline)

| Bước | Hoạt động chính | Công cụ |
| :--- | :--- | :--- |
| **1** | **EDA & Preprocessing** | Pandas, Seaborn, StandardScaler |
| **2** | **Feature Engineering** | PCA (Giảm chiều), Encoding |
| **3** | **Model Selection** | Elbow Method, Silhouette Analysis |
| **4** | **Execution** | Scikit-learn, Scipy |

---

## 4. Kết quả & Đánh giá (Results)
* **Tối ưu hóa số cụm:** Sử dụng đường cong "Khuỷu tay" (Elbow Curve) để xác định điểm gãy khúc tối ưu cho $K$.
* **Độ chính xác phân cụm:** Được kiểm chứng qua **Silhouette Score** (giá trị càng gần 1, các cụm càng tách biệt rõ rệt).
* **Insight:** Kết quả cho phép định danh chính xác các nhóm đối tượng đặc thù (ví dụ: Khách hàng chi tiêu cao nhưng thu nhập thấp).

---
