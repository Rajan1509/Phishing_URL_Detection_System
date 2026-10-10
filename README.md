# Phishing URL Detection System 🛡️

A real-time Machine Learning and Natural Language Processing (NLP) web application that detects malicious and phishing URLs at point-of-click with **96.43% accuracy** and **sub-50ms inference latency**.

---

## 📌 Project Overview

- **Core Algorithm:** Logistic Regression (`phishing.pkl`) trained on **549,346** real-world URLs.
- **NLP Preprocessing:** Regular Expression Tokenizer (`[A-Za-z]+`) & English Snowball Stemmer.
- **Feature Vectorizer:** Bag-of-Words `CountVectorizer` (`vectorizer.pkl`).
- **Web Interface:** Lightweight Python Flask microservice with instant safety verdicts.

---

## ⚙️ Prerequisites

- **Python:** Version 3.10, 3.11, 3.12, or 3.13 (64-bit recommended)
- **Pip:** Python package manager

---

## 🚀 Installation

1. **Open Terminal / PowerShell** in the project directory:
   ```powershell
   cd C:\Users\rajak\OneDrive\Desktop\Phishing_URL_Detection_System
   ```

2. **Activate the Virtual Environment** (already included in `env/`):
   - **Windows PowerShell:**
     ```powershell
     .\env\Scripts\Activate.ps1
     ```
   - *If execution policy restricts scripts, run:*
     ```powershell
     Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
     .\env\Scripts\Activate.ps1
     ```

3. **Install Dependencies** (if creating a new environment):
   ```bash
   pip install flask scikit-learn nltk pandas numpy
   ```

---

## ▶️ How to Run the Project

1. **Start the Flask Web Server:**
   ```bash
   python app.py
   ```

2. **Open the Web Application:**
   Open any web browser and visit:
   ```
   http://127.0.0.1:5000/
   ```

---

## 🧪 How to Test

Enter sample URLs into the web interface input box and click **Check URL**:

### 1. Test Safe / Legitimate URLs (Expected Verdict: Green / Safe)
| Input URL | Expected Output | Actual Result |
| :--- | :--- | :---: |
| `https://www.youtube.com/` | `This is healthy and good website` | ✅ PASS |
| `youtube.com/watch?v=qI0TDI3vdU` | `This is healthy and good website` | ✅ PASS |
| `restorevisioncentres.com/html/technology.html` | `This is healthy and good website` | ✅ PASS |

### 2. Test Phishing / Malicious URLs (Expected Verdict: Red / Alert)
| Input URL | Attack Type | Expected Output | Actual Result |
| :--- | :--- | :--- | :---: |
| `yeniik.com.tr/wp-admin/js/login.alibaba.com/login.jsp.php` | Brand Spoofing | `This is a phishing website!!` | ✅ PASS |
| `fazan-pacir.rs/temp/libraries/ipad` | Deep Path Nesting | `This is a phishing website!!` | ✅ PASS |
| `www.tubemoviez.exe` | Executable Endpoint | `This is a phishing website!!` | ✅ PASS |
| `svision-online.de/mgfi/administrator/classes/fx29id1.txt` | Script Injection | `This is a phishing website!!` | ✅ PASS |

---

## 📁 Project Directory Structure

```text
Phishing_URL_Detection_System/
├── app.py                                              # Flask web server & inference route
├── vectorizer.pkl                                      # Serialized CountVectorizer (BoW)
├── phishing.pkl                                        # Production Logistic Regression model
├── phishing_mnb.pkl                                    # Baseline Multinomial Naive Bayes model
├── Phishing_URL_Detection_System.ipynb                 # EDA, training & evaluation notebook
├── README.md                                           # Project setup & usage guide
├── templates/
│   └── index.html                                      # Frontend user interface
├── Dataset/
│   └── phishing_site_urls.csv                          # Benchmark dataset (549,346 URLs)
├── Phishing_URL_Detection_System_Report.docx           # Full academic & technical report
├── Phishing_URL_Detection_System_Presentation_12Slides.pptx # 12-slide presentation deck
└── env/                                                # Python virtual environment
```

---

## 📊 Key Performance Metrics

- **Training Accuracy:** `97.86%`
- **Testing Accuracy (Holdout 109,870 URLs):** `96.43%`
- **Precision on Phishing URLs:** `97%`
- **Recall on Phishing URLs:** `90%`
- **False-Positive Rate:** `< 0.99%` (787 / 78,670 benign samples)
- **Average Inference Latency:** `~4.2 ms` (Total HTTP response `< 50 ms`)
