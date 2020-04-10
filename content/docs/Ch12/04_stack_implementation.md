# 實作堆疊
一般而言，堆疊的實作和佇列一樣，可以用陣列(array)或鏈結串列(linked list)實作，通常這兩者實做出來沒有太大的差別，唯一要注意的是，用array實作的佇列會有長度上的限制。  

## 以Array實作
首先，我們先要定義一個堆疊結構，在這邊我們現暫訂堆疊只能儲存整數，且限制長度為 100，同時我們需要一個 length 來儲存 **現在的長度** ，而我們這邊先假定所有資料都不會是 **零** ：    

```C++
sturct Stack{
    int data[100];
    int length;
};
```

緊接著是建構子(放在struct裡面)：  

```C++
Stack(){
    this->length = 0;
    for(int i=0; i< 100; i++) {
      data[i] = 0;
    }
};
```

接著分別來實作新增、刪除功能，新增功能(push)必須從頂端(top)放進去：  

```C++
void push(int num) {
    bool success = false;
    if (this->length >= 0 && this->length < 100) {
        this->data[this->length] = num;
        success = true;
    }
    if (success) {
        this->length++;
    }
    return;
};
```

刪除也是類似的方法，和佇列不一樣的是，刪除只能從頂端刪除：  

```C++
void pop() {
    bool success = false;
    if (this->length > 0) {
        this->data[this->length-1] = 0;
        success = true;
    }
    if (success) {
        this->length--;
    }
    return;
};
```

接著，通常堆疊可以知道頂端的資料，因此我們需要一個top函式來存取最頂端的資料：  

```C++
int top(){
    if (this->length == 0) {
        return 0;
    } else {
        return this->data[this->length-1];
    }
};
```

以及，我們有時候會需要了解到這個堆疊現在的狀態，因此加上「目前長度」、「是否為空」和「是否滿了」的函式：  

```C++
int size() {
    return this->length;
};

bool isEmpty() {
    return this->length == 0;
};

bool isFull() {
    return this->length == 100;
};
```

最後，集上面之大成，你就有完整的堆疊結構了！使用的方法和堆疊很像：  

```C++
// 宣告物件
Stack* stack = new Stack();
// 新增資料
stack->push(10);
// 刪除資料
stack->pop();
// 取得頂端資料
stack->top();
// 取得佇列長度
stack->size();
// 檢查佇列是否為空
stack->isEmpty();
// 檢查佇列是否滿了
stack->isFull();
```

## 以Linked List實作
(待補)
