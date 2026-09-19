# 🧠 Reddit Mental Health Discussions: NLP Analysis

This project analyzes how mental-health topics are discussed across Reddit communities, focusing on differences in **discussion volume, emotional tone, vocabulary, and language patterns** between 2019 and 2022.

The analysis combines **data cleaning, exploratory data analysis, sentiment analysis, TF-IDF text analysis, and machine-learning classification** to examine how language differs across five Reddit mental-health communities.

---

## 🔍 Research Question

**How do discussion volume, sentiment, vocabulary, and language patterns differ across Reddit mental-health communities and over time?**

The project focuses on five communities:

- Anxiety
- Depression
- Loneliness
- Mental Health
- SuicideWatch

---

## 📊 Project Overview

The project includes:

- Loading and combining monthly Reddit datasets
- Data quality checks and cleaning
- Duplicate and unusable-post removal
- Exploratory analysis of discussion volume
- Community and yearly comparisons
- Monthly discussion trends
- VADER sentiment analysis
- TF-IDF vocabulary analysis
- Community-level language comparison
- Machine-learning text classification
- Model evaluation
- Confusion-matrix analysis
- Depression-class error analysis
- Final interpretation and limitations

---

## 📦 Dataset

The analysis uses monthly Reddit CSV exports covering approximately:

**January 2019 – August 2022**

A total of:

- **219 raw CSV files**
- **213,838 usable Reddit posts**
- **5 mental-health communities**

were included in the final analysis.

The original raw datasets were preserved while the analysis created a cleaned working dataset for NLP and machine-learning tasks.

### Communities Analyzed

| Community |
| --- |
| Anxiety |
| Depression |
| Loneliness |
| Mental Health |
| SuicideWatch |

---

## 🧹 Data Preparation

The preprocessing workflow includes:

- Combining monthly CSV files
- Extracting community and date information
- Standardizing text fields
- Removing missing or unusable posts
- Removing duplicated text
- Creating year and month variables
- Preparing text for sentiment and TF-IDF analysis
- Creating reproducible samples for NLP and machine learning

The cleaning process was designed to remain simple and reproducible while preserving meaningful user language.

---

## 📈 Exploratory Analysis

The exploratory analysis examines how Reddit discussion activity differs across communities and over time.

Main observations include:

- **Mental Health** is the largest community in the cleaned dataset.
- **2019** contains the highest total discussion volume.
- Monthly activity remains relatively stable overall, with several visible spikes.
- Community activity differs considerably across the five groups.

---

## 💬 Sentiment Analysis

Sentiment is estimated using **VADER compound sentiment**, which is designed for short and informal text such as social-media posts.

The analysis compares:

- Average sentiment by community
- Average sentiment by year
- Differences in emotional tone across mental-health discussions

### Main Sentiment Finding

**SuicideWatch shows the lowest average VADER sentiment** among the communities analyzed.

This result is consistent with the more immediate distress-oriented language commonly found in that community.

Sentiment scores should be interpreted cautiously because automated sentiment tools cannot fully capture sarcasm, ambiguity, context, or complex mental-health language.

---

## 🔤 TF-IDF Language Analysis

TF-IDF is used to identify terms that are especially important within each community.

The analysis removes common and uninformative words so that the remaining terms better represent community-specific discussion patterns.

Examples of themes identified include:

### Anxiety

Language frequently relates to:

- Panic
- Sleep
- Attacks
- Work
- Thoughts
- Fear
- Physical symptoms

### Loneliness

Discussion commonly focuses on:

- Friendship
- Relationships
- Isolation
- Communication
- Social connection

### SuicideWatch

Language contains stronger references to:

- Immediate distress
- Pain
- Family
- Relationships
- Crisis-oriented experiences

Overall, the TF-IDF analysis shows that the communities share some vocabulary but also contain meaningful differences in discussion context.

---

## 🤖 Machine-Learning Classification

A text-classification task was used to test whether Reddit communities contain sufficiently distinct language patterns to predict the community from post text.

The models evaluated include:

1. **Multinomial Naive Bayes with word TF-IDF**
2. **LinearSVC with word TF-IDF**
3. **LinearSVC with word + character TF-IDF**

### Best Model

The strongest model was:

**LinearSVC with combined word and character TF-IDF features**

| Metric | Result |
| --- | ---: |
| Accuracy | **0.588** |
| Macro F1 | **0.584** |
| Macro Precision | **0.581** |
| Macro Recall | **0.587** |

The results indicate **moderate but meaningful separation** between the language used across the five communities.

The model is intended as a language-pattern classification exercise and **not as a diagnostic model**.

---

## 🔎 Depression Class Analysis

Depression was the most difficult community for the classifier to distinguish.

Its class-level F1 score was approximately:

**0.396**

The confusion matrix shows that depression posts are often confused with:

- SuicideWatch
- Mental Health
- Loneliness

