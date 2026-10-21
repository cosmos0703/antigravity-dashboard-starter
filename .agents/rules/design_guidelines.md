# Google Cloud Dashboard Design Guidelines & Rules

## 1. Color Palette (Google Cloud Enterprise Palette)
- **Primary Brand / Accent**: `#1a73e8` (Google Blue)
- **Primary Dark / Hover**: `#1557b0`
- **Background**: `#f8f9fa` (Light Gray surface)
- **Card / Container Background**: `#ffffff` (Pure White)
- **Text Primary**: `#202124` (High-contrast dark gray)
- **Text Secondary / Muted**: `#5f6368` (Medium gray)
- **Border / Divider**: `#dadce0` (Light gray border)

### Semantic & Status Colors
- **Success / Positive Growth**: `#34a853` (Google Green)
- **Warning / Attention (CS 해결률 80% 미만)**: `#f9ab00` / `#ea4335` (Amber / Red Pill Badge)
- **Critical / Danger**: `#ea4335` (Google Red)
- **Department Chart Colors**:
  - Sales: `#1a73e8` (Blue)
  - Marketing: `#a142f4` (Purple)
  - Engineering: `#34a853` (Green)
  - Support: `#f9ab00` (Amber)
  - Operations: `#ea4335` (Coral/Red)

---

## 2. Layout & Typography Hierarchy
- **Font Stack**: Google Sans, Roboto, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif.
- **Top Bar**: Sticky top navigation with Dashboard Title, Last Updated timestamp, and Department Dropdown Filter.
- **KPI Cards Section**:
  - 4 core KPI summary cards side-by-side (Total Revenue, Total Expense, Net Profit, Average CS Resolution Rate).
  - Prominent metric value (28px - 32px, bold) with trend indicator badge.
- **Chart Section**:
  - Monthly & Departmental Revenue vs. Expense Trend Chart (Line / Grouped Bar).
  - Department Expense Breakdown Chart (Donut Chart).
- **Data Table Section**:
  - Customer Support ticket status table with pagination or scroll.
  - Rows with CS resolution rate `< 80%` MUST display a high-visibility warning badge (`<span class="badge warning">Warning (< 80%)</span>`).

---

## 3. Data Integrity & Edge Case Defensive Coding
- **Zero Division Defense**:
  - The `Engineering` department has `revenue = 0.0` across all records.
  - When calculating profit margin, growth rate, or ROI (`(revenue - expense) / revenue`), ensure division by zero is guarded (e.g. return `0%`, `N/A`, or calculate margin against expenses).
- **Missing Value (NaN / Null) Handling**:
  - Handle potential empty strings or null values in numerical fields gracefully by defaulting to `0` or forward-filling.
- **Responsive & Clean UI**:
  - Clean card borders (`border: 1px solid #dadce0; border-radius: 8px;`).
  - Subtle box shadow on cards (`box-shadow: 0 1px 3px rgba(60,64,67,0.1);`).
