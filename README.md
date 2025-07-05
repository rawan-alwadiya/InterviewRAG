# **InterviewRAG: A Context-Aware Interview Preparation Assistant**

**InterviewRAG** is a lightweight Retrieval-Augmented Generation (RAG) system built to support interview preparation through intelligent, context-grounded question answering. It processes **user-uploaded interview PDFs**, retrieves relevant information, and generates coherent answers using **locally hosted open-source models**.

Designed for students, job seekers, and professionals, InterviewRAG rephrases vague user inputs, retrieves relevant context segments, and delivers precise responses—all while maintaining short-term conversation history for enhanced continuity. The system runs entirely offline and ensures a high degree of data privacy and control.

---

## **Project Objectives**

- Upload and parse interview preparation PDFs.
- Split the content into semantically meaningful chunks.
- Store and retrieve text segments using vector-based semantic search.
- Automatically rephrase user questions to improve context matching.
- Generate grounded answers strictly based on the PDF content.
- Track short-term conversational memory across questions.
- Operate fully offline using local language models and vector databases.

---

## **Key Capabilities**

### **PDF-Based Interview Preparation**
- Accepts a PDF document related to interview topics.
- Loads and segments the content for granular retrieval.

### **Semantic Retrieval with Local Embeddings**
- Utilizes `MiniLM` embeddings for efficient vector search across document segments.

### **Question Expansion and Answer Generation**
- Uses `Mistral-7B-Instruct` to expand vague questions and provide detailed, grounded answers.

### **Short-Term Memory Buffer**
- Maintains a history of recent interactions using `ConversationBufferMemory` to support follow-up dialogue.

### **Private, Local Deployment**
- All components—including language models, embeddings, and retrieval—run locally with no external service dependency.

---

## **Core Components**

- **Document Loader**: `PyPDFLoader` for extracting text from uploaded PDFs.
- **Text Chunking**: `RecursiveCharacterTextSplitter` to split documents into context-preserving segments.
- **Embeddings**: `all-MiniLM-L6-v2` via `HuggingFaceEmbeddings` for vector-based retrieval.
- **Vector Store**: `Chroma` for fast and persistent document chunk retrieval.
- **LLM (Answering + Query Expansion)**: `mistralai/Mistral-7B-Instruct-v0.1` via `HuggingFacePipeline`.
- **Memory**: `ConversationBufferMemory` to support conversational continuity.
- **RAG Chain**: LangChain's `ConversationalRetrievalChain` to orchestrate retrieval, memory, and response generation.
