
# GİRİŞ KODLARI 

### SAP FI 

 XD01: yeni müşteri cari oluşturma kodu 
 VA01: müşteri siparişi oluşturma 
 FB01: FI muhasebe işlemleri 
 MB1C: MM malzeme hareketleri 

### ABAP 

 SE38: yeni program oluşturma kodu(ABAP) 
 SE11: yeni tablo oluşturma 
 SE16n: T-code 
 SE80: Fonksiyon Grubu Oluşturma 
 SE37: Sistemde tanımlı tüm fonksiyonları arayabilir ve inceleyebilir 
 SE24: Class Oluşturma 
 SE10: Request oluşturma
 SE91: Mesaj CLass'ı oluşturma


# KISA YOLLAR 
 F4 --> 3 noktaları açmak için 
 F3 --> Geri 
 F8-->Çalıştır 

 SHIFT + F1 --> KODU DÜZENLİ HALE GETİRME KISA YOLU 

 Alt + Tab --> Bilgisayarda açık olan uygulamalar arasında geçiş yapmayı sağlar. 
 Ctrl + Space --> oluşturulan objenin ulaşabileceği methodları çağırmak için 

# ABAP 

## DEĞİŞKEN TANIMLAMA 

 integer ifadeler başında boşluklarla default olarak tanımlanır. 
 Numerik ifadelerde ise rakamın uzunluğu kadar başına 0 koyar. 

```abap
DATA gv_degs1 TYPE p DECIMALS 2.
DATA gv_degs2 TYPE int4.
DATA gv_degs3 TYPE n.
DATA gv_degs4 TYPE c.
DATA gv_degs5 TYPE string.

gv_degs1 = ‘12.54’.

gv_degs2 = 123.
gv_degs3 =654.
gv_degs4 =’A’.
gv_degs4 = ‘C’.

gv_degs5 = ‘Merhaba bir cümle’.

DATA gv_degs2 TYPE n LENGTH 10.
DATA:      -->birden fazla data tanımlamayı sağlar.,
DATA: gv_degs1 TYPE i,
gv_degs2 TYPE n LENGTH 10.
```


## YORUM SATIRI 
```abap
 *Bu bir yorum satırıdır 
 *program akışını bozmaz 
```
###### !YORUM SATIRI Kısayolu CTRL+< 


## EKRANA YAZDIRMA 

```abap

gv_degs1 = 10.

WRITE gv_degs1.
```

## PROGRAMI AKTİF ETME 

 CTRL+F3 

## KAYDET 

 CTRL + S 

###### ALT SATIRA YAZIRMA 

```abap
WRITE / gv_degs1.
```


## TOPLAMA 

```abap
gv_sonuc = gv_degs1 + gv_degs2. 

WRITE gv_sonuc.

```

## ÇOKLU EKRANA YAZIRMA 

```abap
 WRITE: gv_metin, gv_sonuc. 
```
## DEĞİŞKEN TANIMLAMADAN EKRANA STRİNG YAZDIRMA 

```abap
WRITE: / ‘Farkı = ’, gv_sonuc. 
```
## KOŞUL 
```abap
IF koşul.

ENDIF.

IF gv_degs1 > gv_degs2.
   WRITE: ‘Birinci sayı büyüktür’.
ENDIF.

IF gv_degs1 = gv_degs2.
   WRITE: ‘Birinci sayı eşittir’.
ENDIF.
```

## İÇİÇE KOŞUL 
```abap

IF gv_degs1 > gv_degs2.

   ELSEIF gv_degs1 = gv_degs2.

   ELSE

ENDIF.
```

## CASE 
```abap
CASE gv_degs1.
   WHEN 1.
   WHEN 2.
   WHEN OTHERS.
ENDCASE.
````


## DÖNGÜ 
```abap

DO 10 TIMES.
    WRITE ‘döngü’
ENDDO.

WHILE gv_gegs1 <= 10.
    gv_degs1 = gv_degs1 + 1.
    WRITE / gv_degs, ‘döngü 2’.
ENDWHILE.
```
## TABLO OLUŞTURMA 

 Domain=”Bu alanın veri tipi ve uzunluğu ne” 
 Data Element =”Bu alan sistemde ne anlama geliyor” 

 SQL mantığındaki her bir sütunun her bir tablosu için 
 Önce domain oluştur 
 sonra data element oluştur 

 SQL mantığındaki tabloyu da table kısmına giriyoruz 
 Table daki Field kısımlarına önceden oluşturduğumuz elemetleri çekiyoruz. 

## !Client uyarısı için tabloya MANDT alanı girilmeli 


#### VARİABLE: structure ın her bir column u 

#### STRUCTURE: tablonun her bir satırı 

## gv-->burdaki v variable demek gv global variable demek 

#### VARIABLE TANIMLAMAK 

```abap
 DATA: gv_persid TYPE zbk_persi_de, 
 gv_persoyad TYPE ZBK_PERSSOYAD_DE. 
```

## Variable bellekte geçici alan oluşturur. 
 Sadece kod çalışırken kullanılır. 
 Veritabanında bir yeri yoktur. 
 Yani SE11 ile tanımlanan alan fiziksel olarak vardır. Fakat DATA TYPE ile tanımmlanan değişken sadece bellekte çalışır. 

## GEÇİCİ TABLO TANIMI 
```abap

DATA: gv_persid TYPE TABLE OF zbk_pers_t.
```

# ABAPTA SORGULAR 

```abap
SELECT * FROM zbk_pers_t 
INTO TABLE gt_pers_t 
```
 yani aslında select * from kısmı hem sql de hem abapta aynıdır. 
## INTO TABLE dan sonraki kısım benim kalıcı tablodan aldığım verileri geçici tabloya ya da structure a aktardığım kısımdır. 

Tek satır almak için INTO ile Structure yapısı kullanılır. ÇOK satır kayıt almak için INTO TABLE kullanarak geçici tabloda tutulur. 

# Örneğin: 
```abap
DATA: gs_musteri TYPE ztbl_musteri. 

SELECT SINGLE * FROM ztbl_musteri INTO @gs_musteri 
WHERE musteri_no =’0001’ 

