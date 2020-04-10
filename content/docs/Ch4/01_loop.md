# 迴圈

有時候我們需要讓程式重複做某一件事情，我們可以藉由兩種方法做到，一是迴圈，二是遞迴，因為遞迴太過麻煩且不易使用所以在此不做贅述，留待未來。

在C++中使用迴圈和C語言相同，使用while及for。

## while
`while`使用方式為，小括號內為**繼續執行條件**，大括號為執行動作。

假設我們想讓使用者持續輸入數字，並使這些數字相加，當總和大於100時結束，請參考範例10-8：
### 範例 4-1

```C++
#include <stdio.h>
#include <stdlib.h>

int main(){
	int sum = 0,num;
	while(sum <= 100){
        printf("please input a number to sum:");
        scanf("%d",&num);
        sum = sum + num;
        printf("The \"sum\" is %d\n",sum);
	}
	return 0;
}
```

### 練習4-1
> 請參考範例10-8，使用While 改為讓使用者輸入5次數字後印出數字總和並結束程式。

一般迴圈我們都會做三件事情，設定條件變數、設立終止條件、更改條件變數，以範例10-8為例子：
<br>設定條件變數：int sum = 0;
<br>設立繼續條件：sum <= 100
<br>更改條件變數：sum = sum + num;

我們更常會遇到的是如同練習10-8的狀況，條件變數是持續+1，所以我們就有了`for`的使用。

## for
`for`的使用方式為，小括號內依序放入條件變數設定、繼續條件設立、條件變數更改，並用`;`隔開，大括號內為執行動作。

範例10-9為顯示2的九九乘法表

### 範例4-2

```C++
#include <stdio.h>
#include <stdlib.h>

int main(){
    int i;
	for(i=1;i<10;i++){
        printf("2*%d=%2d\n",i,2*i);
	}
	return 0;
}
```

### 練習4-2
> 請利用雙層迴圈(for)印出完整的九九乘法表，並排版。

## do-while
do-while的意義為不論如何都先做一次迴圈內的事情，再進行while迴圈，但個人經常失誤，所以不推薦使用，請參考範例4-3

### 範例4-3

```C++
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main(){
    int flag=0,user,prog;
    srand(time(NULL));
	do{
        printf("please input your hand(3>2,2>1,1>3):");
        scanf("%d",&user);
        prog = rand()%3+1;
        if( (prog-user == -2)||(prog-user == 1) ){
            printf("program: %d\n",prog);
            printf("you    : %d\n",user);
            printf("you lose\n");
        }else if( (user-prog == -2)||(user-prog == 1) ){
            printf("program: %d\n",prog);
            printf("you    : %d\n",user);
            printf("you win\n");
            flag = 1;
        }else{
            printf("program: %d\n",prog);
            printf("you    : %d\n",user);
            printf("draw\n");
        }
        printf("\n");
	}while(flag==0);

	return 0;
}
```

以上程式不容易看出`do-while`的效果，但有其他可以講的概念。`srand()`為亂數種子，是為了讓亂數依據一個方式變動的函式，`rand()`會產生出極大的隨機亂數，使用`%`即可以控制他的範圍。flag(旗標)是我們常常拿來做流程控管的方法，但旗標太多程式也會雜亂，所以不推薦使用太多，程式底層會常常使用到旗標的概念。

### 練習4-3
> 請思考有什麼情況使用do-while比while好

## break
### 範例4-4

```C++
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main(){
    int user,prog;
    srand(time(NULL));
	while(1){
        printf("please input your hand(3>2,2>1,1>3):");
        scanf("%d",&user);
        prog = rand()%3+1;
        if( (prog-user == -2)||(prog-user == 1) ){
            printf("program: %d\n",prog);
            printf("you    : %d\n",user);
            printf("you lose\n");
        }else if( (user-prog == -2)||(user-prog == 1) ){
            printf("program: %d\n",prog);
            printf("you    : %d\n",user);
            printf("you win\n");
            break;
        }else{
            printf("program: %d\n",prog);
            printf("you    : %d\n",user);
            printf("draw\n");
        }
        printf("\n");
	}

	return 0;
}
```

範例4-4和範例4-3一樣，皆為猜拳的程式，但4-4使用了無限迴圈，並使用`break`跳出迴圈代替旗標的功能。
範例4-5會介紹`continue`的用法。


## continue
### 範例4-5

```C++
#include <stdio.h>
#include <stdlib.h>

int main(){
    int i;
    for(i=0;i<100;i++){
        printf("%d:",i);
        if(i%5 == 0){
            printf("i am 5\n");
            continue;
        }
        printf("i am not 5\n");
    }
	return 0;
}
```

`continue`的意義為馬上重新執行迴圈，有別於`break`的跳出迴圈。

## 練習
> 請讓使用者輸入高度，印出三角形，字元不限，如下所示
input:3
<br>--@--
<br>-@@@-
<br>@@@@@
