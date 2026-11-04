# Deep Learning SGU 2026

Kho lưu trữ học tập cho môn Deep Learning tại SGU năm 2026. Đây là tập hợp
nhiều bài tập, notebook, dữ liệu, báo cáo và dự án độc lập; repository không
có một ứng dụng chung hay quy trình build duy nhất.

## Nội dung chính

- **Bài tập và lab:** tài liệu DOCX/PDF, notebook PyTorch và bản HTML xuất từ
  lab.
- **Titanic:** dữ liệu CSV, các notebook phân loại và những file submission
  đã lưu.
- **Function approximation:** dự án PyTorch MLP có script sinh dữ liệu, huấn
  luyện baseline và chạy các thí nghiệm A/B/C.
- **House Price:** dữ liệu, notebook thí nghiệm, mô hình và kết quả trong
  checkout nhóm.
- **Papers:** tài liệu tham khảo PDF theo chủ đề.
- **Archives:** các file ZIP gốc được giữ lại như bản chụp nộp bài; một số
  thành phần trong ZIP trùng với bản đã giải nén.

## Công nghệ

- Python và Jupyter Notebook.
- PyTorch, NumPy, pandas, Matplotlib, scikit-learn; một số notebook dùng thêm
  Weights & Biases (`wandb`) hoặc seaborn.
- Dự án Function Approximation có danh sách phụ thuộc riêng; xem
  [requirements.txt](<SGU26_DeepLearning_Group/BTL01_Function_Approximation/requirements.txt>).

## Yêu cầu và cài đặt

Nên dùng Python 3 và môi trường ảo riêng cho từng dự án. Không có
`requirements.txt` chung ở repository root vì các notebook có phụ thuộc khác
nhau.

Với dự án Function Approximation (Python 3.10 trở lên):

```powershell
Set-Location .\SGU26_DeepLearning_Group\BTL01_Function_Approximation
py -3.12 -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
```

Với các notebook Titanic/House Price, cài Jupyter và các thư viện được import
bởi notebook cần chạy (thường gồm `numpy`, `pandas`, `matplotlib`,
`scikit-learn`, `torch`; `wandb` và `seaborn` được một số notebook sử dụng).
Không cần cài mọi thư viện cho mọi bài. Notebook Titanic phiên bản s1 hiện
import `wandb`; cần cài thư viện này trước khi chạy toàn bộ notebook.

## Cách chạy

### Mở notebook

Từ repository root:

```powershell
jupyter lab
```

- Notebook Titanic s1 trong `notebooks/` đọc dữ liệu từ `titanic/` và hỗ trợ
  working directory là repository root hoặc `notebooks/`. File submission
  được ghi vào `notebooks/`.
- Notebook Titanic s2 được cấu hình theo Kaggle: đường dẫn dữ liệu mặc định là
  `/kaggle/input/competitions/titanic`, còn submission mặc định ghi vào
  `/kaggle/working`. Hãy điều chỉnh `params` trong notebook khi dùng môi trường
  khác.
- Notebook nằm trong `titanic/` dùng các CSV cùng thư mục; có thể mở/chạy từ
  thư mục đó.

### Function Approximation

Chạy các lệnh sau từ thư mục
`SGU26_DeepLearning_Group/BTL01_Function_Approximation/` với môi trường đã cài
`requirements.txt`:

```powershell
python train.py
python run_experiments_ab.py
python run_experiments_c.py
```

`python generate_data.py` tạo lại CSV và hình trong `data/` và `figures/`;
không chạy lệnh này nếu muốn giữ nguyên dữ liệu đã tạo. Các script thí nghiệm
có thể chạy lâu và ghi kết quả vào `results/`.

### House Price

Hai notebook thí nghiệm nằm trong
`SGU26_DeepLearning_Group/house_price/experiments/`. Kiểm tra cấu hình đường
dẫn và thư viện của notebook trước khi chạy; thư mục này hiện chưa có hướng
dẫn cài đặt hoặc manifest phụ thuộc riêng.

## Kiểm thử và cấu hình

Repository hiện không có bộ kiểm thử tự động hoặc lệnh build chung. Các notebook
có thể phụ thuộc vào working directory, dữ liệu cục bộ hoặc môi trường Kaggle.
Không bật W&B online nếu chưa cấu hình tài khoản và mục đích sử dụng; một số
notebook đang đặt chế độ disabled.

## Cấu trúc thư mục

```text
.
├── coursework/
│   ├── assignments/       # BT01–BT04
│   └── labs/              # lab01, lab02
├── notebooks/             # hai notebook Titanic ở cấp repository
├── titanic/               # CSV, notebook và submission đã lưu
├── papers/                # tài liệu tham khảo
├── archives/              # các ZIP gốc
└── SGU26_DeepLearning_Group/
    ├── BTL01_Function_Approximation/
    │   ├── data/ figures/ results/
    │   └── script Python và tài liệu dự án
    └── house_price/
        ├── data/ experiments/
        └── submissions/ reports/
```

## Ghi chú phát triển

- `SGU26_DeepLearning_Group/` là một Git checkout độc lập được giữ nguyên tại
  vị trí hiện tại; kiểm tra trạng thái Git riêng khi làm việc trong đó.
- Các thư mục `.venv/`, dữ liệu, checkpoint, submission và kết quả thí nghiệm
  là tài nguyên cục bộ hoặc đầu ra đã lưu; không xóa chúng như bước dọn dẹp.
- ZIP trong `archives/` được giữ nguyên dù có tệp trùng với bản đã giải nén.
- Các bài tập dùng tên file gốc để bảo toàn ngữ cảnh học tập và nộp bài.