DATA: gt_musteri TYPE TABLE OF ztbl_musteri WITH EMPTY KEY. 

SELECT * FROM ztbl_musteri INTO TABLE @gt_musteri. 
```
## INSERT İŞLEMLERİ 
```abap

INSERT zbk_pers_t FROM gs_pers_t.
```

## DELETE İŞLEMİ 
```abap

DELETE FROM zbk_pers_t WHERE pers_id EQ 2.
```

## MODIFY İŞLEMİ 
```abap

MODIFY zbk_pers_t FROM gs_pers_t.  -->FROM ‘dan sonra yazılan ifadenin key’ i var mı diye bakacak yoksa ekleyecek 
```

# KULLANICI VERİ GİRİŞLERİ 

## PARAMETERS: Program çalışırken kullanıcıdan veri almak için kullanılır. 
```abap
PARAMETERS: p_num1 TYPE int4. 
```
 Parametrenin daha güzel görünmesi için yukarıdaki menüden GİT->Metin Sembolü->Selection Texts 
 burada bir tanımlama girebilirsiniz. 

# ! Aslında Domainler Fieldların veri türleri ve ben sistemde parametre ya da variable tanımlarken de türü olarak data_elementini kullanırım kullanırım. 

## SELECT OPTIONS 

 Parameters ile tek data alabiliyordum select option ile çoklu data alabilirim. 

```abap
DATA: gv_persoyad TYPE int4, 

SELECT-OPTIONS: s_ad FOR gv_perssoyad. 

SELECT-OPTIONS: s_ad FOR gv_psrsoyad, 
s_ad for ZBK_PERS_T-PERS_CINS: 
```

###### ! s_perssd alanı 8 karakterden büyük olursa eğer hata verir. 


###### s_ad-> kullanıcının seçim yapacağı alan (bu bir internal table gibi çalışır) 

## CHECKBOX 

```abap
PARAMETERS: p_cbox1 AS CHECKBOX 
```
## RADIO BUTTON 
```abap
PARAMETERS: p_rad1 RADIOBUTTON GROUP  gr1, 
p_rad2 RADIOBUTTON GROUP gr2. 
```






# INITIALIZATION.    -->Program çalışmaya başladığında ilk tetiklenen bloktur. Değişkenlere değer atanabilir.kullanıcının henüz ekranla etkileşime geçmediği noktadır. 

```abap
p_num =12. 

 AT SELECTION-SCREEN.    -->Kullanıcı seçim ekranında bir işlem yaptığı an tetiklenir.(ENTER’a bastığında). 
* Genelde burada kullanıcıdan gelen veri kontrol edilir(validation yapılır.) 

 p_num =p_num + i. 

 START OF-SELCTION.   -->Seçim ekranı geçildikten sonra ana iş mantığının başladığı yerdir. Genellikle burada veritabanı sorguları,işlemler başlatılır. 

 WRITE ‘START-OF-SELECTION’ 

 PERFORM sayiya_bir_ekle. (Burada FORM bu şekilde çağrılabilir) 

 PERFORM iki_sayinin_carpimi USING 10 
 5. 

 END-OF-SELECTION   -->START-OF-SELECTION sonrası tetiklenen kapanış bloğudur. 
*Genellikle sonuçların gösterimi veya rapor çıktıları burada yapılır. 

 WRITE ‘END-OF-SELECTION’ 
```
## FORM 

```abap
FORM sayiya_bir_ekle 
gv_num1 = gv_num1 + 1. 
ENDFORM. 
```
### !Forma değişken gönderme 
```abap
 FORM iki_sayinin_carpimi USING p_num1 
 p_num2. 
 gv_num1 = gv_num1 + i. 

 ENDFORM. 


 FORM iki_sayinin_carpimi USING p_num1 
 p_num2. 

DATA: lv_sonuc TYPE int4. 
lv_sonuc = p_num1 * p_num2. 
WRITE: ‘Sonuc = ’, lv_sonuc. 

ENDFORM. 
```

 ! FORM içinde tanımlanan değişkenler lokal değişkenlerdir. Bu yüzden değişkenlerin başında lv var. LOCAL VARIABLE 

# INCLUDE 

 INCLUDE SAP’da bir kod bloğunu başka bir programın içine gömmek için kullanılır. 
Tek başına çalışmaz. 

 Bu yüzden genellikle, 
• ###### Ortak tanımlar 
• ###### Ortak fonksiyon çağrıları 
• ###### FORM blokları için kullanılır. 

#### PHP’de 

 INCLUDE ‘dosya.php’ dendiğinde o dosya gerçekten çalışır. 
 INCLUDE edilen dosya kendi başına da işlem yapabilir. 

#### C#’ da ise bunun yerine kullanılan ifade using ‘dir. 
Bu, başka bir namespace’i yani kod dosyasını görünür kılar. 
 Using sadece erişim sağlar, çalıştırmaz. Bu konuda SAP’daki mantığa benzer. 

C# ‘da bir dosyayı include ettiğinde o kodun içinde main fonksiyonu yoksa, o dosya kendi başına çalışmaz. 

###### PEKİ DEĞİŞKENLERİ KARŞILAŞTIRIRSAK 

 C#’da Class’ın içinde ama fonksiyonun dışında olan değişkenler Global, fonksiyonun içinde olan değişkenler lokaldir. Aynı şekilde bu mantık PHP’de de aynıdır. 

 C#’da neydi class mantığı vardı bu yüzden var h= new CLASSNAME() diyerek nesne oluştururduk. 

 Eğer new ile uğraşmadan direkt nesne oluşturnmak istersek eğer bu durumda statik özelliğini kullanırdık. Mesela; 
```csharp
 public class Hesaplama 
 { 
 public int Topla(int a, int b) 
 { 
 return a + b; 
 } 
 } 
 var h= new Hesaplama(); 
 int sonuc = hnTopla(2,3); 


 public class Hesaplama 
 { 
 public static int Topla(int a, int b) 
 { 
 return a + b; 
 } 
 } 
 int sonuc = Hesaplama.Topla(2,3); 
 ```




## FONKSİYON 

 Önce fonksiyon grubu oluşturulur daha sonrasında fonksiyon modülü oluşturulur. 
```abap
 FUNCTION 
 ... 

 ENDFUNCTION. 
