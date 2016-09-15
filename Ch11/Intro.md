# Chapter 11：人形蜈蚣 Linked List

中文：鏈結串列、連結串列

## 1.Introduction 簡介

Linked List 是資料結構的其中一種，利用節點與指標來將資料串起來，可以充分利用記憶體空間。
在 C/C++ 當中，我們將以 Linked List 來實作許多資料結構，如 Stack、Queue。

通常，我們使用陣列來儲存相關的資料。但是陣列有其缺點：

* 宣告時就必須給予陣列大小
* 無法伸縮
* 必須是連續的記憶體空間

例如，有一個學生管理系統，我們需要宣告很多學生的變數，可能會這樣做：

```C++
typedef struct stu {
	int stuID;
}Student;

Student student[10];
```

可是，每一年的學生數量都不同，我們也無法預測未來的學生數量。
如果我們宣告的陣列太小，之後就會不夠用；若宣告的陣列太大，又浪費記憶體空間。

這時，Linked List 就出場了。


## 2.Concept 概念

有一個 節點（Node） 結構，裡面除了資料外，還有一個 節點型態的指標。
每當我們需要一筆新資料時，向系統要一塊空間，然後將指標指過去。

以下便是單向 Linked List：  

![Singly-linked-list.png](img/Singly-linked-list.png)

插入時的運作方式：  

![linked-list-insert.png](img/linked-list-insert.png)

刪除時的運作方式：  

![linked-list-del.png](img/linked-list-del.png)

## 3.Implementation 實作方向

### A. 定義節點
首先我們必須先定義每個 節點（Node） 到底長什麼樣子。  
如同以下的程式碼，我們定義一個 data 節點，裡面有 int 型態的資料以及 data 型態的指標。

```C++
typedef struct data{
    int number;
    struct data *next;
}DATA;
```

### B. 定義必要的指標
接著我們需要至少兩個指標，用來實作 Linked List 的各種功能。  
這兩個指標一個是 head，另一個是 current。head 永遠指向第一個節點，而 current 則是作為各種功能的定位點。

```C++
DATA *head    = NULL;
DATA *current = NULL;
```

### C. 生成節點的方式
我們要開始來生成節點了。假如今天有一筆新的資料被加入，我們應該怎麼做呢？  
寫一個生成 function，向系統要一塊記憶體空間，然後把指標回傳。

```C++
DATA* create_node(int number) {

	//宣告一個 DATA 型態的指標，指向 malloc 跟系統要到的記憶體空間。
    DATA *tempPointer = malloc(sizeof(DATA));

    //將資料放進剛拿到的空間，指向下一個節點的指標設為 null
    n->number = number;
    n->next = NULL;

    //回傳指標
    return tempPointer;
}
```

### D. 使用 Linked List 作插入

我們有能力生成節點之後，必須把節點塞進我們的 Linked List 裡面。

插入時的運作方式：  

![linked-list-insert.png](img/linked-list-insert.png)

```C++
//把 node2 塞到 node1 後面。
void insert_node(DATA* node1, DATA* node2)
{
    node2->next = node1->next;
    node1->next = node2;
}
```

### E. 使用 Linked List 作刪除

用 malloc 要來的記憶體空間會放在 heap 而不是 stack，所以不會隨著 function 結束釋放，
必須要用 free() 釋放掉，否則會造成 memory leak。

刪除時的運作方式：  

![linked-list-del.png](img/linked-list-del.png)

```C++
//刪除 n 的下一個 node 
void remove_node(DATA* n)
{
	//宣告一指標指向 n 的下一個節點
	DATA* temp = n->next;

	//將 n 指向下下一個節點
    n->next = n->next->next;

    //釋放被刪除節點的記憶體空間
    free(temp);
}
```

### F. 印出所有資料

```C++
void printAll(DATA* head) {
	while(head->next != NULL) {
		cout << head->number << endl;
	}
	cout << head->number << endl;
}
```

## 4. Examples 範例

```C++
typedef struct data{
    int number;
    struct data *next;
}DATA;

DATA *head    = NULL;
DATA *current = NULL;

DATA* create_node(int number) {
    DATA *tempPointer = malloc(sizeof(DATA));
    n->number = number;
    n->next = NULL;
    return tempPointer;
}

void createNewDataAtLast(int number) {
	current = head;
	if(head == null) {
		head = create_node(number);
	} else {
		while(current->next != NULL) {
			current = current->next;
		}
		current->next = create_node(number);
	}
}

void printAll(DATA* head) {
	if(head == null) return;
	while(head->next != NULL) {
		cout << head->number << endl;
	}
	cout << head->number << endl;
}

int main(int argc, char const *argv[])
{
	while(1) {
		int choice;
		cout << "Choose the function you want :" << endl;
		cout << "1. Add data" << endl;
		cout << "2. Print All datas" << endl;
		cout << "3. Exit"
		cint >> choice;

		system("cls");

		switch(choice) {
			case 1:
				int data;
				cout << "Input data:";
				cin >> data;
				createNewDataAtLast(data);
				cout << "Add data successfully!" << endl;
				break;
			case 2:
				printAll(head);
				break;
			case 3:
				exit(0);
			default:
				cout << "Error!" << endl;
				break;
		}
		system("pause");
	}
	
	return 0;
}

```

___

### 練習 11-1

設計一個 Linked List 程式，節點結構為：
```C++
typedef struct data{
    int number;
    string name;
    struct data *next;
}DATA;
```

有選單，可以用以下功能：

* 新增資料
* 刪除
* 印出所有資料

### 回家練習 11-2

同上，但功能有：

* 新增資料
* 插入資料
* 刪除
* 查詢
* 排序資料（大到小）
* 排序資料（小到大）
* 印出所有資料
* 刪除所有資料
   
___

