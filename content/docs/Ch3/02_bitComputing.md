# 位元運算
> Life is binary zeros and ones.

在這章節我們將會介紹C 語言的位元運算。
相信大家對於位元應該都已經有了基本的認識，在這種情況下再來看位元運算會比較好理解。

## 位元運算子
在電腦中資料的儲存都是利用0/1的編碼進行儲存，像是一個平常普通的十進位數字 10 跟 7，在電腦裡的儲存假設是4個位元則是:

```C++
10 -> 1010
7  -> 0111
```
而在 C 語言裡面有許多的運算子是專門針對位元進行運算的，如下表:


<table class="tg">
  <tr>
    <th class="tg-baqh">運算子</th>
    <th class="tg-yw4l">意義</th>
    <th class="tg-yw4l">舉例</th>
  </tr>
  <tr>
    <td class="tg-baqh">&amp;</td>
    <td class="tg-yw4l">且(and)</td>
    <td class="tg-yw4l">A&B</td>
  </tr>
  <tr>
    <td class="tg-baqh">|</td>
    <td class="tg-yw4l">或(or)</td>
    <td class="tg-yw4l">A|B</td>
  </tr>
  <tr>
    <td class="tg-baqh">^</td>
    <td class="tg-yw4l">互斥或(xor)</td>
    <td class="tg-yw4l">A^B</td>
  </tr>
  <tr>
    <td class="tg-baqh">&lt;&lt;</td>
    <td class="tg-yw4l">向左位移</td>
    <td class="tg-yw4l">A&lt;&lt;B</td>
  </tr>
  <tr>
    <td class="tg-baqh">&gt;&gt;</td>
    <td class="tg-yw4l">向右位移</td>
    <td class="tg-yw4l">A&gt;&gt;B</td>
  </tr>
  <tr>
    <td class="tg-baqh">~</td>
    <td class="tg-yw4l">取1補數</td>
    <td class="tg-yw4l">~A</td>
  </tr>
</table>

## 課堂演練
在這邊我猜大家還是不太了解內容，那麼照舊我們依然從程式面去講解:

```C++
#include <stdio.h>
int main(){
    /*
    C 語言中宣告各個進位方式:
        二進位:0b+數字
        八進位:0+數字
        十進位:數字
        十六進位:0x+數字
    */

    int a = 0b00001010;//10
    int b = 0b00000011;//3
    int c = 0x0;

    /*
    C 語言中printf各個進位之參數:
        二進位:自己寫(...)
        八進位:%o
        十進位:%d
        十六進位:%x
    */

    printf("a & b = %d\n", a & b);
    printf("a | b = %d\n", a | b);
    printf("a ^ b = %d\n", a ^ b);
    printf("a << b = %d\n", a << b);
    printf("a >> b = %d\n", a >> b);
    printf("~c = %x\n", ~c);

    return 0;
}
```