```
##### IMPORT PARAMETRELERİ: 

 Değiştirilemezler(default olarak): Eğer CHANGING veya EXPORT yapılmadıysa, bu parametrelerle gelen veriler fonksiyon içinde değiştirilse bile dışarıya yansımaz. Localdir. 

 fonksiyon içinde değiştirebilmek için “pass by value” işaretlenirse fonksiyonun içinde de değeri değiştirilebilir. 

 ! Hata yönetimi function daki exceptiondan sağlanır. 

 Burada tanımlanan hata 
```abap
DATA: gv_num1 TYPE int4,
            gv_num2 TYPE int4,
            gv_sonuc TYPE int4,
            gv_mes TYPE char20,

START-OF-SELECTION.

CALL FUNCTION  ‘FONKSIYON_ADI’
   EXPORTING
         iv_num1 = gv_num1
         iv_num2 = gv_num2
  IMPORTING
         ev_sonuc = gv_sonuc
  CHANGING
        cv_mes = gv_mes
  EXCEPTIONS
        divided_by_zero = 1
        OTHERS
IF sy_subrc  eq 0.

  write: / ‘Sonuc:’, gv_sonuc.

ELSEIF sy_subrc eq 1.
    write: / ’= a bölemezsiniz.’
ENDIF.
```


# !sy_subrc---> 0 olması sistemde herhangi bir hata olmadığında kullanılır. 


## CLASS: 
```abap
CLASS path_op DEFINITION.
PUBLIC SECTION.
    DATA: lv_num1 TYPE i,
                lv_num2 TYPE i,
                lv_result TYPE i.

    METHODS: sum_numbers.
ENDCLASS.

CLASS math_op IMPLEMENTATION.
    METHOD sum_numbers.
        lv_result = lv_num1 + lv_num2.
    ENDMETHOD.
ENDCLASS.


DATA: go_math_op TYPE REF TO math_op.
 START-OF-SELECTION.

CREATE OBJECT: go_math_op
```
## CLASS -->methods 

 Class içindeki function demek aslında 
```abap
 METHOD sum_numbers. 
 ev_result = iv_num1 + iv_num2. 
 ENDMETHOD.
```


#### PEKİ FUNCTION İLE METHOD ARASINDAKİ FARK NEDİR? 

 Bu aslında bir OOP sorusudur. 

 FUNCTION-> METHOD 
 Global olarak tanımlanmış, çağrıldığında belirli bir işi yapan bağımsız kod parçacıklarıdır. 
 Bir sınıf(class) içerisinde tanımlanmış alt programlardır. Nesne yönelimli programlamanın parçasıdır 
 Globaldir. Her yerden çağrılabilir. 
 Sadece tanımlandığı sınıf üzerinden çağrılır. 
 Geleneksel ABAP projelerinde yaygındır. 
 Nesne yönelimli ABAP projelerinde kullanılır. 

###### Bir Methodu Çağırırken İzlenecek Yol 
 -->SE38 
 --> 
```abap

DATA: olusturdugun_obje TYPE REF TO referansini_alacagim_ana_class.
DATA: gv_num1 TYPE int4,
            gv_num2 TYPE int4,
            gv_result TYPE int4.

START OF SELECTION.
CREATE OBJECT olusturdugun_obje.

olusturdugun_obje->sum_numbers(
  EXPORTING
     iv_num1 = gv_num1
     iv_num2 = gv_num2

  IMPORTING
     ev_result = gv_result
).

WRITE: gv_result.
```

## STATIC METHOD 

obje oluşturmaya gerek kalmadan methoda ulaşmak için. 

 referansini_alacagim_ana_class=>sum_numbers_v2(). 

## FRIENDS 

 Başka bir class’ın methodunu kullanmaya yarar. 

## EVENTS-->Bu iş bitti, haberiniz olsun.İsteyen tepki versin. 


 kullanmak için METHODS tabında properties’e tıklanarak hangi class’ın hangi eventini kullanmak istiyorsak seçmeliyiz. 

## INTERFACE-->Bu işi yapmayı kabul ettim,kurallara uyacağım. 

## ALIASES-->İnterface’lere isim vermek için kullanılır. 

###### Bir örnekle Interface ve Event arasındaki farkı açıklayalım. 
```abap
INTERFACE zif_order_handler
      METHODS:
         create_order IMPORTING iv_order_id TYPE char10.
ENDINTERFACE.
```
###### İnterfaceimizi tanımladık. Bu interface i kullanan sınıflar sipariş oluşturmalı. 

###### Şimdi EVENT’i fırlatacak sınıfı oluşturalım 
```abap
CLASS zcl_order_manager DEFINITION.
   PUBLIC SECTION.
      INTERFACES zif_order_handler.
      EVENTS order_created FOR_OBJECT zcl_order_manager
          EXPORTING VALUE(ev_order_id) TYPE char10.
ENDCLASS.

CLASS zcl_order_manager IMPLEMENTATION .

     METHOD zif_order_handler~create_order.
        WRITE: ‘Sipariş oluşturuldu’, iv_order_id.

       RAISE EVENTvorder_created EXPORTING ev_order_id.
   
    ENDMETHOD.
ENDCLASS.
```

###### Şimdi dinleyici class ımızı oluşturalım 
```abap
CLASS zcl_order_logger DEFINITION.
    PUBLIC SECTION.
       METHODS log_order FOR EVENT order_created OF zcl_order_manager
           IMPORTING ev_order_id.
ENDCLASS.

CLASS zcl_order_logger IMPLEMENTATION.

    METHOD log_order.
       WRITE: / ‘Log: Sipariş Alındı’,ev_order_id.
    ENDMETHOD.

ENDCLASS.
```


###### Şimdi de ana programımızı yazalım. 
```abap
DATA(lo_order_manager)= NEW zcl_order_manager().
DATA(lo_logger) = NEW zcl_order_logger().

