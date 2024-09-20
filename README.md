## RAG Process repository

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
