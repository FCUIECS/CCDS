# 輸入與輸出

## 輸出(cout)
如同C語言中會有的 `#include <stdio.h> …　return 0;` ，等等必定會寫的內容一樣，以下是C++的基礎架構：

### 範例10-1
```c++
#include <iostream>
int main(){
	std::cout << "Hello World!" << std::endl;
	return 0;
}
```

以上為程式入門的`Hello World!`程式 從上述程式可以看到其實與C的架構相似，不同的只有`#include <iostream>`和`std::cout << ...`的部分。

在C++中，輸出字元會使用`std::cout`而非`printf()`，他能夠判斷型態內容自行輸出，而`std::endl`的效用為換行，也許一開始在`printf()`和`std::cout`的用法上會有一些不適應，不過多練習之後很快就能習慣的。所以請先練習以下題目：

### 練習10-1
請使用`std::cout`輸出自己的生日、姓名及電話如以下範例

	1983/01/21
	西嘉嘉
	0987666666

如果一直打`std::cout`是不是會感到厭煩？如果會，那可以參考下面的寫法。

### 範例10-2
```c++
#include <iostream>
using namespace std;
int main(){
	cout << "Hello World!" << endl;
	return 0;
}
```

在`#include <iostream>`後寫上`using namespace std;`，之後你寫上的`cout`和`endl`就不必再加上`std::`。

為什麼會這樣呢？你可以想像在`iostream`中有許多個`cout`當你只有寫上`cout`時，編譯器沒有辦法判斷是哪一個`cout`，所以你必須寫`std::cout`，編譯器才能知道你要使用的為`std`這個namespace底下的`cout`，所以在最前面加上`using namespace std;`，編譯器就會默認你的`cout`為`std`下的`cout`。

簡單來說，加上`using namespace std;`就只要寫`cout`而非`std::cout`，會方便許多。

除了直接輸出字串，也可以直接輸出整數、變數和運算式的結果，請執行範例10-3。

### 範例10-3
```c++
#include <iostream>
using namespace std;
int main(){
  int ninetyNine = 99;
  cout << "ninetyNine : " << ninetyNine << endl;
  cout << "1 : " << 1 << endl;
  cout << "ninetyNine + 1 : " << ninetyNine+1 << endl;
	return 0;
}
```

## 輸入(cin)
講輸入之前，我們要先提變數型態，我們必須決定輸入型態，才能讓程式知道使用者輸入後的文字該以什麼方式解讀。

| **型態類型** | **保留字** | **佔用空間**|
|:-----|:----|:-----|
| 字元 | char |	1 byte |
|寬字元|wchar_t|2 bytes|
|整數|short|2 bytes|
|整數|int|4 bytes|
|整數|long|4 bytes|
|浮點數|float|4 bytes|
|浮點數|double|8 bytes|
|浮點數|long double|12或16 bytes|
|布林|bool|1 byte|

在練習時比較常用到的是char,int,float,double和bool這幾個型態，前四項於C語言時已經充分學習，布林將於下一小節進行說明。另外，在C語言時字串使用char陣列儲存，在C++使用string物件儲存，將於本章第四節進行說明，在此先講解C++的輸入。

### 範例10-4
```c++
#include <iostream>
using namespace std;
int main(){
  int num;
  cout << "Please input \"num\": ";
  cin >> num;
  cout << "the \"num\" is " << num << endl;
	return 0;
}
```
### 練習10-4
請參考範例10-4，讓使用者輸入小數並該小數印出。

## 複習：if-else與switch-case
我們的程式經常會辨別使用者的輸入而產生不同的輸出，現在我們將練習兩種流程控制，if-else與switch-case。現在我們讓使用者輸入他的身高，若大於180則印出basketball，若大於165則印出baseball，若低於165則印出table tennis，請參考範例10-5：
### 範例10-5
```c++
#include <iostream>
using namespace std;
int main(){
	int height;
	cout << "Please input your height:";
	cin >> height;
	if(height > 180){
		cout << "baskeball" << endl;
	}else if(height > 165){
		cout << "baseball" << endl;
	}else{
		cout << "table tennis" << endl;
	}
}
```
### 練習10-5
請參考範例10-5畫出其程式流程

除了if-else之外，若同時有多個分支需要判斷，我們可以使用switch-case，請參考範例10-6：
### 範例10-6
```c++
#include <iostream>
using namespace std;
int main(){
	char num;
	cout << "Please input num:";
	cin >> num;
	switch (num) {
		case '1':
			cout << "case 1" << endl;
			break;
		case '2':
			cout << "case 2" << endl;
			break;
		case '3':
			cout << "case 3";
			break;
		default:
			cout << "is not 1,2,3"
			break;
	}
}
```
要注意的是，每個case後要放上`break;`，沒加會發生什麼事各位同學可以自行嘗試。而`case '1'`中`1`要加上單引號是因為表示為char型態，若要使其表示為整數型態則不需要加上單引號。
### 練習10-6
請修改範例10-6，將num改為整數型態並使程式正確執行。

### 總練習
請模擬一次性販賣機，讓使用者輸入投幣數量，並選擇a~d四種產品，若能夠購買則顯示購買成功，若錢不夠則顯示購買失敗，販賣機商品及價錢請參考下表。

| **商品代號** | **價錢** |
|:-----:|:----:|
|a|10|
|b|50|
|c|100|
|d|87|

例子1

	請投入金額：50
	a:10
	b:50
	c:100
	d:87
	請輸入商品代號：a
	商品a購買成功

例子2

	請投入金額：50
	a:10
	b:50
	c:100
	d:87
	請輸入商品代號：d
	商品d購買失敗
