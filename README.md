# 1000406_Jeyaditya_AIY2_Logisight_Analytics_FA_2
# 🚚 LogiSight Analytics

### Last-Mile Command Center

> **Turning delivery data into operational insight.**

LogiSight Analytics is an interactive **Streamlit decision-support dashboard** designed to explore last-mile delivery performance across traffic, weather, geography, vehicles, product categories, courier characteristics, and dispatch timing.

The system processes **43,739 delivery records across 16 operational attributes** and transforms them into an interactive analytics environment combining statistical analysis, mathematical modelling, 2D and 3D visualizations, dynamic filtering, and data-quality inspection.

<br>

|  📦 Orders | 📊 Features | ⏱️ Mean Transit | 🚨 Late Boundary |
| :--------: | :---------: | :-------------: | :--------------: |
| **43,739** |    **16**   |  **124.91 min** |  **176.82 min**  |

<br>

> ### 🎯 The Question
>
> **What does the delivery data tell us — and what operational decision could that insight support?**

---

## ✨ What is LogiSight?

Last-mile delivery performance is influenced by multiple factors at once.

Traffic may slow a route down.
Weather may increase delivery times.
Different vehicles may perform differently.
Distance and dispatch time can change the operational picture.
Courier characteristics may reveal additional patterns.

LogiSight brings these dimensions together into a single interactive command center.

Instead of presenting isolated charts, the dashboard allows users to **filter, compare, investigate, and interpret** delivery performance from multiple perspectives.

---

## 📌 At a Glance

| Metric                            |         Result |
| --------------------------------- | -------------: |
| Delivery records                  |     **43,739** |
| Operational attributes            |         **16** |
| Mean delivery time                | **124.91 min** |
| Standard deviation                |  **51.92 min** |
| Statistical late threshold        | **176.82 min** |
| `Metropolitian` records corrected |     **32,698** |
| Preserved `6.0` ratings           |         **53** |
| 2D analytical visualizations      |         **10** |
| Interactive 3D visualizations     |          **2** |



# 🧭 Dashboard Architecture

```text
                         LOGISIGHT ANALYTICS
                                │
              ┌─────────────────┴─────────────────┐
              │                                   │
        FILTER HUB                          KPI COMMAND BAR
              │                                   │
     ┌────────┼────────┐             ┌────────────┼────────────┐
     │        │        │             │            │            │
   Area    Traffic  Weather       Orders      Transit       Late Rate
     │        │        │                         │
   Vehicle Category Missing                    Rating
                       │
                       ▼
              ┌─────────────────────┐
              │   ANALYTICS LAYER   │
              └──────────┬──────────┘
                         │
       ┌─────────────────┼─────────────────┐
       ▼                 ▼                 ▼
   Operational         3D              Diagnostic
   Visuals           Analytics            Matrix
       │                 │                 │
       └─────────────────┼─────────────────┘
                         ▼
                Data Quality & Records
```

The interface is organized into four primary analytical tabs:

| Tab                               | Purpose                                                 |
| --------------------------------- | ------------------------------------------------------- |
| **01 · Core Operational Visuals** | Understand major delivery-performance relationships     |
| **02 · 3D Interactive Analytics** | Explore multidimensional relationships                  |
| **03 · Deep Diagnostic Matrix**   | Investigate distributions, timing, and failure patterns |
| **04 · Data Quality & Records**   | Audit the processed dataset and inspect records         |

---

# 🎛️ Interactive Control Layer

The sidebar acts as the dashboard's **filter hub**.

Users can dynamically filter by:

* 📍 Delivery area
* 🚦 Traffic condition
* 🌦️ Weather
* 🚚 Vehicle type
* 📦 Product category
* ⚠️ Missing traffic values
* ⚠️ Missing weather values

Every KPI and visualization responds to the active filter state.

### Executive KPI Ribbon

The dashboard continuously reports:

**Active Orders**
Number of records matching the current filters.

**Mean Transit Time**
Average delivery time for the filtered dataset.

**Late Breach Rate**
Percentage of filtered records exceeding the statistical late boundary.

**Mean Courier Rating**
Average agent rating while preserving the dataset's observed `1.0–6.0` scale.

---

# 📊 Core Operational Analytics

## 01 · Delay Analyzer

**Weather × Traffic → Mean Delivery Time**

The Delay Analyzer compares average delivery time across combinations of weather and traffic conditions.


### Why it matters

This view helps identify environmental and congestion combinations associated with increased delivery latency.

---

## 02 · Vehicle Performance

**Vehicle Type → Average Delivery Time + Order Volume**

The dashboard compares average delivery time across vehicle categories while also displaying the number of orders associated with each category.

