# Chapter 6：三千世界 Functions

中文：副程式、副函式、函式、函數




## 一、Introduction 介紹

一般來說，程式啟動時從程式進入點開始，即 main 的所在位置，從以前到現在，我們程式也都是寫在 main 裡面。例如下方這個程式：

{%ace edit=false, lang='c_cpp', theme='monokai'%}

int main() {
	printf("hello world!\n");
	return 0;
}

{%endace%}

不過，有時候我們會有一些重複的程式碼，舉例來說，我們可能常常用到次方這個計算，這時候我們就能用 Function 來減少程式碼的數量，而且若是需要修改計算方式的話，不需要每個地方都修改，增加維護性。其實，說穿了就是各位在數學上都有學習過的函數。y = f(x)，只是現在用 C 來表達。
 
接著，我們就來學習如何撰寫 Function 吧！




## 二、Definition 定義

### 1.本體寫法：

根據定義，Function 的本體寫法為：

{%ace edit=false, lang='c_cpp', theme='monokai'%}

return_type function_name( parameter list ) {
   body of the function
}

{%endace%}

舉例來說，次方的 Function 可以寫成這樣：

{%ace edit=false, lang='c_cpp', theme='monokai'%}

int pow(int base, int power) {
	int i, sum = base;
	for (i = 1; i < power; i++) {
		sum = sum * base;
	} 
	return sum; 
}

{%endace%}

### 2.宣告方式：

宣告原型為：

{%ace edit=false, lang='c_cpp', theme='monokai'%}

return_type function_name( parameter list );

{%endace%}

例如以下這個 Function：

{%ace edit=false, lang='c_cpp', theme='monokai'%}

int pow(int base, int power);

{%endace%}

應該寫成這樣：

{%ace edit=false, lang='c_cpp', theme='monokai'%}

int pow(int, int);

{%endace%}

### 3.位置的藝術

一般來說，Function 必須先宣告，再寫本體。不過若是寫在 main 主程式的上面，就不必再寫宣告。

#### 正確：

{%ace edit=false, lang='c_cpp', theme='monokai'%}

void f1(void) {
	...
}

int main(void) {
	f1();
}

{%endace%}

{%ace edit=false, lang='c_cpp', theme='monokai'%}

void f1(int);

int main(void) {
	f1();
}

void f1(int n) {
	...
}

{%endace%}

{%ace edit=false, lang='c_cpp', theme='monokai'%}

void f2(void) {
	...
}

void f1(int n) {
	f2();
}

int main(void) {
	f1();
}

{%endace%}

#### 錯誤：

{%ace edit=false, lang='c_cpp', theme='monokai'%}

int main(void) {
	f1();
}

void f1(int n) {
	...
}

{%endace%}

{%ace edit=false, lang='c_cpp', theme='monokai'%}

void f1(int n) {
	f2();
}

void f2(void) {
	...
}

int main(void) {
	f1();
}

{%endace%}

### 4.沒有輸入或輸出

Function 是可以接受沒有輸入或輸出的，以下這幾種寫法都會成立：

{%ace edit=false, lang='c_cpp', theme='monokai'%}

void pow(int base, int power) {
	...
}

{%endace%}

{%ace edit=false, lang='c_cpp', theme='monokai'%}

int pow(void) {
	...
}

{%endace%}

{%ace edit=false, lang='c_cpp', theme='monokai'%}

void pow() {
	...
}

{%endace%}

___

### 練習 6-1

請設計一個 Function，功能為輸入兩個數字，回傳兩者相加。


### 練習 6-2

請設計一個 Function，功能為印出 "hello world!" 10 次。
___





## 三、Function 的輸入陷阱

假設我們要設計一個 Function，功能為交換兩個整數值。例如：

x = 5, y = 10，當我們呼叫 swap(x,y); 之後會變成 x = 10, y = 5。

這時大家可能會這樣寫：

{%ace edit=false, lang='c_cpp', theme='monokai'%}

void swap(int x, int y) {
	int tmp;
	tmp = x;
	x = y;
	y = tmp;
}

int main() {
	int x = 5, y = 10;
	printf("Before : x = %d, y = %d\n", x, y );
	swap(x, y);
	printf("After : x = %d, y = %d\n", x, y );
	return 0;
}

{%endace%}

但是執行後卻發現，Before 和 After 是一樣的，意味著值沒有被交換，為什麼？

這是因為，C 語言的 Function 在處理輸入時，其實是在另外一個記憶體位址宣告一個變數，縱使變數名稱是一樣的，代表的卻是不同變數。

那要怎麼樣處理這個問題呢？我們在下一章「指標 Pointer」中將會介紹使用方式。




## 四、Function 進階用法：Recursion 遞迴

###「遞迴只應天上有，凡人該當用迴圈」

通常要做一件事情，我們會用迴圈，例如要寫一個程式，功能為「1 加到 n」

{%ace edit=false, lang='c_cpp', theme='monokai'%}

int sum(int n) { 
	int i;
	int tmp = 0;
	for (i = 0; i < n; i++) 
		tmp = tmp + (i + 1);
	return tmp; 
}

{%endace%}

不過我們可以利用 Function 回傳值可以呼叫 Function 的特性，達到一種不斷呼叫自己的感覺。這種使用方式稱為遞迴（Recursion）

{%ace edit=false, lang='c_cpp', theme='monokai'%}

int sum(int n) { 
	if (n==1) 
		return 1; 
	else 
		return sum(n-1) + n; 
}
 
{%endace%}

這是一種抽象的概念，如果我們要計算 sum(10)，程式會這樣跑：

1.第一次，程式會 return sum(9) + 10;。

2.於是，要計算 sum(10) 必須先計算 sum(9)，而 sum(9) 則 return sum(8) + 9;。

3.不斷如此下去，最後到 return sum(1) + 2; 的時候，對於 sum(1)，程式判斷到 n == 1，直接 return 1;。

4.於是 sum (2) 回傳 1 + 2，sum(3) 則回傳 3(1+2) + 3，sum(4) 則回傳 6(1+2+3) + 4，如此下去，我們得到 sum(10) 的答案。 

___

### 練習 6-3

請設計一個 Recursive Function，功能為輸入 3 印出 123，輸入 5 印出 12345。


### 加分練習 6-4

同上題，不過不能另外寫 Function，不能使用迴圈語法。

___


