# Week 3 Applied Project: CodeCoach (AI Coding Tutor)

This project is an AI-powered coding tutor named **CodeCoach**. It is designed to help learners understand programming concepts by providing step-by-step explanations of code snippets, rather than just giving the answers.

## 🚀 Features
- **LLM Integration:** Uses Meta's `meta-llama/Llama-3.2-3B-Instruct` model via Hugging Face.
- **Memory Efficient:** Implements 4-bit quantization (`BitsAndBytesConfig`) to allow the model to run smoothly on a Google Colab T4 GPU.
- **Persona-Driven:** Uses a custom system prompt to ensure the AI acts as a friendly, patient, and encouraging tutor.
- **Streaming Output:** Utilizes `TextStreamer` to print the response as it is being generated.

## 🛠️ Technologies Used
- **Python**
- **Hugging Face Transformers** (`AutoModelForCausalLM`, `AutoTokenizer`)
- **PyTorch**
- **BitsAndBytes** (for 4-bit quantization)
- **Google Colab** (T4 GPU environment)

## 📋 How to Run the Project
1. Open the `code_tutor_using_huggingface.ipynb` notebook in Google Colab.
2. Make sure you have a GPU enabled (Runtime -> Change runtime type -> T4 GPU).
3. You will need to set up your API keys in the Colab "Secrets" tab (the key icon on the left sidebar):
   - `j_lol` : Your Hugging Face Access Token.
   - `OPENAI_API_KEY` : (Optional/Imported in this notebook, but not strictly used in the core Llama logic).
4. Run the cells sequentially. 
5. The final cell will test the model by asking it to explain a simple Python `for` loop.

## 💻 Example Usage
When you run the function:
```python
code_tutor("for i in range(3):\n    print(i * 2)", choosen_model=LLAMA, max_new_tokens=200, quantization=True)
