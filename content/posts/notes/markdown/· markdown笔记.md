---
title: markdown笔记
tags: ["markdown笔记"]
categories: markdown
date: 2022-04-09T11:49:01+08:00
draft: false
---

### · markdown 笔记

##### 1.代码块

````markdown
```java 语言代码

```
````

```java
public static void main(String[] args){
    System.out.print("Hello World!");
}
```

##### 2.标题

```markdown
# 一级标题

## 二级标题

### 三级标题

...

###### 六级标题
```

# 一级标题

## 二级标题

### 三级标题

### ...

###### 六级标题

### 3.字体

```markdown
**加粗**
==高亮==
~~删除线~~
_斜体_
```

**加粗**

~~删除线~~

_斜体_

### 4.引用

```markdown
> 作者：某某某
>
> > 二级作者
> >
> > > 三级作者
```

> 作者：某某某
>
> > 二级作者
> >
> > > 三级作者

### 5.分割

```markdown
## 分割线

分割线 2

---
```

分割线 1

---

分割线 2

---

### 6.插图

```markdown
在线图片
![图片的名字](/图片路径)
本地图片
![图片的名字](/图片url)
```

![照片](https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fb-ssl.duitang.com%2Fuploads%2Fitem%2F201804%2F18%2F2018041882506_fGU3F.thumb.700_0.jpeg&refer=http%3A%2F%2Fb-ssl.duitang.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1651976555&t=832a30901b8a64eb4e655e9170d08f84)

### 7.超链接

```markdown
[名字](地址)
```

[我的网易云歌单](https://music.163.com/playlist?id=557481298&userid=392935859)

### 8.列表

```markdow
无序列表
- 目录1
- 目录2
- 目录3
- 目录4
有序列表
1. 名称
```

- 无序列表

- 目录 1

- 目录 2

1. 有序列表

2. 自动生成的 2

### 9.表格

```mark
| 你好 | 你好 | 早安 |
| ---- | ---- | ---- |
| 晚安 |      |      |
|      |      |      |
|      |      |      |

```

**表格**

| 你好 | 你好 | 早安 |
| ---- | ---- | ---- |
| 晚安 |      |      |
|      |      |      |
|      |      |      |
