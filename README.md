# notebook

《家庭备忘录》角色卡的状态栏面板托管仓库。面板本体经 jsDelivr 拉取，角色卡里的 `正则/状态栏界面.html` 只做一层挂载壳。

## 目录

- `index.html` —— 面板本体（Vue 3 编译产物，单文件，自带 CSS 与 JS）
- `avatar/*.webp` —— 裴清越的七张表情头像（喜 / 怒 / 哀 / 乐 / 羞 / 娇羞 / 爽），384×384，去白底透明

## 更新流程

1. 改源码：`D:\ACARD\tavern_helper_template\src\家庭备忘录\界面\状态栏\`
2. 在 `D:\ACARD\tavern_helper_template` 下编译：

   ```bash
   node node_modules/webpack-cli/bin/cli.js --config webpack.dsh.mjs --mode production
   ```

3. 把 `dist/家庭备忘录/界面/状态栏/index.html` 复制到本仓库根目录，覆盖 `index.html`
4. 提交并推送，记下新的 commit
5. 把角色卡 `正则/状态栏界面.html` 里的 `@<commit>` 换成新 commit，重新打包角色卡
6. 角色卡玩家侧若还是旧面板，去 [jsDelivr purge](https://www.jsdelivr.com/tools/purge) 把
   `https://testingcf.jsdelivr.net/gh/Sherey93/notebook@<commit>/index.html`
   里的 `testingcf.` 换成 `cdn.` 后提交刷新

## 加载地址

```
https://testingcf.jsdelivr.net/gh/Sherey93/notebook@<commit>/index.html
```

## 已知限制

远程加载：断网或 jsDelivr 不稳定时面板空白，不影响正文与剧情推进。