### Why it matters

Provides a direct comparison of observed delivery performance across vehicle types and can support fleet-allocation discussions.

---

## 03 · Agent Rating vs. Delivery Speed

**Courier Rating × Delivery Time × Age Group**

A scatter plot compares courier ratings against delivery time while separating observations into:

* `<25`
* `25–40`
* `40+`

The complete observed rating range is retained, including all **53 records with a rating of `6.0`**.

### Why it matters

Allows users to visually investigate whether courier rating, age grouping, and delivery speed exhibit noticeable relationships within the dataset.

---

## 04 · Area Transit Heatmap

**Delivery Area × Traffic → Mean Delivery Time**

A heatmap compares delivery areas against traffic conditions and displays the corresponding average delivery time.

The source-data spelling anomaly:

```text
Metropolitian
```

is standardized to:

```text
Metropolitan
```

before analysis.

### Why it matters

Makes geographical and congestion-related delivery patterns easier to compare.

---

## 05 · Category Distribution

**Product Category → Delivery-Time Distribution**

A box plot compares delivery times across product categories.

Each distribution exposes:

* Median
* Interquartile range
* Overall spread
* Potential outliers

### Why it matters

Some categories may exhibit greater variability even when their average delivery time appears similar.

---

# 🌐 3D Interactive Analytics

The second dashboard tab moves beyond conventional 2D charts and combines multiple variables into interactive 3D spaces.

---

## 🧑‍✈️ 06 · Courier Performance Hyper-Space

### Dimensions

```text
X → Agent Rating
Y → Agent Age
Z → Delivery Time
```

The visualization samples up to **2,500 records** when the filtered dataset is larger than the display limit.

Users can rotate and inspect the 3D space to explore relationships that may be difficult to see in a conventional scatter plot.

---

## 🌍 07 · Spatial Topography

### Dimensions

```text
X → Geodesic Distance
Y → Order Hour
Z → Delivery Time
Color → Delivery Area
```

This visualization combines:

* Delivery distance
* Dispatch timing
* Delivery duration
* Geographic area

into a single interactive analytical space.

### Why it matters

It provides another way to investigate whether delivery duration changes with distance and operating time.

---

# 🔬 Deep Diagnostic Matrix

The third tab moves from broad operational comparisons into deeper statistical diagnostics.

---

## 08 · Delivery-Time Distribution

**Histogram + Violin Distribution**

The dashboard displays the distribution of delivery times together with the statistical late boundary:

$$
\tau_{\text{late}} = \mu+\sigma
$$

$$
\tau_{\text{late}} = 176.82\text{ minutes}
$$

This makes the relationship between the overall distribution and the analytical cutoff immediately visible.

---

## 09 · 24-Hour Dispatch Profile

**Order Volume × Mean Delivery Time**

A dual-axis visualization compares:

* Hourly order volume
* Mean delivery time

across the full 24-hour clock.

The implementation uses `connectgaps=False` for the delivery-time series so that missing operating periods are not visually connected by misleading diagonal lines.

### Why it matters

Allows dispatch volume and delivery latency to be compared throughout the day.

---

## 10 · SLA Failure Matrix

**Area × Traffic → Late-Delivery Rate**

The resulting matrix highlights area/traffic combinations with comparatively higher proportions of late records.

> The term **SLA** here refers to the dashboard's statistical late classification, not an externally defined contractual SLA.

---

## ⭐ 11 · Agent Rating Spectrum

**Delivery Area × Rating Distribution**

A violin plot displays courier-rating distributions by delivery area.

The chart preserves the complete observed range:

$$
1.0 \leq \text{Rating} \leq 6.0
$$

Individual observations are also displayed alongside the distribution.

### Why it matters

Averages can hide variation. This visualization shows the shape and spread of the rating data rather than reducing each area to a single number.

---

# 🧹 Data Quality & Record Inspection

The fourth tab is dedicated to understanding the quality of the processed dataset.

## Quality Audit

The dashboard explicitly checks:

| Field          | Audit                            |
| -------------- | -------------------------------- |
| `Weather`      | Missing values                   |
| `Traffic`      | Missing values                   |
| `Order_Time`   | Missing values                   |
| `Agent_Rating` | Missing values                   |
| `Distance_km`  | Missing / invalid derived values |

The audit reports both:

* Missing-value count
* Missing-value percentage

---

## 🔎 Raw Record Inspector

The dashboard also exposes the processed records directly.

Users can inspect the filtered dataset rather than relying exclusively on summarized charts.

This provides a useful bridge between:

```text
Raw Record
    ↓
Processed Record
    ↓
Derived Feature
    ↓
Visualization
```

