---
title: '「直播」Nic拉你出坑，HTTP協定，CRUD與RESTful和MVC架構'
date: 2017-05-08 13:51:00
categories:
 - [生活, 上課]
tags:
 - HTTP
 - CRUD
 - RESTful
 - MVC
---
## HTTP協定到底是什麼？
在網路的世界我們看到的網頁進行的任何操作到底發生了什麼事情呢？我們先簡單的介紹兩個動作和三個端點。

三個端點分別為`客戶端(Client)`，`服務端(Server，也可以說是伺服器)`與`資料庫(DB)`，而兩個動作分別為`請求(Request)`和`回應(Response)`。

再來`客戶端所有的操作都會發出請求給服務端，而服務端向資料庫拿取剛剛客戶端想請求的東西後在回應給客戶端`。

其實講白一點就很像我們在電購東西，今天客人(客戶端)想買一台電視，所以他拿起電話打給店家(服務端)說要下訂一台液晶螢幕，這個動作就叫做請求。

再來店家(服務端)收到訂單之後會去倉庫(資料庫)看看剛剛接到的訂單(請求)還有沒有庫存，有的話就會回電話(成功的回應)給客人說下訂成功，即使沒有庫存的還是會回電話給客人說因為沒有庫存的所以沒有下訂成功(失敗的回應)。

而這種互動方式在網路上面就稱為`HTTP協定`，那我們什麼時候會發送請求這個動作呢？

一般最簡單的就是註冊會員送出的表單就是了，但其實我們打開瀏覽器後`輸入的每個網址都是一個請求`喔！接下來順勢看看什麼是CRUD與RESTful吧！

## CRUD與RESTful
剛剛說的HTTP協定他其實有很多種請求的動作，例如HEAD、GET、
POST、PUT等等還有很多，這些網路上就找得到不用特地背起來，而最常用的動作分別是`GET`、`POST`、`PUT`、`PATCH`和`DELETE`，這些也不用背，因為會常用到然而然背起來。

在以前我們`如何對服務端(server)敘述請求的動作`？最原始的方法就是直接在網址裡面敘述：
```
獲取所有使用者資料/getAllUsers
獲取使用者資料/getUser/1
更新使用者資料/update/user/1
刪除使用者資料/delete/user/1
```

但在Ruby on Rails他發明了更直覺的敘述方法，這種敘述方法就稱為`RESTful API`：
```
獲取所有使用者資料/GET/users
獲取使用者資料/GET/user/1
新增使用者資料/POST/user
刪除使用者資料/DELETE/user/1
```
RESTful API最主要的是我們可以直接看到什麼樣的`請求動作已經在大寫清楚地述敘在上面`。

這樣的規範我們得到了兩個最棒的優點：
1.直觀簡潔的resource URI
2.善用HTTP的動詞

老師在這邊有提到一個很特別的事情，就是`HTML5只能用GET和POST`！！
這樣講起來好像又很弔詭，那到底能不能用呢？

`如果是用Rails當服務端是完全沒有問題的`！ROR服務端是可以了解這種敘述方法的，事實上RESTful API就是ROR發明出來的！

## 什麼是MVC架構？
>ROR天生就是照著MVC的架構做出專案

先敘述一下在rails的世界裡Router像是總機小姐，可以決定什麼樣的請求會導向哪裡，或者呼叫什麼資源過來。

接下來老師直接用一個例子示範Live show。
例子：使用者新增一篇Orid文章就給他50點經驗值

首先我們`先建立Model`，先去Routers定義resource，再到終端間下指令新增:
`rails g model experience user_id:intege orid_id:integer point:integer`

別忘了繼續下`rake db:migrate`更新資料庫。

之後我們在`主要的controller檔案`裡面做一個controller：
if @orid.save
    do something
end

現在如果新增一篇文章的話，其實資料庫裡已經有點數了，只是我們沒有把View更新出來所以看不到。
測試資料庫有沒有更新成功的方法可以在終端機下rails c，在這個環境把最後一筆資料叫出來看看。

剛剛發生的事情是我們新增文章後呼叫了Router(總機小姐)，他`了對應的controller(資源)過來幫忙做事情`，然後這件事情有更新了倉庫(資料庫)。

剛剛因為在主要controller直接寫邏輯大家會看不懂，所以我們通常會把剛剛做的controller放入另一隻檔案，然後再善用變數命名去讓主要controller更為清楚精簡語意化，像剛剛的controller命名就是可以是@orid.generate_point。

小補充：如果把@(at)拿掉的話只有在此定義的方法裡面使用。

最後要顯示點數給客戶端，所以要在網頁(view)上面開始新增點數的HTML程式碼。

首先可以在最下面可以先拿出資料：
def total_point
    experiences.sum(:point)
end

然後在最上面開始寫下這些東西的關聯：
has_many....

最後在畫面上要呈現的地方寫上程式碼 `<p> <%= current_user.total_point %> </p>`，這個就完全是`View的事情`了！

小補充：可以在controller寫下程式碼byebug去找出bug，此時網頁的任何操作不會有反應，因為操作的過程和結果都會顯示在終端機開著rails的server的地方。

回顧流程：
Model:資料庫管理人
Controller:機械手臂
View:根據機械手臂顯現出畫面

Q&A
1.現在市場上以手機市場為主，之後會有APP課程嗎？
其實MVC架構是一樣的，所以rails學好觀念再去學APP是很有幫助的，領域完全不同所以比較有可能開相關課程而已。

2.Model有問題就執行刪除數據嗎？
先找出問題再去新增新的再刪除破損的比較乾淨。

3.ROR可以開發遊戲嗎？
效能不會這麼好，也不是這麼齊全。

4.byebug需要安裝嗎？
可以在gemfile安裝。

今天真的是太濃縮了XD，跟本來不及做筆記，大多事情是我自己敘述的，有錯誤再麻煩指點囉！
