# 🎯 AI Resume Job Matching System

![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python)
![NLP](https://img.shields.io/badge/NLP-Sentence_Transformers-yellow)
![LLM](https://img.shields.io/badge/LLM-OpenAI_GPT--4-412991?logo=openai)
![Streamlit](https://img.shields.io/badge/Deployed-Streamlit_Cloud-FF4B4B?logo=streamlit)

> **Paste your resume and a job description. Get an instant AI-powered match score, skill gap analysis, and actionable improvement suggestions.**

🔗 **[Live Demo](https://ai-resume-matcher-vsmxaig3vfeer7unne8ycm.streamlit.app)**

---

## 📌 What This Project Does

Job searching is frustrating when you don't know *why* your resume isn't getting responses. This tool gives you the answer — it uses semantic NLP and LLM analysis to score your resume against any job description and tell you exactly what's missing.

**What you get:**
- 📊 A match score (0–100%) based on semantic similarity
- ❌ Missing skills and keywords the JD requires but your resume lacks
- ✅ Strengths — what's already aligned well
- 💡 Specific, actionable suggestions to improve your resume for that role

---

## 🏗️ Architecture

```
Resume Text  ──┐
               ├──► Sentence Transformer Encoding
Job Desc Text ──┘              │
                               ▼
                    Cosine Similarity Score
                               │
                               ▼
               ┌───────────────────────────────┐
               │  LLM Analysis (GPT-4)         │
               │  - Identify skill gaps        │
               │  - Surface matched skills     │
               │  - Generate suggestions       │
               └───────────────────────────────┘
                               │
                               ▼
                    Streamlit Results Dashboard
```

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Semantic Similarity | Sentence Transformers (`all-MiniLM-L6-v2`) |
| LLM Analysis | OpenAI GPT-4 |
| Orchestration | LangChain |
| Frontend | Streamlit |
| Deployment | Streamlit Cloud |

---

## ✨ Key Features

- 🧠 **Semantic matching** — understands meaning, not just keyword overlap (e.g. "built data pipelines" matches "ETL development")
- 🔍 **Skill gap analysis** — identifies specific missing skills ranked by importance to the JD
- 💬 **LLM-generated suggestions** — concrete rewrite recommendations, not generic advice
- ⚡ **Instant results** — full analysis in under 10 seconds
- 🔐 **Privacy-first** — no resume data stored; all processing is stateless

---

## 🚀 How to Run Locally

```bash
# Clone the repo
git clone https://github.com/madhavi-akella-Lab/ai-resume-matcher
cd ai-resume-matcher

# Install dependencies
pip install -r requirements.txt

# Set your API key
export OPENAI_API_KEY=your_key_here

# Run
streamlit run app.py
```

---

## 📁 Project Structure

```
ai-resume-matcher/
│
├── app.py                  # Streamlit UI
├── matcher.py              # Semantic similarity scoring
├── gap_analyzer.py         # LLM-based gap analysis and suggestions
├── requirements.txt
└── README.md
```

---

## 💡 How It Works

### Step 1 — Semantic Similarity Scoring
Both the resume and job description are encoded using the `all-MiniLM-L6-v2` Sentence Transformer model, producing dense vector representations. Cosine similarity between these vectors produces a meaningful match score that goes beyond simple keyword matching — it understands *context*.

### Step 2 — LLM Gap Analysis
The resume and JD text are passed to GPT-4 with a structured prompt asking it to:
- Identify skills/qualifications in the JD not evidenced in the resume
- Identify strong alignment areas
- Generate 3–5 specific, actionable resume improvement suggestions

### Step 3 — Results Display
Results are rendered in a clean Streamlit dashboard with the match score, a color-coded skills breakdown, and the improvement suggestions ready to act on.

---

## 📊 Sample Output

```
Match Score: 74%

✅ Strong Matches:
  • Python, SQL, ETL pipelines
  • AWS cloud experience
  • Data warehousing (Snowflake)

❌ Gaps Identified:
  • dbt (data build tool) — mentioned 3x in JD
  • Airflow orchestration
  • CI/CD pipeline experience

💡 Suggestions:
  1. Add a bullet mentioning any scheduling tools (Autosys/Control-M map to Airflow experience)
  2. Highlight Databricks Delta Live Tables as equivalent to dbt patterns
  3. Add "version-controlled pipeline deployment" to your ETL migration project bullet
```

---

## 🔮 Future Enhancements

- [ ] PDF resume upload support
- [ ] Side-by-side resume editor with live score updates
- [ ] Batch mode — score one resume against multiple JDs
- [ ] ATS keyword density analysis

---

## 👩‍💻 About the Author

**Madhavi Akella** — Data & AI Engineer | Databricks Generative AI Engineer Associate

🔗 [LinkedIn](https://linkedin.com/in/madhavi-akella-Lab-2b8213114) | 🌐 [Portfolio](https://madhavi-akella-Lab.dev)
