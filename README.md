# akbank-dl-bootcamp-proje
Derin Öğrenme Bootcamp Projesi

# Projenin Amacı  

Bu projenin amacı, beyin MRI görüntülerinden tümör türlerini otomatik olarak sınıflandıran bir derin öğrenme modeli geliştirmektir. Manuel inceleme uzmanlık ve zaman gerektirdiğinden, yapay zekâ desteğiyle daha hızlı ve güvenilir sonuçlar elde edilmesi hedeflenmiştir.  

Ayrıca proje kapsamında hiperparametre optimizasyonu, overfitting/underfitting analizi ve model performansının değerlendirilmesi de yapılmıştır. Böylece yalnızca bir sınıflandırıcı değil, aynı zamanda derin öğrenme sürecinin farklı aşamalarını ele alan bütüncül bir çalışma ortaya konmuştur.


# Veri Seti Hakkında Bilgi  

Projede kullanılan veri seti, beyin MRI görüntülerinden oluşmaktadır. Görseller üç farklı tümör türünü içermektedir:  

- **Glioma**  
- **Meningioma**  
- **Pituitary (Beyin tümörü)**  

Veri seti eğitim, doğrulama ve test alt kümelerine ayrılarak modelin hem öğrenme hem de genelleme performansı ölçülmüştür. Görseller, modelin girdi boyutuna uyacak şekilde yeniden boyutlandırılmış ve normalizasyon işlemi uygulanmıştır.  


# Kullanılan Yöntemler  

Bu projede derin öğrenme tabanlı bir **Convolutional Neural Network (CNN)** modeli kullanılmıştır.  

- Görsellerin ön işlenmesinde **yeniden boyutlandırma** ve **normalize etme** adımları uygulanmıştır.  
- Model mimarisinde **Conv2D, MaxPooling2D, Flatten, Dense** katmanları ve **Dropout** tekniği kullanılmıştır.  
- **Adam optimizer** ve **categorical crossentropy loss** ile eğitim yapılmıştır.  
- Modelin performansı **accuracy, loss grafikleri**, **confusion matrix**, **classification report** ve **hiperparametre optimizasyonu** (dropout oranı, learning rate denemeleri) ile değerlendirilmiştir.


# Elde Edilen Sonuçlar  

- Modelin genel doğruluk (accuracy) skoru **%82** olarak elde edilmiştir.  
- Eğitim sırasında **accuracy artarken** ve **loss azalırken**, doğrulama verilerinde dalgalanmalar gözlemlenmiştir. Bu durum **overfitting riskine** işaret etmiş, ancak dropout gibi yöntemlerle dengelenmiştir.  

- **Confusion matrix** sonuçları incelendiğinde:  
  - **Brain Tumor** sınıfı model tarafından en başarılı şekilde ayırt edilmiştir (**372 doğru tahmin**, yalnızca **41 hata**).  
  - **Brain Glioma** sınıfında model genel olarak başarılıdır (**302 doğru tahmin**), ancak **78 örnek meningioma ile karıştırılmıştır**.  
  - **Brain Meningioma** sınıfında ise en fazla hata görülmüştür (**321 doğru tahmin**, fakat **90’dan fazla hata** ile özellikle glioma ve tumor sınıflarıyla karışıklık yaşanmıştır).  

- **Hiperparametre denemeleri** sonucunda:  
  - **Dropout=0.5, Learning Rate=0.001** kombinasyonu en iyi sonucu vermiştir.  
  - Daha düşük learning rate underfitting’e yol açmıştır, daha düşük dropout ise overfitting riskini artırmıştır.  

Genel olarak, modelin doğruluk skoru tatmin edici düzeydedir ve özellikle **Brain Tumor** sınıfında güçlü performans sergilerken, **Brain Meningioma** sınıfında ek iyileştirmelere ihtiyaç vardır.