This suggests that depression-related language overlaps strongly with broader expressions of distress, isolation, and general mental-health discussion.

The lower classification performance therefore reflects genuine language overlap between communities rather than simply poor model quality.

---

## 💡 Key Findings

- The final dataset contains **213,838 usable Reddit posts** from **219 CSV files**.
- Five major mental-health communities were analyzed.
- **Mental Health** contains the largest number of posts.
- **2019** has the highest discussion volume in the available data.
- **SuicideWatch** shows the lowest average VADER sentiment.
- TF-IDF reveals meaningful differences in community vocabulary.
- Anxiety discussions frequently contain language related to panic, sleep, work, fear, and physical symptoms.
- Loneliness discussions strongly emphasize friendship, relationships, isolation, and social connection.
- SuicideWatch contains more immediate distress and crisis-oriented language.
- The best classifier is **LinearSVC with word + character TF-IDF**.
- The best model achieves **0.588 accuracy** and **0.584 macro F1**.
- Depression is the hardest class to distinguish because its language overlaps with several related communities.
- The results support the idea that Reddit mental-health communities have recognizable but overlapping language patterns.

---

## 🧪 Important Methodological Choices

Several decisions were made to keep the analysis statistically and methodologically defensible.

### Balanced Evaluation

The classification analysis uses balanced community samples so that larger communities do not dominate model evaluation.

### Macro Metrics

Macro-averaged metrics are reported because they treat each community equally regardless of class size.

### Word + Character Features

The final LinearSVC model combines word-level and character-level TF-IDF features.

Character features can capture:

- Word variations
- Informal writing
- Misspellings
- Partial words
- Social-media writing patterns

This improved the model's ability to distinguish communities without introducing unnecessary model complexity.

### No Diagnostic Interpretation

The classification target is **Reddit community membership**, not a user's mental-health condition.

The results therefore describe language patterns between online communities and should not be interpreted as medical or psychological diagnosis.

---

## 🛠️ Technologies Used

- Python
- pandas
- NumPy
- Matplotlib
- Seaborn
- scikit-learn
- VADER Sentiment
- TF-IDF
- LinearSVC
- Multinomial Naive Bayes
- Jupyter Notebook
- HTML
- Git
- GitHub

---

## 📁 Repository Structure

```text
Reddit-Mental-Health-NLP-Analysis/
│
├── README.md
├── index.html
├── reddit_mental_health_analysis.ipynb
│
└── data/
    └── Reddit monthly CSV files
```

`index.html` provides a clean portfolio-style presentation of the project's methodology, results, visualizations, and key findings.

---

## 📓 Full Analysis

The complete project analysis is available in:

- `reddit_mental_health_analysis.ipynb` — complete Jupyter Notebook
- `index.html` — portfolio-style project presentation
- `data/` — Reddit mental-health datasets

The notebook contains the complete workflow from data preparation through exploratory analysis, sentiment analysis, TF-IDF, machine learning, model evaluation, and final interpretation.

---

## ▶️ Reproducing the Analysis

Clone the repository:

```bash
git clone https://github.com/ayaa137/Reddit-Mental-Health-NLP-Analysis.git
```

Open the project directory:

```bash
cd Reddit-Mental-Health-NLP-Analysis
```

Install the main Python packages:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn nltk jupyter
```

Then open the notebook:

```bash
jupyter notebook reddit_mental_health_analysis.ipynb
```

Run the notebook from top to bottom to reproduce the analysis.

---

## ⚠️ Limitations

This project has several important limitations.

- Reddit users are not representative of the general population.
- Posting in a mental-health subreddit does not represent a clinical diagnosis.
- Community labels describe subreddit membership rather than confirmed mental-health conditions.
- VADER sentiment cannot fully capture context, irony, ambiguity, or complex psychological language.
- Different communities may use overlapping vocabulary.
- The available dataset ends around **August 2022**, so 2022 is not a complete year.
- The machine-learning model predicts subreddit membership rather than mental-health status.
- The analysis focuses on textual patterns and does not include demographic or clinical information.

The findings should therefore be interpreted as **patterns in online mental-health discussions**, rather than medical or causal conclusions.

---

## 👩‍💻 Author

**Aya Abdine**

Master's in Data Science for Society and Business  
Constructor University

---

## 🌐 Project Links

**GitHub Repository:**  
https://github.com/ayaa137/Reddit-Mental-Health-NLP-Analysis

## 🌐 Portfolio Website

https://ayaa137.github.io/Reddit-Mental-Health-NLP-Analysis/

---

## 📌 Project Purpose

This project was developed as a portfolio-focused NLP analysis demonstrating practical skills in:

- Data preprocessing
- Exploratory data analysis
- Natural language processing
- Sentiment analysis
- Text feature engineering
- Machine learning
- Model evaluation
- Visualization
- Interpretation of real-world social-media data
