# 🌍 Global Satış ve Kârlılık Analizi Raporu 

Bu proje; segment, ülke ve ürün bazlı finansal performans verilerini inceleyen, şirket yönetiminin stratejik kararlar almasını kolaylaştırmak amacıyla tasarlanmış **etkileşimli ve dinamik bir Power BI Dashboard** çalışmasıdır.

Veri setindeki yapısal bozukluklar, Türkçe karakter (encoding) hataları ve veri tipi uyumsuzlukları **Power Query (ETL)** aşamasında temizlenerek veri modeli analize hazır hale getirilmiştir. Rapor üzerindeki tüm hesaplamalar **DAX (Data Analysis Expressions)** mimarisiyle dinamik ölçülere (measures) dönüştürülmüştür.

---

## 📂 Veri Seti Hakkında

Bu projede kullanılan ham veriler, Kaggle üzerindeki küresel satış simülasyonu veri setinden alınmıştır. Orijinal veri kaynağına ve detaylarına aşağıdaki bağlantıdan ulaşabilirsiniz:

🔗 **Veri Kaynağı:** [Kaggle - Power BI Sample Data](https://www.kaggle.com/datasets/shwetankchaudhary/power-bi-sample-data)

---

## 📈 Proje Özeti ve Temel Bulgular

Proje kapsamında tasarlanan dashboard, şirketin operasyonel hacmini ve kârlılık yapısını net bir şekilde ortaya koymaktadır. Yapılan analizler sonucunda öne çıkan stratejik bulgular şunlardır:

* **Küresel Satış Lideri:** `Country` (Ülke) bazında yapılan analizlerde, en yüksek brüt ciro (`Gross Sales`) ve net satış hacmine ulaşan lider ülkeler ve pazar payları harita ve çubuk grafiklerle dinamik olarak listelenmiştir.
* **Ürün Kârlılık Odakları:** Hangi ürünün (`Product`) ciro odaklı, hangi ürünün ise marj odaklı çalıştığı `Profit` (Kâr) ve `COGS` (Satılan Malın Maliyeti) dengesiyle ortaya konmuştur.
* **İndirim Stratejisi Değerlendirmesi:** `Discount Band` (İndirim Grupları) ile `Discounts` (İndirim Tutarları) arasındaki matematiksel korelasyon incelenmiştir. Yapılan yüksek indirimlerin net kâr marjlarını nasıl etkilediği segment bazlı raporlanmıştır.

---

## 🛠️ Uygulanan Veri Hazırlama (ETL) Adımları

Veri seti ham haldeyken karşılaşılan problemler ve Power Query üzerinde uygulanan profesyonel çözümler aşağıda listelenmiştir:

1.  **Sınırlayıcı Saptama (Delimiter):** Verinin orijinal yapısında ayırıcı karakter olarak **Noktalı Virgül (`;`)** kullanıldığı tespit edilmiş ve tablo yapısı buna göre sütunlara ayrıştırılmıştır.
2.  **Karakter ve Encoding Temizliği:** Metin ve tarih alanlarında meydana gelen Türkçe karakter bozulmaları (Örn: `1.Aðu.14` -> `1.Ağu.14`, `1.Pub.14` -> `1.Şub.14`) manuel değer değiştirme (`Replace Values`) metotlarıyla düzeltilmiştir.
3.  **Yerel Ayar ile Tarih Dönüşümü (Locale):** Bozuk tarih metinleri, sistemin doğru algılayabilmesi için **Yerel Ayar Kullanarak (Using Locale -> Türkçe/Türkiye)** veri türü dönüşümene tabi tutulmuş ve standart `Date` formatına getirilmiştir.
4.  **Veri Tipi Optimizasyonu:** Grafiklerin doğru katlama ve toplama işlemlerini yapabilmesi için finansal sütunlar (`Gross Sales`, `Discounts`, `Profit` vb.) **Ondalık Sayı (Decimal Number)**; kategorik alanlar ise **Metin (Text)** olarak set edilmiştir.
5.  **Özetleme Optimizasyonu (Don't Summarize):** `Year` ve `Month Number` gibi sayısal zaman alanlarının grafiklerde yanlışlıkla toplanmasını önlemek amacıyla Power BI üzerinde varsayılan özetleme özellikleri kapatılmıştır.

