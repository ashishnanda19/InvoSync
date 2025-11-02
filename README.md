# InvoSync

InvoSync is an AI-powered invoice and purchase order reconciliation system that uses **Tesseract OCR** and **RapidFuzz** to detect, extract, and compare data from scanned invoices and purchase orders. It automatically highlights mismatches, corrects inconsistencies, and exports clean, standardized results — saving hours of manual verification work.

---

## Features

- **OCR Extraction:** Reads invoice and purchase order data using [Tesseract OCR](https://github.com/tesseract-ocr/tesseract).  
- **Discrepancy Detection:** Automatically compares and corrects vendor, quantity, and pricing mismatches.  
- **Data Export:** Generates corrected CSV reports and discrepancy summaries.  
- **Modern Frontend:** Built using **React.js + Vite** for a fast and smooth UI.  
- **Seamless Backend Integration:** Flask backend for OCR, comparison, and API handling.  
- **Modular Architecture:** Clean separation of OCR, parsing, comparison, and export logic.  

---

## Tech Stack

| Layer | Technologies |
|-------|---------------|
| **Frontend** | React.js, Vite, TailwindCSS |
| **Backend** | Python, Flask |
| **OCR Engine** | Tesseract OCR |
| **Text Matching** | RapidFuzz |
| **Data Processing** | Pandas, Regex |
| **File Handling** | Pillow, pdf2image |

---

## Project Structure

```
InvoSync/
│
├── backend/
│   ├── app.py               # Flask app entry point
│   ├── compare.py           # Handles comparison between PO and invoice
│   ├── export.py            # Exports corrected data to CSV
│   ├── ocr.py               # OCR logic using Tesseract
│   ├── parse.py             # Parses extracted text into structured format
│   └── requirements.txt     # Backend dependencies
│
├── frontend/
│   ├── index.html
│   ├── package.json
│   ├── package-lock.json
│   └── src/
│       ├── App.jsx
│       ├── main.jsx
│       ├── components/
│       │   ├── HowItWorks.jsx
│       │   ├── Page.jsx
│       │   └── Shell.jsx
│       ├── lib/
│       │   └── api.js
│       └── pages/
│           ├── Dashboard.jsx
│           ├── Exports.jsx
│           ├── Login.jsx
│           ├── RecordDetail.jsx
│           ├── Records.jsx
│           ├── Review.jsx
│           ├── Settings.jsx
│           ├── Signup.jsx
│           └── Upload.jsx
│
└── README.md
```

---

## Architecture Diagram

```
     +---------------------+
     |  Frontend (React)   |
     |  ────────────────   |
     |  Upload Invoices     |
     |  View Discrepancies  |
     +----------+----------+
                |
                v
     +---------------------+
     |   Backend (Flask)   |
     |   ───────────────   |
     | OCR Extraction       |
     | Parsing & Comparison |
     | Export to CSV        |
     +----------+----------+
                |
                v
     +---------------------+
     |   Tesseract OCR     |
     |  Image → Text       |
     +---------------------+
```

---

## Setup & Deployment

### Backend Setup

```bash
cd backend
python -m venv venv
source venv/bin/activate      # (Windows: venv\Scriptsctivate)
pip install -r requirements.txt
python app.py
```

Backend runs on **http://localhost:5000**

---

### Frontend Setup

```bash
cd frontend
npm install
npm run dev
```

Frontend runs on **http://localhost:5173**

---

## How Tesseract OCR is Used

Tesseract OCR is an open-source engine developed by Google that extracts text from images and PDFs.  
In **InvoSync**, it’s used inside `backend/ocr.py` to process invoice and purchase order files.

**Pipeline:**
1. Preprocess image using `Pillow` and `ImageEnhance` for better clarity.  
2. Extract text via:
   ```python
   import pytesseract
   text = pytesseract.image_to_string(image)
   ```
3. Parse the extracted text into structured fields (item name, quantity, price, total).  
4. Compare extracted invoice and purchase order details using **RapidFuzz** for fuzzy string matching.

---

## Workflow

1. Upload `invoice.jpg` and `purchase_order.jpg` through the frontend.  
2. Backend extracts and parses data using **Tesseract OCR**.  
3. Mismatches (e.g., price/quantity/vendor) are identified.  
4. Corrected invoice and discrepancy report are exported as:
   - `corrected_invoice.csv`
   - `discrepancy_report.csv`

---

## Output Files

| File | Description |
|------|--------------|
| `corrected_invoice.csv` | Final corrected invoice after comparison |
| `discrepancy_report.csv` | Log of mismatches and corrections made |

---

## Contributors

**Developed by:**  
[**Ashish Kumar Nanda**](https://github.com/ashishnanda19)<br>
[**Kushagra Gupta**](https://github.com/kushagragupta04)<br>
[**Rashi Gupta**](https://github.com/Rashi228)<br>
[**Ridhi Pahuja**](https://github.com/ridz3)
  
 

---

If you find this project useful, please consider giving it a ⭐ on GitHub!
