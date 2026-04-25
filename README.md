# 📈 Stock Analysis — AI-Powered Stock Research Tool

An AI-driven stock research system powered by **CrewAI multi-agent orchestration**, **LangChain**, and **Llama 3.1** (via Ollama). The system deploys a crew of specialized AI agents that collaboratively perform financial analysis, research, SEC filings review, and investment recommendations for any given stock.

---

## 🚀 Features

- **Multi-Agent Architecture** — A coordinated crew of AI agents, each with a focused role: financial analyst, research analyst, and investment advisor.
- **SEC Filings Analysis** — Automatically fetches and analyzes SEC 10-K (annual) and 10-Q (quarterly) filings using the SEC API.
- **Web Research** — Agents scrape financial news, analyst reports, and market data in real time.
- **Investment Recommendations** — The investment advisor agent synthesizes all findings into actionable buy/hold/sell recommendations.
- **Fully Local LLM** — Runs on **Llama 3.1** via Ollama — no OpenAI API required for inference.
- **Sequential Processing Pipeline** — Tasks are executed in a structured, sequential workflow to ensure each agent builds on prior results.

---

## 🧠 Agent Crew

| Agent | Role | Tools |
|---|---|---|
| **Financial Analyst** | Analyzes financial statements, ratios, and SEC filings | ScrapeWebsite, WebsiteSearch, Calculator, SEC10K, SEC10Q |
| **Research Analyst** | Gathers market intelligence, news, and industry data | ScrapeWebsite, SEC10K, SEC10Q |
| **Investment Advisor** | Synthesizes research into investment recommendations | ScrapeWebsite, WebsiteSearch, Calculator |

---

## 🛠️ Tech Stack

- **[CrewAI](https://github.com/joaomdmoura/crewAI)** — Multi-agent orchestration framework
- **[LangChain](https://github.com/langchain-ai/langchain)** — LLM abstraction and tooling
- **[Llama 3.1](https://ollama.com/library/llama3.1)** (via Ollama) — Local large language model
- **[SEC API](https://sec-api.io/)** — Access to SEC 10-K and 10-Q filings
- **[Serper API](https://serper.dev/)** — Google search for web research
- **[Browserless](https://www.browserless.io/)** — Headless browser for website scraping
- **Python 3.12 / 3.13** — Core language runtime
- **[uv](https://github.com/astral-sh/uv)** — Fast Python package manager

---

## 📁 Project Structure

```
Stock-Analysis/
├── stock_analysis/
│   ├── config/
│   │   ├── agents.yaml        # Agent role definitions and goals
│   │   └── tasks.yaml         # Task descriptions and expected outputs
│   ├── tools/
│   │   ├── calculator_tool.py # Custom calculator tool for financial math
│   │   └── sec_tools.py       # SEC 10-K and 10-Q retrieval tools
│   ├── crew.py                # CrewAI crew, agent, and task definitions
│   ├── main.py                # Entry point — run or train the crew
│   └── __init__.py
├── env.example                # Example environment variable configuration
├── pyproject.toml             # Project dependencies and scripts
└── README.md
```

---

## ⚙️ Prerequisites

- **Python 3.12 or 3.13**
- **[Ollama](https://ollama.com/)** installed and running locally with the `llama3.1` model pulled
- **API keys** for Serper, Browserless, and SEC API (all have free tiers)

---

## 🔧 Installation

**1. Clone the repository**
```bash
git clone https://github.com/sahilbagoriya7688/Stock-Analysis.git
cd Stock-Analysis
```

**2. Install dependencies using uv**
```bash
pip install uv
uv sync
```

Or with standard pip:
```bash
pip install -e .
```

**3. Pull the Llama 3.1 model via Ollama**
```bash
ollama pull llama3.1
```

**4. Configure environment variables**
```bash
cp env.example .env
```

Then edit `.env` with your API keys:
```env
SERPER_API_KEY=your_key_here        # https://serper.dev/ (free tier)
BROWSERLESS_API_KEY=your_key_here   # https://www.browserless.io/ (free tier)
SEC_API_API_KEY=your_key_here       # https://sec-api.io/ (free tier)
OPENAI_API_KEY=your_key_here        # Optional fallback
```

---

## ▶️ Usage

**Run the stock analysis crew:**
```bash
stock_analysis
```

Or directly via Python:
```bash
python -m stock_analysis.main
```

**Train the crew:**
```bash
train
```

---

## 🔄 How It Works

The crew runs in a **sequential pipeline**:

1. **Research Task** — The Research Analyst scrapes financial news, market data, and SEC filings to build a comprehensive research report.
2. **Financial Analysis Task** — The Financial Analyst digs into financial statements, computes key ratios, and evaluates performance using SEC 10-K/10-Q data.
3. **Filings Analysis Task** — A deep dive into SEC filings to identify risk factors, business changes, and management commentary.
4. **Recommendation Task** — The Investment Advisor synthesizes all prior outputs and delivers a final investment recommendation with supporting rationale.

---

## 🔑 API Keys

| Service | Purpose | Link |
|---|---|---|
| Serper API | Web search for research agents | [serper.dev](https://serper.dev/) |
| Browserless | Headless web scraping | [browserless.io](https://www.browserless.io/) |
| SEC API | Access to SEC 10-K & 10-Q filings | [sec-api.io](https://sec-api.io/) |

All three services offer **free tiers** sufficient for development and testing.

---

## 📄 License

This project is open source. Feel free to fork, extend, and adapt it for your own research needs.

---

## 🤝 Contributing

Pull requests are welcome! If you would like to add new agents, tools, or support for additional data sources (e.g., Yahoo Finance, earnings call transcripts), feel free to open an issue or submit a PR.

---

*Built with CrewAI · LangChain · Llama 3.1 · SEC API*
