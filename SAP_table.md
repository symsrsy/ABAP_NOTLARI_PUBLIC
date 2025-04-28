

# MM (Malzeme Yönetimi) Modülü

- MARA → Malzeme Ana Verisi (Malzeme için genel bilgiler: tür, sektör, birimler)
  
	 - MATNR → Malzeme numarası
	   
	 - MTART → Malzeme tipi
	   
	 - MATKL → Malzeme grubu
	   
	 - MEINS → Temel ölçü birimi
	   
	 - SPART → Ürün bölümü
   
- MARC → Malzeme Tesise Özel Verisi (MRP ve stok kontrol verileri)
  
	 - MATNR → Malzeme numarası
	   
	 - WERKS → Tesis kodu
	   
	 - DISPO → Malzeme planlayıcısı
	   
	 - DISMM → MRP tipi
   
- MBEW → Malzeme Muhasebe Değerleri (Değerleme, maliyet bilgileri)
  
	 - MATNR → Malzeme numarası
	   
	 - BWKEY → Değerleme alanı (tesis/şirket)
	   
	 - BWTAR → Değerleme türü
	   
	 - STPRS → Standart fiyat
	   
	 - VPRSV → Fiyat kontrol tipi
   
- MKPF → Malzeme Belgesi Başlık Verisi (Mal hareketi başlığı)
  
	 - MANDT → Sistem numarası (Client)
	   
	 - MBLNR → Belge numarası
	   
	 - MJAHR → Belge yılı
	
	 - BUDAT → Muhasebe tarihi
   
- MSEG → Malzeme Belgesi Satır Verisi (Mal hareketi satır detayları)
  
	 - MBLNR → Belge numarası
	   
	 - ZEILE → Satır numarası
	   
	 - MATNR → Malzeme numarası
	   
	 - WERKS → Tesis
	   
	 - LGORT → Stok yeri
   
- EKKO → Satınalma Belgesi Üst Verisi (Satınalma siparişi başlık bilgileri)
  
	 - EBELN → Satınalma sipariş numarası
	   
	 - BUKRS → Şirket kodu
	   
	 - LIFNR → Tedarikçi numarası
	   
	 - BEDAT → Belge tarihi
   
- EKPO → Satınalma Belgesi Satır Verisi (Satınalma siparişi satır bilgileri)
  
	 - EBELN → Satınalma sipariş numarası
	   
	 - EBELP → Satır numarası
	   
	 - MATNR → Malzeme numarası
	   
	 - MENGE → Sipariş edilen miktar
	   
	 - NETPR → Net fiyat

   
# SD(Satış Dağıtım) Modülü

- VBAK → Satış Belgesi Üst Verisi (Satış siparişi başlık bilgileri)

  - VBELN → Satış belgesi numarası

  - AUART → Satış belgesi türü (örneğin OR - Standart Sipariş)

  - VKORG → Satış organizasyonu

  - VTWEG → Dağıtım kanalı

  - SPART → Ürün bölümü

  - KUNNR → Müşteri numarası (alıcı)

- VBAP → Satış Belgesi Satır Verisi (Satış siparişi satır bilgileri)

  - VBELN → Satış belgesi numarası

  - POSNR → Satır numarası

  - MATNR → Malzeme numarası

  - KWMENG → Sipariş edilen miktar

  - VRKME → Satış birimi

- VBEP → Teslimat Planı Satır Verisi (Satış siparişlerinin teslimat planları)

  - VBELN → Satış belgesi numarası

  - POSNR → Satır numarası

  - ETENR → Teslimat planı numarası

  - EDATU → Teslimat tarihi

  - WMENG → Teslimat miktarı

- LIKP → Teslimat Belgesi Üst Verisi (Teslimat sürecinin başlık bilgileri)

  - VBELN → Teslimat belgesi numarası

  - ERDAT → Oluşturulma tarihi

  - LFDAT → Planlanan teslimat tarihi

  - KUNNR → Müşteri numarası (teslimat yapılan)

