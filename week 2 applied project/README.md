# Week 2 Applied Project: Technical Tutor Chatbot

A chat app that explains code and technical questions step by step. It was built for the Week 2 end-of-week exercise of the LLM engineering course.

## Features

- **Gradio chat UI** built with `gr.ChatInterface`
- **Streaming responses**, so the answer appears as it is generated
- **Model switching** from a dropdown: OpenAI (`gpt-4.1-mini`) or a local Llama model (`llama3.2`) running through Ollama
- **System prompt** that sets the assistant's role as a tutor who explains code step by step

## How it works

Both models are called through the OpenAI Python client. The Llama model is served locally by Ollama, which exposes an OpenAI-compatible API at `http://localhost:11434/v1/`. The dropdown selects which client and model name the `chat` function uses, and the reply is streamed back to Gradio chunk by chunk.

## Requirements

- Python 3.10+
- An OpenAI API key
- [Ollama](https://ollama.com) installed (only needed for the Llama option)

```bash
pip install gradio openai python-dotenv
ollama pull llama3.2
```

## Setup

1. Create a `.env` file next to the notebook:
   ```
   OPENAI_API_KEY=your-key-here
   ```
2. Make sure Ollama is running if you want to use the `llama` option.
3. Open `week2 EXERCISE.ipynb` and run the cells. Gradio prints a local URL (for example `http://127.0.0.1:7860`) that you can open in your browser.

## Usage

1. Choose a model in the **MODEL** dropdown (`openai` or `llama`).
2. Paste a piece of code or ask a technical question.
3. The assistant explains it step by step.

## Possible improvements

- Add tool calling (for example, a function that returns the current time)
- Add audio input and spoken replies
- Write a more detailed system prompt with specific areas of expertise

## Notes

Never commit your `.env` file or API keys. Add `.env` to your `.gitignore`.
