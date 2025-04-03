


Bir Rapor Üzerinden Hem SQL’de hem SAP ABAP’ta ALV raporuyla çekelim. 

**Veri Modelimiz(Tablo Adı: satislar)**
 | satis_id | urun_adi | tutar | Tarih | Bolge |
| ------ | ------ | ------ | ------ | ------ |
| 1001 | Kalem | 50 | 2022-03-12 | Marmara |
| 1002 | Defter | 80 | 2022-04-05 | Ege |
| 1003 | Silgi | 20 | 2023-01-15 | Marmara |
| 1004 | Kalem | 60 | 2023-02-20 | Akdeniz |



**SQL ile Raporlama** 

```sql
SELECT 
      YEAR(tarih) AS yil,
      Bolge,
     SUM(tutar) AS toplam_satis
FROM
     Satislar
GROUP BY 
     YEAR(tarih), bolge
ORDER BY
    Yil, bolge;

```

Yıl ve bölgeye göre gruplayıp toplam satışları topla 

**ABAP ALV Raporu İle Aynı Raporu Yapmak** 

**Önce yapımızı kuruyoruz** 
```abap

TYPES: BEGIN OF ty_satis, 

tarih TYPE d, 

bolge TYPE string, 

tutar TYPE p DECIMALS 2, 

END OF ty_satis. 

TYPES: BEGIN OF ty_rapor, 
yil TYPE i, 
bolge TYPE string, 
toplam_satis TYPE p DECIMALS 2, 
END OF ty_rapor. 

DATA: lt_satis TYPE TABLE OF ty_satis, 
lt_rapor TYPE TABLE OF ty_rapor, 
wa_satis TYPE ty_satis, 
wa_rapor TYPE ty_rapor.
```

Verilerimi örnekle dolduruyoruz 
```abap
wa_satis-tarih = ‘20220312’. 
wa_satis-tarih = ‘Marmara’. 
Wa_satis-tutar = 50. 
APPEND wa_satis TO lt_satis. 


wa_satis-tarih = ‘2022 0405 ’. 

wa_satis-tarih = ‘ Ege ’. 

Wa_satis-tutar = 2 0. 

APPEND wa_satis TO lt_satis. 

```
Yıl ve Bölgeye göre grupluyoruz 
```abap
DATA : lv_yil TYPE i, 

lv_key TYPE string, 

lv_temp TYPE HASHED TABLE OF ty_rapor WITH UNIQUE KEY yil bolge. 

LOOP AT lt_satis INTO wa_satis. 

lv_yil = wa_satis-tarih+0(4). 

READ TABLE lt_temp INTO wa_rapor WITH KEY yil = lv_yil bolge = wa_satis-bolge. 

IF sy-subrc = 0. 

wa_rapor-yil = lv_yil. 

wa_rapor-bolge = wa_satis-bolge. 

wa_rapor-toplam_satis = wa_satis-tutar. 

INSERT wa_rapor INTO TABLE lt_temp. 

ENDIF. 

ENDLOOP. 

Lt_rapor[] = lt_temp[]. 

```
ALV Gösterimi 
```abap
CALL FUNCTION ‘ REUSE_ALV_GRID_DISPLAY ’ 

EXPORTING 

i_structure_name = ‘TY_RAPOR’ 

TABLES 

t_outtab = lt_rapor. 

```

