# AI-Document-WorkBench
# GapGPT Document Workbench

**Client-Side PDF Analysis & Management Workbench powered by OpenAI-compatible APIs**

یک محیط تحت وب سبک و مستقل برای استخراج متن از چند فایل PDF، تقسیم اسناد حجیم به قطعات، ارسال مرحله‌ای محتوا برای تحلیل توسط مدل‌های زبانی و تولید گزارش نهایی ساختاریافته و قابل چاپ.

این پروژه با **HTML / CSS / JavaScript** ساخته شده و برای اجرای آن به Backend یا Node.js نیاز نیست.

---

## 🇮🇷 معرفی فارسی

**GapGPT Document Workbench** یک ابزار تحت وب برای تحلیل اسناد و تبدیل مجموعه‌ای از فایل‌های PDF به یک گزارش تحلیلی ساختاریافته است.

ایده اصلی پروژه این است که به‌جای ارسال مستقیم یک فایل PDF حجیم به مدل زبانی، متن اسناد ابتدا در مرورگر استخراج و به قطعات قابل مدیریت تقسیم شود. سپس هر قطعه به‌صورت جداگانه تحلیل شده و در نهایت بسته‌های شواهد حاصل از تمام قطعات برای تولید پاسخ نهایی در اختیار مدل قرار می‌گیرند.

### قابلیت‌ها

* 📄 انتخاب و بارگذاری هم‌زمان چند فایل PDF
* 🖱️ پشتیبانی از Drag & Drop
* استخراج متن PDF در خود مرورگر
* تقسیم اسناد حجیم به قطعات قابل مدیریت
* تعیین اندازه هر قطعه
* تعیین میزان هم‌پوشانی بین قطعات
* محدود کردن تعداد قطعات هر سند
* تحلیل مرحله‌ای اسناد
* ساخت «بسته شواهد» برای هر قطعه
* ترکیب شواهد و تولید پاسخ نهایی
* پشتیبانی از APIهای سازگار با OpenAI Chat Completions
* تنظیم Endpoint، مدل، Temperature و Max Tokens
* ذخیره تنظیمات در LocalStorage
* امکان استفاده از وب‌سایت شرکت یا پروژه به‌عنوان اطلاعات تکمیلی
* خروجی Markdown/HTML
* چاپ مستقیم گزارش
* ذخیره گزارش نهایی به‌صورت HTML
* کپی متن خروجی
* رابط کاربری فارسی و RTL
* طراحی مناسب برای چاپ A4
* بدون نیاز به Backend
* بدون نیاز به Node.js
* قابل اجرا روی GitHub Pages

---

## معماری پروژه

```text
PDF Files
    │
    ▼
Browser
    │
    ├── PDF.js
    │      │
    │      ▼
    │   Extract Text
    │
    ▼
Text Chunking
    │
    ├── Chunk 1 ──► LLM API
    ├── Chunk 2 ──► LLM API
    ├── Chunk 3 ──► LLM API
    └── ...
            │
            ▼
      Evidence Packets
            │
            ▼
      Final LLM Request
            │
            ▼
      Final Report
            │
      ┌─────┼─────┐
      ▼     ▼     ▼
    Print  HTML  Copy
```

---

## چرا پردازش مرحله‌ای؟

در پروژه‌های تحلیل اسناد، ارسال کل محتوای چند PDF در یک درخواست می‌تواند باعث افزایش شدید حجم ورودی شود.

این پروژه به‌جای آن، فرآیند را به دو مرحله تقسیم می‌کند:

### مرحله اول — تحلیل قطعات

هر سند به قطعات کوچک‌تر تقسیم شده و هر قطعه به‌صورت مستقل تحلیل می‌شود.

مدل برای هر قطعه اطلاعاتی مانند موارد زیر را استخراج می‌کند:

* نکات کلیدی
* افراد و سمت‌ها
* تاریخ‌ها
* تصمیم‌ها
* تعهدات
* ابهام‌ها
* اطلاعات موردنیاز
* ارتباط با درخواست اصلی کاربر

### مرحله دوم — تولید گزارش نهایی

خلاصه و شواهد استخراج‌شده از قطعات در اختیار مدل قرار می‌گیرد تا پاسخ نهایی تولید شود.

این روش برای مواردی مانند:

