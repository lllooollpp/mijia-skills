# Mijia Control Universal AI Agent Skill / 米家控制通用 AI 代理技能包

This is a **Universal AI Agent Skill Pack**. It supports not only Claude (through Agent Skills) but also any AI assistant capable of reading local files and executing Python/CLI (e.g., GitHub Copilot, Cursor, Open Interpreter, etc.).

这是一个**通用型 AI 代理技能包**。不仅支持 Claude (通过 Agent Skills)，也支持任何能够读取本地文件、执行 Python/CLI 的 AI 助理（如 GitHub Copilot, Cursor, Open Interpreter 等）。

## 📁 Project Structure / 目录结构

- **.agent-rules**: [New] Universal agent rules file, defining behavior guidelines for non-Claude models. / [新增] 通用代理规则文件，用于向非 Claude 模型声明行为准则。
- **SKILL.md**: Skill entry point. Defines trigger conditions and core execution logic. / 技能入口。定义了触发条件和核心运行逻辑。
- **instructions.md**: Standard Operating Procedure (SOP). Detailed rules for self-check, device matching, and anomaly handling. / 标准作业程序 (SOP)。详细规定了模型如何自检、匹配设备以及处理异常。
- **requirements.txt**: List of Python dependencies for the skill and its underlying driver `mijiaAPI`. / 该技能及其底层驱动包 `mijiaAPI` 所需的 Python 依赖项列表。
- **scripts/**: Core execution scripts. / 核心执行脚本。
    - `setup_env.py`: Checks current Python environment for `mijiaAPI` and CLI tools, and verifies login status. / 检查当前 Python 环境是否安装了 `mijiaAPI` 包以及 CLI 工具，并验证登录状态。
    - `list_devices.py`: Gets a JSON snapshot of home devices. / 获取家庭设备的 JSON 格式快照。
    - `control_device.py`: Executes specific property read or set commands. / 执行具体的属性读取或设置指令。
- **reference/**: Reference materials. / 参考资料。
    - `device_catalogs.md`: Mapping between known device models and MIoT properties (siid/piid). / 存放已知设备型号（Model）与其 MIoT 属性（siid/piid）的映射关系。

## 🛠️ Prerequisites / 前置准备

Before using this skill, please ensure the following steps are completed: / 在使用此技能之前，请确保完成以下步骤：

1. **Activate Virtual Environment / 激活虚拟环境**: Ensure you are in the correct `.venv`. / 确保你在正确的 `.venv` 下。
2. **Install CLI / 安装 CLI**: Run the following command in the project root to install the project in editable mode: / 在项目根目录下运行以下命令，将项目以可编辑模式安装：
   ```bash
   pip install -e .
   ```
3. **Login / 扫码登录**: Run the following command and use the Mijia app to scan the QR code: / 运行以下命令并使用米家 APP 扫描弹出的二维码：
   ```bash
   mijiaAPI -l
   ```

## 🚀 How to Use / 如何使用

This skill is designed for automatic loading by AI assistants. It triggers when you mention things like: / 这个技能是为 AI 助理自动加载设计的。当你与助理交流并提及以下内容时，它会自动触发：
- "List the current status of my home devices." / "帮我列出我家里现在的设备状态。"
- "Turn on the dining room light." / "打开餐厅的灯。"
- "Check the water level of the humidifier." / "看看加湿器现在的水位。"

## ⚠️ Notes / 注意事项

- **Self-healing Mechanism / 自愈机制**: If the environment is not ready, the assistant will guide you through installation or login based on feedback from `setup_env.py`. / 如果环境未准备好，助理会根据 `setup_env.py` 的反馈自动引导你进行安装或登录。
- **Security / 安全性**: For sensitive operations like unlocking doors or cameras, the assistant will ask for secondary verbal confirmation. / 涉及开锁、摄像头等敏感操作时，助理会要求你进行二次口头确认。
