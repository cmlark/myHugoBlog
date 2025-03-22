---
title: Hexo Next8.x美化配置记录
tags: ["Hexo", "Next主题", "主题美化"]
categories: Hexo
draft: false
date: 2022-04-15T09:42:48+08:00
---

#### 前言

网上收集的方法做一个整合贴。

<!--more-->

#### 1.基础配置

**（1）安装 Next8.x**

可以直接下载 Next，将文件夹直接复制到 hexo 项目的 theme 文件夹下，修改项目的\_config.yml 切换主题。

或者直接使用 git 下载 Next 最新版本。[Next8 的 Github](https://github.com/next-theme/hexo-theme-next)

```bash
cd hexo
git clobe https://github.com/next-theme/hexo-theme-next themes/next
```

**（2）将博客更换为 next 主题**

```yaml
theme: next
```

**（3）配置基本信息**

这里的配置项是在博客根目录下的\_config.yml，并非主题下的。

```yaml
# Site
title: 樱花换小鱼干 #博客的标题
subtitle: ""
description: "" #博客的描述
keywords:
author: 樱花换小鱼干 #你的笔名
language: zh-CN #主题语言
timezone: ""
```

**（4）选配主题的几种排版**

有四种，只能选其一，去掉注释#

```yaml
# Schemes
#scheme: Muse
#scheme: Mist
#scheme: Pisces
scheme: Gemini
```

**（7）配置语言**

```yaml
# You can set a language value if you prefer a translated version of CC license, e.g. deed.zh
# CC licenses are available in 39 languages, you can find the specific and correct abbreviation you need on https://creativecommons.org
language: zh-CN
```

Next 支持多种语言。进入　/next/languages,找到我们所需要要的语言，然后将其文件名替换上面的 zh-CN.

**（8）配置菜单**

Next 默认设置两个菜单项 home 和 archives。

菜单项包含三个值：key:/link/ || icon

注意：key,对大小写敏感。

key 即为下图中‘：’前单词，例如 home,

/link 、icon 与之对应.

key 与之前设置的 luanage 相对应，如果设置为中文，则会自动转换为中文。

/link 　为网页对应的 url

icon 为对应字体图标的类名。

这里字体图标采用 font-awesome.

如果要自定义菜单项，修改 Next 配置文件，如下：

```yaml
menu:
  home: / || fa fa-home
  about: /about/ || fa fa-user
  tags: /tags/ || fa fa-tags
  #categories: /categories/ || fa fa-th
  archives: /archives/ || fa fa-archive
  #schedule: /schedule/ || fa fa-calendar
  #sitemap: /sitemap.xml || fa fa-sitemap
  #commonweal: /404/ || fa fa-heartbeat
```

菜单配置完成后需要配置对应的文件夹，否则点击相应的栏目会报错。

比如要创建关于菜单，除了要在 menu 配置项目里取消注释，还要在站点根目录配置相应的链接。比如，我想要创建 tags 菜单，除了要取消 menu 的 tags 注释外，还要再根目录执行以下命令：

```bash
hexo new page tags
```

其他的菜单类似。也可以在相应的目录里配置要显示的内容，支持 markdown 语法。

```markdown
---
title: 标签
date: 2022-04-15T11:41:49+08:00
type: "tags"
---
```

更改 ttle 后在站点的对应菜单会显示你更改的内容，此文本不可被删除，否则报错。

如果自动生成的 index.md 里没有 type 配置项请自行按照上面的格式添加。

**（9）配置 favicon**

站点默认使用的 favicon 是 Next Icon 　存在于 hexo-site/themes/next/source/images/目录下。里面存在有对应不同设备使用不同的 favicon。在这里我们可以使用自定义 favicon 来替代它。

首先，我们将我们的 favicon 存放到 hexo-site/themes/next/source/images/　目录下，然后配置项目配置文件，否则 favicon 将不会被更改。

```yaml
favicon:
  small: /images/xiaoyugan.png
  medium: /images/xiaoyugan.png
  apple_touch_icon: /images/xiaoyugan.png
  safari_pinned_tab: /images/xiaoyugan.png
  #android_manifest: /manifest.json
```

**（10）配置头像**

在 Next 中默认不展示头像，如需展示，我们需要进入 Next 配置文件，进行更改。

修改自己头像

```yaml
# Sidebar Avatar
avatar:
  # Replace the default image and set the url here.
  url: /images/xiaoyugan.png #/images/avatar.gif
  # 这里置为true可以显示圆形头像。
  rounded: true
  # 这里置为true鼠标放在头像上会转动
  rotated: false
```

其中 url 可以直接指定 url 地址

**（11）启用本地搜索**

在主题配置文件中找到

```yaml
# Local Search
# Dependencies: https://github.com/next-theme/hexo-generator-searchdb
local_search:
  enable: true
  # If auto, trigger search by changing input.
  # If manual, trigger search by pressing enter key or search button.
  trigger: auto
  # Show top n results per article, show all results by setting to -1
  top_n_per_article: 1
  # Unescape html strings to the readable one.
  unescape: false
  # Preload the search data when the page loads.
  preload: false
```

将 enable 置为 true，并在站点根目录下执行：

```bash
npm install hexo-generator-searchdb --save
```

**（11）启用不蒜子阅读统计**

在主题配置目录中找到

```yaml
# Show Views / Visitors of the website / page with busuanzi.
# For more information: http://ibruce.info/2015/04/04/busuanzi/
busuanzi_count:
  enable: true
  total_visitors: true
  total_visitors_icon: fa fa-user
  total_views: true
  total_views_icon: fa fa-eye
  post_views: true
  post_views_icon: far fa-eye
```

将 enable 置为 true

**（12）添加代码复制按钮**

找到如下配置项

```yaml
codeblock:
  # Code Highlight theme
  # All available themes: https://theme-next.js.org/highlight/
  theme:
    light: default
    dark: stackoverflow-dark
  prism:
    light: prism
    dark: prism-dark
  # Add copy button on codeblock
  copy_button:
    enable: true
    # Available values: default | flat | mac
    style: mac
```

将 copy_button 的 enable 改为 true 即可，style 可以选择 default | flat | mac 这三种。

**（13）安装相关依赖**

分别在站点根目录和主题根目录下执行：

```bash
npm install --save
```

至此，基本配置完成，站点基本元素已完善。

**（14）还有一些琐碎的配置**

如果觉得太麻烦可以直接用我的这一份配置文件：

```yaml
# ===============================================================
# It's recommended to use Alternate Theme Config to configure NexT
# Modifying this file may result in merge conflict
# See: https://theme-next.js.org/docs/getting-started/configuration
# ===============================================================

# ---------------------------------------------------------------
# Theme Core Configuration Settings
# See: https://theme-next.js.org/docs/theme-settings/
# ---------------------------------------------------------------

# Allow to cache content generation.
cache:
  enable: true

# Remove unnecessary files after hexo generate.
minify: true

# Define custom file paths.
# Create your custom files in site directory `source/_data` and uncomment needed files below.
custom_file_path:
  #head: source/_data/head.njk
  #header: source/_data/header.njk
  #sidebar: source/_data/sidebar.njk
  #postMeta: source/_data/post-meta.njk
  #postBodyEnd: source/_data/post-body-end.njk
  #footer: source/_data/footer.njk
  #bodyEnd: source/_data/body-end.njk
  #variable: source/_data/variables.styl
  #mixin: source/_data/mixins.styl
  #style: source/_data/styles.styl

# ---------------------------------------------------------------
# Scheme Settings
# ---------------------------------------------------------------

# Schemes
#scheme: Muse
#scheme: Mist
#scheme: Pisces
scheme: Gemini

# Dark Mode
darkmode: false

# ---------------------------------------------------------------
# Site Information Settings
# ---------------------------------------------------------------

favicon:
  small: /images/xiaoyugan.png
  medium: /images/xiaoyugan.png
  apple_touch_icon: /images/xiaoyugan.png
  safari_pinned_tab: /images/xiaoyugan.png
  #android_manifest: /manifest.json

# Custom Logo (Warning: Do not support scheme Mist)
custom_logo: #/uploads/custom-logo.jpg

# Creative Commons 4.0 International License.
# See: https://creativecommons.org/about/cclicenses/
creative_commons:
  # Available values: by | by-nc | by-nc-nd | by-nc-sa | by-nd | by-sa | cc-zero
  license: by-nc-sa
  # Available values: big | small
  size: small
  sidebar: false
  post: false
  # You can set a language value if you prefer a translated version of CC license, e.g. deed.zh
  # CC licenses are available in 39 languages, you can find the specific and correct abbreviation you need on https://creativecommons.org
  language: zh-CN

# Open graph settings
# See: https://hexo.io/docs/helpers#open-graph
open_graph:
  enable: true
  options:
    #twitter_card: <twitter:card>
    #twitter_id: <twitter:creator>
    #twitter_site: <twitter:site>
    #twitter_image: <twitter:image>
    #google_plus: <g+:profile_link>
    #fb_admins: <fb:admin_id>
    #fb_app_id: <fb:app_id>

# ---------------------------------------------------------------
# Menu Settings
# ---------------------------------------------------------------

# Usage: `Key: /link/ || icon`
# Key is the name of menu item. If the translation for this item is available, the translated text will be loaded, otherwise the Key name will be used. Key is case-sensitive.
# Value before `||` delimiter is the target link, value after `||` delimiter is the name of Font Awesome icon.
# External url should start with http:// or https://
menu:
  home: / || fa fa-home
  tags: /tags/ || fa fa-tags
  categories: /categories/ || fa fa-th
  archives: /archives/ || fa fa-archive
  about: /about/ || fa fa-user
  #schedule: /schedule/ || fa fa-calendar
  #sitemap: /sitemap.xml || fa fa-sitemap
  #commonweal: /404/ || fa fa-heartbeat

# Enable / Disable menu icons / item badges.
menu_settings:
  icons: true
  badges: false

# ---------------------------------------------------------------
# Sidebar Settings
# See: https://theme-next.js.org/docs/theme-settings/sidebar
# ---------------------------------------------------------------

sidebar:
  # Sidebar Position.
  position: left
  #position: right

  # Manual define the sidebar width. If commented, will be default for:
  # Muse | Mist: 320
  # Pisces | Gemini: 240
  #width: 300

  # Sidebar Display (only for Muse | Mist), available values:
  #  - post    expand on posts automatically. Default.
  #  - always  expand for all pages automatically.
  #  - hide    expand only when click on the sidebar toggle icon.
  #  - remove  totally remove sidebar including sidebar toggle.
  display: post

  # Sidebar padding in pixels.
  padding: 18
  # Sidebar offset from top menubar in pixels (only for Pisces | Gemini).
  offset: 12

# Sidebar Avatar
avatar:
  # Replace the default image and set the url here.
  url: /images/xiaoyugan.png #/images/avatar.gif
  # If true, the avatar will be displayed in circle.
  rounded: true
  # If true, the avatar will be rotated with the cursor.
  rotated: true

# Posts / Categories / Tags in sidebar.
site_state: true

# Social Links
# Usage: `Key: permalink || icon`
# Key is the link label showing to end users.
# Value before `||` delimiter is the target permalink, value after `||` delimiter is the name of Font Awesome icon.
social:
  #GitHub: https://github.com/yourname || fab fa-github
  E-Mail: mailto:orange_lun@outlook.com || fa fa-envelope
  #Weibo: https://weibo.com/yourname || fab fa-weibo
  #Google: https://plus.google.com/yourname || fab fa-google
  #Twitter: https://twitter.com/yourname || fab fa-twitter
  #FB Page: https://www.facebook.com/yourname || fab fa-facebook
  #StackOverflow: https://stackoverflow.com/yourname || fab fa-stack-overflow
  #YouTube: https://youtube.com/yourname || fab fa-youtube
  #Instagram: https://instagram.com/yourname || fab fa-instagram
  #Skype: skype:yourname?call|chat || fab fa-skype

social_icons:
  enable: true
  icons_only: false
  transition: false

# Blog rolls
links_settings:
  icon: fa fa-globe
  title: Links
  # Available values: block | inline
  layout: block

links:
  #Title: https://example.com

# Table of Contents in the Sidebar
# Front-matter variable (nonsupport wrap expand_all).
toc:
  enable: true
  # Automatically add list number to toc.
  number: false
  # If true, all words will placed on next lines if header width longer then sidebar width.
  wrap: false
  # If true, all level of TOC in a post will be displayed, rather than the activated part of it.
  expand_all: false
  # Maximum heading depth of generated toc.
  max_depth: 6

# ---------------------------------------------------------------
# Footer Settings
# See: https://theme-next.js.org/docs/theme-settings/footer
# ---------------------------------------------------------------

# Show multilingual switcher in footer.
language_switcher: false

footer:
  # Specify the year when the site was setup. If not defined, current year will be used.
  #since: 2021

  # Icon between year and copyright info.
  icon:
    # Icon name in Font Awesome. See: https://fontawesome.com/icons
    name: fa fa-heart
    # If you want to animate the icon, set it to true.
    animated: false
    # Change the color of icon, using Hex Code.
    color: "#ff0000"

  # If not defined, `author` from Hexo `_config.yml` will be used.
  copyright:

  # Powered by Hexo & NexT
  powered: false

  # Beian ICP and gongan information for Chinese users. See: https://beian.miit.gov.cn, http://www.beian.gov.cn
  beian:
    enable: false
    icp:
    # The digit in the num of gongan beian.
    gongan_id:
    # The full num of gongan beian.
    gongan_num:
    # The icon for gongan beian. See: http://www.beian.gov.cn/portal/download
    gongan_icon_url:

# ---------------------------------------------------------------
# Post Settings
# See: https://theme-next.js.org/docs/theme-settings/posts
# ---------------------------------------------------------------

# Automatically excerpt description in homepage as preamble text.
excerpt_description: true

# Read more button
# If true, the read more button will be displayed in excerpt section.
read_more_btn: true

# Post meta display settings
post_meta:
  item_text: true
  created_at: true
  updated_at:
    enable: true
    another_day: true
  categories: true

# Post wordcount display settings
# Dependencies: https://github.com/next-theme/hexo-word-counter
symbols_count_time:
  separated_meta: true
  item_text_total: true

# Use icon instead of the symbol # to indicate the tag at the bottom of the post
tag_icon: false

# Donate (Sponsor) settings
# Front-matter variable (nonsupport animation).
reward_settings:
  # If true, a donate button will be displayed in every article by default.
  enable: false
  animation: false
  #comment: Buy me a coffee

reward:
  #wechatpay: /images/wechatpay.png
  #alipay: /images/alipay.png
  #paypal: /images/paypal.png
  #bitcoin: /images/bitcoin.png

# Subscribe through Telegram Channel, Twitter, etc.
# Usage: `Key: permalink || icon` (Font Awesome)
follow_me:
  #Twitter: https://twitter.com/username || fab fa-twitter
  #Telegram: https://t.me/channel_name || fab fa-telegram
  #WeChat: /images/wechat_channel.jpg || fab fa-weixin
  #RSS: /atom.xml || fa fa-rss

# Related popular posts
# Dependencies: https://github.com/sergeyzwezdin/hexo-related-posts
related_posts:
  enable: true
  title: # Custom header, leave empty to use the default one
  display_in_home: true

# Post edit
# Easily browse and edit blog source code online.
post_edit:
  enable: false
  url: https://github.com/user-name/repo-name/tree/branch-name/subdirectory-name/ # Link for view source
  #url: https://github.com/user-name/repo-name/edit/branch-name/subdirectory-name/ # Link for fork & edit

# Show previous post and next post in post footer if exists
# Available values: left | right | false
post_navigation: left

# ---------------------------------------------------------------
# Custom Page Settings
# See: https://theme-next.js.org/docs/theme-settings/custom-pages
# ---------------------------------------------------------------

# TagCloud settings for tags page.
tagcloud:
  min: 14 # Minimum font size in px
  max: 14 # Maximum font size in px
  amount: 200 # Total amount of tags
  orderby: name # Order of tags
  order: 1 # Sort order

# Google Calendar
# Share your recent schedule to others via calendar page.
calendar:
  calendar_id: <required> # Your Google account E-Mail
  api_key: <required>
  orderBy: startTime
  showLocation: false
  offsetMax: 72 # Time Range
  offsetMin: 4 # Time Range
  showDeleted: false
  singleEvents: true
  maxResults: 250

# ---------------------------------------------------------------
# Misc Theme Settings
# See: https://theme-next.js.org/docs/theme-settings/miscellaneous
# ---------------------------------------------------------------

# Preconnect CDN for fonts and plugins.
# For more information: https://www.w3.org/TR/resource-hints/#preconnect
preconnect: false

# Set the text alignment in posts / pages.
text_align:
  # Available values: start | end | left | right | center | justify | justify-all | match-parent
  desktop: justify
  mobile: justify

# Reduce padding / margin indents on devices with narrow width.
mobile_layout_economy: false

# Browser header panel color.
theme_color:
  light: "#222"
  dark: "#222"

# Override browsers' default behavior.
body_scrollbar:
  # Place the scrollbar over the content.
  overlay: false
  # Present the scrollbar even if the content is not overflowing.
  stable: false

codeblock:
  # Code Highlight theme
  # All available themes: https://theme-next.js.org/highlight/
  theme:
    light: default
    dark: stackoverflow-dark
  prism:
    light: prism
    dark: prism-dark
  # Add copy button on codeblock
  copy_button:
    enable: true
    # Available values: default | flat | mac
    style: mac

back2top:
  enable: true
  # Back to top in sidebar.
  sidebar: false
  # Scroll percent label in b2t button.
  scrollpercent: false

# Reading progress bar
reading_progress:
  enable: false
  # Available values: left | right
  start_at: left
  # Available values: top | bottom
  position: top
  reversed: false
  color: "#37c6c0"
  height: 3px

# Bookmark Support
bookmark:
  enable: false
  # Customize the color of the bookmark.
  color: "#222"
  # If auto, save the reading progress when closing the page or clicking the bookmark-icon.
  # If manual, only save it by clicking the bookmark-icon.
  save: auto

# `Follow me on GitHub` banner in the top-right corner.
github_banner:
  enable: false
  permalink: https://github.com/yourname
  title: Follow me on GitHub

# ---------------------------------------------------------------
# Font Settings
# ---------------------------------------------------------------
# Find fonts on Google Fonts (https://fonts.google.com)
# All fonts set here will have the following styles:
#   light | light italic | normal | normal italic | bold | bold italic
# Be aware that setting too much fonts will cause site running slowly
# ---------------------------------------------------------------
# Web Safe fonts are recommended for `global` (and `title`):
# Arial | Tahoma | Helvetica | Times New Roman | Courier New | Verdana | Georgia | Palatino | Garamond | Comic Sans MS | Trebuchet MS
# ---------------------------------------------------------------

font:
  enable: false

  # Uri of fonts host, e.g. https://fonts.googleapis.com (Default).
  host:

  # Font options:
  # `external: true` will load this font family from `host` above.
  # `family: Times New Roman`. Without any quotes.
  # `size: x.x`. Use `em` as unit. Default: 1 (16px)

  # Global font settings used for all elements inside <body>.
  global:
    external: true
    family: Lato
    size:

  # Font settings for site title (.site-title).
  title:
    external: true
    family:
    size:

  # Font settings for headlines (<h1> to <h6>).
  headings:
    external: true
    family:
    size:

  # Font settings for posts (.post-body).
  posts:
    external: true
    family:

  # Font settings for <code> and code blocks.
  codes:
    external: true
    family:

# ---------------------------------------------------------------
# SEO Settings
# See: https://theme-next.js.org/docs/theme-settings/seo
# ---------------------------------------------------------------

# If true, site-subtitle will be added to index page.
# Remember to set up your site-subtitle in Hexo `_config.yml` (e.g. subtitle: Subtitle)
index_with_subtitle: false

# Automatically add external URL with Base64 encrypt & decrypt.
exturl: false
# If true, an icon will be attached to each external URL
exturl_icon: true

# Google Webmaster tools verification.
# See: https://developers.google.com/search
google_site_verification:

# Bing Webmaster tools verification.
# See: https://www.bing.com/webmasters
bing_site_verification:

# Yandex Webmaster tools verification.
# See: https://webmaster.yandex.ru
yandex_site_verification:

# Baidu Webmaster tools verification.
# See: https://ziyuan.baidu.com/site
baidu_site_verification:

# ---------------------------------------------------------------
# Third Party Plugins & Services Settings
# See: https://theme-next.js.org/docs/third-party-services/
# More plugins: https://github.com/next-theme/awesome-next
# You may need to install the corresponding dependency packages
# ---------------------------------------------------------------

# Math Formulas Render Support
# Warning: Please install / uninstall the relevant renderer according to the documentation.
# See: https://theme-next.js.org/docs/third-party-services/math-equations
# Server-side plugin: https://github.com/next-theme/hexo-filter-mathjax
math:
  # Default (false) will load mathjax / katex script on demand.
  # That is it only render those page which has `mathjax: true` in front-matter.
  # If you set it to true, it will load mathjax / katex script EVERY PAGE.
  every_page: false

  mathjax:
    enable: false
    # Available values: none | ams | all
    tags: none

  katex:
    enable: false
    # See: https://github.com/KaTeX/KaTeX/tree/master/contrib/copy-tex
    copy_tex: false

# Easily enable fast Ajax navigation on your website.
# For more information: https://github.com/next-theme/pjax
pjax: false

# FancyBox is a tool that offers a nice and elegant way to add zooming functionality for images.
# For more information: https://fancyapps.com/fancybox/
fancybox: false

# A JavaScript library for zooming images like Medium.
# Warning: Do not enable both `fancybox` and `mediumzoom`.
# For more information: https://medium-zoom.francoischalifour.com
mediumzoom: false

# Vanilla JavaScript plugin for lazyloading images.
# For more information: https://apoorv.pro/lozad.js/demo/
lazyload: false

# Pangu Support
# For more information: https://github.com/vinta/pangu.js
# Server-side plugin: https://github.com/next-theme/hexo-pangu
pangu: false

# Quicklink Support
# For more information: https://getquick.link
# Front-matter variable (nonsupport home archive).
quicklink:
  enable: false

  # Home page and archive page can be controlled through home and archive options below.
  # This configuration item is independent of `enable`.
  home: false
  archive: false

  # Default (true) will initialize quicklink after the load event fires.
  delay: true
  # Custom a time in milliseconds by which the browser must execute prefetching.
  timeout: 3000
  # Default (true) will attempt to use the fetch() API if supported (rather than link[rel=prefetch]).
  priority: true

# ---------------------------------------------------------------
# Comments Settings
# See: https://theme-next.js.org/docs/third-party-services/comments
# ---------------------------------------------------------------

# Multiple Comment System Support
comments:
  # Available values: tabs | buttons
  style: tabs
  # Choose a comment system to be displayed by default.
  # Available values: disqus | disqusjs | changyan | livere | gitalk | utterances
  active:
  # Setting `true` means remembering the comment system selected by the visitor.
  storage: true
  # Lazyload all comment systems.
  lazyload: false
  # Modify texts or order for any naves, here are some examples.
  nav:
    #disqus:
    #  text: Load Disqus
    #  order: -1
    #gitalk:
    #  order: -2

# Disqus
# For more information: https://disqus.com
disqus:
  enable: false
  shortname:
  count: true

# DisqusJS
# For more information: https://disqusjs.skk.moe
disqusjs:
  enable: false
  # API Endpoint of Disqus API (https://disqus.com/api/docs/).
  # Leave api empty if you are able to connect to Disqus API. Otherwise you need a reverse proxy for it.
  # For example:
  # api: https://disqus.skk.moe/disqus/
  api:
  apikey: # Register new application from https://disqus.com/api/applications/
  shortname: # See: https://disqus.com/admin/settings/general/

# Changyan
# For more information: https://changyan.kuaizhan.com
changyan:
  enable: false
  appid:
  appkey:

# LiveRe comments system
# You can get your uid from https://livere.com/insight/myCode (General web site)
livere_uid: # <your_uid>

# Gitalk
# For more information: https://gitalk.github.io
gitalk:
  enable: false
  github_id: # GitHub repo owner
  repo: # Repository name to store issues
  client_id: # GitHub Application Client ID
  client_secret: # GitHub Application Client Secret
  admin_user: # GitHub repo owner and collaborators, only these guys can initialize gitHub issues
  distraction_free_mode: true # Facebook-like distraction free mode
  # When the official proxy is not available, you can change it to your own proxy address
  proxy: https://cors-anywhere.azm.workers.dev/https://github.com/login/oauth/access_token # This is official proxy address
  # Gitalk's display language depends on user's browser or system environment
  # If you want everyone visiting your site to see a uniform language, you can set a force language value
  # Available values: en | es-ES | fr | ru | zh-CN | zh-TW
  language:

# Utterances
# For more information: https://utteranc.es
utterances:
  enable: false
  repo: user-name/repo-name # Github repository owner and name
  # Available values: pathname | url | title | og:title
  issue_term: pathname
  # Available values: github-light | github-dark | preferred-color-scheme | github-dark-orange | icy-dark | dark-blue | photon-dark | boxy-light
  theme: github-light

# Isso
# For more information: https://posativ.org/isso/
isso: # <data_isso>

# ---------------------------------------------------------------
# Post Widgets & Content Sharing Services
# See: https://theme-next.js.org/docs/third-party-services/post-widgets
# ---------------------------------------------------------------

# Star rating support to each article.
# To get your ID visit https://widgetpack.com
rating:
  enable: false
  id: # <app_id>
  color: "#fc6423"

# AddThis Share. See: https://www.addthis.com
# Go to https://www.addthis.com/dashboard to customize your tools.
add_this_id:

# ---------------------------------------------------------------
# Statistics and Analytics
# See: https://theme-next.js.org/docs/third-party-services/statistics-and-analytics
# ---------------------------------------------------------------

# Google Analytics
# See: https://analytics.google.com
google_analytics:
  tracking_id: # <app_id>
  # By default, NexT will load an external gtag.js script on your site.
  # If you only need the pageview feature, set the following option to true to get a better performance.
  only_pageview: false

# Baidu Analytics
# See: https://tongji.baidu.com
baidu_analytics: # <app_id>

# Growingio Analytics
# See: https://www.growingio.com
growingio_analytics: # <project_id>

# Cloudflare Web Analytics
# See: https://www.cloudflare.com/web-analytics/
cloudflare_analytics:

# Microsoft Clarity Analytics
# See: https://clarity.microsoft.com/
clarity_analytics: # <project_id>

# Show number of visitors of each article.
# You can visit https://www.leancloud.cn to get AppID and AppKey.
leancloud_visitors:
  enable: false
  app_id: # <your app id>
  app_key: # <your app key>
  # Required for apps from CN region
  server_url: # <your server url>
  # Dependencies: https://github.com/theme-next/hexo-leancloud-counter-security
  # If you don't care about security in leancloud counter and just want to use it directly
  # (without hexo-leancloud-counter-security plugin), set `security` to `false`.
  security: true

# Another tool to show number of visitors to each article.
# Visit https://console.firebase.google.com/u/0/ to get apiKey and projectId.
# Visit https://firebase.google.com/docs/firestore/ to get more information about firestore.
firestore:
  enable: false
  collection: articles # Required, a string collection name to access firestore database
  apiKey: # Required
  projectId: # Required

# Show Views / Visitors of the website / page with busuanzi.
# For more information: http://ibruce.info/2015/04/04/busuanzi/
busuanzi_count:
  enable: true
  total_visitors: true
  total_visitors_icon: fa fa-user
  total_views: true
  total_views_icon: fa fa-eye
  post_views: true
  post_views_icon: far fa-eye

# ---------------------------------------------------------------
# Search Services
# See: https://theme-next.js.org/docs/third-party-services/search-services
# ---------------------------------------------------------------

# Algolia Search
# For more information: https://www.algolia.com
algolia_search:
  enable: false
  hits:
    per_page: 10

# Local Search
# Dependencies: https://github.com/next-theme/hexo-generator-searchdb
local_search:
  enable: true
  # If auto, trigger search by changing input.
  # If manual, trigger search by pressing enter key or search button.
  trigger: auto
  # Show top n results per article, show all results by setting to -1
  top_n_per_article: 1
  # Unescape html strings to the readable one.
  unescape: false
  # Preload the search data when the page loads.
  preload: false

# ---------------------------------------------------------------
# Chat Services
# See: https://theme-next.js.org/docs/third-party-services/chat-services
# ---------------------------------------------------------------

# A button to open designated chat widget in sidebar.
# Firstly, you need to enable and configure the chat service.
chat:
  enable: false
  icon: fa fa-comment # Icon name in Font Awesome, set false to disable icon.
  text: Chat # Button text, change it as you wish.

# Chatra Support
# For more information: https://chatra.com
# Dashboard: https://app.chatra.io/settings/general
chatra:
  enable: false
  async: true
  id: # Visit Dashboard to get your ChatraID
  #embed: # Unfinished experimental feature for developers. See: https://chatra.com/help/api/#injectto

# Tidio Support
# For more information: https://www.tidio.com
# Dashboard: https://www.tidio.com/panel/dashboard
tidio:
  enable: false
  key: # Public Key, get it from dashboard. See: https://www.tidio.com/panel/settings/developer

# Gitter Support
# For more information: https://gitter.im
gitter:
  enable: false
  room:

# ---------------------------------------------------------------
# Tags Settings
# See: https://theme-next.js.org/docs/tag-plugins/
# ---------------------------------------------------------------

# Note tag (bootstrap callout)
note:
  # Note tag style values:
  #  - simple    bootstrap callout old alert style. Default.
  #  - modern    bootstrap callout new (v2-v3) alert style.
  #  - flat      flat callout style with background, like on Mozilla or StackOverflow.
  #  - disabled  disable all CSS styles import of note tag.
  style: simple
  icons: false
  # Offset lighter of background in % for modern and flat styles (modern: -12 | 12; flat: -18 | 6).
  # Offset also applied to label tag variables. This option can work with disabled note tag.
  light_bg_offset: 0

# Tabs tag
tabs:
  # Make the nav bar of tabs with long content stick to the top.
  sticky: false
  transition:
    tabs: false
    labels: true

# PDF tag
# NexT will try to load pdf files natively, if failed, pdf.js will be used.
# So, you have to install the dependency of pdf.js if you want to use pdf tag and make it available to all browsers.
# Dependencies: https://github.com/next-theme/theme-next-pdf
pdf:
  enable: false
  # Default height
  height: 500px

# Mermaid tag
mermaid:
  enable: false
  # Available themes: default | dark | forest | neutral
  theme:
    light: default
    dark: dark

# ---------------------------------------------------------------
# Animation Settings
# ---------------------------------------------------------------

# Use Animate.css to animate everything.
# For more information: https://animate.style
motion:
  enable: true
  async: false
  transition:
    # All available transition variants: https://theme-next.js.org/animate/
    post_block: fadeIn
    post_header: fadeInDown
    post_body: fadeInDown
    coll_header: fadeInLeft
    # Only for Pisces | Gemini.
    sidebar: fadeInUp

# Progress bar in the top during page loading.
# For more information: https://github.com/CodeByZach/pace
pace:
  enable: true
  # All available colors:
  # black | blue | green | orange | pink | purple | red | silver | white | yellow
  color: black
  # All available themes:
  # big-counter | bounce | barber-shop | center-atom | center-circle | center-radar | center-simple
  # corner-indicator | fill-left | flat-top | flash | loading-bar | mac-osx | material | minimal
  theme: material

# Canvas ribbon
# For more information: https://github.com/hustcc/ribbon.js
canvas_ribbon:
  enable: true
  size: 300 # The width of the ribbon
  alpha: 0.4 # The transparency of the ribbon
  zIndex: -1 # The display level of the ribbon

# ---------------------------------------------------------------
# CDN Settings
# See: https://theme-next.js.org/docs/advanced-settings/vendors
# ---------------------------------------------------------------

vendors:
  # The CDN provider of NexT internal scripts.
  # Available values: local | jsdelivr | unpkg | cdnjs | custom
  # Warning: If you are using the latest master branch of NexT, please set `internal: local`
  internal: local
  # The default CDN provider of third-party plugins.
  # Available values: local | jsdelivr | unpkg | cdnjs | custom
  # Dependencies for `plugins: local`: https://github.com/next-theme/plugins
  plugins: jsdelivr
  # Custom CDN URL
  # For example:
  # custom_cdn_url: https://cdn.jsdelivr.net/npm/${npm_name}@${version}/${minified}
  # custom_cdn_url: https://cdnjs.cloudflare.com/ajax/libs/${cdnjs_name}/${version}/${cdnjs_file}
  custom_cdn_url:

# Assets
# Accelerate delivery of static files using a CDN
# The js option is only valid when vendors.internal is local.
css: css
js: js
images: images

# Waline
# For more information: https://waline.js.org, https://github.com/lizheming/waline
waline:
  enable: true
  avatarCDN: https://sdn.geekzu.org/avatar/
  serverURL: https://waline-qmkdgwexn-ivy-lun.vercel.app/ # Waline server address url
  placeholder: "请在评论时在上面留下昵称和邮箱哦😊" # Comment box placeholder
  avatar: robohash # Gravatar style
  meta: [nick, mail, link] # Custom comment header
  pageSize: 10 # Pagination size
  lang: zh-cn # Language, available values: en, zh-cn
  visitor: false # Article reading statistic
  comment_count: true # If false, comment count will only be displayed in post page, not in home page
  requiredMeta: [] # Set required fields: [nick] | [nick, mail]
  libUrl: # Set custom library cdn url
```

#### 2.花里胡哨的配置

**==一些稍微高级点的配置教程==**

**（1）添加 waline 评论系统**

具体文档请看——>[Waline 官网](https://waline.js.org/)，按照官网教程配置后端。

配置完成后，在站点根目录打开命令执行下面的命令，安装 waline 插件最新版本：

```bash
npm install @waline/hexo-next --save
```

随后在主题配置文件中引入 waline：

```yaml
# Waline
# For more information: https://waline.js.org, https://github.com/lizheming/waline
waline:
  enable: true
  serverURL: https://waline.example.com # 在这里粘贴你获得的评论地址
  placeholder: "Just go" # 这里是评论框里显示的文字
  avatar: mm # 头像
  meta: [nick, mail, link] # Custom comment header
  pageSize: 10 # Pagination size
  lang: zh-cn # Language, available values: en, zh-cn
  visitor: false # Article reading statistic
  comment_count: true # If false, comment count will only be displayed in post page, not in home page
  requiredMeta: [] # Set required fields: [nick] | [nick, mail]
  libUrl: # Set custom library cdn url
```

如果 avatar 无法使用，可以直接在 waline 的配置中添加 gravatar 的国内 cdn：

```yaml
https://sdn.geekzu.org/avatar/
```

**（2）彩色标签云**

在`/themes/next/layout/`目录下，新增`tag-color.njk 文件，加入下方代码：

```html
<script type="text/javascript">
  var alltags = document.getElementsByClassName("tag-cloud-tags");
  var tags = alltags[0].getElementsByTagName("a");
  for (var i = tags.length - 1; i >= 0; i--) {
    var golden_ratio = 0.618033988749895;
    var s = 0.5;
    var v = 0.999;
    var h = golden_ratio + Math.random() * 0.8 - 0.5;
    var h_i = parseInt(h * 6);
    var f = h * 6 - h_i;
    var p = v * (1 - s);
    var q = v * (1 - f * s);
    var t = v * (1 - (1 - f) * s);
    var r, g, b;
    switch (h_i) {
      case 0:
        r = v;
        g = t;
        b = p;
        break;
      case 1:
        r = q;
        g = v;
        b = p;
        break;
      case 2:
        r = p;
        g = v;
        b = t;
        break;
      case 3:
        r = p;
        g = q;
        b = v;
        break;
      case 4:
        r = t;
        g = p;
        b = v;
        break;
      case 5:
        r = v;
        g = p;
        b = q;
        break;
      default:
        r = 1;
        g = 1;
        b = 1;
    }
    tags[i].style.background =
      "rgba(" +
      parseInt(r * 255) +
      "," +
      parseInt(g * 255) +
      "," +
      parseInt(b * 255) +
      "," +
      0.5 +
      ")";
  }
</script>

<style>
  .tag-cloud-tags {
    text-align: center;
    counter-reset: tags;
  }
  .tag-cloud-tags a {
    display: inline-block;
    border: 0px;
    border-radius: 10px;
    padding: 0px 10px;
    margin: 8px;
    color: rgba(34, 34, 34, 0.8);
  }
  /* 文字前添加相应的符号，content后的Unicode可以自定义*/
  .tag-cloud-tags a:before {
    font-family: "Font Awesome 5 Free";
    content: "\f02b";
    font-weight: 900;
  }

  .tag-cloud-tags a:hover {
    box-shadow: 0px 5px 15px 0px rgba(0, 0, 0, 0.4);
    transform: scale(1.1);
    transition-duration: 0.15s;
  }
</style>
```

在/themes/next/layout/page.swig/中引入 tag-color.swig：

在下方加上 `{% include 'tag-color.swig' %}` 代码

```yaml
<div class="post-body{% if page.direction and page.direction.toLowerCase() === 'rtl' %} rtl{% endif %}">
    {%- if page.type === 'tags' %}
          {%- include '_partials/page/tags.njk' -%}
    {% elif page.type === 'categories' %}
      {%- include '_partials/page/categories.njk' -%}
    {% elif page.type === 'schedule' %}
      {%- include '_partials/page/schedule.njk' -%}
    {% else %}
      {{ page.content }}
    {%- endif %}
    {%- include 'tag-color.njk' %} #这里是添加的代码
</div>
```

修改文章底部标签样式

打开 themes/next/layout/\_macro/post.njk，找到以下代码并修改：

```twig
- {%- set tag_indicate = '<i class="fa fa-tag"></i>' if theme.tag_icon else '#' %}
+ {%- set tag_indicate = '<i class="fa fa-tag"></i>' if theme.tag_icon else '<i class="fa fa-tag"></i>' %}
```

**（3）启用圆角**

打开 next/source/css/\_variables/Gemini.styl，将以下两行代码取消注释：

```twig
// $border-radius-inner     = 0 0 3px 3px;
// $border-radius           = 3px;
```

并修改为：

```twig
$border-radius-inner     = 25px 25px 25px 25px;
$border-radius           = 25px;
```

即可启用大圆角，如不喜欢可以自行修改上面的值。

**（4）更改鼠标指针**

找到 themes/next/source/css/\_variables/Gemini.styl，添加如下代码：

```css
* {
  cursor: url(https://deerblog.xyz/blog-image/Arrow.cur), auto;
}
:link {
  cursor: url(https://deerblog.xyz/blog-image/Hand.cur), auto;
}
```

**（5）添加全站美化元素**

找到文件 themes/next/layout/\_partials/footer.njk，在末尾添加以下代码：

```html
{# 樱花飘落 #}
<script src="https://cdn.jsdelivr.net/gh/wallleap/cdn@latest/js/sakura.js"></script>
{# 星星跟随坠落 #}
<script src="https://cdn.jsdelivr.net/gh/cungudafa/cdn@2.1.2/js/cursor.js"></script>
{# 搞怪标题 #}
<script src="https://cdn.jsdelivr.net/gh/wallleap/cdn@latest/js/hititle.js"></script>
{# 爱心 #}
<script src="https://cdn.jsdelivr.net/gh/wallleap/cdn/js/love.js"></script>
```
