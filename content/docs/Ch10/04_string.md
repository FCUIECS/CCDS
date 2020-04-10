# 字串

## string
接下來要介紹的是字串，在C語言中我們使用char陣列來表示字串，並使用`string.h`的函式對字串做處理，在C++中擁有string這個類別，意味著能夠比C語言更方便的使用字串。考慮到同學們還未學習物件導向，所以只先教導同學如何使用，若想學習物件導向請另找資源。

**請切記要#include<string>**

請執行以下範例

```C++
#include <iostream>
#include <string>
using namespace std;
int main(){
	string str1("I am string no.1");
	cout << "The string \"" << str1 << "\"'s size is " << str1.size() << endl;
	return 0;
}
```

使用string時程式會自動開放空間存入，並不像char陣列一樣還要手動配置空間。`str1.size()`為C++的寫法，意義為**請str1告訴我他的長度**，在C語言要查詢string長度必須寫`strlen(str1)`，是使用`strlen()`查詢str1的長度，雖說結果相同，但寫法、內部結構和意義上卻是大相逕庭。

當然，在實務上我們更常讓使用者輸入姓名等等資料，那就有別於上個範例的直接賦予值，在C++中讓使用者輸入我們使用`cin`加上`>>`，如以下範例所示。

```C++
#include <iostream>
#include <string>
using namespace std;

int main(){
	string userName;
    cout << "Please input your name:";
	cin >> userName;
	cout << "your name is " << userName << endl;
	if(userName=="Wang"){
        cout << "What a good name !!!" << endl;
	}
	return 0;
}
```

從這個範例中使用者若輸入`Wang`將會印出`What a good name !!!`，仔細看if的小括號內寫的是`userName=="Wang"`，這是因為string這個類別有定義屬於他的`==`，所以可以直接使用此種寫法，若是使用其他類別請先閱讀文件、查找資料或者做過嘗試後再使用。

string有很多功能可以使用，但本課程為教學資料結構，所以其餘功能請讀者自行查找資料嘗試。

## 複習：副程式(function)
常常我們會持續地做同一事情，但這件事情由多行程式碼組成，這時候我們就需要用到副程式的概念，請參考下列兩種程式碼：

```C++
#include <iostream>
#include <math.h>
using namespace std;

int main(){
	cout << "3,4  : " << sqrt(3*3+4*4) << endl;
	cout << "5,12 : " << sqrt(5*5+12*12) << endl;
  cout << "8,15 : " << sqrt(8*8+15*15) << endl;
	return 0;
}
```

```C++
#include <iostream>
#include <math.h>
using namespace std;

float getHypotenuse(int a,int b){
    return sqrt(a*a+b*b);
}
int main(){
	cout << "3,4  : " << getHypotenuse(3,4) << endl;
	cout << "5,12 : " << getHypotenuse(5,12) << endl;
  cout << "8,15 : " << getHypotenuse(8,15) << endl;
	return 0;
}
```

看似是第二段程式碼多了一些東西，但是你可以想像，假設今天你要做的這件事需要十行甚至更多程式碼，但是你突然發現了錯誤，那麼就需要砍掉這些程式碼重寫，那麼可能就會砍到其他程式碼。如果把它包成一個function，你會更方便做管理與除錯。

副程式的架構為　回傳型態 副程式名稱(參數型態 參數名稱...){要做的事}

若沒有需要回傳的東西則寫`void`，副程式為一個大章節，請同學自己多做練習。

## 補充：類別與物件
在此以最簡易的方式說明

類別與物件的關係，可以想像成型態與變數，類別和型態都是用來概括一個類型，物件和變數才是真正會占用記憶體空間的資料。

`int num`，int是型態，num是變數。`string str1;`，string是類別，str1是物件。
物件可以自己做事，但是變數只能被使用，更詳細的請參考物件導向設計。
