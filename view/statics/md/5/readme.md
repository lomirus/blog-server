# 更新日志 （2020/11/25 ~ 2021/1/10）

初始创建于：***2020/11/25***

最后编辑于：***2021/01/10***

## 2021/1/10

最近由于期末考试以及开发重点的暂时性转移，所以最近可能更新的比较少qaq

### 更新内容

* 增加了管理员前台查询碎语 `id` 的功能；

### 已知问题

* 在边缘点击导航栏的按钮会导致点击失效（问题原因已知）；

### 开发计划

* 为文章添加目录；
* 主页增加搜索栏；
* 将更新日志独立；
* 增加回到顶部按钮；
* 优化代码结构（前端&后端）；
* 预防 SQL 注入等；

## 2021/1/3

### 更新内容

* 将服务器请求方式由 `XHR` 改为 `Fetch`；
* 将传输评论的方式由 url 中的 `query` 改为 body 中的 `json`；
* 后端增加对评论的二次检测，防止用户绕过对评论、用户名是否为空的 JS 检测以提交评论；
* 将评论提示语、评论编辑区提示语、修改头像提示语、提交按钮的显示文本统一改为中文；
* 优化了匿名用户提交评论的逻辑：若用户提交评论时没有输入用户名，系统不会将”匿名用户“作为用户名保存到本地；
* 优化了更改头像的逻辑：更改头像后自动保存，无需像之前一样需提交评论后才可保存；
* 优化了更改头像的逻辑：更改头像前检测头像地址是否有效，若无效则提示更改失败；

### 已知问题

* 在边缘点击导航栏的按钮会导致点击失效（问题原因已知）；

### 开发计划

* 为文章添加目录；
* 主页增加搜索栏；
* 将更新日志独立；
* 增加回到顶部按钮；
* 优化代码结构（前端&后端）；
* 预防 SQL 注入等；

## 2021/1/2

### 更新内容

* 优化了修复图片地址的方式：改为先使用 Regex 自动替换 Markdown 代码，然后再进行渲染；
* 优化了行内公式的解析与渲染，同时修复了行内数学公式存在灰色背景的问题；
* 优化了块级公式的解析与渲染，取消了自己造的 Markdown 方言解析轮子，统一为 Markdown 语法，并且使标签更趋语义化；

### 已知问题

* 在边缘点击导航栏的按钮会导致点击失效（问题原因已知）；

### 开发计划

* 为文章添加目录；
* 主页增加搜索栏；
* 将更新日志独立；
* 增加回到顶部按钮；
* 优化代码结构（前端）；
* 后端增加评论二次检测（防止用户可通过绕过对评论、用户名是否为空的 JS 检测）

## 2021/1/1

### 优化内容

* 优化了后端架构（优化了后端代码之后，现在又开始感觉前端的 JS 代码又丑又乱了...以后也顺便再优化一下前端的吧）；
* 修改解析 markdown 的方式为`marked.js`；
* 优化了文章页面内链接的显示颜色；

### 修复内容

* 修复了`onblur`与`onclick`冲突导致`nav`中按钮点击无效的 bug；
* 通过某种并不怎么优雅的方式修复了存在图片的文章页面内控制台会报错的问题（修复原理是在客户端还没来得及请求错误地址之前就把它改成正确地址，以后有空的话再采用尽量更优雅点的方式来修复）；

### 已知问题

* 在边缘点击导航栏的按钮会导致点击失效（问题原因已知）；
* 行内数学公式存在灰色背景（问题原因已知）；

### 开发计划

* 为文章添加目录；
* 主页增加搜索栏；
* 将更新日志独立；
* 增加回到顶部按钮；
* 优化代码结构（前端）；

## 2020/12/31

### 修复内容

* 修复了点开导航栏有时会缺失过渡动画的问题

### 已知问题

* 在边缘点击导航栏的按钮会导致点击失效（问题原因已知）
* 行内数学公式存在灰色背景（问题原因已知）
* 存在图片的文章页面内控制台会报错（问题原因已知）

### 开发计划

* 为文章添加目录；
* 主页增加搜索栏；
* 修改解析 markdown 的方式为`marked.js`；
* 将更新日志独立；
* 增加回到顶部按钮；
* 优化代码结构（前端&后端）

## 2020/12/30

### 开发内容

* 增加了目录框，但目前其内无内容；
* 主页增加了备案信息；

### 已知问题

* 点开导航栏有时会缺失过渡动画（问题原因已知）
* 在边缘点击导航栏的按钮会导致点击失效（问题原因已知）

### 开发计划

