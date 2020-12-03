---
title: "在hugo網頁上新增disqus留言版"
date: 2020-12-03T06:29:27+08:00
description: "Sample article showcasing basic Markdown syntax and formatting for HTML elements."
tags: [disqus,hugo]
categories: [架網站]
---

架設完hugo網站之後，可能會需要留言版，這篇文章會帶你一步步架設，雖然網路上有各種架設方法，但是不一定適用每種網站（似乎是跟主題有關），這裡提供的是我的用法，如果不適用，請尋找其他文章。

## 步驟

1.進入[disqus](https://disqus.com/)網站註冊帳號

![disqus首頁](/image/disqushome.png)

2.到下面這個頁面，選擇 ‘I want to install Disqus on my site’，接下來的步驟請參考[這個網站](https://vineo.cn/config-disqus.html)，這裡就不一一說明，註冊完請記住您的shortname。

![disqus選擇頁面](/image/disquschoice.png)

3.開啟你的網站中的single.html檔案（通常在theme/(theme name)/layout/_default裡面），這裡根據主題會有些不同，在我這裡原本是 

```
{{ template "_internal/disqus.html"  . }}
```

（原本是官方的模板，但是我在這裡出了些小問題，所以使用這篇文章寫的模板），將它改成

```
{{ partial "disqus.html" . }}
```
 
，並在theme/(theme name)/layout/partial裡面新增一個disqus.html，貼上以下內容：

```html
<div id="disqus_thread"></div>
<script>
(function() {
var d = document, s = d.createElement('script');
s.src = 'https://<你的disqus-shortname>.disqus.com/embed.js';
s.setAttribute('data-timestamp', +new Date());
(d.head || d.body).appendChild(s);
})();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
```

4.最後在你的config.toml中最後在你的config.toml中新增，將它改成 
```
disqusShortname = "<你的disqus-shortname>"
```

![留言版](/image/disqusok.png)

恭喜你，你完成了！

參考資料

* [原文](https://portfolio.peter-baumgartner.net/2017/09/10/how-to-install-disqus-on-hugo/)

* [Yihui Xie的程式碼](https://github.com/rstudio/blogdown/issues/52#issuecomment-288407836)