---
layout: post
title: html5 to jekyll
subtitle: 
date: 2016-10-12
author: hugohoover
---
# structures p0

## copy `index.html` to `_layouts/default.html`.

## 刪除index中的重複部分，分別是head，footer，，，

刪除default中的content部分，
但是用瀏覽器運行index的時候，頁面顯示異常。
我認為是沒有安裝jekyll的原因，沒有liquid所以識別不了front matter。

教程中可能是在jekyll serve的情況下進行改寫的。

### 確實是我猜測的那樣

因為凌晨了，我中斷了這個項目。
接下來，我要對其他html進行改寫。
具體的操作是，刪除head，footer，用 `include` 命令加入。

。

# 睡了一覺，重新開始這個項目

完全按照教程是不能完成我的項目的，因為兩個html是有差異的。
初學者需要用相同的源代碼來重現作者的方法。
或者，理解其中的意義和關鍵步驟，然後在自己的案例中進行發揮，如俗話所說的舉一反三。

我相信自己已經有了一些背景知識，於是我不採用完全相同的html模板。

# structure p1

## 建立了<sub>layout</sub>/{default.html,pagr.html,post.html}

### \_layout/post.html is needed to be modified

### break: banner不是固定的，所以隨著頁面移動
