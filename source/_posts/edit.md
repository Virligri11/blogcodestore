---
title: Hexo-Next 魔改记录
date: 
tags: editing
description: change blog model
---


# 1.背景添加条纹

->在themes 的——config.yml里面添加
```
# Canvas-nest
# Dependencies: https://github.com/theme-next/theme-next-canvas-nest
# For more information: https://github.com/hustcc/canvas-nest.js
canvas_nest:
  enable: true
  color: "225, 225, 225" # RGB values, use `,` to separate
  opacity: 1 # The opacity of line: 0~1
  zIndex: -1 # z-index property of the background
  count: 300 # The number of lines
```
->在themes/next/layout/_layout.njk的footer中添加
```
    {% if theme.canvas_nest.enable %}

    <script color="{{ theme.canvas_nest.color }}" 
            opacity="{{ theme.canvas_nest.opacity }}" 
            zIndex="{{ theme.canvas_nest.zIndex }}" 
            count="{{ theme.canvas_nest.count }}" 
            src="https://cdn.jsdelivr.net/npm/canvas-nest.js@1/dist/canvas-nest.js">
    </script>

    {% endif %}
```

github仓库：https://github.com/hustcc/canvas-nest.js?tab=readme-ov-file

# 2.链接色调更改

在themes\next\source\css\_common\components\post\post.styl中的.post-body中添加
```
  p a{
    color: #549ddd;
    border-bottom: none;
    border-bottom: 1px solid #0593d3;
    &:hover {
      color: #fc6423;
      border-bottom: none;
      border-bottom: 1px solid #fc6423;
    }
  }

```
# 3. 添加字数总计

先`npm install hexo-wordcount --save`
然后在/themes/next/layout/post/post-meta.njk中添加
```
  {%- if theme.post_meta.wordcounts %}
      <div class="theme-info">
      <div class="powered-by"></div>
      <span><i class="far fa-calendar"></i></span>
      <span class="post-count">Total word count: {{ wordcount(post.content) }}</span>
    </div>
  {%- endif %}
```
然后`npm install hexo-wordcount --save`
再之后在_config.yml中添加
```
# Post wordcount display settings
# Dependencies: https://github.com/willin/hexo-wordcount
post_wordcount:
  item_text: true
  wordcount: true
  min2read: true
  totalcount: true
  separated_meta: true

```
**reminder: icons of wordcounts need to change

# 4. 添加背景图片

手动更改
`blog/themes/next/source/css/_schemes/Gemini/index.styl`
```
body {
 	background:url(/images/background.png);
 	background-repeat: no-repeat;
    background-attachment: fixed; //是否滚动，fixed固定
    background-size: cover;      //填充
    background-position: center;
}
```
# 5. 设置间距
`/blog/themes/next/source/css/_variables/Pisces.styl`
```
$content-desktop-large        = 70em;
$content-desktop-largest      = 75%;
```
# 6. 边框圆角
`/blog/themes/next/source/css/_variables/Gemini.styl`
```
$border-radius-inner     = 30px 30px 30px 30px;
$border-radius           = 30px 30px 30px 30px;
```

# 7. 
`/blog/themes/next/source/css/_schemes/Pisces/_header.styl`
```
.site-brand-container {
  margin-top:50px
  background: rgba(225,225,225,0);

  .site-nav-on & {
    +tablet-mobile() {
      box-shadow: 0 0 16px rgba(0, 0, 0, .5);
    }
  }
}
```