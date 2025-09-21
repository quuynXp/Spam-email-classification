# Spam Email Classification (WEKA)

A machine learning project to classify emails as **spam** or **non-spam (ham/normal)** using **text mining techniques** in **WEKA**.  
The project evaluates two classic algorithms — **C4.5 (J48 Decision Tree)** and **Naive Bayes** — on a dataset of 5,180 emails.

---

## 📌 Introduction

Every day, email users receive hundreds of spam messages with new content and spoofed sender addresses generated automatically by bots. Traditional filtering techniques (blacklists/whitelists of domains, IPs, or addresses) are ineffective at scale.  

By applying **text mining and machine learning** to email classification, we can achieve higher accuracy and adapt to new spam trends. Moreover, classification can also capture dependencies such as geographic or topical clustering of spam.

---

## 📊 Dataset

- Total: **5,180 emails** distributed across three folders:  
  - `norm` → normal emails  
  - `ham` → non-spam but potentially harmful  
  - `spam` → spam emails  

- Key dataset features:  
  1. Frequency of specific words or characters appearing in emails.  
  2. Run-length attributes (55–57) measuring the length of consecutive uppercase character sequences.  

The dataset was preprocessed into CSV and then converted into **ARFF** format for use in WEKA.

---

## 🧠 Algorithms & Implementation

### 1. C4.5 (J48 Decision Tree)

- The **C4.5 algorithm** (Ross Quinlan) is an extension of ID3 and is widely used to generate decision trees for classification tasks.  
- Implemented as **J48** in WEKA.  
- Ranked among the **Top 10 Data Mining Algorithms of All Time**.  
- Produces decision trees that can be visualized and interpreted.  

**Example Decision Tree:**  
![Decision Tree Example](https://github.com/quuynXp/Spam-email-classification/images/24_vi_du_cay_quyet_dinh.JPG)

### 2. Naive Bayes

- Probabilistic classifier based on **Bayes’ Theorem**.  
- Assumes independence between predictor features.  
- Well-suited for text classification problems due to simplicity and scalability.  

**Naive Bayes Illustration:**  
![Naive Bayes](https://github.com/quuynXp/Spam-email-classification/images/23_thuat_toan_NaiveBayes.png)

---

## ⚙️ Setup & How to Run

1. **Install WEKA**  
   - Download from [WEKA Official Site](http://www.cs.waikato.ac.nz/ml/weka/downloading.html).  

2. **Prepare the dataset**  
   - Original dataset: 5,180 text files organized into 3 folders (`norm`, `ham`, `spam`).  
   - Convert dataset into CSV, then into **ARFF** (WEKA format).  

   ![CSV Conversion](https://github.com/quuynXp/Spam-email-classification/images/3_chuyen_file_csv_thanh_arff.png)

3. **Train & Evaluate with J48**  
   - Load dataset into WEKA.  
   - Select **J48 classifier**.  
   - Run training with different **percentage split options (66%, 80%, 90%)**.  

   **Results:**  
   - Full dataset → **98% accuracy**  
   - 66% split → **93% accuracy**  
   - 80% split → **94% accuracy**  
   - 90% split → **89% accuracy**

   ![Training Results](https://github.com/quuynXp/Spam-email-classification/images/9_ket_qua_training_1.png)

4. **Test on Custom Dataset**  
   - Create a test dataset from your own email samples.  
   - Apply trained model → WEKA outputs predicted labels.  

   ![Testing Results](https://github.com/quuynXp/Spam-email-classification/images/16_kiem_thu_bang_file_test.png)

5. **Compare with Naive Bayes**  
   - Repeat the process with **Naive Bayes** classifier.  
   - Similar experiments with percentage splits (66%, 80%, 90%) confirm robust performance.  

   ![Naive Bayes Results](https://github.com/quuynXp/Spam-email-classification/images/19_ket_qua_thuat_toan_NaiveBayesMultinomailText_66%.png)

---

## 📈 Results & Observations

- **J48 Decision Tree** achieved up to **98% accuracy** with the full dataset.  
- **Naive Bayes** provided competitive results, sometimes more stable across splits.  
- Both methods demonstrate the effectiveness of **text mining + ML** for spam detection.  
- Accuracy can be further improved with:  
  - Larger datasets  
  - Feature engineering (ignoring dictionary words, focusing on spam keywords)  
  - Ensemble methods  

---

## 🔐 Conclusion

Email spam remains a widespread issue with significant risks to user privacy and security. While many anti-spam tools exist, **text classification remains one of the most effective strategies**.  

By leveraging machine learning models like **J48** and **Naive Bayes**, we can automatically classify spam with high accuracy and adapt to evolving spam patterns.

---

## 📚 References

1. Anderson, A., Corney, M., de Vel, O., Mohay, G. *Identifying the Authors of Suspect E-mail*. Communications of the ACM, 2001.  
2. Hershkop, S., Wang, K., Lee, W., Nimeskern, O., Creamer, G., Rowe, R. *Email Mining Toolkit Technical Manual*, Columbia University, 2006.  
3. Bron, C., Kerbosch, J. *Algorithm 457: Finding all cliques of an undirected graph.* CACM, 1973.  
4. Zhou, D., Zhang, Y., et al. *Towards Discovering Organizational Structure from Email Corpus*. ICMLA 2005.  
5. Carenini, G., Ng, R. T., Zhou, X. *Scalable Discovery of Hidden Emails from Large Folders*. UBC, Canada.  
6. Chen, H., et al. *Discover The Power of Social and Hidden Curriculum to Decision Making: Experiments with Enron Email and Movie Newsgroups*. ICMLA 2007.  
