# 泡泡圣诞树 · Bubble Christmas

一个单文件、无外链依赖的互动圣诞树。手机竖屏优先，**双击 `index.html` 就能玩**，也适合直接发到微信里打开。

> A tiny interactive Christmas tree in one 70 KB HTML file. No dependencies, no build, no network. Made for phones.

![预览](preview.png)

## 快速开始 / Quick start

1. 下载本仓库。
2. 双击 `index.html`。
3. 或者打开 GitHub Pages 在线版：`https://dsjsunu.github.io/bubble-christmas-tree/`

想在微信里发给朋友？微信聊天窗口不能直接运行 `.html` 附件，需要先变成一个 HTTPS 网址。最简单的是把仓库开 GitHub Pages，或把 `index.html` 拖到 [Netlify Drop](https://app.netlify.com/drop)。

## 能玩什么

| 操作 | 反馈 |
| --- | --- |
| 点树上的 10 个小装饰 | 泡泡爆闪、音效、进度提示；集齐 10 个触发烟花和角色台词 |
| 点白猫「橘子」/ 小狐「柚子」 | 弹出台词气泡、角色弹跳、爱心星星粒子 |
| 点顶部星星 / 底部「许愿」 | 打开许愿卡；愿望保存在本地，变成树梢上的小吊牌 |
| 点树梢「✦ N」吊牌 | 查看 / 轮播已经许下的愿望 |
| 双击空白处 / 点「烟花」 | Canvas 粒子烟花 |
| 点「灯光」 | 整棵树变暗 / 重新点亮 |
| 点「音乐」 | WebAudio 合成的八音盒版 Jingle Bells，不加载音频文件 |
| 点击任意空白 | 小星星粒子 |

## 技术实现

- **树**：60 个带高光、渐变的 SVG 圆泡叠成锥形，背后一层深绿剪影防止漏底；再加 34 个呼吸小灯、10 个可互动装饰。
- **角色**：纯 SVG 手绘的两只原创小动物 —— 橘色小猫「橘子」和戴星星帽的小狐「柚子」，不依赖任何外部素材。
- **雪 / 烟花**：一块全屏 Canvas，雪花常驻，烟花和点击粒子共用同一套粒子系统。
- **声音**：WebAudio 振荡器合成，首次点击后才创建 `AudioContext`，不自动播放；Jingle Bells 是公版旋律。
- **愿望**：`localStorage` 保存，手机端刷新不丢；只存在当前浏览器，不会上传服务器。
- **微信适配**：`viewport-fit=cover` + `safe-area-inset-*` 适配刘海屏；禁止下拉回弹、双击缩放、长按菜单；`text-size-adjust:100%` 防止微信改字号；不用 ES Module、外部字体、外部图片；DPR 上限 2。
- **性能**：静态 SVG 不逐帧重绘；Canvas 只画雪和粒子；`document.hidden` 时暂停音乐。

已在 390×844、375×667、320×568、1440×900 四种视口做过 Chromium 渲染和点击测试，无控制台报错。

## 自定义

| 想改什么 | 搜索 |
| --- | --- |
| 标题与文案 | `泡泡圣诞树` |
| 愿望存储键 | `WISH_KEY` |
| 角色台词 | `momoLines` / `yuzuLines` |
| 主配色 | `:root` 里的 `--pink`、`--mint`、`--gold`；树泡颜色在 `mintFills` / `accentFills` |
| 音乐旋律 | `melody` 数组，格式 `[MIDI 音高, 拍数]` |
| 关掉开场台词 | 删掉 `setTimeout(... 3300)` 那一段 |
| 角色造型 | `<g id="momo">` 和 `<g id="yuzu">` |

## 素材与版权

- 角色「橘子」「柚子」是项目内的原创 SVG 绘制，不包含任何第三方角色图片。
- Jingle Bells 旋律属于公有领域，音色由 WebAudio 实时合成。
- 代码以 [MIT](LICENSE) 许可发布，可自由使用、修改、商用。

## English

A single-file interactive Christmas tree: 60 glossy SVG bubbles, two original hand-drawn mascots, canvas snow and fireworks, synthesized music-box melody, and locally saved wishes. No dependencies — open `index.html` and play. MIT licensed.

---

圣诞快乐。如果它让你的十二月暖和了一点，欢迎点个 ⭐。
