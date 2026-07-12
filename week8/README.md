# Week 8 Assignment

## Build an Agentic AI pipeline.
Short Quiz and small agent pipeline project.

## Advanced Agentic AI Pipeline Smart Assistant

An intelligent, single-agent AI system designed to parse user intent dynamically and route tasks using deterministic local tools or advanced cognitive inference via the Google Gemini 2.5 API. The application features a high-fidelity cyberpunk dark-mode Gradio user interface.

## 🚀 Features
- Intent-Based Routing: Automatically classifies user queries to map them to specialized tool pipelines or generative models.
- Specialized Local Tools: 
  - Safe Math Calculator: Evaluates mathematical strings locally after strict sanitization (whitelisting operators to secure the execution pipeline).
  - Text Keyword Extractor: Parses text arrays to isolate unique terms with character lengths $> 4$.
- Cognitive Inference Drop: Integrates the google-genai SDK using the gemini-2.5-flash engine for unstructured general inquiries.
- Secure Credential Handling: Collects API keys implicitly using getpass to prevent hardcoding configuration tokens.
- Cyberpunk Interactive Interface: Responsive UI layer packaged with custom CSS injections and dynamic execution route badges.

## 📂 Project Architecture

The system operates as a single-agent stateful routing machine:
``` 
               +-----------------------+
               |      User Query       |
               +-----------+-----------+
                           |
                           v
               +-----------+-----------+
               |  Intent Classification|
               +-----+-----+-----+-----+
                     |     |     |
      +--------------+     |     +---------------+
      | (Math)             | (Keywords)          | (General)
      v                    v                     v
+-----+-----+        +-----+-----+         +-----+-----+
| Calculator|        |  Keyword  |         |  Gemini   |
|   Tool    |        | Extractor |         |2.5-Flash  |
+-----+-----+        +-----+-----+         +-----+-----+
      |                    |                     |
      +--------------------+---------------------+
                           |
                           v
               +-----------+-----------+
               |  Structured JSON/Dict |
               +-----------+-----------+
                           |
                           v
               +-----------+-----------+
               | Custom Gradio Chatbot |
               +-----------------------+
```
--- 

## 🛠️ Tech Stack & Requirements
- Language: Python 3.x
- UI Framework: Gradio
- LLM Service: Google GenAI SDK (gemini-2.5-flash)
- Libraries: os, json, re, getpass

## 📦 Installation & Setup  

- Clone or download this project workspace.
- Install the production dependencies using pip:

```pip install -q google-genai gradio
```
---

- Obtain a valid API Key from Google AI Studio.

## Running the Application

Open the project inside a Jupyter/Google Colab environment and execute the execution blocks sequentially


- Authentication: When prompted, paste your Gemini API Key:
```
Enter your Gemini API Key: (KEY......)
🚀 Gemini Client successfully initialized!
```

- Launch UI: The execution engine will spin up a local and public interface link via Gradio:

```
* Running on public URL: https://<unique-id>.gradio.live  
```

## 📦 Expected Data Contracts
The agent guarantees structural interface uniformity by outputting data objects bound to the following JSON contract signature:

```JSON
{
  "type": "calculation / keywords / general / error",
  "result": "String representation or extracted data arrays matching the target node resolution."
}
```


## Prompt Execution Samples

- Math Intent: "Calculate (1200 / 4) + 50" $\rightarrow$ Returns calculated evaluation string via safe local execution.
- Keyword Intent: "Extract keywords from data science infrastructure..." $\rightarrow$ Evaluates structural tokens locally.
- General Intent: "Explain deep learning in two sentences." $\rightarrow$ Triggers model execution context securely via Gemini.


## 🤝 Contribution & License

Designed and maintained for Agentic Systems Pipelines. Feel free to open issues or pull requests to enhance validation rules, extend pipeline tracking telemetry, or bundle multi-agent networks.


               
