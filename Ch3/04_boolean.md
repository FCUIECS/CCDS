# 布林運算

> C 語言中並沒有布林*!*

## 布林運算

在這邊有個很重要的觀念要告訴大家，其實在C 語言中並沒有布林這型態，一定有很多同學在這邊會有疑問，那這章節是不是有寫錯了？，但其實這是一個 C 的重要觀念。

> **非零即為真**。

希望大家對於這項觀念有一定的基本概念，那既然如此本章到底要講些什麼。
其實本章節主要是要教大家關係以及邏輯運算，因為在撰寫程式的過程中必然會遇到許多時候，我們會使用關係以及邏輯運算做為判斷的基準。所以這兩部份將會在下面進行詳細介紹。


## 關係運算子

C 語言中的關係運算子都是二元運算子，所以也就是代表需要有兩個運算元來進行運算，而在關係運算子的回傳部分將會以 0 為假，1 為真。其中各項運算子包含

<table class="tg">
  <tr>
    <th class="tg-yw4l">運算子</th>
    <th class="tg-yw4l">意義</th>
    <th class="tg-yw4l">舉例</th>
  </tr>
  <tr>
    <td class="tg-yw4l">&lt;</td>
    <td class="tg-yw4l">小於</td>
    <td class="tg-yw4l">A &lt; B</td>
  </tr>
  <tr>
    <td class="tg-yw4l">&lt;=</td>
    <td class="tg-yw4l">小於等於</td>
    <td class="tg-yw4l">A &lt;= B</td>
  </tr>
  <tr>
    <td class="tg-yw4l">&gt;</td>
    <td class="tg-yw4l">大於</td>
    <td class="tg-yw4l">A &gt; B</td>
  </tr>
  <tr>
    <td class="tg-yw4l">&gt;=</td>
    <td class="tg-yw4l">大於等於</td>
    <td class="tg-yw4l">A &gt;= B</td>
  </tr>
  <tr>
    <td class="tg-yw4l">==</td>
    <td class="tg-yw4l">相等</td>
    <td class="tg-yw4l">A == B</td>
  </tr>
  <tr>
    <td class="tg-yw4l">!=</td>
    <td class="tg-yw4l">不相等</td>
    <td class="tg-yw4l">A != B</td>
  </tr>
</table>

所以今天假設有一程式內容為:

{%ace edit=false, lang='c_cpp', theme='monokai'%}
#include <stdio.h>
int main(){
    int a = 5;
    int b = 2;
    printf("%d\n", a >= b);
    return 0;
}
{%endace%}
則該程式輸出則為1，這應該是非常淺而易見的，對吧？

## 邏輯運算子
邏輯運算子在C 語言中其實並不多，僅僅只有三個運算子

<table class="tg">
  <tr>
    <th class="tg-yw4l">運算子</th>
    <th class="tg-yw4l">意義</th>
    <th class="tg-yw4l">舉例</th>
  </tr>
  <tr>
    <td class="tg-yw4l">!</td>
    <td class="tg-yw4l">非(not)</td>
    <td class="tg-yw4l">!A</td>
  </tr>
  <tr>
    <td class="tg-yw4l">&amp;&amp;</td>
    <td class="tg-yw4l">且(and)</td>
    <td class="tg-yw4l">A &amp;&amp; B</td>
  </tr>
  <tr>
    <td class="tg-yw4l">||</td>
    <td class="tg-yw4l">或(or)</td>
    <td class="tg-yw4l">A || B</td>
  </tr>
</table>

其中!則是代表A的相反，而或跟且則是像前面位元運算一樣的運作方式，就不在多進行舉例。

## 補充
> 先乘除後加減 聽過吧？

課程到了這部分其實C 語言中幾種比較常使用到的運算子都已經介紹完畢，但是還有一個在使用各項運算子時很重要的標準，也就是各個運算子的**先後順序**，就如同我們在寫算式會有先乘除後加減一般，其實在C 語言內也有類似的東西，但是它的內容更加的多元。

<style type="text/css">
.tg .tg-baqh{text-align:center;vertical-align:top}
</style>

<table class="tg">
  <tr>
    <th class="tg-yw4l">運算子</th>
    <th class="tg-yw4l">結合規則</th>
  </tr>
  <tr>
    <td class="tg-yw4l">() [] -&gt; .</td>
    <td class="tg-baqh">-&gt;</td>
  </tr>
  <tr>
    <td class="tg-yw4l">! ~ ++ -- + - * &amp; (type) sizeof</td>
    <td class="tg-baqh">&lt;-</td>
  </tr>
  <tr>
    <td class="tg-yw4l">* / %</td>
    <td class="tg-baqh">-&gt;</td>
  </tr>
  <tr>
    <td class="tg-yw4l">+ -</td>
    <td class="tg-baqh">-&gt;</td>
  </tr>
  <tr>
    <td class="tg-yw4l">&lt;&lt; &gt;&gt;</td>
    <td class="tg-baqh">-&gt;</td>
  </tr>
  <tr>
    <td class="tg-yw4l">&lt; &lt;= &gt; &gt;=</td>
    <td class="tg-baqh">-&gt;</td>
  </tr>
  <tr>
    <td class="tg-yw4l">== !=</td>
    <td class="tg-baqh">-&gt;</td>
  </tr>
  <tr>
    <td class="tg-yw4l">&amp;</td>
    <td class="tg-baqh">-&gt;</td>
  </tr>
  <tr>
    <td class="tg-yw4l">^</td>
    <td class="tg-baqh">-&gt;</td>
  </tr>
  <tr>
    <td class="tg-yw4l">|</td>
    <td class="tg-baqh">-&gt;</td>
  </tr>
  <tr>
    <td class="tg-yw4l">&amp;&amp;</td>
    <td class="tg-baqh">-&gt;</td>
  </tr>
  <tr>
    <td class="tg-yw4l">||</td>
    <td class="tg-baqh">-&gt;</td>
  </tr>
  <tr>
    <td class="tg-yw4l">？:</td>
    <td class="tg-baqh">&lt;-</td>
  </tr>
  <tr>
    <td class="tg-yw4l">= += -= /= %= &amp;=</td>
    <td class="tg-baqh">&lt;-</td>
  </tr>
  <tr>
    <td class="tg-yw4l">^= |= &lt;&lt;= &gt;&gt;=</td>
    <td class="tg-baqh">&lt;-</td>
  </tr>
  <tr>
    <td class="tg-yw4l">,</td>
    <td class="tg-baqh">-&gt;</td>
  </tr>
</table>

## 練習時間
想必大家一定看的眼花撩亂，不知道大家是否可以依據此表算出以下答案各為多少嗎？
{%ace edit=false, lang='c_cpp', theme='monokai'%}
5+2*3

4+(2-8)*45/2-5

5<<(2+2)*5-3+4

(14<<(2+1)*3+1)-5573
{%endace%}
