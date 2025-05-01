# SAP ABAP – REUSE ALV vs SALV Karşılaştırması

Bu doküman, SAP ABAP'ta iki farklı ALV gösterim yöntemi olan **REUSE ALV** ve **SALV (Simple ALV)** yapılarının farklarını ve kullanım alanlarını karşılaştırmalı olarak açıklar.

---

## 1. Karşılaştırma Tablosu

| Özellik                          | REUSE ALV                                | SALV (Simple ALV)                        |
|----------------------------------|-------------------------------------------|------------------------------------------|
| Tam Adı                          | `REUSE_ALV_GRID_DISPLAY`                  | `CL_SALV_TABLE` sınıfı                    |
| Kullanım Yılı                    | Daha eski (4.6x ve öncesi)                | Daha yeni (ECC 6.0 ve sonrası)           |
| Programlama Tarzı               | Prosedürel                                | Nesne yönelimli (Object-Oriented)        |
| Fieldcatalog Gerekliliği        | Evet, elle tanımlanır                     | Hayır, otomatik tanır                    |
| Kullanım Kolaylığı              | Daha fazla kod gerektirir                 | Daha kısa, okunabilir kod                |
| Özelleştirme (renk, ikon vs.)   | Çok esnek                                 | Kısıtlı                                  |
| Event (çift tıklama, buton)     | Evet                                      | Yok (standart SALV'da)                   |
| Genişletilebilirlik             | Yüksek                                    | Düşük (ancak miras alınarak genişletilir)|
| Günümüzde Kullanım Durumu       | Hâlâ aktif projelerde kullanılır          | Yeni projelerde daha çok tercih edilir   |

---

## 2. Ne Zaman Hangisi Tercih Edilmeli?

### REUSE ALV:
- Satır/sütun bazlı stil özelleştirme gerekiyorsa
- Kullanıcı etkileşimleri (çift tıklama, buton vb.) gerekiyorsa
- Eski sistem veya raporlar üzerinde çalışıyorsan

### SALV (Simple ALV):
- Sadece listeleme yapacaksan (kullanıcı etkileşimi gerekmeden)
- Daha kısa ve modern kod yapısı istiyorsan
- Eğitim, prototipleme veya standart gösterim yapıyorsan

---

## 3. Kod Örneği – REUSE ALV

```abap
DATA: gt_data TYPE TABLE OF sflight,
      gt_fcat TYPE slis_t_fieldcat_alv,
      gs_fcat TYPE slis_fieldcat_alv.

SELECT * INTO TABLE gt_data FROM sflight UP TO 50 ROWS.

gs_fcat-fieldname = 'CARRID'.
gs_fcat-coltext = 'Havayolu'.
APPEND gs_fcat TO gt_fcat.

CALL FUNCTION 'REUSE_ALV_GRID_DISPLAY'
  EXPORTING
    it_fieldcat = gt_fcat
  TABLES
    t_outtab = gt_data.
```

---

## 4. Kod Örneği – SALV

```abap
DATA: gt_data TYPE STANDARD TABLE OF sflight,
      gr_table TYPE REF TO cl_salv_table.

SELECT * INTO TABLE gt_data FROM sflight UP TO 50 ROWS.

cl_salv_table=>factory(
  IMPORTING r_salv_table = gr_table
  CHANGING  t_table      = gt_data ).

gr_table->display( ).
```

---

## 5. Sonuç

- **SALV**, daha modern ve hızlı uygulamalar için uygundur. Özellikle sadece görüntüleme amaçlı raporlar için idealdir.
- **REUSE ALV**, gelişmiş kontrol, event yönetimi ve stil özelleştirme gereken durumlarda hâlâ güçlü bir araçtır.

Yeni geliştirmelerde **SALV**, bakım veya geniş raporlarda ise **REUSE ALV** tercih edilir.
