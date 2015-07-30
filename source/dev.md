title: "自定义详情页技术规范"
---

### 兼容目标

 - 主流移动设备：iPad 2+，iPhone 4+ ，三星、魅族、华为、红米、小米1S 以上及主流 Android 千元机型；
 - 操作系统：iOS 7.0+ 与 Android 4.0+；

### 加载速度、请求数与资源压缩

 - 以 3G 网络环境 100kb/s 的网络速度计算，详情页首次加载过程中，可以在 **2s** 内看到 Loading 页面；
 - 原则上页面中不超过 1 个的样式文件请求、2 个的脚本文件网络请求；
 - 图片资源应当进行压缩，JPG 图片使用 80% 以下质量，PNG 图片使用 [TinyPNG](http://tinypng.com) 进行压缩；
 - 详情页平均单页资源不超过 300 KB，总资源包大小不超过页数乘以300KB（不包括视频资源）；
 - 应当对小图片进行 [CSS 雪碧图](https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/CSS_Image_Sprites) 合并，因低版本系统及低端设备渲染问题，单张图片尺寸不超过 2000x2000 像素，超过时需切分成多张雪碧图；

**资源文件格式标准**

| 文件类似        | 格式           | 大小       | 其它备注|
| :------------- |:-------------|:----------|:-----------------------------|
| 背景音乐        | mp3          |小于 80 KB |开头和结尾音轨建议做使用淡入淡出处理 |
| 分享缩略图      | jpg          |小于 6 KB |尺寸为 120x120 像素             |
| 视频文件        | mov/mp4/avi|暂无要求|分辨率>=960×540，视频码率>=1500kbps，画面比例 4:3或16:9 |


### 资源部署

 - 详情页应只包含静态文件资源，涉及数据交互使用 AJAX 进行数据提交；
 - 详情页所有资源上线前将部署到腾讯服务器；
 - 不允许在页面中添加非腾讯域名的资源；
 - 若页面中包括视频，自行上传视频至腾讯视频服务器，告知视频地址；

### 自测与提测申请

 - 至少提前 **5 个工作日** 提供到微信侧；
 - 提交微信团队测试前，请做好自测，并填写自测列表（[下载自测列表](http://mp.weixin.qq.com/promotion/res/standard/files/test.xls)）；
 - 微信广告测试团队将会进行全面测试，发现问题后反馈给广告客户进行优化修复，直至详情页质量符合要求；

**提测申请及部署申请邮件内容**

| 内容 | 要求|
|:-|:-|
|基本信息|公众号名称、微信号、AppID、原始ID|
|需求文档|包括功能点列表和说明，产品流程图|
|修改说明|非首次提交时，需要详细说明本次提测修复的缺陷以及修复方案|
|自测报告|报告需包含主流移动设备、主流操作系统中的测试情况，以及填写好的自测列表|
|源代码压缩包|以 ZIP 格式压缩（不得包含空文件，.svn/.git/.DS_Store/Thumbs.db/.log 等系统文件）。|
|广告详情页地址|若使用了微信授权登录，为方便测试，提供无需微信登录也可进行测试的地址|