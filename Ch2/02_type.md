# 基礎五型
C語言之中，型態是所有資料儲存的基本，想要儲存資料，得先分清楚型態是什麼，也因此在輸出之後，緊接而來的就是「型態」。  
我們可以透過宣告某個型態的「變數」，來儲存該類型的「資料」，而C語言的型態共有五種，分別是int、float、double、char以及void，以下就分別介紹他們。

## int
int，全文是integer，也就是我們中文所說的「整數」，舉凡0、1這類沒有特殊符號的數字，都可以用int來儲存。  
在C語言中，一個int變數就是占用 4 bytes 的記憶體空間，換言之，它所能保存的數值範圍只有 2147483647 ~ -2147483648。  
{%ace edit=false, lang='c_cpp', theme='monokai'%}
int a = 1;
int b = -1;
int c = 2147483647;
int d = -2147483647;
{%endace%}

> **INT 的儲存範圍定義在 limits.h 中，會根據系統及函式庫實作上而有所差別，基準值為 2147483647(or greater) ~ -2147483647(or less)git p**

而輸出時，我們要使用一些方式來讓printf()認得這小祖宗是整數(int)：
{%ace edit=false, lang='c_cpp', theme='monokai'%}
printf("%d\n", num);
{%endace%}

然而，光一個整數就有許許多多不同的表達方式，例如：八進位、十六進位等等，因此簡單列了個表格說明：

|  格式控制字元 |          意義           |
|:-----------:|:-----------------------|
| %d          | 輸出有號整數             |
| %o          | 輸出無號八進位整數        |
| %x          | 輸出無號十六進位整數(小寫) |
| %X          | 輸出無號十六進位整數(大寫) |

{%ace edit=false, lang='c_cpp', theme='monokai'%}
printf("%d\n", 10); // 10
printf("%o\n", 10); // 12
printf("%x\n", 10); // a
printf("%X\n", 10); // A
{%endace%}

因此一個整數就可以有四種輸出變化，不過要特別注意的是，轉換輸出成八進位及十六進位是沒有正負號的。

## float
float，中文稱為「浮點數」，用比較耳熟能詳的單字就是「小數」，負責去儲存0.1、-1.2、0.0這種帶有小數點的數字。  
在C語言中，float是一個單精度浮點數，一個float變數就是占用 4 bytes 的記憶體空間，通常小數點後六位之後的問算都可能會有誤差。  
{%ace edit=false, lang='c_cpp', theme='monokai'%}
float a = 0.1;
float b = -1.2;
float c = 0.0;
{%endace%}

那要輸出一個浮點數相對於整數就簡單多了，你只需要：

{%ace edit=false, lang='c_cpp', theme='monokai'%}
printf("%f\n", num);
{%endace%}

不過，如果你是指數愛好者，或許你會比較喜歡以科學記號方式來顯示：  
{%ace edit=false, lang='c_cpp', theme='monokai'%}
printf("%e\n", num);
printf("%E\n", num);
printf("%g\n", num);
printf("%G\n", num);
{%endace%}
%e 及 %E 的差別在於英文字母 E 的大小寫，而 %g 和 %G 則分別是取 %e 及 %E 和 %f 較短的那個。  

## double
double，中文稱為「倍精度浮點數」，簡單來說，double也是拿來儲存小數的型態，只不過可以存的比較精準。  
在C語言中，一個 double 變數就是占用 8 bytes 的記憶體空間，通常小數點後15位之後的問算都可能會有誤差。  

{%ace edit=false, lang='c_cpp', theme='monokai'%}
double a = 0.1;
double b = -1.2;
double c = 0.0;
{%endace%}

要輸出一個double變數跟輸出float很類似，只要加個符號就好：  

{%ace edit=false, lang='c_cpp', theme='monokai'%}
printf("%lf\n", num);
{%endace%}

## char
char，全文是character，中文稱為「字元」，可以儲存ASCII表上所有的字元，其中就包括了所有的標點符號、英文字母及數字。  
在C語言中，一個char只占用了 1 byte 的記憶體空間，不過實際上使用的只有 7 bits，換言之，真正儲存範圍只有 -127 ~ 127。  
在定義字元的時候，我們可以用單引號(')將字母或標點符號夾住來表示該字元，或者是用對應的ASCII碼。  
{%ace edit=false, lang='c_cpp', theme='monokai'%}
char ch  = 'A';
char ch2 = 65;
{%endace%}
在廣義上，char屬於整數家族的一員，因此 char 跟 int 在數值不大的狀況下可以直接進行轉換。  
而要輸出一個字元，我們可以簡單的使用：
{%ace edit=false, lang='c_cpp', theme='monokai'%}
printf("%c", ch);
{%endace%}

另外，值得一提的是，我們先前所提到的格式控制字元，全部都是char所可以儲存的。

## void
void，中文稱為「空」、「虛無」，是整個C語言中最特別的型態，因為 void 變數不能儲存任何資料。  
基本上，當你定義了 void 變數的時候，就會得到一個錯誤。  
不過，void 在別的地方確有其意義，我們在未來的副函式及指標章節，會有額外的介紹。  

## 練習
請試著宣告變數，儲存以下資料：
- 1
- -10
- 48
- 99.5
- 99.555555555
- '0'
- '\a'
