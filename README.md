# Urban Development Planning Using Census Data

> **Data Science Project** | University of Hull  
> Analysing mock census data to guide infrastructure investment decisions for a mid-sized UK town

---

## 📌 Project Overview

This project simulates a **local government data science task**: given a mock census of a fictional UK town (sandwiched between two metropolitan areas), the goal was to clean, analyse, and derive actionable recommendations on:

- **(a) What to build** on an unoccupied plot of land
- **(b) Where to invest** public funding

The dataset was generated using the **Faker** package, modelled on the 1881 UK Census format, covering 11 demographic fields across thousands of residents.

---

## 🗂️ Dataset

| Field | Description |
|-------|-------------|
| House Number / Street | Residential address |
| Name | First name, Surname |
| Age | Resident age |
| Relationship to Head of House | Family/lodger/visitor role |
| Marital Status | Single, Married, Divorced, Widowed |
| Gender | Male, Female |
| Occupation | Modern-style occupations |
| Infirmity | Health conditions |
| Religion | Multi-faith representation |

---

## 🧹 Data Cleaning

Each column was inspected and cleaned systematically with documented rationale:

- **House Number** — Converted text entries (e.g. `"two"`) to numeric; removed invalid rows
- **Names** — Missing first names marked `Undetermined`; missing surnames inferred from household context (e.g. assigning shared family surname based on co-residents)
- **Age** — Word entries (e.g. `"twenty eight"`) converted to integers; missing ages estimated from household context
- **Marital Status** — Standardised abbreviations (`M → Married`); corrected logically impossible entries (e.g. under-18 divorcees reassigned to `Single`)
- **Occupation** — Individuals aged 66+ recorded as `Unemployed` reassigned to `Retired`; blank entries inferred from household occupation data
- **Religion** — Nonsense entries (`"Nope"`, `"Housekeeper"`, `"Jedi"`) replaced with `None`; children under 18 assigned parent's religion where inferable

---

## 📊 Analysis Performed

### 1. Age Distribution
- Built an **age pyramid** segmented by gender
- Classified population into: Children, Students, University-Age, Young Adults, Adults, Elderly
- Projected **10-year school-age population growth** using crude birth rate

### 2. Divorce & Marriage Rate
- Calculated **crude marriage and divorce rates** per 1,000 population
- Analysed marital status by age bracket and gender
- Identified housing implications from single/divorced occupants in overused properties

### 3. Unemployment Trends
- Grouped occupations into: Employed, Unemployed, Student, Retired, Child
- Visualised unemployment distribution by age bracket and gender
- Computed **labour force participation rate**

### 4. Religious Affiliations

| Religion | % of Population |
|----------|----------------|
| No Religion | 45.12% |
| Christian | 28.02% |
| Catholic | 14.41% |
| Methodist | 9.40% |
| Muslim | 1.68% |
| Sikh | 0.85% |
| Jewish | 0.44% |

### 5. Housing Occupancy
- Calculated occupancy levels per household
- Identified **overused and underused housing stock**
- Estimated proportion of singles and divorcees in overused homes

### 6. Commuter Analysis
- Filtered **university students** (University Student, PhD Student) as definite commuters
- Identified likely commuting occupations from the employed group
- Used this to assess demand for a **train station**

### 7. Birth & Death Rate
- **Crude Birth Rate**: estimated from children aged 0–4 over a 5-year window
- **Crude Death Rate**: estimated from population decline in age brackets 81+
- Used to model **future elderly population** and **school-age child growth**

### 8. Migration
- **Immigration**: estimated from single lodgers and visitors
- **Emigration**: estimated from the gender imbalance in divorced residents

---

## ✅ Key Recommendations

Based on the full analysis:

**Land Use**: Recommended building a **train station** — the data showed a significant commuter population (university students + professional commuters) with no direct rail access to either neighbouring city.

**Investment Priority**: Recommended **old age care funding** — projected elderly population remained substantial over the 10-year horizon, and current infirmity data indicated growing demand for end-of-life support services.

Both decisions were justified against competing options using statistical evidence from the cleaned dataset.

---

## 🛠️ Tech Stack

- **Python** — Pandas, NumPy, Matplotlib, Seaborn
- **Jupyter Notebook**
- **Data Wrangling** — Missing value imputation, outlier correction, categorical standardisation
- **Statistical Analysis** — Crude rates (birth, death, marriage, divorce, immigration)
- **Visualisation** — Age pyramids, histograms, boxplots, bar charts, KDE plots

---

## 📁 Repository Structure

```
├── DS_FINAL_Assess_.ipynb   # Full analysis notebook
├── README.md                # Project documentation
└── data/                    # Census dataset (mock)
```

---

## 👤 Author

**Muhammad Salahuddin**  
MSc Artificial Intelligence & Data Science — University of Hull  
[GitHub](https://github.com/msnoorani) | [LinkedIn](https://linkedin.com/in/msnoorani)