---

# 🧮 Mathematical Foundations

LogiSight is not simply a visualization dashboard.

The application uses mathematical transformations and statistical measures to generate several of its analytical features.

---

## Mean

$$
\mu=
\frac{1}{N}
\sum_{i=1}^{N}x_i
$$

For the complete dataset:

$$
\boxed{\mu=124.91\text{ minutes}}
$$

---

## Standard Deviation

$$
\sigma=
\sqrt{
\frac{1}{N-1}
\sum_{i=1}^{N}(x_i-\mu)^2
}
$$

For the complete dataset:

$$
\boxed{\sigma=51.92\text{ minutes}}
$$

---

## Statistical Late Boundary

$$
\tau_{\text{late}}=\mu+\sigma
$$

Therefore:

$$
\boxed{\tau_{\text{late}}=176.82\text{ minutes}}
$$

The application then assigns:

```text
Delivery Time > 176.82 min  →  Is_Late = 1
Delivery Time ≤ 176.82 min  →  Is_Late = 0
```

---

## 🌐 Haversine Distance

The dashboard derives approximate geographic distance between store and drop-off coordinates using the Haversine formula.

With:

$$
R=6371.0\text{ km}
$$

the calculation uses:

$$
a=
\sin^2\left(\frac{\Delta\phi}{2}\right)
+
\cos(\phi_1)\cos(\phi_2)
\sin^2\left(\frac{\Delta\lambda}{2}\right)
$$

$$
c=
2\operatorname{atan2}
(\sqrt a,\sqrt{1-a})
$$

$$
d=R\,c
$$

Distances greater than **500 km** are treated as anomalous GPS-derived values and converted to `NaN`.

---

# 🧽 Data Preparation Pipeline

Before the dashboard performs analysis, the dataset passes through a preprocessing pipeline.

```text
Last Mile Delivery Data.csv
            │
            ▼
     Whitespace Cleanup
            │
            ▼
     String-Null Handling
            │
            ▼
     Category Normalization
            │
            ▼
      Numeric Conversion
            │
            ▼
       Date / Time Parsing
            │
            ▼
      Haversine Distance
            │
            ▼
       Age Stratification
            │
            ▼
     Statistical Threshold
            │
            ▼
       Interactive Dashboard
```

---

## 01 · Whitespace Normalization

Whitespace is stripped from object columns so values such as:

```text
"High "
```

and

```text
"High"
```

are not treated as different categories.

---

## 02 · String Null Conversion

The following string representations are converted to actual missing values:

```text
"NaN"
"nan"
"None"
""
```

---

## 03 · Area Name Normalization

The dataset contains:

```text
Metropolitian
```

which is standardized to:

```text
Metropolitan
```

This correction affects **32,698 records**.

---

## 04 · Numeric Conversion

The following fields are explicitly converted to numeric values:

* `Delivery_Time`
* `Agent_Age`
* `Agent_Rating`

---

## 05 · Date & Time Processing

`Order_Date` is converted to a datetime value.

`Order_Time` is used to derive:

```text
Order_Hour = 0–23
```

This enables the 24-hour dispatch analysis.

---

## 06 · Distance Derivation

Store and drop-off coordinates are used to calculate:

```text
Distance_km
```

using the Haversine method.

Values exceeding **500 km** are treated as anomalous and converted to missing values.

---

## 07 · Age Cohorts

Agent ages are grouped into three analytical cohorts:

| Age Range | Cohort         |
| --------- | -------------- |
| `<25`     | Junior         |
| `25–40`   | Core Workforce |
| `40+`     | Senior Fleet   |

---

## 08 · Rating Preservation

The source rating scale is preserved rather than artificially clipped.

The observed range remains:

```text
1.0 → 6.0
```

including the **53 records rated `6.0`**.

---

# 🛠️ Technology Stack

| Technology               | Role                                                    |
| ------------------------ | ------------------------------------------------------- |
| **Python 3.10+**         | Application runtime and processing                      |
| **Streamlit**            | Interactive dashboard framework                         |
| **Pandas**               | Data cleaning, transformation, grouping and aggregation |
| **NumPy**                | Numerical computation                                   |
| **Plotly Express**       | Interactive statistical and categorical charts          |
| **Plotly Graph Objects** | Custom and advanced interactive visualizations          |

### 🎨 Interface

The dashboard uses a custom **dark glassmorphism / frosted-glass** interface with:

* KPI cards
* Horizontal navigation
* Responsive analytical sections
* Interactive Plotly charts
* Expandable explanations
* High-contrast data presentation

---

# 📁 Project Structure

