# Chapter 9：剪紙成兵 File I/O
## 檔案處理

C本身提供了許多檔案的輸入與輸出，以方便使用者設計與檔案有關的系統函數。

其中包含了開檔、讀檔以及寫檔...等

簡單來說有以下這些

| 函數名稱  | 功能說明 |
|-------|------|
|fopen( )|開啟一個檔案|
|fclose( )|關閉一個檔案|
|putc( )|輸出一個字元到檔案|
|getc( )|從某一個檔案讀取一個字元|
|fprintf( )|輸出資料至某檔案|
|fscanf( )|從某檔案讀取資料|
|feof( )|測試是否到了檔案結束位置|
|ferror( )|測試檔案操作是否正常|
|fseek( )|設定準備讀取檔案資料的位置|
|rewind( )|將準備讀取檔案資料位置，設定在檔案起始位置|
|remove( )|檔案的刪除|


## 開檔

### fopen( ) 用於開啟檔案,檔案在使用前是需先經過開啟動作的

使用格式如下

### **FILE  \*fopen(char  \*filename, char  \*mode);**


各項資料的定義如下所示：
 
1. filename：檔案指標，指的是欲開啟的檔案名稱。
2. mode：檔案使用模式，指的是檔案被開啟之後，它的使用方式。
 
下面是檔案開啟之後，一般常使用的方式：

| 函數名稱  | 功能說明 |
|-------|------|
|"r"|開啟一個文字檔(text)，供程式讀取。|
|"w"|開啟一個文字檔(text)，供程式將資料寫入此檔案內。如果磁碟內不包含這個檔案，則系統會自行建立這個檔案。如果磁碟內包含這個檔案，則此檔案內容會被蓋過而消失。|
|"a"|開啟一個文字檔(text)，供程式將資料寫入此檔案的末端。如果此檔案不存在，則系統會自行建立此檔案。|
|"rb"|開啟一個二元檔(binary)，供程式讀取。|
|"wb"|開啟一個二元檔，供程式將資料寫入此檔案內。如果磁碟內不包含這個檔案，則系統會自行建立這個檔案。如果磁碟內包含這個檔案，此檔案內容會被蓋過而消失。|
|"ab"|開啟一個二元檔(binary)，供程式將資料寫入此檔案末端，如果此檔案不存在，則系統會自行建立此檔案。|


## 關檔

### fclose( ) 用於關閉檔案,如果fclose( )執行失敗，它的傳回值是非零值

在C語言中關閉檔案主要有兩個目的：
1. 檔案在關閉前會將檔案緩衝區資料寫入磁碟檔案內，否則檔案緩衝區資料會遺失。
2. 一個Ｃ語言程式，在同一時間可開啟的檔案數量有限，一般是20個，如果你的程式很大，要開啟超過20個檔案時，你必須將暫時不用的檔案關閉。
 
## 寫檔

###  fprintf( ) 主要目的是供你將資料，以格式化方式寫入某檔案內

使用格式如下

### **fprintf( fp ,  "……" , ………);**

此函數控制列印區和列印和列印變數區的使用,格式和printf( )使用格式相同. fprintf( )和printf( )兩者唯一的差別是，printf( )會將資料列印在螢幕上，而fprintf( )會將資料列印在某個檔案內。

範例:
```C
#include <stdio.h>

int main()
{
    FILE *fp;
    int  var,i;
    int  sum = 0;
    float average;
    fp = fopen("data1.txt","w");     /* open file pointer */

    for ( i = 0; i < 5; i++ )
    {
       printf("\1: input number %d here ==>  ",i+1);
       scanf("%d",&var);
       sum += var;
       fprintf(fp,"%d\n",var);
    }
    average = (float) sum / 5.0;
    fprintf(fp,"\2: The average is %6.2f",average);
    fclose(fp);
    
    return 0; 
}
```

## 讀檔

### fscanf( ) 主要的目的是讓我們從某個檔案讀取資料

使用格式如下

### **fscanf( fp ,  "……" , ………);**

fscanf( )函數和scanf( )函數兩者之間最大的差別在，scanf( )函數主要用於從鍵盤輸入讀取資料，fscanf( )函數則是從fp檔案指標所指的檔案讀取資料。

範例:
```C
#include <stdio.h>

int main()
{
    FILE *fp;
    int i,var;
    fp = fopen("data1.txt","r");     /* open file pointer */

    for ( i = 0; i < 5; i++ )
    {
         fscanf(fp,"%d",&var);
         printf("%d\n",var);
    }
    fclose(fp);
    return 0;
}
```

## 補充

### putc( ) 主要功能是將一個字元寫入某檔案內，
使用格式:
**int putc( int ch, FILE \*fp );**

此函數如果執行成功，它的傳回值是ch字元值，如果執行失敗，它的傳回值是EOF。且上述格式中，ch代表所欲輸出的字元，fp則是檔案指標。
下列為一個簡單建立一個檔案的程式應用。

```C
/* putc example: alphabet writer */
#include <stdio.h>

int main ()
{
  FILE * pFile;
  char c;

  pFile=fopen("alphabet.txt","wt");
  for (c = 'A' ; c <= 'Z' ; c++) {
    putc (c , pFile);
    }
  fclose (pFile);
  return 0;
}
```

### getc( ) 主要目的是某一個檔案中，讀取一個字元。

使用格式:

**int  getc(FILE  \*fp);**
 
 
當執行getc( )函數成功時，傳回值是所讀取的字元，如果所讀取的是檔案結束字元，則此值是EOF，在stdio.h內，此值是 -1。
