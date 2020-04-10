# 陣列

陣列將同一型態同一作用的變數排在一起，請參考範例4-6。

### 範例4-6

```C++
#include <stdio.h>
#include <stdlib.h>

int main(){
    int i,array[5];
    for(i=0;i<5;i++){
        printf("%d:",i);
        scanf("%d",&array[i]);
    }
    printf("\n");
    for(i=0;i<5;i++){
        printf("%d:%d\n",i,array[i]);
    }
	return 0;
}
```

我們以`int array[5]`宣告出一個變數名稱為`array`並存著五個`int`值的陣列，而陣列索引值從 **0** 開始。我們通常都會使用for迴圈將值依序瀏覽並進行操作。

範例4-7為二維陣列的作法，三維四維的作法同理可證，請自行練習

### 範例4-7

```C++
#include <stdio.h>
#include <stdlib.h>

int main(){
    int i,j,grade[5][3];
    for(i=0;i<5;i++){
        for(j=0;j<3;j++){
            printf("%d,%d:",i,j);
            scanf("%d",&grade[i][j]);
        }
    }
    printf("\n");
    while(1){
        printf("please input 0~4: ");
        scanf("%d",&i);
        if(i>-1 && i<5){
            printf("English:%d\n",grade[i][0]);
            printf("Chinese:%d\n",grade[i][1]);
            printf("ComputerScience:%d\n",grade[i][2]);
        }
    }
	return 0;
}
```

## 泡沫排序法

泡沫排序法是最容易學與最容易實作的排序法，如圖所示，假設我們要將陣列由小排到大，首先比前兩個，若前一個比較大則交換，接著比較二三個，若前面比較大則交換，直到將最大的排到最後面，在從頭進行一次排出次大的。如範例4-8。

![bubble_sort.png](/img/Ch4/bubble_sort.png)

### 範例4-8

```C++
#include <stdio.h>
#include <stdlib.h>

int main(){
    int i,j,k,temp;
    int test[5]={4,3,2,5,1};
    for(i=0;i<5-1;i++){
        for(j=0;j<5-i-1;j++){
            //see progress
            printf("\ni,j:%d,%d : ",i,j);
            for(k=0;k<5;k++){
                printf("%d ",test[k]);
            }
            //end
            if(test[j]>test[j+1]){
                temp = test[j];
                test[j] = test[j+1];
                test[j+1] = temp;
                printf("swap");
            }
        }
    }
    //see end
    printf("\nend     : ",i,j);
    for(k=0;k<5;k++){
        printf("%d ",test[k]);
    }
    //end
	return 0;
}
```

### 練習4-8
> 請參考範例4-8，改動ｉ和ｊ雙重迴圈的變數使結果依然正確

## 選擇排序法

選擇排序法直接找到最大的數的位子，將其放置正確的位置。如圖所示：

![select_sort.png](/img/Ch4/select_sort.png)

### 範例4-9

```C++
#include <stdio.h>
#include <stdlib.h>

int main(){
    int i,j,k,temp,num;
    int test[5]={4,3,2,5,1};
    for(i=4;i>-1;i--){
        //see progress
        printf("\n%d : ",5-i);
        for(k=0;k<5;k++){
            printf("%d ",test[k]);
        }
        //end
        num=0;
        for(j=0;j<i+1;j++){
            if(test[num]<test[j]){
                num=j;
            }
        }
        temp = test[num];
        test[num] = test[i];
        test[i] = temp;
    }
    //see end
    printf("\nend:");
    for(k=0;k<5;k++){
        printf("%d ",test[k]);
    }
    //end
	return 0;
}
```
