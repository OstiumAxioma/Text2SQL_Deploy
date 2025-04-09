
# 🧠 Text-to-SQL with Local LLMs

<p align="center">
  <b>Vanna + Ollama + ChromaDB | Run LLMs Locally for Natural Language to SQL</b>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Vanna-AI-blueviolet?logo=OpenAI" />
  <img src="https://img.shields.io/badge/Ollama-LLM-informational?logo=OpenAI" />
  <img src="https://img.shields.io/badge/ChromaDB-Embeddings-orange" />
  <img src="https://img.shields.io/badge/HuggingFace-Models-yellow?logo=huggingface" />
  <img src="https://img.shields.io/badge/Platform-Windows-blue?logo=windows" />
  <img src="https://img.shields.io/badge/Python-3.10+-green?logo=python" />
</p>

---

## 📌 About This Project

This project implements a **locally-deployable Text-to-SQL system** using open-source tooling:

- 🤖 **[Vanna](https://github.com/vanna-ai/vanna)** – generates SQL queries from natural language  
- 🧱 **[ChromaDB](https://github.com/chroma-core/chroma)** – stores vectorized schema + user prompts  
- 🦙 **[Ollama](https://ollama.com)** – runs local LLMs like `llama3.2` directly on your Windows machine  
- 🤗 **[Hugging Face](https://huggingface.co)** & 🧠 **[ModelScope](https://modelscope.cn)** – open model sources

> ✅ No OpenAI key required  
> ✅ Works fully offline  
> ✅ Suitable for teaching, enterprise dashboards, or privacy-aware deployment

---

## 🗂️ Project Structure

```bash
📁 text2sql-llm/
├── text2SQL_LLM.ipynb       # Main notebook for training + querying
├── tips.csv                 # Sample dataset
├── README.md                # This file
```

---

## ⚙️ Installation (Windows)

```bash
git clone https://github.com/your-username/text2sql-llm
cd text2sql-llm

python -m venv .venv
.venv\Scripts\activate

pip install -r requirements.txt
```

Make sure the following packages are installed:
- `vanna[chromadb]`
- `chromadb`
- `flask`
- `onnxruntime`
- `ollama` (`pip install ollama`)

---

## 🦙 Run Ollama (Local LLM)

Install from https://ollama.com and start a local model:

```bash
ollama run llama3.2
```

Or choose any model like `mistral`, `phi3`, etc.

---

## 🚀 Run the Notebook

Launch `text2SQL_LLM.ipynb` and run through the following steps:

- Load dataset: `tips.csv`
- Train Vanna on schema
- Ask natural questions
- Receive SQL output

```python
vn.ask("What is the average tip for smokers on Sunday?")
```

🔁 Output:
```sql
SELECT AVG(tip) FROM tips WHERE smoker = 'Yes' AND day = 'Sun';
```

---

## 🌐 Optional Web UI (Flask)

```python
from vanna.flask import VannaFlaskApp

app = VannaFlaskApp(vn, allow_llm_to_see_data=True)
app.run(port=8084)
```

Then visit 👉 [http://localhost:8084](http://localhost:8084)

---

## 🧪 Technologies Used

| Tool        | Description                                 |
|-------------|---------------------------------------------|
| 🧠 Vanna     | Natural language → SQL via prompt + schema  |
| 🧱 ChromaDB  | Vector store for schema and prompt history  |
| 🦙 Ollama    | Run LLMs locally (no API key required)      |
| 🤗 HuggingFace / 🧠 ModelScope | LLM model sources            |
| 🐍 Python    | Version 3.10+                               |

---

## 📚 Citations

- [1] Brown et al. (2020). *Language Models are Few-Shot Learners*. NeurIPS.  
- [2] Yu et al. (2018). *Spider: A Large-Scale Human-Labeled Text-to-SQL Dataset*.  
- [3] Touvron et al. (2023). *LLaMA: Open Foundation Models*.  
- [4] Vanna AI. https://github.com/vanna-ai/vanna  
- [5] Ollama. https://ollama.com  
- [6] ChromaDB. https://github.com/chroma-core/chroma  
- [7] Hugging Face. https://huggingface.co/models  
- [8] ModelScope. https://modelscope.cn

---

## 🚧 Limitations

- Complex SQL (e.g., multi-table joins) not fully supported yet  
- Performance depends on the model selected (LLaMA/Mistral/etc.)  
- Accuracy still limited for deeply nested queries or grouped conditions

---

## 📄 License

MIT License
