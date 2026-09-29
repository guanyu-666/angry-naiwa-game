# 奶蛙弹射 · 网页小游戏

一个用 Phaser3 + Matter 物理做的弹射小游戏（愤怒小鸟式）：拖拽奶蛙蓄力发射，打塌木石高塔、把藏在塔里的肥嘟嘟全部打下平台即胜利。好友内部娱乐，不上架不商用。

## 目录说明

| 文件/目录 | 作用 |
|---|---|
| `index.html` | **游戏本体（单文件）**，Phaser 已内联，游戏逻辑全在里头 |
| `assets/` | 所有图片素材，**必须和 index.html 放在同级** |
| `lib/` | Phaser 库源码（已内联进 index.html，可不上传） |
| `main.js` | 游戏逻辑源码（index.html 是从它构建出来的） |
| `build_release.py` | 改完 main.js 后重跑它，重新生成单文件 index.html |

> 上传 / 分享时**只需要 `index.html` + `assets/` 两个东西**就够了。

## 上传 GitHub

```bash
cd game
git init
git add index.html assets
git commit -m "奶蛙弹射 v3"
git remote add origin <你的仓库地址，如 https://github.com/用户名/仓库名.git>
git push -u origin main
```

## 开启 GitHub Pages（免费托管，把链接发给好友就能玩）

1. 打开仓库页面 → **Settings** → **Pages**
2. **Branch** 选 `main`，目录选 `/ (root)` → 点 **Save**
3. 等一两分钟，访问 `https://<用户名>.github.io/<仓库名>/` 即可游玩

## 本地预览（必须走 http，不能直接双击）

Phaser 用 XHR 加载图片，直接双击 `index.html`（`file://` 协议）会被浏览器 CORS 拦截，图片加载不出来。本地起个服务即可：

```bash
cd game
python -m http.server 8000
```

然后浏览器打开 `http://localhost:8000/`。

## 修改游戏逻辑

1. 编辑 `main.js`
2. 运行 `python build_release.py` 重新生成单文件 `index.html`
3. 重新上传即可

## 玩法 & 操作

- 拖拽奶蛙向后下方蓄力，松手发射，拖拽时有白色轨迹虚线预测落点
- 木/石搭成高塔保护肥嘟嘟，打塌塔 / 砸开缺口 / 直接命中都能打到它
- 肥嘟嘟：被打碎 / 被倒下的木石砸中 / 被打下平台 都算消灭，全部消灭即过关
- 右上角「暂停」可冻结；主页有「继续游戏 / 选择关卡 / 重新开始」，右下角「形象商店」可换奶蛙皮肤
