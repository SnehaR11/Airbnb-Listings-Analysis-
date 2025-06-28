# 🏡 Airbnb-Listings-Analysis

This project performs a detailed analysis on an Airbnb dataset comprising 75 columns and nearly 88,000 records. The goal was to identify high-performing listings based on user reviews and ratings by applying data preprocessing, visualization, feature engineering, and machine learning techniques.

## 📊 Key Highlights

### 🔹 Data Cleaning & Preprocessing
- Removed unnecessary columns to retain only the most relevant 20.
- Handled missing values using mode imputation and removed a column (`bathrooms`) with 100% missing values.
- Encoded categorical variables using Label Encoding.

### 🔹 Exploratory Data Analysis (EDA)
- Visualized relationships between room types, property types, reviews, and price.
- Identified most common room categories and listing patterns using count plots and pair plots.

### 🔹 Feature Engineering
- Created a new binary column `Success`:
  - **"Good"** if both number of reviews and review score rating were **above average**
  - **"Bad"** otherwise

### 🔹 Model Building
- **Logistic Regression**
  - Achieved **~89.87% accuracy**
  - Balanced performance with good precision and recall

- **Decision Tree Classifier**
  - Achieved **100% accuracy**
  - However, this resulted in overfitting (explained below)

---

## 📌 Why the Decision Tree Model Achieved 100% Accuracy

While the Decision Tree classifier reported **100% accuracy**, this is not necessarily a good thing. Here’s why:

### ⚠️ Overfitting Detected

- The model **memorized** patterns in the training data too precisely.
- It was able to make perfect predictions on the test set—but may fail on new, unseen data.
- The data was **imbalanced**, with many more “Bad” listings than “Good,” making it easier to split perfectly.

### 🔎 Contributing Factors

- **Highly predictive features** like `number_of_reviews` and `review_scores_rating` made it easier for the tree to split cleanly.
- No regularization or pruning was applied, allowing the tree to grow too deep and specific.

### 🛠️ Solutions

- Introduce **regularization** (e.g., `max_depth`, `min_samples_leaf`) to prevent overfitting.
- Use **cross-validation** to validate performance more accurately.
- Try ensemble methods like **Random Forest** or **Gradient Boosting** for better generalization.

---

## 💻 Tech Stack

- **Python**
- **Jupyter Notebook**
- **Pandas, NumPy, Matplotlib, Seaborn**
- **Scikit-learn**

