# Cheat Engine 7.7 简体中文汉化语言包

[![Cheat Engine](https://img.shields.io/badge/Cheat%20Engine-7.7-blue)](https://cheatengine.org/)
[![License](https://img.shields.io/badge/license-CC%20BY--NC--SA%204.0-green)](https://creativecommons.org/licenses/by-nc-sa/4.0/)
[![Platform](https://img.shields.io/badge/platform-Windows-lightgrey)](#)

为 **Cheat Engine 7.7** 补全的简体中文语言包。在社区旧版 7.6 汉化的基础上，对齐 7.7 官方 `.po` 模板逐条补全，覆盖率达 **100%**。

> **这是什么**：不是从零翻译，而是把旧版汉化包升级到能完整适配 7.7 的版本。旧包在 7.7 上有 146 条界面文本无译文（直接回退显示英文），本包把它们全部补齐。

---

## ✨ 特点

- **100% 覆盖** —— 全库 5538 条文本（主界面 4875 + 附属模块 663），零空译
- **修好了旧包的隐藏 bug** —— 3 处 Pascal Format 占位符顺序错乱（`%s`/`%d` 错位会让界面显示串位），33 处换行丢失（多段提示被压成一行）
- **术语统一** —— 同一英文词在不同窗口有 65 种不一致译法，收敛到 3 组合理保留项
- **格式对齐官方** —— CRLF 行尾、无 BOM、标准 PO 头，CE 的 Lazarus TPOFile 直接解析
- **语言菜单显示中文名** —— 附带 `name.txt`，下拉框里显示「简体中文 (zh_CN)」而非 `zh_CN`

---

## 📦 安装

### 方式 A：替换安装（推荐）

1. 关闭 Cheat Engine
2. 备份原有语言目录（如果存在）：
   ```
   C:\Program Files\Cheat Engine\languages\zh_CN\  →  改名或复制到别处
   ```
3. 把本包的 `zh_CN` 整个文件夹放进 `C:\Program Files\Cheat Engine\languages\`
4. 启动 CE，菜单 **Edit → Settings → Languages** 选「简体中文 (zh_CN)」

`C:\Program Files` 需要管理员权限，解压时可能要右键「以管理员身份运行」解压工具。

### 方式 B：并存测试（不想动原包时用）

1. 把 `zh_CN` 文件夹改名为 `zh_CN_new`，放进 `languages\`
2. 用命令行启动，临时指定语言：
   ```cmd
   "C:\Program Files\Cheat Engine\cheatengine-x86_64.exe" --LANG zh_CN_new
   ```

两种方式都不需要改注册表，也不影响 CE 本体文件。

---

## 📋 文件清单

| 文件 | 条目数 | 说明 |
|---|---:|---|
| `cheatengine-x86_64.po` | 4875 | 主程序界面（含全部菜单、对话框、窗体） |
| `Tutorial-x86_64.po` | 132 | 内置教程 |
| `lclstrconsts.po` | 348 | Lazarus LCL 框架自身字符串 |
| `Java.po` | 71 | Java 相关 |
| `pseudocodediagram.po` | 46 | 伪代码流程图 |
| `monoscript.po` | 34 | Mono/.NET 脚本 |
| `patchscan.po` | 17 | 补丁扫描 |
| `VersionCheck.po` | 10 | 版本检查 |
| `SaveSessions.po` | 5 | 会话保存 |
| `name.txt` | — | 语言菜单显示名 |

---

## 🔧 这个包改了什么

### 1. 补齐 146 条缺失译文

旧包基于 7.6，7.7 新增了大量界面文本。缺失集中在：

- `tfrmmemoryviewex.*` —— 内存视图扩展（约 15 条）
- `tfrmexecuteexceptionlog.*` —— 执行异常日志（约 13 条）
- `tfrmstructuresconfig.*` / `tfrmstructures2.*` —— 结构编辑（约 27 条）
- `tmainform.mi*` —— 主菜单新增项（约 20 条）
- `tfrmresumepointerscan.*` —— 指针扫描续接（8 条）
- 其余零散分布

### 2. 修复 3 处占位符错位

Pascal Format 按 `%s`、`%d` 出现顺序取参，中文重排语序必然串位：

| 原文 | 旧包（错） | 本包（修正） |
|---|---|---|
| `Error in the structure definition of %s at line %d` | `在第 %d 行中 %s 结构定义出错` | `%s 的结构定义在第 %d 行出错` |
| `Failure assembling %s at %.8x` | `在 %.8x 处装配 %s 失败` | `装配 %s 于 %.8x 处失败` |
| `No help found for line %d, column %d of %s.` | `未找到 %s 的第 %d 行，第 %d 列的帮助。` | `未找到第 %d 行、第 %d 列（%s）的帮助。` |

### 3. 修复 33 处换行错乱

旧包把多段提示合并成单行（或多出尾随换行），导致帮助文本挤成一坨。逐条按官方模板的空行结构重排。

### 4. 统一 62 组不一致译法

| 英文 | 旧包乱象 | 统一为 |
|---|---|---|
| Speedhack | 速度黑客 / 启用速度hack / 启用速度破解 | 速度黑客 |
| Value | 数值 / 值 | 值 |
| Active | 激活 / 活动 | 启用 |
| Pointer | 指针 / 指向 | 指针 |
| Next Scan | 下一个扫描 / 下一次扫描 | 下一次扫描 |
| pointermap | 指针映射 / 指针图 | 指针图 |
| Jumplines | 跳行 / 跳转行 | 跳转行 |

**刻意保留的差异**：`Filter`（过滤/过滤器）、`Unrandomizer`（去随机化/去随机化器）、`numeric`（数字/数字键）——这几组在具体语境里含义确实不同，强行统一反而更糟。

### 5. 修掉一处 HTML 实体残留

旧包把指针符号 `P->` 误写成 `P-&gt;`，界面上直接显示 HTML 实体。

---

## ⚠️ 已知限制

**以下界面元素无论用哪个语言包都显示英文**，因为它们不在官方 `.po` 模板覆盖范围内：

| 位置 | 字符串 | 原因 |
|---|---|---|
| 设置 → MonoExtension | `Enable "Uses Mono" option on successful mono attach`<br>`Ignore the "Uses Mono" option inside a table` | `autorun\monoscript.lua:7217-7218` 里 `createSettingsOption()` 的第 2 个参数是硬编码英文字面量，**未经过 `translate()`**，任何 po 文件都无法覆盖 |
| 设置 → Auto Save / Extra Custom Types | `Auto Save`<br>`Extra Custom Types` | 由 `autorun\autosave.lua:284`、`bigendian.lua:278` 在运行时用 `translate()` 注册，但官方未提供 `autosave.po` / `bigendian.po`，译文无处可放 |

这类由 Lua 插件运行时注册的字符串共约 **110 条**（含 CEShare、.NET/Mono Info、Java Info 等模块）。技术上可以为各插件单独建立 `.po` 补上，但这超出了「对齐官方模板」的范围，本包暂未包含。

需要的话可以另开一个「插件扩展汉化」包。

---

## 🔍 校验

每个 po 文件都经过以下检查：

- ✅ `msgid` 序列、`msgctxt`、`#:` 引用、`#,` flags 与官方模板**逐条一致**
- ✅ 无空译文（3 条纯空白占位除外，属窗体布局需要）
- ✅ Pascal Format 占位符序列完全匹配原文
- ✅ 换行数与原文一致
- ✅ 行尾统一 CRLF、无 BOM、引号成对、无非法转义

校验脚本与生成工具一并保留在本仓库 `tools/` 下，可自行复现。

---

## 🛠 重新生成

```bash
python tools/build_zh_po.py       reference/cheatengine-x86_64.po \
                                  reference/zh_CN/cheatengine-x86_64.po \
                                  output/zh_CN/cheatengine-x86_64.po
python tools/build_tutorial_po.py reference/Tutorial-x86_64.po \
                                  reference/zh_CN/tutorial-x86_64.po \
                                  output/zh_CN/Tutorial-x86_64.po
python tools/build_misc_po.py     reference reference/zh_CN output/zh_CN
python tools/publish_zh.py        output/zh_CN reference
```

校验：
```bash
python tools/verify_zh_po.py reference/cheatengine-x86_64.po output/zh_CN/cheatengine-x86_64.po
python tools/strict_check.py output/zh_CN
```

---

## 🙏 致谢

- [Cheat Engine](https://cheatengine.org/) — Dark Byte 及贡献者
- 旧版 7.6 简体中文语言包的原始译者（`gpt-po v1.2.3` / Poedit 3.5）
- CE 社区中文用户

---

## 📄 授权

本语言包采用 **CC BY-NC-SA 4.0** 授权。

请同时遵守 Cheat Engine 自身的 `license.txt`：仅限个人/教学用途，**禁止商用**、**禁止二次分发**、**禁止制作便携版上传**。

---

## 📮 反馈

发现错译、漏译或占位符问题，欢迎提 Issue，请附上：

1. CE 版本（菜单 Help → About 里的版本号）
2. 出现问题的界面截图
3. 该界面的英文原文（切回英文可对照）
