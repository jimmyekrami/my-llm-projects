# Technical Question Explainer

A tool that takes a technical question and returns an explanation,
using the OpenAI API (gpt-4o-mini) and a local model through Ollama (llama3.2).

## How to run
1. Add your own OPENAI_API_KEY to a .env file
2. Install Ollama and run: ollama pull llama3.2
3. Open the notebook and run all cells

## What I learned
- Calling the OpenAI API
- Running an open-source model locally with Ollama
- Comparing the outputs of the two models
## My addition
A text summarization function that streams the response from gpt-4.1-mini.
The system prompt makes the model always answer in Arabic.