
# Makine Öğrenmesi ile Phishing Tespiti
# Phishing Website Detection Using Machine Learning

Makine öğrenmesi algoritmaları kullanılarak phishing (oltalama) web sitelerinin sınıflandırılması, özellik analizi ve model performanslarının karşılaştırılması üzerine geliştirilmiş bir veri bilimi projesi.

A machine learning project focused on phishing website classification, feature analysis, and comparative evaluation of classification algorithms.

**Teknolojiler / Technologies:** Python | Scikit-learn | Pandas | NumPy | SciPy | Matplotlib | Seaborn | Jupyter Notebook

---

# Türkçe

## Proje Hakkında

Bu proje, phishing (oltalama) saldırılarıyla ilişkili web sitelerinin makine öğrenmesi yöntemleri kullanılarak sınıflandırılması amacıyla geliştirilmiştir.

Çalışmada, web sitelerinin çeşitli teknik özelliklerini içeren bir veri seti kullanılarak farklı sınıflandırma algoritmaları eğitilmiş ve karşılaştırılmıştır.

Proje kapsamında veri ön işleme, keşifsel veri analizi, sınıflandırma modellerinin geliştirilmesi, özellik önem analizi, hiperparametre optimizasyonu ve performans değerlendirme işlemleri gerçekleştirilmiştir.

Çalışmada üç farklı makine öğrenmesi algoritması kullanılmıştır:

- Logistic Regression
- K-Nearest Neighbors (KNN)
- Random Forest

## Projenin Amacı

- Web sitelerini teknik özelliklerine göre sınıflandırmak
- Makine öğrenmesi algoritmalarının phishing tespitindeki performanslarını karşılaştırmak
- Veri ön işleme ve özellik analizi yöntemlerini uygulamak
- Hiperparametre optimizasyonunun model performansına etkisini incelemek
- Sınıflandırma sonuçlarını farklı performans metrikleriyle değerlendirmek

## Veri Seti

Projede `PhishingData.arff` veri seti kullanılmıştır.

Veri seti 1.353 kayıt ve 9 giriş değişkeni içermektedir.

### Kullanılan Özellikler

| Özellik | Açıklama |
|---|---|
| SFH | Server Form Handler özelliği |
| popUpWidnow | Açılır pencere davranışı |
| SSLfinal_State | SSL bağlantı durumu |
| Request_URL | URL üzerinden kaynak isteği özellikleri |
| URL_of_Anchor | Bağlantıların yönlendirme özellikleri |
| web_traffic | Web sitesi trafik bilgisi |
| URL_Length | URL uzunluğu |
| age_of_domain | Alan adı yaşı |
| having_IP_Address | URL içerisinde IP adresi kullanımı |

### Hedef Değişken

`Result` sütunu web sitelerinin sınıflandırılması için kullanılmıştır.

Veri setinde üç farklı sınıf etiketi bulunmaktadır:

- -1
- 0
- 1

Bu nedenle çalışma üç sınıflı bir sınıflandırma problemidir.

### Sınıf Dağılımı

| Sınıf | Kayıt Sayısı |
|---|---:|
| -1 | 702 |
| 0 | 103 |
| 1 | 548 |
| Toplam | 1.353 |

Sınıflar arasında dengesizlik bulunduğundan model değerlendirmesinde yalnızca doğruluk oranı değil, sınıf bazlı metrikler de önem taşımaktadır.

## Kullanılan Teknolojiler

| Teknoloji | Kullanım Amacı |
|---|---|
| Python | Model geliştirme ve veri analizi |
| Pandas | Veri işleme ve temizleme |
| NumPy | Sayısal hesaplamalar |
| SciPy | ARFF veri setinin yüklenmesi |
| Scikit-learn | Makine öğrenmesi modelleri ve değerlendirme |
| Matplotlib | Grafik oluşturma |
| Seaborn | Veri görselleştirme |
| Jupyter Notebook | Analiz ve model geliştirme ortamı |

## Uygulanan Yöntemler

### 1. Veri Ön İşleme

İlk aşamada ARFF formatındaki veri seti `scipy.io.arff` kullanılarak yüklenmiş ve Pandas DataFrame yapısına dönüştürülmüştür.

Bu süreçte:

- Veri tipleri incelenmiştir.
- Eksik değer kontrolü yapılmıştır.
- Sınıf dağılımları analiz edilmiştir.
- Kategorik gösterimler sayısal değerlere dönüştürülmüştür.
- Giriş değişkenleri ve hedef değişken ayrılmıştır.

Veri seti %80 eğitim ve %20 test olacak şekilde ayrılmıştır.

### 2. Logistic Regression

Logistic Regression modeli kullanılarak web sitelerinin üç sınıftan hangisine ait olduğu tahmin edilmiştir.

Model, eğitim veri seti üzerinde eğitilmiş ve test verileri üzerinde değerlendirilmiştir.

### 3. K-Nearest Neighbors (KNN)

K-Nearest Neighbors algoritması kullanılarak benzer özelliklere sahip kayıtların sınıflandırılması gerçekleştirilmiştir.

