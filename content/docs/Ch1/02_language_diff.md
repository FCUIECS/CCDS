# 低中高階語言
程式語言就是人與電腦溝通的橋樑，  
就像世界上有很多語言，像是中文、英文、日文等等，  
程式語言也有很多種，像是C、C++、Java、Python，  
使用程式語言寫程式即可電腦溝通  

CPU只看得懂一種語言，叫做機器碼(Machine code)，  
所以需要跟CPU溝通的話就需要翻譯的存在，
將程式碼轉換成機器碼有三種方式，組譯、編譯、直譯

* 組譯(Assembling)
  * 將組合語言轉換成機器語言
  * 反過來將機器語言變成組合語言(Disassemble)
    * 玩資安，寫外掛的重要技能
  * ex. 組合語言使用組譯器
* 直譯
  * 透過直譯器(interpreter)對原始碼進行一邊讀解，一邊執行的動作
  * 優點，在每個指令打完後就可以知道結果，較適合新手(but直譯跳到編譯難)
  * 每次執行每次直譯
  * ex. python使用直譯器
* 編譯
  * 將原始程式碼透過編譯器(Compiler)轉換成機器碼，再直接執行機器碼
  * 優點；轉換速度快，可以一次找出不合文法的內容
  * 原始程式 --> 經由編譯器 --> 變成目的檔 --> 經由連結器 --> 變成執行檔  
  * SOURCE.C --> COMPILER --> SOURCE.OBJ --> LINKER --> SOURCE.EXE  
  * 編譯過一次後，以後只需要執行機器碼
  * ex. C語言使用編譯器

越接近CPU語言的叫低階語言，  
越接近人類語言的較高階語言，  
還有個剛好在中間的叫做中階語言。  
* 低階語言
  * 每一道指令對應一個 CPU 控制碼、程式碼超級多、重複性大
  * 對硬體控制較好
  * 程式效能較高
  * 比較難懂
  * ex. 組合語言、機器碼
* 中階語言
  * 原本C也算是高階語言，不過有些高階語言使用C編譯完的函式庫(Library)
  * 因此有些人也稱C為高階語言
  * ex. C語言
* 高階語言
  * 比較好懂，程式碼較少
  * 較容易撰寫、除錯
  * 對硬體控制能力較差、程式效能也較差
  * ex. python、Java

同一件事情，  
假設高階語言要寫十行程式碼，  
低階語言可能需要五百行，  
但，低階語言能直接做到很多高階語言不容易做到的事情。  
