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

{%ace edit=false, lang='c_cpp', theme='monokai'%}
struct Student {
	int stuID;
}Student;

Student student[10];
{%endace%}

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