* صورتجلسات
* رزومه‌ها
* پروپوزال‌ها
* گزارش‌های مدیریتی
* اسناد سازمانی
* قراردادها
* مستندات پروژه
* فایل‌های PDF حجیم

کاربرد دارد.

---

# 🚀 اجرای پروژه

پروژه به‌صورت Client-Side طراحی شده و می‌تواند مستقیماً روی GitHub Pages اجرا شود.

### روش ساده

فایل HTML را در Repository قرار دهید:

```text
index.html
```

سپس GitHub Pages را برای Repository فعال کنید.

پس از فعال شدن Pages، پروژه از طریق آدرس GitHub Pages قابل دسترسی خواهد بود.

---

# ⚙️ تنظیمات API

پس از اجرای برنامه، وارد بخش:

**تنظیمات مدل و API**

شوید.

موارد زیر قابل تنظیم هستند:

```text
Endpoint
API Key
Model
Temperature
Max Tokens
```

پروژه برای APIهایی طراحی شده که ساختار درخواست آن‌ها با OpenAI Chat Completions سازگار باشد.

نمونه Endpoint:

```text
https://api.gapgpt.app/v1/chat/completions
```

---

# 📄 کار با PDF

در بخش «کارگاه تحلیل» می‌توانید چند PDF را انتخاب کنید یا فایل‌ها را Drag & Drop کنید.

فایل‌ها ابتدا توسط PDF.js در مرورگر پردازش می‌شوند.

ساختار کلی:

```text
PDF
 ↓
PDF.js
 ↓
Extracted Text
 ↓
Chunking
 ↓
LLM Analysis
```

> فایل PDF برای استخراج متن مستقیماً به API ارسال نمی‌شود؛ محتوای متنی استخراج‌شده برای تحلیل ارسال می‌شود.

---

# 🧩 تنظیم Chunking

سه پارامتر اصلی برای کنترل تقسیم اسناد وجود دارد:

### Chunk Size

حداکثر طول هر قطعه بر اساس تعداد کاراکتر.

### Overlap

مقداری از انتهای قطعه قبلی که در قطعه بعدی نیز تکرار می‌شود.

این قابلیت کمک می‌کند اطلاعاتی که در مرز بین دو قطعه قرار گرفته‌اند کمتر از دست بروند.

### Maximum Chunks

حداکثر تعداد قطعات قابل ایجاد برای هر سند.

---

# 🌐 اطلاعات وب‌سایت

امکان وارد کردن وب‌سایت شرکت یا پروژه نیز وجود دارد.

برای مثال:

```text
https://example.com
```

همچنین می‌توان از مدل خواست در صورت پشتیبانی Endpoint و امکان دسترسی، اطلاعات وب‌سایت را نیز در تحلیل لحاظ کند.

---

# 🖨️ خروجی

خروجی نهایی را می‌توان به چند شکل استفاده کرد:

### چاپ / PDF

گزارش با قالب مناسب چاپ A4 آماده می‌شود.

### HTML

گزارش کامل به‌صورت یک فایل HTML مستقل ذخیره می‌شود.

### Copy

متن نهایی در Clipboard کپی می‌شود.

---

# 🛠️ تکنولوژی‌ها

* HTML5
* CSS3
* Vanilla JavaScript
* PDF.js
* Fetch API
* LocalStorage
* OpenAI-compatible Chat Completion API
* GitHub Pages

این پروژه عمداً بدون Framework و بدون Backend نوشته شده است.

---

# 📁 ساختار ساده Repository

```text
gapgpt-document-workbench/
│
├── index.html
└── README.md
```

در نسخه‌های آینده می‌توان پروژه را به ساختار زیر توسعه داد:

```text
gapgpt-document-workbench/
│
├── index.html
│
├── css/
│   └── app.css
│
├── js/
│   ├── app.js
│   ├── pdf.js
│   ├── api.js
│   └── renderer.js
│
├── assets/
│
└── README.md
```

---

# 🇬🇧 English

## GapGPT Document Workbench

GapGPT Document Workbench is a lightweight, client-side web application for analyzing multiple PDF documents using OpenAI-compatible Large Language Model APIs.

The application extracts text from PDF files directly in the browser, splits large documents into manageable chunks, analyzes each chunk independently, combines the extracted evidence, and finally generates a structured report.

No backend server or Node.js runtime is required.

---

## Features

