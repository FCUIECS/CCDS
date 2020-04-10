# 結構指標
又是指標？  
沒錯，又是指標！  
在Ｃ語言中，結構也可以定義指標，我們稱它為「結構指標」，結構指標是我們未來實作一些「資料結構」的基礎。

## 指標宣告
以上一章節 typedef 後的結構為例：
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
宣告的方法就跟一般變數一樣，加個星號``*``就好：  
```c++
// 兩者是一樣的
Student *a;
struct _Student *b;
```
兩者都需要給予記憶體空間才能存放資料，否則都只能存記憶體位址，使用完畢也要使用``free()``來釋放空間。
```c++
// 兩種寫法是一樣的
a = (Student *)malloc(sizeof(Student));
free(a);
b = (struct _Student *)malloc(sizeof(struct _Student));
free(b);
```

## 成員取值
結構指標取值的方法有兩種，一個是跟結構變數一樣的用``.``，另一個則是用``->``。  
以下都採用 ``Student *a`` 作為範例：  
```c++
// 輸入
scanf("%s", (*a).name);
scanf("%s", a->name);
// 賦值
strcpy((*a).name, "Danny");
strcpy(a->name, "Danny");
// 輸出
printf("%s", (*a).name);
printf("%s", a->name);
```
兩種寫法都可以，不過要注意的是，由於``.``這個運算子的優先權大於``*``，因此在使用時務必將 ``*a`` 用 ``( )`` 夾起來。  
為了避免忘記，我們會建議各位未來在使用結構指標時，一律使用 ``->``。  
