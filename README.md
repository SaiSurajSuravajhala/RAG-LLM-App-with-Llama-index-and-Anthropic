# RAG-LLM-App-with-Llama-index-and-Anthropic

A simple **Retrieval Augmented Generation (RAG)** system that lets you chat with your PDF documents using AI. Upload your PDFs and ask questions about them!

## 🤖 What is RAG?

RAG stands for **Retrieval Augmented Generation**. In simple terms:
- **Retrieval**: Find relevant information from your documents
- **Augmented**: Add that information to the AI's knowledge
- **Generation**: AI generates answers based on your documents

Think of it as giving the AI a library of your documents so it can answer questions about them accurately!

## 🚀 Features

- **Upload PDF Documents**: Add your own PDF files to the system
- **Ask Questions**: Chat with your documents using natural language
- **Get Accurate Answers**: AI answers based on your uploaded content
- **Free Embeddings**: Uses HuggingFace models (no OpenAI API needed for embeddings)
- **Fast AI Responses**: Powered by Claude 3 Haiku for quick answers

## 📋 Requirements

Before running this project, you need:

1. **Python 3.8+** installed on your computer
2. **Anthropic API Key** (for Claude AI)
   - Sign up at [Anthropic Console](https://console.anthropic.com/)
   - Get your API key from the dashboard

## 🛠️ Installation

1. **Clone this repository**
   ```bash
   git clone https://github.com/yourusername/RAG-LLM-App-with-Llama-index-and-Claude.git
   cd RAG-LLM-App-with-Llama-index-and-Claude
   ```

2. **Install required packages**
   ```bash
   pip install -r requirements.txt
   ```

3. **Set up your API key**
   - Create a `.env` file in the project folder
   - Add your Anthropic API key:
   ```
   ANTHROPIC_API_KEY=your_api_key_here
   ```

## 📁 Project Structure

```
RAG-LLM-App/
├── data/                    # Put your PDF files here
│   ├── attention.pdf        # Sample PDF about attention mechanism
│   └── yolo.pdf            # Sample PDF about YOLO object detection
├── test.ipynb              # Main notebook with all the code
├── requirements.txt        # List of required Python packages
├── .env                    # Your API keys (create this file)
└── README.md              # This file
```

## 🚀 How to Use

1. **Add your PDF files**
   - Put your PDF documents in the `data/` folder
   - The system will automatically read all PDFs in this folder

2. **Run the notebook**
   - Open `test.ipynb` in Jupyter Notebook or Google Colab
   - Run all cells step by step

3. **Ask questions**
   - Use the query engine to ask questions about your documents
   - Example: `query_engine.query("What is attention mechanism?")`

## 💡 Example Usage

```python
# Load your documents
documents = SimpleDirectoryReader("data").load_data()

# Create an index (this processes your documents)
index = VectorStoreIndex.from_documents(documents)

# Create a query engine
query_engine = index.as_query_engine()

# Ask questions about your documents
response = query_engine.query("What is YOLO in computer vision?")
print(response)
```

## 🔧 How It Works

1. **Document Processing**: Your PDFs are split into smaller chunks
2. **Embedding Creation**: Each chunk gets converted to numbers (embeddings) using HuggingFace
3. **Storage**: Embeddings are stored in a vector database
4. **Question Answering**: When you ask a question:
   - System finds relevant chunks from your documents
   - Sends question + relevant chunks to Claude AI
   - Claude generates an answer based on your documents

## 📦 Dependencies

- `llama-index`: Main framework for building RAG applications
- `llama-index-llms-anthropic`: Claude AI integration
- `anthropic`: Anthropic's Python SDK
- `sentence-transformers`: Free embeddings model
- `pypdf`: PDF document processing
- `python-dotenv`: Environment variable management

## 🎯 Sample Questions You Can Ask

Based on the sample PDFs included:

**About Attention Mechanism:**
- "What is attention mechanism?"
- "How does self-attention work?"
- "What are the advantages of attention?"

**About YOLO:**
- "What is YOLO?"
- "How does YOLO detect objects?"
- "What are the different versions of YOLO?"

## 🔒 Security Note

- Never commit your `.env` file to GitHub
- Keep your API keys private
- The `.env` file is already in `.gitignore` to prevent accidental uploads

## 🛟 Troubleshooting

**Common Issues:**

1. **"No module named 'llama_index'"**
   - Make sure you installed all requirements: `pip install -r requirements.txt`

2. **"API key not found"**
   - Check your `.env` file has the correct API key
   - Make sure the file is in the project root folder

3. **"Empty Response"**
   - Your question might be too different from document content
   - Try asking more specific questions about your documents

## 🌟 Future Improvements

- [ ] Add a web interface using Streamlit
- [ ] Support for more document types (Word, PowerPoint)
- [ ] Chat history to remember previous questions
- [ ] Multiple document collections
- [ ] Real-time document upload