SET HANDLER lo_logger->log_order FOR lo_order_manager.
lo_order_manager->zif_order_handler~create_order(iv_order_id = ‘ORD12345’).
```

Burada 
 SET HANDLER Dinleyiciyi aktif hale getirdi 
 RAISE EVENT ile olayı tetikledi. 

## ALT SINIF

```abap
CLASS math_op DEFINITION.
PUBLIC SECTION.
*buradaki public section aslında bu sınıfın dışındaki kodların erişebileceği methodları tanımlamak için kullanılıyor.
DATA:lv_num1 TYPE i,
lv_num2 TYPE i,
lv_result TYPE i.
METHODS: sum_numbers.
ENDCLASS.
*yukarıda oluşturduğumuz sınıf aslında ana class'tır.

CLASS math_op IMPLEMENTATION.
METHOD sum_numbers.
lv_result = lv_num1 + lv_num2.
ENDMETHOD.
ENDCLASS.
*IMPLEMENTATION kısmı DEFINITION'da sadece adı geçen metodların nasıl çalışacağını tanımladığımız yerdir.

CLASS math_op_diff DEFINITION INHERITING FROM math_op.
PUBLIC SECTION.
METHODS numb_diff.
ENDCLASS.
*yukarıda math_op sınıfının bir alt sınıfını oluşturduk.

CLASS math_op_diff IMPLAMENTATION.
METHOD numb_diff.
lv_result = lv_num1 - lv_num2.
ENDMETHOD.
ENDCLASS.


DATA:go_math_op TYPE REF TO math_op.
START-OF-SELECTION.

CREATE OBJECT:go_math_op.
CREATE OBJECT:math_op_diff.

go_math_op ->lvnum1 = 12.
go math_op->lv_num2 = 23.
go_math_op->sum_numbers().

WRITE: go_math_op->lv_result.

go_math_op_diff->lv_num1 = 12.
go_math_op_diff->lv_num2 = 7.
go_math_op_diff->numb_diff().

```
Peki aynı örneği ben PHP'de yapsaydım nasıl yapardım
```php
class MathOp{
public $num1;
public$num2;
public $result;

public function sumNumbers(){
$this->result = $this->num1 + $this->num2; 
}
}
class MathOpDiff extends MathOp {
public function numbDiff(){
$this->result = $this->num1 - $this->num2;

}
}
$math = new MathOpDiff();
$math->num1 = 12;
$math->num2 = 23;
$math->sumNumbers();
echo "Toplam:" . $math->result . "\n";

$math->numbDiff();
echo "Fark:" . $math->result ."\n";

```
Peki aynı örneği C#'da yapsaydık nasıl yapardık.
```csharp
using System;
class MathOp
{
public int num1;
public int num2;
public int result;

public void SumNumbers()
{
result = num1 - num2;
}
}
class MathOpDiff : MathOp
{
public void NumbDiff()
{
result = num1 -num2;
}

}
class Program {
static void Main()
{
MathOpDiff math = new MathOpDiff();
math.num1 = 12;
math.num2 = 23;

math.SumNumbers();
Console.WriteLıne("Toplam:" + math.result);

math.NumbDiff();
Console.WriteLine("Fark:"+ math.result);
}
}
```
Bir şey farkettiniz mi?
Evet IMPLEMANTATION bloğu PHP ve C#'da yok.

## PACKAGE

! Eğer SE80 ile girip Package seçtikten sonra $TMP yazarsanız local objeleri görebilirsiniz.
Bir package oluşturmak için

## MESSAGE TYPE

6 tane mesaj tipi var.
1.Bunlar success, error, warning mesajı
2.Pop-up mesajlar
3.ex mesaj

### Success mesajı
```abap
START-OF-SELECTION


MESSAGE 'Hello abap' TYPE 'S'.
write: 'Message Abap'.

```
### İnfo mesajı
pop-up şeklinde bilgi mesajı vermek için
```abap
START-OF-SELECTION

MESSAGE 'Hello abap' TYPE 'I'.
write: 'Message Abap'.

```
### Warning mesajı
yazıldığı yerde akışı durdurur alttaki abap yazısını vermek
```abap
START-OF-SELECTION


MESSAGE 'Hello abap' TYPE 'W'.
write: 'Message Abap'.

```
### Error mesajı
warning mesajı gibi davranır

```abap
START-OF-SELECTION

MESSAGE 'Hello abap' TYPE 'E'.
write: 'Message Abap'.
```
## Abend mesajı
pop-up şeklinde bir uyarı mesajıdır.programın akışını durdurur ve anasayfaya atar.
geri dönülemez mantıksal olarak hatalı bir durumda alınır.

```abap
START-OF-SELECTION


MESSAGE 'Hello abap' TYPE 'A'.
write: 'Message Abap'.
```
### Exit mesajı
hatayı dump(sistemsel) ekranında verir.
Ciddi ve sistemsel seviyede bir hata olduğunda alınır.

```abap
START-OF-SELECTION

MESSAGE 'Hello abap' TYPE 'X'.
write: 'Message Abap'.

```

### Hata mesajlarının viewını değiştirme

```abap
MESSAGE 'Hello abap' TYPE 'S'. DISPLAY LIKE 'A'
```

#### Diğer Hata'nın değiştirilme yöntemleri

Git-> Metin Sembolleri

```abap
MESSAGE text-000 TYPE 'I'.
MESSAGE text-000 TYPE 'S'.
```

#### Mesaj class'ı oluşturup mesajarı yönetmek

SE91 ->Mesaj class'ı oluşturmak için

```abap
MESSAGE i000(zegt)
```
#### Mesaj class'ında parametre kullanamak
parametre tanımlarken üstteki yöntemi takip edip değiştirilebilir kısıma & işareti konmalı.

```abap
MESSAGE i0001 WITH 'Çarşamba'.

```
Bir kaç tane parametre varsa

```abap
MESSAGE i0001 WITH 'Çarşamba' 'Perşembe'.

