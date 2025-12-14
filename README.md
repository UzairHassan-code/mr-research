## Mr. Research 🤖

The Verifiable Autonomous Research Agent
Mr. Research is not just another chatbot. It is a Multi-Agent System designed to perform deep, verifiable research. Unlike standard LLMs that hallucinate facts, Mr. Research follows a strict workflow: Plan → Research → Summarize → Fact-Check.

It uses LangGraph to manage state, Google Gemini for reasoning, and Tavily for live web data, ensuring that every answer is backed by real-time sources and verified for accuracy.

# 🚀 Key Features

🧠 Multi-Agent Orchestration: Specialized agents for planning, retrieving, summarizing, and fact-checking.

✅ Human-in-the-Loop: The workflow pauses after planning, allowing the user to approve or modify the research path before execution.

🕵️ Fact-Checking Layer: A dedicated step where the AI reviews its own summary against raw sources to flag unsupported claims.

🌐 Live Web Access: Uses the Tavily API to fetch real-time data, bypassing the training data cutoff.

🔄 Stateful Memory: Remembers context for follow-up questions without restarting the research process.

⚡ Modern Frontend: A clean, dark-mode interface built with Next.js 14 and Tailwind CSS.

🏗 Architecture
The system is built on LangGraph, creating a cyclic graph workflow. Here is the logic flow:

### Code snippet

graph TD
    
    Start([User Query]) --> Router{Router}
    
    Router -->|New Topic| Planner[Generate Plan]
    Router -->|Follow Up| Answer[Answer Follow-Up]
    
    Planner -->|Wait for Approval| Human((Human Review))
    Human --> Retriever[Retrieve Info (Tavily)]
    
    Retriever --> Summarizer[Summarize Results]
    Summarizer --> FactChecker[Fact Check Report]
    FactChecker --> Final[Generate Final Answer]
    
    Final --> End([End])
    Answer --> End
    
### 🛠 Tech Stack

Backend
Language: Python

Orchestration: LangGraph

LLM: Google Gemini 1.5 Flash (via langchain-google-genai)

Search Tool: Tavily Search API

Framework: LangChain

Frontend
Framework: Next.js 14 (App Router)

Styling: Tailwind CSS

Icons: Lucide React

### ⚙️ Installation & Setup
Prerequisites
Python 3.10+

Node.js 18+

API Keys for Google Gemini and Tavily.

1. Backend Setup
Bash

# Clone the repository
git clone https://github.com/UzairHassan-code/mr-research.git
cd mr-research/backend

# Create virtual environment
python -m venv venv
source venv/bin/activate  
On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
Create a .env file in the backend folder:

# Code snippet

GOOGLE_API_KEY=your_google_gemini_key
TAVILY_API_KEY=your_tavily_key

2. Frontend Setup
Bash

# Navigate to frontend directory
cd ../frontend

# Install dependencies
npm install

# Run the development server
npm run dev
🧩 How It Works
The Planner: Upon receiving a query, the agent generates a numbered list of search topics.

The Review: (Optional configuration) The system pauses. You can confirm the plan.

The Hunt: The agent executes the search queries using Tavily, gathering raw content from URLs.

The Synthesis: The raw data is condensed into a summary.

The Audit: The Fact-Checker Agent compares the Summary vs. Raw Data. If the summary claims "X happened," but the raw data doesn't support it, the agent flags it.

The Result: You receive a polished answer with cited sources and a verification report.

### 🤝 Contributing
Contributions are welcome! Please feel free to submit a Pull Request.

Fork the Project

Create your Feature Branch (git checkout -b feature/AmazingFeature)

Commit your Changes (git commit -m 'Add some AmazingFeature')

Push to the Branch (git push origin feature/AmazingFeature)

Open a Pull Request