```text
delivery-performance-dashboard/
│
├── 📄 Last mile Delivery Data.csv
├── 🐍 math_app.py
├── 📦 requirements.txt
└── 📘 README.md
```

The dataset must remain at the project root because the application loads it using:

```python
pd.read_csv("Last mile Delivery Data.csv")
```

---

# 🚀 Getting Started

## Prerequisites

Install:

* Python **3.10–3.13**
* Git

---

## 1. Clone the Repository

Replace the placeholder repository address with the actual GitHub repository.

```bash
git clone https://github.com/<YOUR_USERNAME>/delivery-performance-dashboard.git
cd delivery-performance-dashboard
```

---

## 2. Create a Virtual Environment

### Windows

```bash
python -m venv venv
venv\Scripts\activate
```

### macOS / Linux

```bash
python3 -m venv venv
source venv/bin/activate
```

---

## 3. Install Dependencies

```bash
pip install -r requirements.txt
```

---

## 4. Verify the Dataset

Confirm that the project root contains:

```text
Last mile Delivery Data.csv
```

alongside:

```text
math_app.py
```

---

## 5. Launch LogiSight

```bash
streamlit run math_app.py
```

The dashboard will normally become available locally at:

```text
http://localhost:8501
```

---

# ☁️ Streamlit Cloud Deployment

LogiSight can be deployed through Streamlit Cloud once the project files have been pushed to GitHub.

### Required repository files

```text
math_app.py
requirements.txt
Last mile Delivery Data.csv
README.md
```

### Deployment configuration

| Setting    | Value                                            |
| ---------- | ------------------------------------------------ |
| Repository | `<YOUR_USERNAME>/delivery-performance-dashboard` |
| Branch     | `main`                                           |
| Main file  | `math_app.py`                                    |

The deployment environment installs the packages listed in `requirements.txt` and launches the Streamlit application.

---

# 🎓 Course & Assessment Mapping

LogiSight was developed as a **Mathematics for AI-II Formative Assessment 2 (FA-2)** project.

| Stage                | Focus                  | LogiSight Implementation                                                           |
| -------------------- | ---------------------- | ---------------------------------------------------------------------------------- |
| **FA-1 · Stage 1**   | Operational questions  | Questions linked to delivery, fleet, traffic, weather and workforce variables      |
| **FA-1 · Stage 2**   | Feature planning       | Analytical purpose assigned to major visualizations                                |
| **FA-1 · Stage 3**   | Data & UI planning     | End-to-end preprocessing pipeline and four-tab architecture                        |
| **FA-2 · Stage 4**   | Data processing        | Cleaning, normalization, Haversine distance, age cohorts and statistical threshold |
| **FA-2 · Stage 5**   | Visualization          | Core analytics, diagnostics, 3D exploration and quality analysis                   |
| **FA-2 · Stage 6–7** | Interface & deployment | Streamlit UI, interactive filtering, GitHub repository and deployment workflow     |

---

# 🧠 Design Philosophy

LogiSight is built around a simple principle:

> **A visualization should help answer a question, not simply occupy space on a dashboard.**

The analytical workflow therefore follows:

```text
                    ┌─────────────────────┐
                    │   Delivery Records  │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │   Data Preparation  │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ Mathematical Logic  │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ Statistical Analysis│
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ Interactive Charts  │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ Operational Insight │
                    └─────────────────────┘
```

This connects four core ideas:

**Data → Mathematics → Visualization → Decision Support**

---

# 📚 Analytical Coverage

| Dimension                       | Included |
| ------------------------------- | :------: |
| Delivery time                   |     ✅    |
| Traffic                         |     ✅    |
| Weather                         |     ✅    |
| Vehicle type                    |     ✅    |
| Product category                |     ✅    |
| Courier rating                  |     ✅    |
| Courier age                     |     ✅    |
| Delivery area                   |     ✅    |
| Dispatch hour                   |     ✅    |
| Geographic distance             |     ✅    |
| Missing-data analysis           |     ✅    |
| Statistical late classification |     ✅    |
| 3D visualization                |     ✅    |
| Raw-record inspection           |     ✅    |

---

# 👤 Project Information

**Project:** LogiSight Analytics — Last-Mile Command Center
**Course:** Mathematics for AI-II
**Assessment:** Formative Assessment 2 (FA-2)
**Student:** Jeyaditya
**Facilitator:** Syed Ali Beema
**School:** Jain Vidyalaya

---

## 🙌 Acknowledgement

Built as an academic project exploring how **mathematical analysis, data processing, and interactive visualization** can be combined into a practical operational analytics system.

---

<p align="center">

**LogiSight Analytics**

*From delivery records to operational insight.*

</p>