```
# DEBUG
/h yazıp entera bas F8 yap
F5->bir sonraki satıra geç
F6->Bir sonrakisatıra geç ama içine girmeden geç
F7->Ondan çık onun çağrıldığı programa dön
F8->Debugdan çık


# EKRAN TASARIMI
Nesne listesi görünümü -> Programda oluşturulan objeleri listeler

## PBO---->Screen----->PAI

PBO: Screen ekrana gelmeden önce çalışcak kısım
PAI: Screen ekrana geldikten sonra çalışacak kısım
## SCREEN
```abap
CALL SCREEN 01000.
```

## GUI STATUS- GUI TITLES

```abap
MODULE status_0100 OUTPUT.
SET PF-STATUS 'STATUS 0100'.
SET TITLEBAR 'TITLE_0100'.
ENDMODULE.
```
###### ! sy-ucomm--->anlık olarak ekrana vermiş olduğumuz butonun funtion kodunu tutar.

```abap
MODULE user_command_0100 INPUT.
IF sy-ucomm EQ '&BACK'.
LEAVE TO SCREEN 0.
ENDIF.
ENDMODULE.
```
!LEAVE TO SCREEN 0.--> ekrandan çık yani

## GUI-STATUS çoklu buton oluşturma
```abap
MODULE user_command_0100 INPUT.
DATA: lv_text TYPE char200.
CONCATENATE sy-ucomm
'butonuna basılmıştır'
INTO lv_text
SEPERATED BY space.

MESSAGE lv_text TYPE 'I'.

CASE
WHEN '&BCK'.
LEAVE TO SCREEN 0.
ENDCASE.

IF sy-ucomm EQ '&BACK'.
LEAVE TO SCREEN 0.
ENDIF.
ENDMODULE.
```
###### ! CONCATENATE--> Bİrden fazla string ifadeyi birleştirmek için


# LAYOUT'TA RADIO BUTTON

```abap
MODULE user_command_0100 INPUT.

CASE sy-ucomm.
WHEN '&BCK'.
*IF gv_rad1 eq 'X'.
IF gv_rad1 eq abap_true.
else.
ENDIF.
LEAVE TO SCREEN 0.
ENDCASE.

ENDMODULE.
```
# CLEAR

```abap
MODULE user_command_0100 INPUT.

CASE ok_code.
WHEN '&BCK'.
LEAVE TO SCREEN 0.
WHEN '&CLEAR'.
CLEAR: gv_ad,
gv_soyad,
gv_yas,
gv_yas,
gv_cbox.
gv_rad1 = abap_true.
ENDCASE.

ENDMODULE.
```

# SUBSCREEN
```abap
MODULE status_0100.
call SUBSCREEN sub1 INCLUDEDING sy-repid '0101'.

PROCESS AFTER INPUT.
MODULE user_command_0100.
CALL SUBSCREEN sub1.
```

###### !sy-repid---> screenin tutulduğu program.

# SUBSTREPT

```abap
MODULE user_command_0100 INPUT.
CASE sy-ucomm.
when '&BACK' OR '&EXIT'.
SET SCREEN 0.
WHEN ''&ATAB1.
tb_id-activetab = '&TAB1'.
WHEN ''&ATAB2.
tb_id-activetab = '&TAB2'.
ENDCASE.
ENDMODULE.
```
# SALV
```abap
DATA: gt_sbook TYPE TABLE OF sbook,
      go_salv type REF TO cl_salv_table.
START-OF-SELECTION

SELCET * UP TO 20 ROWS FROM sbook
into TABLE gt_sbook.

cl_salv_table=>factory(
IMPORTING
r_salv_table = go_salv
CHANGING
t_table = gt_sbook
).
```

#### SAP'nin kendi içinde oluşturduğu test TABLE'ı SBOOK koduyla bulabiliriz bunun için SE16n -->SBOOK yapmak gereklidir.

# REUSE ALV

```abap
TYPES: BEGIN OF gty_list,
ebeln TYPE ebeln,
ebelp TYPE ebelp,
bstyp TYPE ebstyp,
bsart TYPE esart,
matnr TYPE matnr,
menge TYPE bstmg,
END OF gty_list.

DATA: gt_list TYPE TABLE OF gty_list,
gs_list TYPE gty_list.

DATA: gt_fieldcatalog TYPE slis_t_fieldcat_alv,
gs_fieldcatalog TYPE slis_fieldcat_alv.

START OF SELECTION.

PERFORM get_data.
PERFORM set_fc.
PERFORM set_layout.
PERFORM display_alv.

SELECT
ekko-ebeln
ekpo-ebelp
ekko-bstyp
ekko-bsart
ekpo-matnr
ekpo-menge
FROM ekko
INNER JOIN ekpo ON ekpo-ebln EQ ekko-ebeln
INTO TABLE gt_list.

CLEAR: gs_fieldcatalog.
gs_fieldcatalog-fieldname = 'EBELN'.
gs_fieldcatalog-seltext_s = 'SAS No'
gs_fieldcatalog-seltext_m = 'SAS Numarası'
gs_fieldcatalog-seltext_l = 'SAS No'
gs_fieldcatalog-col_pos = 0.
APPEND gs_fieldcatalog TO gt_fieldcatalog.

CLEAR: gs_fieldcatalog.
gs_fieldcatalog-fieldname = 'EBELP'.
gs_fieldcatalog-seltext_s = 'Kalem'
gs_fieldcatalog-seltext_m = 'Kalem'
gs_fieldcatalog-seltext_l = 'Kalem'
gs_fieldcatalog-key = abap_true.
gs_fieldcatalog-col_pos = 1.
APPEND gs_fieldcatalog TO gt_fieldcatalog.


CLEAR: gs_fieldcatalog.
gs_fieldcatalog-fieldname = 'BSTYP'.
gs_fieldcatalog-seltext_s = 'Belge Tipi'
gs_fieldcatalog-seltext_m = 'Belge Tipi'
gs_fieldcatalog-seltext_l = 'Belge Tipi'
gs_fieldcatalog-col_pos = 4.
APPEND gs_fieldcatalog TO gt_fieldcatalog.

CLEAR: gs_fieldcatalog.
gs_fieldcatalog-fieldname = 'BSART'.
gs_fieldcatalog-seltext_s = 'Belge Türü'
gs_fieldcatalog-seltext_m = 'Belge Türü'
gs_fieldcatalog-seltext_l = 'Belge Türü'
gs_fieldcatalog-col_pos = 5.
APPEND gs_fieldcatalog TO gt_fieldcatalog.

