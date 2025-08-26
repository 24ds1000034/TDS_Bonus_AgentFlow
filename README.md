# TDS_AgentFlow – Web-Based Multi-Tool AI System

IntelliFlow is a browser-based intelligent agent framework designed to coordinate multiple computational tools in a reasoning-driven cycle. It integrates large language models (LLMs), search APIs, and browser-based code execution to accomplish complex tasks autonomously.

---

## Features

- **Multi-LLM Compatibility**
  - Works with OpenAI, Anthropic, and Google models

- **Integrated Tooling**
  - Google Search API for real-time information retrieval  
  - AI Pipe API for customizable workflows (summarization, sentiment analysis, etc.)  
  - Secure JavaScript execution within the browser  

- **Adaptive Reasoning**
  - Iterative decision-making loop that continues until the task is complete  

- **User-Friendly Interface**
  - Responsive and modern design with robust error handling  

---

## Installation & Setup

1. Open `index.html` in a modern web browser.  
2. Configure required API keys:
   - **LLM Provider Key** (OpenAI, Anthropic, or Google)  
   - **Google Search API Key**  
   - **Custom Search Engine ID**  

---

### Obtaining API Keys

#### OpenAI
- [Generate API Key](https://platform.openai.com/api-keys)

#### Google Search
1. Go to [Google Cloud Console](https://console.cloud.google.com/)  
2. Enable *Custom Search JSON API*  
3. Generate API key and configure [Custom Search Engine](https://cse.google.com/)  

#### Anthropic
- [Generate API Key](https://console.anthropic.com/) for Claude models  

---

## Example Use Cases

### Research Assistant
```plaintext
Prompt: "Summarize recent advancements in quantum computing"
```
- Retrieves relevant research  
- Produces structured summary  

### Data Analysis
```plaintext
Prompt: "Generate sample data and compute statistics"
```
- Runs in-browser JavaScript  
- Produces statistical insights  

### Interview Assistant
```plaintext
Prompt: "Interview me for a blog post on IBM"
```
- Gathers background info  
- Structures an interview-based article  

---

## Tool Modules

### 🔍 Google Search
- Real-time web retrieval  
- Adjustable number of results  

### 🤖 AI Pipe API
- Summarization, keyword extraction, sentiment analysis, translation  

### 💻 JavaScript Execution
- Secure execution within browser sandbox  
- Captures console output  
- Syntax-highlighted results  

---

## Architecture Overview

### Agent Reasoning Cycle
```javascript
async agentCycle() {
    while (true) {
        const reply = await this.queryLLM();
        if (reply.content) this.addMessage('agent', reply.content);

        if (reply.tool_calls?.length > 0) {
            const results = await Promise.all(
                reply.tool_calls.map(tc => this.processToolCall(tc))
            );
        } else {
            break;
        }
    }
}
```

### Tool Invocation Schema (OpenAI-style function calling)
```json
{
  "type": "function",
  "function": {
    "name": "google_search",
    "description": "Retrieve information via Google Search",
    "parameters": {
      "type": "object",
      "properties": {
        "query": {"type": "string"},
        "num_results": {"type": "integer"}
      }
    }
  }
}
```

---

## Built-in Demo Functions

```javascript
demo.fibonacci(10)       // Fibonacci sequence
demo.isPrime(17)         // Prime number check
demo.generateData(10)    // Random dataset generation
```

---

## Error Handling

- User-friendly alerts  
- Automatic API error recovery  
- Input validation  
- Safe code execution in browser sandbox  

---

## Browser Support

- Chrome 80+  
- Firefox 75+  
- Safari 13+  
- Edge 80+  

---

## Security

- API keys stored in browser session only  
- No server-side execution  
- CORS restrictions apply for external APIs  

---

## Roadmap / Extensions

- Document upload and analysis  
- Image generation integration  
- Voice interface (speech-to-text)  
- Export options (PDF/Markdown)  
- Plugin system for extensibility  
- Local storage for persistence  

---

## Troubleshooting

- **Missing API key** → Verify credentials  
- **Google Search errors** → Check API key, CSE ID, and quota  
- **CORS restrictions** → Use proxy setup if needed  
- **Tool execution errors** → Validate code syntax and connectivity  

---

## License

Released under the **MIT License**.  

---

## Author

Developed by **24DS1000034 - George**  
Showcasing the potential of browser-based AI reasoning with integrated multi-tool workflows.