* 为文章添加目录；
* 修复导航栏有时会出现缺失动画、点击失效的问题，并确保仍可选中导航栏下层文字；
* 主页增加搜索栏；
* 修改解析 markdown 的方式为`marked.js`；
* 将更新日志独立；
* 增加回到顶部按钮。

## 2020/12/27

### 开发内容

* 修改`选项`按钮为`≡`按钮;
* 缩小了文章页面的封面滑动距离；
* 修复了文章页面中遮罩层图片有时被意外选中影响观看且无法取消选中的问题；
* 修复了导航按钮会遮住`imgMask`影响观看的问题；

### 开发计划

* 为文章添加目录；
* 修复导航栏有时会出现缺失动画、点击失效的问题，并确保仍可选中导航栏下层文字；
* 主页增加搜索栏；
* 修改解析 markdown 的方式为`marked.js`；
* 将更新日志独立；
* 增加回到顶部按钮。

## 2020/12/26

### 开发内容

* 将导航区域由侧边栏改为悬浮按钮样式，同时统一了目录按钮；
* 优化了文章界面；

![20-12-26-1](20-12-26-1.png)

* 优化了文章页面的图片的宽度适应机制，防止有些图片强行放大导致影响观感

### 开发计划

* 为文章添加目录；
* 主页增加搜索栏；
* 升级 blackfriday 为 v2；
* 将更新日志独立；
* 评论区域下方增加回到顶部按钮。

## 2020/12/18

### 开发内容

* 文章页面内增加了目录按钮（暂时不能使用）；
* 修复了在 Firefox 中响应式布局的临界值无效等问题，同时进一步重构并优化了响应式布局的相关代码；

### 开发计划

* 为文章添加目录；
* 主页增加搜索栏；
* 升级 blackfriday 为 v2；
* 为侧边栏的阴影遮罩层添加淡入淡出动画；
* 将更新日志独立；
* 评论区域下方增加回到顶部按钮。

## 2020/12/17

### 开发内容

* 文章页面内的标题支持锚点跳转，并增加相应特效；

![20-12-17-1](20-12-17-1.png)

* 文章页面内的`Header`会在用户进行锚点跳转或向下滚动时自动隐藏，在向上滚动时重新出现；
* 使用 CSS 的媒体查询重写了响应式布局的实现方式；
* 修改“只言”的名称为“碎语”

### 开发计划

* 为文章添加目录；
* 主页增加搜索栏；
* 升级 blackfriday 为 v2；
* 为侧边栏的阴影遮罩层添加淡入淡出动画
* 评论区域下方增加回到顶部按钮。

## 2020/12/16

### 开发内容

* 文章页面通过`Katex`增加了对数学公式解析的支持（感谢`Victor`大佬的指导）

![20-12-16-1](20-12-16-1.png)

* 文章页面增加了`header`与侧边栏；

![20-12-16-2](20-12-16-2.png)

* 文章页面背景、排版、自适应逻辑进一步优化。

![20-12-16-3](20-12-16-3.png)
![20-12-16-4](20-12-16-4.png)

### 开发计划

* 为文章添加目录；
* 主页增加搜索栏；
* 升级 blackfriday 为 v2；
* 为侧边栏的阴影遮罩层添加淡入淡出动画
* 评论区域下方增加回到顶部按钮。

## 2020/12/14

### 开发内容

* 删除了“只言”页面的管理员后台管理页面，改为通过 API 方式访问；
* 增加了修改“只言”内容的 API；
* 对修改“只言”内容的 API 增加了 Cookie 鉴权，并做了一个小彩蛋；
* 增加了设置 Cookie 的 API；
* “只言”现已可获取地理位置（手动添加）；
* 修复了“只言”页面内卡片会正序显示的 feature；
* 减小了“只言”页面内卡片的间距；
* 优化侧边栏逻辑，去除了侧边栏隐藏状况下 url 中的无用 query，使 url 得以缩短
* 优化了评论成功后的通知逻辑，防止无通知权限时无法告知用户，同时使代码更趋于规范。

### 开发计划

* 为文章添加目录；
* 为文章添加侧边栏；
* 主页增加搜索栏；
* 为侧边栏的阴影遮罩层添加淡入淡出动画
* 评论区域下方增加回到顶部按钮。

## 2020/12/13

### 开发内容

* 增加了“只言”页面；
* 其他细节修改及重构。

![](9.png)

### 开发计划

* 只言可以检测地理位置（目前是无论在哪儿发都是重庆）；
* 管理员后台给弄个加密；
* 为文章添加目录；
* 为文章添加侧边栏；
* 主页增加搜索栏；
* 为侧边栏的阴影遮罩层添加淡入淡出动画
* 评论区域下方增加回到顶部按钮。

