# Autonomous Web-Enabled Market Research Assistant

**Local RAG Chatbot with Real-Time Web Search**  
Built in 3 days using LM Studio | February 2026

### Overview
Engineered a completely private, offline-first AI research assistant that can autonomously search the web and extract targeted data from complex websites — without any paid APIs or rate limits.

### Key Features
- 14B-parameter local models (Qwen/Mistral) optimized for 12GB VRAM with KV-cache tuning for faster inference
- Real-time web search integration via Serper
- Headless browser automation (Playwright) for scraping dynamic content
- Model Context Protocol (MCP) for seamless tool integration
- Hybrid RAG pipeline that dramatically reduces hallucination on current events and market data

### Architecture
- Fully local LLM inference via LM Studio
- MCP server configuration for tool calling
- Dynamic context injection from live web sources
- Zero external API costs or data privacy risks

### How to Run
1. Install LM Studio
2. Load a 14B model (Qwen2.5 or Mistral)
3. Place `mcp.json` in the correct LM Studio folder
4. Enable Serper and Playwright tools
5. Start chatting — the assistant will automatically search and synthesize live data

### Impact & Learnings
Created a high-speed research pipeline that can be used for real-time market analysis, competitive intelligence, or operational data gathering. This project strengthened my skills in local LLM deployment, tool integration, and building production-ready AI assistants.

### Screenshots
![Chat Interface](screenshots/01-chat-interface.png)
![Web Search in Action](screenshots/02-web-search-in-action.png)

### Technologies
LM Studio • Qwen/Mistral 14B • Model Context Protocol (MCP) • Serper • Playwright • RAG

Built as a personal experiment to explore autonomous AI agents and real-time data pipelines.
