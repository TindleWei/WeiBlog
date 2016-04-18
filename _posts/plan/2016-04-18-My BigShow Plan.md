---
layout: post
title:  My BigShow Plan
date:   2016-04-18
categories: Plan
---

关于BigShow, 最重要的是：快！快！快！

但是我最近确实做慢了。

应该反思。

## 任务300

1. 点击搜索后的第一次自动搜索提示
2. 搜索界面的网格视图
3. 搜索框的输入与确定
4. 搜索框的下拉提示列表
5. 选择图片后的图片展示



## 前言

首先是36Kr的一篇文章, 可以借助这个GIF搜索引擎：http://giphy.com/

微软的Bing也是可以搜索gif图片，但我发现它的图片还是来自Giphy.

比如搜索南方公园 http://giphy.com/search/south-park

所以，BigShow的内容方面就有源源不断与时俱进的素材了。

这里是 Giphy 的文档：https://github.com/Giphy/GiphyAPI

更多的文档：https://api.giphy.com/  http://giphy.com/labs

## 内容分级

关于Parameters,
rating - limit results to those rated (y,g, pg, pg-13 or r).  
  G: General Audiences. All ages admitted.  
  PG: Parental Guidance Suggested. Some material may not be suitable for children.  
  PG-13: Parents Strongly Cautioned. Some material may be inappropriate for children under 13.  
  R: Restricted. Under 17 requires accompanying parent or adult guardian.  
  NC-17: No Children. No one 17 and under admitted.  



-------------------------------------------------------------------------------------------------
选择不光可以是文字，它可以是任何东西。
-------------------------------------------------------------------------------------------------

## 数据

Plot
num(三叉树排序)
isEnd: 0 非End, 1 End
dataFrom: (参考项)giphy, user
dataImg: (jsonstring: data: type:)
dataText: (jsonstring: data: type:)
dataChoose: (jsonstring: data: type:)
fromStory

Story
[nothing add now]

关于GiphyAPI

Translate Endpoint:
http://api.giphy.com/v1/gifs/translate?s=superman&api_key=dc6zaTOxFJmzC
将名词转化为特定图片,每次随机一个

Search Endpoint: 
http://api.giphy.com/v1/gifs/search?q=funny+cat&api_key=dc6zaTOxFJmzC
通过搜索关键字获得数据列表,默认为25个

Random Endpoint:
http://api.giphy.com/v1/gifs/random?api_key=dc6zaTOxFJmzC&tag=american+psycho
根据标签随机获得一个数据

Trending Gifs:
http://api.giphy.com/v1/gifs/trending?api_key=dc6zaTOxFJmzC
随机数据流25个

-------------------------------------------------------------------------------------------------

Gmail之父说过一句话：你需要将某几件事情做得精益求精，而不要追求面面俱到。

对于BigShow，有3个核心点：
制作：上手环节、自动补全
游戏中：选择、结局、生命值
分类：栏目、排序、推荐

-------------------------------------------------------------------------------------------------

关于字体

我在 http://www.uisdc.com/23-handwritten-english-font 找到了http://www.fontsquirrel.com/fonts/architects-daughter,
该ArchitectsDaughter.ttf字体遵从SIL Open Font License协议。
知乎上其他的 https://www.zhihu.com/question/21759657。
