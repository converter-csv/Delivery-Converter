# ☕ Thong Kee · Food Platform Report Converter

A browser-based tool to process and convert food delivery platform transaction reports into a copy-paste ready format for Google Sheets. Supports **GrabFood**, **ShopeeFood**, and **FoodPanda**.

> Runs entirely in your browser — no data is uploaded anywhere.

---

## 📋 Features

### GrabFood
- Filters out **Cancelled** orders automatically
- Classifies orders: Short Order ID ending in **`T`** = Self Pick, otherwise Delivery
- Groups by **Updated Date**
- Extracts:
  - Order Count + Amount (Delivery & Self Pick)
  - Merchant-Funded Discount (daily total)
  - Refund rows (`Deduction - Eater Compensation`) — row by row with Order ID
  - Compensation rows (`Compensation - Orders`) — row by row with Order ID

### ShopeeFood
- Supports **all outlets in one file** — auto-detects and separates by store name
- Separate **Adjustment file** for refunds and compensations
- Groups by **Order Create Time**
- Extracts:
  - Order Count + Amount (Delivery & Self Pick)
  - Item Voucher Subsidy + Shipping Voucher Subsidy + Flash Sale Subsidy (3 columns)
  - Refund rows (`ShopeeFood_Adjustment_Deduct`) — row by row with Order ID
  - Compensation rows (`ShopeeFood_Adjustment_Add`) — row by row with Order ID

### FoodPanda
- Supports **all outlets in one file** — auto-detects and separates by outlet name
- Filters out **Customer Cancelled** orders automatically
- Classifies: `FOODPANDA` = Delivery, `SELFPICKED` = Self Pick
- Extracts:
  - Order Count + Amount (`Products Value Paid By Customer`)
  - Voucher Paid By Vendor + Discount Paid By Vendor (2 columns)

---

## 🚀 How to Use

1. **Download** `thongkee-converter.html`
2. **Open** it in any browser (Chrome, Edge, Firefox)
3. **Select** the platform tab (GrabFood / ShopeeFood / FoodPanda)
4. **Drop** your exported file(s) into the drop zone
5. For ShopeeFood, drop both the **Settlement** and **Adjustment** files
6. For ShopeeFood and FoodPanda, **select the outlet** from the buttons that appear
7. Click a **Copy button** and paste directly into your Google Sheet

---

## 📁 Supported File Formats

| Platform | File | Format |
|---|---|---|
| GrabFood | Transaction export | `.xlsx` `.xls` `.csv` |
| ShopeeFood | Settlement Report | `.xlsx` `.xls` `.csv` |
| ShopeeFood | Adjustment Report | `.xlsx` `.xls` `.csv` |
| FoodPanda | Transaction export (`Appendix A`) | `.xlsx` `.xls` `.csv` |

---

## ⎘ Copy Buttons

Each platform provides ready-to-paste copy buttons:

| Button | Content | Paste Into |
|---|---|---|
| **Copy Orders** | Count + Amount, interleaved Delivery then Self Pick per day | First Delivery Order Count cell |
| **Copy Discount / Subsidy** | Daily totals, Delivery row only | Discount / Subsidy column |
| **Copy Refund** | Amount + Order ID, date-aware, row by row | Refund amount cell (add rows first) |
| **Copy Compensation** | Amount + Order ID, date-aware, row by row | Compensation amount cell (add rows first) |

> **Tip:** For Refund and Compensation, manually add the extra rows in your Google Sheet first, then paste. The data is date-aware and automatically skips Self Pick rows so alignment is correct.

---

## 🏪 Outlet Mapping

| Outlet | ShopeeFood Store Name | FoodPanda Outlet Name |
|---|---|---|
| Connaught | Taman Connaught | Thong Kee Cafe (Taman Connaught) |
| Puchong | Puchong Square | Thong Kee Cafe (Puchong) |
| Klang | Klang Bukit Raja | Thong Kee Cafe (Klang) |
| Kepong | Kepong Baru | Thong Kee Cafe (Kepong) |
| Sri Petaling | Sri Petaling | Thong Kee Cafe (Sri Petaling) |
| Ara Damansara | Ara Damansara | Thong Kee Cafe (Ara Damansara) |
| Pandan Indah | Pandan Indah | Thong Kee Cafe (Pandan Indah) |
| Sungei Wang | Sungei Wang | Thong Kee Cafe (Sungei Wang) |
| TSLAW | TSLAW Tower | Thong Kee Cafe (TSLAW) |
| Glenmarie | Glenmarie | Thong Kee Cafe (Glenmarie) |
| Sea Park | Sea Park | Thong Kee Cafe (Sea Park) |
| Setapak | Setapak | Thong Kee Cafe (Setapak) |

---

## 🔒 Privacy

All processing happens **locally in your browser**. No files, data, or credentials are sent to any server.

---

## 🛠️ Built With

- Vanilla HTML + CSS + JavaScript
- [SheetJS (xlsx)](https://sheetjs.com/) for Excel file parsing

---

*Built for Thong Kee Cafe internal use.*
