###### Önce ABAP ile bir class oluşturalım ve ondan miras alalım

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
