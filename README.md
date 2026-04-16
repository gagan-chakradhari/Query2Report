```markdown
# 🔬 Multi-Agent Research System

**AI-powered automated research agent** that conducts research on any topic, gathers information, writes detailed reports, and critically reviews them—all without human intervention.

---

## ✨ Features

✅ **Automated Web Search** - Uses Tavily API to find relevant information  
✅ **Smart Content Scraping** - Extracts detailed content from top URLs  
✅ **AI Report Writing** - Generates structured research reports using GPT-4  
✅ **Quality Review** - Built-in critic agent that scores and reviews reports  
✅ **Beautiful UI** - Interactive web interface powered by Streamlit  
✅ **Multi-Agent Collaboration** - Multiple specialized agents work together  

---

## 🏗️ Architecture

```
Topic Input
    ↓
[Step 1] Search Agent → Web Search (Tavily API)
    ↓
[Step 2] Reader Agent → Content Scraping (BeautifulSoup)
    ↓
[Step 3] Writer Chain → Report Generation (GPT-4o-mini)
    ↓
[Step 4] Critic Chain → Quality Review & Scoring
    ↓
Final Report + Feedback
```

---

## 📋 Project Structure

```
.
├── agents.py         # Agent definitions & chains
├── tools.py          # Web search & scraping tools
├── pipeline.py       # Main orchestration logic
├── app.py            # Streamlit web interface
├── requirements.txt  # Python dependencies
├── .env              # API keys (not in git)
└── README.md         # This file
```

---

## 🚀 Setup & Installation

### Prerequisites
- Python 3.8 or higher
- OpenAI API key
- Tavily API key

### Step 1: Clone Repository
```bash
git clone https://github.com/YOUR_USERNAME/multi-agent-research-system.git
cd multi-agent-research-system
```

### Step 2: Create Virtual Environment
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

### Step 3: Install Dependencies
```bash
pip install -r requirements.txt
```

### Step 4: Setup API Keys
Create a `.env` file in the root directory:
```
OPENAI_API_KEY=your_openai_key_here
TAVILY_API_KEY=your_tavily_key_here
```

Get API keys from:
- **OpenAI**: https://platform.openai.com/api-keys
- **Tavily**: https://tavily.com

### Step 5: Run Application
```bash
streamlit run app.py
```

Open your browser → `http://localhost:8501`

---

## 📖 How It Works

1. **Enter Research Topic** → System receives the topic for research
2. **Search Phase** → Finds 5 relevant sources from the internet
3. **Scraping Phase** → Extracts detailed content from best URLs
4. **Writing Phase** → Generates structured report with Introduction, Key Findings, Conclusion
5. **Critique Phase** → Reviews report and provides score (0-10) with feedback

---

## 🛠️ Technology Stack

- **LLM Model**: OpenAI GPT-4o-mini
- **Framework**: LangChain
- **Web Search**: Tavily API
- **Web Scraping**: BeautifulSoup4 + Requests
- **Frontend**: Streamlit
- **Async Support**: aiohttp
- **Environment**: python-dotenv

---

## 💻 CLI Usage

Run research from command line:

```bash
python pipeline.py
# Then enter your research topic when prompted
```

---

## 🐍 Python API Usage

```python
from pipeline import run_research_pipeline

# Run research on a topic
result = run_research_pipeline("Machine Learning in Finance")

# Access individual components
search_results = result['search_results']
scraped_content = result['scraped_content']
report = result['report']
feedback = result['feedback']

print(report)
print(feedback)
```

---

## 📝 Output Example

```
FINAL REPORT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Introduction
Provides background and context on the topic.

Key Findings
- Finding #1: Detailed explanation
- Finding #2: Detailed explanation
- Finding #3: Detailed explanation

Conclusion
Summarizes the research findings.

Sources
- https://source1.com
- https://source2.com
- https://source3.com

CRITIC FEEDBACK
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Score: 8.5/10

Strengths:
- Well-structured content
- Credible sources

Areas to Improve:
- Add more recent data
- Expand on methodology
```

---

## ⚙️ Configuration

Edit agents.py to customize behavior:

```python
# Change model
llm = ChatOpenAI(model="gpt-4o-mini", temperature=0)

# Adjust temperature:
# 0 = Deterministic (same output every time)
# 1 = Creative (varied outputs)
```

Edit prompts in agents.py:
- `writer_prompt` - Controls report structure and style
- `critic_prompt` - Controls review criteria

---

## 🔧 Troubleshooting

| Problem | Solution |
|---------|----------|
| **API Key Error** | Ensure `.env` file exists with correct API keys |
| **ModuleNotFoundError** | Run `pip install -r requirements.txt` again |
| **Scraping Fails** | Some URLs may be blocked; system tries alternative sources |
| **Slow Performance** | Consider switching to `gpt-3.5-turbo` for faster responses |
| **Port 8501 in Use** | Run `streamlit run app.py --server.port 8502` |
| **Timeout Errors** | Increase timeout in tools.py or check internet connection |

---

## 📦 Dependencies

| Package | Purpose |
|---------|---------|
| `langchain` | Agent & chain orchestration |
| `openai` | GPT-4 API access |
| `tavily-python` | Web search functionality |
| `streamlit` | Web UI framework |
| `beautifulsoup4` | HTML parsing & scraping |
| `requests` | HTTP requests |
| `python-dotenv` | Environment variable management |

Install all with:
```bash
pip install -r requirements.txt
```

---

## 🚀 Advanced Features

### Custom Topics
```python
topics = [
    "Quantum Computing Breakthroughs 2025",
    "Renewable Energy Solutions",
    "AI Ethics and Privacy"
]

for topic in topics:
    result = run_research_pipeline(topic)
```

### Batch Processing
Extend pipeline.py to process multiple topics and save results to database.

---

## 📋 Limitations & Considerations

- ⏱️ **Time**: Full research takes 30-60 seconds
- 💰 **Cost**: Each run uses OpenAI and Tavily API tokens
- 🔗 **Connectivity**: Requires active internet connection
- 📄 **Accuracy**: Depends on source quality and AI model
- 🚫 **Paywalls**: Cannot access paywalled content

---

## 🔮 Future Enhancements

- [ ] Multi-language support
- [ ] PDF/Word export functionality
- [ ] Research history database
- [ ] Parallel URL scraping
- [ ] Custom prompt templates
- [ ] Research comparison tool
- [ ] Citation formatting (APA, MLA, Chicago)
- [ ] Fact-checking integration
- [ ] Source credibility scoring

---

## 📄 License

MIT License - Free to use, modify, and distribute

---

## 🤝 Contributing

Contributions are welcome! Please:
1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

---

## 📧 Support & Issues

Found a bug? Have a suggestion?
- Open an issue on GitHub
- Check existing issues first
- Provide clear description and steps to reproduce

---

## 👨‍💻 Author

Created as an AI research automation tool

---

## 🙏 Acknowledgments

- Built with **LangChain** framework
- Uses **OpenAI GPT-4o-mini** model
- Powered by **Tavily Search API**
- UI with **Streamlit**

---

**Happy Researching! 🎓**
```
