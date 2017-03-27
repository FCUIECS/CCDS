# 字串

在大部分語言中，字串會使用string類別儲存，在C語言中則是用`char陣列`表示，再使用`printf("%s",string);`印出，請參考範例5-1

## 字串IO

### 範例5-1

{%ace edit=false, lang='c_cpp', theme='monokai'%}
#include <stdio.h>
#include <stdlib.h>

int main(){
    unsigned char str[11] = "HelloWorld";
    printf("%s",str);
	return 0;
}
{%endace%}

`HelloWorld`中有十個字元，而字串有終止字元(`'\0'`)，所以我們必須大小宣告為11才能完整的放入`HelloWorld`。

### 練習5-1
> 請參考範例5-1將str陣列大小改變看會有什麼結果

使用`printf("%s",str);`進行字串輸出，使用`scanf("%s",str);`進行字串輸入，要注意此時`str`沒有加上`&`，請參考範例5-2

### 範例5-2

{%ace edit=false, lang='c_cpp', theme='monokai'%}
#include <stdio.h>
#include <stdlib.h>

int main(){
    char str[100];
    printf("please input:");
    scanf("%s",str);
    printf("your input:%s\n",str);
	return 0;
}
{%endace%}

請注意，`scanf("%s",str);`，**沒有加&**，原因與指標有關，將於之後更詳細說明。

### 練習5-2
> 請使用範例5-2，請嘗試使用各種輸入並觀看其結果。

**注意：輸入' '時只會將前半段讀入**，在`scanf()`中' '也是終止的字元之一，若要避免此情況可以使用`scanf("%[^\n]",s);`，`scanf()`還有很多特殊寫法，但因為不常用到故不再多做敘述。

中文字佔兩個Bytes，我們可以將`char`以十六進位的方式印出用以表示，請參考範例5-3。

### 範例5-3

{%ace edit=false, lang='c_cpp', theme='monokai'%}
#include <stdio.h>
#include <stdlib.h>

int main(){
    unsigned char str1[3] = "逢",str2[3];
    printf("%s\n",str1);
    printf("%X,%X\n\n",str1[0],str1[1]);

    str2[0]=0xB3;
    str2[1]=0x7B;
    str2[2]='\0';
    printf("%s\n",str2);

	return 0;
}
{%endace%}

由範例5-3可以得知，"逢"字由0xB3和0x7B組成，我們從str2直接存值進入，再以字串形式印出，也的確是同一個字，`'\0'`則是終止符號，當讀到此字元時停止印出。

### 練習5-3
> 請設計一個程式證明printf()讀到'\0'時停止。

## function使用

引入`string.h`後有許多方便的函式可以使用，詳細可以查官方文件。以下將會介紹幾個function的範例，若有疑慮可以於網路上搜尋更多範例。

### strlen

{%ace edit=false, lang='c_cpp', theme='monokai'%}
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
int main(){
    char str[100];
    int len;
    printf("please input any string:");
    scanf("%s",str);
    len = strlen(str);
    printf("\"%s\"\'s size is %d",str,len);
	return 0;
}
{%endace%}

strlen會回傳字串的長度，藉由範例可以多多嘗試。

### strcpy

{%ace edit=false, lang='c_cpp', theme='monokai'%}#include <stdio.h>
#include <stdlib.h>
#include <string.h>
int main(){
    char str[100],str2[100];
    int len;
    printf("please input any string in str2:");
    scanf("%s",str2);
    strcpy(str,str2);
    printf("after strcpy\(str,str2\)\nstr:\"%s\"\n",str);
	return 0;
}
{%endace%}

strcpy會讓str的資料等於str2的資料，並非直接寫`str = str2;`，後者使str2和str存取同一個陣列，而非複製出另一個相同的字串。

### strcat

{%ace edit=false, lang='c_cpp', theme='monokai'%}
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
int main(){
    char str[100],str2[100];
    int len;
    printf("please input any string1:");
    scanf("%s",str);
    printf("please input any string2:");
    scanf("%s",str2);
    strcat(str,str2);
    printf("after strcat\(str,str2\)\n str:\"%s\"\n",str);
	return 0;
}
{%endace%}

strcat將str的尾端接上str2。

### strstr

{%ace edit=false, lang='c_cpp', theme='monokai'%}
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
int main(){
    char str[] = "the git book is very convenience.";
    char str2[]= "book";
    char* temp;
    printf("str:\"%s\"\n",str);
    printf("str2:\"%s\"\n",str2);
    temp = strstr(str,str2);
    printf("after temp = strstr\(str,str2\)\ntemp:\"%s\"\n",temp);
	return 0;
}
{%endace%}

strstr會在str中找到等於str2的第一個位址，並將該值回傳，有關位址和指標請詳見本書第七章。

### strcmp

{%ace edit=false, lang='c_cpp', theme='monokai'%}
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
int main(){
    char str[100];
    char str2[] = "OpenSesame";
    printf("please input the password:");
    scanf("%s",str);
    printf("the strcmp\(str,str2\) is %d\n",strcmp(str,str2));
    if(!strcmp(str,str2)){
        printf("door opening.\n");
    }else{
        printf("nothing happened.\n");
    }
	return 0;
}
{%endace%}

strcmp會讓str減str2，若大於回傳1，小於回傳-1，等於回傳0，這使得我們可以對字串進行大小比較甚至排序。

### strcmp練習
> 請宣告可以存取5個字串的陣列，讓使用者分別輸入值，接著排序後印出

### strspn

{%ace edit=false, lang='c_cpp', theme='monokai'%}
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
int main(){
    char str[100];
    char str2[] = "abcdefghijklmnopqrstuvwxyz";
    printf("str2 :%s\n",str2);
    printf("str  :");
    scanf("%s",str);
    printf("the strspn\(str,str2\) is %d\n",strspn(str,str2));
	return 0;
}
{%endace%}

strspn會回傳str有幾個字元被包含於str2，直到第一個沒有被包含的為止。
