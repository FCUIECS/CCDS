# Chapter 10 天元突破 C++ Intro
本章節將簡易用C++複習基本程式邏輯，並教導C和C++的不同之處，以便接下來資料結構相關課程的銜接，因為並非是物件導向課程，故本章節並不會注重教導物件導向的觀念。


型態為資料的儲存方式，有整數、小數和字元等等，我們直接以表格的方式觀看：



其中值得一提的是**bool**這個資料型態，在C語言中，我們可能會宣告一個**int**作為條件判斷的變數，但我們從表格中可以看到兩者佔用空間是有差的，而程式碼管理上**bool**作為條件判斷的變數也會比其他型態更為清楚明瞭。

在**bool**中提供兩個值，分別為**true**和**false**，兩者皆為c++的保留字，所以不能任意更改大小寫，請執行以下程式。

```c++
#include <iostream>
using namespace std;

int main(){
	bool flag;
	flag = ture;
	if(flag){
		cout << "The flag is ture!!!" << endl;
	}else{
		cout << "The flag is false!!!" << endl;
	}
	return 0;
}
```

###練習10-2
請使用前次範例並將`flag`的值設為`false`。

<br>
其他型態的使用和C語言大同小異，在此不再多做介紹。

接下來要介紹的是字串，在C語言中我們使用char陣列來表示字串，並使用`string.h`的函式對字串做處理，在C++中擁有string這個類別，意味著能夠比C語言更方便的使用字串。考慮到同學們還未學習物件導向，所以只先教導同學如何使用，若想學習物件導向請另找資源。

請執行以下範例

```c++
#include <iostream>
#include <string>
using namespace std;
int main(){
	string str1("I am string no.1");
	cout << "The string \"" << str1 << "\"size is " << str1.size() << endl;
	return 0;
}
```

使用string時程式會自動開放空間存入，並不像char陣列一樣還要手動配置空間。`str1.size()`為C++的寫法，意義為**請str1告訴我他的長度**，在C語言要查詢string長度必須寫`strlen(str1)`，是使用`strlen()`查詢str1的長度，雖說結果相同，但寫法、內部結構和意義上卻是大相逕庭。

當然，在實務上我們更常讓使用者輸入姓名等等資料，那就有別於上個範例的直接賦予值，在C++中讓使用者輸入我們使用`cin`加上`>>`，如以下範例所示。

```c++
#include <iostream>
#include <string>
using namespace std;

int main(){
	string userName;
  cout << "Please input your name:" << endl;
	cin >> userName;
	cout << "your name is " << userName << endl;
	return 0;
}
```
