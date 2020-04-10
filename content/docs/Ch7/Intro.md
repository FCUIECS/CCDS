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

```C++
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
```C++
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

```C++
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


## 四、指標的特性

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
```C++
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

```C++
Before : x = 5, y = 10
After : x = 10, y = 5
```

x, y 成功被交換了！如果你不知道為什麼，從頭再看一次指標的定義吧！

## 六、指標的安全問題

說起來，這麼強大的武器就像雙面刃一樣，指標的好處是可以快速的直接進行記憶體存取，然而壞處卻也相同。萬一不小心修改到不應該修改的地方，程式可是會直接掛掉的。更慘的是，由指標所造成的 bug 通常很難被找到，甚至是修復。在這裡，我們稍微學習一下關於指標的安全問題。

### 1.釋放不用的指標

為了避免有許多已不必要的指標掌控著記憶體，指標若不使用就應該被釋放掉。使用方式很簡單，使用 free() 函式即可。使用 free() 釋放指標後，記憶體空間將被歸還給系統，避免程式占用大量記憶體。

```C++

int *ptr;

...

free(ptr);

```

### 2.宣告指標後，要指向 void 或其他地址

假設有一程式如下：

```C++

int *ptr;

*ptr = 10;

```

這將會發生大問題，為什麼？  
當宣告了一個指標後，代表某一塊記憶體空間被拿來當作是 int 型態指標的空間，但是這個空間原本可能有某些資料沒有被清掉。於是，你的指標正指向一個未知的區域，有時候不小心就可能造成大問題。  

所以最好都先給 void。


## 七、動態記憶體配置

到目前為止我們都是講述一般的記憶體配置方式，假若需要一塊整數空間，我們就宣告 int 變數；需要 10 個，我們就宣告 int 陣列。不過，這樣的使用方式無法滿足實務上的需求。  

例如，今天我們需要寫一個校務系統，但沒辦法確定每年的學生人數都一樣。這時候用陣列，如果人太少，就浪費空間；人太多，根本不夠用。我們沒辦法提前知道要多少記憶體空間，只能見招拆招。這時候用到的，就是動態記憶體配置。

### 1.malloc()

### 2.calloc()

### 3.realloc()      


## 八、真正的指標

上述提到的用法，對於各位來說真正有用的應該只有在 Function 的部分，各位可能有很多疑問，這東西這麼抽象，這麼難學，到底有什麼用？別急，接著就是要教你指標的各種型態。

### 1.指標與陣列

### 2.指標與字串

### 3.指標與結構

### 4.指標與函數
