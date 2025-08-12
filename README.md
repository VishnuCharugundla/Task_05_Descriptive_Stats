# Syracuse Basketball 2024–25 — GPT Evaluation & Truth Set

## 📌 Project Overview
This project evaluates GPT’s ability to correctly interpret and analyze structured sports statistics by comparing its answers to a manually calculated **truth set** derived from the official 2024–2025 Syracuse University Men’s Basketball statistics.

The workflow:
1. **Extract data** from the official PDF stats sheet into CSV format.
2. **Ask GPT** a series of questions, increasing in complexity:
   - **Straightforward lookups**
   - **Calculation-based queries**
   - **Multi-metric & subjective reasoning**
3. **Generate a truth set** using Python code and the extracted CSV.
4. **Compare GPT answers** to the truth set.
5. **Document findings** and identify areas where GPT fails or passes.

---

## 🏀 Dataset
The dataset comes from Syracuse University’s official **2024–2025 Men’s Basketball overall statistics** as of March 12, 2025.  
It includes:
- Player-level stats (minutes, FG%, 3PT%, FT%, rebounds, assists, turnovers, points, etc.)
- Team totals & averages
- Game-by-game results

Source: Official Syracuse Athletics PDF.

---

## 🔍 Evaluation Process
The evaluation consisted of **10 questions** grouped into three difficulty tiers:

### 1️⃣ Straightforward Questions
- How many games did Syracuse win overall?  
- Which player scored the most total points?  
- Who had the highest FG% (min 100 FGA)?  
- What was the team’s average rebounds per game?  

### 2️⃣ Calculation Questions
- Which player had the best Assist-to-Turnover ratio (min 20 assists)?  
- Which player had the highest average rebounds per game?  
- Who had the highest free throw percentage among players attempting at least 50 free throws?  

### 3️⃣ Multi-Metric & Subjective Questions
- Who was the most improved player from the first half to the second half of the season in terms of PPG?  
- Should the coach focus on offense or defense to win two more games next season? Which one player should be the focus and why?  
- Which player had the biggest impact on team wins based on efficiency?  

---

## ⚙️ Methodology
1. **PDF to CSV Conversion**:  
   We used `pdfplumber` to parse the PDF and extract the player stats table into a clean CSV file.

2. **Truth Set Generation**:  
   All answers were calculated using Python (`pandas`), applying filters and aggregation rules exactly as stated in each question.

3. **Comparison**:  
   GPT answers were compared to truth set results in `Comparison.xlsx`, with **Notes / Why Incorrect** detailing reasons for mismatches.

---

## 📊 Key Findings
- GPT was **accurate** for most straightforward and simple calculation questions.
- GPT sometimes **ignored explicit filters** (e.g., min 50 free throw attempts).
- Multi-metric questions often produced **reasoned but unverifiable answers**, requiring human judgment.
- Data parsing accuracy was critical — incorrect parsing would cascade into wrong answers.

---

## 🚀 How to Run the Truth Set Code
1. Install dependencies:
   ```bash
   pip install pandas pdfplumber

2. Run the Jupyter notebook:
   ```bash
   jupyter notebook notebooks/truth_set.ipynb
3. Review output in [Comparison.xlsx](Comparison.xlsx).