- LIPS → Teslimat Belgesi Satır Verisi (Teslimat sürecinin satır bilgileri)

  - VBELN → Teslimat belgesi numarası

  - POSNR → Satır numarası

  - MATNR → Malzeme numarası

  - LFIMG → Teslimat miktarı

  - VRKME → Satış birimi

- VBRK → Fatura Üst Verisi (Müşteri faturalarının başlık bilgileri)

  - VBELN → Fatura numarası

  - FKART → Fatura türü (örneğin F2 - Standart fatura)

  - FKDAT → Fatura tarihi

  - KUNAG → Fatura edilen müşteri

- VBRP → Fatura Satır Verisi (Müşteri faturalarının satır detayları)

  - VBELN → Fatura numarası

  - POSNR → Satır numarası

  - MATNR → Malzeme numarası

  - FKIMG → Fatura edilen miktar

  - VRKME → Satış birimi

- VBFA → Belge Akışı (Satış belgeleri arasındaki ilişki)

  - VBELV → Önceki belge numarası

  - POSNV → Önceki belgenin satır numarası

  - VBELN → Sonraki belge numarası

  - POSNN → Sonraki belgenin satır numarası

  - VBTYP → Belge türü (örneğin satış siparişi, teslimat, fatura)

- KNVV → Müşteri Satış Verileri (Müşteri ile satış organizasyonu ilişkisi)

  - KUNNR → Müşteri numarası

  - VKORG → Satış organizasyonu

  - VTWEG → Dağıtım kanalı

  - SPART → Ürün bölümü

  - KALKS → Fiyatlandırma prosedürü

- KNA1 → Müşteri Genel Verisi (Müşteri ana verileri - temel bilgiler)

  - KUNNR → Müşteri numarası

  - NAME1 → Müşteri adı

  - LAND1 → Ülke kodu

  - ORT01 → Şehir

  - REGIO → Bölge/Kıta kodu
 
  # FI(Finansal Muahsebe) Modülü

- BKPF → Muhasebe Belgesi Üst Verisi (Muhasebe kayıtlarının başlık bilgileri)
  
	 - BUKRS → Şirket kodu
	   
	 - BELNR → Belge numarası
	   
	 - GJAHR → Belge yılı
	   
	 - BLART → Belge türü (örneğin SA - Muhasebe Belgesi)
	   
	 - BLDAT → Belge tarihi
	   
	 - BUDAT → Muhasebe tarihi
	   
	 - TCODE → Belgeyi oluşturan işlem kodu
	   
- BSEG → Muhasebe Belgesi Satır Verisi (Muhasebe kayıtlarının satır detayları)
  
	 - BUKRS → Şirket kodu
	   
	 - BELNR → Belge numarası
	   
	 - GJAHR → Belge yılı
	   
	 - BUZEI → Satır numarası
	   
	 - HKONT → Ana hesap numarası (GL Account)
	   
	 - WRBTR → Belge tutarı
	   
	 - DMBTR → Yerel para birimi tutarı
	   
	 - SHKZG → Borç/Alacak göstergesi
	   
- BSID → Müşteri Açık Alacaklar (Açık müşteri faturaları)
  
	 - BUKRS → Şirket kodu
	   
	 - KUNNR → Müşteri numarası
	   
	 - BELNR → Belge numarası
	   
	 - GJAHR → Belge yılı
	   
	 - WRBTR → Belge tutarı
   
- BSAD → Müşteri Kapanmış Alacaklar (Ödenmiş müşteri faturaları)
  
	 - BUKRS → Şirket kodu
	   
	 - KUNNR → Müşteri numarası
	   
	 - BELNR → Belge numarası
	   
	 - GJAHR → Belge yılı
	   
	 - WRBTR → Belge tutarı
   
- BSIK → Tedarikçi Açık Borçlar (Açık tedarikçi faturaları)
  
	 - BUKRS → Şirket kodu
	   
	 - LIFNR → Tedarikçi numarası
	   
	 - BELNR → Belge numarası
	   
	 - GJAHR → Belge yılı
	   
	 - WRBTR → Belge tutarı
   
