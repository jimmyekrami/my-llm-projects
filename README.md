# Week 3 Applied Project — Code Tutor Using Hugging Face

## Overview

This project explores a small AI coding tutor named **CodeCoach**. It takes a programming snippet and asks an instruction-tuned language model to explain the code step by step. The notebook uses the Hugging Face Transformers library to load `meta-llama/Llama-3.2-3B-Instruct`, with optional 4-bit quantization to reduce GPU memory use.

## Features

- Explains code step by step in a friendly, beginner-focused style.
- Gives debugging guidance and small examples.
- Uses a configurable Hugging Face causal language model.
- Supports optional 4-bit quantization with `bitsandbytes`.
- Demonstrates generating and displaying a model response in a notebook.

## Project file

- `code_tutor_using_huggingface.ipynb` — the main Jupyter/Google Colab notebook.

## Requirements

The notebook is designed for **Google Colab with a GPU runtime**. It uses these Python packages:

- `torch`
- `transformers`
- `huggingface_hub`
- `bitsandbytes`
- `openai`
- `gradio` (imported in the notebook)

Install dependencies in a notebook cell if needed:

```bash
pip install -U transformers huggingface_hub bitsandbytes openai gradio
```

A compatible CUDA GPU runtime is expected because the model inputs are moved to `cuda`. Quantization support depends on the runtime and hardware.

## Setup

1. Upload or open the notebook in Google Colab.
2. In Colab, select **Runtime → Change runtime type → T4 GPU** (or another compatible GPU, if available).
3. Add your Hugging Face access token to Colab Secrets under the name `j_lol`.
4. Add an OpenAI API key to Colab Secrets under the name `OPENAI_API_KEY`.
5. Make sure your Hugging Face account has access to `meta-llama/Llama-3.2-3B-Instruct` and has accepted any required model terms.
6. Run the notebook cells from top to bottom.

> **Secrets:** Never paste API keys or access tokens into a notebook, commit them to GitHub, or print them in output. The notebook reads them from Colab Secrets. The current code creates an OpenAI client, but the demonstrated `code_tutor()` function generates responses with the local Hugging Face model.

## Example

The notebook includes an example using:

```python
for i in range(3):
    print(i * 2)
```

The tutor is prompted to explain what the code does step by step.

## Notes and limitations

- Loading the model may take several minutes and requires sufficient GPU memory.
- The current function uses a local Hugging Face model; it does not yet provide an OpenAI-backed model path or a Gradio interface, despite importing those libraries.
- The notebook's `code_tutor()` function uses `choosen_model` as the model ID argument.
- Model responses may be incomplete or inaccurate, so verify explanations and code before relying on them.

## Future improvements

- Add a Gradio interface for entering code and viewing explanations.
- Add a separate OpenAI API implementation and a model selector.
- Improve output decoding so the displayed response contains only newly generated text.
- Add error handling for missing secrets, unavailable GPUs, and model-access errors.
