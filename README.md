# 🧠 Agentic Cursor - Python Project Assistant

A powerful agentic assistant designed to help automate Python-based Data Science and Machine Learning project workflows. This assistant uses function-calling and planning-action-observation loops to manage files, folders, and code with natural language instructions.

---

## 🚀 Features

- ✅ Agentic execution loop (`PLAN → ACTION → OBSERVE → COMPLETE`)
- 🧠 Uses Groq-hosted LLaMA 3 (via OpenAI SDK)
- 🗃️ File system management (create, read, update, delete files/folders)
- 📂 Move, copy, check existence of files and folders
- 🧾 Supports Streamlit app generation and Jupyter notebooks
- ⚙️ Can run shell commands (`pip install`, `ls`, etc.)
- 🤖 Fully JSON-structured assistant responses (no hallucination)

---

## 🛠 Tools Supported

| Function         | Description                                                                 |
|------------------|-----------------------------------------------------------------------------|
| `create_file`    | Creates a file at a specified path with provided content                    |
| `read_file`      | Reads the content of a file                                                 |
| `update_file`    | Appends content to an existing file                                         |
| `delete_file`    | Deletes a file                                                              |
| `create_folder`  | Creates a folder (with parent directories if needed)                        |
| `delete_folder`  | Deletes an empty folder                                                     |
| `list_files`     | Lists contents of a folder                                                  |
| `move_file`      | Moves or renames a file or folder                                           |
| `copy_file`      | Copies a file from source to destination                                    |
| `check_exists`   | Checks if a file/folder exists                                              |
| `run_command`    | Executes a Linux shell command                                              |

---

## 🧑‍💻 System Prompt Design

This assistant operates in 4 intelligent stages:

1. **PLAN** – Interprets the user instruction
2. **ACTION** – Selects and calls an appropriate tool
3. **OBSERVE** – Interprets result, checks success/failure
4. **COMPLETE** – Summarizes what was done

All responses are formatted in strict JSON:
```json
{
  "step": "plan",
  "content": "The user wants to create a file.",
  "function": "create_file",
  "input": {
    "path": "app.py",
    "content": "print('Hello World')"
  }
}
```

---

## 🧪 Example Usage

**User:** Create a new folder named `ML`

**Assistant:**
```json
{
  "step": "plan",
  "content": "The user wants to create a new folder named 'ML'.",
  "function": "create_folder",
  "input": "ML"
}
```

**User:** Move `data.csv` into `project` folder  
**Assistant:**
```json
{
  "step": "plan",
  "content": "The user wants to move 'data.csv' into the 'project' folder.",
  "function": "move_file",
  "input": {
    "source": "data.csv",
    "destination": "project/data.csv"
  }
}
```

---

## 🔧 Setup Instructions

1. Clone the repo:
   ```bash
   git clone https://github.com/your-repo/agentic-cursor.git
   cd agentic-cursor
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Set up `.env`:
   ```bash
   touch .env
   # Add your GROQ API key and base URL
   ```

---

## 📁 Folder Structure

```
agentic-cursor/
├── main.py
├── tools.py
├── README.md
├── .env
└── requirements.txt
```

---

## 🧠 Built With

- [Groq](https://groq.com/)
- [OpenAI SDK](https://pypi.org/project/openai/)
- [Python 3.x](https://www.python.org/)