İlk modelde komşu sayısı 5 olarak belirlenmiştir.

### 4. Random Forest

Random Forest algoritması kullanılarak birden fazla karar ağacına dayalı sınıflandırma modeli geliştirilmiştir.

Modelde 100 karar ağacı kullanılmıştır.

Ayrıca Random Forest üzerinden özellik önem skorları hesaplanarak giriş değişkenlerinin sınıflandırma üzerindeki göreli etkileri incelenmiştir.

### 5. Özellik Önem Analizi

Random Forest modelinin `feature_importances_` özelliği kullanılarak değişkenlerin önem skorları hesaplanmıştır.

Önem skoru 0.01'in altında kalan değişkenleri belirlemeye yönelik bir analiz yapılmıştır.

Kaydedilen deney sonucunda bu eşik altında herhangi bir değişken bulunmamıştır.

### 6. Hiperparametre Optimizasyonu

GridSearchCV kullanılarak Logistic Regression ve KNN algoritmalarının hiperparametreleri araştırılmıştır.

Logistic Regression için incelenen parametreler:

- C
- solver

KNN için incelenen parametreler:

- n_neighbors
- weights

Optimizasyon aşamasında 5 katlı çapraz doğrulama kullanılmıştır.

Notebook'ta kaydedilen en iyi parametreler:

| Model | Parametre | Değer |
|---|---|---|
| Logistic Regression | C | 10 |
| Logistic Regression | solver | lbfgs |
| KNN | n_neighbors | 5 |
| KNN | weights | distance |

## Model Performansları

Modellerin ayrılmış test veri setinde elde edilen doğruluk sonuçları aşağıdaki gibidir.

| Model | Accuracy |
|---|---:|
| Logistic Regression | %83,39 |
| K-Nearest Neighbors | %85,24 |
| Random Forest | %87,82 |

Bu deneyde en yüksek genel doğruluk oranı Random Forest modeliyle elde edilmiştir.

Sonuçlar notebook içerisinde kayıtlı test çıktılarından alınmıştır.

### Performans Değerlendirme Metrikleri

Modeller aşağıdaki metriklerle değerlendirilmiştir:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion Matrix

Sınıflar arasındaki dengesizlik nedeniyle genel accuracy değeri tek başına yeterli değildir.

Özellikle daha az örnek içeren 0 sınıfının performansı da değerlendirme açısından önemlidir.

## Görselleştirme ve Analiz

Proje kapsamında aşağıdaki analizler gerçekleştirilmiştir:

- Sınıf dağılımı grafikleri
- Confusion Matrix görselleştirmeleri
- Modellerin doğruluk oranlarının karşılaştırılması
- Random Forest özellik önem grafikleri
- Hiperparametre optimizasyonu sonrası model karşılaştırmaları

## Proje Yapısı

```text
Makine_ogrenmesi_ile_Phishing_Tespiti/
└── Website Phishing/
    ├── PhishingData.arff
    └── Website Phishing.ipynb
```

## Kurulum ve Çalıştırma

### Gereksinimler

- Python 3
- Jupyter Notebook
- Pandas
- NumPy
- SciPy
- Scikit-learn
- Matplotlib
- Seaborn

### Projeyi Klonlama

```bash
git clone https://github.com/sumeyyeduz35/Makine_ogrenmesi_ile_Phishing_Tespiti.git
cd Makine_ogrenmesi_ile_Phishing_Tespiti
```

### Gerekli Kütüphaneleri Yükleme

```bash
python -m pip install notebook pandas numpy scipy scikit-learn matplotlib seaborn
```

### Notebook'u Çalıştırma

```bash
jupyter notebook
```

Jupyter arayüzünde `Website Phishing` klasörünü açın ve `Website Phishing.ipynb` dosyasını çalıştırın.

## Teknik Sınırlamalar

- Model sonuçları kullanılan veri seti ve eğitim/test ayrımına bağlıdır.
- Veri seti üç sınıflı bir sınıflandırma problemi içermektedir.
- Sınıflar arasında örnek sayısı farklılıkları bulunmaktadır.
- Özellik önemine dayalı seçim işlemlerinin eğitim verisiyle sınırlandırılması, daha güvenilir değerlendirme sağlayabilir.
- Modellerin farklı veri setleri ve gerçek dünya örnekleri üzerinde ayrıca doğrulanması gerekir.

## Proje Durumu

**Tamamlandı — Deneysel makine öğrenmesi projesi.**

Bu çalışma; veri ön işleme, sınıflandırma algoritmaları, özellik önem analizi, hiperparametre optimizasyonu ve model karşılaştırması üzerine uygulamalı deneyim sunmaktadır.

---

# English

## About the Project

This project focuses on classifying phishing-related websites using supervised machine learning algorithms.

A dataset containing technical website characteristics is used to train, evaluate, and compare multiple classification models.

The project covers data preprocessing, exploratory analysis, machine learning model development, feature importance analysis, hyperparameter optimization, and performance evaluation.

Three machine learning algorithms are investigated:

- Logistic Regression
- K-Nearest Neighbors (KNN)
- Random Forest

## Project Objectives

