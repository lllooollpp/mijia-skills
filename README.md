# Mijia Control Universal AI Agent Skill

这是一个**通用型 AI 代理技能包**，不仅支持 Claude (through Agent Skills)，也支持任何能够读取本地文件、执行 Python/CLI 的 AI 助理（如 GitHub Copilot, Cursor, Open Interpreter 等）。

## 📁 目录结构

- **.agent-rules**: [新增] 通用代理规则文件，用于向非 Claude 模型声明行为准向。
- **SKILL.md**: 技能入口。定义了触发条件和核心运行逻辑。
- **instructions.md**: 标准作业程序 (SOP)。详细规定了模型如何自检、匹配设备以及处理异常。
- **requirements.txt**: 该技能及其底层驱动包 `mijiaAPI` 所需的 Python 依赖项列表。
- **scripts/**: 核心执行脚本。
    - `setup_env.py`: 检查当前 Python 环境是否安装了 `mijiaAPI` 包以及 CLI 工具，并验证登录状态。
    - `list_devices.py`: 获取家庭设备的 JSON 格式快照。
    - `control_device.py`: 执行具体的属性读取或设置指令。
- **reference/**: 参考资料。
    - `device_catalogs.md`: 存放已知设备型号（Model）与其 MIoT 属性（siid/piid）的映射关系。

## 🛠️ 前置准备

在使用此技能之前，请确保完成以下步骤：

1. **激活虚拟环境**: 确保你在正确的 `.venv` 下。
2. **安装 CLI**: 在项目根目录下运行以下命令，将项目以可编辑模式安装：
   ```bash
   pip install -e .
   ```
3. **扫码登录**: 运行以下命令并使用米家 APP 扫描弹出的二维码：
   ```bash
   mijiaAPI -l
   ```

## 🚀 如何使用

这个技能是为 Claude 自动加载设计的。当你与 Claude 交流并提及以下内容时，它会自动触发：
- "帮我列出我家里现在的设备状态。"
- "打开餐厅的灯。"
- "看看加湿器现在的水位。"

## ⚠️ 注意事项

- **自愈机制**: 如果环境未准备好，Claude 会根据 `setup_env.py` 的反馈自动引导你进行安装或登录。
- **安全性**: 涉及开锁、摄像头等敏感操作时，Claude 会要求你进行二次口头确认。
