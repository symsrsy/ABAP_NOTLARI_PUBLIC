# SAP ABAP – GSList (Kod İçi Yapı) vs. SE11 Structure Karşılaştırması

## 1. GSList Nedir?

GSList, genelde geliştiricilerin *program içinde TYPES veya DATA ile tanımladığı geçici yapılar*dır.

### Örnek:
abap
TYPES: BEGIN OF ty_person,
         name TYPE string,
         age  TYPE i,
       END OF ty_person.

DATA: gs_person TYPE ty_person.


### Özellikleri:
- Sadece o programda geçerlidir (lokaldir)
- Hafızada (RAM'de) tutulur, veritabanında kaydı yoktur
- Hızlı tanımlama için kullanılır
- Geliştirme sürecinde esneklik sağlar

## 2. SE11 Structure Nedir?

SE11 üzerinden tanımlanan yapılar, SAP sistemine *kalıcı olarak kayıt edilen global veri yapıları*dır.

### Özellikleri:
- SE11 ekranından oluşturulur
- Tüm programlar tarafından erişilebilir (global)
- Daha kontrollü ve standart yapılar sağlar
- Alan tipi, domain, arama yardımı (F4 help) bağlamaları yapılabilir
- Dokümantasyon, versiyonlama, transport desteği vardır

## 3. GSList vs. SE11 Structure – Karşılaştırma Tablosu

| Kriter                     | GSList (Kod İçi Yapı)                | SE11 Structure (Dictionary Yapısı)        |
|----------------------------|--------------------------------------|-------------------------------------------|
| Tanımlama Yeri             | Programın içinde (TYPES, DATA)   | SE11 (ABAP Dictionary)                  |
| Kapsam                    | Sadece tanımlandığı program           | Tüm sistemde kullanılabilir               |
| Performans                 | Daha hızlı (hafif işler için ideal)   | Biraz daha yüksektir ama güçlüdür         |
| Transport Sistemi          | Hayır                                 | Evet (versiyon kontrolü yapılabilir)      |
| Arama yardımı, domain      | Yok                                   | Vardır (F4 help, domain bağlama)          |
| Bakım Kolaylığı            | Koda gömülü                           | Ortak yapı, merkezi yönetim               |
| Yeniden Kullanılabilirlik | Kısıtlı                               | Yüksek                                    |

## 4. Hangi Durumda Hangisi Tercih Edilmeli?

### GSList (lokal yapı) kullan:
- Küçük bir deneme/POC yapıyorsan
- Yapıyı sadece 1 programda kullanacaksan
- Hızlıca prototip oluşturuyorsan
- Projenin geçici olduğunu biliyorsan

### SE11 Structure kullan:
- Yapıyı birden fazla programda kullanacaksan
- Ekran, ALV veya interface tarafında F4 yardım/alan kontrolü gerekiyorsa
- Ekip geliştirmesi yapıyorsan (başkaları da kullanacaksa)
- Sisteme entegre kalıcı bir yapı geliştiriyorsan
- Kodun uzun ömürlü ve versiyon kontrollü olması gerekiyorsa

## 5. Pratik Tavsiye

> Gerçek bir iş ortamında *structure’lar merkezi tanımlanır*. Kod içinde sadece DATA: gs_abc TYPE zstruktur. gibi tanımlar kullanılır. Çünkü:
> - Kod okunabilirliği artar
> - Hata riski düşer
> - Geliştiriciler arasında standart sağlanır

## 6. Ekstra: Kısa Yol Bilgileri

- SE11: Structure, Table veya Data Type tanımlamak/görüntülemek için
- Ctrl + F3: SE11’de structure içeriğini çalıştır
- F4: Field yardımını test etmek için
- SE80: Global yapıları entegre etmek için hızlı erişim

## Sonuç

Küçük çaplı, deneme amaçlı işlerde GSList kullanılabilir.  
Ancak *şirket ortamında, sürdürülebilir ve yeniden kullanılabilir projeler için SE11 structure kullanımı şarttır.*
