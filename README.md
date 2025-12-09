# RAG Verification Agent

This project implements an intelligent Verification Agent that combines local knowledge retrieval with external web search to provide accurate and verified answers.

The agent ingests a PDF report, stores its content in a local vector database (ChromaDB), and answers user queries by synthesizing information from the PDF. It then supplements and verifies this information using real-time web search (Tavily).

## Features

- **PDF Ingestion**: Extracts text from PDF documents and chunks them for processing.
- **RAG (Retrieval-Augmented Generation)**: Uses ChromaDB to store and retrieve relevant context from the PDF.
- **Web Verification**: validats and supplements internal knowledge with Tavily Web Search.
- **Gemini Powered**: Utilizes Google's Gemini models for embedding and response generation.

## Prerequisites

- Python 3.x
- Google Gemini API Key
- Tavily API Key

## Installation

1. Clone the repository (if applicable) or navigate to the project directory.

2. **Create and Activate a Virtual Environment** (Recommended):
   Isolate your project dependencies by creating a virtual environment.

   *Windows*:
   ```bash
   python -m venv venv
   .\venv\Scripts\activate
   ```

   *macOS/Linux*:
   ```bash
   python3 -m venv venv
   source venv/bin/activate
   ```

3. **Install Dependencies**:
   Once the virtual environment is active, install the required packages using the provided `requirements.txt` file:
   ```bash
   pip install -r requirements.txt
   ```

## Setup

1. **Environment Variables**:
   Create a `.env` file in the root directory and add your API keys:
   ```env
   GOOGLE_API_KEY=your_gemini_api_key
   TAVILY_API_KEY=your_tavily_api_key
   ```

2. **Database Folder**:
   Create a folder named `chroma_db` in the root directory to store the vector database files:
   ```bash
   mkdir chroma_db
   ```
   *Note: While the script initializes the database, ensuring this folder exists prevents potential permission or path issues.*

3. **Source Document**:
   Place your specific PDF file (e.g., `report.pdf` or `Stanford.pdf`) in the root directory. Update the `pdf_path` variable in the notebook if your filename differs.

## Usage

1. Open the Jupyter Notebook `agent.ipynb`.
2. Run the cells sequentially to initializes the clients, ingest the PDF, and define the agent functions.
3. Use the `verify_information(query)` function to ask questions.

Example:
```python
query = "Summarize the main points of the report and verify..."
response = verify_information(query)
print(response)
```

## Attribution

The sample PDF (`Stanford.pdf`) used for testing this agent was created using excerpts from the following article:

*   **Title**: The End of Static Prompts: Stanford's ACE Framework Changes Everything – Why your AI gets smarter by remembering more, not learning less
*   **Author**: Manav Sutar (InfraFlow AI)
*   **Date**: Oct 13, 2025
