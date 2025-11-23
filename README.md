# Bitcoin Fiyat Tahmini – MacroMinds

Bu proje, FET445 Veri Madenciliği dersi kapsamında, **ABD makroekonomik göstergeleri** ve **finansal piyasa verilerini** kullanarak **Bitcoin (BTC-USD)** fiyatının farklı zaman ufuklarında tahmin edilmesini amaçlamaktadır.

## 1. Proje Bilgileri

- **Ders:** FET445 – Veri Madenciliği
- **Dönem:** 2025–2026 Güz Dönemi
- **Grup Adı:** MacroMinds

**Grup Üyeleri:**

| Öğrenci No     | İsim                        | Görevler (Kısaca)                                   |
|----------------|-----------------------------|-----------------------------------------------------|
| 22040101116    | Khaiitmurod Khabibullayev  | Veri birleştirme, EDA, Linear Regression + DT       |
| 22040101002    | Abdumajid Abdulkhaev       | Ridge, KNN, RFE tabanlı feature selection           |
| 22040101139    | Diyorjon Ochilov           | MI tabanlı feature selection, LinearRegression + DT |
| 22040101043    | İbrahim Halil Yanaç        | Ridge + KNN, PCA deneyleri                          |
| 22040101123    | Yesset Yelebayev           | Lasso, SVR, Lasso-based feature selection           |

---

## 2. Problem Tanımı

Amaç, **Bitcoin'in gelecekteki fiyatını**, hem kendi geçmiş fiyatları hem de ABD ekonomisine ait makroekonomik göstergeler yardımıyla tahmin etmektir.

Tahmin edilen 4 farklı hedef değişken (target) vardır:

- `Target_1d`  → 1 gün sonrası BTC kapanış fiyatı
- `Target_7d`  → 7 gün sonrası BTC kapanış fiyatı
- `Target_30d` → 30 gün sonrası BTC kapanış fiyatı
- `Target_365d` → 365 gün sonrası BTC kapanış fiyatı

Bu, bir **zaman serisi regresyon problemi** olarak tasarlanmıştır.

---

## 3. Kullanılan Veri Setleri

Veriler iki ana kaynaktan elde edilmiştir:

1. **Yahoo Finance**
   - `BTC-USD` (Bitcoin fiyatı)
   - `^GSPC` (S&P 500 endeksi)
   - `^VIX` (Volatilite endeksi)
   - `GOLD`, `GC=F` (Altın)
   - `IVV` (S&P500 ETF)
   - `DXY` (Dolar endeksi)
   - `EURUSD=X` (EUR/USD kuru)

2. **FRED (Federal Reserve Economic Data)**
   - `CPI` (Tüketici fiyat endeksi)
   - `UNRATE` (İşsizlik oranı)
   - `PAYEMS` (Tarım dışı istihdam)
   - `GDP` (GSYİH)
   - `STLFSI2` (Finansal stres endeksi)
   - `WALCL` (FED bilanço büyüklüğü)
   - `ECBDFR` (Faiz oranları / politika faizleri)
   - `FEDFUNDS`, `ZQ=F` (Faiz ve faiz beklentileri)

Tüm seriler **tarih bazlı** olacak şekilde hizalanmış ve **günlük frekansa** dönüştürülmüştür. Eksik değerler için linear interpolation kullanılmıştır.

---

## 4. Proje Yapısı

```text
.
├── README.md                      # Bu dosya
├── requirements.txt               # Kullanılan temel Python paketleri
│
├── data/
│   ├── raw datasets               # Orjinal veri setleri
│   ├── merged_final.csv           # Tüm feature'ların ve target'ların birleştirilmiş hali
├── results/
    ├── results_final_22040101116_khaiitmurod.csv
    ├── results_final_22040101002_abdumajid.csv
    ├── results_final_22040101139_diyorjon.csv
    ├── results_final_22040101043_ibrahim.csv
    ├── results_final_22040101123_yesset.csv
│
├── notebooks/
│   ├── FET445_22040101116_MacroMinds_1.ipynb
│   ├── FET445_22040101002_MacroMinds_2.ipynb
│   ├── FET445_22040101139_MacroMinds_3.ipynb
│   ├── FET445_22040101043_MacroMinds_4.ipynb
│   └── FET445_22040101123_MacroMinds_5.ipynb
│
└── report/
    └── FET445_MacroMinds_ProjectOutline.pdf
