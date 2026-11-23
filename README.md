# Çevrimiçi Parekende - Talep Tahmini ve Zaman Serisi Analizi

## Proje Amacı
Bu projenin amacı, e-ticaret satış verileri üzerinde veri ön işleme, keşifsel veri analizi (EDA) ve zaman serisi modelleme tekniklerini (Holt-Winters / Exponential Smoothing) uygulayarak günlük talep tahmin modeli geliştirmek ve model performansını değerlendirmektir.

## Kullanılan Veri Seti
* **Veri Seti:** Online Retail Dataset (UCI Machine Learning Repository / Kaggle)
* **Kapsam:** Birleşik Krallık merkezli bir online perakende firmasının 2010–2011 yılları arasındaki tüm işlem kayıtlarını (fatura numarası, stok kodu, ürün tanımı, miktarı, birim fiyatı, müşteri ID, ülke ve fatura tarihi) içerir.

## Yöntemler ve İş Akışı
1. **Veri Ön İşleme (Data Preprocessing):**
   * Eksik `CustomerID` kayıtlarının ve hatalı fiyatların (`UnitPrice <= 0`) temizlenmesi.
   * Toplam harcama tutarını gösteren `TotalPrice = Quantity * UnitPrice` değişkeninin türetilmesi.
   * İade işlemlerinin (`Quantity < 0`) ve tarih formatlarının dönüştürülerek zaman serisine hazırlanması.
2. **Keşifsel Veri Analizi (EDA):**
   * Satış hacmine yön veren baskın pazar (UK) dışındaki uluslararası satış performansının ve ciro dağılımlarının incelenmesi/görselleştirilmesi.
3. **Zaman Serisi Modelleme (Demand Forecasting):**
   * Günlük bazda (`resample('D')`) toplam satışların çıkarılması ve verinin %80 Eğitim, %20 Test olarak ayrılması.
   * Holt-Winters Exponential Smoothing (Toplamsal, Karma ve Çarpımsal) modellerinin kurulması ve tahmin üretimi.
   * Model başarısının MAE, RMSE, MAPE ve WAPE metrikleri ile değerlendirilmesi.

## Elde Edilen Sonuçlar
* **EDA Bulguları:** İngiltere dışındaki pazarlarda en yüksek ciro katkısını sırasıyla Hollanda (Netherlands), İrlanda (EIRE), Almanya (Germany) ve Fransa (France) sağlamaktadır.
* **Zaman Serisi Performansı:** Günlük verideki yüksek oynaklık (gürültü) nedeniyle Holt-Winters modelleri additif ve multiplikatif trend/mevsimsellik bileşenlerinde yüksek sapma göstermiştir.
