# 三元運算子

**此章節需要修改**

在此稍微帶過三元運算子，效果可以當作if-else，只是可以一行完成，在if-else要做的事情不多時可以使用，或者是直接回傳二分法後的值。

請參考以下範例：

```C++
#include <iostream>
#include <stdlib.h>
#include <time.h>
using namespace std;

int main(){
    srand(time(NULL));
    int point = rand()%15+3;
	cout << point << ((point > 10)? " is big":" is small");
	return 0;
}
```

用法為 `(條件)?正確做的事:錯誤做的事`
