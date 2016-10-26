# 實作佇列
一般而言，佇列的實作有兩種方法，用陣列(array)或鏈結串列(linked list)實作，通常這兩者實做出來沒有太大的差別，唯一要注意的是，用array實作的佇列會有長度上的限制。  

## 以Array實作
首先，我們先要定義一個佇列結構，在這邊我們現暫訂佇列只能儲存整數，且限制長度為 100，同時我們需要一個 length 來儲存 **現在的長度** ，而我們這邊先假定所有資料都不會是 **零** ：    

{%ace edit=false, lang='c_cpp', theme='monokai'%}
sturct Queue{
    int data[100];
    int length;
};
{%endace%}

緊接著是建構子(放在struct裡面)：  

{%ace edit=false, lang='c_cpp', theme='monokai'%}
Queue(){
    this->length = 0;
    for(int i=0; i< 100; i++) {
        data[i] = 0;
    }
};
{%endace%}

接著分別來實作新增、刪除功能，新增功能(push)必須從後端放進去：  

{%ace edit=false, lang='c_cpp', theme='monokai'%}
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
{%endace%}

刪除也是類似的方法，只不過刪除只能從前端刪除，而且每次移除，都必須將第 n 個往前移動一個位置：  

{%ace edit=false, lang='c_cpp', theme='monokai'%}
void pop() {
    bool success = false;
    if (this->length > 0) {
        for(int i=1; i<100; i++) {
            this->data[i-1] = this->data[i];
        }
        this->data[99] = 0;
        success = true;
    }
    if (success) {
        this->length--;
    }
    return;
};
{%endace%}

接著，通常佇列可以知道前端的資料與後端的資料，因此我們需要幾個函式來存取第一筆跟第 n 筆資料：  

{%ace edit=false, lang='c_cpp', theme='monokai'%}
int front(){
    if (this->length == 0) {
        return 0;
    } else {
        return this->data[0];
    }
};

int rear(){
    if (this->length == 0) {
          return 0;
    } else {
          return this->data[this->length-1];
    }
};
{%endace%}

以及，我們有時候會需要了解到這個佇列現在的狀態，因此加上「目前長度」、「是否為空」和「是否滿了」的函式：  

{%ace edit=false, lang='c_cpp', theme='monokai'%}
int size() {
    return this->length;
};

bool isEmpty() {
    return this->length == 0;
};

bool isFull() {
    return this->length == 100;
};
{%endace%}

最後，集上面之大成，你就有完整的佇列結構了！使用的方法和之前的 Linked List 很像：  

{%ace edit=false, lang='c_cpp', theme='monokai'%}
// 宣告物件
Queue queue = new Queue();
// 新增資料
queue->push(10);
// 刪除資料
queue->pop();
// 取得前端資料
queue->front();
// 取得後端資料
queue->rear();
// 取得佇列長度
quere->size();
// 檢查佇列是否為空
queue->isEmpty();
// 檢查佇列是否滿了
queue->isFull();
{%endace%}

## 以Linked List實作
(待補)
