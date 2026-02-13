Title: 迁移语雀到 Obsidian2023 年 10 月 23 日语雀崩了，还崩了几小时，挺突然的，于是花了点时间迁移到 ob - 掘金

URL Source: https://juejin.cn/post/7298314768251519011

Published: 2023-11-06T15:05:16.000Z

Markdown Content:
迁移语雀到 Obsidian2023 年 10 月 23 日语雀崩了，还崩了几小时，挺突然的，于是花了点时间迁移到 ob - 掘金
===============
![Image 1: 稀土掘金](https://lf-web-assets.juejin.cn/obj/juejin-web/xitu_juejin_web/e08da34488b114bd4c665ba2fa520a31.svg) ![Image 2: 稀土掘金](https://lf-web-assets.juejin.cn/obj/juejin-web/xitu_juejin_web/6c61ae65d1c41ae8221a670fa32d05aa.svg)

*   首页

        *   [首页](https://juejin.cn/)
        *   [沸点](https://juejin.cn/pins)
        *   [课程](https://juejin.cn/course)
        *   [数据标注 HOT](https://aidp.juejin.cn/)
        *   [AI Coding](https://aicoding.juejin.cn/)
        *   更多
                *   [直播](https://juejin.cn/live)
                *   [活动](https://juejin.cn/events/all)
                *   [APP](https://juejin.cn/app?utm_source=jj_nav)
                *   [插件](https://juejin.cn/extension?utm_source=jj_nav)
        *   [直播](https://juejin.cn/live)
        *   [活动](https://juejin.cn/events/all)
        *   [APP](https://juejin.cn/app?utm_source=jj_nav)
        *   [插件](https://juejin.cn/extension?utm_source=jj_nav)
    *       *
            *   *   写文章

                *   发沸点

                *   写笔记

                *   写代码

                *   草稿箱


                创作灵感 查看更多

    *   ## 首次登录 / 注册免费领取








# 迁移语雀到 Obsidian

[supree](https://juejin.cn/user/4283353031515646/posts)

2023-11-06 21,835 阅读6分钟

# 语雀心碎用户

事情的起因， 就是 2023 年 10 月 23 日语雀崩了，还崩了几小时 [语雀的P0事故](https://link.juejin.cn/?target=https%3A%2F%2Fwww.zhihu.com%2Fquestion%2F627448953%2Fanswer%2F3261582775 "https://www.zhihu.com/question/627448953/answer/3261582775")，虽然那段期间我没用语雀，但不免担心万一语雀突然凉了咋办，毕竟玉伯走了，还有钉钉文档这样的竞品，加上这次事故处理这么久，产生了信任危机，虽然后来做了复盘并补偿了 6 个月会员，但信任这种东西一旦崩塌就很难重新建立的，所以下定决心做一次迁移。

迁移到哪儿，目前其实就 3 个选择：

*   [notion](https://link.juejin.cn/?target=https%3A%2F%2Fwww.notion.so%2Fzh-cn%2Fproduct%3Ffredir%3D1 "https://www.notion.so/zh-cn/product?fredir=1")
*   [Obsidian](https://link.juejin.cn/?target=https%3A%2F%2Fobsidian.md%2F "https://obsidian.md/")
*   [思源](https://link.juejin.cn/?target=https%3A%2F%2Fb3log.org%2Fsiyuan%2F "https://b3log.org/siyuan/")

这几个笔记本都满足我基本的需求：写 markdown， 支持图床。但在很久之前就从印象笔记迁移到语雀了，当时印象笔记对 markdown 的支持特别差，反馈了 bug 都从不解决，当时还有一年多会员没用，于是当时就迁移了一次到语雀。notion 的功能特别强大，迁移 notion 应该是最简单，但为了避免将来又要搞一次，所以就不考虑 notion，思源和 Obsidian 都差不多，思源的上手曲线相对 Obsidian 简单些，但其文件格式非 `.md`，为了数据本地化更完整，最终选择 Obsidian，整体迁移思路如下：

![Image 3: image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/14d3bf9d805646c6af6d1e13288cd16c~tplv-k3u1fbpfcp-jj-mark:3024:0:0:0:q75.awebp#?w=706&h=851&s=31825&e=png&b=fffdfd)

# 从语雀导出所有笔记和图片

当然不可能一个个从语雀手动拷贝出来，断断续续也有百来篇笔记，所以就得考虑用工具来处理，想起当初语雀开始收费的时候，天猪写了一个脚本来着，然后抓紧翻出来看：[如何看待语雀付费策略？](https://link.juejin.cn/?target=https%3A%2F%2Fwww.zhihu.com%2Fquestion%2F562238887%2Fanswer%2F2732941385 "https://www.zhihu.com/question/562238887/answer/2732941385")，里面提到他写了一个 [工具](https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2Fatian25%2Fyuque-exporter "https://github.com/atian25/yuque-exporter") 来处理这事，于是直接下载下来使用，但发现运行起来报了各种该错误，折腾了一下没解决（这个方案需要用官方的 token，使用 token 要花钱。。。），于是重新找了一个工具：[GitHub - renyunkang/yuque-exporter: A tool for exporting Yuque documents as markdown.](https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2Frenyunkang%2Fyuque-exporter "https://github.com/renyunkang/yuque-exporter")

这个工具运行起来也是报错，但好在作者使用 chatgpt 写的，错误比较容易处理，而且采用的无头浏览器调用网页版的导出功能，不需要额外花费，于是就用这个了

![Image 4: image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/1c06c3914d434614b2ee5623b03e164c~tplv-k3u1fbpfcp-jj-mark:3024:0:0:0:q75.awebp#?w=613&h=144&s=8721&e=png&b=fefefe)

改后可以运行的脚本放在：[GitHub - zaiMoe/moveout-yuque: 语雀心碎用户](https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2FzaiMoe%2Fmoveout-yuque "https://github.com/zaiMoe/moveout-yuque") 注意，需要用 node@16 运行

导出图片的脚本我也用 chatgpt 写了一个 node 版本，运行：`npm run replace` 就行

## 上传图床

最终选择的方案是阿里云的 oss，相比腾讯 cos 便宜些，也比放在自己的服务器靠谱。 最终方案： [阿里云 oss](https://link.juejin.cn/?target=https%3A%2F%2Foss.console.aliyun.com%2Fbucket "https://oss.console.aliyun.com/bucket") \+ [picgo](https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2FMolunerfinn%2FPicGo "https://github.com/Molunerfinn/PicGo")

### 阿里云 oss 设置

首先购买一个资源包，这个可以用于存储和上传 ![Image 5: image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/ebb22ba0ae84473fb6c336b508ea3793~tplv-k3u1fbpfcp-jj-mark:3024:0:0:0:q75.awebp#?w=1015&h=836&s=56642&e=png&b=fefefe)

其次看个人需求是否购买流量包，这个是用于访问 oss 资源时的流量费用。对于个人笔记本来说，访问量很小，就不需要开了，有一定的免费额度，即使收费也不贵

![Image 6: image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/ce2099844c8d46c3b74ed2c332e2173e~tplv-k3u1fbpfcp-jj-mark:3024:0:0:0:q75.awebp#?w=2257&h=230&s=27558&e=png&b=fcfcfc)

购买后就可以创建一个 bucket，主要设置就是下面两项，其他的按需开，要收费的就不建议使用了。

![Image 7: image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/cc335d26f2654df5a537bca03de00574~tplv-k3u1fbpfcp-jj-mark:3024:0:0:0:q75.awebp#?w=1186&h=1208&s=130152&e=png&b=fefcfc)

### 配置 oss 权限

到 [阿里云的访问控制](https://link.juejin.cn/?target=https%3A%2F%2Fram.console.aliyun.com%2Fusers "https://ram.console.aliyun.com/users") 中，创建一个子用户，并未这个账户添加 oss 的权限

> 注意，创建成功的时候会显示 `AccessKey ID` 和 `AccessKey Secret` ，记得复制下来

![Image 8: image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a5f3ba17140a4fccbeb273fd6377bb4a~tplv-k3u1fbpfcp-jj-mark:3024:0:0:0:q75.awebp#?w=1234&h=589&s=40359&e=png&b=ffffff)

![Image 9: image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/2a2235fa1868478b93a6f6f93344a070~tplv-k3u1fbpfcp-jj-mark:3024:0:0:0:q75.awebp#?w=728&h=248&s=9736&e=png&b=ffffff)

然后在回到 [bucket 授权策略](https://link.juejin.cn/?target=https%3A%2F%2Foss.console.aliyun.com%2Fbucket%2Foss-cn-guangzhou%2Fzaimoe-bucket%2Fpermission%2Fpolicy "https://oss.console.aliyun.com/bucket/oss-cn-guangzhou/zaimoe-bucket/permission/policy") 中，配置好访问权限 ![Image 10: image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/b22d478675584ff691957f52dd03c2dd~tplv-k3u1fbpfcp-jj-mark:3024:0:0:0:q75.awebp#?w=964&h=638&s=29804&e=png&b=fefefe)

### 本地图片上传图床

虽然 Obsidian 的 [image-auto-upload-plugin](https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2Frenmu123%2Fobsidian-image-auto-upload-plugin%2Fblob%2Fmaster%2Freadme-zh.md "https://github.com/renmu123/obsidian-image-auto-upload-plugin/blob/master/readme-zh.md") 插件支持自动将本地文件上传到图床并替换代码中的图片，但任然需要一个个的替换，文件太多了，手动是不可能手动的，于是又用 chatgpt 写了一个工具，同样在项目中运行： `npm run upload`，当然需要改一下代码中一些配置

![Image 11: image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/03b2b826cad147f7ab85dbb27ed973b8~tplv-k3u1fbpfcp-jj-mark:3024:0:0:0:q75.awebp#?w=503&h=321&s=22213&e=png&b=1f1f1f)

## Obsidian 调试

这里主要做 2 件事情：

1.  多端同步
2.  图床使用
3.  个人偏好设置

### 多端同步

个人笔记本，就直接同步到 github 或者 gitee 就行，创建相关仓库并把文件上传上去之后，在 Obsidian 中安装 **[obsidian-git](https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2Fdenolehov%2Fobsidian-git "https://github.com/denolehov/obsidian-git")** 插件，然后设置下同步方案即可，因为我同一时间只会用一台设备，所以不用考虑过于频繁的提交，其他的按需设置：

![Image 12: image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/80d2f8416c2e4a5791b367986f9916d7~tplv-k3u1fbpfcp-jj-mark:3024:0:0:0:q75.awebp#?w=987&h=686&s=64281&e=png&b=1f1f1f)

对了，在首次提交之前，记得补充一个 .gitignore 文件，其中内容：

bash

 体验AI代码助手

 代码解读

复制代码

`.obsidian/workspace # 忽略本地个人喜好的配置`

接着可以在右上角找到这个工具，这里就像 vscode 的面板了，不详细介绍

![Image 13: image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/b88bb8d19a0f4f869209e6aeada09f8b~tplv-k3u1fbpfcp-jj-mark:3024:0:0:0:q75.awebp#?w=606&h=525&s=13313&e=png&b=252525)

如果没有可以按下： `Ctrl + P` 搜索 `git` 手动打开

![Image 14: image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/9f017a5a713944ad93b50326220f4783~tplv-k3u1fbpfcp-jj-mark:3024:0:0:0:q75.awebp#?w=903&h=206&s=11747&e=png&b=1f1f1f)

### 图床配置

#### 配置 Picgo

![Image 15: image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/39397ca7df8a4df888200e368ee49d5c~tplv-k3u1fbpfcp-jj-mark:3024:0:0:0:q75.awebp#?w=965&h=522&s=48043&e=png&b=3f3c37)

*   keyid: 就是上面创建子用户的 AccessKey ID
*   keySecret: 即 AccessKey Secret
*   设置 bucket 和 设定储存区域：打开 bucket 的 [基本信息](https://link.juejin.cn/?target=)[阿里云登录页](https://link.juejin.cn/?target=https%3A%2F%2Foss.console.aliyun.com%2Fbucket%2Foss-cn-guangzhou%2Fzaimoe-bucket%2Foverview "https://oss.console.aliyun.com/bucket/oss-cn-guangzhou/zaimoe-bucket/overview") 页面
*   设置 bucket 和 设定储存区域：打开 bucket 的 [基本信息](https://link.juejin.cn/?target=) 页面，分别对应这两个部分

![Image 16: image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e21c26e8e44343368c8458067a7a4ad9~tplv-k3u1fbpfcp-jj-mark:3024:0:0:0:q75.awebp#?w=1687&h=155&s=11309&e=png&b=ffffff)

其他的可以不填。

然后上传一张图片测试，没问题的话就能在 bucket 中看到你上传的图片了。

#### Obsidian 自动上传图片

子需要安装 [image-auto-upload-plugin](https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2Frenmu123%2Fobsidian-image-auto-upload-plugin%2Fblob%2Fmaster%2Freadme-zh.md "https://github.com/renmu123/obsidian-image-auto-upload-plugin/blob/master/readme-zh.md") 这个插件，然后上面都不要修改即可。

![Image 17: image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/f30616508b954dc8a5a5f5230c144db9~tplv-k3u1fbpfcp-jj-mark:3024:0:0:0:q75.awebp#?w=981&h=376&s=42525&e=png&b=1f1f1f)

上面说到，这个插件支持将单个文件中的图片上传，其方法是，按下 `ctrl+p` ，搜索 `upload`

![Image 18: image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/55e3cff2869d432b9b54669b45933147~tplv-k3u1fbpfcp-jj-mark:3024:0:0:0:q75.awebp#?w=857&h=236&s=12773&e=png&b=212121)

### 个人偏好设置

这一块因人而异了，我本身只是需要一个好用的 markdown 编辑器，所以不想花费太多时间研究各类插件、主题。所以这里之推荐几个我觉得还不错的插件：

#### [Obsidian Linter](https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2Fplaters%2Fobsidian-linter%23obsidian-linter "https://github.com/platers/obsidian-linter#obsidian-linter") （强烈推荐）

markdown lint 插件，虽然 Obsidian 本身是类似 Typro 那种同步渲染的，但这种模式下，源 markdwon 格式可能会很乱，而且为了保证一些书写习惯还得自己记忆，比如我习惯单词、数字前后有空格，这个插件就非常适合了，能让我更加专注写文档而不用考虑样式，因此十分推荐

安装完成之后，除了默认设置，建议开启下面几个：

![Image 19: image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/19a63d9f42db4eef95b09aa2bbfea41a~tplv-k3u1fbpfcp-jj-mark:3024:0:0:0:q75.awebp#?w=985&h=147&s=22049&e=png&b=1e1e1e) ![Image 20: image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/75f21e4169b6477aba83d7b4e7486c20~tplv-k3u1fbpfcp-jj-mark:3024:0:0:0:q75.awebp#?w=1008&h=219&s=23899&e=png&b=1e1e1e)

![Image 21: image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/5a0022cf3c344dd28b813d526ad9c516~tplv-k3u1fbpfcp-jj-mark:3024:0:0:0:q75.awebp#?w=978&h=281&s=37774&e=png&b=1e1e1e)

另外单词拼写检查可以在这里开启，不需要在这个插件中开启了

![Image 22: image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/57f51ef7c22947eab4889c5d9b64acd8~tplv-k3u1fbpfcp-jj-mark:3024:0:0:0:q75.awebp#?w=1334&h=389&s=49406&e=png&b=202020)

#### [Obsidian Auto Link Title](https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2Fzolrath%2Fobsidian-auto-link-title%23obsidian-auto-link-title "https://github.com/zolrath/obsidian-auto-link-title#obsidian-auto-link-title")

粘贴链接会自动显示链接标题，非常好用。

![Image 23: auto-link-title.gif](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/2bb3c89fc9e4495fa1b61c69ef1d7cd1~tplv-k3u1fbpfcp-jj-mark:3024:0:0:0:q75.awebp#?w=670&h=476&s=53150&e=gif&f=148&b=1e1e1e)

#### [Advanced Tables for Obsidian](https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2Ftgrosinger%2Fadvanced-tables-obsidian%23advanced-tables-for-obsidian "https://github.com/tgrosinger/advanced-tables-obsidian#advanced-tables-for-obsidian")

表格美化，写 markdown 的同学都知道表格多麻烦

![Image 24: formulas-demo.gif](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/bb123ff08915490d9011a109758ff51e~tplv-k3u1fbpfcp-jj-mark:3024:0:0:0:q75.awebp#?w=676&h=337&s=292905&e=gif&f=170&b=1c1c1c)

#### [obsidian-editing-toolbar Plugin](https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2FPKM-er%2Fobsidian-editing-toolbar%23obsidian-editing-toolbar-plugin "https://github.com/PKM-er/obsidian-editing-toolbar#obsidian-editing-toolbar-plugin")

就是一个工具栏，很多快捷键记不住，方便使用

![Image 25: image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/96c3e116b7df41f2a183f8a4a055c4ab~tplv-k3u1fbpfcp-jj-mark:3024:0:0:0:q75.awebp#?w=1333&h=138&s=13016&e=png&b=212121)

## 总结

为了笔记数据的安全，从语雀迁移到了 Obsidian 中，本身只是需要一个能舒服写 markdown 的编辑器，因此不要太多折腾就达到了要求。所以如果写作需求比较小，可以尝试这种简易的方案，通过一些插件，写 markdown 体验会挺好的，当然如果不想折腾就直接用 notion 吧

标签：

[GitHub](https://juejin.cn/tag/GitHub)[前端](https://juejin.cn/tag/%E5%89%8D%E7%AB%AF)

评论 58

![Image 26: avatar](https://lf-web-assets.juejin.cn/obj/juejin-web/xitu_juejin_web/58aaf1326ac763d8a1054056f3b7f2ef.svg)

0 / 1000

标点符号、链接等不计算在有效字数内

⌘ + Enter

 即可发布评论！

最热

最新

[![Image 27: 犹如那海边的头像](https://p6-passport.byteacctimg.com/img/user-avatar/862c569183ccc43a45601f333a6c96b3~200x200.awebp)](https://juejin.cn/user/2682464100695389/robots)

[犹如那海边](https://juejin.cn/user/2682464100695389)

![Image 28](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/51b98a0c69a34689b8ca2c10dd66156d~tplv-k3u1fbpfcp-image.image#?w=43&h=20&s=6724&e=svg&a=1&b=f36937)

然而这次整个阿里没了，用阿里云oss依旧有问题![Image 29: [奸笑]](https://lf-web-assets.juejin.cn/obj/juejin-web/xitu_juejin_web/img/jj_emoji_17.bcebf79.png)

2年前

15

评论

*   屏蔽作者：犹如那海边

*   举报


[![Image 30: ly_fashion的头像](https://p3-passport.byteacctimg.com/img/user-avatar/c5a1b4feabcc348fe7cdfc737fb45822~200x200.awebp)](https://juejin.cn/user/2362175827225912/robots)

[ly\_fashion](https://juejin.cn/user/2362175827225912)

首席执行官 @天工开悟技术团队

为嘛不用notion

2年前

点赞

5

*   屏蔽作者：ly\_fashion

*   举报


[![Image 31: supree的头像](https://p9-passport.byteacctimg.com/img/user-avatar/49d5b3de41ce9610ab6014e426642072~100x100.awebp)](https://juejin.cn/user/4283353031515646)

[supree](https://juejin.cn/user/4283353031515646)

作者

:

其实文中提到了，想把数据尽量保留在自己手中。其次 notion 过于强大，其实我只是要一个好用的 markdown 编辑器

2年前

点赞

回复

*   屏蔽作者：supree

*   举报


[![Image 32: ly_fashion的头像](https://p3-passport.byteacctimg.com/img/user-avatar/c5a1b4feabcc348fe7cdfc737fb45822~100x100.awebp)](https://juejin.cn/user/2362175827225912)

[ly\_fashion](https://juejin.cn/user/2362175827225912)

回复

[supree](https://juejin.cn/user/4283353031515646)

作者

:

![Image 33: [发呆]](https://lf-web-assets.juejin.cn/obj/juejin-web/xitu_juejin_web/img/jj_emoji_4.28b310a.png)typora

2年前

点赞

回复

*   屏蔽作者：ly\_fashion

*   举报


查看全部 5 条回复

[![Image 34: 星河arnold的头像](https://p26-passport.byteacctimg.com/img/user-avatar/c9607092cac04848de3b6b93f921c48e~200x200.awebp)](https://juejin.cn/user/1679709496676391/robots)

[星河arnold](https://juejin.cn/user/1679709496676391)

提醒你一下，每年都有不少人因盗刷oss流量而大量欠费，建议oss私有+cdn鉴权访问oss，cdn流量更便宜且可以设置带宽封顶，可以大大降低盗刷损失。

2年前

5

3

*   屏蔽作者：星河arnold

*   举报


[![Image 35: supree的头像](https://p9-passport.byteacctimg.com/img/user-avatar/49d5b3de41ce9610ab6014e426642072~100x100.awebp)](https://juejin.cn/user/4283353031515646)

[supree](https://juejin.cn/user/4283353031515646)

作者

:

是的，有这个问题，顶一下。特别是如果做对外的博客，更要考虑这些。

2年前

点赞

回复

*   屏蔽作者：supree

*   举报


[![Image 36: 用户3440613530216的头像](https://p3-passport.byteacctimg.com/img/user-avatar/a1c64ab21657f58422f39ee6ce5538af~100x100.awebp)](https://juejin.cn/user/1612309042573364)

[用户3440613530216](https://juejin.cn/user/1612309042573364)

:

请问哪里有详细的教程吗，一直担心盗刷问题，但又没有找到解决方案

2年前

点赞

回复

*   屏蔽作者：用户3440613530216

*   举报


查看全部 3 条回复

查看全部 58 条评论

![Image 37](https://lf-web-assets.juejin.cn/obj/juejin-web/xitu_juejin_web/c12d6646efb2245fa4e88f0e1a9565b7.svg) 148

![Image 38](https://lf-web-assets.juejin.cn/obj/juejin-web/xitu_juejin_web/336af4d1fafabcca3b770c8ad7a50781.svg) 58

![Image 39](https://lf-web-assets.juejin.cn/obj/juejin-web/xitu_juejin_web/3d482c7a948bac826e155953b2a28a9e.svg) 收藏

加个关注，精彩更新不错过~

![Image 40: avatar](https://p9-passport.byteacctimg.com/img/user-avatar/49d5b3de41ce9610ab6014e426642072~70x70.awebp)

关注

[![Image 41: avatar](https://lf-web-assets.juejin.cn/obj/juejin-web/xitu_juejin_web/58aaf1326ac763d8a1054056f3b7f2ef.svg)

supree ![Image 42: 创作等级LV.4](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/1f4453379f1d416ca00c3619e796d330~tplv-k3u1fbpfcp-jj:0:0:0:0:q75.avis)

前端 @鸽子组扫地僧

榜上有名](https://juejin.cn/user/4283353031515646/posts)

[11

文章](https://juejin.cn/user/4283353031515646/posts)[65k

阅读](https://juejin.cn/user/4283353031515646/posts)[89

粉丝](https://juejin.cn/user/4283353031515646/followers)

加个关注，精彩更新不错过~

关注

已关注

[私信](https://juejin.cn/notification/im?participantId=4283353031515646)

目录

收起

*   [语雀心碎用户](https://juejin.cn/post/7298314768251519011#heading-0)

*   [从语雀导出所有笔记和图片](https://juejin.cn/post/7298314768251519011#heading-1)

        *   [上传图床](https://juejin.cn/post/7298314768251519011#heading-2)

                *   [阿里云 oss 设置](https://juejin.cn/post/7298314768251519011#heading-3)

                *   [配置 oss 权限](https://juejin.cn/post/7298314768251519011#heading-4)

                *   [本地图片上传图床](https://juejin.cn/post/7298314768251519011#heading-5)

        *   [Obsidian 调试](https://juejin.cn/post/7298314768251519011#heading-6)

                *   [多端同步](https://juejin.cn/post/7298314768251519011#heading-7)

                *   [图床配置](https://juejin.cn/post/7298314768251519011#heading-8)

                *   [个人偏好设置](https://juejin.cn/post/7298314768251519011#heading-11)

        *   [总结](https://juejin.cn/post/7298314768251519011#heading-16)


搜索建议

[*语雀*停机事件后，你也在找替代方案吗？](https://juejin.cn/post/7294425916549201935?from=search-suggest)

[工具推荐：一款好用且免费的笔记软件 *Obsidian*](https://juejin.cn/post/7169838406933938212?from=search-suggest)

[想了四年，一键发布文章到多平台终于在*Obsidian*中实现了（*语雀*版）](https://juejin.cn/post/7397024073228779554?from=search-suggest)

[知识管理协同工具，你在使用石墨笔记、*语雀*、Baklib还是什么？](https://juejin.cn/post/7233208763922268216?from=search-suggest)

[炒冷饭、*语雀*崩、领会员-我最主观的一段文字](https://juejin.cn/post/7294082278515294258?from=search-suggest)

[*语雀*，这波故障，放眼整个互联网也是炸裂般的存在。](https://juejin.cn/post/7293168604614377507?from=search-suggest)

[*Obsidian*+gitee实现笔记存储](https://juejin.cn/post/7202144813595443261?from=search-suggest)

[在众多优秀的笔记应用中，为什么选择wolai](https://juejin.cn/post/7012279459633971230?from=search-suggest)

[谈谈我的「数字文具盒」 - *Obsidian*](https://juejin.cn/post/7182080014177796133?from=search-suggest)

[使用 *Obsidian* + Git 构建自己的云端笔记系统](https://juejin.cn/post/7208015349451096120?from=search-suggest)

精选内容

[Angular 中的增量水合：构建“秒开且可交互”的 SSR 应用

掘金安东尼

 · 

35阅读

 · 

1点赞](https://juejin.cn/post/7605881632541409331 "Angular 中的增量水合：构建“秒开且可交互”的 SSR 应用")[拒绝重写！Flutter Add-to-App 全攻略：让原生应用“渐进式”拥抱跨平台

RaidenLiu

 · 

97阅读

 · 

2点赞](https://juejin.cn/post/7605772919225106466 "拒绝重写！Flutter Add-to-App 全攻略：让原生应用“渐进式”拥抱跨平台")[【LangChain.js学习】大模型分类

用泥种荷花

 · 

37阅读

 · 

0点赞](https://juejin.cn/post/7605859660612517922 "【LangChain.js学习】大模型分类")[基于 GitHub Actions 的 Notion RSS 自动化部署指南

leikooo

 · 

10阅读

 · 

0点赞](https://juejin.cn/post/7605625595571322895 "基于 GitHub Actions 的 Notion RSS 自动化部署指南")[利用Github Page + Hexo 搭建专属的个人网站（一）

前端拿破轮

 · 

13阅读

 · 

0点赞](https://juejin.cn/post/7605792874174119999 "利用Github Page + Hexo 搭建专属的个人网站（一）")

找对属于你的技术圈子

回复「进群」加入官方微信群

![Image 43](https://lf-web-assets.juejin.cn/obj/juejin-web/xitu_juejin_web/img/qr-code.4e391ff.png)

为你推荐

*   [语雀，这波故障，放眼整个互联网也是炸裂般的存在。](https://juejin.cn/post/7293168604614377507)

    [你好呀，我是歪歪。 昨天语雀凉了一下午，哦，不对，下午一般是指 12 点到 18 点的这 6 个小时。 语雀是从下午 14 点到晚上 22 点多，凉了 8 小时有余。 这故障时长，放眼整个互联网也是炸](https://juejin.cn/post/7293168604614377507)

    *   [why技术](https://juejin.cn/user/3702810893364350)

    *   2年前

    *   64k
    *   232
    *   152

    [程序员](https://juejin.cn/tag/%E7%A8%8B%E5%BA%8F%E5%91%98)

    ![Image 44: 语雀，这波故障，放眼整个互联网也是炸裂般的存在。](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/8c05b903c7bf46549d6330f606a72c11~tplv-k3u1fbpfcp-jj:216:144:0:0:q75.avis#?w=550&h=266&s=78973&e=png&b=fcfcfc)

*   [为什么我放弃了有道云笔记，选择了 Obsidian](https://juejin.cn/post/7220698356775469113)

    [历经数次笔记丢失后，我在 17年开始使用云笔记软件，使用有道云笔记4年后，我放弃它而开始用 Obsidian, 本文讲述我选择 Obsidian 的理由。](https://juejin.cn/post/7220698356775469113)

    *   [Ethan\_Zhou](https://juejin.cn/user/1151943916391965)

    *   2年前

    *   21k
    *   148
    *   91

    [前端](https://juejin.cn/tag/%E5%89%8D%E7%AB%AF) [掘金·金石计划](https://juejin.cn/tag/%E6%8E%98%E9%87%91%C2%B7%E9%87%91%E7%9F%B3%E8%AE%A1%E5%88%92) [后端](https://juejin.cn/tag/%E5%90%8E%E7%AB%AF)

    ![Image 45: 为什么我放弃了有道云笔记，选择了 Obsidian](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/d56a5f0f80434759bc64b2a496ae7331~tplv-k3u1fbpfcp-jj:216:144:0:0:q75.avis)

*   [炒冷饭、语雀崩、领会员-我最主观的一段文字](https://juejin.cn/post/7294082278515294258)

    [目录 什么是语雀 语雀，为每一个人提供优秀的文档和知识库工具。 作为一个程序员来说，我们需要一块位置去存储我们正在学习的技术、过往踩过的坑以及正在做的事情，如果我们需要记录每天的TO-DO List，](https://juejin.cn/post/7294082278515294258)

    *   [FirstMrRight](https://juejin.cn/user/1908407915791262)

    *   2年前

    *   1.3k
    *   点赞
    *   3

    [后端](https://juejin.cn/tag/%E5%90%8E%E7%AB%AF) [运维](https://juejin.cn/tag/%E8%BF%90%E7%BB%B4)

    ![Image 46: 炒冷饭、语雀崩、领会员-我最主观的一段文字](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/9b5e78093e96465691b7c1d249496768~tplv-k3u1fbpfcp-jj:216:144:0:0:q75.avis#?w=1920&h=1280&s=205961&e=jpg&b=181f2d)

*   [Obsidian+gitee实现笔记存储](https://juejin.cn/post/7202144813595443261)

    [从最开始的Typora单纯作为本地笔记，到语雀的云存储，再到Obsidian的自定义插件，笔记工具的“迭代”也有一种自身做笔记方式不断演进的感觉。本文想要实现的是Obsidian+git实现本地和gi](https://juejin.cn/post/7202144813595443261)

    *   [chenzn](https://juejin.cn/user/369092000493703)

    *   2年前

    *   1.4k
    *   点赞
    *   评论

    [后端](https://juejin.cn/tag/%E5%90%8E%E7%AB%AF)

*   [在众多优秀的笔记应用中，为什么选择wolai](https://juejin.cn/post/7012279459633971230)

    [1️⃣ 写在前面 最近半年的时间，体验了许多优秀的笔记应用。其中包括 ：OneNote 印象笔记 Notion Obsidian 专注笔记 思源笔记 Effie Seeds Typora 语雀](https://juejin.cn/post/7012279459633971230)

    *   [mingyong](https://juejin.cn/user/1195880817900958)

    *   4年前

    *   1.2k
    *   4
    *   评论

    [笔记](https://juejin.cn/tag/%E7%AC%94%E8%AE%B0)

    ![Image 47: 在众多优秀的笔记应用中，为什么选择wolai](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/aaf74df062e2457688865ee5c070fb58~tplv-k3u1fbpfcp-jj:216:144:0:0:q75.avis)

*   [谈谈我的「数字文具盒」 - Obsidian](https://juejin.cn/post/7182080014177796133)

    [这篇关于 Obsidian 是生产力工具的终篇了，因为目前涉及 Obsidian 的文章特别多，所以我就不啰里啰嗦叙述重复的文字了。本文主要涉及到 Obsidian 和 Docusaurus](https://juejin.cn/post/7182080014177796133)

    *   [7Wate](https://juejin.cn/user/3285757718442232)

    *   3年前

    *   1.4k
    *   3
    *   评论

    [程序员](https://juejin.cn/tag/%E7%A8%8B%E5%BA%8F%E5%91%98)

    ![Image 48: 谈谈我的「数字文具盒」 - Obsidian](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/8d5d4aae2cfe4ef88e77e1d7e9b0c411~tplv-k3u1fbpfcp-jj:216:144:0:0:q75.avis)

*   [初识Obsidian-第一版](https://juejin.cn/post/7472191058069028927)

    [本篇文章主要分享自己从Typora辗转结识Obsidian的际遇，并简单评点Ob的几点优劣。原文地址：\[初识Obsidian-第一版\](https://blog.huan99.com/post/202](https://juejin.cn/post/7472191058069028927)

    *   [growhuan](https://juejin.cn/user/3173664424725274)

    *   12月前

    *   280
    *   点赞
    *   评论

    [后端](https://juejin.cn/tag/%E5%90%8E%E7%AB%AF)

    ![Image 49: 初识Obsidian-第一版](https://p6-xtjj-sign.byteimg.com/tos-cn-i-73owjymdk6/88f0b4f544fd417ab9c2694fb747d8d9~tplv-73owjymdk6-jj-mark-v1:0:0:0:0:5o6Y6YeR5oqA5pyv56S-5Yy6IEAgZ3Jvd2h1YW4=:q75.awebp?rk3s=f64ab15b&x-expires=1771577080&x-signature=YYq%2Fg91121VkwAAcvYQW78gtWLE%3D)

*   [语雀收费后来吐槽一下](https://juejin.cn/post/7230699871249055803)

    [我与语雀 几年前我还是一名编程小白的时候，急需一种笔记工具来记录自己的学习笔记。曾经用过印象笔记，也有过Hexo自己搭建过上到Github，但效果都不是很理想，因为整理和排序都非常麻烦。偶然间看到群友](https://juejin.cn/post/7230699871249055803)

    *   [TingCode](https://juejin.cn/user/4407308245008701)

    *   2年前

    *   3.2k
    *   1
    *   2

    [前端](https://juejin.cn/tag/%E5%89%8D%E7%AB%AF)

    ![Image 50: 语雀收费后来吐槽一下](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/6dcaba97c9de492ea5d49f8777def563~tplv-k3u1fbpfcp-jj:216:144:0:0:q75.avis)

*   [支付宝办公神器语雀上线“空间”功能，8大实用指南快速上手！](https://juejin.cn/post/6844903832380506120)

    [近日，蚂蚁金服旗下知识创作与分享工具语雀发布“空间功能”，上周我们对这一办公室神器进行了介绍。（详情请戳：阿里员工都在用的知识管理工具，究竟有何特别？） 总体而言，语雀支持在线文档编写、多人协作、灵活的团队管理和金融级安全存储的基础上，新增“空间”功能，助力企业知识管理，帮助企…](https://juejin.cn/post/6844903832380506120)

    *   [蚂蚁数字科技](https://juejin.cn/user/3245414056467304)

    *   6年前

    *   2.0k
    *   点赞
    *   评论

    [支付宝](https://juejin.cn/tag/%E6%94%AF%E4%BB%98%E5%AE%9D)

*   [我在开发本地版「语雀」（下）](https://juejin.cn/post/7332113324651872294)

    [在上篇文章《我在开发本地版「语雀」（上）》中挑重点介绍了我开发 KnoSys GUI 应用的缘由及其核心功能；即便如此，有的人看过之后仍是不解我为啥要造这个轮子。 简单来说，KnoSys 是我宏大愿景](https://juejin.cn/post/7332113324651872294)

    *   [欧雷殿](https://juejin.cn/user/2670050655615806)

    *   2年前

    *   5.2k
    *   3
    *   8

    [前端](https://juejin.cn/tag/%E5%89%8D%E7%AB%AF) [客户端](https://juejin.cn/tag/%E5%AE%A2%E6%88%B7%E7%AB%AF) [开源](https://juejin.cn/tag/%E5%BC%80%E6%BA%90)

    ![Image 51: 我在开发本地版「语雀」（下）](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a7db2e14cdf24496b3e47b6b374b01b7~tplv-k3u1fbpfcp-jj:216:144:0:0:q75.avis#?w=1400&h=835&s=394404&e=png&b=061925)

*   [“云”端的语雀：用 JavaScript 全栈打造商业级应用](https://juejin.cn/post/6844904047720267783)

    [作者| 不四（死马）蚂蚁金服语雀产品技术负责人语雀是什么？语雀是一个专业的云端知识库，面向个人和团队，提供与众不同的知识管理，打造轻松流畅的工作协同，它提供各种格式的在线文档（富文本、表格、设计稿等）](https://juejin.cn/post/6844904047720267783)

    *   [阿里云云原生](https://juejin.cn/user/3808363977648493)

    *   6年前

    *   3.1k
    *   14
    *   评论

    [Kubernetes](https://juejin.cn/tag/Kubernetes)

*   [初识 Obsidian](https://juejin.cn/post/7487853041288380431)

    [本篇文章基于第一版修改润色而成，主要分享个人学习工作中使用过的那些工具软件以及以及一路辗转结识 Obsidian 的际遇。](https://juejin.cn/post/7487853041288380431)

    *   [growhuan](https://juejin.cn/user/3173664424725274)

    *   10月前

    *   99
    *   点赞
    *   评论

    [后端](https://juejin.cn/tag/%E5%90%8E%E7%AB%AF)

    ![Image 52: 初识 Obsidian](https://p6-xtjj-sign.byteimg.com/tos-cn-i-73owjymdk6/1f66ae20402740eb9c7b2dd2ad2e36fa~tplv-73owjymdk6-jj-mark-v1:0:0:0:0:5o6Y6YeR5oqA5pyv56S-5Yy6IEAgZ3Jvd2h1YW4=:q75.awebp?rk3s=f64ab15b&x-expires=1771577080&x-signature=1sdLFLkvtb2obyNH4Pvnhk71rBQ%3D)

*   [从免费的Vuepress迁移到付费的语雀，我都经历了些啥？](https://juejin.cn/post/7420244722336415755)

    [大家好，我是爱折腾的刘大逵，写完这篇文章，我就开始着手设计CMS系统了！这篇文章主要会介绍我们开源的轻量级权限系统Eva为什么要从免费的Vuepress搬家至付费的语雀中。 当然，重中之重，先恭喜大家](https://juejin.cn/post/7420244722336415755)

    *   [刘大逵](https://juejin.cn/user/1772858474767966)

    *   1年前

    *   188
    *   点赞
    *   评论

    [开源](https://juejin.cn/tag/%E5%BC%80%E6%BA%90)

    ![Image 53: 从免费的Vuepress迁移到付费的语雀，我都经历了些啥？](https://p6-xtjj-sign.byteimg.com/tos-cn-i-73owjymdk6/5dd9e4f30d974c49ad20449622126a08~tplv-73owjymdk6-jj-mark-v1:0:0:0:0:5o6Y6YeR5oqA5pyv56S-5Yy6IEAg5YiY5aSn6YC1:q75.awebp?rk3s=f64ab15b&x-expires=1771577080&x-signature=3MVgdssMMCp1lugGbIJtVhGzXzo%3D)

*   [语雀-西湖边上最好的知识管理平台](https://juejin.cn/post/6844903807776735246)

    [\[利益相关：我不是语雀团队的，但是我看好语雀，也希望语雀越来越猴。\] 好奇心驱使我，在合理合规的可见范围内发现了语雀的周报，在撸完了语雀的所有的可以看到的周报后，对语雀团队以及语雀这个产品有了点点的了解，非常有趣和看好。 语雀的周报里面，语雀的同学非常的专业，并且无论职位领域都…](https://juejin.cn/post/6844903807776735246)

    *   [鼓延](https://juejin.cn/user/2049145403870782)

    *   6年前

    *   2.9k
    *   3
    *   4

    [前端](https://juejin.cn/tag/%E5%89%8D%E7%AB%AF)

    ![Image 54: 语雀-西湖边上最好的知识管理平台](https://p1-jj.byteimg.com/tos-cn-i-t2oaga2asx/gold-user-assets/2019/3/27/169bdb25be279f2e~tplv-t2oaga2asx-jj:216:144:0:0:q75.avis)

*   [“云”端的语雀：用 JavaScript 全栈打造商业级应用](https://juejin.cn/post/6844904048299261959)

    [语雀是一个专业的云端知识库，面向个人和团队，提供与众不同的知识管理，打造轻松流畅的工作协同，它提供各种格式的在线文档（富文本、表格、设计稿等）编辑能力，支持实时在线多人协同编辑，数据云端保存不丢失。而语雀与其他文档工具最大的不同是，它通过知识库来对文档进行组织，让知识创作者更好…](https://juejin.cn/post/6844904048299261959)

    *   [阿里云云栖号](https://juejin.cn/user/2875978146128984)

    *   6年前

    *   727
    *   5
    *   评论

    [大数据](https://juejin.cn/tag/%E5%A4%A7%E6%95%B0%E6%8D%AE)


收藏成功！

已添加到「」， 点击更改

*   微信

    ![Image 55](https://juejin.cn/post/7298314768251519011)微信扫码分享

*   新浪微博
*   QQ

APP内打开

 *    ![Image 56: 下载掘金APP](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/2ad212d53ccd44569d10317171664bae~tplv-k3u1fbpfcp-jj:180:0:0:0:q75.avis) 下载APP

    下载APP
*    ![Image 57: 微信扫一扫](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/9f4933cc8fdb411cba89904f14a3ec0a~tplv-k3u1fbpfcp-jj:180:0:0:0:q75.avis) 微信扫一扫

    微信公众号
*   [新浪微博](https://weibo.com/xitucircle)

![Image 58](https://lf-web-assets.juejin.cn/obj/juejin-web/xitu_juejin_web/8867e249c23a7c0ea596c139befc04d7.svg)

![Image 59](https://lf-web-assets.juejin.cn/obj/juejin-web/xitu_juejin_web/img/MaskGroup.13dfc4f.png) 选择你感兴趣的技术方向

后端

前端

Android

iOS

人工智能

开发工具

代码人生

阅读

跳过

上一步

至少选择1个分类

温馨提示

当前操作失败，如有疑问，可点击申诉



沉浸阅读

确定屏蔽该用户

屏蔽后，对方将不能关注你、与你产生任何互动，无法查看你的主页