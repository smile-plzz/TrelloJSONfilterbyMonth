

# 🗂️ Trello JSON Date Filter

A **standalone, browser-based Trello JSON analyzer** that helps you filter cards, actions, and comments by a **single month** or a **custom date range** — no server required.
Upload your Trello board export, choose a month or date window, and instantly get:

* Filtered lists of cards or actions.
* Full comment details.
* Range-based summary reports.
* Interactive bar charts.
* One-click CSV and PDF exports.

All processing happens **locally in your browser** — no data ever leaves your computer.

---

## 🚀 Features

### 🔍 Core Filters

* **Cards** – Filter by creation date, due date, or last activity.
* **Actions** – Filter all activity, including comments, by month or custom range.
* **Comment Extraction** – Include comment text (`commentCard`) for qualitative analysis.
* **Time Range Modes** – Toggle between quick month/year selection and precise start/end dates.

### 📊 Reporting

* **Activity Report** (for Actions)

  * KPIs: total actions, comments, card creations, checklist ops, etc.
  * Summaries: actions by type, member, and day.
* **Charts**

  * Bar charts for **Actions by Type**, **Member**, and **Day**.
  * Adjustable top-member limit.
  * Download charts as PNGs.

### 📄 Exports

* **Filtered JSON** – Save filtered results.
* **CSV Reports**

  * All actions (with comment text)
  * Comments only
  * By type, member, or day
* **PDF Reports**

  * Combines KPIs, charts, and tables into a print-ready report.
  * Auto-opens “Save as PDF” dialog.

### 🧪 Built-in Self Tests

A “Run tests” button verifies core functionality:

* Date range validation
* Comment inclusion logic
* Fallback printing when pop-ups are blocked

---

## 🧩 How It Works

1. Export your Trello board:

   * Open your board → **Menu → More → Print and export → Export as JSON**
2. Open `index.html` in any modern browser.
3. Upload the JSON file or paste the contents.
4. Choose:

   * **Year and Month** or switch to a **Custom Date Range**
   * **Target:** Cards or Actions
   * **Date Field:** Created, Due, or Last Activity (for cards)
   * (Optional) Filter by action types or comments only.
5. Click **Filter**.
6. Preview, analyze, or download your results:

   * JSON, CSV, or full PDF report.

---

## 🧱 Technical Overview

### Frontend

* Pure **HTML + CSS + JavaScript** — no dependencies.
* Runs entirely offline (using the File API and Blob URLs).

### Architecture

| Component                 | Responsibility                                               |
| ------------------------- | ------------------------------------------------------------ |
| `getActiveRange()`        | Normalizes month vs. custom range selections                 |
| `filterCardsInRange()`    | Filters cards by date range and date field                   |
| `filterActionsInRange()`  | Filters actions by type and date                             |
| `buildReport()`           | Generates KPI counts and grouped summaries                   |
| `renderReport()`          | Renders tables and enables CSV exports                       |
| `drawBarChart()`          | SVG-based bar chart renderer (no libraries)                  |
| `generatePdf()`           | Creates a self-contained HTML report and triggers print/save |
| `runTests()`              | Built-in unit tests (runs in-browser)                        |

### Data Handling

* `monthRange(year, month)` returns UTC start/end boundaries plus a printable label.
* Custom ranges use `parseDateInput()` and UTC math to include the entire end date.
* Comment text lives in `action.data.text`.
* Dates are normalized with `Date.UTC()` for consistent filtering.

---

## 🧪 Running the App

Simply open `index.html` in your browser:

```bash
# No dependencies required
open index.html
```

If testing locally via file:// protocol throws CORS issues for chart downloads (rare on Chromium browsers), you can use a lightweight static server:

```bash
python3 -m http.server 8080
# Then visit http://localhost:8080
```

---

## 🧠 Developer Notes

### Key Files

| File                   | Description                             |
| ---------------------- | --------------------------------------- |
| `index.html`           | Main application and all JS logic       |
| `README.md`            | This documentation                      |
| (optional) `style.css` | You can extract CSS for maintainability |

### Adding New Features

* To include new Trello action types, append to the `POP_TYPES` array.
* To add more KPIs or visualizations:

  * Extend `buildReport()` to count or group by new fields.
  * Add a new chart via `drawBarChart(svg, rows, labelKey, valueKey)`.

### Common Pitfalls

| Issue                                                 | Fix                                                                   |
| ----------------------------------------------------- | --------------------------------------------------------------------- |
| “Cannot read properties of null (reading 'document')” | Fixed by wrapping all code in `DOMContentLoaded`.                     |
| Pop-up blocker prevents PDF generation                | Falls back to iframe-based print method automatically.                |
| Large dataset slows preview                           | Disable “Preview all rows” toggle to limit preview to first 200 rows. |

---

## 📘 Test Cases

| Test                        | Description                                         |
| --------------------------- | --------------------------------------------------- |
| **monthRange()**            | Returns correct UTC start/end/label for given month |
| **createdFromId()**         | Extracts date from Trello card ID.                  |
| **filterActionsInRange()**  | Filters correctly by type and date.                 |
| **getActiveRange()**        | Validates custom start/end dates.                   |
| **generatePdf()**           | Falls back gracefully if pop-ups are blocked.       |

Run tests by clicking **Run tests** in the UI — results appear inline with ✅ / ❌ indicators.

---

## 📄 License

MIT License.
You are free to modify, distribute, and embed this app in your Trello analytics workflows.

---

## 👨‍💻 Author & Contributions

Created by **[Ismail Hossain]** – DevsNest Workspace
For issues, contributions, or enhancements:

* PRs and feedback welcome
* Built for real-world Trello reporting and automation needs


