# 【开源】让 Claude 变身超强米家管家：一套通用的 AI Agent 智能家居控制方案

## 💡 引言

还在用传统的手机 APP 一个个点选开关？或者受限于小爱同学相对固定的指令集？随着 AI Agent（人工智能代理）时代的到来，我们完全可以用更自然、更像“真人”的方式来掌管我们的智能家居。

最近我开发并整理了一套**米家控制通用 AI 代理技能包**，实测在 **Claude (Agent Skills)**、**GitHub Copilot** 以及 **Cursor** 等 AI 助理中运行非常完美。今天就把这套方案分享给大家。

---

## 🔥 核心亮点

1.  **真正的自然语言理解**：不用死记硬背指令，对 AI 说“我要睡觉了”，它会自动帮你关灯、拉窗帘、开启空气净化器睡眠模式。
2.  **跨平台兼容**：不仅支持 Claude 的官方 Skill 模式，也能在任何具备本地文件读取和 Python 执行能力的 AI 环境中运行。
3.  **自愈式环境配置**：内置环境自检脚本，如果依赖没装或者没登录，AI 会引导你一步步完成。
4.  **安全可靠**：针对开锁、摄像头等敏感操作，强制加入二次确认逻辑。

---

## 🏗️ 项目架构

该项目主要由以下几部分组成：

*   **`mijiaAPI` 驱动**：底层基于开源的米家协议封装，支持扫码登录。
*   **Skill 定义 (`SKILL.md`)**：向 AI 声明它具备的能力和触发条件。
    *   **SOP 指令 (`instructions.md`)**：详细的逻辑步骤，确保 AI “做事有章法”。
    *   **执行脚本 (`scripts/`)**：包含环境检查、设备枚举和精准控制的纯 Python 实现。
    *   **设备映射表 (`reference/`)**：解决了不同厂商型号不同导致的 `siid/piid` 匹配难题。

---

## 🛠️ 快速上手

### 1. 准备环境
确保你的电脑安装了 Python 3.8+ 环境。建议在虚拟环境中操作：

```bash
# 进入项目目录
cd mijia-skills
# 创建并激活虚拟环境
python -m venv .venv
.\.venv\Scripts\activate  # Windows
```

### 2. 安装依赖
直接以可编辑模式安装项目，会自动通过 `setup.py` (或 requirements) 配置好命令：

```bash
pip install -e .
```

### 3. 扫码登录
运行以下命令，使用米家 APP 扫描出现的二维码完成授权：

```bash
mijiaAPI -l
```

---

## 🚀 进阶玩法：联动 Claude / Cursor / Copilot

将此项目文件夹打开，你可以直接对 AI 发起挑战：

> **User**: "看看客厅现在的温湿度是多少？如果超过26度就帮我把空调打开，制冷模式，24度。"
>
> **Claude**: (自动调用 `list_devices.py` 查找设备 -> 解析 `device_catalogs.md` 获取 siid/piid -> 调用 `control_device.py` -> 返回结果) "好的，当前客厅温度 27.5℃，已为您开启空调并设置为制冷 24℃。"

---

## 🔒 安全与建议

*   **二次确认**：在 `instructions.md` 中，我特别设定了敏感操作必须询问用户。
*   **本地执行**：所有控制指令均在本地触发，不经过任何第三方中转云（除小米官方 API 外），隐私更有保障。

---

## 📈 结语

这套方案真正让 AI 从“聊天框”走进了“物理世界”。如果你也想打造一个真正懂你的 AI 管家，欢迎尝试这个项目！

**项目地址**: [https://github.com/lllooollpp/mijia-skills.git](https://github.com/lllooollpp/mijia-skills.git) (记得给个 Star ⭐️ 哦！)

---

#SmartHome #AI #Claude #Agent #Mijia #Python #开源项目