* Multiple PDF file support
* Drag & Drop upload
* Client-side PDF text extraction
* Configurable text chunking
* Configurable chunk overlap
* Maximum chunks per document
* Multi-stage document analysis
* Evidence packet generation
* Final report generation
* OpenAI-compatible API support
* Custom API endpoint
* Custom model selection
* Temperature control
* Max token configuration
* LocalStorage settings
* Optional website/project information
* Markdown-to-HTML rendering
* Printable A4 reports
* HTML report export
* Clipboard copy
* Persian RTL interface
* GitHub Pages compatible
* No backend required
* No Node.js required

---

## How It Works

The application uses a two-stage analysis pipeline.

### Stage 1 — Document Analysis

Each PDF is converted to text in the browser and divided into configurable chunks.

Each chunk is sent to the selected language model and converted into a structured evidence packet.

```text
PDF
 ↓
PDF.js
 ↓
Text Extraction
 ↓
Chunking
 ↓
LLM
 ↓
Evidence Packet
```

### Stage 2 — Final Generation

The evidence packets are combined and sent to the model together with the original user request.

```text
Evidence Packets
        ↓
Final Prompt
        ↓
LLM
        ↓
Structured Report
```

This approach is particularly useful for large collections of:

* Meeting transcripts
* Resumes
* Proposals
* Contracts
* Business documents
* Project documentation
* Management reports
* Organizational documents

---

## Browser-Based Architecture

The application is intentionally designed as a client-side tool.

```text
User Browser
     │
     ├── HTML / CSS
     ├── JavaScript
     ├── PDF.js
     └── Fetch API
             │
             ▼
      OpenAI-Compatible API
```

No application server is required.

---

## GitHub Pages

The application can be deployed directly to GitHub Pages.

A minimal repository can contain:

```text
index.html
README.md
```

After enabling GitHub Pages, the application can be accessed directly through the generated Pages URL.

---

## API Compatibility

The application expects an API compatible with the Chat Completions style interface.

Example:

```text
POST /v1/chat/completions
```

The application sends messages in the following general structure:

```json
{
  "model": "gpt-4o",
  "messages": [
    {
      "role": "system",
      "content": "..."
    },
    {
      "role": "user",
      "content": "..."
    }
  ],
  "temperature": 0.2,
  "max_tokens": 5000
}
```

---

## Configuration

The following parameters can be configured from the UI:

| Setting     | Description                           |
| ----------- | ------------------------------------- |
| Endpoint    | API endpoint                          |
| API Key     | Authentication key                    |
| Model       | Language model                        |
| Temperature | Response randomness                   |
| Max Tokens  | Maximum output size                   |
| Chunk Size  | Maximum characters per chunk          |
| Overlap     | Overlapping characters between chunks |
| Max Chunks  | Maximum chunks per document           |

---

## PDF Processing

PDF files are processed locally in the browser using PDF.js.

The general workflow is:

```text
PDF File
   ↓
PDF.js
   ↓
Extract Text
   ↓
Chunk Text
   ↓
Analyze Chunks
```

The original PDF file itself is not directly sent to the LLM endpoint by the application.

---

## Output

Generated reports can be:

* Printed
* Saved as HTML
* Converted to PDF through the browser print dialog
* Copied to the clipboard

The report layout is optimized for A4 printing.

---

## Technology Stack

```text
HTML5
CSS3
Vanilla JavaScript
PDF.js
Fetch API
LocalStorage
OpenAI-compatible APIs
GitHub Pages
```

No framework is required.

---

## Project Status

**Status: Experimental / Functional Prototype**

The project is designed as a practical document-analysis workbench and can be extended with additional processing modules.

Potential future features include:

* OCR for scanned PDFs
* Persistent project files
* Conversation history
* Document indexing
* More advanced Markdown rendering
* Table rendering
* Multi-model workflows
* Parallel chunk processing
* Retry and rate-limit handling
* Export to DOCX
* Export to PDF
* Local Python proxy
* Offline document preprocessing
* Speech-to-text integration
* Structured JSON output
* Custom analysis pipelines

---

## License

Choose a license appropriate for your intended use before publishing the project publicly.

For example:

```text
MIT License
```

if you want others to freely use, modify, and redistribute the project under the MIT terms.

---

## Author

**GapGPT Document Workbench**

A lightweight experiment in browser-based document analysis, LLM orchestration, and structured report generation.

