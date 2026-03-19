# Autonomous Web-Enabled Market Research Assistant

## Overview
Engineered a completely private, offline-first AI research agent capable of autonomously searching the web and extracting targeted market data from complex websites. This system eliminates paid API dependencies while dynamically injecting live web context to reduce LLM temporal hallucinations.

## Architecture & Hardware Metrics
* **Model Scale:** Utilizes a locally hosted 20B-parameter model (GPT-OSS 20B) operating within a 70,000-token context window.
* **Hardware Optimization:** Zero-cost local inference achieved by offloading 17 model layers to the GPU, maintaining an 11 GB VRAM footprint.
* **Execution Latency:** Achieved sub-15-second automated reasoning and tool-calling cycles for dynamic data extraction.
* **Tool Integration:** Utilizes the Model Context Protocol (MCP) to seamlessly integrate Playwright (headless browser automation) and Serper (real-time search) directly into the agent's reasoning loop.


## How to Run
1. Install [LM Studio](https://lmstudio.ai/).
2. Load a compatible local model (e.g., GPT-OSS 20B, Qwen2.5 14B, Mistral 14B).
3. Place `mcp.json` in the LM Studio configuration directory to enable MCP tools.
4. Enable the Serper and Playwright tools within the UI.
5. Initialize the chat to begin autonomous web extraction.

## System Prompt Engineering
To ensure the model optimally utilized its tools within hardware constraints and avoided infinite loops, a highly structured system prompt was deployed: 

"You are an autonomous web automation and research agent. You have access to a headless browser via the Playwright MCP tool. Your objective is to execute web navigation, extraction, and automation tasks accurately and systematically. 

You must strictly adhere to the following rules for every action:

1. ONE ACTION PER STEP: Do not attempt to chain multiple browser commands (e.g., navigating, filling a form, and clicking) in a single tool call. Execute one action, wait for the observation, and then plan the next.
2. VERIFY DOM STATE: Before attempting to click, fill, or extract data from an element, you must verify its exact selector exists in the current DOM. Do not guess selectors. 
3. PACE YOURSELF: Websites render dynamically. If an expected element is missing, assume the page is still loading. Wait or check for loading spinners before throwing an error.
4. CLEAR OBSTACLES FIRST: The moment you navigate to a new URL, immediately scan the DOM for cookie consent banners, newsletter popups, or modal overlays. You must close or accept these before attempting your primary task.
5. HANDLE FAILURES GRACEFULLY: If a tool call fails or returns an error (e.g., "element not interactable"), do not blindly repeat the exact same command. Analyze the error, adjust your selector or strategy, and try an alternative approach."

### Impact & Learnings
Created a high-speed research pipeline that can be used for real-time market analysis, competitive intelligence, or operational data gathering. This project strengthened my skills in local LLM deployment, tool integration, and building production-ready AI assistants.

### Screenshots
![Chat Interface](screenshots/01-chat-interface.png)
![Web Search in Action](screenshots/02-web-search-in-action.png)
![FinalResults](screenshots/FinalResult.png)


### Technologies
LM Studio • Qwen/Mistral 14B and GPT-OSS 20B • Model Context Protocol (MCP) • Serper • Playwright • RAG


Built as a personal experiment to explore autonomous AI agents and real-time data pipelines.
