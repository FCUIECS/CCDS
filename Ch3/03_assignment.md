# 指派運算

指派這個概念其實其實相當的簡單，大家其實也已經知道甚至在使用了，最基本的指派運算子其實就是"="。

等於可以幫助我們來將右邊的值給左邊的變數資料，但是其實等於可以跟更多的運算子合用。會直接進行運算並存回左邊變數資料，如下。

## 指派運算子

<table class="tg">
  <tr>
    <th class="tg-baqh">運算子</th>
    <th class="tg-yw4l">意義</th>
    <th class="tg-yw4l">舉例</th>
  </tr>
  <tr>
    <td class="tg-yw4l">=</td>
    <td class="tg-yw4l">指派</td>
    <td class="tg-yw4l">A = B</td>
  </tr>
  <tr>
    <td class="tg-yw4l">+=</td>
    <td class="tg-yw4l">相加並指派</td>
    <td class="tg-yw4l">A += B</td>
  </tr>
  <tr>
    <td class="tg-yw4l">-=</td>
    <td class="tg-yw4l">相減並指派</td>
    <td class="tg-yw4l">A -= B</td>
  </tr>
  <tr>
    <td class="tg-yw4l">*=</td>
    <td class="tg-yw4l">相減並指派</td>
    <td class="tg-yw4l">A *= B</td>
  </tr>
  <tr>
    <td class="tg-yw4l">/=</td>
    <td class="tg-yw4l">相除並指派</td>
    <td class="tg-yw4l">A /= B</td>
  </tr>
  <tr>
    <td class="tg-yw4l">%=</td>
    <td class="tg-yw4l">取餘數並指派</td>
    <td class="tg-yw4l">A %= B</td>
  </tr>
  <tr>
    <td class="tg-yw4l">&amp;=</td>
    <td class="tg-yw4l">且(and)並指派</td>
    <td class="tg-yw4l">A &amp;= B</td>
  </tr>
  <tr>
    <td class="tg-yw4l">|=</td>
    <td class="tg-yw4l">或(or)並指派</td>
    <td class="tg-yw4l">A |= B</td>
  </tr>
  <tr>
    <td class="tg-yw4l">^=</td>
    <td class="tg-yw4l">互斥或(xor)並指派</td>
    <td class="tg-yw4l">A ^= B</td>
  </tr>
  <tr>
    <td class="tg-yw4l">&lt;&lt;=</td>
    <td class="tg-yw4l">位元向左位移並指派</td>
    <td class="tg-yw4l">A &lt;&lt;= B</td>
  </tr>
  <tr>
    <td class="tg-yw4l">&gt;&gt;=</td>
    <td class="tg-yw4l">位元向右位移並指派</td>
    <td class="tg-yw4l">A &gt;&gt;= B</td>
  </tr>
</table>

上述就是在指派的運算子部分，而在這邊我們利用一些較簡單的例子帶過，我相信大家應該可以可以理解以下程式內容，其餘指派運算子算法其實相同於案例就不在多加描述。

```c++
#include <stdio.h>
int main(){
    int a = 5;
    int b = 2;

    printf("a += b = %d\n", a += b);
    printf("a -= b = %d\n", a -= b);
    printf("a *= b = %d\n", a *= b);
    printf("a /= b = %d\n", a /= b);
    printf("a %%= b = %d\n", a %= b);

    return 0;
}
```