CLEAR: gs_fieldcatalog.
gs_fieldcatalog-fieldname = 'MATNR'.
gs_fieldcatalog-seltext_s = 'Malzeme'
gs_fieldcatalog-seltext_m = 'Malzeme'
gs_fieldcatalog-seltext_l = ''Malzeme'
gs_fieldcatalog-col_pos = 3.
APPEND gs_fieldcatalog TO gt_fieldcatalog.

CLEAR: gs_fieldcatalog.
gs_fieldcatalog-fieldname = 'MENGE'.
gs_fieldcatalog-seltext_s = 'Miktar'
gs_fieldcatalog-seltext_m = 'Miktar'
gs_fieldcatalog-seltext_l = 'Miktar'
gs_fieldcatalog-col_pos = 2.
APPEND gs_fieldcatalog TO gt_fieldcatalog.

gs_layout-window_titlebar = 'REUSE ALV'.
gs_layout-zebra = abap_true.
gs_layout-colwidth_optimize = abap_true.


CALL FUNCTION 'REUSE_ALV_GRID_DISPLAY'
EXPORTING
is_layout = gs_layout
it_fieldcat = gt_fieldcatalog
TABLES t_outtab = gt_list
IF sy-subrc <> 0.
Implement suitable error handling here
ENDIF


```
NOT:

window_titlebar: ALV başlığı

	•	zebra: Satırlar arası gri-beyaz şerit

	•	colwidth_optimize: Sütun genişliğini otomatik ayarlama 
 
Bu, ALV ekranını çağıran SAP’nin standart fonksiyonudur.

	•	EXPORTING: fieldcatalog, layout, veri gibi parametreler bu alanda verilir

	•	TABLES: gösterilecek veri tablosu (gt_list) buraya verilir 

 # ALV(ABAP List Viewer) Nedir?
 
 SAP'de verileri excel gibi tablo halinde kullanıcıya göstermek için kullanılır.

 # FIELD CATALOG (ALAN KATALOĞU) NEDİR?

 ALV tablosunda hangi alanların gösterilebileceğini, başlıklarının ne olacağını, görünümünü belirler.

 # LAYOUT NEDİR?

 ALV tablosunun görsel ayarlarını yapar:
 
 Renkli olsun mu? Zebra olsun mu? gibi.

 

 
 # SAP ALV (ABAP List Viewer) Türleri ve Örnekleri
SAP'de veri raporlaması için kullanılan ALV (ABAP List Viewer) yapılarını açıklayan ve örneklerle desteklenen detaylı bir rehber.
---
## 1. REUSE_ALV_GRID_DISPLAY
**Tanım:**  
Klasik ABAP programlarında kullanılan en yaygın ALV fonksiyon modülüdür.
**Avantajlar:**
- Eski sistemlerde bile çalışır.
- Kullanımı hızlıdır.
**Kod Örneği:**
```abap
REPORT z_alv_reuse_example.
TABLES: ekko.
TYPES: BEGIN OF ty_data,
        ebeln TYPE ekko-ebeln,
        bstyp TYPE ekko-bstyp,
      END OF ty_data.
DATA: it_data TYPE TABLE OF ty_data,
     wa_data TYPE ty_data.
SELECT ebeln bstyp FROM ekko INTO TABLE it_data UP TO 20 ROWS.
DATA: it_fcat TYPE slis_t_fieldcat_alv,
     wa_fcat TYPE slis_fieldcat_alv.
wa_fcat-fieldname = 'EBELN'.
wa_fcat-seltext_m = 'Belge No'.
APPEND wa_fcat TO it_fcat.
wa_fcat-fieldname = 'BSTYP'.
wa_fcat-seltext_m = 'Belge Tipi'.
APPEND wa_fcat TO it_fcat.
CALL FUNCTION 'REUSE_ALV_GRID_DISPLAY'
 EXPORTING
   it_fieldcat = it_fcat
 TABLES
   t_outtab    = it_data.
```
---
## 2. CL_GUI_ALV_GRID
**Tanım:**  
Nesne yönelimli ABAP ile geliştirilmiş ALV yapısıdır. Gelişmiş kullanıcı etkileşimleri sunar.
**Kod Örneği:**
```abap
REPORT z_alv_gui_example.
DATA: gr_alv      TYPE REF TO cl_gui_alv_grid,
     gr_cont     TYPE REF TO cl_gui_custom_container,
     it_data     TYPE TABLE OF ekko,
     ok_code     TYPE sy-ucomm.
SELECT * FROM ekko INTO TABLE it_data UP TO 10 ROWS.
CALL SCREEN 100.
MODULE status_0100 OUTPUT.
 CREATE OBJECT gr_cont
   EXPORTING container_name = 'CONTAINER'.
 CREATE OBJECT gr_alv
   EXPORTING i_parent = gr_cont.
 CALL METHOD gr_alv->set_table_for_first_display
   EXPORTING i_structure_name = 'EKKO'
   CHANGING  it_outtab        = it_data.
ENDMODULE.
MODULE user_command_0100 INPUT.
 CASE ok_code.
   WHEN 'EXIT'.
     LEAVE PROGRAM.
 ENDCASE.
ENDMODULE.
```
---
## 3. CL_SALV_TABLE (SALV)
**Tanım:**  
Daha modern ve sade OOP yapısıyla kullanılır. Fieldcatalog gibi yapıların çoğu otomatik hazırlanır.
**Kod Örneği:**
```abap
REPORT z_salv_example.
DATA: lt_data TYPE TABLE OF ekko,
     lo_alv  TYPE REF TO cl_salv_table.
SELECT * FROM ekko INTO TABLE lt_data UP TO 10 ROWS.
cl_salv_table=>factory(
 IMPORTING r_salv_table = lo_alv
 CHANGING  t_table      = lt_data ).
