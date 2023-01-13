# 主题配置

## 配置文件 async.yml

约定 ＞ 配置

::: danger
请在 `_config.async.yml` 中定义您所需要的配置，其余将自动使用主题的默认配置。

如未特殊说明，皆默认在 `_config.async.yml` 文件中配置。

请最好**不要**对**主题的任何文件**进行修改，除非您确认您拥有一定的开发能力或此后将不会对主题进行升级。
:::

## 语言 Language
本主题内置了中英文两种语言，`zh-Hans` 和 `en`。

> 站点的语言需要自己在 Hexo 目录下的 `_config.yml` 中设置。

```yaml
language: zh-Hans
```
### 个性化语言包

在 Hexo 工作目录下新建 `source/_data/languages.yml`。（若 `source/_data` 目录不存在，请新建。）

采用约定大于配置的方式，您仅需在 `languages.yml` 中自定义您想要覆盖的语言，其余将自动与主题默认配置合并。（这样做也更方便日后的升级）

配置方式参考下例：

> 各语言对应属性和内容见 [languages | hexo-theme-async](https://github.com/MaLuns/hexo-theme-async/blob/master/languages/)，覆盖对应项即可。

```yaml
# 将要覆盖的语言
en:
  site:
    title: Site Information

zh-Hans: 
  site:
    title: 本站信息

# 你也可以扩展其他语言
```

如果仅使用中文语言，除 `zh-Hans` 项均可删除。


## 主题模式 ThemeMode
- `default`：设置主题默认模式
  - `style-light`：亮色模式
  - `style-dark`：暗色模式
  - `auto`：跟随系统选择
- `switch`：如果为 false，将不会出现主题切换按钮，只加载设置默认主题模式。
``` yaml
theme: 
  switch: true 
  default: style-light 
```

## 网站图标 Favicon
用于 logo、icon、PWA 安装图标配置。

- `logo`：顶部 logo
- `icon16`：icon 16*16
- `icon32`：icon 32*32
- `appleTouchIcon`：iOS 添加到桌面是图标
- `webmanifest`：应用程序清单文件
- `visibilitychange`：是否在离开窗口时切换标题显示
- `hidden`：离开窗口时显示图标
- `show_text`：激活窗口时显示文字
- `hide_text`：离开窗口显示文字

``` yaml
favicon:
  logo: favicon-32x32.png
  icon16: favicon-16x16.png 
  icon32: favicon-32x32.png
  appleTouchIcon: apple-touch-icon.png
  webmanifest: /site.webmanifest
  visibilitychange: true
  hidden: failure.ico
  show_text: (/≧▽≦/)咦！又好了！
  hide_text: (●—●)喔哟，崩溃啦！
```

## CDN
Content Delivery Network，统一加载网络资源，有利于提高网页加载速度。

当您需要添加三方插件来个性您的博客时，您应该优先使用 CDN 加载文件。

JavaScript 资源类型说明：
- `head`: 插入到 head，其他三种默认时插入到 body 结尾的。
- `base`: 立即加载并执行。
- `async`: 异步加载，加载完成后立即执行。
- `defer`: 异步加载资源，但最后执行。

``` yaml
cdn:
  css: 
  js:
    head:
    base: 
    async: 
    defer: 
```

## 图标 Icon
本主题默认使用 Font Awesome 5 图标。

> 默认支持的图标列表见 [默认图标](/about/icon.html)

如您想要使用其他图标，只需要在 `assets.icons` 中配置您的图标。

- `type`：图标类型 `font` `symbol`
- `css`： font-class 图标资源 url （有值或为空时，将覆盖或去除内置 Font Awesome 5 图标）
- `js`：多色图标资源 url 

``` yaml
assets:
  icons: 
    type: font # font symbol
    css: 
    js:
```
### [iconfont](https://www.iconfont.cn/)

阿里旗下，可定制自己所需图标集。国内速度良好。（推荐） [使用说明](https://www.iconfont.cn/help/detail?helptype=code)

``` yaml {5}
assets:
  icons: 
    type: font 
    # 这里是您从 iconfont 处获得的图标链接。
    css: //at.alicdn.com/t/font_383361_cfn4m13f4v.css
    js:
```

多色图标使用方式：

``` yaml {3,5}
assets:
  icons: 
    type: symbol 
    css: 
    js: //at.alicdn.com/t/font_383361_cfn4m13f4v.js
```

::: warning
当您覆盖内置图标资源时，因为博客 UI 中一些固定的图标使用到了，所以您需要将 [固定图标](#自定义图标-icon) 进行修改。

单色图标 和 多色图标是可以同时使用的，但是博客 UI 固定图标只能根据 `type` 决定使用哪一种。
:::

## 用户信息 User

用户基本信息，用于博主名称、头像、友链交换规则、站点运行计时等等。
 
- `name`：昵称，用于侧栏或其他区域标识
- `first_name`：名，用于顶部将姓和名分别显示
- `last_name`：姓，
- `email`：邮箱
- `domain`：域名
- `avatar`：头像
- `describe`：网站简介
- `ruleText`：友链交换规则
- ~~`birthDay`：博客计时开始时间 v1.1.7 弃用~~
- ~~`copyrightYear`：版权日期 v1.1.7 弃用~~

``` yaml
user:
  name: 白云苍狗
  first_name: 苍狗
  last_name: 白云
  email: admin@imalun.com
  domain: https://www.imalun.com
  avatar: /img/avatar.jpg
  describe: 网站简介。
  ruleText: 暂不接受个人博客以外的友链申请，确保您的网站内容积极向上，文章至少30篇，原创70%以上，部署HTTPS。
```

## 导航栏 TopBars

顶部导航的 logo 在 [favicon](#favicon) 中配置，主题切换按钮在 [主题模式](#主题模式) 中配置。

- `title`：标题
- `url`：路径
- `noswup`：不使用局部刷新
- `target`：打开链接方式，和 a 标签属性一致
- `children`：二级菜单 
``` yaml
top_bars:
  - title: home
    url: /
    children:
      - title: archives2
        url: /archives2/
  - title: archives
    url: /archives/
    noswup: true
```

## 侧栏 Sidebar

### 社交图标
默认内置 Font-Awesome Brand 图标，可根据您的需求添加，您可以通过在头部引入自定义图标资源来获取更多图标。

- `name`：链接名称
- `icon`：图标 class
- `url`：链接

``` yaml
sidebar:
  social:  # 社交地址
    - name: github
      icon: fab fa-github   
      url: https://github.com 
    - name: gitee
      icon: iconfont cg-gitee
      url: https://gitee.com
```

如果您不想放置任何链接，仅需在 `sidebar` 中设置：

``` yaml
sidebar:
  social: 
```

### 打字动画
- `typedTextPrefix`：为固定前缀
- `typedText`：为打字效果切换条目，可设置多条，按顺序切换。
``` yaml
sidebar:
  typedTextPrefix: I`m
  typedText: [ 'Web Developer' ]
```

### 侧栏信息
侧栏信息是一个数组，里面元素 key-val 形式的。

``` yaml
sidebar:
  info: # 个人信息 
    - key: 地址
      val: 火星
    - key: 年龄
      val: 18
```

## 横幅 Banner
每个页面横幅都可以自定义不同背景图、标语等

- `default`：默认配置
    - `type`：横幅类型 img、slideshow、video
    - `bgurl`：背景图地址，如果 type 是 slideshow，需要为数组
    - `bannerTitle`：横幅上标题
    - `bannerText`：横幅描述
- `index`：首页 (属性字段和上面保持一致)
    - `videoUrl`：视频地址 (仅首页有)
- `archive`：分类页
- `links`：友链页
- `comment`：评论页
- `about`：关于

``` yaml
banner:
  index:
    type: img
    bgurl: https://pic1.zhimg.com/v2-b3c2c6745b9421a13a3c4706b19223b3_r.jpg?source=1940ef5c
    bannerTitle: 树深时见鹿，<br>溪午不闻钟。
    bannerText: Hi my new friend!
```

## 页脚 Footer
此配置在 `v1.1.7+` 新增，以前版本在 [用户信息-user](#用户信息-user) 配置。

### 起始年份
``` yaml
footer:
  copyrightYear: 2020
```

### 驱动
自豪地显示当前使用的博客框架 Hexo 与主题 Yun 的名字及版本。

如：`由 Hexo 驱动 v5.4.2 | 主题 - Async v1.1.6`

让更多人知道 Hexo 与主题 Async，这有利于开源社区进一步发展。

``` yaml {3}
footer:
  powered:
    enable: true
```

### 备案

国内用户可以提供备案号，开启备案显示。

备案信息默认链接为：<https://beian.miit.gov.cn/>

- `enable`: 开启备案
- `icp`: 备案号

```yaml
footer:
  beian:
    enable: true
    icp: 苏ICP备xxxxxxxx号
```

### 运行时间

默认关闭。

`本博客已萌萌哒地运行 442 天`

```yaml
footer:
  live_time:
    enable: false
    prefix: footer.tips
    start_time: 04/10/2022 17:00:00
```

### 自定义文本

`custom_text` 为自定义页脚，可以包含 HTML。
譬如有时使用其他服务商进行托管页面，或一些 ICP 之外的备案信息。

```yaml
footer:
  custom_text: Hosted by <a href="https://github.com" rel="noopener" target="_blank">Github Pages</a>
```

## 文章 Article

这里是一些关于文章相关配置合集。

### 打赏 Reward

开启后，将在每篇文章 `post` 末尾显示打赏按钮。

- `enable`: 开启打赏
- `comment`: 在打赏按钮下显示你想说的话
- `url`: 你的打赏链接（当你开启打赏链接时，将自动跳转你的外部链接而不是展开二维码）
- `methods`: 数组，打赏方式

#### 打赏二维码

- `name`: 打赏方式
- `path`: 图片路径

在 `_config.async.yml` 中进行覆盖。

```yaml
reward:
  enable: true
  comment: I'm so cute. Please give me money.
  methods:
    - name: 支付宝
      path: 二维码地址
```

您也可以在某篇文章的首部单独设置是否开启打赏。

```yaml
reward: true
# reward: false
```

### 文章目录

文章详情页目录，默认关闭。开启后，您可以在文章页单独配置当前文章关闭。[参考这里](/guide/page.html#文章-posts)

``` yaml 
is_toc: true
```

### 图片懒加载

默认开启，将会为 Markdown 的图片 img 加上 loading="lazy" 属性。

``` yaml
lazyload:
  enable: true
```

### 归档页

默认下归档页时间轴卡片显示了标题和摘要信息，如果设置为 `less` 将只显示标题。

- `type`: 显示方式，可选 `more` || `less`

``` yaml
archive:
  type: more # less more
```

### 版权信息

设置您的文章的分享版权

> [关于许可协议](https://creativecommons.org/licenses/)
> 默认使用 署名-非商业性使用-相同方式共享 4.0，即 [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.zh)。


- `license`：设置证书 (by | by-nc | by-nc-nd | by-nc-sa | by-nd | by-sa | zero)
- `language`：设置语言 (deed.zh | deed.en | deed.ja ｜ ...)
- `post`：在每篇文章末尾显示
- `clipboard`：是否在复制文章时，在剪贴板中追加版权信息（默认关闭）

```yaml
creative_commons:
  license: by-nc-sa
  language: deed.zh
  post: false
  clipboard: false
```

> 你的 `url` 请在 Hexo 工作目录下的 `_config.yml` 中设置。
> [配置｜ Hexo](https://hexo.io/zh-cn/docs/configuration#%E7%BD%91%E5%9D%80)

```yaml
# URL
# # If your site is put in a subdirectory, set url as 'https://yoursite.com/child' and root as '/child/'
url: https://www.imalun.com
```

## 自定义图标 Icon
博客中存在一些固定的图标，譬如主题切换图标、分类图标等。

可以通过配置 `icons` 修改：

``` yaml
icons:
  # 主题切换图标
  sun: far fa-sun
  moon: far fa-moon
  # 首页视频播放
  play: fas fa-play
  # 邮箱
  email: far fa-envelope
  # 分类进入图标
  next: fas fa-arrow-right
  # 文章详情 日期
  calendar: far fa-calendar-alt
  # 文章详情 时间
  clock: far fa-clock
  # 文章详情 作者
  user: far fa-user
  # 返回顶部 v1.1.3+
  back_top: fas fa-arrow-up
  # 查询 v1.1.5+
  search: fas fa-search
  # 关闭 v1.1.5+
  close: fas fa-times
  # 打赏 v1.1.7+
  reward: fas fa-hand-holding-usd
```

## 自定义样式 Style

相比 `head` 引入，您可以直接编写 `less` 文件，并使用主题已有的变量，且将和主题样式文件一起编译。

- 新建 `source/_data/style/dark.less`、`source/_data/style/light.less`，开始编写你的自定义样式了。他们分别默认会合并到 `dark`、`light` 两种模式中去。
- 如果需要覆盖变量可以添加 `source/_data/style/dark.variables.less`、`source/_data/style/light.variables.less`，进行覆盖。

```text {4,5,6,7,8}
┌── blog                     
│   └── source
│       └── _data
│           └── style
│               ├── dark.less
│               ├── light.less
│               ├── dark.variables.less
│               └── light.variables.less
│   └── themes
```

## 渐进式应用 PWA

开始 PWA 只需要设置 sw 为 true 即可，本主题已添加 Server Worker 相关操作 。

``` yaml
sw: true
```
::: warning
使用 PWA 要求
- 站点必须为 HTTPS。
- 添加一个清单文件（manifest)，直接在 `source` 下新增。
:::

清单文件 结构
``` json
{
    "name": "白云苍狗",
    "short_name": "白云苍狗",
    "description": "描述",
    "icons": [
        {
            "src": "/android-chrome-192x192.png",
            "sizes": "192x192",
            "type": "image/png"
        },
        // ...
        {
            "src": "/android-chrome-512x512.png",
            "sizes": "512x512",
            "type": "image/png"
        }
    ],
    "theme_color": "#fff",
    "background_color": "#fff",
    "display": "standalone",
    "start_url": "/"
}
```

## 更多配置

你可以直接查看 [\_config.yml ｜ hexo-theme-async](https://github.com/MaLuns/hexo-theme-async/blob/master/package/hexo-theme-async/_config.yml) 文件及相关注释。