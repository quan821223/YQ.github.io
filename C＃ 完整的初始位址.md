# 完整的初始位址名稱 in C# 
###### tags: `Lesson learnt`, `C#`, `WPF`

### 現象
> 情境，把某一 wpf 編寫的工具程式當作插件程式於另一系統進行呼叫並且執行，當主程式運行該工具程式後發生該工具程式打不開且一直在背後執行的狀況。

### 檔案配置

後來檢視程式碼，疑似找不到初始位址而發生該現象發生。以下為資料夾的檔案配置

〔main〕[debug]
   │ 
   ├──〔tool app〕
   │ ．．．       ├── 〔tool.exe〕
   │ ．．．       ├── 
   │ ．．．       
   ├──〔main.exe〕

### 分析

最開始使用這樣的寫法，摁~非常不嚴謹(不然不會出現一些應用上的問題)。因為用這種寫法會抓到debug的資料夾
，重點是跳錯的時候沒有任何徵兆。
```csharp!
   if (Directory.Exists(System.Windows.Forms.Application.StartupPath + @".\util") == false) Directory.CreateDirectory(@".\util");
```
後來就反覆看程式碼並且關閉一些變數才發現該狀況是位址出問題，後來上網找看有沒有比較嚴謹的寫法。
```csharp!
    if (Directory.Exists(System.Windows.Forms.Application.StartupPath + @"\util") == false) Directory.CreateDirectory(System.Windows.Forms.Application.StartupPath + @"\util");
```

:book: Reference
---
> [ 自己 ](https://github.com/quan821223)

---
:muscle: Declaration
---
 > 此處所出的文章 :
 > 1. 只是圖謀本人在未來寫code時能有個複習(偷看的小抄?)的地方
 > 2. 以上談論都只是實務上碰到的問題，小弟只是想做一個Lessons learned 
 總之希望可以幫助像我一樣半路出家寫code維生的打工仔，如內容有錯要糾正(鞭)一下請小力小弟怕痛(誤)，讓大夥在這看不盡的學習之路程不會這麼荊棘與顛波。