- BSAK → Tedarikçi Kapanmış Borçlar (Ödenmiş tedarikçi faturaları)
  
	 - BUKRS → Şirket kodu
	   
	 - LIFNR → Tedarikçi numarası
	   
	 - BELNR → Belge numarası
	   
	 - GJAHR → Belge yılı
	   
	 - WRBTR → Belge tutarı
	   
- BSIS → Ana Hesap Açık Kalemler (GL hesaplarındaki açık kalemler)
  
	 - BUKRS → Şirket kodu
	   
	 - HKONT → Ana hesap numarası
	   
	 - BELNR → Belge numarası
	   
	 - GJAHR → Belge yılı
	   
	 - WRBTR → Belge tutarı
   
- BSAS → Ana Hesap Kapanmış Kalemler (GL hesaplarındaki kapalı kalemler)
  
	 - BUKRS → Şirket kodu
	   
	 - HKONT → Ana hesap numarası
	   
	 - BELNR → Belge numarası
	   
	 - GJAHR → Belge yılı
	   
	 - WRBTR → Belge tutarı
   
- LFA1 → Tedarikçi Ana Verisi (Tedarikçi temel bilgileri)
  
	 - LIFNR → Tedarikçi numarası
	   
	 - NAME1 → Tedarikçi adı
	   
	 - LAND1 → Ülke kodu
	   
	 - ORT01 → Şehir
	   
	 - REGIO → Bölge
   
- KNA1 → Müşteri Ana Verisi (Müşteri temel bilgileri)
  
	 - KUNNR → Müşteri numarası
	   
	 - NAME1 → Müşteri adı
	   
	 - LAND1 → Ülke kodu
	   
	 - ORT01 → Şehir
	   
	 - REGIO → Bölge


# CO (Maliyet Muhasebesi)

- COBK → CO Belgesi Üst Verisi (Maliyet muhasebesi belgelerinin başlık bilgileri)
  
	 - OBJNR → Nesne numarası
	   
	 - BELNR → Belge numarası
	   
	 - GJAHR → Belge yılı
	
	 - BUDAT → Muhasebe tarihi
	   
	 - TCODE → Belgeyi oluşturan işlem kodu
   
- COEP → CO Belgesi Satır Verisi (Maliyet muhasebesi kayıtlarının satır detayları)
  
	 - OBJNR → Nesne numarası
	   
	 - BELNR → Belge numarası
	   
	 - GJAHR → Belge yılı
	   
	 - KSTAR → Birincil/ikincil maliyet unsuru (Cost Element)
	   
	 - WERT → Tutar
	   
	 - PERBL → Muhasebe periyodu
   
- CSKS → Masraf Yeri Ana Verisi (Cost Center bilgileri)
  
	 - KOSTL → Masraf yeri kodu
	   
	 - KOKRS → Kontrol alanı (Controlling Area)
	   
	 - BUKRS → Şirket kodu
	   
	 - VERAK → Sorumlu kişi
   
- CSKT → Masraf Yeri Açıklamaları (Cost Center isimlendirmeleri)
  
	 - KOSTL → Masraf yeri kodu
	   
	 - KOKRS → Kontrol alanı
	   
	 - SPRAS → Dil kodu
	   
	 - LTEXT → Masraf yeri adı (uzun açıklama)
   
- COKP → CO Planlama Belgesi Üst Verisi (Planlama başlık bilgileri)
  
	 - OBJNR → Nesne numarası
	   
	 - BELNR → Belge numarası
	   
	 - GJAHR → Planlama yılı
	   
	 - VRGNG → İşlem türü (Planlama işlemi)
   
- COVP → CO Belgesi ve Planlama Satır Verisi (Hem fiili hem plan verileri)
  
	 - OBJNR → Nesne numarası
	   
	 - BELNR → Belge numarası
	   
	 - GJAHR → Yıl
	   
	 - KSTAR → Maliyet unsuru
	   
	 - WERT → Değer (Tutar)
	   
	 - PERBL → Periyot
   
- COAS → İç Sipariş Ana Verisi (Internal Order master data)
  
	 - AUFNR → İç sipariş numarası
	   
	 - KOKRS → Kontrol alanı
	   
	 - AUART → İç sipariş türü
	   
	 - KOSTV → Sorumlu masraf yeri
	   
