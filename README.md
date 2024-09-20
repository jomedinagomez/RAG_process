## RAG Process repository


---  
### Repository Description  
   
The RAG Process repository is aimed to be a resource for managing the data lifecycle in RAG applications, providing tools for data preprocessing, indexing, and tool/function calling integration.

The RAG Process repository is structured to facilitate the management and processing of data for retrieval-augmented generation (RAG) tasks. It is organized into several key directories, each serving a distinct purpose:  
   
#### 1. Data  
- **Processed**: Contains files, structured data, and tool descriptions that have been refined from raw data.  
- **Raw**: Houses the original, unprocessed data files.    
#### 2. Traditional RAG  
- **Preprocessing and Chunking**: Scripts and libraries for preprocessing and segmenting (chunking) documents.  
   - All of the approaches use Azure Document Intelligence for OCR.
   - You can chose among different preprocessing options:  
     - Markdown processing for rich, hierarchical text handling: ```This approach uses MarkdownHeaderTextSplitter.```  
     - Page indexing for detailed file analysis:  ```This approach keeps the integrity of each page.```  
     - Chunk processing for efficient data handling: ```This approach avoid chunking tables.```
- **Pull Indexer**: Tools for indexing data using Azure SQL Database and CosmosDB. Includes scripts for data loading to both services (Azure SQL Database and Azure CosmosDB and index creation.
  - In this folder you will find sample code to create indexers using different strategies:
    - No skillset: ```This assumes that your data will be already chunked and that each chunk/section contains a vector.```
    - Skillset: ```This approach uses an skillset alongside the integrated vectorizer to chunk your documents and created the vector embeddings.```
#### 3. Tool Calling  
- **CosmosDB tool**:  This notebook showcases an approach to generate CosmosDB NoSQL queries based on natural language questions. It uses Azure OpenAI to convert the question into a NoSQL query and then executes the query against CosmosDB.
- **RAG tool**: this tool executes on a few functions:
   - rewrite_query: ```This function rewrites a user's question into multiple search intents to find the most relevant documents in Azure Search.```
   - HybridSearch: ```This function performs a hybrid search using both text and vector queries to retrieve relevant documents from Azure Search.```
   - GetRAGAnswer: ```This function is designed to generate answers based on retrieved documents and the user's query. It uses a prompt to guide the response generation and ensures that the answers are based on the provided documents.```
- **SQLDB tool**:  This notebook showcases an approach to generate Azure SQL Database queries based on natural language questions. It uses Azure OpenAI to convert the question into a Azure SQL Database query and then executes the query against Azure SQL Database.
- **Multi tool**:  This approach processes each message in a conversation, determines the appropriate action or tool to invoke (such as querying CosmosDB, SQLDB, or performing a document search), and updates the conversation history with the responses. It maintains the context throughout the conversation and returns the final conversation history and results.
  
#### 4. Legacy  
- **Page Index**: Includes Jupyter notebooks for reading files, creating search indexes, and pushing data to indexes. These are legacy processes that were previously used.  
- Contains older versions of processing scripts and notebooks, including those for handling new search SKUs.
#### 5. Docs  
- A section dedicated to documentation, providing essential information and guidance on using the repository's resources. 
---  

#### Repository Map
```
RAG_process/
├── data/
│   ├── processed/
│   │   ├── files/
│   │   │   ├── 10K-AMZN-02-03-2023.pdf.parquet
│   │   │   ├── 10K-AMZN-02-04-2022.pdf.parquet
│   │   │   ├── ...
│   │   │   └── 10Q-MSFT-10-25-2022.pdf.parquet
│   │   ├── structured/
│   │   │   ├── customers.csv
│   │   │   ├── merchants.csv
│   │   │   ├── products.csv
│   │   │   ├── sales.csv
│   │   │   ├── sales_detail.csv
│   │   │   └── stock.csv
│   │   └── tool_description/
│   │       └── GetSQLDBAnswerDescription.txt
│   └── raw/
├── legacy/
│   ├── step_1_read_files.ipynb
│   ├── step_2_create_search_index.ipynb
│   ├── step_3_push_datatoindex.ipynb
│   └── page_index/
│       ├── step_1_read_files.ipynb
│       ├── step_2_create_search_index.ipynb
│       └── step_3_push_datatoindex.ipynb
├── tool_calling/
│   ├── AISearch_tool_calling.ipynb
│   ├── AzureSQL_tool_calling.ipynb
│   ├── CosmosDB_tool_calling.ipynb
│   └── MultiAgent_tool_calling.ipynb
└── Traditional_RAG/
    ├── Preprocessing and Chunking/
    └── Pull_Indexer/
        ├── AzureSQL_DB/
        │   ├── create_indexer/
        │   └── load_data/
        │       └── SQLDB_upload_data.ipynb
        └── CosmosDB_NoSQL/
            ├── create_indexer/
            │   ├── 2_create_indexer_documents_NoSkill.ipynb
            │   └── 2_create_indexer_documents_Skill.ipynb
            └── load_data/
                └── CosmosDB_upload_data.ipynb
```
---
```
This is a demo repository and is not aimed for production workloads.
```
---
