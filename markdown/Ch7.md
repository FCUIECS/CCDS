# Chapter 7：鬼門遁甲 Pointer

中文：指標




## 一、Introduction 介紹

指標，是 C 語言中最強而有力的一項特性，也是最多人放棄的一個地方。指標有強力，而且高效能的優點，卻也伴隨著難以撰寫、難以入門、難以理解、難以維護的缺點。其寫法千變萬化，令人嘆為觀止。但是不要怕，只要搞懂了指標的定義，你就踏出成功的第一步了。

在介紹指標之前，讓我們複習一下變數（Variable）這個機制是如何運作的。

變數提供了一個有名稱的記憶體位址，當我們宣告 int x = 0; 的時候，其實是系統在記憶體當中找一塊 int 大小的空間，記錄下記憶體位址（像是 0x23ff12，每次不一樣），名稱設為 x。

### 取址運算子（Address-of operator）

如果我們想知道變數的記憶體位址，可以使用取址運算子「&」：

```C++

int main(void) {
	int x = 10;
	printf("Value of x : %d\n", x);
	printf("Address of x : %p\n", &x);
	return 0;
}

```

執行結果為：

```
Value of x : 10
Address of x : 0x23ff12
```

也就是說，記憶體位置 0x23ff12 這個地方放著 10，這個地方的名字叫做 x。

而我們這章節要介紹的 Pointer 指標，是一種型態，專門儲存記憶體位址。就像是一個指標指向某一個地方。簡單來說，指標指向記憶體位址。


## 二、Definition 定義

### 宣告方式

指標的宣告方式為：

```C++

type *ptr;

```

例如：

```C++

int *ptr;
float *ptr2;
char *ptr3;

```

宣告指標必須宣告型態，讓 Compiler 可以知道目標記憶體位址上的資料要如何解釋。


## 三、How to use 使用方式

我們必須把指標指向某個記憶體位址，可以這樣寫：

```C++

int x = 10;
int *ptr = &x;

```

或是

```C++

int x = 10;
int *ptr;

ptr = &x;

```

這樣子寫，代表宣告 ptr 是一個 int 型態的指標，指向變數 x 的記憶體位址。

### 提取運算子（Dereference）

如果要取得這個記憶體的值，我們要用 * 提取運算子。

```C++

int x = 10;
int *ptr &x;;

printf("The value of x : %d\n", x);
printf("The value of address where ptr point : %d\n", *x);

```

執行結果為：
```
The value of x : 10
The value of address where ptr point : 10
```


如果我們把全部都 print 出來比較的話：

```C++

int x = 10;
int *ptr = &x;;

printf("The value of x : %d\n", x);
printf("The address of x : %p\n", &x);
printf("The address where ptr point : %p\n", ptr);
printf("The value of address where ptr point : %d\n", *ptr);
printf("The address of pointer ptr : %p\n", &ptr);

```

執行結果應該會像以下：

```
The value of x : 10
The address of x : 0x12fe1e
The address where ptr point : 0x12fe1e
The value of address where ptr point : 10
The address of pointer ptr : 0xfa131a
```

不要忘記指標也擁有自己的記憶體位址。

___

### 練習 7-1

設計一個 float 型態的指標，並且像範例一樣 print 出來看看位址與數值。
___


## 四、指標特性

我們寫了一個以下的程式：

```C++

int x = 10;
int *ptr = &x;

```

並且對 ptr 所指向的值做修改：

```C++

*ptr = 20;

```

這時候值會如何變化呢？我們 print 出來看看：

```C++

printf("The value of address where ptr point : %d\n", *ptr);
printf("The value of x : %d\n", x);

```

執行結果如下：
```
The value of address where ptr point : 20
The value of x : 20
```

由於指標 ptr 指向的記憶體位址和變數 x 所代表的記憶體位址是同樣的，於是我們修改了 ptr 指標所指向的記憶體位址的值，也同樣修改了變數 x 的值。

實務上，這種特性可以讓你有許多種用法，其中一種最基本的，就是拿來解我們在上一章節所提到的 Function 問題。

## 五、解 Function 的輸入陷阱

上一章提到，假設我們要設計一個 Function，功能為交換兩個整數值，會遇到一些問題，原因是在 Function 中使用的變數和外面的變數是不同的，為了解決這個問題，我們必須使用上述指標的特性。

愚蠢的你大概還沒想到怎麼做，簡單說，就是我們把記憶體位址當作 Function 的參數傳進去！

原本的程式應該是這樣：

```C++

void swap(int x, int y) {
	int tmp;
	tmp = x;
	x = y;
	y = tmp;
}

int main() {
	int x = 5, y = 10;
	printf("Before : x = %d, y = %d", x, y );
	swap(x, y);
	printf("After : x = %d, y = %d", x, y );
	return 0;
}

```

我們改成這樣：

```C++

void swap(int *x, int *y) {
	int tmp;
	tmp = *x;
	*x = *y;
	*y = tmp;
}

int main() {
	int x = 5, y = 10;
	printf("Before : x = %d, y = %d\n", x, y );

	//傳記憶體位址進去
	swap(&x, &y);
	
	printf("After : x = %d, y = %d\n", x, y );
	return 0;
}

```

執行結果：

```
Before : x = 5, y = 10
After : x = 10, y = 5
```

x, y 成功被交換了！如果你不知道為什麼，從頭再看一次指標的定義吧！

