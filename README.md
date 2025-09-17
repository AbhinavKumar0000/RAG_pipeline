# WebInsight Querry Hub: Chat with Your Documents

[![Python Version](https://img.shields.io/badge/Python-3.9%2B-blue.svg)](https://python.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

WebInsight is a powerful and interactive application that allows you to chat with your own documents. Built with the **Retrieval-Augmented Generation (RAG)** architecture, it leverages Google's state-of-the-art Gemini models to understand and answer questions based on the content of provided web pages and PDF files.

This tool transforms static documents into a dynamic, conversational knowledge base, ensuring that the answers you receive are accurate, context-aware, and directly sourced from your provided materials.



---

## ✨ Features

* **Multi-Source Ingestion**: Load and process information directly from both public **website URLs** and uploaded **PDF documents**.
* **Interactive Chat UI**: A simple and intuitive web interface built with **Gradio** makes the application accessible to everyone.
* **Powered by Google Gemini**: Utilizes the **Gemini-1.5-Flash** model for fast and intelligent answer generation and Google's models for high-quality text embeddings.
* **High-Speed Similarity Search**: Employs **FAISS** to create an efficient, in-memory vector index for near-instant retrieval of relevant information.
* **Text-to-Speech Output**: 🔊 Listen to the generated answers with an integrated **Google Cloud Text-to-Speech** feature for enhanced accessibility.
* **Source Verification**: Responses include the sources from which the information was retrieved, ensuring transparency and trustworthiness.

---

## 🛠️ Tech Stack & Architecture

This project is built with a modern, end-to-end RAG pipeline:

* **Backend**: Python
* **LLM Framework**: LangChain
* **LLM & Embeddings**: Google Gemini
* **Vector Store**: FAISS (Facebook AI Similarity Search)
* **Web UI**: Gradio
* **Text-to-Speech**: Google Cloud Text-to-Speech API

### Application Workflow
The application follows a standard RAG pipeline:
1.  **Ingestion**: User provides URLs or PDFs through the Gradio UI.
2.  **Processing**: LangChain loads and splits the documents into text chunks.
3.  **Indexing**: Each chunk is converted into a vector embedding by Google's model and stored in a FAISS index.
4.  **Retrieval**: When a question is asked, its vector is used to find the most similar document chunks from the FAISS index.
5.  **Generation**: The retrieved chunks (context) and the user's question are passed to the Gemini LLM, which generates a final, source-based answer.
6.  **Output**: The answer is displayed in the Gradio UI and can be converted to audio.

---

## 🚀 Getting Started

Follow these steps to set up and run the project on your local machine.

### 1. Prerequisites
* Python 3.9 or higher
* A Google Cloud account with the **"Cloud Text-to-Speech API"** enabled.
* A Google API Key for Gemini. You can get one from [Google AI Studio](https://aistudio.google.com/app/apikey).

### 2. Installation & Setup
1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/AbhinavKumar0000/RAG_pipeline](https://github.com/AbhinavKumar0000/RAG_pipeline)
    cd YOUR_REPOSITORY_NAME
    ```

2.  **Create a virtual environment (recommended):**
    ```bash
    python -m venv venv
    # On Windows
    venv\Scripts\activate
    # On macOS/Linux
    source venv/bin/activate
    ```

3.  **Install the required libraries:**
    ```bash
    pip install -r requirements.txt
    ```

4.  **Set up your API keys and credentials:**
    * **Gemini API Key**: Create a file named `.env` in the root directory and add your Google API Key:
        ```
        GOOGLE_API_KEY="Your...Key...Here"
        ```
    * **Google Cloud TTS Credentials**:
        * Go to your Google Cloud project, create a service account, and download the JSON key file.
        * Set an environment variable that points to the path of this JSON file.
        ```bash
        # On macOS/Linux
        export GOOGLE_APPLICATION_CREDENTIALS="/path/to/your/key.json"
        # On Windows (Command Prompt)
        set GOOGLE_APPLICATION_CREDENTIALS="C:\path\to\your\key.json"
        ```

### 3. Running the Application
Once the setup is complete, launch the Gradio web server with the following command:
```bash
python app.py
