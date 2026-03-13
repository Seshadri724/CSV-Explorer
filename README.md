# 📊 DataScope — Offline CSV Explorer & Visualizer

> Drop any CSV. Get instant column profiling, distribution charts, scatter plots, per-column stats, filter/sort, and filtered export. No code. No server. No API.

![React](https://img.shields.io/badge/React-18-61dafb?style=flat-square&logo=react)
![Recharts](https://img.shields.io/badge/Charts-Recharts-ff6b35?style=flat-square)
![Offline](https://img.shields.io/badge/Works-Offline-green?style=flat-square)

---

## What It Does

DataScope is a Bloomberg-terminal-style data tool for developers who need to quickly understand a CSV without writing pandas or opening Excel.

- **⊞ Table View** — sortable columns, per-column filters, paginated rows (50/page), NULL highlighting, type-coloured cells
- **◈ Column Profile** — full statistics per column: min/max/mean/median/stddev for numbers; top values + frequency bars for strings; fill-rate bar
- **▲ Charts** — auto-generated histogram (numeric) or frequency bar chart (string) for every column
- **⊕ Scatter Plot** — pick any two numeric columns; all other numeric pairs auto-render below
- **⬇ Export** — download currently filtered and sorted data as a new CSV

---

## Auto-Detection Features

| Feature | Detail |
|---|---|
| Delimiter | Auto-detects `,` `\t` `;` `\|` |
| Column Types | `number`, `string`, `date`, `boolean` inferred per column |
| NULL values | Empty cells highlighted as `NULL` in red |
| Quoted fields | Handles `"field with, comma"` correctly |

---

## Installation

### Prerequisites

- [Node.js](https://nodejs.org/) v16 or higher
- npm or yarn

### Steps

```bash
# 1. Clone the repository
git clone https://github.com/yourusername/datascope.git
cd datascope

# 2. Install dependencies
npm install

# 3. Install Recharts (charting library)
npm install recharts

# 4. Start the development server
npm start
```

Opens at `http://localhost:3000`

### Build for Production (Fully Offline)

```bash
npm run build
```

The `build/` folder is self-contained — works without any server.

---

## Project Structure

```
datascope/
├── src/
│   └── App.jsx          ← Main component (CSVExplorer)
├── public/
│   └── index.html
├── package.json
└── README.md
```

### Setting Up from Scratch

```bash
npx create-react-app datascope
cd datascope
npm install recharts
# Replace src/App.js with csv-explorer.jsx content
npm start
```

---

## How to Use

### Step 1 — Load Data

**Option A: Drag & Drop**
Drag any `.csv`, `.tsv`, or `.txt` file onto the upload zone on the landing page.

**Option B: Click to Browse**
Click the upload zone and select your file from the file picker.

**Option C: Sample Data**
Click **LOAD SAMPLE DATA →** to instantly load a 15-row employee dataset and explore all features.

---

### Step 2 — Explore

#### Table View (⊞)
- Click any **column header** to sort ascending; click again for descending
- Type in the **filter row** (second row) under any column to filter that column live
- Use the **search bar** (top right) to search across all columns simultaneously
- NULL cells appear in red — easy to spot missing data
- Pagination controls at the bottom: 50 rows per page

#### Column Profile (◈)
- Click any column name in the **left sidebar** to select it
- Switch to the Profile tab to see full statistics
- **Numeric columns** show: min, max, mean, median, std deviation, sum, unique count, null count
- **String columns** show: top 5 values with frequency bars, avg string length, unique count
- **Fill rate bar** shows what % of rows have a value

#### Charts (▲)
- All columns shown at once as auto-generated charts
- Click any chart panel to jump to that column's full profile

#### Scatter Plot (⊕)
- Select X axis and Y axis from numeric column dropdowns
- Up to 400 data points plotted (for performance)
- All other numeric column pairs auto-render below as mini scatter plots
- Click any mini plot to make it the main chart

#### Export (⬇ EXPORT button, top right)
- Downloads the currently filtered + sorted data as a CSV
- Filename prefixed with `filtered_`

---

## Column Type Legend

| Badge | Type | Colour |
|---|---|---|
| `#` | Number | Blue |
| `A` | String / Text | Green |
| `D` | Date | Purple |
| `B` | Boolean | Amber |
| `?` | Unknown | Grey |

---

## Supported File Formats

| Format | Extension | Notes |
|---|---|---|
| Comma-separated | `.csv` | Standard CSV |
| Tab-separated | `.tsv` | Auto-detected |
| Pipe-separated | `.txt` | Auto-detected |
| Semicolon-separated | `.csv` | Common in European locales |

Files with quoted fields (`"value with, comma"`) are handled correctly.

---

## Tech Stack

- **React 18** — UI framework
- **Recharts** — bar charts, scatter plots, area charts
- **Pure JavaScript** — CSV parsing, type inference, statistics (no pandas, no server)

---

## Performance Notes

- Scatter plots cap at 400 rows for render performance
- Frequency charts cap at 15 unique values
- Histograms use 12 bins by default
- Pagination at 50 rows keeps the table fast even for large files

---

## Privacy

- Everything runs in your browser — no data uploaded, no server, no cloud
- Safe for confidential business data, PII, internal reports

---

## License

MIT — free to use, modify, and distribute.
