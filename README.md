# 🏅 Olympics Data Analysis in R

This project explores trends in Olympic athlete performance using **R**, with data cleaning, visualization, and modeling through **tidyverse** and **tidymodels**.

---

## 📊 Overview
The Olympics bring together thousands of athletes across diverse sports.  
This analysis examines how **age, physical traits, and event characteristics** relate to performance and medal outcomes using the 2024 TidyTuesday Olympics dataset.

---

## 🎯 Research Goals
1. **Age Trends Across Sports** – Do certain sports favor older or more experienced athletes?  
2. **City-Level Performance** – Which cities have historically hosted the most successful events?  
3. **Physical Attributes** – How do age, height, weight, and sex relate to success?  
4. **Predictive Modeling** – Can we use athlete data to predict future outcomes?

---

## ⚙️ Data Cleaning
Steps included:
- Replaced missing medals with `"None"`  
- Removed redundant `games` column  
- Replaced hyphens with spaces in `sport` and `event`  
- Created summarized dataset with `avg_age`, `min_age`, `max_age`, and `total_athletes` per sport  
- Cleaned city names using a custom `gsub`/`sapply` function  
- Converted `year` to factor and set `"Athletics"` as base sport  
- Renamed `name` → `athlete`

> These cleaning steps used advanced R functions (`left_join`, `gsub`, `fct_relevel`, `rename`), going beyond basic requirements. :contentReference[oaicite:0]{index=0}

---

## 📈 Exploratory Analysis

### 1. Age by Sport & Medal  
Violin and boxplots show that sports like **Roque**, **Croquet**, and **Polo** have higher median athlete ages, emphasizing experience-based success. :contentReference[oaicite:1]{index=1}

### 2. Top Cities by Medal Count  
Bar charts reveal **London**, **Sydney**, and **Athina** as the most frequent hosts with large medal counts. :contentReference[oaicite:2]{index=2}

### 3. Physical Attributes  
Scatterplots highlight:
- **Age vs Weight**, colored by medal  
- **Age vs Height**, colored by sex  
These plots reveal clustering by sex and performance level. :contentReference[oaicite:3]{index=3}

---

## 🤖 Modeling
Built multiple **linear regression models** using `tidymodels`:

- **Physical Models:** `age ~ height + weight + sex + year`
  - Tested interaction and dummy variable combinations.  
- **Age Models:** `age ~ avg_age + min_age + max_age + total_athletes + medal`
  - Added interaction terms (`min_age:medal`) for better accuracy.  

**Results:**
- Interaction terms improved model fit (lower RMSE, higher R²).  
- Removing variables had minor effects.  
- Best model: *Age model with interaction term*. :contentReference[oaicite:4]{index=4}

---

## 🧠 Insights
- **Older sports** (e.g., Roque, Croquet) favor experience.  
- **Medal-winning athletes** tend to cluster in consistent physical ranges.  
- **Age-height-weight** relationships differ by sex and medal type.  
- **Best model** shows interactions between minimum age and medal predict age patterns effectively. :contentReference[oaicite:5]{index=5}

---

## ⚠️ Limitations
- Missing or incomplete records  
- No inclusion of training, socioeconomic, or geopolitical variables  
- Focus limited to certain sports — broader generalizations may vary :contentReference[oaicite:6]{index=6}

---

## 📚 Tools Used
- **R Packages:** tidyverse, ggplot2, tidymodels, ggrepel, arrow  
- **Data Source:** [TidyTuesday Olympics Dataset (2024-08-06)](https://github.com/rfordatascience/tidytuesday)

---

