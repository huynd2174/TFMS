# TFMS - Trading and Financial Market System

## Giới thiệu

TFMS (Trading and Financial Market System) là một hệ thống phân tích và dự đoán thị trường chứng khoán sử dụng các phương pháp học máy và phân tích dữ liệu. Dự án này tích hợp nhiều kỹ thuật khác nhau để phân tích giá cổ phiếu, bao gồm mô hình dự đoán dựa trên học sâu (LSTM), học máy truyền thống (Random Forest), phân tích tương quan và phân tích tình cảm từ tin tức thị trường.

Hệ thống được thiết kế để hỗ trợ các nhà đầu tư và nhà phân tích tài chính trong việc đưa ra quyết định dựa trên dữ liệu, bằng cách cung cấp các công cụ dự đoán và phân tích đa chiều về thị trường chứng khoán.

## Cấu trúc dự án

Dự án bao gồm các thành phần chính sau:

- **Dữ liệu cổ phiếu**: Các file CSV chứa dữ liệu lịch sử giá cổ phiếu của các công ty công nghệ lớn (AAPL, AMZN, GOOG, MSFT, TSLA)
- **Mô hình dự đoán**: Các notebook Jupyter triển khai các mô hình dự đoán khác nhau
- **Phân tích tương quan**: Công cụ phân tích mối quan hệ giữa các phương pháp dự đoán và giá thực tế
- **Phân tích tình cảm**: Hệ thống phân tích tình cảm từ tin tức thị trường liên quan đến các cổ phiếu

### Cấu trúc file

```
TFMS/
├── AAPL.csv              # Dữ liệu lịch sử cổ phiếu Apple
├── AMZN.csv              # Dữ liệu lịch sử cổ phiếu Amazon
├── GOOG.csv              # Dữ liệu lịch sử cổ phiếu Google
├── MSFT.csv              # Dữ liệu lịch sử cổ phiếu Microsoft
├── TSLA.csv              # Dữ liệu lịch sử cổ phiếu Tesla
├── LSTM_.ipynb           # Mô hình dự đoán sử dụng LSTM
├── RFR__.ipynb           # Mô hình dự đoán sử dụng Random Forest
├── SA_.ipynb             # Phân tích tình cảm từ tin tức
└── correlation_analysis.ipynb  # Phân tích tương quan giữa các phương pháp
```

## Tính năng chính

### 1. Dự đoán giá cổ phiếu sử dụng LSTM

Mô hình LSTM (Long Short-Term Memory) được triển khai để dự đoán giá cổ phiếu dựa trên dữ liệu lịch sử. Quá trình này bao gồm:

- Chuẩn hóa dữ liệu sử dụng MinMaxScaler
- Tạo chuỗi dữ liệu với độ dài lookback để học các mẫu thời gian
- Xây dựng và huấn luyện mô hình LSTM với các tham số tối ưu
- Đánh giá hiệu suất mô hình sử dụng R-squared và trực quan hóa kết quả

### 2. Dự đoán giá cổ phiếu sử dụng Random Forest

Mô hình Random Forest Regressor được sử dụng như một phương pháp thay thế để dự đoán giá cổ phiếu:

- Xử lý và chuẩn bị dữ liệu đầu vào
- Tạo các tính năng từ dữ liệu lịch sử
- Huấn luyện mô hình Random Forest với tối ưu hóa siêu tham số
- So sánh kết quả dự đoán với giá thực tế

### 3. Phân tích tình cảm từ tin tức thị trường

Hệ thống phân tích tình cảm (Sentiment Analysis) được triển khai để đánh giá tác động của tin tức đến thị trường:

- Thu thập tin tức liên quan đến các công ty cổ phiếu thông qua NewsAPI
- Phân tích tình cảm của các tiêu đề tin tức sử dụng TextBlob
- Phân loại tin tức thành tích cực, tiêu cực hoặc trung tính
- Tính điểm tình cảm tổng hợp để đánh giá xu hướng thị trường

### 4. Phân tích tương quan

Công cụ phân tích tương quan giúp đánh giá hiệu quả của các phương pháp dự đoán:

- So sánh kết quả dự đoán từ LSTM, Random Forest và phân tích tình cảm
- Tính toán hệ số tương quan giữa các phương pháp và giá thực tế
- Trực quan hóa mối quan hệ thông qua biểu đồ scatter plot
- Đánh giá phương pháp nào có độ chính xác cao nhất

## Cài đặt và sử dụng

### Yêu cầu hệ thống

- Python 3.6+
- Jupyter Notebook
- Các thư viện: pandas, numpy, matplotlib, seaborn, scikit-learn, keras, tensorflow, textblob, newsapi-python

### Cài đặt thư viện

```bash
pip install pandas numpy matplotlib seaborn scikit-learn keras tensorflow textblob newsapi-python
```

### Sử dụng

1. Clone repository về máy:
```bash
git clone https://github.com/huynd2174/TFMS.git
cd TFMS
```

2. Mở và chạy các notebook Jupyter:
```bash
jupyter notebook
```

3. Chạy từng notebook theo thứ tự sau để có kết quả tốt nhất:
   - `correlation_analysis.ipynb` - Để hiểu tổng quan về dữ liệu
   - `LSTM_.ipynb` - Để xây dựng và đánh giá mô hình LSTM
   - `RFR__.ipynb` - Để xây dựng và đánh giá mô hình Random Forest
   - `SA_.ipynb` - Để thực hiện phân tích tình cảm từ tin tức

## Phương pháp và kỹ thuật

### Xử lý dữ liệu

- **Chuẩn hóa dữ liệu**: Sử dụng MinMaxScaler để đưa dữ liệu về khoảng [0,1]
- **Tạo chuỗi thời gian**: Chuyển đổi dữ liệu thành chuỗi có độ dài lookback để phát hiện mẫu
- **Chia tập dữ liệu**: Phân chia dữ liệu thành tập huấn luyện và tập kiểm tra

### Mô hình LSTM

- Mô hình LSTM được xây dựng với 2 lớp LSTM (50 đơn vị) và 1 lớp Dense
- Sử dụng hàm tối ưu Adam và hàm mất mát mean_squared_error
- Huấn luyện trong 100 epochs với batch_size=32
- Đánh giá bằng R-squared để đo lường độ chính xác

### Mô hình Random Forest

- Sử dụng RandomForestRegressor từ scikit-learn
- Tối ưu hóa siêu tham số thông qua GridSearchCV
- Đánh giá bằng mean_squared_error và R-squared

### Phân tích tình cảm

- Sử dụng NewsAPI để thu thập tin tức liên quan đến cổ phiếu
- Áp dụng TextBlob để phân tích tình cảm của tiêu đề tin tức
- Phân loại tình cảm dựa trên giá trị polarity

### Phân tích tương quan

- Tính toán hệ số tương quan Pearson giữa các phương pháp dự đoán và giá thực tế
- Trực quan hóa mối quan hệ bằng scatter plot
- So sánh hiệu suất của các phương pháp khác nhau

## Kết luận

TFMS cung cấp một bộ công cụ toàn diện để phân tích và dự đoán thị trường chứng khoán, kết hợp nhiều phương pháp khác nhau để đạt được cái nhìn đa chiều về thị trường. Hệ thống này có thể được sử dụng bởi các nhà đầu tư, nhà phân tích tài chính, hoặc bất kỳ ai quan tâm đến việc dự đoán xu hướng thị trường chứng khoán dựa trên dữ liệu lịch sử và phân tích tin tức.

## Tác giả

- [huynd2174](https://github.com/huynd2174)

