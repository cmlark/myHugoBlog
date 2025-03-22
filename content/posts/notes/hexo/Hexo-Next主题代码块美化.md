---
title: Hexo Next主题代码块美化
tags: ["Hexo", "Next主题", "主题美化"]
categories: Hexo
draft: false
date: 2022-04-11T01:00:09+08:00
---

#### 1.正文

在 NexT 主题下的 scripts 目录中创建 events.js

```css

var exec = require('child_process').exec;

hexo.on('new', function(data){
    exec('open -a MacDown ' + data.path);
});
```

在 NexT 主题下的 scripts 目录中创建 codeblock.js

```css

var attributes = [
  'autocomplete="off"',
  'autocorrect="off"',
  'autocapitalize="off"',
  'spellcheck="false"',
  'contenteditable="true"'
]

var attributesStr = attributes.join(' ')

hexo.extend.filter.register('after_post_render', function (data) {
  while (/<figure class="highlight ([a-zA-Z]+)">.*?<\/figure>/.test(data.content)) {
    data.content = data.content.replace(/<figure class="highlight ([a-zA-Z]+)">.*?<\/figure>/, function () {
      var language = RegExp.$1 || 'plain'
      var lastMatch = RegExp.lastMatch
      lastMatch = lastMatch.replace(/<figure class="highlight /, '<figure class="iseeu highlight /')
      return '<div class="highlight-wrap"' + attributesStr + 'data-rel="' + language.toUpperCase() + '">' + lastMatch + '</div>'
    })
  }
  return data
})
```

在 themes/next/source/css/\_common/components/highlight/highlight.styl 的基础上调整了下样式，包裹上一层类 mac Panel 的效果。

**==注： 这里不用删除原来 highlight.styl 里边的内容，只需要在末尾添加下面代码即可==**

```css
.highlight-wrap[data-rel] {
  position: relative;
  overflow: hidden;
  border-radius: 5px;
  box-shadow: 0 10px 30px 0px rgba(0, 0, 0, 0.4);
  margin: 35px 0;
  ::-webkit-scrollbar {
    height: 10px;
  }

  ::-webkit-scrollbar-track {
    -webkit-box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.3);
    border-radius: 10px;
  }

  ::-webkit-scrollbar-thumb {
    border-radius: 10px;
    -webkit-box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.5);
  }
  &::before {
    color: white;
    content: attr(data-rel);
    height: 38px;
    line-height: 38px;
    background: #21252b;
    color: #fff;
    font-size: 16px;
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    font-family: "Source Sans Pro", sans-serif;
    font-weight: bold;
    padding: 0px 80px;
    text-indent: 15px;
    float: left;
  }
  &::after {
    content: " ";
    position: absolute;
    -webkit-border-radius: 50%;
    border-radius: 50%;
    background: #fc625d;
    width: 12px;
    height: 12px;
    top: 0;
    left: 20px;
    margin-top: 13px;
    -webkit-box-shadow: 20px 0px #fdbc40, 40px 0px #35cd4b;
    box-shadow: 20px 0px #fdbc40, 40px 0px #35cd4b;
    z-index: 3;
  }
}
```

在 highlight.styl 中找到如下部分代码，修改 margin 为 36px 0 0 0：

```css

$code-block {
  overflow: auto;
-  margin: 20px 0;  //这一行改为
+  margin: 36px 0 0 0;  //这个
  padding: 0;
  font-size $code-font-size;
  color: $highlight-foreground;
  background: $highlight-background;
  line-height: $line-height-code-block;
}
```

在主题中将高亮代码变为：night eighties

```css
highlight_theme: night eighties;
```

最后来要在网站根目录下打开 Git Bash，然后执行以下命令重新生成静态页面：

```shell

hexo clean && hexo g
```