- AUFK → Sipariş Ana Verisi (Üretim/Proje/İç siparişler için ortak tablo)
  
	 - AUFNR → Sipariş numarası
	   
	 - OBJNR → Nesne numarası
	   
	 - AUART → Sipariş türü
	   
	 - KOKRS → Kontrol alanı
	   
	 - ERDAT → Oluşturulma tarihi

# PP (Üretim Planlama)

- AUFK → Sipariş Ana Verisi (Üretim, bakım ve proje siparişlerinin başlık bilgisi)
  
	 - AUFNR → Sipariş numarası
	   
	 - AUART → Sipariş türü (örneğin üretim siparişi)
	   
	 - OBJNR → Nesne numarası
	   
	 - KOKRS → Kontrol alanı
	   
	 - ERDAT → Oluşturulma tarihi
   
- AFKO → Üretim Siparişi Üst Verisi (Üretim süreci ile ilgili üst bilgiler)
  
	 - AUFNR → Sipariş numarası
	   
	 - MATNR → Malzeme numarası
	   
	 - GSTRP → Planlanan başlama tarihi
	   
	 - GLTRP → Planlanan bitiş tarihi
	   
	 - PSMNG → Planlanan miktar
   
- AFVC → Operasyon Verisi (Üretim operasyonları satır bilgileri)
  
	 - AUFPL → Operasyon sırası numarası
	   
	 - VORNR → Operasyon numarası
	   
	 - LTXA1 → Operasyon açıklaması
	   
	 - ARBID → Çalışma merkezi ID'si
   
- AFFL → Operasyon Atama Verisi (Operasyonların iş yerlerine atamaları)
  
	 - AUFPL → Operasyon sırası numarası
	   
	 - VORNR → Operasyon numarası
	   
	 - ARBID → İş yeri ataması
   
- AFVV → Operasyon Zaman ve Miktar Verileri (Zaman ve miktar değerleri)
  
	 - AUFPL → Operasyon sırası numarası
	   
	 - VORNR → Operasyon numarası
	   
	 - VGE01 → Tahmini iş süresi
	   
	 - VGW01 → İşçilik saati
   
- CRHD → Çalışma Merkezi Ana Verisi (Work Center bilgileri)
  
	 - OBJID → Çalışma merkezi objesi
	   
	 - ARBPL → Çalışma merkezi adı
	   
	 - WERKS → Tesis kodu
	   
	 - VERWE → İş türü
	   
- MAPL → İş Planı ve Çalışma Merkezi İlişkisi (Routing ve iş merkezi ilişkileri)
  
	 - PLNNR → Plan numarası
	   
	 - PLNAL → Plan alternatifi
	
	 - ARBID → İş yeri kimliği
   
- CAUFV → Üretim Siparişi Görünümü (Üretim siparişlerini hızlı listelemek için)
  
	 - AUFNR → Sipariş numarası
	   
	 - OBJNR → Nesne numarası
	   
	 - MATNR → Malzeme numarası
	   
	 - GSTRP → Planlanan başlama tarihi
   
- MAST → Malzeme ve Ürün Ağacı İlişkisi (BOM - Bill of Materials)
  
	 - MATNR → Malzeme numarası (ana ürün)
	   
	 - STLAN → Ürün ağacı tipi
	   
	 - STLNR → Ürün ağacı numarası
   