- Classify websites based on technical characteristics
- Compare machine learning algorithms for phishing-related website classification
- Apply data preprocessing and feature analysis techniques
- Explore hyperparameter optimization
- Evaluate classification results using multiple performance metrics

## Dataset

The project uses the `PhishingData.arff` dataset.

The dataset contains 1,353 records and 9 input features.

### Input Features

| Feature | Description |
|---|---|
| SFH | Server Form Handler characteristics |
| popUpWidnow | Pop-up window behavior |
| SSLfinal_State | SSL connection characteristics |
| Request_URL | Resource request URL characteristics |
| URL_of_Anchor | Anchor URL characteristics |
| web_traffic | Website traffic information |
| URL_Length | URL length |
| age_of_domain | Domain age |
| having_IP_Address | IP address usage in URLs |

### Target Variable

The `Result` column is used as the classification target.

The dataset contains three class labels:

- -1
- 0
- 1

Therefore, the project addresses a three-class classification problem.

### Class Distribution

| Class | Samples |
|---|---:|
| -1 | 702 |
| 0 | 103 |
| 1 | 548 |
| Total | 1,353 |

The class distribution is imbalanced, making class-specific evaluation metrics particularly important.

## Technologies Used

| Technology | Purpose |
|---|---|
| Python | Model development and analysis |
| Pandas | Data processing |
| NumPy | Numerical computations |
| SciPy | Loading ARFF files |
| Scikit-learn | Machine learning and evaluation |
| Matplotlib | Data visualization |
| Seaborn | Statistical visualization |
| Jupyter Notebook | Experimentation environment |

## Methodology

### 1. Data Preprocessing

The ARFF dataset is loaded using `scipy.io.arff` and converted into a Pandas DataFrame.

The preprocessing workflow includes:

- Data type inspection
- Missing value analysis
- Class distribution analysis
- Conversion of feature values to numerical types
- Separation of input features and the target variable

The dataset is divided into 80% training data and 20% test data.

### 2. Logistic Regression

A Logistic Regression classifier is trained to predict website categories.

The model is evaluated on the held-out test dataset.

### 3. K-Nearest Neighbors

KNN classification is performed based on similarities between observations.

The initial configuration uses five nearest neighbors.

### 4. Random Forest

A Random Forest classifier containing 100 decision trees is trained for the classification task.

The model is also used to examine feature importance scores.

### 5. Feature Importance Analysis

Feature importance values are calculated using the Random Forest model.

A threshold of 0.01 is applied to identify low-importance features.

The recorded analysis did not identify any features below this threshold.

### 6. Hyperparameter Optimization

GridSearchCV is used to explore parameter combinations for Logistic Regression and KNN.

Five-fold cross-validation is applied during optimization.

The recorded best parameters are:

| Model | Parameter | Value |
|---|---|---|
| Logistic Regression | C | 10 |
| Logistic Regression | solver | lbfgs |
| KNN | n_neighbors | 5 |
| KNN | weights | distance |

## Model Performance

The recorded test accuracy results are:

| Model | Accuracy |
|---|---:|
| Logistic Regression | 83.39% |
| K-Nearest Neighbors | 85.24% |
| Random Forest | 87.82% |

Random Forest achieved the highest overall test accuracy in this experiment.

These results are taken from the saved notebook outputs.

### Evaluation Metrics

The following metrics are used:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion Matrix

Due to the imbalanced class distribution, overall accuracy should not be interpreted as the only indicator of model quality.

Class-specific metrics, particularly those for the minority class, are important for evaluating performance.

## Visualization and Analysis

The project includes:

- Class distribution visualization
- Confusion matrix analysis
- Model accuracy comparisons
- Random Forest feature importance visualization
- Hyperparameter optimization comparisons

## Project Structure

```text
Makine_ogrenmesi_ile_Phishing_Tespiti/
└── Website Phishing/
    ├── PhishingData.arff
    └── Website Phishing.ipynb
```

## Installation and Usage

### Requirements

- Python 3
- Jupyter Notebook
- Pandas
- NumPy
- SciPy
- Scikit-learn
- Matplotlib
- Seaborn

### Clone the Repository

```bash
git clone https://github.com/sumeyyeduz35/Makine_ogrenmesi_ile_Phishing_Tespiti.git
cd Makine_ogrenmesi_ile_Phishing_Tespiti
```

### Install Dependencies

```bash
python -m pip install notebook pandas numpy scipy scikit-learn matplotlib seaborn
```

### Run the Notebook

```bash
jupyter notebook
```

Open the `Website Phishing` directory and run `Website Phishing.ipynb`.

## Technical Limitations

- Model performance depends on the dataset and the selected train-test split.
- The dataset represents a three-class classification problem.
- The class distribution is imbalanced.
- Feature selection should ideally be performed using training data only to prevent evaluation bias.
- Additional validation on independent datasets and real-world examples would be required before practical deployment.

## Project Status

**Completed — Experimental machine learning project.**

This project demonstrates practical experience with data preprocessing, classification algorithms, feature importance analysis, hyperparameter tuning, and comparative model evaluation.