lo_alv->display( ).
```
---
## Karşılaştırma Tablosu
| Özellik              | REUSE_ALV_GRID_DISPLAY | CL_GUI_ALV_GRID       | CL_SALV_TABLE         |
|----------------------|------------------------|------------------------|------------------------|
| Yapı                 | Fonksiyon              | OOP                    | OOP (minimalist)       |
| GUI Etkileşimi       | Kısıtlı                | Gelişmiş               | Yok                    |
| Kod Miktarı          | Orta                   | Fazla                  | Az                     |
| Güncellik            | Eski                   | Modern                 | Modern & Sade          |
| Özelleştirilebilirlik| Orta                   | Çok yüksek             | Düşük                  |
---
> Her ALV türü, ihtiyacına göre farklı projelerde tercih edilebilir.
>
> # ABAP'ta INSERT, APPEND ve SQL INSERT Farkları
Bu doküman, ABAP ve SQL dünyasında kullanılan `INSERT`, `APPEND` gibi komutların farklarını ve kullanım amaçlarını karşılaştırmalı olarak açıklar.
---
## 1. SQL'deki `INSERT`
SQL dilinde kullanılır, **veritabanındaki fiziksel bir tabloya yeni satır ekler**.
```sql
INSERT INTO tablo (alan1, alan2) VALUES ('deger1', 'deger2');
```
**Özellikleri:**
- Kalıcı olarak veritabanına kayıt yazar
- SAP’nin arkasındaki fiziksel tabloları etkiler
---
## 2. ABAP'taki `INSERT`
ABAP dilinde iki farklı şekilde kullanılır:
### a. Internal Table'a INSERT (Sıralı yerleştirme)
```abap
INSERT wa_satir INTO TABLE it_tablo.
```
- İç tabloya uygun sırada veri ekler
- Sorted table kullanıldığında doğru sıraya göre ekler
### b. Veritabanına INSERT (SQL gibi)
```abap
INSERT ztablo FROM wa_veri.
```
- SAP'nin veritabanındaki tabloya veri ekler
- SQL `INSERT INTO` ile eşdeğerdir
---
## 3. ABAP'taki `APPEND`
```abap
APPEND wa_satir TO it_tablo.
```
- İç tabloya **sonuna** veri ekler
- Sorted veya Hashed olmayan tablolar için uygundur
---
## 4. APPEND vs INSERT Karşılaştırması (Internal Table Bağlamında)
| Özellik           | `APPEND`                        | `INSERT INTO TABLE`                |
|------------------|----------------------------------|------------------------------------|
| Ekleme pozisyonu | Her zaman **en sona** ekler       | Sorted table ise **sıraya göre** ekler |
| Hata kontrolü     | Yinelenen veri eklenebilir        | Sorted veya Hashed tabloda hata verebilir |
| Performans       | Genellikle daha hızlı             | Kontrol içerdiği için daha yavaş olabilir |
| Kullanım alanı   | ALV fieldcatalog, klasik listeler | Sorted tablolar, benzersiz anahtarlı tablolar |
---
## 5. Kod Örnekleri
### APPEND Örneği:
```abap
DATA: lt_list TYPE TABLE OF string,
     lv_satir TYPE string.
lv_satir = 'Merhaba dünya'.
APPEND lv_satir TO lt_list.
```
### INSERT (Internal Table) Örneği:
```abap
DATA: lt_list TYPE SORTED TABLE OF string WITH UNIQUE KEY table_line,
     lv_satir TYPE string.
lv_satir = 'Merhaba SAP'.
INSERT lv_satir INTO TABLE lt_list.
```
### INSERT (Veritabanı) Örneği:
```abap
DATA: wa_data TYPE ztablo.
wa_data-id = 1001.
wa_data-name = 'Yeni Kayıt'.
INSERT ztablo FROM wa_data.
```
---
## Sonuç
- **SQL INSERT** → Veritabanına kayıt atar
- **ABAP APPEND** → İç tabloya sona ekler
- **ABAP INSERT** → İç tabloya uygun sırada ekler veya veritabanına kayıt atar
> Hangi INSERT kullanacağını, tablo tipi ve veri yapısı belirler.

# SAP ALV'de `CL_GUI_ALV_GRID` ve `Container` Yapıları
Bu doküman, SAP ABAP'ta `CL_GUI_ALV_GRID` kullanılarak yapılan nesne yönelimli ALV ekranları ve bu yapıların yerleştirildiği `Container` kavramını açıklar.
---
## 1. Container Nedir?
**Container**, SAP GUI ekranlarında ALV gibi nesneleri yerleştirmek için kullanılan bir "görsel alan"dır.
### Neden Gerekli?
- ALV grid gibi nesneler doğrudan ekrana basılamaz.
- Bir alana (container) yerleştirilerek görünmeleri sağlanır.
### Yaygın Container Türleri
| Container Türü              | Açıklama                                         |
|----------------------------|--------------------------------------------------|
| `CL_GUI_CUSTOM_CONTAINER`  | Ekranda belirli bir alanı hedef alır             |
| `CL_GUI_DOCKING_CONTAINER` | Ekranın kenarına kenetlenir                      |
| `CL_GUI_SPLITTER_CONTAINER`| Ekranı bölerek birden fazla container oluşturur |
---
## 2. CL_GUI_ALV_GRID Nedir?
`CL_GUI_ALV_GRID`, GUI tabanlı ekranlarda ALV (ABAP List Viewer) göstermek için kullanılan sınıftır.
---
## 3. Kod Örneği ve Açıklamaları
```abap
DATA: gr_alvgrid  TYPE REF TO cl_gui_alv_grid,
     gr_container TYPE REF TO cl_gui_custom_container.
CREATE OBJECT gr_container
 EXPORTING container_name = 'CONTAINER'.
```
- `gr_container`: Ekranda çizilmiş alana referanstır (SE51'de çizilen Custom Control)
- `CREATE OBJECT`: Nesne oluşturulur
```abap
CREATE OBJECT gr_alvgrid
 EXPORTING i_parent = gr_container.
```
- `gr_alvgrid`: ALV grid nesnesi oluşturulur
- `i_parent`: Hangi container içinde gösterileceğini belirler
```abap
CALL METHOD gr_alvgrid->set_table_for_first_display
 EXPORTING i_structure_name = 'EKKO'
 CHANGING  it_outtab        = gt_data.
