

**ETL (VERİ AMBARI SÜRECİ)**

 Extract-->çek 
 Transform-->(dönüştür) 
 Load -->(yükle) 

 Örneğin, 
 excelden çek 
 tarih formatlarını düzenle 
 HANA’ ya yükle 

| ÖZELLİK | OLTP | OLAP |
| ------ | ------ | ------ |
| AMAÇ | Günlük operasyonları yönetmek | Veri Analizi ve karar desteği sağlamak |
| YAPI | Satış, sipariş, müşteri girişi gibi işlemler | Raporlama, analiz, trend takibi |
| HEDEF KULLANICI | Operasyonel kullanıcılar(satışçı,depo,muhasebe) | Analist, yönetici, karar verici |
| SORGULAR | Kısa,hızlı,anlık | Yoğun, büyük veri, özet ve istatiksel sorgular |
| VERİTABANI TİPİ | Normalleştirilmiş toblolar (çok tablo,ilişkili) | Denormalize, daha az tablo ama geniş ve özet |
| ÖRNEK SORGU | Bu sipariş detaylarını getir | Son 3 yılda hangi bölgede satışlar arttı. |



**SQL ile OLTP ve OLAP**


###### OLTP’de 
```sql
SELECT *FROM sipariş WHERE sipariş_no =’S1234’ 
```
###### OLAP 
```sql
SELECT urun_kategori, SUM(tutar) AS toplam_satis 
FROM satis_ozet 
WHERE yil BETWEEN 2021 AND 2023 
GROUP BY urun_kategori; 
```
**OLTP ve OLAP SAP-HANA-ABAP Karşığı**

###### OLTP --> SAP ECC / S / 4HANA Üzerindeki Operasyonel Tablolar: 

###### Sipariş giriş ekranı 
###### FI muhasebe modülü 
###### MM malzeme hareketleri 
```abap
 SELECT * FROM vbak INTO TABLE lt_sipariş WHERE vbeln = ‘S1234’ 
```
 OLAP --> SAP BW ya da HANA üzerinde veri ambarı katmanı: 

###### CDS View ile model oluşturursun 
 Calculation View ile detaylı analiz yaparsın 
 AMDP ile büyük veri işler, ALV ile raporlarsın 

###### PEKİ NASIL İŞLER BU BİR ŞİRKETTE 

 Bir şirkette çalışıyorsunuz diyelim. 

 Sipariş kayıtlarını içeren bir tablo erişeceğiz(OLTP) 

 Ama yöneticin diyor ki: “Bana aylara göre toplam satışları getir.” 
 İşte bu OLAP’tır 

 Bu durumda izlenecek adım şudur: 

 CDS View yazarsın --> satış verilerini tarih bazlı gruplayarak çekersin. 
 Veya Calculation View ile bunu HANA Studio’da oluşturursun. 

 ABAP ile bu View’ı çağırıp ALV raporu tasarlarsın. 


