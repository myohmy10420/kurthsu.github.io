---
title: '正法寶藏JavaScript第十一～三堂課(初探React)'
date: 2016-09-27 08:30:00
categories:
 - [生活, 跨行學程式]
---
這兩堂課是學習Facebook開發的『框架』，只能說天啊，被搞的覺得自己很像低能兒，超級挫折啊！！！！！！！！XD

## 什麼是框架
網路上對於框架的解說十分豐富，但總的來說就是讓一個團隊有一個寫程式的架構，除了把一些底層的東西打包好更好使用之外也可以讓專案更好管理和維護。

你可以想像一群建築工人他們每個人會蓋的房子是千變萬化的，如果沒有一個藍圖和規則蓋房子的話不但沒有效率之外房子的格局很有可能是千變萬化而且彼此的東西是格格不入難以融入的。

沒有藍圖而去蓋一棟摩天大樓這像話嗎？XD

## React的條件與語法
首先要學習React這個框架除了前端三大語言(HTML,css,JavaScript)要有基礎的熟悉度之外還需要對於node和npm有一定的認識。

node和npm是相輔相成的，這兩個像是前端界的套件管理工具，你可以想像當要蓋房子的時候不可能全部的工具都自己做，手推車、吊具、甚至是一些蓋房子的技術等等，一些東西是可以去引進別人已經做好而且完善的工具和套件，而React就是電腦本身完全不懂而別人製作出來的套件之一，只是功能龐大的成為了一個框架。

在語法上面越來愈多高層語言希望程式越來越語意化，讓Programmer越來越好跟我們的電腦溝通，我們在[React的官方網站](https://facebook.github.io/react/index.html)可以找到官方相當的推薦jsx這種語法，搭配上ES6的語法可以讓整個程式很容易給人閱讀和維護。

## React的環境
承如上個主題有提到React也是node可以安裝的套件，那我們如何建立React的環境呢？

如果真的想要看一下React怎麼運作的話可以使用官方釋出的create-react-app專案樣板產生器，可以直接看裡面的東西體驗React的魅力，使用方法請輸入下列指令：
- sudo npm install -g create-react-app
- create-react-app 專案名稱
- cd 專案名稱
- npm start
執行完之後應該會自行開啟一個網頁顯示範例

但這對node和專案管理要有一定熟悉度的人來說會比較實在，不然對於我這種菜鳥反而會產生超級多的疑點導致於腦袋爆炸。XD

除了官方網站的範例之外網路上也有釋出很多React的教程，有[免費的React101](https://www.gitbook.com/book/kdchang/react101/details)或者一些需要付費有影片的電子教材，其實我本人蠻不推React101的，對於新手來說真的很不友善，對於我來說有影片跟著一步一步做並且有解說才是最實在的！這是我和朋友購買的線上電子教材，也是叫[React101](https://www.mokoversity.com/training/React-101)。


## React核心--Component、import、export
這兩堂老師所教導的React讓我覺得這個框架可以把功能切成非常多的細項，甚至可以不斷使用，非常符合物件導向的精神。

在Component裡面我們甚至可以把html的東西寫在Component裡面，這樣可以讓html和javascript的互動更加的靈活並且效能更好。

老師曾說React入門門檻其實反而比較低，因為他是非常囉唆的框架，
每一個功能都需要環環相扣好，如果某個功能沒有用到甚至React還會出現警告，而且每一個Component做好做export之後在要使用這個Component的檔案一定要import進去。

對我來說React給我的感覺就像是製作一塊拼圖，每一個拼圖的凸點一定要有一個凹口去接應他，如此繁雜的防呆機制雖然很麻煩，但大大的降低了新手程式爆炸的風險。

import和export就是屬於ES6的jsx語法，可以參考網路上別人提供的[jsx簡易教學](http://blog.techbridge.cc/2016/04/21/react-jsx-introduction/)來初步認識jsx語法。
