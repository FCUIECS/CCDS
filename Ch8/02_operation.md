# 結構操作
一般的結構變數，可以直接將**結構變數當成一般變數來使用**。

## 成員取值
如果我們想要取得一個結構變數中的成員的值，可以運用「 . 」這個運算子，以前一章的 Student 結構為例子：  
```c++
struct Student {
    char name[20];
    char sex;
    int chinese_score;
    int math_score;
    int english_score;
    double average;
};
int main() {
    struct Student s;
}
```
當我們想要存取 s 的 name（名字）的時候，就可以這樣寫：  
```c++
// 輸入
scanf("%s", s.name);
// 賦值
strcpy(s.name, "Danny");
// 輸出
printf("%s", s.name);
```

## 變數初始化
結構變數的初始化方法非常簡單，一樣在宣告的同時，運用``{ }``、``.``、``,``三者結合即可，範例如下：
```c++
struct Student s = {
    .name = "Peter",
    .sex = 'M',
    .chinese_score = 63,
    .math_score = 98,
    .english_score = 87,
    .average = 82.666666
};
```
每個成員前面都要加``.``，成員之間則用``,``隔開，前後則用``{ }``夾起來。

## 複製結構
結構變數跟一般變數具有相似性質，一般變數能做的，結構變數大多也能做，例如常見的「賦值」。  
我們可以直接將已經有資料的結構變數，賦予給一個沒有資料的結構變數，如此一來就可以達到「複製」的效果。
```c++
struct Student s = {
    .name = "Peter",
    .sex = 'M',
    .chinese_score = 63,
    .math_score = 98,
    .english_score = 87,
    .average = 82.666666
}, t;
t = s;
```
此時，t 裡面的內容會跟 s 一模一樣，我們可以來檢查看看：  
```c++
printf("%s\n", s.name);
printf("%s\n", t.name);
```
各位也可以自行檢查其他成員的值是否相同。

## 傳遞結構變數
結構變數也可以正常地丟進一般變數中，舉例來說，如果我想傳入一個 Student 結構變數去計算平均，我們可以這樣寫：  
```c++
double calc_average(struct Student stu) {
    return (stu.chinese_score + stu.math_score + stu.english_score) / 3.0;
}

int main() {
    struct Student s = {
        .name = "Peter",
        .sex = 'M',
        .chinese_score = 63,
        .math_score = 98,
        .english_score = 87,
        .average = 82.666666
    };
    s.average = calc_average(s);
    // ...
}
```
又或者，你可以連回傳都不要，讓函式計算完直接幫你塞回去：  
```c++
double calc_average(struct Student *stu) {
    stu->average = (stu->chinese_score + stu->math_score + stu->english_score) / 3.0;
}

int main() {
    struct Student s = {
        .name = "Peter",
        .sex = 'M',
        .chinese_score = 63,
        .math_score = 98,
        .english_score = 87,
        .average = 82.666666
    };
    calc_average(&s);
    // ...
}
```

## 自定義型態
有時候你會覺得``struct Student``打起來很長，用起來很煩、寫起來很煩，有沒有更簡單的寫法？  
有，當然有，我們可以透過 ``typedef`` 來自定義型態，typedef的定義如下：
```c++
typedef struct tag { member-list } type-name ; 
```
舉例來說，以上面的 Student 結構來講，我們可以自定義一個 Student 型態：  
```c++
typedef struct _Student {
    char name[20];
    char sex;
    int chinese_score;
    int math_score;
    int english_score;
    double student_average;
} Student;
```
而此時我們可以透過型態來宣告變數，也可以透過結構來宣告變數：  
```c++
// 這兩個宣告出來的東西是一樣的
Student a;
struct _Student b;
```
初始化方式和原本一樣，而且，這兩個變數也是可以互相等號（賦值）的：  
```c++
Student a = {
    .name = "Peter",
    .sex = 'M',
    .chinese_score = 63,
    .math_score = 98,
    .english_score = 87,
    .average = 82.666666
};
struct _Student b;
b = a;
```
存取方式也和結構變數一樣，利用``.``來做成員取值：  
```c++
Student s= {
     .name = "Peter",
     .sex = 'M',
     .chinese_score = 63,
     .math_score = 98,
     .english_score = 87,
     .average = 82.666666
 };
// 輸入
scanf("%s", s.name);
// 賦值
strcpy(s.name, "Danny");
// 輸出
printf("%s", s.name);
```
