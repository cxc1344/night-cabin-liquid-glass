# 林间夜屋 · Night Cabin — Liquid Glass

A single-file Three.js night scene: a lamplit cabin in a pine forest, with a
campfire, rain, lightning, procedural ambient audio — and a full
**liquid-glass UI** whose refraction, chromatic dispersion and specular
highlights are rendered in real time.

**Just open `index.html`.** No build step, no server, no external requests —
even Three.js is inlined. It runs offline, on desktop and on phones.

## 玩法

底部是一排液态玻璃按钮（全胶囊圆角，图标是矢量描边，不是 emoji）：

| 按钮 | 作用 |
|---|---|
| 窗灯 | 开关小屋的灯 |
| 篝火 | 点燃 / 熄灭篝火 |
| 下雨 | 下雨（带积水反光、雨声、随机闪电） |
| 声音 | 程序化环境音：风、雨、火、蟋蟀、雷声（Web Audio 现场合成，无音频文件） |
| 环绕 | 自动环绕镜头 |
| 下雪 | **短按**开关下雪；**长按**弹出雪量滑杆，左小雪右大雪 |

下雪是全场联动的：雪会**逐步积起来**——地面、屋顶斜面、屋脊、烟囱、
树冠一起变白，积雪越厚篝火越弱，最后被雪堆盖灭；关掉下雪则慢慢化掉，
余烬会重新燃起来。雪量滑杆同时控制雪花密度、下落速度和积雪速度。

静止不动一会儿，界面会自己淡下去，镜头开始缓缓环绕，进入放空模式。

## 液态玻璃是怎么做的

不是毛玻璃。做法已经抽成了一个可复用的 Agent Skill 单独开源：

**→ [liquid-glass-skill](https://github.com/cxc1344/liquid-glass-skill)**

核心三件套：运行时按元素形状生成 SDF 位移图（中间中性、只在边缘弯曲）、
RGB 三通道不同尺度位移造成色散、高光跟随指针/陀螺仪并能响应场景里的闪电。

## English summary

`index.html` is a self-contained Three.js scene (library inlined, zero
network requests). Its UI implements real liquid glass — runtime SDF
displacement refraction with RGB dispersion and a live specular layer — the
same implementation packaged as an agent skill in
[liquid-glass-skill](https://github.com/cxc1344/liquid-glass-skill).
Tap the snowflake button to start snow: it accumulates gradually on the
ground, roof slopes, ridge, chimney and trees, and slowly smothers the
campfire. Long-press the snow button for an intensity slider.

Tip: enable **GitHub Pages** (Settings → Pages → Deploy from branch `main`)
and this file becomes a live demo at
`https://cxc1344.github.io/night-cabin-liquid-glass/`.

## License

MIT — see [LICENSE](LICENSE).

Built by [cxc1344](https://github.com/cxc1344) with Muse (syzsg).
