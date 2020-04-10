# 基礎結構

在Ｃ語言中，我們可以利用結構來做很多事情，不過結構到底是啥呢？

## 為何要用結構？
在先前寫的一些範例中，我們的程式會有越來越多的變數宣告，以最常見的成績系統範例來說，大多都長得像這樣：  
```c++
int main() {
    int chinese_score[100], math_score[100], english_score[100];
    char student_name[100][20], student_sex[100];
    double student_average[100];
    // ... 
}
```
結構可以協助我們將相同或相關的變數整合成一個，讓我們可以更輕鬆地去閱讀程式碼、更方便地去撰寫程式。  
以上面這例子來講，所有的score、name、sex、average都是學生的資料，而我們把這些資料分開來存，會讓我們在後續的資料處理會有相當程度的障礙。  
因此我們可以運用結構，將上面的例子變成：  
```c++
int main() {
    struct Student stu[100];
    // ...
}
```
這樣，我們在存取學生資料時，只要到stu的某一項去尋找就好了，不必在各個變數中來回尋找。  

> 在C語言中，結構體(struct)指的是一種資料結構，是C語言中聚合數據類型(aggregate data type)的一類。結構體可以被聲明為變量、指針或數組等，用以實現較複雜的資料結構。結構體同時也是一些元素的集合，這些元素稱為結構體的成員(member)，且這些成員可以為不同的類型，成員一般用名字訪問。
> -- Wikipedia

## 原型宣告
結構的原型宣告建議寫在``int main()``之外、，所有函式宣告之上，避免錯誤。
基本上，結構的定義會長得像這個樣子：  
```c++
struct tag { member-list } variable-list ; 
```
實際上宣告則會是這樣：
```c++
struct Student {
    char name[20];
    char sex;
    int chinese_score;
    int math_score;
    int english_score;
    double average;
} stu[100];
```
其中，Student 就是 tag，中間所有的變數就是 member-list（成員列表），而 stu[100] 就是宣告的 variable-list 。  
在Ｃ語言中的結構，成員的型態可以不相同；結構可以不寫tag，但必須在原型宣告時宣告變數；variable-list 也可以為空，但這時你就必須有 tag。

## 結構變數宣告
你可以在原型宣告的時候就宣告好變數，不過當然你也可以在主函式或其他函式中宣告，宣告的定義如下：  
```c++
struct tag variable-list;
```
以上面的 Student 結構來講，宣告一個變數名為 s：
```c++
struct Student s;
```
