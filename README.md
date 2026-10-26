# 🏅 Olympics Data Analysis in R

An R Markdown report that cleans the 2024 TidyTuesday Olympics dataset with the **tidyverse** and visualizes how athlete age and host city relate to medal outcomes.

---

## 📊 Overview
The Olympics bring together thousands of athletes across diverse sports.
This analysis (`Project.Rmd`) loads the [TidyTuesday Olympics dataset (2024-08-06)](https://github.com/rfordatascience/tidytuesday/tree/main/data/2024/2024-08-06) directly from GitHub, cleans it, and produces two plots plus a written conclusion and limitations section. It knits to a PDF report.

---

## 🎯 Research Goals
The report frames four research questions:
1. **Age Trends Across Sports** – Do certain sports favor older or more experienced athletes?
2. **City-Level Performance** – Which cities have historically hosted the most successful events?
3. **Physical Attributes** – How do age, height, weight, and sex relate to success?
4. **Predictive Modeling** – Can patterns in the data be used to predict outcomes such as future winners?

The current notebook contains code for questions 1 and 2; questions 3 and 4 are discussed only in the written conclusion (there are no physical-attribute plots or models in the code).

---

## ⚙️ Data Cleaning
Steps performed in the second code chunk:
- Replaced missing medals with `"None"`
- Replaced hyphens with spaces in `sport` and `event`
- Dropped the redundant `games` column (column 9)
- Computed `avg_age`, `min_age`, `max_age`, and `total_athletes` per sport, pivoted them to long format, and joined them back onto the athlete rows
- Trimmed leading/trailing whitespace from city names with a custom `gsub`/`sapply` function
- Converted `year` to a factor and set `"Athletics"` as the first level of `sport`
- Renamed `name` → `athlete`

---

## 📈 Exploratory Analysis

### 1. Age by Sport & Medal
Violin and box plots of age for the five sports with the highest median athlete age (Roque, Art Competitions, Alpinism, Polo, Croquet), faceted by medal type.

### 2. Top Cities by Medal Count
Faceted horizontal bar charts of entry counts by medal type for the three host cities with the most entries (London, Athina, Sydney).

---

## 🧠 Insights
- **Older sports** (e.g., Roque, Croquet) have higher median athlete ages, suggesting experience matters.
- The conclusion also discusses age, height, weight, and sex trends, which are not yet backed by plots or models in the notebook.

---

## ⚠️ Limitations
- Missing or incomplete records
- No training, socioeconomic, or geopolitical variables
- Limited sport coverage – broader generalizations may vary

---

## 📁 Project Structure
```
Project.Rmd   # R Markdown report: data loading, cleaning, plots, conclusion
README.md
```

---

## 🛠️ Tech Stack
- **R** with **tidyverse** (readr, dplyr, tidyr, stringr, forcats, ggplot2)
- **R Markdown** (rmarkdown + knitr), rendered to PDF

---

## 🚀 Getting Started

### Prerequisites
- R (tested with 4.1) and, optionally, RStudio
- R packages: `tidyverse`, `rmarkdown`, `knitr`
- A LaTeX distribution for the default PDF output (e.g. TinyTeX via `tinytex::install_tinytex()`)
- Internet access – the dataset is downloaded at run time from `raw.githubusercontent.com`

### Install packages
```r
install.packages(c("tidyverse", "rmarkdown", "knitr"))
```

### Render the report
From the repository root:
```bash
Rscript -e 'rmarkdown::render("Project.Rmd")'                                   # PDF (needs LaTeX)
Rscript -e 'rmarkdown::render("Project.Rmd", output_format = "html_document")'  # HTML (no LaTeX needed)
```
Or open `Project.Rmd` in RStudio and click **Knit**.

No environment variables or secrets are required.
