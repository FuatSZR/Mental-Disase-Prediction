# Mental Sağlık Durumu Tespiti için Metin Sınıflandırma Projesi
<p align="center">
  <img src="mental_health.jpg" alt="Proje Kapak Fotoğrafı" width="500">
</p>

[![Lisans](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) 
## Özet

Bu proje, kullanıcıların çevrimiçi yorumları analiz edilerek Anksiyete, Depresyon gibi mental sağlık sorunlarına sahip olup olmadıklarını tespit etmeyi amaçlamaktadır. Projede, metin verilerini ön işlemede **Bag of Words (BoW)** ve **TF-IDF** algoritmaları kullanılmış ve sınıflandırma için **Naive Bayes** ve **Destek Vektör Makinesi (SVM)** algoritmalarının farklı çekirdekleri denenerek toplamda 12 farklı model elde edilmiştir. Yapılan performans değerlendirmeleri sonucunda, **TF-IDF** öznitelik çıkarımı ve **sigmoid çekirdekli Destek Vektör Makinesi (SVM)** algoritması kombinasyonunun **0.925 doğruluk** ve **0.925 F1 skoru** ile en iyi performansı gösterdiği belirlenmiştir.

## Projenin Amacı

Bu projenin temel amacı, çevrimiçi platformlardaki kullanıcıların yazılı yorumlarını kullanarak, bu kişilerin potansiyel olarak Anksiyete, Depresyon gibi mental sağlık sorunlarına sahip olup olmadıklarını otomatik olarak tespit etmektir. İnternet kullanımının yaygınlığı sayesinde, sosyal medya ve forumlar gibi platformlarda paylaşılan duygusal ifadeler, zihinsel sağlık durumlarını anlamak için değerli bir veri kaynağı sunmaktadır. Bu proje, bu tür verileri analiz ederek, otomatik bir sınıflandırma sistemi geliştirmeyi ve mental sağlık değerlendirme süreçlerine destek olmayı hedeflemektedir.

## Projenin Adımları

1.  **Veri Toplama:**
    * Kaggle üzerinden elde edilen "**Mental Health Corpus**" veri seti kullanılmıştır.
    * Veri seti, kullanıcı yorumlarını ve bu kullanıcıların mental sağlık durumunu (0: yok, 1: var) belirten iki kolondan oluşmaktadır.
    * Toplamda **27972** eşsiz veri bulunmaktadır.

2.  **Veri Ön İşleme ve Öznitelik Çıkarımı:**
    * Kullanılan ön işleme adımları:
        1.  **Metin Temizleme (Text Cleaning):** Gereksiz karakterler, noktalama işaretleri, sayılar ve özel semboller kaldırılmış, metin büyük/küçük harf dönüşümü uygulanmıştır.
        2.  **Tokenizasyon:** Metinler kelime düzeyinde token'lara ayrılmıştır.
        3.  **Stop Words Kaldırma:** Dilin yaygın ve anlamsız kelimeleri (örneğin, "bir", "ve", "ama") metinden çıkarılmıştır.
        4.  **N-Gram Oluşturma (Opsiyonel):** Ardışık kelime grupları oluşturularak bağlamsal bilgiyi yakalama potansiyeli değerlendirilmiştir.
        5.  **Stemming veya Lemmatization:** Kelimeler kök formlarına indirgenerek farklı çekimlerin aynı anlamı taşıması sağlanmıştır.
    * Öznitelik çıkarımı için kullanılan algoritmalar:
        1.  **Bag of Words (BoW):** Metinlerdeki kelimelerin frekanslarını temel alarak bir vektör gösterimi oluşturulmuştur. Kelime sırası ve bağlamı göz ardı edilmiştir.
        2.  **TF-IDF (Term Frequency-Inverse Document Frequency):** Kelimelerin belge içindeki frekansını ve tüm belgelerdeki yaygınlığını dikkate alarak kelimelerin önemini ölçen bir vektör gösterimi oluşturulmuştur.

3.  **Model Geliştirme:**
    * Aşağıdaki makine öğrenmesi algoritmaları ve çekirdekleri kullanılarak modeller geliştirilmiştir:
        * **Destek Vektör Makinesi (SVM):**
            * Lineer Çekirdek (Linear Kernel)
            * Polinomal Çekirdek (Polynomial Kernel)
            * Radyal Baz Fonksiyonu Çekirdeği (RBF Kernel)
            * Sigmoid Çekirdek (Sigmoid Kernel)
        * **Naive Bayes:**
            * Multinominal Naive Bayes
            * Bernoulli Naive Bayes
    * Bu 6 farklı model, hem BoW hem de TF-IDF ile ayrı ayrı eğitilerek toplamda **12 farklı sonuç** elde edilmiştir.

4.  **Performans Değerlendirmesi:**
    * Geliştirilen tüm modellerin performansları doğruluk (Accuracy) ve F1 skoru gibi çeşitli metrikler kullanılarak karşılaştırılmıştır.
    * En yüksek performansa sahip model belirlenmiştir.

## Değerlendirme Sonuçları

### Bag of Words (BoW) ile Elde Edilen Sonuçlar


* **Multinominal Naive Bayes:** Doğruluk: 0.850, F1 Skoru: 0.867
* **Bernoulli Naive Bayes:** Doğruluk: 0.799, F1 Skoru: 0.770
* **Support Vector Machine (linear kernel):** Doğruluk: 0.905, F1 Skoru: 0.904
* **Support Vector Machine (polinomal kernel):** Doğruluk: 0.700, F1 Skoru: 0.586

### TF-IDF ile Elde Edilen Sonuçlar


* **Multinominal Naive Bayes:** Doğruluk: 0.864, F1 Skoru: 0.877
* **Bernoulli Naive Bayes:** Doğruluk: 0.832, F1 Skoru: 0.813
* **Support Vector Machine (linear kernel):** Doğruluk: 0.912, F1 Skoru: 0.913
* **Support Vector Machine (polinomal kernel):** Doğruluk: 0.847, F1 Skoru: 0.849
* **Support Vector Machine (RBF kernel):** Doğruluk: 0.915, F1 Skoru: 0.916
* **Support Vector Machine (sigmoid kernel):** Doğruluk: 0.925, F1 Skoru: 0.925

## Sonuç

Yapılan değerlendirmeler sonucunda, **TF-IDF** öznitelik çıkarımı ile **sigmoid çekirdekli Destek Vektör Makinesi (SVM)** algoritmasının kombinasyonu, **0.925 doğruluk** ve **0.925 F1 skoru** elde ederek diğer tüm kombinasyonlardan daha üstün bir performans sergilemiştir.

## Anahtar Kelimeler

Mental Sağlık, Anksiyete, Depresyon, Makine Öğrenimi, Metin Sınıflandırma, Bag of Words, TF-IDF, Naive Bayes, Destek Vektör Makinesi (SVM), Hipertarametre Ayarlama, Metin Analizi

## Lisans

Bu proje [MIT Lisansı](https://opensource.org/licenses/MIT) altında lisanslanmıştır. ---