- STPO → Ürün Ağacı Satırları (BOM'daki her bir bileşenin detayları)
  
	 - STLNR → Ürün ağacı numarası
	   
	 - STLKN → Ürün ağacı satır numarası
	   
	 - IDNRK → Bileşen malzeme numarası
	   
	 - MENGE → Miktar
   
- PLKO → İş Planı Üst Verisi (Routing üst bilgileri)
  
	 - PLNNR → Plan numarası
	   
	 - PLNTY → Plan türü (Routing, Ref. Operation Set)
	   
- PLPO → İş Planı Operasyon Verisi (Routing operasyonları)
  
	 - PLNNR → Plan numarası
	   
	 - PLNKN → Plan satır numarası
	   
	 - VORNR → Operasyon numarası
	   
	 - ARBID → Çalışma merkezi kimliği

   # WM (Warehouse Management- Depo Yönetimi)

- LTAK → Transfer Siparişi Üst Verisi (Depo hareketleri için başlık bilgileri)
  
	 - TANUM → Transfer siparişi numarası
	   
	 - BLDAT → Belge tarihi
	   
	 - WERKS → Tesis
	   
	 - LGNUM → Depo numarası
   
- LTAP → Transfer Siparişi Satır Verisi (Depo hareketleri için satır bilgileri)
  
	 - TANUM → Transfer siparişi numarası
	   
	 - TAPOS → Satır numarası
	   
	 - MATNR → Malzeme numarası
	   
	 - LGPLA → Kaynak depo yeri
	   
	 - LGTYP → Kaynak depo tipi
	   
	 - NLPLA → Hedef depo yeri
	   
	 - NLTYP → Hedef depo tipi
	   
- LQUA → Depo Yeri Bazlı Stoklar (Depodaki mevcut stok bilgileri)
  
	 - LGNUM → Depo numarası
	   
	 - LGTYP → Depo tipi
	   
	 - LGPLA → Depo yeri
	   
	 - MATNR → Malzeme numarası
	   
	 - VERME → Mevcut miktar
   
- MKPF → Malzeme Belgesi Üst Verisi (Stok hareketlerinin başlık bilgileri - MM ile ortak)
  
	 - MBLNR → Belge numarası
	   
	 - MJAHR → Belge yılı
	   
	 - BUDAT → Muhasebe tarihi
	   
- MSEG → Malzeme Belgesi Satır Verisi (Stok hareketlerinin satır bilgileri - MM ile ortak)
  
	 - MBLNR → Belge numarası
	   
	 - ZEILE → Satır numarası
	   
	 - MATNR → Malzeme numarası
	   
	 - WERKS → Tesis
	   
	 - LGORT → Stok yeri
	   
- LAGP → Depo Yeri Ana Verisi (Depo yerlerinin detaylı tanımları)
  
	 - LGNUM → Depo numarası
	   
	 - LGTYP → Depo tipi
	   
	 - LGPLA → Depo yeri
	   
	 - LZONE → Depo alanı
   
- T331 → Transfer Siparişi Tipi Tanımları (Transfer siparişi türlerinin yönetimi)
  
	 - BWLVS → Transfer siparişi hareket türü
	   
	 - BWART → Malzeme hareket türü
	   
	 - SOBKZ → Özel stok göstergesi

   # HR(İnsan Kaynakları)

- PA0000 → Organizasyonel Bilgiler (Personelin organizasyon değişiklikleri, durum bilgileri)

  - PERNR → Personel numarası

  - BEGDA → Başlangıç tarihi

  - ENDDA → Bitiş tarihi

  - MASSN → İşlem türü (örneğin işe alım, işten çıkarma)

  - MASSG → İşlem nedeni

- PA0001 → Organizasyon Atamaları (Personelin şirket içi atama bilgileri)

  - PERNR → Personel numarası

  - WERKS → Tesis (iş yeri)

  - BTRTL → Alt iş yeri

  - PLANS → Pozisyon kodu

  - KOSTL → Masraf yeri

- PA0002 → Kişisel Bilgiler (Personelin kimlik bilgileri)

  - PERNR → Personel numarası

  - VORNA → Ön ad (isim)

  - NACHN → Soyad

  - GESCH → Cinsiyet

  - GBDAT → Doğum tarihi

- PA0006 → Adres Bilgileri (Personelin adres bilgileri)

  - PERNR → Personel numarası

  - STRAS → Sokak

  - ORT01 → Şehir

  - PSTLZ → Posta kodu

  - LAND1 → Ülke

- PA0016 → İş Sözleşmesi Bilgileri (Çalışma şekli, çalışma süresi gibi bilgiler)

  - PERNR → Personel numarası

  - BEGDA → Başlangıç tarihi

  - ENDDA → Bitiş tarihi

  - ARBGB → İş sözleşmesi grubu

  - ABKRS → Bordro alanı

- PA0032 → İç İzinler Bilgisi (İzinler, askerlik durumu, diğer izin hakları)

  - PERNR → Personel numarası

  - SUBTY → Alt tür (örneğin askerlik, doğum izni)

  - BEGDA → Başlangıç tarihi

  - ENDDA → Bitiş tarihi

- PA0105 → İletişim Bilgileri (E-posta, telefon, kullanıcı adı vb.)

  - PERNR → Personel numarası

  - SUBTY → Alt tür (örneğin e-posta için '0010')

  - USRID → Kullanıcı ID'si (örneğin sistemdeki kullanıcı adı)

  - USRID_LONG → Kullanıcının tam e-posta adresi

- HRP1000 → Organizasyon Birimi Ana Verisi (Organizasyonel yapı elemanları)

  - OBJID → Nesne numarası

  - OTYPE → Nesne türü (örneğin 'O' Organizasyon birimi, 'S' Pozisyon)

  - STEXT → Kısa açıklama (birimin adı)

  - PLVAR → Planlama varyantı

- HRP1001 → Organizasyonel İlişkiler (Pozisyonlar ve organizasyon birimleri arasındaki ilişkiler)

  - OBJID → Ana nesne numarası

  - RSIGN → İlişki yönü (A→ veya B←)

  - RELAT → İlişki türü (örneğin bir pozisyonun bir organizasyona ait olması)

  - SOBID → İlgili nesne numarası
 
# PM (Bakım Yönetimi)
  
- IFLOT → Fonksiyonel Lokasyon Ana Verisi (Sabit varlıkların konumsal organizasyonu)
  
	 - TPLNR → Fonksiyonel lokasyon numarası
	   
	 - PLTXT → Fonksiyonel lokasyon açıklaması
	   
	 - WERK → Tesis kodu
   
- ILOA → Fonksiyonel Lokasyon Muhasebe Atamaları (Fonksiyonel lokasyonlara muhasebe bağlantıları)
  
	 - TPLNR → Fonksiyonel lokasyon numarası
	   
	 - BUKRS → Şirket kodu
	   
	 - KOSTL → Masraf yeri
	   
	 - ANLNR → Sabit kıymet numarası
   
- EQUI → Ekipman Ana Verisi (Bakımı yapılacak taşınabilir varlıkların bilgileri)
  
	 - EQUNR → Ekipman numarası
	   
	 - EQART → Ekipman türü
	   
	 - TPLNR → Fonksiyonel lokasyon numarası
	   
	 - SERNR → Seri numarası
   
- EQUZ → Ekipman Kullanım Geçmişi (Ekipmanın fonksiyonel lokasyonlardaki geçmişi)
  
	 - EQUNR → Ekipman numarası
	   
	 - TPLNR → Fonksiyonel lokasyon numarası
	   
	 - DATBI → Bitiş tarihi
	   
	 - DATAB → Başlangıç tarihi
   
- IFLOTX → Fonksiyonel Lokasyon Açıklamaları (Çok dilli fonksiyonel lokasyon açıklamaları)
  
	 - TPLNR → Fonksiyonel lokasyon numarası
	   
	 - SPRAS → Dil anahtarı
	   
	 - PLTXT → Açıklama
   
- QMEL → Arıza Kayıtları (Arıza, hata veya iş emri talepleri)
  
	 - QMNUM → Arıza numarası
	   
	 - QMTXT → Arıza açıklaması
	   
	 - AUFNR → İlgili iş emri numarası
	   
	 - QMDAT → Arıza oluşturulma tarihi
	   
- AUFK → İş Emri Ana Verisi (Bakım iş emirleri başlık bilgileri - CO/PM ortak tablo)
  
	 - AUFNR → İş emri numarası
	   
	 - AUART → İş emri türü
	   
	 - OBJNR → Nesne numarası
	   
	 - ERDAT → Oluşturulma tarihi
   
- AFVC → Operasyonlar (İş emrindeki operasyon adımları - PP/PM ortak tablo)
  
	 - AUFPL → Operasyon sırası numarası
	   
	 - VORNR → Operasyon numarası
	   
	 - LTXA1 → Operasyon açıklaması
	   
	 - ARBID → Çalışma merkezi ID'si
   
- CRHD → Çalışma Merkezi Ana Verisi (İş merkezleri - PP/PM ortak tablo)
  
	 - OBJID → Çalışma merkezi objesi
	   
	 - ARBPL → Çalışma merkezi adı
	   
	 - WERKS → Tesis kodu

# QM (Kalite Yönetimi)

- QALS → Kalite Denetim Partisi Üst Verisi (Inspection lot başlık bilgileri)
  
	 - PRUEFLOS → Denetim partisi numarası
	   
	 - MATNR → Malzeme numarası
	   
	 - WERKS → Tesis kodu
	   
	 - AUFNR → Üretim siparişi numarası (varsa)
   
- QASE → Kalite Denetim Partisi Sonuçları (Inspection lot sonuç bilgileri)
  
	 - PRUEFLOS → Denetim partisi numarası
	   
	 - VORGLFNR → İş adımı numarası
	   
	 - MERKNR → Karakteristik numarası
	   
	 - SOLLMWERT → Hedef değer
	   
	 - ISTMWERT → Ölçülen değer
   
- QAMR → Kalite Planı Ana Verisi (Inspection characteristic master data)
  
	 - PLNNR → Plan numarası
	   
	 - PLNAL → Plan alternatifi
	   
	 - MERKNR → Karakteristik numarası
	   
	 - VORNR → Operasyon numarası
   
- QAVE → Denetim Belgesi (Inspection lot belgesi bilgileri)
  
	 - PRUEFLOS → Denetim partisi numarası
	   
	 - VORNR → Operasyon numarası
	   
	 - MERKNR → Denetim karakteristiği numarası
	   
	 - CODE → Hata kodu (varsa)
   
- QMAT → Malzeme Kalite Yönetimi Verisi (Malzeme bazında kalite verileri)
  
	 - MATNR → Malzeme numarası
	   
	 - WERKS → Tesis kodu
	   
	 - QSSYS → Kalite yönetimi sistemi tipi
   
- QMFE → Arıza Bildirimi (Kalite sorunlarının hata kayıtları)
  
	 - QMNUM → Bildirim numarası
	   
	 - FEGRP → Hata grubu
	   
	 - FECOD → Hata kodu
	   
	 - MATNR → İlgili malzeme numarası
   
- QMEL → Arıza Kayıtları (Bakım ve kalite bildirimi ortak kullanımı - PM ile ortak tablo)
  
	 - QMNUM → Arıza numarası
	   
	 - QMTXT → Bildirim açıklaması
	   
	 - AUFNR → İlgili iş emri numarası
	   
	 - QMDAT → Bildirim oluşturulma tarihi
   

# PS(Project System - Proje Yönetimi)


- PROJ → Proje Tanımları (Projelerin genel başlık bilgileri)
  
	 - PSPID → Proje tanımlayıcısı (Proje ID'si)
	   
	 - OBJNR → Nesne numarası
	   
	 - VERNR → Versiyon numarası
	   
	 - STSMA → Durum profili
   
- PRPS → İş Paketi (WBS Element) Verileri (Projelerin detay iş paketleri)
  
	 - PSPNR → WBS eleman numarası
	   
	 - PSPID → WBS eleman kimliği (görsel ID)
	   
	 - POSID → WBS pozisyon numarası
	   
	 - PRTXT → WBS elemanı açıklaması
	   
	 - OBJNR → Nesne numarası
   
- AUFK → Sipariş Ana Verisi (Proje siparişleri dahil, CO/PM ile ortak tablo)
  
	 - AUFNR → Sipariş numarası
	   
	 - OBJNR → Nesne numarası
	   
	 - AUART → Sipariş türü
	   
	 - KOKRS → Kontrol alanı
	   
	 - ERDAT → Oluşturulma tarihi
   
- AFVC → Operasyonlar (Proje siparişi operasyonları - CO/PP/PM ile ortak tablo)
  
	 - AUFPL → Operasyon sırası numarası
	   
	 - VORNR → Operasyon numarası
	   
	 - LTXA1 → Operasyon açıklaması
	   
	 - ARBID → Çalışma merkezi ID'si
   
- CJVV → Proje Versiyon Verisi (Proje planlama versiyon bilgileri)
  
	 - PSPNR → WBS eleman numarası
	   
	 - VRGNG → İşlem türü
	   
	 - VERSN → Planlama versiyonu
   
- COSP → Planlanan Maliyet Verileri (WBS ve siparişler için plan maliyetler)
  
	 - OBJNR → Nesne numarası
	   
	 - GJAHR → Yıl
	   
	 - PERBL → Dönem
	   
	 - WTG001 → Planlanan tutar
	   
- COSS → Gerçek Maliyet Verileri (WBS ve siparişler için gerçekleşen maliyetler)
  
	 - OBJNR → Nesne numarası
	   
	 - GJAHR → Yıl
	   
	 - PERBL → Dönem
	   
	 - WTG001 → Gerçekleşen tutar
	   

# Önemli Tablolar

MM (Malzeme Yönetimi)

	•	MARA → Malzeme Ana Verisi

	•	MARC → Malzeme Tesise Özel Verisi

	•	MBEW → Malzeme Muhasebe Değerleri

	•	MKPF → Malzeme Belgesi Başlık

	•	MSEG → Malzeme Belgesi Satır

	•	EKKO → Satınalma Belgesi Başlık

	•	EKPO → Satınalma Belgesi Satır
SD (Satış ve Dağıtım)

	•	VBAK → Satış Belgesi Başlık

	•	VBAP → Satış Belgesi Satır

	•	LIKP → Teslimat Belgesi Başlık

	•	LIPS → Teslimat Belgesi Satır

	•	VBRK → Fatura Başlık

	•	VBRP → Fatura Satır
FI (Finansal Muhasebe)

	•	BKPF → Muhasebe Belgesi Başlık

	•	BSEG → Muhasebe Belgesi Satır

	•	BSID → Açık Müşteri Alacakları

	•	BSIK → Açık Tedarikçi Borçları
CO (Maliyet Muhasebesi)

	•	COBK → CO Belgesi Başlık

	•	COEP → CO Belgesi Satır

	•	CSKS → Masraf Yeri Ana Verisi

	•	COAS → İç Sipariş Ana Verisi
PP (Üretim Planlama)

	•	AUFK → Üretim Siparişi Başlık

	•	AFKO → Üretim Siparişi Üst Verisi

	•	AFVC → Üretim Operasyon Verisi

	•	MAST → Ürün Ağacı Başlık

	•	STPO → Ürün Ağacı Satır
WM (Depo Yönetimi)

	•	LTAK → Transfer Siparişi Başlık

	•	LTAP → Transfer Siparişi Satır

	•	LQUA → Depo Stokları
HR (İnsan Kaynakları)

	•	PA0000 → Organizasyonel Bilgiler

	•	PA0001 → Organizasyon Atamaları

	•	PA0002 → Kişisel Bilgiler

	•	HRP1000 → Organizasyon Birimi Ana Verisi

	•	HRP1001 → Organizasyonel İlişkiler
PM (Bakım Yönetimi)

	•	IFLOT → Fonksiyonel Lokasyon

	•	EQUI → Ekipman Ana Verisi

	•	QMEL → Arıza Bildirimi

	•	AUFK → İş Emri Başlık
QM (Kalite Yönetimi)

	•	QALS → Kalite Denetim Partisi Başlık

	•	QASE → Kalite Denetim Sonuçları

	•	QMEL → Arıza Bildirimi
PS (Proje Sistemi)

	•	PROJ → Proje Ana Verisi

	•	PRPS → İş Paketi (WBS Elemanı)

	•	COSP → Planlanan Maliyet Verileri

	•	COSS → Gerçekleşen Maliyet Verileri 

 


  
   
