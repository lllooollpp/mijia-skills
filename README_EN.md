# Mijia Control Universal AI Agent Skill

[中文版](./README.md)

This is a **Universal AI Agent Skill Pack**. It supports not only Claude (through Agent Skills) but also any AI assistant capable of reading local files and executing Python/CLI (e.g., GitHub Copilot, Cursor, Open Interpreter, etc.).

## 📁 Project Structure

- **.agent-rules**: [New] Universal agent rules file, defining behavior guidelines for non-Claude models.
- **SKILL.md**: Skill entry point. Defines trigger conditions and core execution logic.
- **instructions.md**: Standard Operating Procedure (SOP). Detailed rules for self-check, device matching, and anomaly handling.
- **requirements.txt**: List of Python dependencies for the skill and its underlying driver `mijiaAPI`.
- **scripts/**: Core execution scripts.
    - `setup_env.py`: Checks current Python environment for `mijiaAPI` and CLI tools, and verifies login status.
    - `list_devices.py`: Gets a JSON snapshot of home devices.
    - `control_device.py`: Executes specific property read or set commands.
- **reference/**: Reference materials.
    - `device_catalogs.md`: Mapping between known device models and MIoT properties (siid/piid).

## 🛠️ Prerequisites

Before using this skill, please ensure the following steps are completed:

1. **Activate Virtual Environment**: Ensure you are in the correct `.venv`.
2. **Install CLI**: Run the following command in the project root to install the project in editable mode:
   ```bash
   pip install -e .
   ```
3. **Login**: Run the following command and use the Mijia app to scan the QR code:
   ```bash
   mijiaAPI -l
   ```

## 🚀 How to Use

This skill is designed for automatic loading by AI assistants. It triggers when you mention things like:
- "List the current status of my home devices."
- "Turn on the dining room light."
- "Check the water level of the humidifier."

## ⚠️ Notes

- **Self-healing Mechanism**: If the environment is not ready, the assistant will guide you through installation or login based on feedback from `setup_env.py`.
- **Security**: For sensitive operations like unlocking doors or cameras, the assistant will ask for secondary verbal confirmation.
