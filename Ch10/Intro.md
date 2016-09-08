#Chapter 10 天元突破 C++ Intro

本章節將教導C和C++的不同之處，以便接下來資料結構相關課程的銜接，因為並非是物件導向課程，故本章節並不會教導物件導向的觀念。

##一、起手式

就如同C語言中會有的 `#include <stdio.h> …　return 0;` ，等等必定會寫的內容一樣，以下是C++的基礎架構：

```

	#include <iostream>
	int main(){
		std::cout << "Hello World!" << std::endl;
		return 0;
	}
```

以上為一個最基礎的`Hello World!`程式 從上述程式可以看到其實與C的架構相似，不同的只有`#include <iostream>`和`std::cout << ...`的部分。

在C++中，輸出字元會使用`std::cout`而非`printf()`，他能夠判斷型態內容自行輸出，而`std::endl`的效用為換行，也許一開始在`printf()`和`std::cout`的用法上會有一些不適應，不過多練習之後很快就能習慣的。所以請先練習以下題目：

###練習10-1
請使用`std::cout`輸出自己的生日、姓名及電話如以下範例

	1983/01/21
	西嘉嘉
	0987666666
<br>
如果一直打`std::cout`是不是會感到厭煩？如果會，那可以參考下面的寫法。

```

	#include <iostream>
	using namespace std;

	int main(){
		cout << "Hello World!" << endl;
		return 0;
	}
```


在`#include <iostream>`後寫上`using namespace std;`，之後你寫上的`cout`和`endl`就不必再加上`std::`。

為什麼會這樣呢？你可以想像在iostream中有許多個`cout`當你只有寫上`cout`時，編譯器沒有辦法判斷是哪一個`cout`，所以你必須寫`std::cout`，編譯器才能知道你要使用的為`std`這個namespace底下的`cout`，所以在最前面加上`using namespace std;`，編譯器就會默認你的`cout`為`std`下的`cout`。

簡單來說，加上`using namespace std;`就只要寫`cout`而非`std::cout`，會方便許多。


##二、型態與字串

型態為資料的儲存方式，有整數、小數和字元等等，我們直接以表格的方式觀看：

**型態類型**	**保留字**	**佔用空間** <br>
字元	    char	1 byte <br>
寬字元	wchar_t	2 bytes <br>
整數	    short	2 bytes <br>
整數	    int	    4 bytes <br>
整數	    long	4 bytes <br>
浮點數	float	4 bytes <br>
浮點數	double	8 bytes <br>
浮點數	long double	12 or 16 bytes <br>
布林	    bool	1 byte <br>

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
