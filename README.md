
# پروژه فاین‌تیون و مقایسه مدل‌های ParsBERT و XLM-RoBERTa روی مجموعه داده SnappFood
### Fine-Tuning and Comparison of ParsBERT and XLM-RoBERTa on SnappFood Sentiment Dataset

این پروژه به صورت تخصصی به پیاده‌سازی، فاین‌تیون و مقایسه عملکرد دو مدل ترنسفورمر قدرتمند یعنی **ParsBERT** (بومی فارسی) و **XLM-RoBERTa** (چندزبانه) برای کار تحلیل احساسات نظرات فارسی کاربران اسنپ‌فود می‌پردازد.

This project implements, fine-tunes, and evaluates two state-of-the-art Transformer models, **ParsBERT** (monolingual Persian) and **XLM-RoBERTa** (multilingual), on the Persian SnappFood dataset for binary sentiment classification.

---

## 📊 مشخصات مجموعه داده / Dataset Details
ما از مجموعه داده رسمی **ParsiAI/snappfood-sentiment-analysis** موجود در Hugging Face استفاده می‌کنیم:
- **ستون ورودی:** `comment` (نظرات کاربران به زبان فارسی)
- **ستون هدف:** `label_id` (شناسه برچسب احساس به صورت صفر و یک برای منفی و مثبت)

We utilize the official **ParsiAI/snappfood-sentiment-analysis** dataset from Hugging Face:
- **Input Column:** `comment` (Persian user reviews)
- **Target Column:** `label_id` (Binary sentiment identifier: 0 for negative, 1 for positive)

---

## ⚙️ هایپرپارامترهای آموزشی / Training Hyperparameters
جهت اطمینان از صحت و عدالت در فرآیند مقایسه (Fair Comparison)، تمامی هایپرپارامترهای آموزشی برای هر دو مدل کاملاً یکسان انتخاب شده‌اند:

To ensure a strictly fair comparison, training configurations are kept identical for both runs:

| Parameter (پارامتر) | Value (مقدار) |
| :--- | :--- |
| **Model Architectures** | `HooshvareLab/bert-fa-base-uncased` & `xlm-roberta-base` |
| **Max Sequence Length** | 128 |
| **Batch Size (Train/Eval)** | 16 |
| **Learning Rate** | 2e-5 |
| **Epochs** | 3 |
| **Weight Decay** | 0.01 |
| **Metric for Best Model** | Accuracy |

---

## 🛠️ ساختار و نحوه اجرا / Implementation & Execution
پروژه در قالب یک فایل نوتبوک سازمان‌دهی شده است که مراحل آن به شرح زیر است:

1. **نصب وابستگی‌ها (Installation):** نصب کتابخانه‌های مورد نیاز نظیر `transformers`، `datasets`، `evaluate` و `accelerate`.
2. **پیش‌پردازش داده‌ها (Data Preprocessing):** توکنایز کردن دقیق متون و تبدیل صریح کلاس‌های متنی یا عددی به تنسورهای صحیح مناسب مدل.
3. **آموزش مدل ParsBERT (ParsBERT Training):** فاین‌تیون مدل بر روی دادهای آموزشی و ارزیابی در پایان هر اپوک.
4. **آموزش مدل XLM-RoBERTa (XLM-RoBERTa Training):** بارگذاری نسخه چندزبانه رابرتا و تکرار فرآیند فاین‌تیون.
5. **مقایسه نهایی (Evaluation & Comparison):** ارزیابی نهایی هر دو مدل روی داده‌های تست پیش‌بینی‌نشده (`test split`) و نمایش درصد دقت (Accuracy) به صورت مستقیم.

### Run Steps:
- Clone the repository / Open the notebook in Google Colab.
- Run the setup cell to install requirements.
- Execute the cells sequentially to preprocess, train, and test both models.

---

## 📄 لایسنس / License
این پروژه تحت لایسنس **MIT** به صورت کاملاً متن‌باز منتشر شده است.
This project is licensed under the **MIT License** and is open to contributions.
