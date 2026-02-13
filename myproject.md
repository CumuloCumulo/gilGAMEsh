可以，而且**浏览器插件方案是最合适的**。

你现在遇到的问题本质是：

> 语雀的 video 是「卡片组件（card）」
> Markdown 导出时只会输出占位文本
> `[此处为语雀卡片，点击链接查看](about:blank#SB2px)`

也就是说：

* Markdown 导出功能 **不会展开卡片内容**
* 视频真实地址只存在于 DOM 里的 `<video><source src="...mp4">`

你贴的 DOM 里关键点是：

```html
<video>
  <source src="https://cloud.video.taobao.com/play/...mp4?auth_key=...">
</video>
```

这个 `src` 才是你真正要的东西。

---

# ✅ 你的目标可以实现吗？

答案是：

> ✅ 完全可以
> 而且插件方式是最优解

你可以：

1. 先调用语雀自带的“导出 Markdown”
2. 同时在页面里抓 `<video source>`
3. 下载视频
4. 替换 Markdown 里的占位卡片

---

# 🧠 本质问题分析

语雀视频卡片结构：

```
ne-card data-card-name="video"
```

导出 Markdown 时：

```
[此处为语雀卡片，点击链接查看](about:blank#SB2px)
```

其中：

```
SB2px  ← card id
```

而 DOM 里：

```
<ne-card id="SB2px">
```

这就是关键！

👉 Markdown 里的占位 ID 和 DOM 里的 card id 是一致的。

这给了你“映射能力”。

---

# 🚀 插件实现方案（推荐架构）

## 步骤 1：拦截导出前

插件 content script 做两件事：

### ① 收集页面视频信息

```js
const videos = []

document.querySelectorAll('ne-card[data-card-name="video"]').forEach(card => {
  const id = card.id
  const video = card.querySelector('video source')

  if (video) {
    videos.push({
      id,
      url: video.src
    })
  }
})
```

得到：

```json
[
  {
    "id": "SB2px",
    "url": "https://cloud.video.taobao.com/play/xxx.mp4"
  }
]
```

---

## 步骤 2：触发语雀官方导出

你可以：

* 模拟点击导出按钮
* 或监听下载事件

浏览器插件可以监听：

```js
chrome.downloads.onCreated
```

---

## 步骤 3：下载视频

background script：

```js
chrome.downloads.download({
  url: videoUrl,
  filename: `videos/${id}.mp4`
})
```

注意：

* 这个视频 URL 带 auth_key
* 有时是短期有效链接
* 所以必须在页面打开时立即下载

---

## 步骤 4：替换 Markdown 占位符

原 Markdown：

```
[此处为语雀卡片，点击链接查看](about:blank#SB2px)
```

替换为：

```md
<video src="./videos/SB2px.mp4" controls></video>
```

或者：

```md
![video](./videos/SB2px.mp4)
```

甚至：

```md
<video src="./videos/SB2px.mp4" controls width="600"></video>
```

---

# ⚠ 关键难点

## 1️⃣ auth_key 过期问题

视频 URL 类似：

```
https://cloud.video.taobao.com/play/...mp4?auth_key=...
```

这个通常：

* 带时间戳
* 有过期时间

解决方法：

* 立即下载
* 或用 fetch 把视频 blob 存本地

---

## 2️⃣ 跨域问题

插件下载没问题
但普通 fetch 可能会被 CORS 限制

推荐：

```
chrome.downloads.download
```

---

## 3️⃣ 视频可能不止一个 source

有些是：

```html
<source src="xxx.m3u8">
```

如果是 m3u8：

你需要：

* 用 ffmpeg 下载
* 或用 m3u8 下载器

---

# 🏗 推荐插件架构

```
manifest.json
background.js
content.js
utils/videoCollector.js
utils/mdRewriter.js
```

---

# 🎯 你的完整插件流程

```
用户打开语雀页面
        ↓
插件扫描视频卡片
        ↓
存储 {cardId → videoURL}
        ↓
用户点击“导出 Markdown”
        ↓
插件监听下载完成
        ↓
下载视频文件
        ↓
修改 Markdown
        ↓
重新保存
```

---

# 🔥 更高级做法（工程级）

你甚至可以：

* 不用语雀导出
* 直接抓 DOM
* 把整篇文章转 Markdown
* 同时处理视频 / 表格 / 代码块

那就是“语雀完全本地化导出器”。

---

# 💡 最优方案建议

如果你是想把这个整合进你的浏览器 Agent 项目：

我建议你做一个：

> 「语雀增强导出插件」

功能：

* 一键导出 Markdown
* 自动下载图片
* 自动下载视频
* 自动替换卡片
* 自动打包 zip

这个插件会非常有价值。

---

# 📌 最终回答你核心问题

> 可不可以在浏览器插件中，利用语雀导出 Markdown，同时把视频保存？

✔ 可以
✔ 技术上完全可行
✔ ID 映射已经帮你解决了最大难题

---

如果你愿意，我可以：

* 给你写完整插件结构代码
* 或帮你设计成“可复用卡片解析框架”
* 或帮你设计成通用知识库导出引擎

你现在是想：

1️⃣ 临时迁移用
2️⃣ 长期插件
3️⃣ 集成进你的浏览器 Agent

选一个，我给你对应的工程级方案。
