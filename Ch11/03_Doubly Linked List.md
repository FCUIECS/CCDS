# 雙向鏈結串列 Doubly Linked List

## 1. What is Doubly LL? 什麼是雙向？

前面的 Linked List 有個小問題，假如我今天要找 current 指標所指向的節點，往前兩個節點的資料時，必須要從 head 重新尋找起，而且程式會複雜一些。

要解決這個問題，我們只要在節點中增加一個指標是往前指的，就可以了。

示意圖：  
![Doubly-linked-list.png](img/Doubly-linked-list.png)

## 2. Implementation 實作

加上一個指標就行了。

```C++
typedef struct data{
    int number;
    struct data *next;
    struct data *prev;
}DATA;
```

至於其他的方法，就要多增加一些程式碼，像是新增、刪除。  
想一下，自己寫寫看吧！

___

### 練習 11-3

請設計一個 雙向 Linked List 程式，節點結構為：
```C++
typedef struct data{
    int number;
    struct data *next;
    struct data *prev;
}DATA;
```

有選單，可以用以下功能：

* 新增資料
	* 在最後面新增一筆資料
* 刪除
	* 輸入要刪除的位置，執行刪除
* 印出所有資料
	* 一筆一筆印出 number 和 name
* 印出第n個節點以及前後節點的資料

第4個功能，例如輸入5，則印出4,5,6節點的資料。如果沒有，就印出錯誤。  
___