## 2020/12/12

### 开发内容

* 主页和关于页面去除了顶栏链接设计，改为侧边栏（防止以后出现更多链接导致顶栏空间不足而被占满）；
* 顶栏定位方式由`absolute`改为`fixed`；
* 侧边栏中增加了新分类，内容暂时为空。

![](8.png)

* 修复了在首页中屏幕尺寸放大时可能导致封面图片无法加载的 bug。

### 开发计划

* 评论区域下方增加回到顶部按钮；
* 主页文章卡片增加创建时间；

## 2020/12/09

### 开发内容

* Markdown 文件的解析方式更改：
	* 以前：传输 Markdown 源代码至客户端，再在前端通过 marked.js 进行解析；
	* 现在：先在后端通过 blackfriday 进行解析，然后通过 template 直接返回解析好的 HTML 源代码。

### 开发计划

* 评论区域下方增加回到顶部按钮；
* 主页文章卡片增加创建时间；

## 2020/12/05

### 开发内容

* 增加了顶赞操作时“Like”图标随目前赞数正负而不同的特效（共四种）;
* “Like”赞数改为通过伪元素显示;
* 对不存在的文章页面返回 404；
* 将通知页面更改为关于页面，并增加了友链

### 开发计划

* 评论区域下方增加回到顶部按钮；
* 主页文章卡片增加创建时间；

## 2020/12/04

### 开发内容

对评论界面进行大幅优化，细节过多，难以记述，建议直接看图：

![7](7.png)

图中未直接表现出来的功能列举如下：

* 可自定义用户名，头像，并可保存在本地；
* 顶踩按钮增加鼠标悬浮特效；
* 输入框与提交按钮增加鼠标悬浮特效；
* “Like”图标会随赞数正负而改变（红心与心碎）；
* 顶赞操作时“Like”图标会出现特效，并随是否为赞或踩而产生速度上的不同（共两种）

### 开发计划

* 评论区域下方增加回到顶部按钮；
* 在关于页面增加友链（虽然目前并没有）；
* 主页文章卡片增加创建时间；

## 2020/12/03

### 开发内容

* 优化了 markdown 中引用的样式；

![5](5.png)

* 取消了评论修改时间的保存与显示，并且在低分屏下会自动隐藏评论时间只显示日期以节约空间

![6](6.png)

### 开发计划

* 评论区域下方增加回到顶部按钮；
* 在关于页面增加友链（虽然目前并没有）；
* 主页文章卡片增加创建时间；
* 完善博文的评论系统：
	* 关联用户信息；
	* 优化小屏设备的显示；
	* 优化评论界面。

## 2020/11/27

### 开发内容

* 文章页面内部封面居中显示；
* 更改文字选中时的背景样式为粉紫色（~~抄袭~~借鉴了红岩软件站）；
* 评论系统使用了 Web Notification，评论成功后显示通知消息；
* 修复了在某些临界情况下宽度足够文章页面仍显示横向滚动条的bug；

![2](2.png)
![3](3.png)
![4](4.png)

### 开发计划

* 评论区域下方增加回到顶部按钮；
* 在关于页面增加友链（虽然目前并没有）；
* 主页文章卡片增加创建时间；
* 完善博文的评论系统：
	* 关联用户信息；
	* 优化小屏设备的显示；
	* 可以删除评论。

## 2020/11/26

### 开发内容

* 优化了主页在小屏设备（主要指移动端）的显示；
* 优化了文章页面在小屏设备（主要指移动端）的显示；
* 优化了通知页面在小屏设备（主要指移动端）的显示；
* 其他多处自适应与显示的细小优化。

![1](1.png)

### 开发计划

* 评论区域下方增加回到顶部按钮；
* 在关于页面增加友链（虽然目前并没有）；
* 主页文章卡片增加创建时间；
* 完善博文的评论系统，例如关联用户信息。
* 首页预览图改为加载缩略图；
* 文章页面内部封面居中显示。

## 2020/11/25

### 开发内容

* 增加了导航栏，可以跳转至主页；
* 删除了主页中的通知栏，将其转移到单独页面，可在导航栏进行跳转；
* 稍微优化了主页的自适应，并略微调高了预览内容的加载长度（150->180）。

### 开发计划

* 评论区域下方增加回到顶部按钮；
* 在关于页面增加友链（虽然目前并没有）；
* 主页文章卡片增加创建时间；
* 完善博文的评论系统，例如关联用户信息。
* 首页预览图改为加载缩略图；
* 文章页面内部封面居中显示。