```
- `set_table_for_first_display`: ALV'yi veri ile doldurur
- `i_structure_name`: Gösterilecek verinin yapısı (örneğin EKKO tablosu)
- `it_outtab`: Verinin kendisi (internal table)
---
## 4. Akış Özet
1. Ekrana bir Custom Control çizilir (`SE51`)
2. `CL_GUI_CUSTOM_CONTAINER` ile bu alan programda tanımlanır
3. `CL_GUI_ALV_GRID` nesnesi oluşturulur
4. Veri, `set_table_for_first_display` ile ALV'ye bağlanır
5. ALV ekranda gösterilir
---
## 5. Gerçek Hayattan Benzetme
| Gerçek Dünya         | SAP Karşılığı                 |
|----------------------|-------------------------------|
| Tepsi                | Container                     |
| Tabak (içerik)       | ALV Grid                      |
| Yiyecek (veri)       | Internal Table (gt_data)      |
| Tepsiye tabağı koymak| ALV'yi container'a bağlamak   |
---
> Bu yapı sayesinde SAP GUI ekranları etkileşimli ve şık hale gelir. Özellikle F4 yardımı, buton ekleme, renklendirme gibi işlemler için `CL_GUI_ALV_GRID` tercih edilir.


# SAP ABAP’ta FORM – PERFORM Yapısı ve Object-Oriented (OO) Yaklaşımı



##  FORM – PERFORM Nedir?

PERFORM, klasik ABAP’ta bir alt programı (subroutine) çağırmak için kullanılır.

FORM, çağrılan o alt programı tanımladığın bölümdür.

Ne işe yarar?

	•	Kod tekrarını önler
 
	•	Modüler yapı sağlar (aynı işlemi tekrar tekrar yazmak yerine bir yerde tanımlayıp çağırırsın)
 
	•	Prosedürel (sıralı) programlamada kullanılır

 ```abap
START-OF-SELECTION.
  PERFORM hesapla USING 10 20.

FORM hesapla USING p_sayi1 TYPE i p_sayi2 TYPE i.
  DATA: sonuc TYPE i.
  sonuc = p_sayi1 + p_sayi2.
  WRITE: / 'Sonuç:', sonuc.
ENDFORM.
```

##  PERFORM – USING ne demek?

	•	PERFORM çağrısı ile dışardan veri gönderirsin
 
	•	USING ile bu verileri FORM bloğu alır

 ```abap
PERFORM hesapla USING 5 10. "GÖNDEREN
FORM hesapla USING a TYPE i b TYPE i. "ALAN
```

## 3. Object-Oriented (Nesne Yönelimli) ABAP’ta Ne Değişti?

OO yapıda FORM – PERFORM kullanılmaz.

Bunun yerine CLASS tanımlanır, işlemler METHOD içine yazılır.

Veri alışverişi şu şekildedir:

	•	IMPORTING: dışarıdan veri alırsın
 
	•	EXPORTING: dışarıya veri gönderirsin
 
	•	CHANGING: hem alırsın hem değiştirirsin
 
	•	RETURNING: bir sonuç döndürürsün (fonksiyon gibi)

 ```abap
CLASS lcl_hesap DEFINITION.
  PUBLIC SECTION.
    METHODS toplama
      IMPORTING
        sayi1 TYPE i
        sayi2 TYPE i
      RETURNING VALUE(sonuc) TYPE i.
ENDCLASS.

CLASS lcl_hesap IMPLEMENTATION.
  METHOD toplama.
    sonuc = sayi1 + sayi2.
  ENDMETHOD.
ENDCLASS.

START-OF-SELECTION.
  DATA(lo_hesap) = NEW lcl_hesap( ).
  DATA(lv_sonuc) = lo_hesap->toplama( sayi1 = 10 sayi2 = 20 ).
  WRITE: / 'Sonuç:', lv_sonuc.
```

##  FORM vs OO (Object-Oriented) Yaklaşım Karşılaştırması

| Klasik Yöntem (FORM)         | OO Yöntem (METHOD)                    |
|-----------------------------|---------------------------------------|
| FORM hesapla              | METHOD toplama                     |
| PERFORM hesapla USING...  | CALL METHOD... IMPORTING...        |
| Prosedürel (sıralı)         | Nesne yönelimli                      |
| Daha eski sistemlerde sık   | Modern SAP sistemlerinde tercih edilir |
| Tek yönlü veri aktarımı     | Çok yönlü ve yapılandırılmış veri    |


##  Ne Zaman FORM, Ne Zaman METHOD?

| Durum                                      | Kullanım Tavsiyesi              |
|-------------------------------------------|---------------------------------|
| Eskiden yazılmış klasik raporlar          | FORM – PERFORM devam ettirilebilir |
| Yeni geliştirme yapıyorsan                | OO (Class/Method) tercih et     |
| Reusable, test edilebilir yapılar gerekiyorsa | OO kesinlikle daha iyi         |


## MODULE – CHAIN – ENDCHAIN Nedir?

	•	Modül havuzu (dialog program – ekran tabanlı program) içinde kullanılır.
 
	•	Dynpro (ekran) işlemleri sırasında tetiklenir.
 
	•	Genellikle ekran alanı kontrolleri, veritabanı işlemleri için kullanılır.

 ```àbap
PROCESS BEFORE OUTPUT.
  MODULE init_screen.

PROCESS AFTER INPUT.
  MODULE kontrol_kullanici.
```

```abap
MODULE kontrol_kullanici INPUT.
  IF kullanıcı_adı IS INITIAL.
    MESSAGE 'Kullanıcı adı boş olamaz' TYPE 'E'.
  ENDIF.
ENDMODULE.
```

## FORM vs MODULE Karşılaştırması

| Kriter              | FORM / PERFORM                    | MODULE                         |
|---------------------|-----------------------------------|--------------------------------|
| Kullanıldığı yer    | Klasik raporlar, genel programlar | Dialog (ekran) programları     |
| Çağırma şekli       | PERFORM form_adi               | MODULE modul_adi             |
| Parametre alma      | USING / CHANGING ile              | Parametre almaz (global alan kullanır) |
| Ekran bağlantısı     | Yok                               | PROCESS bloğuyla çalışır       |
| Bağlı olduğu yapı   | Alt program (subroutine)          | Module Pool (Dynpro)           |



