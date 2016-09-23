# 結構與物件

C++的struct有別於C語言，可以在其中放入function與constructor，不過我個人並不建議使用，若已有物件導向觀念會較推薦使用class做編寫。

以下先介紹最基礎的struct用法：

    struct 結構名稱{
        型態1 變數名稱1;
        型態2 變數名稱2;
        ...
    };

相較於C語言還要`typedef`，C++免於了這個麻煩，其餘要注意的是要記得加上分號。

### 範例10-10

{%ace edit=false, lang='c_cpp', theme='monokai'%}
#include <iostream>
using namespace std;
struct fraction{
    int son;
    unsigned int mom;
};

int main(){
    fraction a;
    a.son = 5;
    a.mom = 6;
    cout << "a:" << a.son << "/" << a.mom << endl;
    return 0;
}
{%endace%}

以上為一個分數的結構，內部有分子和分母，在設定值時必須一個一個值設定，以下為使用function的範例：

### 範例10-11

{%ace edit=false, lang='c_cpp', theme='monokai'%}
#include <iostream>
using namespace std;
struct fraction{
    int son;
    unsigned int mom;
    double toDouble(){
        double dnum = son;
        return dnum/mom;
    }
};

int main(){
    fraction a;
    a.son = 5;
    a.mom = 6;
    cout << "a:" << a.toDouble() << endl;
    return 0;
}
{%endace%}

此時的struct會有一點類別的味道，因為`a.toDouble()`就是叫`a`告訴程式他`toDouble`後的結果，並非程式對他做運算。

接下來要介紹constructor，中文為建構函式，這是當一個struct的物件(先暫時稱為物件)，被產生時會被呼叫的function，一般做為初始設定用，以下為範例：

### 範例10-12

{%ace edit=false, lang='c_cpp', theme='monokai'%}
#include <iostream>
using namespace std;
struct fraction{
    int son;
    unsigned int mom;
    double toDouble(){
        double dnum = son;
        return dnum/mom;
    }
    fraction(int s,unsigned int m){
        son = s;
        mom = (m!=0)?m:1;
    }
};

int main(){
    fraction a(5,6);
    cout << "a:" << a.toDouble() << endl;
    return 0;
}
{%endace%}

constructor寫法為寫一個不含回傳值(void也不寫)的function，且function名稱為結構名稱，剩下的部分就如同寫副程式一樣，值得一提的是，我可以在這邊預防使用者將分母設為0，防止了`toDouble()`時會發生的錯誤。

**建構函式可以有多種，請記得寫不含參數的建構函式**

而宣告時就像呼叫function一樣，只是前方多了結構名稱，寫法很容易理解，但要熟悉還需要練習，下面要提的是destructor(解構函式)，他是destructor的相反，會在物件終結時執行，寫法就是constructor前面加上`~`，請參考以下範例

### 範例10-13

{%ace edit=false, lang='c_cpp', theme='monokai'%}
#include <iostream>
#include <stdlib.h>
using namespace std;
struct fraction{
    int son;
    unsigned int mom;
    double toDouble(){
        double dnum = son;
        return dnum/mom;
    }
    fraction(int s,unsigned int m){
        son = s;
        mom = (m!=0)?m:1;
    }
    ~fraction(){
        cout << "the fraction dead.";
    }
};

int main(){
    fraction a(5,6);
    cout << "a:" << a.toDouble() << endl;
    system("pause");
    return 0;
}
{%endace%}

在未來如果在結構中用到動態記憶體配置，請記得在解構的時候將其free掉。

**struct 與 class 相當相像，但請千萬不要搞混**

## 複習：陣列(Array)
陣列是一種資料結構，一般搭配迴圈使用，舉個最簡單的例子，我要印出座號1~10號的成績：
### 範例10-14

{%ace edit=false, lang='c_cpp', theme='monokai'%}
#include <iostream>
#include <stdlib.h>
using namespace std;
int main(){
    int grade[10] = {12,54,75,24,8,97,45,32,58,60};
    for(int i=0;i<10;i++){
        cout << "座號" << i+1 << "的成績: " << grade[i] << endl;
    }
    return 0;
}
{%endace%}

陣列的第一個位子為0。

**陣列很重要，陣列很重要，陣列很重要**

C++中struct陣列的其中一種寫法，另一種寫法將於下一節介紹，請參考以下範例：
### 範例10-15

{%ace edit=false, lang='c_cpp', theme='monokai'%}
#include <iostream>
#include <stdlib.h>
using namespace std;
struct fraction{
    int son;
    unsigned int mom;
    double toDouble(){
        double dnum = son;
        return dnum/mom;
    }
    fraction(){}
    fraction(int s,unsigned int m){
        son = s;
        mom = (m!=0)?m:1;
    }
    ~fraction(){
    }
};
int main(){
    fraction a[5];
    for(int i=0;i<5;i++){
        a[i] = {5+i,6+i};
        cout << "a[" << i << "]: " << a[i].toDouble() << endl;
    }
    return 0;
}
{%endace%}

### 總練習
請更改第三節的總練習，並閱讀以下題目：
請模擬販賣機，讓使用者輸入投幣數量，並選擇a~d四種產品，若能夠購買則顯示購買成功該樣商品名稱並顯示退幣，若錢不夠則顯示購買失敗，如果輸入錯誤的代號則請使用者重新輸入，販賣機商品及價錢請參考下表。

| **商品代號** | **商品名稱** | **價錢** |
|:-----:|:----:|:----:|
|a|Atom|10|
|b|World|50|
|c|God|100|
|d|human|87|

請定義一個結構含有 編號、商品名稱、商品價格，使用陣列存取此結構物件。使用至少一個副程式(function)。


例子1

    請投入金額：50
    a:10
    b:50
    c:100
    d:87
    請輸入商品代號：a
    Atom購買成功，退幣0元

    請投入金額：50
    a:10
    b:50
    c:100
    d:87
    請輸入商品代號：d
    human購買失敗

    請投入金額：100
    a:10
    b:50
    c:100
    d:87
    請輸入商品代號：d
    human購買成功，退幣13元

    請投入金額：100
    a:10
    b:50
    c:100
    d:87
    請輸入商品代號：e
    請輸入商品代號：e
    請輸入商品代號：a
    Atom購買成功，退幣90元
