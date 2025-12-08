## 🧠 Alzheimer's Disease Prediction Project Summary

# 🧠 Alzheimer Hastalığı Tahmin Projesi Özeti 

Bu proje, hasta sağlık verileri, klinik ölçümler ve yaşam tarzı faktörlerini kullanarak Alzheimer hastalığının varlığını tahmin etmeyi amaçlamaktadır. Çeşitli Makine Öğrenmesi ve Derin Öğrenme modelleri ile yüksek sınıflandırma doğruluğu hedeflenmiştir.

## 📌 Proje İş Akışı

### 1. Veri Anlama ve Temizleme
* **Veri Seti:** `alzheimers_disease_data.csv` yüklendi ve incelendi.
* **İlk Kontroller:** Veri setinde eksik (NaN) veya tekrar eden kayıt bulunmadı.
* **Veri Temizleme:** `DoctorInCharge` ve `PatientID` gibi model için işlevsiz sütunlar çıkarıldı.
* **Gruplandırma:** `Age` (Yaş) sütunu kategorik gruplara ("60-70", "71-80", "81-90") ayrıldı ve bu gruplar sayısal olarak kodlandı (Ordinal Encoding).

### 2. Özellik Mühendisliği (Feature Engineering)
* Yeni tıbbi göstergeler türetildi:
    * **Kan Basıncı:** `PulsePressure` (Sistolik - Diyastolik) hesaplandı.
    * **Kolesterol Oranları:** `LDL_HDL_Ratio`, `TG_HDL_Ratio` ve `NonHDL_Cholesterol` oluşturuldu.
    * **Toplu Hastalık/Semptom Sayımı:** `ChronicDiseaseCount` ve `SymptomCount` eklendi.

### 3. Keşifçi Veri Analizi (EDA)
* Hedef değişkenin (`Diagnosis`) dağılımı görselleştirildi (Sınıf dengesizliği mevcut).
* Sayısal özelliklerin dağılımları histogramlarla görselleştirildi.
* **Korelasyon Analizi:** Özellikler ile teşhis arasındaki pozitif ve negatif korelasyonları belirlemek için ısı haritası (heatmap) çıkarıldı.

### 4. Özellik Seçimi ve Ölçekleme
* **RFE (Recursive Feature Elimination):** Random Forest algoritması kullanılarak en etkili **12 özellik** (örn. `MemoryComplaints`, `FunctionalAssessment`, `MMSE`, `ADL`) seçildi.
* **Ölçekleme:** Seçilen özellikler **MinMaxScaler** ile 0-1 aralığına ölçeklendirildi.

### 5. Model Geliştirme ve Karşılaştırma
* Veri, %75 eğitim ve %25 test olarak bölündü.
* **GridSearchCV** ile hiperparametre optimizasyonu yapılarak klasik Makine Öğrenmesi modelleri eğitildi.

| Algoritma | Precision | Recall | F1-Score |
| :--- | :--- | :--- | :--- |
| **Random Forest** | 0.95 | 0.92 | **0.93** |
| **XGBoost** | 0.94 | 0.93 | **0.93** |
| Gradient Boosting | 0.94 | 0.92 | 0.93 |
| Decision Tree | 0.91 | 0.91 | 0.91 |
| SVC | 0.85 | 0.81 | 0.83 |

* **Derin Öğrenme (YSA):** Keras kullanılarak 3 katmanlı basit bir Yapay Sinir Ağı (ANN) eğitildi.
    * Test F1-Skoru: **0.86 - 0.90** (Epok sayısına göre değişir).

### 6. Sonuç
* En iyi performansı **Random Forest** ve **XGBoost** algoritmaları göstermiştir (F1-Skoru $\approx 0.93$).
* Tüm modeller, yaşlı hastalarda Alzheimer teşhisi için yüksek doğruluk potansiyeli sergilemiştir.

***

# 🇬🇧 Alzheimer's Disease Prediction Project Summary

This project aims to predict the presence of Alzheimer's disease using patient health data, clinical measurements, and lifestyle factors. High classification accuracy was targeted using various Machine Learning and Deep Learning models.

## 📌 Project Workflow

### 1. Data Understanding & Cleaning
* **Dataset:** The `alzheimers_disease_data.csv` was loaded and inspected.
* **Initial Checks:** No missing (NaN) or duplicate records were found in the dataset.
* **Data Cleaning:** Irrelevant columns like `DoctorInCharge` and `PatientID` were removed.
* **Binning:** The `Age` column was grouped into categorical bins ("60-70", "71-80", "81-90") and subsequently numerically encoded (Ordinal Encoding).

### 2. Feature Engineering
* New medical indicators were derived to potentially improve model performance:
    * **Blood Pressure:** `PulsePressure` (Systolic - Diastolic) was calculated.
    * **Cholesterol Ratios:** `LDL_HDL_Ratio`, `TG_HDL_Ratio`, and `NonHDL_Cholesterol` were created.
    * **Aggregate Counts:** `ChronicDiseaseCount` and `SymptomCount` were added to summarize medical history.

### 3. Exploratory Data Analysis (EDA)
* The distribution of the target variable (`Diagnosis`) was visualized (showing class imbalance).
* Distributions of numerical features were visualized using histograms.
* **Correlation Analysis:** A heatmap was generated to identify positive and negative correlations between features and the diagnosis.

### 4. Feature Selection and Scaling
* **RFE (Recursive Feature Elimination):** The top **12 most influential features** (e.g., `MemoryComplaints`, `FunctionalAssessment`, `MMSE`, `ADL`) were selected using the Random Forest algorithm to reduce dimensionality and prevent overfitting.
* **Scaling:** The selected features were scaled to a 0-1 range using **MinMaxScaler**.

### 5. Model Development and Comparison
* The data was split into 75% training and 25% testing sets.
* Classical Machine Learning models (Random Forest, XGBoost, SVC, etc.) were trained and optimized using **GridSearchCV**.

| Algorithm | Precision | Recall | F1-Score |
| :--- | :--- | :--- | :--- |
| **Random Forest** | 0.95 | 0.92 | **0.93** |
| **XGBoost** | 0.94 | 0.93 | **0.93** |
| Gradient Boosting | 0.94 | 0.92 | 0.93 |
| Decision Tree | 0.91 | 0.91 | 0.91 |
| SVC | 0.85 | 0.81 | 0.83 |

* **Deep Learning (ANN):** A 3-layer Sequential Artificial Neural Network (ANN) was trained using Keras.
    * Test F1-Score: **0.86 - 0.90** (Varies by epoch count).

### 6. Conclusion
* **Random Forest** and **XGBoost** demonstrated the best performance (F1-Score $\approx 0.93$).
* All implemented models showed high potential for accurately classifying Alzheimer's diagnoses in older patients.
