# Konverter Bankovnih Izvoda — Bank Statement Converter

A privacy-first, browser-based tool that converts PDF bank statements into clean, structured CSV or Excel files — with support for merging multiple statements into one unified export.

No server. No uploads. No account. Everything runs locally in your browser.

---

## Features

### Multi-File Support
- Drag and drop **multiple PDFs at once** onto the upload zone
- Add more files at any time — drop additional PDFs on top of already selected ones
- Each file appears in a list with its name, size, and processing status
- Remove individual files with a single click before or after parsing

### Merge & Sort
- Transactions from all uploaded statements are **merged into a single output**
- Automatically **sorted by date** (oldest to newest) across all files
- A **Source column** (Fajl / File / Файл) shows which PDF each transaction came from — useful when combining statements from multiple banks or periods

### Export Options
- **CSV** — semicolon-separated, decimal comma format, ready for European Excel locales; includes BOM for correct encoding
- **Excel (.xlsx)** — proper number formatting, frozen header row, auto-fitted column widths, separate columns for debit/credit

### Transaction Parsing
- Extracts: Date, Description, Amount, Debit, Credit, Running Balance, Source file
- Handles multiple date formats: `DD.MM.YYYY`, `DD/MM/YYYY`, `YYYY-MM-DD`, and month-name formats
- Reconstructs multi-line descriptions that span across lines in the PDF
- Works with text-based PDFs from most major banks

### Privacy & Security
- **100% client-side** — your financial data never leaves your device
- No backend, no analytics, no cookies
- Works offline once the page is loaded

### Multilingual UI
- Full interface in **Serbian**, **English**, and **Russian**
- All status messages, column headers, and export filenames adapt to the selected language

### UX Details
- Drag-and-drop with visual feedback
- Per-file processing status: Pending → Processing → X transactions found / Error
- Progress bar during extraction
- Demo data mode to explore the interface without a real PDF
- Responsive layout — works on mobile

---

## How to Use

### Single Statement
1. Open `bank-converter.html` in any modern browser
2. Drag your PDF onto the drop zone, or click to browse
3. Click **Extract Transactions**
4. Download as CSV or Excel

### Multiple Statements (Merge)
1. Drag **all PDFs at once** onto the drop zone (or drop them one by one — they accumulate)
2. Review the file list; remove any unwanted files with the × button
3. Click **Extract Transactions**
4. All transactions are merged, sorted by date, and shown in one table with a Source column
5. Download the combined result as CSV or Excel

### Test with Sample Data
Open `generate-test-pdfs.html` to download two pre-built sample statements (Raiffeisen Bank March 2026, Banca Intesa April 2026) and use them to test the merge feature.

---

## Supported PDF Types

| Type | Supported |
|------|-----------|
| Text-based PDFs (digital bank statements) | ✅ |
| Scanned / image PDFs | ❌ |
| Password-protected PDFs | ❌ |

Most online banking portals generate text-based PDFs. If your PDF opens in a viewer and you can select/copy the text, it will work.

---

## Output Columns

| Column | Description |
|--------|-------------|
| Date | Transaction date, normalized to `YYYY-MM-DD` |
| File | Source PDF filename (without extension) |
| Description | Merchant or transaction description |
| Amount | Signed amount (`+` credit, `−` debit) |
| Debit | Debit amount (positive value) |
| Credit | Credit amount (positive value) |
| Balance | Running account balance |

---

## Tech Stack

- **PDF.js** — PDF parsing and text extraction
- **SheetJS (xlsx)** — Excel file generation
- **jsPDF** — sample PDF generation (test generator only)
- Zero build tools, zero dependencies to install — single HTML file

---

## Local Development

The repo includes a lightweight PowerShell static file server for local testing:

```powershell
cd bank-converter
powershell -ExecutionPolicy Bypass -File serve.ps1
# Open http://localhost:3000
```

---

## License

MIT — free to use, modify, and distribute.
