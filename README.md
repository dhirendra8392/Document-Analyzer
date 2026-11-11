
# Document Analyzer Agent

## Overview

Document Analyzer Agent is an interactive AI-powered application that extracts and summarizes key information from academic research papers in PDF format. It uses **Retrieval-Augmented Generation (RAG), ChromaDB, LangChain, and OpenAI GPT-4o-mini** to retrieve relevant document content and generate structured insights.

The application simplifies research paper analysis by automating the extraction of important information such as paper titles, summaries, publication dates, and authors, reducing the need to manually read entire documents.

## Key Features

- **PDF Document Processing:** Upload and extract text from research papers in PDF format.
- **Text Chunking:** Split extracted document content into smaller overlapping chunks while preserving contextual information.
- **Embedding Generation:** Convert text chunks into vector representations using OpenAI embedding models.
- **Vector Database:** Store and organize document embeddings using ChromaDB.
- **Semantic Retrieval:** Retrieve relevant document sections based on contextual similarity.
- **RAG Pipeline:** Combine retrieved document context with LLM-based generation to produce relevant responses.
- **Structured Information Extraction:** Extract paper titles, summaries, publication dates, and author information.
- **Source-Based Responses:** Display supporting document passages and explanations alongside generated answers.
- **Interactive Interface:** Provide a Streamlit-based interface for document uploading and analysis.

## System Architecture

The application follows a modular document processing and RAG pipeline.

```text
       Research Paper (PDF)
                |
                v
         PDF Text Extraction
          (PyPDFLoader)
                |
                v
          Text Chunking
    (RecursiveCharacterTextSplitter)
                |
                v
        Embedding Generation
                |
                v
          ChromaDB
        (Vector Storage)
                |
                v
       Semantic Retrieval
                |
                v
        Retrieved Context
                |
                v
          GPT-4o-mini
                |
                v
       Structured Output
                |
                v
       Streamlit Interface
```

## Technical Implementation

### 1. Interactive User Interface

- Developed the application interface using Streamlit.
- Implemented a two-column layout for document uploading and result visualization.
- Added PDF upload functionality and OpenAI API key input.
- Displayed the uploaded research paper alongside the extracted results.

### 2. PDF Processing and Text Chunking

- Used LangChain's `PyPDFLoader` to extract text from uploaded PDF documents.
- Converted extracted content into structured document objects.
- Implemented `RecursiveCharacterTextSplitter` with a chunk size of 1000 characters and an overlap of 200 characters.
- Preserved contextual continuity between consecutive document chunks.

### 3. Embedding Generation and Vector Storage

- Generated semantic embeddings using OpenAI's embedding model.
- Stored document embeddings in ChromaDB for efficient similarity-based retrieval.
- Implemented document chunk deduplication to avoid redundant vector entries.
- Organized vector collections using cleaned document filenames.

### 4. Retrieval-Augmented Generation (RAG)

- Implemented a retrieval pipeline to identify relevant document chunks.
- Used semantic similarity search to retrieve contextual information from ChromaDB.
- Passed retrieved document content to GPT-4o-mini using LangChain's `ChatOpenAI`.
- Designed a prompt template to generate responses based on the retrieved document context.

### 5. Structured LLM Output

- Used Pydantic-based structured output to organize LLM responses.
- Extracted the following information:
  - Research paper title
  - Paper summary
  - Publication date
  - Author information
- Included supporting source passages and explanations for extracted information.

### 6. Result Visualization

- Used Pandas to organize the extracted information into a structured table.
- Displayed the final answer, supporting context, and explanation for each extracted field.
- Presented the results directly within the Streamlit application.

## Technology Stack

| Category | Technologies |
|---|---|
| Programming Language | Python |
| Frontend | Streamlit |
| LLM Framework | LangChain |
| Large Language Model | OpenAI GPT-4o-mini |
| Embedding Model | OpenAI text-embedding-ada-002 |
| Vector Database | ChromaDB |
| PDF Processing | PyPDFLoader |
| Text Splitting | RecursiveCharacterTextSplitter |
| Structured Output | Pydantic |
| Data Processing | Pandas |

## Limitations

- Currently supports machine-readable PDFs; scanned documents requiring OCR are not supported.
- Requires a valid OpenAI API key for embedding generation and LLM inference.
- Uses a predefined query for extracting research paper metadata.
- Extraction quality depends on document structure, text availability, and retrieved context.

## Future Enhancements

- Support custom questions and conversational document querying.
- Enable analysis of multiple research papers.
- Add OCR support for scanned PDF documents.
- Implement downloadable summaries and structured reports.
- Improve retrieval through hybrid search and metadata filtering.

## How to Run

### Prerequisites

- Python 3.x
- Valid OpenAI API key
- Required Python dependencies

### Installation

Install the project dependencies:

```bash
pip install -r requirements.txt
```

### Run the Application

Launch the Streamlit application:

```bash
streamlit run stream_app.py
```

Open the local URL displayed in the terminal to access the application.

Enter your OpenAI API key, upload a research paper in PDF format, and generate the extracted information.

*Note: Run the command from the directory containing `stream_app.py`. Adjust the filename or path if your application entry point is named differently.*

## Developer

**Dhirendra Sahani**

B.Tech – Electronics and Instrumentation Engineering  
National Institute of Technology, Agartala

- GitHub: [dhirendra8392](https://github.com/dhirendra8392)
- LinkedIn: [Dhirendra Sahani](https://www.linkedin.com/in/dhirendra-sahani-129b98265/)

## License

This project is licensed under the MIT License.
