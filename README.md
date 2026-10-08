# oil-codex-title

<p align="center">
  <img src="./assets/readme/hero.svg" width="840" alt="Codex 话题实时命名，更好区分。对比普通标题与带 emoji 的具体任务标题。">
</p>

让 Codex 的话题标题跟上你正在做的事情。每轮对话结束后，自动参考最近 3～5 轮内容更新标题，话题再多，也更容易找到。

## 一眼看出正在做什么

以下为命名效果示例：

| 原来的标题 | 更容易找回的标题 |
| --- | --- |
| 回应中文问候 | 🧩 邮箱验证码｜过期排查 |
| 确认注册功能 | 🧩 支付回调｜重复发货修复 |
| 讨论视频标题 | 🎬 图像模型评测｜视频策划 |
| 继续修改 | 🎨 登录表单｜布局优化 |

统一采用 **「类别 emoji + 对象｜目标」**，先找对象，再看正在做什么。

- **对象在前**：把“CRT 转场”“登录表单”等辨识词放到前面，默认省略外层已有的项目名。
- **类别固定**：🎬 内容制作、🧩 工具开发、🔎 对比调研、🎨 页面设计、📝 方法整理。同一个视频进入修改阶段，也不会因此换成开发图标。
- **名称稳定**：准确的对象名称尽量不变；旧标题整理一次，之后只在工作目标实质变化时更新；“继续”“推送”不会取代主线。
- **不打断对话**：独立的 Luna Fast 在后台命名，不往原对话里添加消息。
- **跟随你的语言**：根据最近几轮用户消息的主要语言命名，保留产品名；偶尔一句外语不会让标题来回切换。例如：🧩 Email verification｜Fix expiry。
- **减少重复消耗**：稳定标题后的简单确认可直接保留，支持查看命名与归档评估的实际用量。
- **由你控制**：可以预览新标题、固定喜欢的名称，也可以随时暂停或恢复自动命名。
- **可选闲置归档**：定期收起长期未聊、已经完成的话题，保护置顶与待办。先预览再开启；已归档话题不再参与模型评估，相同内容也不会每天重复判断。

## 让 Codex 帮你安装

复制下面这段话发给 Codex：

```text
帮我从 GitHub 仓库 MogooStudio/oil-codex-title 安装完整插件，使用仓库内的 mogoo-oil-title 插件市场，开启话题自动命名并检查是否生效。需要我在界面中信任 Hook 的步骤，请告诉我怎么操作。
```

安装后，在新话题里正常聊天即可。默认使用 Luna Fast，消耗当前 Codex 账号的模型额度。

此 fork 额外支持可选中转站，默认仍沿用原版官方调用方式。可通过 `configure --provider relay` 配置 API 基础地址、密钥环境变量名和模型；切回 `--provider official` 会恢复原有官方模型配置。详见 [中转站配置](docs/使用与边界.md#可选中转站配置)。

也可以让 Codex「打开 oil-codex-title 的设置页面」，在本地页面选择官方或中转站、编辑配置并保存。命令入口为 `python3 scripts/oil_codex_title.py settings`（Windows 使用 `py -3`）。页面与后台 Hook 共用配置，保存后下次命名生效，详见 [可视化设置](docs/使用与边界.md#本地可视化设置)。

命令行安装及后续更新：

```sh
codex plugin marketplace add MogooStudio/oil-codex-title --ref main
codex plugin add oil-codex-title@mogoo-oil-title
codex plugin marketplace upgrade mogoo-oil-title
codex plugin add oil-codex-title@mogoo-oil-title
```

若原先已安装同名插件，请停用或卸载旧来源，避免同时加载两个自动命名 Hook。安装和更新不会自动信任 Hook；请在 Codex 官方 Hook 管理界面检查并信任新定义。

本 fork 基于 [oil-oil/oil-codex-title](https://github.com/oil-oil/oil-codex-title)，保留原作者的 MIT 许可。[更新记录](CHANGELOG.zh.md)

## 日常怎么用

直接对 Codex 说：

- “预览这个话题的新标题。”
- “固定这个话题的标题。”
- “暂停自动命名。” / “恢复自动命名。”
- “预览可以归档的闲置话题。” / “每天帮我整理闲置话题。”

目前为**预览版**，macOS 已实测，Windows 与 Linux 已通过自动化测试，桌面完整流程仍待实测；云端暂不支持。部分桌面版本的置顶列表可能仍显示旧标题，可让 Codex“检查真实标题并同步桌面显示”。

[详细使用与数据说明](docs/使用与边界.md) · [归档规则](docs/归档工作流.md) · [兼容性与验证记录](docs/发布验收.md) · [MIT 许可证](LICENSE)
